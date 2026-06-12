---
title: "better performance of my intel video card"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by ubuntu_jazzbach on 2007-01-16
Hi !!!

I recently moved to Edgy in order to solve some problems I had with the repos in Hoary (yes, I was still using Hoary despite it's so aged !!!) and one of the things I loved from Hoary was that the video performed awesome in my LapTop (I have a HP Pavillion dv1000).

Now that I'm running Edgy, I noticed that the framerate of my video output decreased slightly (the screensavers are slooooooower, je, je, je) so, I searched over the net and I found that if I compiled a new kernel from scratch I could get it optimized for good video performance (my video card is an Intel Corporation 82852/855GM Integrated Graphics Device). So, the question is: How can I compile the newest kernel for good video performance :confused: :confused:  (I haven't compiled a kernel in my life)

---

### Post by kristjans on 2007-01-16
I have the same video card. I *think* I've read somewhere, that 915resolution would make the PC *good enough for only office use*. 

I've installed the Intel driver, but right now I've got a flickery screen, which I hope someone helps me to fix in the other thread. ;)

---

### Post by ubuntu_jazzbach on 2007-01-16
I've downloaded the Intel driver so, let's see if I get the same flickering (or if this solves the slow-mo problem). Whatever the result may be, I'll be posting it.

By the way, could you post the thread related to this:

> I've installed the Intel driver, but right now I've got a flickery screen, which I hope someone helps me to fix in the other thread. 

---

### Post by kristjans on 2007-01-16
[http://ubuntuforums.org/showthread.php?t=339300](http://ubuntuforums.org/showthread.php?t=339300)

The thread is here. I am not sure if it is driver's issue or monitors, but I hope I find out. I am probably going for driver's reinstall.

---

### Post by Mycen on 2007-01-26
I also have the 82852 video card, slow as hell indeed. To solve that, I tried installing the videodrivers i got from intel.com, but when I ./install, after a few steps it says
> Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.
While the dri.log says
> make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/mycen/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.


What does it mean? latest kernel modules?
I would be quite grateful if someone could help me on this. And THEN hope i won't flicker as well.....

---

### Post by zgornel on 2007-01-26
Bottom line : intel video performance will increase only if intel releases some outstanding drivers. So far, 2D is OK really but 3D = 0. Mesa's fault.

---

### Post by Mycen on 2007-01-26
Well i suspect the driver might fix a lot of my problems since the i915 driver also increased performance in windows enormously... I just can't get it to install...

---

