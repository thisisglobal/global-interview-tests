# Employee Service Coding Test

### Task
* Create a RESTful API with one endpoint:
    * ```GET /employees```
* With optional query params:
    * **managerId**: return all employees for a given manager
        * e.g. ```/employees?managerId=1```
        * Defaults to return all employees
    * **sort**: the name of the field to sort by
        * e.g. ```/employees?sort=lastName``` 
        * Defaults to unsorted
    * **direction**: the direction to sort
        * ASC/DESC
        * e.g. ```/employees?sort=lastName?direction=DESC```
        * Defaults to ASC
        
### Database
| Column Name     | type           | example   |
|: ------------ : |:-------------: | -----:    |
| id              | INT(11)        | 1         |
| first_name      | VARCHAR(32)    | Cristiano |
| last_name       | VARCHAR(32)    | Ronaldo   |       
| manager_id      | INT(11)        |    7      |  
| role            | VARCHAR(64)    | Footballer|       

To pull the seeded docker MySQL image run: 

```docker pull cmboult/global-test-db```.

To run the container on port 3326 (default for project setup), run:

```docker run -d -p 3326:3203 cmboult/global-test-db```

### Example Responses
```
GET /employees
[  
   {  
      "id":2,
      "firstName":"Bill",
      "lastName":"Bryson",
      "managerId":1,
      "role":"Researcher"
   },
   {  
      "id":3,
      "firstName":"Charles",
      "lastName":"Crawford",
      "managerId":5,
      "role":"Director"
   },
   {  
      "id":1,
      "firstName":"Andrew",
      "lastName":"Allard",
      "managerId":3,
      "role":"Manager"
   }
]
```   

```
GET /employees?sort=lastName&direction=DESC
[  
   {  
      "id":3,
      "firstName":"Charles",
      "lastName":"Crawford",
      "managerId":5,
      "role":"Director"
   },
   {  
      "id":2,
      "firstName":"Bill",
      "lastName":"Bryson",
      "managerId":1,
      "role":"Researcher"
   },
   {  
      "id":1,
      "firstName":"Andrew",
      "lastName":"Allard",
      "managerId":3,
      "role":"Manager"
   }
]
```

```
GET /employees?managerId=3
[  
   {  
      "id":1,
      "firstName":"Andrew",
      "lastName":"Allard",
      "managerId":3,
      "role":"Manager"
   }
]
```