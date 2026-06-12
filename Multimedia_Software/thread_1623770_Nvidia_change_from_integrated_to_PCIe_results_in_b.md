---
title: "Nvidia: change from integrated to PCIe results in black screen"
date: 2010-11-17
forum: Multimedia Software
---

### Post by practic on 2010-11-17
Here's the scenario: installed Ubuntu 10.10 on a relatively recent mb (Asus M3N with integrated Nvidia 8200). Later, decided to add a PCIe Nvidia 8400GS. Everything is fine until the desktop should appear, but a black screen is shown instead.

I then switch to another terminal with ctrl-alt-f3, login, sudo nano /etc/X11/xorg.conf and change "nvidia" to "nv". Then sudo reboot, and it all works, but without the nvidia driver.

Any attempt to remove/reinstall the Nvidia drivers still results in the black screen when trying to boot with the proprietary driver installed.

I also tried removing nvidia files that were in kernel source directories, reinstalling the kernel...black screen. Tried installing the previous kernel and booting with that...black screen.

Is there something else I'm missing that would cause the nvidia driver to try and load the motherboard graphics instead of PCIe? It all works with the nouveau driver, so why not with nvidia driver?

I'm pretty sure that if I download the latest Nvidia run file, and do an install from that, it will all work, but then my video will be hosed when the kernel gets updated, and I'll have to do the whole process again. So that is not the best solution.

At this point, I'm ready to back-up home directory and reinstall, but would really like to avoid that if possible. Does anyone know why this is happening?

I've had this happen before with other hardware (so it's not just a hardware problem), but have yet to find a reasonable answer, other than reinstall. But there's got to be an easier way...

---

### Post by practic on 2010-11-17
Okay, here's what I came up with. 

We tried a full install of the latest Nvidia RUN file and it also failed.

We also tried a full reinstall of Ubuntu, and this did not help either. As soon as the proprietary driver was enabled, the next reboot brought a black screen at the desktop.

We tried 3 different video cards on this board and all the NVidia ones did the same thing (black screen when NVidia driver loads). We tested these on another computer running Ubuntu 10.10 64 and they were fine. We then tried an ATI Radeon HD2400 Pro on the troubled machine and it worked fine also.

At this point, I'm drawing the conclusion that there is a problem between Linux and this motherboard. It supports SLI, although none of the NVidia cards I was trying are SLI type. However, for some reason deep down in the nuts and bolts, there are some compatibility issues here. The motherboard did not have any options for disabling SLI, and maybe this is tricking Linux into thinking the video should be SLI compatible, or maybe the NVidia driver is trying to link up the integrated graphics with the PCIe card. Anyway, for now we are staying with the integrated graphics.

The main reason for trying to improve it was to play 1080p smoothly, which neither the integrated 8200, nor the ATI HD2400 could do. The 8400GS cards are capable of it though, but not on this motherboard (Asus M3N78-VM).

---

### Post by PRC09 on 2010-11-17
Dont know if this will help any.I have an 8400gs and it works fine with the latest drivers from this ppa,not the same motherboard tho.....


[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick)

---

### Post by practic on 2010-11-18
Thanks for the response! I think we had the X-Updates PPA turned on already on that computer. 

The 8400GS (we had two different brands of the card) worked fine on another computer running the same Ubuntu. That's why I think it's related to the motherboard/kernel/nvidia driver, and perhaps the SLI feature.

---

### Post by Blivia on 2010-11-18
[COLOR=Blue][FONT=Arial Black]I know I'm still a Ubuntu newb, but... Maybe your problem is that the drivers are running on your On-board graphics card? They are both Nvidia, so it could be getting confused somewhere- But I'm no expert, I just started using Ubuntu myself. I'm also waiting for an answer on my own topic- Anyway I hope my view on the matter will offer some insight on your problem. [/FONT][/COLOR]

---

### Post by cchhrriiss121212 on 2010-11-18
That integrated chip should be able to use vdpau output in smplayer, then it should play 1080p with ease.

If you are still wanting to use the 8400GS have a look through your BIOS settings, you may even need to update it in order to change some option.

