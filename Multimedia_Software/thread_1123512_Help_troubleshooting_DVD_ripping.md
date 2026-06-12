---
title: "Help troubleshooting DVD ripping"
date: 2009-04-12
forum: Multimedia Software
---

### Post by ant2ne on 2009-04-12
I'm building a library of my DVDs to play from my XBMC.

No matter what device I use for ripping. It stops at a mere few chapters in. It performs a good quality rip, but just stops.

I've used
xDVDshrink
HandBrake
k9copy

```
ant2ne@2ne-buntu:~$ sudo apt-get install libdvdcss2
[sudo] password for ant2ne: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

I have no hard drive partition less than 50gigs. So I'm not running out of space.

Only thing seemingly relevant from dmesg is
```
[46059.523177] attempt to access beyond end of device
[46059.523178] sr0: rw=0, want=16279892, limit=2097151

```

Any idea what I'm doing wrong? 

Thanks

---

### Post by blastus on 2009-04-12
Just use DVDFab Decrypter in Wine.

---

### Post by ant2ne on 2009-04-25
> **blastus said:**
> Just use DVDFab Decrypter in Wine.That is a solution. But DVDFab is not freeware. Any other suggestions?

---

### Post by andrew.46 on 2009-04-25
Hi ant2ne,

For simple ripping, as opposed to ripping *and* transcoding, you could try using the commandline vobcopy. To mirror an entire DVD simply use:

```
vobcopy -m
```

I have always found vobcopy to be reasonably robust although it will fail if libdvdcss fails. If this works on your DVD then of course there is the transcoding...

All the best,

Andrew

---

### Post by mc4man on 2009-04-25
Vobcopy would be a good choice, if for nothing else may show why the rips are failing 
Don't remember if a -v to command (verbose) adds any add. info
Like
vobcopy -v -m  (note this presumes the drive is /dev/scd0 or /dev/dvd, otherwise
vobcopy -v -m -i /dev/scd1

I actually set vobcopy up to be an autorun choice (don't use as the current default but available from r.click on dvd icon or holding down shift while inserting pop up, though can be made the default action on dvd insertion

In that case the autorun choice calls a script instead of vobcopy itself. (works from any drive and or multiple rips at once - needs a couple seconds pause before inserting next disk.


```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m -F 16" /media/* 

```

or output other than home folder
```
#!/bin/bash
gnome-terminal -e "vobcopy -v -m -F 16 -o /home/doug/Videos" /media/* 
```

---

