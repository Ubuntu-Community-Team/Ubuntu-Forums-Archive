---
title: "viaSwapOutWork: Assertion `sz == vmesa-&gt;total_alloc[heap]' failed."
date: 2008-11-12
forum: Multimedia Software
---

### Post by art vandelay on 2008-11-12
Hi.

I need to run 2 OpenGL programs(clients), as part of a client server application I'm programming. When I open a second program sometimes it gives me the following message and then it shuts off:

via_tex.c:429: viaSwapOutWork: Assertion `sz == vmesa->total_alloc[heap]' failed.

Sometimes I can run 2 programs with no problems at all but sometimes it is just impossible to open two, even after rebooting. 

I have an Ubuntu 7.04(feisty) installation with up to date packages. I tried to upgrade to 7.10 but I wasn't successful, altough I'm gonna try  again to do so. I have an Athlon XP 1.8 with 1 GB of RAM with a VIA onboard memory card.

I've already double the shared memory to the video card to 64 
MBs(the maximum allowed) fro mthe BIOS.

Any idea to fix this issue will be really appreciated.

Thanks in advance.

---

### Post by art vandelay on 2008-11-12
BTW, I have libgl1-mesa-dev version 7.0.1-1ubuntu3 installed

---

### Post by art vandelay on 2008-11-13
I've updated xserver-xorg-video-via but it's still the same. All of the OpenGL/Mesa packages are up to date also.

---

