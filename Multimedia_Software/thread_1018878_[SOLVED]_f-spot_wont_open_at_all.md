---
title: "[SOLVED] f-spot wont open at all"
date: 2008-12-22
forum: Multimedia Software
---

### Post by dog-soldier on 2008-12-22
im using ubuntu 8.04 since i installed it f-spot wont open. i have uninstalled and reinstalled and still the same. i had to install digikam to get my pics off my camera but would like to try out f-spot. 
anyone have any ideas?
also i did a search and seen to run f-spot in a terminal so here is what i got

```
dogsoldier@dogsoldier-desktop:~$ f-spot
Starting new FSpot server
XXXXX
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
XXXXX
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot

```

---

### Post by RomanIvanov on 2008-12-22
problem with SQLite DB driver

"sudo apt-get install sqlite" should be what you're looking for...

---

### Post by dog-soldier on 2008-12-22
> **RomanIvanov said:**
> problem with SQLite DB driver

"sudo apt-get install sqlite" should be what you're looking for...

ran that and got 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sqlite is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by directhex on 2008-12-22
rm ~/.gnome2/f-spot/photos.db

---

### Post by dog-soldier on 2008-12-22
> **directhex said:**
> rm ~/.gnome2/f-spot/photos.db

that did the trick..thanks:)

---

### Post by directhex on 2008-12-22
> **dog-soldier said:**
> that did the trick..thanks:)

Send your thanks & adulation to [http://childsplaycharity.org/](http://childsplaycharity.org/) on my behalf.

---

