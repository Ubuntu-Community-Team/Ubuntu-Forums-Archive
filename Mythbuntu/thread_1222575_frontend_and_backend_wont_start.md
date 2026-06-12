---
title: "frontend and backend wont start"
date: 2009-07-25
forum: Mythbuntu
---

### Post by spleblem on 2009-07-25
hey randomly i turned my pc on the other day and the front end didnt open
not sure what i have done
also the backend wont open
here is what terminal shows

```
media@media-pc:~$ mythfrontend
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2009-07-25 16:58:38.616 Using runtime prefix = /usr
2009-07-25 16:58:38.616 Configuration::Load - Error parsing: /home/media/.mythtv/config.xml at line: 1  column: 1
2009-07-25 16:58:38.616 Configuration::Load - Error Msg: unexpected end of file
2009-07-25 16:58:39.160 XScreenSaver support enabled
2009-07-25 16:58:39.160 DPMS is active.
2009-07-25 16:58:39.160 DBHostName is not set in mysql.txt
2009-07-25 16:58:39.160 Assuming localhost
2009-07-25 16:58:39.160 DBUserName is not set in mysql.txt
2009-07-25 16:58:39.160 DBPassword is not set in mysql.txt
2009-07-25 16:58:39.160 DBName is not set in mysql.txt
2009-07-25 16:58:39.160 Empty LocalHostName.
2009-07-25 16:58:39.160 Using localhost value of media-pc
2009-07-25 16:58:39.161 Configuration::Load - Error parsing: /home/media/.mythtv/config.xml at line: 1  column: 1
2009-07-25 16:58:39.161 Configuration::Load - Error Msg: unexpected end of file
2009-07-25 16:58:39.165 New DB connection, total: 1
2009-07-25 16:58:39.168 Connected to database '' at host: localhost
2009-07-25 16:58:39.168 Closing DB connection named 'DBManager0'
2009-07-25 16:58:39.169 Primary screen 0.
2009-07-25 16:58:39.170 Connected to database '' at host: localhost
2009-07-25 16:58:39.170 Using screen 0, 1024x768 at 0,0
2009-07-25 16:58:39.174 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:39.174 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2009-07-25 16:58:40.174 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:41.175 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:42.176 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:43.177 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:44.177 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:44.178 Timed out waiting.
2009-07-25 16:58:44.178 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.
media@media-pc:~$ 
```

