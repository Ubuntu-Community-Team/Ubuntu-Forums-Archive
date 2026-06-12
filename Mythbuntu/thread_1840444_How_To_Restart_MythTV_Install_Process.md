---
title: "How To Restart MythTV Install Process"
date: 2011-09-07
forum: Mythbuntu
---

### Post by Singlebbl on 2011-09-07
What is the procedure for restarting the MythTV install process using Mythbuntu?  I would like to be able to simply delete the current mythconverg database and build a new one from scratch.  No recordings have been made so there is very little to lose by doing this.  

I'm running Ubuntu 10.04 LTS on a Dell Dimension 4600 and am using an HDHR dual tuner for video capture.  I assume that Mythbuntu installed MythTV 0.24.1 but I have not found a way to verify that.  

I made a lot of mistakes during the install process and it now appears that the mythconverg database is corrupt.  

The mythbackend is listening on port 6549 instead of 6543 and 6544:  
```
seth@Landon:~$ sudo netstat -ltnp |grep myth
[sudo] password for seth: 
tcp        0      0 0.0.0.0:6549            0.0.0.0:*               LISTEN      25711/mythbackend
```And an examination of the data in mythconverg shows strange looking entries:  
```
mysql> SELECT * FROM settings WHERE data LIKE '%127%';
+-----------------+-----------+----------+
| value           | data      | hostname |
+-----------------+-----------+----------+
| BackendServerIP | 127.0.0.1 | landon   |
| MasterServerIP  | 127.0.0.1 | NULL     |
| BackendServerIP | 127.0.0.1 | landon   |
+-----------------+-----------+----------+
3 rows in set (0.00 sec)

mysql> SELECT * FROM settings WHERE data LIKE '%168%';
+----------------+-------------------------------------+----------+
| value          | data                                | hostname |
+----------------+-------------------------------------+----------+
| DefaultVxmlUrl | [http://192.168.0.10/vxml/index.vxml](http://192.168.0.10/vxml/index.vxml) | Landon   |
+----------------+-------------------------------------+----------+
1 row in set (0.00 sec)mysql> SELECT * FROM settings WHERE data LIKE '%6549%';
Empty set (0.00 sec)

mysql> SELECT * FROM settings WHERE data LIKE '%6544%';
+-------------------+------+----------+
| value             | data | hostname |
+-------------------+------+----------+
| BackendStatusPort | 6544 | Landon   |
| BackendStatusPort | 6544 | Landon   |
+-------------------+------+----------+
2 rows in set (0.00 sec)

mysql> SELECT * FROM settings WHERE data LIKE '%6543%';
+-------------------+------+----------+
| value             | data | hostname |
+-------------------+------+----------+
| BackendServerPort | 6543 | Landon   |
| MasterServerPort  | 6543 | NULL     |
| BackendServerPort | 6543 | Landon   |
+-------------------+------+----------+
3 rows in set (0.00 sec)
```

---

### Post by MickSulley on 2011-09-08
I think you should be able to use Synaptic to do a complete removal, that should remove all of the setup, then install again.

---

### Post by nickrout on 2011-09-08
```
mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'
mysql -u root < /usr/share/mythtv/sql/mc.sql
```

---

### Post by Singlebbl on 2011-10-22
[SIZE=1]> **nickrout said:**
> [SIZE=2]```
mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```[/SIZE]

Thanks, this works.  

Turned out that the port issue was a result of not having 0.24.1 installed.  Now that the code is updated, it's running at a very basic level with several issues still to be resolved.  

See [http://www.mythtvtalk.com/could-not-connect-master-backend-server-15038/#post58504](http://www.mythtvtalk.com/could-not-connect-master-backend-server-15038/#post58504) for details.  

[/SIZE][SIZE=3]Note:  Added missing "-p" to the second sql command[/SIZE]

---

