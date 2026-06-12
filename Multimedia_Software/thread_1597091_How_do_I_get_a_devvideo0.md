---
title: "How do I get a /dev/video0?"
date: 2010-10-14
forum: Multimedia Software
---

### Post by kerryhall on 2010-10-14
My webcam is detected under lsusb, but no /dev/video0 shows up. How do I get one?

---

### Post by alphacrucis2 on 2010-10-14
> **kerryhall said:**
> My webcam is detected under lsusb, but no /dev/video0 shows up. How do I get one?

I think that probably means it hasn't been claimed by a driver. What sort is it?

---

### Post by kerryhall on 2010-10-15
I got a ID 06a5:d800

Which looks like it can use this driver:
[http://sourceforge.net/projects/nw802/files/](http://sourceforge.net/projects/nw802/files/)

but I can't get that driver to build. :( Ugh

---

### Post by alphacrucis2 on 2010-10-15
> **kerryhall said:**
> I got a ID 06a5:d800

Which looks like it can use this driver:
[http://sourceforge.net/projects/nw802/files/](http://sourceforge.net/projects/nw802/files/)

but I can't get that driver to build. :( Ugh

Looks very old. The date says 2003 and I think that is for 2.4 kernels. You would need to find a version for 2.6 kernels. Some info on this thread might help:

[URL="http://ubuntuforums.org/showthread.php?t=621240"]http://ubuntuforums.org/showthread.php?t=621240
[/URL]


See post 13. Of course you would have to modify the instructions for your specific kernel version.

---

### Post by kerryhall on 2010-10-15
Thanks for the help! I followed those exact instructions from that post, but I get:

  CC [M]  /home/kerry/Desktop/nw802-2.4/nw8xx_jpgl.o
/home/kerry/Desktop/nw802-2.4/nw8xx_jpgl.c:114:33: error: macro "clamp" requires 3 arguments, but only 1 given

etc, which looks like it can be solved here:
[http://ubuntuforums.org/showthread.php?t=1080759](http://ubuntuforums.org/showthread.php?t=1080759)

See post number 3. But how do I apply that patch?

---

### Post by kerryhall on 2010-10-15
Ok, I applied the patch, it builds, installs, etc, but still no /dev/video0

Perhaps I was wrong about the driver

[https://bbs.archlinux.org/viewtopic.php?id=83105](https://bbs.archlinux.org/viewtopic.php?id=83105)

---

### Post by kerryhall on 2010-10-15
It looks like I need this one: 

[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44)

But I get the same build error as here:

[http://forums.linuxmint.com/viewtopic.php?f=49&t=22991&start=0](http://forums.linuxmint.com/viewtopic.php?f=49&t=22991&start=0)

---

### Post by kerryhall on 2010-10-26
Bump

---

### Post by kelly333 on 2010-10-27
it seems i have suffered the same problem, thanks for the help....:)

---

### Post by kerryhall on 2010-10-27
No luck for you yet though? Did you get those drivers to compile?

---

### Post by kerryhall on 2010-11-09
anyone get this to build with 2.6 kernels?

[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=2&lid=44)

---

### Post by no2498 on 2010-11-10
this worked for the gspca driver you may need to change the cam name to match yours
type lsusb in a terminal click enter
should tell you your cam name

SOLVED!!

gspca is now integrated in the kernel,but it works only after unloading the module and reloading it while camera is plugged in...

sudo modprobe -r gspca_sunplus
sudo modprobe gspca_sunplus

hope it helps some

---

### Post by kerryhall on 2010-11-13
lsusb tells me:

Bus 002 Device 009: ID 06a5:d800 Divio Chicony TwinkleCam

but there is no gspca driver that resembles that name

wrote a shell script to load every possible gspca driver. still no /dev/video

---

### Post by no2498 on 2010-11-15
sunplus

is/was the name of his cam sorry

---

### Post by kerryhall on 2010-11-20
so i 

plug the cam
modprobe gspca_sunplus
modprobe gspca_main

still no /dev/video0

replug the cam, still no go

do i need to manually create a /dev/video0?

---

### Post by kerryhall on 2010-12-02
Bump

---

