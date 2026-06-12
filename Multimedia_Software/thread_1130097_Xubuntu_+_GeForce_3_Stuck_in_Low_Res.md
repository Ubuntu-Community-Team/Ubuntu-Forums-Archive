---
title: "Xubuntu + GeForce 3 Stuck in Low Res"
date: 2009-04-19
forum: Multimedia Software
---

### Post by etali on 2009-04-19
Hi all,

I rescued an ancient machine from a friend, and put Xubuntu on it, but I seem to be stuck in low res.

Originally I put Kubuntu on it (I hadn't clicked how OLD the machine was), which was stuck in 800x600, and also running really slowly.  It's an ancient computer (900Mhz processor, 256MB RAM), so I figured I'd try Xubuntu instead.

Xubuntu launched in 800x600.  I installed the recommended drivers for the GeForce 3 (NVidia 96 ones), and enabled them when the restricted driver warning came up.

After a reboot, Xubuntu has decided that it will only run in 640x480!  I tried using the NVidia X Server Settings manager but that only lists really low resolutions and won't take anything else.

All I want is 1024 x 768 :)  

The monitor I'm using is ancient and un-branded.  I know it can do 1024 at 56hz, though.

Any tips would be very much appreciated.

---

### Post by etali on 2009-04-19
Problem solved.

My xorg.conf was just full of default stuff.  I did an apt-get update / apt-get upgrade and installed the restricted packages, then ran nvidia-xconfigure.

After that I got a blank screen on bootup, so used the recover xserver option on the boot menu, then removed the higher resolutions from xorg.conf.

Now booting in 1024 :)  Hope this helps anyone else who has similar troubles.

---

