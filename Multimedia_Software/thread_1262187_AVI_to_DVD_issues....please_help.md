---
title: "AVI to DVD issues....please help"
date: 2009-09-09
forum: Multimedia Software
---

### Post by riminicat on 2009-09-09
A friend of mine at work has been trying to convert an AVI to DVD for a week or so now.  He got sick of Windows and deleted, and has never used linux before.  Any way he's been messing with programs and hasn't had a whole lot of issues, just bluetooth, HDMI, and the AVI issue are the only things keeping him from liking Ubuntu.  Here is a copy of the message he gets when he tries to convert an AVI to a DVD, if you know how to fix this, let me know please.

> STAT: fixed 12915 VOBUS 
WARN: The use of jumppad requires a menu; creating a dummy ENGLISH menu
INFO: dvdauthor creating table of contents
INFO: Scanning /tmp/dvd/VIDEO_TS/VTS_01_0.IFO
Start preview
Executing command: xine "dvd://tmp/dvd"
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
libdvdread: Encrypted DVD support unavailable.
libdvdread: Couldn't find device name.

---

### Post by Earl_Maroon on 2009-09-09
You will probably need libdvdcss2 from the repos.

---

### Post by riminicat on 2009-09-12
I told him to try it and it worked, thanks for the help.

---

