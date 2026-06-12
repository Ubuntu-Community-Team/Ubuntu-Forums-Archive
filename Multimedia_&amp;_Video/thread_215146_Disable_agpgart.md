---
title: "Disable agpgart"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by krishnarao on 2006-07-13
I have an nvidia geforce fx5500 gpu on a sempron 3000+ based desktop. I've installed the nvidia drivers and the NvAgp was set at 3 (basically uses agpgart). In this setting the X server would very frequently hang.
The only solutions that have worked are:
1. use the nv driver: no games
2. use the nvidia driver with NvAgp set to 1. when I do this the agp gets disabled. Reason being nvidia-agp is unable to load as the agpgart and amd64-agp load earlier.
Is there a way of preventing the two modules from loading.
I'm using ubuntu 6.06 dapper drake.

---

### Post by tseliot on 2006-07-13
> **krishnarao said:**
> I have an nvidia geforce fx5500 gpu on a sempron 3000+ based desktop. I've installed the nvidia drivers and the NvAgp was set at 3 (basically uses agpgart). In this setting the X server would very frequently hang.
The only solutions that have worked are:
1. use the nv driver: no games
2. use the nvidia driver with NvAgp set to 1. when I do this the agp gets disabled. Reason being nvidia-agp is unable to load as the agpgart and amd64-agp load earlier.
Is there a way of preventing the two modules from loading.
I'm using ubuntu 6.06 dapper drake.
DISABLE AGPGART

Blackist the amd64_agp & agpgart modules by adding this to your /etc/modprobe.d/blacklist (don't worry if the file is blank or doesn't exist):

```
sudo nano -w /etc/modprobe.d/blacklist
```

Copy and paste the following lines:
```
blacklist agpgart
blacklist amd64_agp
```

CTRL+X to exit (save)

```
sudo nano -w /etc/X11/xorg.conf
```

Put this option in the Section Device of your /etc/X11/xorg.conf:

```
Option          "NvAGP"                 "1"
```
 
Restart your computer

---

### Post by ctaggart on 2006-07-16
I tried getting rid of agpgart by adding it to /etc/modprobe.d/blacklist like you instructed, but it still shows up in lsmod after a reboot.

ctaggart@ubuntu:~$ lsmod | grep agp
nvidia_agp              8348  1
agpgart                34888  2 nvidia,nvidia_agp

I'm trying to troubleshoot my instability Ubuntu Dapper problems.  It is freezing on me often.

---

### Post by ctaggart on 2006-07-17
Any idea how to get rid of nvidia and agpgart?  I do not need either, do I?  Here is what I put in /etc/modprobe.d/blacklist

blacklist agpgart
blacklist nvidia
blacklist nvidia_agp

Then I ran update-modules.  Is that required?  Upon reboot, nvidia_agp is gone, but agpgart and nvidia still show up in lsmod.

---

