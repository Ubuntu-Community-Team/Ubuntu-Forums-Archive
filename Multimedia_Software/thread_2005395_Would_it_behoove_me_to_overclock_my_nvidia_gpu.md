---
title: "Would it behoove me to overclock my nvidia gpu?"
date: 2012-06-17
forum: Multimedia Software
---

### Post by Randymanme on 2012-06-17
I wonder what benefits there might for my computer if I were to overclock my integrated graphics card (NVIDIA® GeForce® 6150 SE GPU) .

As  things stand, this computer (or maybe just the graphics card) isn't  good enough to run Ubuntu 12.04 Unity.   Well how much better  does it need to be?

Since the graphics card is integrated with  the motherboard, does one overclock just the gpu and not the cpu?  Or  does one overclock them both in tandum?  Or would overclocking just the  cpu cover the gpu also?

I've googled overclocking a nvidia gpu and one of the hits was [http://lifehacker.com/5864640/how-to-ov ... erformance]("http://lifehacker.com/5864640/how-to-overclock-your-video-card-and-boost-your-gaming-performance").   This tutorial is for NVIDIA or AMD video cards and calls for a Windows  machine.  Well, I do have Windows 7 on this box.  Specifically, is  overclocking operating-system-specific -- I mean would overclocking my  gpu with Windows only apply to Windows but not to Linux, or would the  gpu, itself, be overclocked to where it's a hardware adjustment  applicable to whatever operating systems are installed on the computer?

I'm  under the impression that overclocking my cpu would give my computer  more alacrity or faster response time.  The tutorials I've read so far  (both today as well as in the past, when I was working up nerve to  actually try to do it) have suggested that determining how much to  overclock is a trial and error process.  

But it would seem to me  that for any given gpu, there would exist some manufacturer  specifications on how much it *could* be overclocked without seeing  artifacts; and that there would be suggested overclocking increments  based on the experiences of various communities, like, say,  Ubuntu forums.  And the same for CPUs. 

I do  have a Nvidia GeForce FX5200 card that I'm not using.  Would it be  better to overclock it since it's an add-on card that I can screw up and  leave my integrated card intact?  But can that add-on card be  overclocked enough to be better than my integrated gpu?

Any thoughts on this?  Any help or advice would be much appreciated.  Thank you.

---

### Post by Tweak42 on 2012-06-18
Looking at Toms Hardware chart, it appears the FX 5200 and your integrated 6150 are at approximately the same performance level.  In direct comparison I'd say the dedicated card should perform faster because it's not borrowing the main system memory. 
[http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107-7.html](http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107-7.html)

Unless you can up the voltage levels to far beyond stock, it's very unlikely you can damage your gpu (or even your cpu) by upping just the clockspeed because they will more likely crash and lockup before any damage can be done. 

Overclocking isn't possible on the current Nvidia linux drivers and hardware as they are in windows.  However I'm not sure about the open nouveau drivers and the nvidia legacy drivers for old hardware.

In any case, overclocking is mainly to squeeze a little more performance out of your card, not make it work with something it cannot do normally.  With that in mind, you may want to stick with Unity 2D or ubuntu variant that uses a low requirement window renderer.

---

### Post by gnusci on 2012-06-18
you can overclock but install more fans to your CPU.

---

