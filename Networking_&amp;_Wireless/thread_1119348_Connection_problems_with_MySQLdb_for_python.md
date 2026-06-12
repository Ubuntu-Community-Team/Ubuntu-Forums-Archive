---
title: "Connection problems with MySQLdb for python"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by Captain_Glen on 2009-04-07
Hi,

I have installed MySQLdb for python

```
sudo apt-get install python-mysqldb
```

I have written a basic python script

```
#!/usr/bin/python

# import MySQL module
import MySQLdb

# connect
db = MySQLdb.connect(host="glen-laptop", user="mythtv", passwd="mythtv",
db="mythconverg")

# create a cursor
cursor = db.cursor()

# execute SQL statement
cursor.execute("SELECT * FROM channel")

# get the resultset as a tuple
result = cursor.fetchall()

# iterate through resultset
for record in result:
        print record[0] , "-->", record[1]
```

glen-laptop is my host name but when I run the script with IDLE I get an error that it couldn't connect to the database.  If I replace glen-laptop with localhost it works.  But I want to be able to run this script on a different computer to the one that has the database.

The error is 
```
Traceback (most recent call last):
  File "/home/glen/test.py", line 8, in <module>
    db="mythconverg")
  File "/var/lib/python-support/python2.5/MySQLdb/__init__.py", line 74, in Connect
    return Connection(*args, **kwargs)
  File "/var/lib/python-support/python2.5/MySQLdb/connections.py", line 170, in __init__
    super(Connection, self).__init__(*args, **kwargs2)
OperationalError: (2003, "Can't connect to MySQL server on 'glen-laptop' (111)")
```

Any help would be appreciated.

---

### Post by lensman3 on 2009-04-08
Change the following line:

db = MySQLdb.connect(host="glen-laptop", user="mythtv", passwd="mythtv",
db="mythconverg")

TO


db = MySQLdb.connect(host="glen-laptop", user="mythtv", passwd="mythtv",
"mythconverg")

That second line with db="mythconverg") is assigning the variable db twice?  That or change the first db to something else.

Sorry I don't know python (or want to know).

---

### Post by Subnet on 2009-04-08
Is your login granted permissions to login from something other than localhost? It's been a long time since I've touched MySQL after I switched to PostgreSQL. Also, I would probably look at using sqlalchemy.

---

