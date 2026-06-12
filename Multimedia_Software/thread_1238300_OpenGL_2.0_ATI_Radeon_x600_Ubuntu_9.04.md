---
title: "OpenGL 2.0 ATI Radeon x600 Ubuntu 9.04"
date: 2009-08-12
forum: Multimedia Software
---

### Post by Kapli on 2009-08-12
I just installed Ubuntu 9.04, never used Ubuntu before so I'm kinda new. My graphic card is an ATI Radeon x600, I'm trying to find drivers for it, I think i installed [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) somehow, but they don't seem to support OpenGL 2.0.
I need OpenGL 2.0 to run HeroesofNewerth, the requirements for that is     * Pentium 4 / Athlon XP (Processor with SSE required)
* 1GB of RAM
* 128MB fully OpenGL 2.0 / GLSL 1.20 compliant video card
* glibc-2.4

Any help is appreciated.

---

### Post by ssri on 2009-08-12
If you want OpenGL 2.0 support right now on an ATI legacy card, then you have to downgrade xserver and install the last Catalyst (ATI's propriety driver) that supported your card, which is 9.3 I think.  Be prepared tp spend some time in terminal.  I have a Mobility Radeon x2300 and downgrading xserver using this guide, installing Catalyst 9.3 via the manual way ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)), and moving my working xorg.conf from intrepid worked like a charm :).

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by Kapli on 2009-08-13
Oh well, I formatted and installed 08.04 instead :P
Weird I didn't find that guide, I was googling the whole day :O
Well it works fine now and 08.04 is fine so I'll just stay here :P

---

### Post by Kapli on 2009-08-14
> **ssri said:**
> If you want OpenGL 2.0 support right now on an ATI legacy card, then you have to downgrade xserver and install the last Catalyst (ATI's propriety driver) that supported your card, which is 9.3 I think.  Be prepared tp spend some time in terminal.  I have a Mobility Radeon x2300 and downgrading xserver using this guide, installing Catalyst 9.3 via the manual way ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)), and moving my working xorg.conf from intrepid worked like a charm :).

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

Ok so I decided I wanted to go back to 9.04 and follow this guide to get the drivers, what I don't understand though is why would you have to install the catalyst drivers manually, and did you just follow the easy way guide in the manual way? Also what do you mean by moving the xorg.conf from intrepid?

Thanks in advance.

---

### Post by Kapli on 2009-08-14
Alright, I followed the guide to downgrade Xorg and then I installed catalyst 9.3 manually with that guide. Everything seems to work now, I am able to play Heroes of Newerth which was my goal, there is only 1 problem, the performance is greatly reduced. I don't know why but I get a much lower FPS, so yeah I'll just go back to 08.04 or 08.10 I think.

---

### Post by markbuntu on 2009-08-14
Check in the Xorg.0.log. There may be a problem with the driver, DRI2 not working or the kernel modules not loaded. That is the usual cause of low performance since you get stuck with indirect rendering.

---

### Post by Kapli on 2009-08-14
Not sure what I'm supposed to look for, it says (II) fglrx(0): [DRI] installation complete at some place and (II) fglrx(0): [drm] added 1 reserved context for kernel

I don't really know, but I know that the performance was excellent when I ran it in ubuntu 08.04 with just enabling it in hardware drivers and doing just the updates after a fresh installation. 
In 8.10 and 09.04 using the guide to downgrade xorg the performance is really bad as in a very low FPS with the Catalyst 9.3 drivers and with the drivers from the hardware drivers. In 08.04 I was able to run Heroes of Newerth at 1680x1050, but in the other two versions described I had to go down to 1280x720 or something for it to be playable.
I really don't get it though, why it worked in 08.04.
Tomorrow I will once again format and install 08.04, hopefull I will be able to recreate the circumstances and Heroes of Newerth will run with good performance.

Edit: Alright, I'm back on 08.04 and the second I run Heroes of Newerth I notice the performance is better, although I have no idea why. All I did was a fresh installation of 08.04, then I updated and then I enabled drivers through hardware drivers and everything seems to work smoothly now.

---

### Post by avengeru on 2009-12-11
> **markbuntu said:**
> Check in the Xorg.0.log. There may be a problem with the driver, DRI2 not working or the kernel modules not loaded. That is the usual cause of low performance since you get stuck with indirect rendering.


Can u say please what should he look for? Because i have same problem with ATI HD3870 xubuntu 9.10 :(

---

### Post by markbuntu on 2009-12-11
You should look for lines that begin with (EE)

---

### Post by avengeru on 2009-12-14
> **markbuntu said:**
> You should look for lines that begin with (EE)
And where i can find it ? Looks like there is no search function in xubuntu...

---

### Post by markbuntu on 2009-12-14
Just look in the var/log/Xorg.0.log. It is not very long.

---

