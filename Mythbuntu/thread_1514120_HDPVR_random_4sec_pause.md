---
title: "HDPVR random 4sec pause"
date: 2010-06-20
forum: Mythbuntu
---

### Post by MonsterMaxx on 2010-06-20
I have a new HDPVR hooked to my backend.
Backend is a Pentium 4 D 2.8 w/ 4GB of ram & 2tb of storage + the system drive.  Plus a PVR350 & PVR500.  

Frontend is an i7 w/ GTX465 4GB of ram and a SSD drive.  Very fast, Win Experience scores in the high 6s / low 7s.

Both running mythbuntu 10.04

All 'seems' fine except when watching something from the HDPVR which will give a random 3-4 sec pause.  Sometimes it'll play for 10-15min w/o interuption, sometimes it'll happen 2-3 times in a row.
It doesn't skip, drop frames or anything, there's just this pause in the playback.

Backend is doing nothing else (not recording other streams.)
Doesn't seem to matter if I'm recording/watching a HD channel or not, it's the HDPVR.  Does not occur w/ anything from the PVR350 or 500


How would I go about diagnosing and solving this problem?  

Thanks in advance.

---

### Post by ian dobson on 2010-06-20
Hi,

A GTX465 is a NVidia graphic card isn't it. Are you using the nvidia drivers or the open source ones? Do you have VDPAU enabled in mythtv?

My low power frontend (1GHz Core2Duo/9600gt) is more than enough to playback any content (BBC HD 1080p) when using VDPAU.

Regards
Ian Dobson

---

### Post by MonsterMaxx on 2010-06-22
yes, the 465 is a Nvidia card...latest greatest, but not absolute top of the line, screaming fast in windoze
Using Nvidia drivers.

VDPAU is active on the front end, tried all three (slim, normal and Hi), no difference.  3-4sec pause.

It's weird, sometimes it'll play for 15min or so w/o pausing, sometimes it'll do the 'pause' 2-3 times in a row.

Very annoying.

??

---

### Post by ian dobson on 2010-06-22
Hi,

What do you see in the backend log file?(/var/log/myth/frontend.log and /var/log/mythtv/backend.log) you don't need to include everything, just things that "look like errors/something out of the normal".

Maybe the NVidia drivers aren't quite upto speed with the newest graphic cards.

Regards
Ian Dobson

---

