---
title: "And how about Nvidia GeForce2 MX 100/200?"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Thanatios on 2009-05-13
Greetings,

I have a little question about a videocard I have. I am planning to install Ubuntu on my system:

> Pentium: 4 3,21 GHZ
Memory: 1 GB DDR RAM
Nvidia: GeForce2 MX 100/200
Hard Drive: 100 GB HDD

So my question would be, if its possible to make Ubuntu 9.04 work with the Legacy drivers (71) together with compiz and GLX support? And any suggestions on how to do so?

I have been reading a lot, and I still can't find a good answer to my question.

Thanks in advance

---

### Post by srozzman on 2009-05-13
I have that card, and have to say it is much too slow to run compiz on, even with minimal settings

---

### Post by Thanatios on 2009-05-13
Well I have been reading some stuff about it. And I think that the card is quite capable of running it. 

It also depends largely on your system specs.

But for instance, just check this youtube movie: [http://www.youtube.com/watch?v=_qddueXkD8E](http://www.youtube.com/watch?v=_qddueXkD8E)

---

### Post by wabbalee on 2009-05-13
Not too sure as it is has been a while since I used a legacy driver for nVidia but the last time compiz could not work with legacy. Some other 3d funcionality was working ok.

---

### Post by Thanatios on 2009-05-13
Well yes, I have been reading that the new Ubuntu 9.04 doesn't support ATI legacy drivers. But the question I'm asking is to make sure what version of Ubuntu does work with the nVidia legacy drivers.

Because if they don't, then I'll have to install Ubuntu 8.04 on my system.

---

### Post by wabbalee on 2009-05-13
I am not saying that Jaunty has no legacy drivers for nVidia, but the last time I used nVidia legacy drivers (which is a few Ubuntu's ago) compiz could not work with that driver (very well). I am suggesting that would still be the case..

---

### Post by wabbalee on 2009-05-13
and a quick check in synaptic tells me that the legacy drivers for your card are still present for Jaunty.

---

### Post by Thanatios on 2009-05-14
Well the question is still if they would work with nVidia.

But yeah, I'll install Ubuntu Jaunty and check it out then. I noticed that the drivers simply won't work with nVidia Riva TNT2, I have been searching around, and only found workarounds for Ubuntu 8.04. 

See my other thread here: [http://ubuntuforums.org/showthread.php?t=1158454](http://ubuntuforums.org/showthread.php?t=1158454)

But still thanks for your help. I'll let know.

---

### Post by jorgeblasio on 2009-09-28
Hi Thanatios,

I've a system with Jaunty (1.05 Ghz Athlon, 512 Mb RAM and a GeForce2 MX 200 w/64 VRAM). I just figured out how to install the 96.43.13 drivers from Nvidia and applied the workaround to the DRI 0666 permission issue and I've got OpenGL working.

What is strange is that I just can't get Compiz to load through the Appearances menu, but if I run compiz --replace in Terminal, Compiz and Emerald replace metacity and I can even play with the Desktop Cube!

Also worth mentioning is that the video card passes the compiz-check script test!

What I also can't understand is that the open xorg ATI drivers perform better with Compiz on an RV100 ATI card that is supposedly inferior to this GeForce...

Update:
I still can't activate Compiz, BUT I created a new user account in this machine and lo and behold, in that account Compiz loads automatically!

Do you guys know if Compiz keeps logs somewhere?

---