---

### Post by practic on 2010-11-20
chris,

Hey, I didn't know about that option. We tried it here and it works great! 

The CPU activity was very minimal, and the 1080p played back smoothly.

Is SMPlayer the only one that supports this?

---

### Post by cchhrriiss121212 on 2010-11-21
A few other players also support vdpau, smplayer is just the one I prefer. See here:
[http://en.wikipedia.org/wiki/VDPAU#Software_supporting_VDPAU](http://en.wikipedia.org/wiki/VDPAU#Software_supporting_VDPAU)
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

---

### Post by practic on 2010-11-21
> **cchhrriiss121212 said:**
> A few other players also support vdpau, smplayer is just the one I prefer.

I did a bit of brief reading and it seems while GStreamer has some code to support it, that's not finished. Mplayer can do it, with the correct config or command-line (but much easier just to use SMPlayer). And VLC could also do it but you have to do a custom compile.

...so...I think I'll stick with SMPlayer also for now!

---

### Post by atari130xe on 2010-12-22
Hello Practic I am suffering the same problem look at to my posts about this:

[http://ubuntuforums.org/showthread.php?t=1590243&highlight=black+screen+ubuntu+maverick]("http://ubuntuforums.org/showthread.php?t=1590243&highlight=black+screen+ubuntu+maverick")

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/660596]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/660596")

As you can see I got the same GPU as you (Nvidia Geforce 8400GS PCIe) and I had no problems till Ubuntu Maverick, also it happen with a couple more of distros like Arch Linux, Chakra Linux (an Arch derivate), etc. its a problem with something related to the 260. series Nvidia proprietary drivers (till 253. series works ok), it works ok with nouveau but without 3D acceleration, it means that you can't run a lot of software as Google Earth, etc. I don't know what to do, the video card is not that old to buy a new one.

---

### Post by practic on 2010-12-22
In my case, it was related to a specific motherboard that supports SLI. The motherboard graphics (Nvidia 8200) worked, but the addon card (8400GS) didn't. The same card (8400GS) works on all other systems I've used it on (with Ubuntu 10.10)...so that's what makes me think it is partly related to the motherboard.

---

### Post by atari130xe on 2010-12-27
> **practic said:**
> In my case, it was related to a specific motherboard that supports SLI. The motherboard graphics (Nvidia 8200) worked, but the addon card (8400GS) didn't. The same card (8400GS) works on all other systems I've used it on (with Ubuntu 10.10)...so that's what makes me think it is partly related to the motherboard.

It would be great to know how you have made to work your 8400GS on other systems and which systems, I have tried to make it to work with many Linux distros with no luck, thanks! Could you post your PC  configuration (mobo, ram, etc.) in which 8400GS PCIe works with 260.xx.xx Nvidia proprietary drivers? By the way my mobo supports SLI and it does not work on it, so I have entered BIOS setup and changed from SLI "auto" to SLI "one single card" and neither work. so...

---

### Post by practic on 2010-12-27
Here are two of my systems which work fine:

Gigabyte GA-73PVM-S2H Motherboard
Intel Core2Duo E7200
4GB DDR2 A-Data 800MHZ RAM
Asus EN8400GS PCIe Graphics Card
Ubuntu 10.10 64bit

Gigabyte M68M-S2P Motherboard
AMD Phenom X3 8850 AM2+
2GB Mushkin Silverline 800MHZ RAM
Asus EN8400GS PCIe Graphics Card
Ubuntu 10.10 64bit

This is the system that does not work with the 8400GS on PCIe:

Asus M3N78-VM
AMD Phenom 8250e
2GB RAM (not sure of the brand)
Ubuntu 10.10 64bit

The Asus board supports "Hybrid SLI" and I think that is the difference, and where the problems come in.

I've also tried an XFX 8400GS on my working systems, and it was fine, so it is not specific to the maker of the graphics card.

Why don't you look for a Gigabyte board on sale? There's a few GA-M68M-S2P on Amazon for $50 plus free shipping. It will fix everything!

---

