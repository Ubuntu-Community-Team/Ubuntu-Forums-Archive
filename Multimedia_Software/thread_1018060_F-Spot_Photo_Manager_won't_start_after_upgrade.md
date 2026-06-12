---
title: "F-Spot Photo Manager won't start after upgrade"
date: 2008-12-21
forum: Multimedia Software
---

### Post by sirlancelot on 2008-12-21
I've upgraded to Intrepid 8.10, so I'm using F-Spot 0.5.0.3. a new version for me (I think my previous version was 0.4.4).

Now, F-Spot doesn't start up at all. Here's the output when I try to run it from a terminal:```
mpietz@mpietz-dt-ubuntu:~$ f-spot
[Info  15:06:29.282] Initializing DBus
[Info  15:06:29.387] Initializing Mono.Addins
[Info  15:06:29.527] Starting new FSpot server
Updating F-Spot Database
Updated database from version 14 to 15

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: table "photos" already exists
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

```

It just hangs after that. I've let it run for over 5 minutes thinking that it is updating the database with the "md5_sum" column that was added in the version. But nothing.

I have ~2500+ images, with at least 2 tags per image. The "photos.db" is 3.1mb.

F-Spot does work if I rename "photos.db". It creates a new empty one and starts fine, with no pictures.

Thanks for any assistance.

---

### Post by WhiteHorse on 2009-02-16
Same type of problem here. The damn prog worked yesterday and today it's totally hosed. From the command line I get:

> [Info  09:59:53.267] Initializing DBus
[Info  09:59:53.428] Initializing Mono.Addins
[Info  09:59:53.683] Starting new FSpot server

Unhandled Exception: Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

I've deleted the database, tried to dump it to a flat file and reimport it, etc. I've reinstalled f-spot and sqlite, sqlite3.

F-Spot: 0.5.0.3
Ubuntu: 8.10

---

