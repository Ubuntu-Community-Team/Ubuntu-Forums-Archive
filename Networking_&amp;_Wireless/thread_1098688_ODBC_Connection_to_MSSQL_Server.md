---
title: "ODBC Connection to MSSQL Server"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by fabio.casolari on 2009-03-17
Hi i have tried without success to connect to an mssql server via odbc/php5 i can't configure correctly the connection driver.

Here the error:
```
Warning: odbc_connect() [function.odbc-connect]: SQL error: [unixODBC][Driver Manager]Data source name not found, and no default driver specified, SQL state IM002 in SQLConnect in /var/www/default/dbmacchine/test.php on line 3
```

And here my config:

/etc/odbc.ini & /etc/odbcinst.ini
```
[TECNO60]
Driver        = FreeTDS
Description     = Conexion a Sql  con FreeTDS / ODBC
Trace         = No
Servername    = 172.16.1.3
Database    = TECNO60

[default]
Driver        = FreeTDS
Description     = Conexion a Sql  con FreeTDS / ODBC
Trace         = No
Servername    = 172.16.1.3
Database    = TECNO60
```

---

### Post by ethos84 on 2009-03-25
Trying to do a similar thing (just connect in general).

Can't find any helpful info and by helpful I mean anything that works.

---

### Post by fabio.casolari on 2009-03-25
FOUND A SOLUTION:

on Ubuntu Server I needed to install some packages

```
sudo aptitude install unixodbc unixodbc-dev freetds-dev sqsh tdsodbc
```

With FreeTDS installed I could configure it like this:

```
/etc $ cat freetds.conf
[SERVER]
  host = 192.168.0.10
  port = 1433
  tds version = 7.0
```

The important thing here is SERVER, which is the DSN that I’ll use when connecting to the database. The host, and port are self-explanatory, and it’s worth nothing that I had to use 7.0 specifically as the tds version.

Testing FreeTDS is not too hard:

```
$ sqsh -S SERVER -U username -P password
sqsh: Symbol `_XmStrings' has different size in shared object, consider re-linking
sqsh-2.1 Copyright (C) 1995-2001 Scott C. Gray
This is free software with ABSOLUTELY NO WARRANTY
For more information type '\warranty'
1> use test
2> go
1> select top 1 firstname, lastname from tblClients
2> go

[record returned]

(1 row affected)
1> quit
```

Next up it’s necessary to configure ODBC:

```
/etc$ cat odbcinst.ini
[FreeTDS]
Description     = TDS driver (Sybase/MS SQL)
Driver          = /usr/lib/odbc/libtdsodbc.so
Setup           = /usr/lib/odbc/libtdsS.so
CPTimeout       =
CPReuse         =
FileUsage       = 1

/etc$ cat odbc.ini
[SERVER]
Driver          = FreeTDS
Description     = ODBC connection via FreeTDS
Trace           = No
Servername      = SERVER
Database        = DATABASE
```

I then tested the connection with isql:

```
$ isql -v SERVER username password
+---------------------------------------+
| Connected!                            |
|                                       |
| sql-statement                         |
| help [tablename]                      |
| quit                                  |
|                                       |
+---------------------------------------+
SQL> use DATABASE
[][unixODBC][FreeTDS][SQL Server]Changed database context to 'database'.
[ISQL]INFO: SQLExecute returned SQL_SUCCESS_WITH_INFO
SQLRowCount returns -1
SQL> select top 1 firstname from tblClients;

[record returned]

SQLRowCount returns 1
1 rows fetched
SQL> quit
```

OK, so we’ve got ODBC using FreeTDS to connect to a remote MSSQL server.

Bye,
Fabio Casolari
[http://www.ripartodazero.it](http://www.ripartodazero.it)

---

### Post by enebish on 2011-02-04
Grazie Fabio... I was really going mad.

---

### Post by vineeth v s on 2011-08-30
me too facing the same problem and i tried that solution,
but after installing 

[code]
sudo aptitude install unixodbc unixodbc-dev freetds-dev sqsh tdsodbc
when i tried 
[code]
/etc $ cat freetds.conf
/etc $
their is no such file!!!


what should i do??

---

### Post by NeroMaverick on 2011-09-09
> **vineeth v s said:**
> me too facing the same problem and i tried that solution,
but after installing 

```

sudo aptitude install unixodbc unixodbc-dev freetds-dev sqsh tdsodbc
when i tried 
[code]
/etc $ cat freetds.conf
/etc $
their is no such file!!!


what should i do??

Try this
[CODE]cat /etc/freetds/freetds.conf
```

Remember this, when in doubt tab it out :P (basically frantically hit tab before finishing the file name, dir name, etc.)

Also you'll want to use nano or vi for editing (gedit for the less extreme users), cat just displays the contents of files

So
```
nano /etc/freetds/freetds.conf
```

---

