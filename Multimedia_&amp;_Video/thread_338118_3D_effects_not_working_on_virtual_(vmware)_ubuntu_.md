---
title: "3D effects not working on virtual (vmware) ubuntu install"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by Mr Brown Shoes on 2007-01-14
Hi people,

I recently installed ubuntu on vmware running within windows xp pro. If I run the 3Dfx screen savers in the virtual ubuntu it seems to be using software rendering - indicating that the graphics drivers may not be set up correctly. I've read elsewhere that vmware is using a virtual graphics card and thus the driver for the virtual hardware isn't so good, causing 3D graphics to be 'slow'. Does slow mean software rendering or should I try and fix this problem. If so, where do I start.

I'm using vmware workstation: 5.5.1 build 19175, ubuntu: 2.6.15 -27 -386, graphics: NVIDIA GeForce 4 MX 420. I haven't installed the VMware tools onto the virtual ubuntu

btw I'm not hung up on the screen savers but I will be developing some OpenGL code in the future and I'd like to sort this issue now.

Thanks in advance.

---

### Post by oldmanstan on 2007-01-14
yeah, from what i've read vmware uses a software video card that specifically does not include 3d capability.  apparently it has no knowledge of what card you have in your computer and just uses a sort of generic driver of some sort.

---

### Post by Mr Brown Shoes on 2007-01-14
Guess I'll have to set up a duel boot then... <sigh>

---

