---
title: "Banshee-1 crashes in both Xubuntu 8.04 and Ubuntu 8.10"
date: 2008-10-21
forum: Multimedia Software
---

### Post by Sharule on 2008-10-21
Banshee-1 started crashing after playing only one song after an update on intrepid about a week ago.Funny thing is it started doing it in Hardy as well(they share the same /home folder btw.) I have no clue how to fix this. Here is the output from the banshee log after crashing.
> [Info  17:55:33.867] Running Banshee 1.2.1

(Nereid:10652): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
[Info  17:55:36.389] All services are started 2.224582s
[Info  17:55:38.368] nereid Client Started

Unhandled Exception: Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] 
Any help would be much appreciated. Thank you!

---

### Post by directhex on 2008-10-22
rm -r ~/.config/banshee*

And make sure you run it TWICE the first time (IIRC due to an error in the launch script it won't work the first time you try to run it)

---

