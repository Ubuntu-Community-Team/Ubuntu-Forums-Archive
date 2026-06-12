---
title: "F-Spot Wont Open"
date: 2008-05-16
forum: Multimedia Software
---

### Post by castusalbuscor on 2008-05-16
I've been trying to open F-Spot for the past three days, but alas its not playing nice. I am not sure what's wrong.
Not sure what sort of information would be helpful in this case other than I am running Ubuntu 8.04 on a Dell Inspiron 1100, with 1GB of RAM.

---

### Post by squaregoldfish on 2008-05-17
Try launching FSpot from a console (f-spot), and see if anything interesting appears there.

I often find I need to run ```
dbus-launch f-spot
```but I've never figured out why.

Steve.

---

### Post by castusalbuscor on 2008-05-17
> **squaregoldfish said:**
> Try launching FSpot from a console (f-spot), and see if anything interesting appears there.

I often find I need to run ```
dbus-launch f-spot
```but I've never figured out why.

Steve.


I gave it a try, typing bith **f-spot** and **dbus-launch f-spot** in terminal and I got this error:
```
elie@Torchwood-Ubuntu:~$ dbus-launch f-spot
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

### Post by abhilashkumar on 2008-05-21
> **squaregoldfish said:**
> Try launching FSpot from a console (f-spot), and see if anything interesting appears there.

I often find I need to run ```
dbus-launch f-spot
```but I've never figured out why.

Steve.

**I face this problem too! I tried in the console and this is what I got:**


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

---

### Post by Tha-Fox on 2008-07-03
Has anyone found any solution to this? I have this problem too and I'm running Gutsy.

There's no problem anymore. I upgraded to Hardy and now it works.

---

### Post by boilerbots on 2008-08-17
had this problem and it wasn't that I needed to upgrade my database.

After trying several things the solution that worked for me was to first uninstall f-spot. Then completely delete what remained in the "/usr/lib/f-spot" directory. Then install the f-spot package again and it worked.

A quick experiment of putting back the extensions caused it to crash again, so it looks like it could be something in the extensions directory.

I am happing I can finally get my photos synced up again.

---

### Post by daporgue on 2008-10-26
Hi guys, I had the same problem related with dbus and the option to run dbus-launch-f-spot didn't help, so what I did and IT WORKS, was, just go to Synaptic and mark for re installation dbus packages, also uninstall f-spot after that and install it again. Now try to run it ;-)

---

### Post by MeanStreak on 2008-12-08
I'm having the same problem - since upgrading to 8.10. Frustrating because F-Spot was my means to import photos from my camera. I have tried completely removing and re-installing in Synaptic but still it fails to initialise. This is a core app in Ubuntu's stable - this needs to be fixed.

---

### Post by WhiteHorse on 2009-02-16
Same problem here.
F-Spot 0.5.0.3
Ubuntu: 8.10

> [Info  10:57:47.101] Initializing DBus
[Debug 10:57:47.332] DBusInitialization took 0.207088s
[Info  10:57:47.332] Initializing Mono.Addins
[Debug 10:57:47.740] Mono.Addins Initialization took 0.40761s
[Info  10:57:47.753] Starting new FSpot server

Unhandled Exception: Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 

I tried completely removing f-spot, reinstalling dbus, reinstalling f-spot, rebuilding the database, deleting the database.

It does run as root after throwing an error 
> ** No session dbus found. Starting one **
[Info  11:01:51.763] Initializing DBus
[Info  11:01:51.930] Initializing Mono.Addins
[Info  11:01:52.193] Starting new FSpot server
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
[Info  11:01:59.066] Starting BeagleService
[Info  11:01:59.066] Hack for gnome-settings-daemon engaged
[Info  11:02:05.921] Exiting

---

### Post by strfish7 on 2009-02-22
Having the same problem....anybody got any ideas?

---

### Post by directhex on 2009-02-23
To me, it sounds like database corruption (the DB is stored in ~/.gnome2/f-spot/photos.db)

But if deleting that still doesn't help, then I'm at a loss

---

### Post by WhiteHorse on 2009-02-25
I fixed this. My problem was my disk was full. Just run 

df

and if you see 100% usage on a disk, then it's probably the disk-full issue.

---

### Post by chiaseth on 2009-04-30
I had the same exact problem, here's what I did to fix it:

1. Complete Removal F-Spot in Synaptic.
2. Reinstall  dbus in Synaptic.
3. rm -rf ~/.gnome2/f-spot/*
4. Install F-Spot in Synaptic.

Ok, so it's a little bit of slash-and-burn, but it worked. I didn't have anything to lose in my F-spot DB.

---

