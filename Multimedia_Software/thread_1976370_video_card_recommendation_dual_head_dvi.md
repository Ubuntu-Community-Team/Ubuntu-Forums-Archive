---
title: "video card recommendation dual head dvi"
date: 2012-05-08
forum: Multimedia Software
---

### Post by draptik on 2012-05-08
Hi,

Summary:
Can somebody recommend a video card which works out of the box with nvidia or ati drivers with current Ubuntu 12.04? For details please see below.
 
After I upgraded from 11.10 to 12.04 my video card (NVIDIA GeForce 9500 GT) was not supported anymore.

I am affected by bug [#948053]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/948053")

I have already tried a couple of solutions. See thread [http://ubuntuforums.org/showthread.php?p=11903026](http://ubuntuforums.org/showthread.php?p=11903026)

My question is: Can somebody recommend a simple video card which works out of the box with Ubuntu 12.04 and fulfills the following simple requirements?

[LIST]
[*]64bit Ubuntu 12.04
[*]dual head DVI (very important!)
[*]passive cooling (no fan)
[*]RAM >256MB
[/LIST]

Thankful for any pointers,
Patrick

---

### Post by Yellow Pasque on 2012-05-09
That bug doesn't affect you. It is for older cards that can't use nvidia-current drivers.

---

### Post by draptik on 2012-05-10
Hi Temüjin,

> **Temüjin said:**
> That bug doesn't affect you. It is for older cards that can't use nvidia-current drivers.

Thank you for your reply. 

Yes, "nvidia-current" is the driver I was recently using with Ubuntu 11.10.  Previously I was using "nvidia-173". The reason my video card does not work with Ubuntu 12.04 is the same: Ubuntu upgraded to a new Xorg version. Nvidia currently has not patched all video card drivers for this Xorg version.

Can you recommend a dual head nvidia video card which works out of the box?

Cheers,
Patrick

---

### Post by Yellow Pasque on 2012-05-10
> Nvidia currently has not patched all video card drivers for this Xorg version.

Why can you not use the nvidia-current (295.x) driver? It works with Xserver 1.11 and should work fine in 12.04.

---

