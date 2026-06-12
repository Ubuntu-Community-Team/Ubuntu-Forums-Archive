---
title: "ATI X1650 Hardy Solutions??"
date: 2008-05-19
forum: Multimedia Software
---

### Post by Zaka Swartz on 2008-05-19
EDIT***SOLVED***Kernel 2.6.24.18 update fix!

There are MANY threads on the ATI Hardy problems, and a good many regarding the ATI X1650 white/black screen problems with no satisfied customers.

I have Hardy installed WITHOUT Compiz running at all ~ it's the pits to have a decent graphics card and not even be able to run minimal 3D ~ let alone SERIOUS 3d stuff.

I have the 32bit version stalled on a 64bit AMD rig with the X1650 doing the honors in the video department.

Is there another X1650 user that has successfully enabled 3D?

How did you do it?  *(My patience is wearing thin after losing a weekend to getting out of 'RECOVER' mode.)*

Thanks in advance,

Zaka

---

### Post by Zaka Swartz on 2008-05-20
Bump...

---

### Post by Zaka Swartz on 2008-05-22
One more shove... ;)

---

### Post by Jellman on 2008-05-22
hey, have you tryed envyng? you may need to uninstall your previous drivers?

```


sudo apt-get remove xorg-driver-fglrx
sudo apt-get install envyng-core
sudo envyng -t


```

Scott

---

### Post by Zaka Swartz on 2008-06-01
Thanks for the tip, Scott ~ loading the drivers via Envy did not help ~ compiz is installed, and if special effects are enabled I get the white screen and must 'recover.'  (Same as installing the restricted drivers from the terminal or using the hardware config tool.)

I'm considering going with the onboard ATI 1200 graphics or getting an nVidia card comparable to the ATI X1650...or, alternately just being patient until either ATI, folks on the Hardy team or a creative Hack gets an ATI driver cooked up.

Thanks, again!

Zaka

---

### Post by RickyF430 on 2008-06-01
I too was having many problems with black/white screens when I installed Hardy on my computer. Every driver I tried would cause the black screen on the boot, and I had to make do with the default driver, until I followed the guide at:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
(it might be for Ubuntu Feisty, but I was willing to give anything a try - I followed the second method of the guide)

After this, and without changing anything, I installed EnvyNG and loaded the ATi driver from it. A reboot later, everything works fine - desktop effects, compiz (and 1500FPS on fgl_glxgears)

Hope this works for you too

Richard

---

### Post by kellemes on 2008-06-02
I have the same card and it's working fine with [fglrx 8.42.3]("http://ati.amd.com/support/drivers/linux/previous/linux-r-8-42-3.html").

---

### Post by sim-value on 2008-06-02
But this driver doesnt have any Video Playback does it ?

---

### Post by Zaka Swartz on 2008-06-02
Thanks for the Feisty tip, RickyF430 & kellemes ~ I'll wade through that one next weekend!  

One question ~ to you have to do anything special to keep the update driver function from over-writing the older driver?

Thanks in advance,

Zaka

---

### Post by kellemes on 2008-06-02
> **Zaka Swartz said:**
> One question ~ to you have to do anything special to keep the update driver function from over-writing the older driver?

Thanks in advance,

Zaka

Good question..
I use Debian, not Ubuntu but I guess it works the same..
I "pin" the fglrx-driver packages by including the following lines in /etc/apt/preferences

```
Package: fglrx-kernel-src
Pin: version 8.43.2-2
Pin-Priority: 1001

Package: fglrx-driver
Pin: version 8.43.2-2
Pin-Priority: 1001
```

Explanation about pinning: [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin")

---

### Post by kellemes on 2008-06-02
> **sim-value said:**
> But this driver doesnt have any Video Playback does it ?

This driver has it all..
It may be the newer drivers perform better, at least this one works. I never could get newer versions of this driver to function without giving me the blackest screen I've ever seen.
So for now it seems the only way to get this card going.

@Zaka Swartz: Out of interest.. Do you have the AGP version of this card?

---

### Post by Zaka Swartz on 2008-06-03
> **kellemes said:**
> This driver has it all..
It may be the newer drivers perform better, at least this one works. I never could get newer versions of this driver to function without giving me the blackest screen I've ever seen.
So for now it seems the only way to get this card going.

@Zaka Swartz: Out of interest.. Do you have the AGP version of this card?

Thanks for the pin driver info! 

I'm using the PCIe version, on a 64bit dual core setup with 4GB ram.

---

### Post by miciurin on 2008-06-03
I also have the X1650. I had some problems in gutsy with older versions. However, once I installed Hardy (reformat fresh) it works without any problems (including compiz). I remember when having a black or white screen in the gutsy times that I had to change the AGP aperture size in BIOS to 256 (the card is 512 though). Not your case since yours is PCIe. But maybe some BIOS settings still can be applied. Envy also gave good results.

Good luck.

---

### Post by Zaka Swartz on 2008-06-03
> **miciurin said:**
> I also have the X1650. I had some problems in gutsy with older versions. However, once I installed Hardy (reformat fresh) it works without any problems (including compiz). I remember when having a black or white screen in the gutsy times that I had to change the AGP aperture size in BIOS to 256 (the card is 512 though). Not your case since yours is PCIe. But maybe some BIOS settings still can be applied. Envy also gave good results.

Good luck.

Good idea miciurin!  There may well be a BIOS setting that can affect this situation...I'll start plundering!

---

### Post by Zaka Swartz on 2008-06-07
It would appear that the gnomes have been busy at the Ubuntu workshop...

With the latest update to the 2.6.24.18 Kernel, the 3D driver for ATI video cards is new and improved and working very well!

Happy Trails ~ and thanks to all who replied!

---

### Post by smilinmonki666 on 2008-06-13
Hi,

Does this apply to the AGP version??

---

### Post by Zaka Swartz on 2008-06-14
Don't the pci/agp versions use the same 'normal' ATI driver?  I suspect so, hopefully the update solved your probs as well!

---

### Post by smilinmonki666 on 2008-06-16
No, this hasn't solver my problem, the update hasn't done much my ATI Sapphire X1650 AGP version still crashes, I have a good mind to return back to my 64mb nVidia card...


:'(

Please someone help??

---

### Post by abanuelosh on 2008-08-27
I have the same problem with my Sapphire x1650 AGP, i have tryed every method posted in this forums and other forums, i get the same result: >>>a black screen after boot<<<

My rig isÇ:

ASUS P4C800 E
2Gb RAM
>>> Sapphire x165 512 Mb :(
Viewsonic LCD 19 inch 1440*900

PLEASE HELP USS!!!

---

