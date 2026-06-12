---
title: "MythwWeather database problems."
date: 2010-03-20
forum: Mythbuntu
---

### Post by xinix on 2010-03-20
I have been unable to get mythweather working on my system.  I get errors about tables not existing in the database. I am having this issue on both an old database as well as on a fresh new test installation (on a different system). I'm using MythTV 0.22+fixes.

How can I manually create the required tables and field so that I can get this plugin working?

Thanks

Here are the errors I'm getting:

```
2010-03-20 11:25:48.214 Error preparing query: SELECT DISTINCT wss.sourceid, source_name, update_timeout, retrieve_timeout, path, author, version, email, types FROM weathersourcesettings wss LEFT JOIN weatherdatalayout wdl ON wss.sourceid = wdl.weathersourcesettings_sourceid WHERE hostname = :HOST;
2010-03-20 11:25:48.214 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.weathersourcesettings' doesn't exist

2010-03-20 11:25:48.214 DB Error (Finding weather source scripts for host):
Query was:
SELECT DISTINCT wss.sourceid, source_name, update_timeout, retrieve_timeout, path, author, version, email, types FROM weathersourcesettings wss LEFT JOIN weatherdatalayout wdl ON wss.sourceid = wdl.weathersourcesettings_sourceid WHERE hostname = ?;
Bindings were:
:HOST=vampiro
No error type from QSqlError?  Strange...
2010-03-20 11:25:48.214 Error preparing query: SELECT DISTINCT location, weathersourcesettings_sourceid,                 weatherscreens.units, weatherscreens.screen_id FROM weatherdatalayout,weatherscreens WHERE weatherscreens.screen_id = weatherscreens_screen_id AND       weatherscreens.hostname = :HOST
2010-03-20 11:25:48.214 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.weatherdatalayout' doesn't exist

2010-03-20 11:25:48.215 DB Error (Finding weather sources for this host):
Query was:
SELECT DISTINCT location, weathersourcesettings_sourceid,                 weatherscreens.units, weatherscreens.screen_id FROM weatherdatalayout,weatherscreens WHERE weatherscreens.screen_id = weatherscreens_screen_id AND       weatherscreens.hostname = ?
Bindings were:
:HOST=vampiro
No error type from QSqlError?  Strange...
2010-03-20 11:25:48.241 Loading window theme from /home/xinix/.mythtv/themes/Algae/weather-ui.xml
2010-03-20 11:25:48.271 Error preparing query: SELECT DISTINCT wss.sourceid, source_name, update_timeout, retrieve_timeout, path, author, version, email, types FROM weathersourcesettings wss LEFT JOIN weatherdatalayout wdl ON wss.sourceid = wdl.weathersourcesettings_sourceid WHERE hostname = :HOST;
2010-03-20 11:25:48.271 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.weathersourcesettings' doesn't exist

2010-03-20 11:25:48.271 DB Error (Finding weather source scripts for host):
Query was:
SELECT DISTINCT wss.sourceid, source_name, update_timeout, retrieve_timeout, path, author, version, email, types FROM weathersourcesettings wss LEFT JOIN weatherdatalayout wdl ON wss.sourceid = wdl.weathersourcesettings_sourceid WHERE hostname = ?;
Bindings were:
:HOST=vampiro
No error type from QSqlError?  Strange...
2010-03-20 11:25:48.271 Error preparing query: SELECT DISTINCT location, weathersourcesettings_sourceid,                 weatherscreens.units, weatherscreens.screen_id FROM weatherdatalayout,weatherscreens WHERE weatherscreens.screen_id = weatherscreens_screen_id AND       weatherscreens.hostname = :HOST
2010-03-20 11:25:48.272 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.weatherdatalayout' doesn't exist

2010-03-20 11:25:48.272 DB Error (Finding weather sources for this host):
Query was:
SELECT DISTINCT location, weathersourcesettings_sourceid,                 weatherscreens.units, weatherscreens.screen_id FROM weatherdatalayout,weatherscreens WHERE weatherscreens.screen_id = weatherscreens_screen_id AND       weatherscreens.hostname = ?
Bindings were:
:HOST=vampiro
No error type from QSqlError?  Strange...
2010-03-20 11:25:48.272 Error preparing query: SELECT screen_id, container, units, draworder FROM weatherscreens  WHERE hostname = :HOST ORDER BY draworder;
2010-03-20 11:25:48.272 Driver error was [2/1146]:
QMYSQL3: Unable to prepare statement
Database error was:
Table 'mythconverg.weatherscreens' doesn't exist

2010-03-20 11:25:48.272 DB Error (Selecting weather screens.):
Query was:
SELECT screen_id, container, units, draworder FROM weatherscreens  WHERE hostname = ? ORDER BY draworder;
Bindings were:
:HOST=vampiro
No error type from QSqlError?  Strange...
```

---

### Post by ian dobson on 2010-03-20
Hi,

Have a look here:- [http://itstumbles.blogspot.com/](http://itstumbles.blogspot.com/) 

Regards
Ian Dobson

---

### Post by xinix on 2010-03-20
Ian,  Thank you!

That got me on the right track.  I had to add a field called 'updated' in the 'weathersourcesettings' table.  Otherwise, I followed the instructions you pointed me to.  Here's a direct link to the page with just the mythweather info, in case anyone else needs this.  [http://itstumbles.blogspot.com/2009/03/mythtv-rebuild.html]("http://itstumbles.blogspot.com/2009/03/mythtv-rebuild.html")

I tried different searches for myhtweather + database but none gave me this site.  I'm glad you knew about it.

Thanks.

---

