---
title: "ATI FGLRX Video Driver problem."
date: 2009-08-11
forum: Multimedia Software
---

### Post by halo_effect on 2009-08-11
Hi I am new to the Ubuntu Linux community. I am running Ubuntu 9.04 externally from an internal hard drive in an enclosure connected to my laptop via USB 2.0. My GPU is an ATI FireGL V5700 with 512 MB of VRAM that comes standard in a Lenovo ThinkPad W500 laptop. After installing the suggested driver from ATI, the FGLRX driver found in the Hardware Drivers sub menu in the System tab, my screen was completely scrambled!:confused::( I had to eventually boot in rcovery mode and remove the driver from the the root directory. Everything is well now, but unfortunately I can't turn on any of my Desktop Effects without an appropriate driver. This is my third day using Ubuntu and I am absoulutely lovin' the experience!:P For an open source OS Ubuntu just :guitar:! I would really appreciate if anyone could provide any help or suggestions for a resolution to this issue! Any help is much appreciated as I would like to use programs like Blender, Gimp and Inkscape utilizing the power of my ATI card.

Thanks!

---

### Post by markbuntu on 2009-08-11
According to the release notes the driver does not support the FireGL V5700.

---

### Post by stalet on 2009-08-12
It is supported, i got the same machine and ive used the fglrx driver. 

Follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Remember to set the bios "Graphics mode" to "discrete" and set "OS switchable" to "no"

The driver you allready used will probably work with just the bios changed.
But the latest driver from amd has a few bugfixes you might not want to miss.

---

### Post by Scythium on 2009-08-30
I also just installed Ubuntu on my W500 and got the same issue when I installed the FGLRX video drivers.

The reason I used this driver was because the v5700 is based off the 3650.
The name changed to v5700 when I updated my bios to 3.00 - 1.20.

Let me know what you work out!

I'm going to do some more reading about this.

---

### Post by mr_e_uss on 2009-08-30
> **stalet said:**
> It is supported, i got the same machine and ive used the fglrx driver. 

Follow this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

Remember to set the bios "Graphics mode" to "discrete" and set "OS switchable" to "no"

The driver you allready used will probably work with just the bios changed.
But the latest driver from amd has a few bugfixes you might not want to miss.

stalet:  Are you saying that you have a Lenovo W500, and you are using the fglrx driver with the ATI FireGL V5700?  Are you able to use multiple displays?  And, are you able to use Compiz effects, 2D and 3D?

If so, this is great news -- there is a lot of confusion about fglrx support for the W500 and Ubuntu 9.04.

Thanks.

---

### Post by stalet on 2009-11-08
> **mr_e_uss said:**
> stalet:  Are you saying that you have a Lenovo W500, and you are using the fglrx driver with the ATI FireGL V5700?  Are you able to use multiple displays?  And, are you able to use Compiz effects, 2D and 3D?

If so, this is great news -- there is a lot of confusion about fglrx support for the W500 and Ubuntu 9.04.

Thanks.

Yes.
I got a W500 currently running 9.10 (but it worked for 9.04 as well)
With compiz 2D and 3D effects. On the ATI card the effects are really smooth - and I can play 3D games with 1920x1200 resolution without problems. The only thing is that you have to enable the xserver-nobackfill to avvoid lag when resizing windows.

[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill)

After updating to 9.10 the suspend/resume seems to work ok as well. At least with the 9.10 fglrx driver installed.

Ive testet multiple displays (videocanons and such) - and it works without problems.

-S

---

