---
title: "Sound but no Video"
date: 2009-10-20
forum: Multimedia Software
---

### Post by JKoczeniak on 2009-10-20
I have ubuntu 9.04 jaunty.  It is an older Toshiba satellite and I am getting no video for youtube.  I do get sound but I cant get video.  I have installed flash 10 and have all sorts of addons for firefox installed and I cant seem to get it to work.  I also cant get on pandora.com it just stops loading like 1/4 of the way through the progress bar.  I had this problem with my new laptop that I installed ubuntu on and the problem with that one was the fact that I needed the 64 bit flash player.  I have replicated the steps for this computer and have had no luck.  I do not have the 64 bit flash but just the good old 32 bit.  I have exhausted googles search to try and fix the issue and cannot come up with a solution.  Please help thanks guys.

---

### Post by RichardLinx on 2009-10-21
Are you running 32 or 62 Bit OS?
Open a terminal and type the following commands, then post the output back here:
```
uname -a
```
Have you installed your graphics card driver?
```
glxgears
```
If the cogs don't show up, or are extremely choppy after you execute the "glxgears" command then it means your graphics card isn't installed or doesn't support 3D acceleration.

---

### Post by JKoczeniak on 2009-10-23
When I do glxgears the gears come up and are spinning great.  There is no lag.  I do know that the display drivers are installed and they do have 3D capability but the computer runs slow when I enable the driver.

As for the other entry here is what came up:

(uname -a)
Linux bret-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i 686 GNU/Linux

---

### Post by RichardLinx on 2009-10-24
You're running a 32 Bit OS. Have you tried removing and reinstalling flash? That tends to fix the issue for a lot of people. (Just completely remove it through Synaptic)

If reinstalling doesn't fix it, try seeing if it will work under Opera: [http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by JKoczeniak on 2009-10-26
I have tried to remove it from the package manager and nothing works still I will try opera and see if that works.

---

