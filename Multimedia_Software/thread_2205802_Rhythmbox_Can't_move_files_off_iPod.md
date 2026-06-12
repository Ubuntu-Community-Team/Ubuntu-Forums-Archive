---
title: "Rhythmbox: Can't move files off iPod"
date: 2014-02-16
forum: Multimedia Software
---

### Post by quark3 on 2014-02-16
I'm not entirely sure where to put this, but hey, here looks good.

Right to the point, I'm trying to use Rhythmbox to move my music off my iPod (Touch 4 (1) (MC540ZP), Jailbroken (1.1.9), 6.0.1(10A523)) to my PC so I can listen to it when I don't have access to my iPod. Trouble is, it crashes as soon as the operation is about to start. I've re-installed and installed all the codecs it wanted. Here's the log (when run from terminal):

```
connor@connor-desktop-ubuntu:~$ rhythmbox

#Rhythmbox open, begin reading iPod

** (rhythmbox:11568): WARNING **: Itdb_Track ID '1291' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1288' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1285' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1282' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1279' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1276' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1273' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1270' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1206' not found.


** (rhythmbox:11568): WARNING **: Itdb_Track ID '1169' not found.

libitdbprep: itdb_iphone_start_sync called with uuid=64739432208894f9ca54a7cfc860bfb1936bd853
itdb_iphone_start_sync: posted syncWillStart
itdb_iphone_start_sync: posted syncLockRequest
Locking for sync, attempt 0...
itdb_iphone_start_sync: posted syncDidStart

#Copy starts

** (rhythmbox:11568): CRITICAL **: itdb_splr_validate: assertion `at != ITDB_SPLAT_UNKNOWN' failed

(rhythmbox:11568): GLib-WARNING **: (/build/buildd/glib2.0-2.32.4/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)

(rhythmbox:11568): Rhythmbox-WARNING **: Could not write database to iPod: Unsupported checksum type

(rhythmbox:11568): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Segmentation fault (core dumped)

```

It can play songs from the iPod (Except for a few that were deleted from the iPod but show up in here for some reason) and I could live with it, but I don't want to.

I'm using Ubuntu 12.04 LTS with all the latest updates. (I think)

Thanks!

---

### Post by quark3 on 2014-03-07
I sure hope I'm allowed to bump this.

---

