---
title: "GTX 280M (notebook) SLI support???"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Aikimox on 2009-12-30
Hi,
I installed Ubuntu Karmic on Alienware M17X with dual GTX 280M  video cards. I'm using the latest video driver from Nvidia - 195.30. But it seems like SLI is not working properly. I tried it with 190.x drivers and got messed up colors on reboot. After updating to 195.30 I could see SLI enabled in Nvidia Xserver and Glxgears would heat up both cards, but the stuttering was so big that even simplest video rendering would be ugly to look at. So I switched it Off. Has anyone managed to make it working normally under Karmic? 

Thanks in advance,
Aikimox

---

### Post by Aikimox on 2010-01-03
Bump...
So no one is running SLI?
Well I hope someone can help me here.
I'll provide some more detals:
After doing a clean install of Ubuntu 9.10
I added **ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic** to the repositories and got the following drivers available in the Hardware Drivers: 173,185,190,195(recommended). So I activated the 195 and tried running glxgears right away - 10-15k :confused::redface::icon_frown:
I tried a few changes nvidia-xconfig --sli=on,AFR,auto...but to no avail. The best I'm getting is 15k with SLI enabled and **very** choppy rendering. With SLI off the highest is 20k and everything is smooth.
Knowing that with GTX 280M SLI I should be getting 100k+ in glxgears, doesn't make me happy at all...
:redface:

---

