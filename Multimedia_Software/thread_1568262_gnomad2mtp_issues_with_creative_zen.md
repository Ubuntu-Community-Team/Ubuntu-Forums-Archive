---
title: "gnomad2/mtp issues with creative zen"
date: 2010-09-04
forum: Multimedia Software
---

### Post by iceman30ad on 2010-09-04
OK my Zen plugs in and works just fine with banshee and rhythmbox but i liked using gnomad to handle  the player  tryed mounting unmounting un/re installing gnomad and libmtp8 

ran gnomad through terminal and heres the result
[PHP]chris@chris-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 041e:4157 Creative Technology, Ltd Zen (MTP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-laptop:~$ gnomad2

(~~~~~~~~~~

(gnomad2:8407): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnomad2:8407): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnomad2:8407): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnomad2:8407): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnomad2:8407): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Device 0 (VID=041e and PID=4157) is a Creative ZEN.
Queried Creative ZEN
Segmentation fault
chris@chris-laptop:~$ 
[/PHP]

any help greatly appreated 
and yes make it simple i am still a bit of a noob

---

### Post by iceman30ad on 2010-09-06
bump

---

### Post by filias on 2011-01-11
I have the same problem.

Also in rhythmbox I cant play the tracks in the player.

Any help would be great!

Thanks.

---

### Post by iceman30ad on 2011-01-12
found out gnomad has been depreated 

banshee has taken over  just install every thing banshee related and mtp related and it works

---

