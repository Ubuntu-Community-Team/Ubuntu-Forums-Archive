---
title: "F-spot Photo Manager won't open"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by DJ_Peng on 2007-10-01
I imported some pictures from my digital camera today (which finally worked in the Gutsy beta, it never did under Feisty), but when I tried to get into f-spot (version 0.4.0-0ubuntu3) it wouldn't start up. I tried purging it and reinstalling it via apt, but when I tried to launch it from the Terminal I got > peng@IceBox:~$ f-spot
Initializing Mono.Addins
Starting new FSpot server
Updating F-Spot Database
Updated database from version NULL to 1
Updated database from version 1 to 2
Updated database from version 2 to 3

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
Does anyone have any thoughts about what may be going wrong?

---

### Post by eternalperson on 2007-10-02
> **DJ_Peng said:**
> I imported some pictures from my digital camera today (which finally worked in the Gutsy beta, it never did under Feisty), but when I tried to get into f-spot (version 0.4.0-0ubuntu3) it wouldn't start up. I tried purging it and reinstalling it via apt, but when I tried to launch it from the Terminal I got Does anyone have any thoughts about what may be going wrong?

F-Spot 0.4.0 is very buggy. I've had similar issues with it. Try restarting or try using a different photo manager. 
I tried it in openSUSE 10.3 RC1 and it couldn't even import photos. In Ubuntu it imported 'em and then crashed.

---

### Post by DJ_Peng on 2007-10-02
Ah, ok. Thanks for the info. Hopefully they'll have something better when Gutsy goes gold.

---

