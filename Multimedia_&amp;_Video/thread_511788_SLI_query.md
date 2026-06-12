---
title: "SLI query"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by MrCuddles on 2007-07-28
Hey folks,

I've fairly recently installed Feisty Fawn on the following system:
Asus Striker Extreme nForce 680i SLI motherboard
( +packaged SupremeFX audio card )
Intel Conroe Dual Core 2.66 GHz processor
2x Asus EN8800GTS gpus

I think that's all the pertinent data, but there's also a functioning Linksys WMP54GS wireless card wedged between the 8800s.

I'm pretty new to Linux. Ubuntu is the first distribution I've installed at home. I use RHEL on Sun boxes at work, but with absolutely no admin privileges, so I was limited in what I could learn.

So I've followed a handful of guides about installing the nVidia drivers and they've all worked fine and dandy for one card, but I don't notice any difference if xorg.conf is set with sli=auto, AFR, off, or any other setting. Consistent average results from glxgears is roughly 22000FPS. When I began installing Feisty, it was after I had a working SLI configuration in XP ( dual-booting now ), which was a fairly automated process. But here, I'm not really sure if the system even sees more than one card at this point, the hardware manager gives me squat for information about anything nVidia in there, a lot of "unknown" attributes. I can use the first card with any of my monitors at any resolution I want.

My question is, then, how can I go about properly setting up these drivers and my system to have these great cards working together through SLI? Do you folks need any other information to make an informed suggestion?

-Chris

---

### Post by MrHippocampus on 2007-07-28
I wouldn't say that glxgears performance is a good indicator of SLI working or not. I would try a proper game, if you don't have any lying around you could try one of the many open source fps's which should stress the cards a bit :)

---

### Post by MrCuddles on 2007-07-28
Mind naming a few that I could test with? I haven't the faintest clue which one might provide a reliable benchmark, as I'm really not an avid PC gamer by any means. And aside from this kind of test, are there any other methods by which I can see if both cards are even recognized by the system, leaving aside temporarily the issue of whether or not they are teamed?

-Chris

---

### Post by MrHippocampus on 2007-07-28
Nexuiz is one off the top of my head, it should be in the repo's (Its probably a fairly big download). If you turn up the settings it should take up the resources required to show whether or not SLI is working.

As for seeing if both cards are recognised, you could simply do "lspci" and see if there are two entries for nvidia. Or you could look through /var/log/Xorg.0.log and see if there are any messages about SLI in there.

---

### Post by MrCuddles on 2007-07-28
/var/log/Xorg.0.log shows the following:

```
(**) NVIDIA(0): Option "SLI" "AFR"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): NVIDIA SLI alternate frame rendering selected.
(WW) NVIDIA(0): DamageEvents are not currently compatible with SLI.  Disabling
(WW) NVIDIA(0):     DamageEvents.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:8:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize one NVIDIA graphics device!
(WW) NVIDIA(0): Failed to initialize SLI configuration.  Reason: One GPU
(WW) NVIDIA(0):     failed to initialize; Only one GPU will be used for this X
(WW) NVIDIA(0):     screen.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS (G80) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 327680 kBytes
```

cat /proc/driver/nvidia/cards/* shows the following:

```
Model:           GeForce 8800 GTS
IRQ:             21
Video BIOS:      60.80.18.00.01
Card Type:       PCI-E
DMA Size:        40 bits
DMA Mask:        0xffffffffff
Bus Location:    01.00.0
Model:           GeForce 8800 GTS
IRQ:             21
Video BIOS:      ??.??.??.??.??
Card Type:       PCI-E
DMA Size:        40 bits
DMA Mask:        0xffffffffff
Bus Location:    08.00.0
```

It sees the card, but the Video BIOS line for the second card is a little fishy, to say the least. I've also discovered that the 8800GTS is nowhere to be found on any of nVidia's "supported hardware" lists for Linux which accompany the drivers. Despite this, does anyone know how I can get around this issue?

-Chris

---

### Post by MrHippocampus on 2007-07-29
Ive looked around a bit and havent found anything useful :(. I suggest searching/posting on the [nvidia linux forum]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") and see what they say there, they actually have people employed by nvidia on there. (If you you post on there, read the FAQ's first and generate a bug report).

---

### Post by MrCuddles on 2007-07-29
I'll do that. Thank you for your efforts.

-Chris

---

### Post by skreiner on 2007-08-02
I have a setup nearly the same as yours. The graphics issues have been quite difficult for me to solve. I had to install Ubuntu using the alternate version because I could not get Fiesty or Edgy 64 or 32 bit to install using the standard image, even in Safe Video mode.

Once up and running, I have also been unable to get SLI working. It seems my issue is related to no Root Bridge connection (according to nvidia's [ site.]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/chapter-25.html") When I followed the checks on the bottom of this page the linkage was not correct. According to nvidia, the only solution is to "to upgrade your kernel to one that properly detects your PCI bus layout".

If you come across any more usefull info, please let me know.

---

