---
title: "Xubuntu 8.10 - Can't get Nvidia driver working"
date: 2009-05-04
forum: Multimedia Software
---

### Post by Billy Ng on 2009-05-04
I see other references to this issue, but can't seem to find anything that fixes it.

XUbuntu 8.10
PNY Verto GeForce 8400 GS (x2)

Initial install of OS leaves me with working vesa driver.  Run full system update (staying on 8.10, not going to 9.04) first.  Restricted drivers message comes up, offers me recommended 180 Nvidia drivers - install and reboot.

after reboot:
----------------------
Come back to "kinit:  No resume image, doing normal boot..."


lspci finds the following:
----------------------------------
08:00.0 VA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
09:00.0 VA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)


startx gives me:
--------------------------------
(EE) No devices detected

Fatal server error:
no screens found
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.


nvidia-detector finds:
------------------------------
none

Booting into recovery mode and select xfix and resume doesn't improve the situation at all.  As a last ditch effort, manually download the Nvidia drivers off their website and manually installed them (sudo sh NVIDIA-Linux-x86-180.51-pkg1.run) ... installation went smoothly, but video still no workie.

Any ideas?

The ultimate goal here is to get 4 monitors running, 2 on each of these cards.  But for now I'll settle for getting just 1 monitor working with an Nvidia driver.  I've tried the 173, the 177, and the 180 on both the 2.6.27-11 and 2.6.27-7 kernels.

Any help appreciated

Billy Ng

---

### Post by Anthalion on 2009-05-04
[B]You wont get any help !!! Not even I with my soundcard problem on Xubuntu havent got any help !!!

I am switching to Fedora !!!

Goodbye Ubuntu/Xubuntu !!! [/B]

---

### Post by dinub1 on 2009-05-04
> **Anthalion said:**
> [B]You wont get any help !!! Not even I with my soundcard problem on Xubuntu havent got any help !!!

I am switching to Fedora !!!

Goodbye Ubuntu/Xubuntu !!! [/B]

Anthalion, you may be very right. I am finding out that the programmers at Canonical are screwing up Ubuntu more and more with each new revision.... Nothing works like before (like ver 7.xx). 
I have this video problem which runs in low res with a high res screen. whatever I tried to do I failed. even installing ver 9.04 clean does not solve a thing. Still it runs in low res mode. With nVidia restricted drivers or without.

Note that Linux Mint ver 5, which is also an Ubuntu derivative, doesn't suffer from this illness :) And by default, without installing any restricted drivers. And with sae hardware as Ubuntu. It runs by default at 1680 x 1050 my screen default resolution. it detects the screen correctly etc... Ubuntu does not.

My conclusion: Ubuntu is loosing steam... :(

---