```
media@media-pc:~$ mythfrontend
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2009-07-25 16:58:38.616 Using runtime prefix = /usr
2009-07-25 16:58:38.616 Configuration::Load - Error parsing: /home/media/.mythtv/config.xml at line: 1  column: 1
2009-07-25 16:58:38.616 Configuration::Load - Error Msg: unexpected end of file
2009-07-25 16:58:39.160 XScreenSaver support enabled
2009-07-25 16:58:39.160 DPMS is active.
2009-07-25 16:58:39.160 DBHostName is not set in mysql.txt
2009-07-25 16:58:39.160 Assuming localhost
2009-07-25 16:58:39.160 DBUserName is not set in mysql.txt
2009-07-25 16:58:39.160 DBPassword is not set in mysql.txt
2009-07-25 16:58:39.160 DBName is not set in mysql.txt
2009-07-25 16:58:39.160 Empty LocalHostName.
2009-07-25 16:58:39.160 Using localhost value of media-pc
2009-07-25 16:58:39.161 Configuration::Load - Error parsing: /home/media/.mythtv/config.xml at line: 1  column: 1
2009-07-25 16:58:39.161 Configuration::Load - Error Msg: unexpected end of file
2009-07-25 16:58:39.165 New DB connection, total: 1
2009-07-25 16:58:39.168 Connected to database '' at host: localhost
2009-07-25 16:58:39.168 Closing DB connection named 'DBManager0'
2009-07-25 16:58:39.169 Primary screen 0.
2009-07-25 16:58:39.170 Connected to database '' at host: localhost
2009-07-25 16:58:39.170 Using screen 0, 1024x768 at 0,0
2009-07-25 16:58:39.174 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:39.174 Unexpected DB Schema version.  Waiting to see if DB is being upgraded.
2009-07-25 16:58:40.174 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:41.175 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:42.176 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:43.177 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:44.177 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:58:44.178 Timed out waiting.
2009-07-25 16:58:44.178 This version of MythTV requires an updated database schema. Please run mythtv-setup or mythbackend to update your database.
media@media-pc:~$ clear

media@media-pc:~$ mythbackend
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2009-07-25 16:59:08.142 Using runtime prefix = /usr
2009-07-25 16:59:08.142 DBHostName is not set in mysql.txt
2009-07-25 16:59:08.142 Assuming localhost
2009-07-25 16:59:08.142 DBUserName is not set in mysql.txt
2009-07-25 16:59:08.143 DBPassword is not set in mysql.txt
2009-07-25 16:59:08.143 DBName is not set in mysql.txt
2009-07-25 16:59:08.143 Empty LocalHostName.
2009-07-25 16:59:08.143 Using localhost value of media-pc
2009-07-25 16:59:08.143 Configuration::Load - Error parsing: /home/media/.mythtv/config.xml at line: 1  column: 1
2009-07-25 16:59:08.143 Configuration::Load - Error Msg: unexpected end of file
2009-07-25 16:59:08.147 New DB connection, total: 1
2009-07-25 16:59:08.150 Connected to database '' at host: localhost
2009-07-25 16:59:08.151 Closing DB connection named 'DBManager0'
2009-07-25 16:59:08.151 Connected to database '' at host: localhost
2009-07-25 16:59:08.152 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.152 Current Schema Version: (none)
2009-07-25 16:59:08.152 DataDirectProcessor::FixProgramIDs() -- begin
2009-07-25 16:59:08.153 New DB DataDirect connection
2009-07-25 16:59:08.153 Connected to database '' at host: localhost
2009-07-25 16:59:08.153 DB Error (Fixing program ids in recorded):
Query was:
UPDATE recorded SET programid=CONCAT(SUBSTRING(programid, 1, 2),                      '00', SUBSTRING(programid, 3)) WHERE length(programid) = 12
Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.154 New DB connection, total: 2
2009-07-25 16:59:08.154 Connected to database '' at host: localhost
2009-07-25 16:59:08.154 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'BackupDBLastRunStart' AND hostname is NULL;
Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.154 DB Error (SaveSettingOnHost query failure: ):
Query was:
INSERT INTO settings (value,data,hostname ) VALUES ( 'BackupDBLastRunStart', '2009-07-25 16:59:08', NULL );
Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.155 DB Error (StorageGroup::StorageGroup()):
Query was:
SELECT DISTINCT dirname FROM storagegroup WHERE groupname = 'DB Backups' AND hostname = 'media-pc'
Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.155 New DB connection, total: 3
2009-07-25 16:59:08.155 Connected to database '' at host: localhost
2009-07-25 16:59:08.156 SG(DB Backups) Error: Directory value for Default Storage Group is empty.  Using hardcoded default value of '/var/lib/mythtv/recordings'
2009-07-25 16:59:08.156 Backing up database to file: /var/lib/mythtv/recordings/--20090725165908.sql
2009-07-25 16:59:08.178 DBUtil Error: Error backing up database: mysqldump --defaults-extra-file='/tmp/mythtv_db_backup_conf_r8GhWF' --host='localhost' --user='' --add-drop-table --add-locks --allow-keywords --complete-insert --extended-insert --lock-tables --no-create-db --quick '' > '/var/lib/mythtv/recordings/--20090725165908.sql' 2>/dev/null (512)
2009-07-25 16:59:08.178 DB Error (Clear setting):
Query was:
DELETE FROM settings WHERE value = 'BackupDBLastRunEnd' AND hostname is NULL;
Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.178 DB Error (SaveSettingOnHost query failure: ):
Query was:
INSERT INTO settings (value,data,hostname ) VALUES ( 'BackupDBLastRunEnd', '2009-07-25 16:59:08', NULL );
Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.179 No current database version. Auto upgrading
2009-07-25 16:59:08.179 Newest Schema Version : 1214
2009-07-25 16:59:08.179 ERROR: Unable to create schemalock table: Driver error was [2/1046]:
QMYSQL3: Unable to execute query
Database error was:
No database selected

2009-07-25 16:59:08.179 Couldn't upgrade database to new schema
media@media-pc:~$ 
```

thanks for any help guys

---

### Post by klc5555 on 2009-07-25
My guess would be your mythconverg database is partly or completely hosed; or that there is some other MySQL problem (less likely).

You might want to check whether mythconverg.sql still exists. If so, you might want to run (sudo) the repair/optimize script from a terminal to see whether it makes a difference. You may wish to run mysqlcheck to see whether it finds problems --described here: [http://www.mythtv.org/wiki/Database_errors](http://www.mythtv.org/wiki/Database_errors)   In mythbuntu you'll need to run it sudo and use your mysql password rather than the dummy one shown in the guide. 

If your mythconverg is really hosed, you may end up having to drop your database (make a new backup of it first, just in case) and restoring from an earlier backup as described here: [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance)
and here: [http://www.mythtv.org/wiki/Backup_your_database](http://www.mythtv.org/wiki/Backup_your_database)

If you never made a backup (bummer :( ) Mythbuntu may still have saved your bacon (or most of it):  it's supposed to drop a mythconverg backup once weekly in /var/backups Check and see whether it's done so and one can be used for recovery as described in the cited docs above.

---

### Post by ianhaycox on 2009-07-26
Have you checked if /home/media/.mythtv/config.xml exists or is corrupted ?

It should look something like this:

```

<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>6a3933a3-51a2-41e2-88b0-820f9bb411b8</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>xxxxxxx</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>


```

---

### Post by spleblem on 2009-07-27
had a look at the config file at it seems to be a blank file
does this mean it is corrupt?
how would i go about fixing this?

---

### Post by ianhaycox on 2009-07-27
Yep, it's corrupt. If you have a backup, restore it from there, otherwise copy mine and change the database info to match /etc/mythtv/mysql.txt.  Don't know about the Media Renderer bit ?

Have you got any other frontends or frontend users ? Copy their config.xml

Last resort would be to mv .mythtv .mythtv-old and run mythtv-setup again and hope it recreates everything.

---

