---
title: "Have I stumbled apon a banshee bug?"
date: 2008-10-23
forum: Multimedia Software
---

### Post by morbid_bean on 2008-10-23
I will open banshee and double click a song and it will just crash. Im using the newest version (1.2.1)

```
Unhandled Exception: Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] 
```

---

### Post by morbid_bean on 2008-10-23
:frown:

---

### Post by directhex on 2008-10-23
> **morbid_bean said:**
> :frown:

Try #banshee on gimpnet, or file a bug. The forums are not frequented by anyone who can help.

---

