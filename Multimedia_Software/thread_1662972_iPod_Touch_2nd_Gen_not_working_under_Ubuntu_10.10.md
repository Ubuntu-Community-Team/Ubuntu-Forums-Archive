---
title: "iPod Touch 2nd Gen not working under Ubuntu 10.10"
date: 2011-01-09
forum: Multimedia Software
---

### Post by Kasami on 2011-01-09
Hey I've been trying things all day. My iPod was working on 10.04 but after the upgrade it has stopped working.

When I plug it in it asks me if I want to launch it in Shotwell and Rhythmbox.

**Shotwell** and it shows none of the pictures which are on it.

**Rhythmbox** displays the iPod icon for it but shows no songs.

**Banshee** shows the iPod, shows that 11.3 gigs of it has been used but does not see it as usable media. Screenshot below.

**gtkpod** gives me the error:
```
iPod Database Import Failed: 'Error during XML parsing of file /home/kasami/.gvs/Mr. iPod/iTunes_Control/iTunes/PlayCounts.plist
```

**Nautilus** displays the files of the iPod but does not mount it in /media as it seems it should.

Version 2.2.1 firmware.

Thanks in advance, not sure what specific information you need.

---

### Post by Kasami on 2011-01-09
lsusb

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5986:0180 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:1293 Apple, Inc. iPod Touch 2.Gen
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ocgstyles on 2011-01-15
same problem here, except that i'm using 1st gen ipon touch.  started banshee from command line with --debug option.  errors:

```
/home/xxxxxx/.gvfs/ipod/iTunes_Control/iTunes/PlayCounts.plist:1: parser error : Start tag expected, '<' not found
bplist00
^
[3 Warn  18:27:35.437] iPod database could be loaded, creating a new one - GLib.GException: Error during XML parsing of file /home/xxxxxx/.gvfs/ipod/iTunes_Control/iTunes/PlayCounts.plist (in `libgpod-sharp')
  at GPod.ITDB.itdb_parse_wrapped (System.String mountpoint) [0x00000] in <filename unknown>:0 
  at GPod.ITDB..ctor (System.String mountpoint) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.AppleDevice.AppleDeviceSource.LoadFromDevice (Boolean refresh) [0x00000] in <filename unknown>:0 
/home/xxxxxx/.gvfs/ipod/iTunes_Control/iTunes/PlayCounts.plist:1: parser error : Start tag expected, '<' not found
bplist00
```

---

### Post by CryptSphinx on 2011-01-15
I'm also experiencing the same problems , searches on google suggest a know problem on Kubuntu with Amarok (seems to be so) but I'm also using Ubuntu on this computer and having the above error in gtkpod .
Device is not syncing in banshee or rhythmbox

---

### Post by CryptSphinx on 2011-01-17
Feeling enraged I booted  into XP (first time in months since I discovered a lin replacement for sonicstage) - similar probs there - after a re-initialisation its playing friendly with Clementine. 

So it appears the problem was the device ... for me.

---

### Post by dannykopping on 2011-02-17
Renaming or removing the PlayCounts.plist file worked file for me...

---

### Post by tmeier on 2011-03-16
> **dannykopping said:**
> Renaming or removing the PlayCounts.plist file worked file for me...

Made a copy of PlayCounts.plist and then deleted it from my first Generation iPod Touch ios 2.2.1 and then restarted RhythmBox and everything worked fine.

---

