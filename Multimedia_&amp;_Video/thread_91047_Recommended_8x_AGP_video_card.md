---
title: "Recommended 8x AGP video card"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by gfarrow on 2005-11-16
I have a machine that I want to put Ubuntu on.  That machine has a AOPEN GF4 MX440 8x-DV128 video card (nVidia chipset), which displays flickering white horizontal lines under X (it works fine with Windows). I've tried several versions of Linux/XFree on that machine, tried different nvidia drivers, and always had the same problem (actually the nvidia drivers locked up the machine).  I have wasted way too much time on this problem to date.

So long story short I need a recommendation on a cheap, 8x AGP video card that is guarenteed to work reliably with XFree so I can put this problem to bed and uses Linux on that machine.

---

### Post by Teroedni on 2005-11-16
If you know it is working on Windows it is guarantied to work in Linux too
Which driver have you installed .what modes are you running on.
Try to Install Ubuntu on it ,and if something doesnt work paste the xorg file then.

You have tested the exactly same size and refresh rate when you were cross checking with Windows right?

---

### Post by gfarrow on 2005-11-16
I've spent way too many hours previously trying to fix this problem including trying alternate drivers from nvidia, etc.  My time is worth more than the price of a new video card.  And the same problem occurs with the Ubuntu live CD.  I'm not going to install Ubuntu for real until I can verify with the live CD that it will work properly.

I'm a Linux advocate and I've used Linux since prior to version 1 of the kernel, which is longer ago than I like to think about (anybody else remember the Soft Landing distribution which required dozens of floppies).  However, in the interests of honesty, just because something works under Windows is no guarentee that it will work under Linux.  I have had plenty of issues over the years with hardware which worked under Windows but was not recognized under Linux, or didn't work properly under Linux.  I've also had the opposite, where hardware worked well under Linux but not Windows.  This isn't a slam on Linux, it is just reality and is a major factor in the slow adoption of Linux on the desktop.  (I am running a LAMP server on Ubuntu 5.10).

---

### Post by Teroedni on 2005-11-16
Okey the reason i say this was that the Mx400 have full support in Linux.
But it may be that your card is corrupt or something. 
I would inded recomend a mx400 but in your case it may be that either your card is corrupt or your motherboard doesnt like the card.

I did not mean to offend you sorry:(

So i would the recommend an Ti 4200 or a geforce 6200 like in my sinature;)
BUT:It may be as said earlier that your motherboard doesnt like Nvidia

So i will ask first if this is the first Nvidia card you tried in that pc
Which Motherboard do you have
Processor and such

Also have you done a ram test. Linux is more sensitive to the ram than windows. Maybe that is the problem?

---

### Post by gfarrow on 2005-11-16
No offense taken.  Thanks for the alternate suggestions.  Also the video card works flawlessly under Windows.

I actually replaced the motherboard on this box a couple of months ago.  I had the same video problem with the old motherboard and the new one, so I doubt if that is the problem.

---

### Post by mcpish on 2005-11-18
I just picked up a GeForce 6200 the other day and it's working great under Ubuntu.  I've got dual display setupnow with my monitor and TV.

---

### Post by daniels7 on 2005-11-18
matrox g200 works fine with mga driver (included in distro)
in Poland for 4 Euro (secondhand)

---

### Post by joshage1 on 2005-11-21
I got no problem with my video cards "128 mb 8x Inno 3d geforce 4 MX440-B, 8mb g200 Matrox, Sparkle 32mb Riva TNT2 m64" with redfox MVIG400 motherboard. It all works fine with ubuntu 5.10. 

I got a problem though on my sound (Cirrus Loggic 4235) on my other older motherboard. I got no sound at all. I'm still trying to figure it out.:confused:  Anybody?

I'll test my 16mb (PCI slot) savage4 next time and post it here.
Thanks...

---

