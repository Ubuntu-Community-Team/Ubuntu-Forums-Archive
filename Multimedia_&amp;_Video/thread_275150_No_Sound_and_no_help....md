---
title: "No Sound and no help..."
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by backu on 2006-10-10
HELP! 

I've been all over the forums looking at posts made by people with the same problem I have... and half of them say they fixed it, but don't say how. 

I have a Creative Labs Live! 24bit, which ALSA supports, but cannot for the life of me get the driver for this damn thing loaded, so I have no sound. I don't know what to do, everything I've tried (Including the 'Comprehensive' doesn't work. What the heck do I need to do to get this damn card working right? Onboard is disabled (Also supported, but wouldn't load). Alsa driver is snd-ca0106 on Dapper Drake

---

### Post by backu on 2006-10-10
Very interesting... come to find out, the modules aren't available in the 2.6.15-27-server kernel.. sound works in the 2.6.15-26-server kernel without a problem, and it has the modules.. SO HOW DO I GET IT TO WORK IN 27?!

---

### Post by kvonb on 2006-10-11
Probably not much help, but I have the SBlive (as well as an onboard which is disabled), I am also running 2.6.15-27-686 kernel - and all works well!

I found that the SBLive is the easiest to get working, I didn't do anything at all, just installed Dapper.

Does your mainboard have the nVidia chipset (NOT video card, but mainboard chipset, it will say in the manual)?  I've heard people have problems with that in conjunction with other devices, something to do with restricted modules.

Also, does the mixer icon show up when you have booted?  If it is there and doesn't have a red cross over it, then it looks like some sound card has been found.  If so, double-click on the mixer icon, then selcet FILE -> CHANGE DEVICE, see what is listed there, it may be set to use the onboard sound (even though it is disabled), if so, select SB Live, check all the levels - especially the PCM one, it seems to control the overall sound level.  If there is no PCM listed, click on PREFERENCES and enable it from the list.

And of course - make sure that your speakers are plugged into the correct output from the sound card (namely the light green one).

Hope you have luck,

Regards,  Kev :)

---

