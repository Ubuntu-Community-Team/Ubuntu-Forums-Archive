---
title: "f-spot doesn't launch"
date: 2010-06-29
forum: Multimedia Software
---

### Post by azertyh on 2010-06-29
hi,

f-spot doesn't launch when i click on its icon.

i try to launch f-spot in a terminal. no success. i got this message :

```
azertyh@azertyh-desktop:~$ f-spot
[Info  18:19:10.532] Initializing DBus
[Info  18:19:10.636] Initializing Mono.Addins
[Info  18:19:10.780] Starting new FSpot server (f-spot 0.6.1.5)
[Info  18:19:10.848] Updating F-Spot Database

Unhandled Exception: Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
```

i try gksudo f-spot. f-spot launchs. the message in the terminal is :

```
azertyh@azertyh-desktop:~$ gksudo f-spot
** No session dbus found. Starting one **
[Info  21:52:29.581] Initializing DBus
[Info  21:52:29.829] Initializing Mono.Addins
[Info  21:52:31.390] Starting new FSpot server (f-spot 0.6.1.5)
cleanup context
[Info  21:52:40.949] Starting BeagleService
[Info  21:52:40.968] Hack for gnome-settings-daemon engaged

(f-spot:1794): Gdk-WARNING **: losing last reference to undestroyed window

g gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
[Info  21:52:42.837] Exiting

```

and i find that with my wife's account, f-spot runs by clicking its icon (???).

any advice? how to launch f-spot with my account?

another information : i have ubuntu but i have installed and use xfce. f-spot doesn't launch neither in gnome nor in xfce.

---

### Post by azertyh on 2010-06-30
bring up my post.

---

### Post by azertyh on 2010-07-04
solved it by deleted the ~/.config/f-spot directory.
found the solution here [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/474644](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/474644)

---

### Post by shellbo on 2010-08-11
> **azertyh said:**
> solved it by deleted the ~/.config/f-spot directory.
found the solution here [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/474644](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/474644)
thanks, i came across this post the first time i went looking for the answer..
however, i don't really understand what it is exactly that i have to do and how i have to go about doing it...
a newbie-friendlier explanation would be very much appreciated!

---

