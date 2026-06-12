---
title: "Upgraded to 12.04, now any video is a &quot;negative&quot; AMD/ATI"
date: 2013-01-13
forum: Multimedia Software
---

### Post by penst8grad on 2013-01-13
Finally upgraded to 12.04 and I thought everything was good, but alas it wasn't.  I'm the recorder/editor for team videos and provide film for the coaches.  Tonight I went to process some video and noticed that the video is exceptionally dark, almost black.  But where I can see anything it is almost like a film negative.

I tried installing the newest AMD/ATI driver, but there was no change.  Here's a fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 5450     
OpenGL version string: 4.2.11931 Compatibility Profile Context

Strangely, when I use VLC if I force it to X11 it works.  Unfortunately I cannot process that way.

Any suggestions?

---

### Post by penst8grad on 2013-01-14
I fixed the problem.  Don't know if I solved it or just found a workaround.  
Added blacklist fglrx and blacklist fglrx* to /etc/modprobe.d/blacklist-local.conf and it's working now.

---

