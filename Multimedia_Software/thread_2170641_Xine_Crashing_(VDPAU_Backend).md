---
title: "Xine Crashing (VDPAU Backend)"
date: 2013-08-27
forum: Multimedia Software
---

### Post by and003 on 2013-08-27
I recently purchased a copy of *G.I. Joe: Retaliation* to watch on my computer using the Xine video player. However, I have run into an irritating snag. Everytime I try to run Xine, it keeps crashing. I've searched the other records of Xine crashing for others at this site, but found nothing to fit my particular situation. To understand what I'm dealing with, I am enclosing the record of an attempt I made to run Xine through a terminal window.

******

and003@Tiger-Ubuntu-MS-7309:~$ xine
This is xine (X11 gui) - a free video player v0.99.7.
(c) 2000-2010 The xine Team.
Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
vo_vdpau: Can't create vdp device : No vdpau implementation.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (XVideo)
  Minor opcode of failed request:  17 ()
  Serial number of failed request:  2620
  Current serial number in output stream:  2620
and003@Tiger-Ubuntu-MS-7309:~$

---

### Post by mc4man on 2013-08-27
open xine > settings > setup (or alt+s on xine window),  & pick another video output driver as in screen, try xv or opengl2

---

### Post by and003 on 2013-08-29
> **mc4man said:**
> open xine > settings > setup (or alt+s on xine window),  & pick another video output driver as in screen, try xv or opengl2
I'd do that, but everytime I tried to open Xine, it crashed, leading to the output you saw in my post. As such, it doesn't stay open long enough for me to change the settings. Not that it matters now, because the problem appears to have ended. I tried opening Xine today and it didn't crash. I'm not sure how it happened, but the problem apparently disappeared after my most recent Ubuntu operating system update. Even so, I'd like to know what to do if this somehow happens again.

---

### Post by mc4man on 2013-08-29
> **and003 said:**
> I'd do that, but everytime I tried to open Xine, it crashed, leading to the output you saw in my post. As such, it doesn't stay open long enough for me to change the settings. Not that it matters now, because the problem appears to have ended. I tried opening Xine today and it didn't crash. I'm not sure how it happened, but the problem apparently disappeared after my most recent Ubuntu operating system update. Even so, I'd like to know what to do if this somehow happens again.
Well if it was something that could be fixed in xine's pref's & it wouldn't stay open, ect. then 
```
gedit ~/.xine/config
```

---

