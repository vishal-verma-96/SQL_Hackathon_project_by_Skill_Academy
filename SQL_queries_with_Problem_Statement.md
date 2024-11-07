***Problem Statement***</br>
**List the salary of all the employees.**

The Employee table is described as follows:

|   Field   |   Type  |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | char(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

*where ENAME is Employee name,*</br>
*ESRNO is Employee Service Record Number,*</br>
*BDATE is Birthday,*</br>
*MGRSRNO is Manager Serial Number and*</br> 
*DNO is Department Number.*

**Solution**
```sql
SELECT ename,salary FROM employee;
```

***Problem Statement*** </br>
**Display the names of all employees with any “A” at any place of the name.**

The Employee table is described as follows:

| Field | Type |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

**Solution**
```sql
SELECT ename 
FROM employee 
WHERE ename LIKE '%A%';                 
```

***Problem Statement***</br> 
**Display the name of all female employees.**

The Employee table is described as follows:

| Field | Type |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

**Solution**
```sql
SELECT ename,sex 
FROM employee 
WHERE sex = 'F';                   
```

***Problem Statement***</br> 
**Display the employee who is paid most in the company.**

The Employee table is described as follows:

|  Field | Type |
|---|---|
| ENAME  | varchar(20) |
| ESRNO | varchar(7) |
| BDATE  | date |
| ADDRESS | varchar(20) |
| SEX  | varchar(20) |
| SALARY | int(7) |
| MGRSRNO  | varchar(6) |
| DNO | int(7) |

**Solution**
```sql
SELECT ename,salary 
FROM employee 
WHERE salary = (SELECT MAX(salary) FROM employee);               
```

***Problem Statement***</br>
**Display employee name, address with their respective department no and department name.**

The Employee and Department table are described as follow:

|   Field   |   Type  |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

|   Field   |   Type  |
|-----|-----|
| DNAME | varchar(12) |
| DNUMBER | int(2) |
| MGRSRNO | char(6) |
| MGRSTARTD | date |

*where MGRSRNO is Manager Serial Number and*</br>
*MGRSTARTD is refers to the date when the specified department established.*

**Solution**
```sql
SELECT ename,address,dnumber,dname
FROM employee
JOIN department ON employee.dno = department.dnumber;   
```

***Problem Statement***</br>
**Display all the employees who are not in ACADEMIC department.**

The Employee and Department table are described as follow:

|   Field   |   Type  |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

|   Field   |   Type  |
|-----|-----|
| DNAME | varchar(12) |
| DNUMBER | int(2) |
| MGRSRNO | varchar(6) |
| MGRSTARTD | date |

**Solution**
```sql
SELECT ename,dname             
FROM employee 
JOIN department ON employee.dno = department.dnumber             
WHERE DNAME <> 'ACADEMIC';               
```

***Problem Statement***</br>
**Display SATYAS’ project location.**

The Employee and Project table are described as follow:

|   Field   |   Type  |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

|   Field   |   Type  |
|-----|-----|
| PNAME | varchar(12) |
| PNUMBER | int(2) |
| PLOCATION | varchar(6) |
| DNUM | date |

*where PNAME is Project name,*</br>
*PNUMBER is Project number,*</br>
*PLOCATION is Project Location and*</br>
*DNUM is Department Number.*

**Solution**
```sql
SELECT ename,pname,plocation
FROM employee
JOIN project ON employee.dno = project.dnum
WHERE ENAME = 'SATYA';                         
```

***Problem Statement***</br>
**Find the total working hours of each female employee.**

The Employee and Works_On table are described as follow:

|   Field   |   Type  |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

|   Field   |   Type  |
|-----|-----|
| ESRNO | varchar(6) |
| PNO | int(3) |
| HOURS | decimal(5,2) |


**Solution**
```sql
SELECT ename,sex,SUM(hours) as total_working_hours
FROM employee
JOIN works_on ON employee.esrno = works_on.esrno
WHERE sex = 'F'
GROUP BY ename,sex;                        
```

***Problem Statement***</br>
**Display the details of the people whose projects are located at SOUTH AFRICA.**

The Employee and Project table are described as follow:

|   Field   |   Type  |
|-----|-----|
| ENAME | varchar(20) |
| ESRNO | varchar(7) |
| BDATE | date |
| ADDRESS | varchar(20) |
| SEX | varchar(20) |
| SALARY | int(7) |
| MGRSRNO | varchar(6) |
| DNO | int(7) |

|   Field   |   Type  |
|-----|-----|
| PNAME | varchar(12) |
| PNUMBER | int(2) |
| PLOCATION | varchar(6) |
| DNUM | date |

**Solution**
```sql
SELECT employee.*,project.plocation          
FROM employee
JOIN project ON employee.dno = project.dnum           
WHERE plocation='SOUTH AFRICA';                         
```
