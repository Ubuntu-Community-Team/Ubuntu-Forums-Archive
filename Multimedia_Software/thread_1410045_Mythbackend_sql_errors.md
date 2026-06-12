---
title: "Mythbackend sql errors"
date: 2010-02-18
forum: Multimedia Software
---

### Post by kempy1000 on 2010-02-18
Hi,

I have noticed these errors in my mythbackend.log can anyone suggest what is causing them?

I reset the log and rebooted the system and this is the log just after booting.

(I think they maybe linked to a problem with my machine not sutting down automatically)

```

2010-02-18 00:42:05.008 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:05.080 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:05.122 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=22592, :SOURCEID=1, :TRANSPORTID=20544
No error type from QSqlError?  Strange...
2010-02-18 00:42:05.223 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:05.256 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:05.289 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5888, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:05.374 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:05.406 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:05.440 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=6016, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:05.474 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:05.507 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:05.540 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26304, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:05.826 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:05.857 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:05.891 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26560, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:06.177 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:06.208 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:06.241 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5696, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:06.879 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:06.908 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:06.942 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8577, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:07.178 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:07.219 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:07.261 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8570, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:07.354 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:07.395 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:07.437 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=6784, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:07.681 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:07.720 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:07.762 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8576, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:07.855 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:07.896 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:07.938 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5632, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:08.073 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:08.130 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:08.189 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=23680, :SOURCEID=1, :TRANSPORTID=20544
No error type from QSqlError?  Strange...
2010-02-18 00:42:08.358 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:08.423 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:08.523 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=22976, :SOURCEID=1, :TRANSPORTID=20544
No error type from QSqlError?  Strange...
2010-02-18 00:42:08.557 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:08.590 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:08.623 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8637, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:08.833 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:08.882 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:08.974 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5824, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:09.075 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:09.175 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:09.275 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=6848, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:09.376 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:09.475 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:09.584 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8570, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:09.745 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:09.793 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:09.835 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=17472, :SOURCEID=1, :TRANSPORTID=16520
No error type from QSqlError?  Strange...
2010-02-18 00:42:09.877 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:09.919 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:09.961 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26176, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.004 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.103 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.170 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=6720, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.246 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.279 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.313 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8772, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.347 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.380 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.414 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=23104, :SOURCEID=1, :TRANSPORTID=20544
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.447 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.481 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.514 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26624, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.548 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.581 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.615 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26688, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.649 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.682 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.715 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26240, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.801 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.832 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.866 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=6912, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:10.900 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:10.933 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:10.967 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5632, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:11.001 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:11.034 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:11.076 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=6784, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:11.118 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:11.159 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:11.201 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5952, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:11.244 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:11.319 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:11.370 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=17608, :SOURCEID=1, :TRANSPORTID=16520
No error type from QSqlError?  Strange...
2010-02-18 00:42:11.412 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:11.478 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:11.545 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=26368, :SOURCEID=1, :TRANSPORTID=24640
No error type from QSqlError?  Strange...
2010-02-18 00:42:11.704 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:11.796 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:11.896 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=8637, :SOURCEID=1, :TRANSPORTID=8203
No error type from QSqlError?  Strange...
2010-02-18 00:42:12.022 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:12.096 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:12.464 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=5952, :SOURCEID=1, :TRANSPORTID=4168
No error type from QSqlError?  Strange...
2010-02-18 00:42:12.732 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:12.764 Driver error was [2/2006]:
QMYSQL3: Unable to prepare statement
Database error was:
MySQL server has gone away

2010-02-18 00:42:12.798 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = ?   AND       networkid        = ?   AND       transportid      = ? AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = ?
Bindings were:
:NETWORKID=9018, :SERVICEID=17608, :SOURCEID=1, :TRANSPORTID=16520
No error type from QSqlError?  Strange...
2010-02-18 00:42:12.884 Error preparing query: SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = :SERVICEID   AND       networkid        = :NETWORKID   AND       transportid      = :TRANSPORTID AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = :SOURCEID
2010-02-18 00:42:12.989 mythbackend version: trunk [23548] www.mythtv.org
2010-02-18 00:42:13.141 Using runtime prefix = /usr
2010-02-18 00:42:13.174 Using configuration directory = /.mythtv
2010-02-18 00:42:13.208 Empty LocalHostName.
2010-02-18 00:42:13.241 Using localhost value of chimera
2010-02-18 00:42:13.282 New DB connection, total: 1
2010-02-18 00:42:13.317 Unable to connect to database!
2010-02-18 00:42:13.350 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-02-18 00:42:15.942 UPnPautoconf() - No UPnP backends found
2010-02-18 00:42:15.983 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-02-18 00:42:16.226 Deleting UPnP client...
2010-02-18 00:42:16.954 Failed to init MythContext, exiting.
2010-02-18 00:42:17.077 mythbackend version: trunk [23548] www.mythtv.org
2010-02-18 00:42:17.136 Using runtime prefix = /usr
2010-02-18 00:42:17.177 Using configuration directory = /.mythtv
2010-02-18 00:42:17.220 Empty LocalHostName.
2010-02-18 00:42:17.261 Using localhost value of chimera
2010-02-18 00:42:17.310 New DB connection, total: 1
2010-02-18 00:42:17.345 Unable to connect to database!
2010-02-18 00:42:17.378 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

................................................................................
2010-02-18 00:42:19.970 UPnPautoconf() - No UPnP backends found
2010-02-18 00:42:20.003 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2010-02-18 00:42:20.204 Deleting UPnP client...
2010-02-18 00:42:20.881 Failed to init MythContext, exiting.
2010-02-18 00:42:21.004 mythbackend version: trunk [23548] www.mythtv.org
2010-02-18 00:42:21.046 Using runtime prefix = /usr
2010-02-18 00:42:21.079 Using configuration directory = /.mythtv
2010-02-18 00:42:21.114 Empty LocalHostName.
2010-02-18 00:42:21.147 Using localhost value of chimera
2010-02-18 00:42:21.188 New DB connection, total: 1
2010-02-18 00:42:21.222 Unable to connect to database!
2010-02-18 00:42:21.255 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-02-18 00:42:23.083 mythbackend version: trunk [23548] www.mythtv.org
2010-02-18 00:42:23.131 Using runtime prefix = /usr
2010-02-18 00:42:23.223 Using configuration directory = /.mythtv
2010-02-18 00:42:23.316 Empty LocalHostName.
2010-02-18 00:42:23.407 Using localhost value of chimera
2010-02-18 00:42:23.490 New DB connection, total: 1
2010-02-18 00:42:23.551 Unable to connect to database!
2010-02-18 00:42:23.618 Driver error was [1/2002]:
QMYSQL: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

2010-02-18 00:42:23.686 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-02-18 00:42:23.736 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
SSDP::PerformSearch - did not write entire buffer.2010-02-18 00:42:23.886 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error

SSDP::PerformSearch - did not write entire buffer.
2010-02-18 00:43:09.979 mythbackend version: trunk [23548] www.mythtv.org
2010-02-18 00:43:10.056 Using runtime prefix = /usr
2010-02-18 00:43:10.157 Using configuration directory = /.mythtv
2010-02-18 00:43:10.269 Empty LocalHostName.
2010-02-18 00:43:10.366 Using localhost value of chimera
2010-02-18 00:43:10.915 New DB connection, total: 1
2010-02-18 00:43:11.797 Connected to database 'mythconverg' at host: localhost
2010-02-18 00:43:11.867 Closing DB connection named 'DBManager0'
2010-02-18 00:43:12.052 Connected to database 'mythconverg' at host: localhost
2010-02-18 00:43:12.767 Current MythTV Schema Version (DBSchemaVer): 1254
2010-02-18 00:43:13.844 MythBackend: Starting up as the master server.
2010-02-18 00:43:14.059 New DB connection, total: 2
2010-02-18 00:43:14.162 Connected to database 'mythconverg' at host: localhost
2010-02-18 00:43:15.052 New DB connection, total: 3
2010-02-18 00:43:15.158 Connected to database 'mythconverg' at host: localhost
2010-02-18 00:43:15.804 New DB scheduler connection
2010-02-18 00:43:15.906 Connected to database 'mythconverg' at host: localhost
2010-02-18 00:43:16.961 Enabling Upnpmedia rebuild thread.
2010-02-18 00:43:18.378 Main::Registering HttpStatus Extension
2010-02-18 00:43:18.484 Enabled verbose msgs:  important general
2010-02-18 00:43:18.678 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-18 00:43:19.572 Reschedule requested for id -1.
2010-02-18 00:43:20.907 Scheduled 44 items in 1.3 = 0.77 match + 0.56 place
2010-02-18 00:43:20.972 Seem to be woken up by USER
2010-02-18 00:43:21.999 MainServer::ANN Monitor
2010-02-18 00:43:22.307 adding: chimera as a client (events: 0)
2010-02-18 00:43:22.080 I'm idle now... shutdown will occur in 300 seconds.
2010-02-18 00:43:22.391 MainServer::ANN Monitor
2010-02-18 00:43:22.607 adding: chimera as a client (events: 1)
2010-02-18 00:43:24.643 MainServer::ANN Monitor
2010-02-18 00:43:24.734 adding: chimera as a client (events: 0)
2010-02-18 00:43:27.148 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2010-02-18 00:44:17.505 MainServer::ANN Playback
2010-02-18 00:44:17.555 adding: chimera as a client (events: 0)
2010-02-18 00:44:17.598 MainServer::ANN Monitor
2010-02-18 00:44:17.639 adding: chimera as a client (events: 1)
2010-02-18 00:44:36.495 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-02-18 00:46:06.571 Reschedule requested for id -1.
2010-02-18 00:46:06.819 Scheduled 44 items in 0.2 = 0.05 match + 0.20 place

```

Thanks
Chris

---

### Post by theDaveTheRave on 2010-02-23
kempy1000

looking at the time stamps on the error messages it looks as though the error are only occuring for about 5 minutes?

I wonder if the error messages are somehow due to the myth backend starting up before the mysql daemon has had a chance to get the server running?

You need to look to see what the time is between the first error and the first connect, and then see if this fits with the time for the system to come up fully??

don't know if that helps or not though, unfortunately I don't have myth on my system (maybe one day :( ), so I can't do a double check of my error logs, maybe another myth user out there will be able to help you out?

David

---

