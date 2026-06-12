---
title: "No sound and no nvidia driver after kernell update"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by Kramxel on 2007-07-21
Hello

2 days ago I updated my kernell through the update system.

The problem I have is after the update my "nvidia" driver stoped working and I must now use the "nv" one.
Besides that I've lost sound.

I Have a Creative Geforce 2 MX video card and a Creative Labs Sound Blaster 1024 sound card.

Any help would be apreciated.

---

### Post by DDRFreak21 on 2007-07-21
I've had the same problem a few times:

What happens is the kernel gets updated but the linux-restricted-modules does not.

Example:
The kernel gets updated to 2.6.20-16
BUT the linux-restricted-modules stays at 2.6.20-15

What it boils down to is that your kernel is updated but the system can no longer load the proprietary drivers such as Nvidia and Creative. 

**Solution:**
Go into Synaptic and install the linux-restricted-modules that matches your current version.
OR
**Example**:
```
sudo apt-get install linux-restricted-modules-2.6.20-16-386
```
this is assuming that you are running a 32bit installation.

You will need to modify the command to whichever kernel you just updated to.

---

### Post by Kramxel on 2007-07-22
Thanks for the reply.

Been a litle busy this weekend...

I've now found that you were right, it is a problem with the linux-restricted-modules (LRM)

My kernel is 2.6.17-12-386

First:
One of the problems involved the LRM being a version older than of my kernel.

I solved that by upgrading to the correct version.

Second:
I found another problem that involved (re)instaling the nvidia-glx driver before updating the LRM.

Solved by instaling the LRM first then the nvidia-glx.

Third:
Found yet another problem as the nvidia.ko file that the nvidia-glx creates in the /lib/modules/2.6.17-12-386/volatile folder disapears after restarting...

Found no fix, as my X config file can't access the nvidia.ko file.

Fourth:
Still no sound....

Any help would be apreciated...

---

### Post by Kramxel on 2007-07-22
Hi

Envy solved my third issue.

I think it was the linux header files who was a previous version.
Or maybe it had nothin to do with it.... I don't know....

Sound is still AWOL....

Thanks

---

### Post by Kramxel on 2007-07-23
I had some more issues with the nvidia driver, including a disapeering desktop instalation O0

Fixed that by reinstaling the ubuntu-desktop

Meanwhile after so much fixing, I've found that my PCM and WAVE audio channels have been turned to a mute.... 

All my problems are gone now.


Next time a kernel update shows up, I'll think twice before doing that "important security update"...

---

