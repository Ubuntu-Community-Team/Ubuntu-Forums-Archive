---
title: "nvidia 190.42 driver + video colors"
date: 2009-11-17
forum: Multimedia Software
---

### Post by psycho5 on 2009-11-17
Hi, 

Sometimes when I try to run a video in vlc or mplayer, the colors seem inverted. I am using Nvidia 9500 GT with karmic 32-bit. How can I begin to fix this problem?

---

### Post by xc3RnbFO8P on 2009-11-17
Try Vlc Preferences> Reset Preferences.

---

### Post by psycho5 on 2009-11-17
I found a temporary solution, when playing the video, start a terminal session and run:

```

sudo apt-get install xvattr

```

then 

```

xvattr -a XV_HUE -v 0

```

---

### Post by eemarchetti on 2009-11-17
Need a little help.
 
I am new in the Linux world and I am facing a problem.
 
I installed the Ubuntu 9.10.
It recognizes my Nvidia video card, but It does not let me download the last driver 190.XXX.
I only have the 185.XXX available.
I tryed using the nvidia home page download, but it does not execute the file.
 
Is there any hint for me?
 
Best Regards,
 
Eduardo Marchetti

---

### Post by xc3RnbFO8P on 2009-11-17
> I am new in the Linux world and I am facing a problem.
You should use drivers that is supported by Canonical.
> Canonical provides critical updates supplied by the developers of nvidia-185-kernel-source until April 2011
Here is howto:
[http://ubuntuforums.org/showthread.php?t=990978]("http://ubuntuforums.org/showthread.php?t=990978")

---

### Post by nss0000 on 2009-11-17
Hummm...

When I installed KK_9.1 a week ago it automagically brought-down the latest NV_190.42 driver plus NV_GUI. Works just fine with my BFG_9800-gtx+/Hanns_28" display kit.

---

### Post by eemarchetti on 2009-11-17
The interesting part is that when I download any file for Linux, it opens and execute.
 
This file is a .run extention.
"NVIDIA-Linux-x86_64-190.42-pkg2.run"
 
I do not know how to run it... 
 
Any hint?

---

### Post by BiynaYahu on 2009-11-17
type "chmod +x /path_to_file/NVIDIA-Linux-x86_64-190.42-pkg2.run"
then "cd /path_to_file/"
then "./NVIDIA-Linux-x86_64-190.42-pkg2.run"

I just installed these drivers, and found that they aren't detecting my native resolution properly.  It will only allow up to 640x480, while 1024x768  is my true max resolution.

---

### Post by rockdj on 2009-12-15
> **psycho5 said:**
> I found a temporary solution, when playing the video, start a terminal session and run:

```

sudo apt-get install xvattr

```

then 

```

xvattr -a XV_HUE -v 0

```

Thanks, that solves the issue for me (for now).  I'm using the same drivers with a Dell XPS M1530 laptop (Geforce 8600M GT) and that problem of inverted colours just cropped up randomly.  All video output is affected (gstreamer-properties confirms this) so it's not an application-specific issue but a system-level one.

I've not done anything to change the system since installing the 190.42 drivers, except all standard updates for 9.10.  I note that one of these was the 2.6.31-16-generic kernel update so perhaps that's potential cause?

---

