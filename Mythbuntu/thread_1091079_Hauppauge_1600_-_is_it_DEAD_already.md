---
title: "Hauppauge 1600 - is it DEAD already?"
date: 2009-03-09
forum: Mythbuntu
---

### Post by mookie60 on 2009-03-09
This is my first crack at MythTV . . . it hasn't gone well.  

Bought a Hauppauge hvr 1600 kit (1183 model w/FM & remote) and installed it on a MythBuntu 8.10 (fully updated) machine (older Dell optiplex 260, 2.2ghz).   The machine currently has only integrated graphics, but i've got an NVidia 6200 on order.  Only standard def for me.  The PC will be both backend & frontend.


day 1:

Initially MythTV detected several "card types", including MPEG-2.   After some initial fiddling (using MPEG-2), I got it to display on my pc monitor, even recorded 1 minute as a test.   When I attempted to play back what appeared to be a successfully recording, the video wouldn't play at all.  I kind of expected this after having read about the problems with the first recording after a boot up.

When I went back to the capture card setup, the MPEG-2 tuner was no longer present, it was now "Failed to open".   All other card types were still detected.

Does this mean the MPEG-2 tuner/encoder died?


day 2:

Not sure if the tuner died or not, I tried to install the "fix" for this card, as laid out on the wiki page:   

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Several attempts (existing 8.10, plus a fresh 8.10 install, updated & not-updated) to execute this fix on MythB 8.10 returned errors/warnings during the "make" ("warning: format not a string literal and no format arguments") and "make install" ( like: "ERROR: Module tuner_types does not exist in /proc/modules").  Obviously this didn't work.   All the while though, all the other tuner card types were "found", but not the MPEG2

day 3:

The same wiki fix was done on MythB 8.04.   There were the same type of warnings during the "make" (if I remember that correctly).  However the "make install", "unload" and "modprobe" went fine - BUT STILL NO MPEG-2!   The other "card types" were found again (only after the wiki fix), just as before.


So, is my MPEG-2 dead?  . . .  get a new 1600 card, or get one of the other Hauppauges (I feel I need the hardware encode/decode)?  I'll quickly get another analog card if this first one pans out.   I'm on Brighthouse cable (NO cable box), and they say they'll continue to use analog for the foreseeable future.  I'm still standard def.

and, is 8.04 or 8.10 the preferred choice?   as a linux noob, I'm still getting used to Ubuntu, but I'd certainly do another distro if it worked better.


Thanks for any advice/tips/suggestions.

---

### Post by klc5555 on 2009-03-09
> **mookie60 said:**
> This is my first crack at MythTV . . . it hasn't gone well.  

Bought a Hauppauge hvr 1600 kit (1183 model w/FM & remote) and installed it on a MythBuntu 8.10 (fully updated) machine (older Dell optiplex 260, 2.2ghz).   The machine currently has only integrated graphics, but i've got an NVidia 6200 on order.  Only standard def for me.  The PC will be both backend & frontend.


day 1:

Initially MythTV detected several "card types", including MPEG-2.   After some initial fiddling (using MPEG-2), I got it to display on my pc monitor, even recorded 1 minute as a test.   When I attempted to play back what appeared to be a successfully recording, the video wouldn't play at all.  I kind of expected this after having read about the problems with the first recording after a boot up.

When I went back to the capture card setup, the MPEG-2 tuner was no longer present, it was now "Failed to open".   All other card types were still detected.

Does this mean the MPEG-2 tuner/encoder died?


day 2:

Not sure if the tuner died or not, I tried to install the "fix" for this card, as laid out on the wiki page:   

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Several attempts (existing 8.10, plus a fresh 8.10 install, updated & not-updated) to execute this fix on MythB 8.10 returned errors/warnings during the "make" ("warning: format not a string literal and no format arguments") and "make install" ( like: "ERROR: Module tuner_types does not exist in /proc/modules").  Obviously this didn't work.   All the while though, all the other tuner card types were "found", but not the MPEG2

day 3:

The same wiki fix was done on MythB 8.04.   There were the same type of warnings during the "make" (if I remember that correctly).  However the "make install", "unload" and "modprobe" went fine - BUT STILL NO MPEG-2!   The other "card types" were found again (only after the wiki fix), just as before.


So, is my MPEG-2 dead?  . . .  get a new 1600 card, or get one of the other Hauppauges (I feel I need the hardware encode/decode)?  I'll quickly get another analog card if this first one pans out.   I'm on Brighthouse cable (NO cable box), and they say they'll continue to use analog for the foreseeable future.  I'm still standard def.

and, is 8.04 or 8.10 the preferred choice?   as a linux noob, I'm still getting used to Ubuntu, but I'd certainly do another distro if it worked better.


Thanks for any advice/tips/suggestions.

1)Sometimes on bootup the cx18 driver fails to load properly. If this happens, usually sudo rmmod cx18 ; followed by sudo modprobe cx18 fixes this without a reboot. Then your backend setup should detect the card (as _something_). Which leads to ... 

2)Usually myth's backend setup ("capture card setup")refuses to add the analog side of this card as the correct MPEG-2. You end up having to add it as the incorrect v4l, and once so added, you can go back into the entry for this card and change it to MPEG-2. Then mythtv is happy with it.

3)The cx18 driver was fixed on 4 Jan. to eliminate the "first corrupted analog capture" problem specified in the wiki. I compiled the patched driver a week ago and can confirm the fix works as advertised. I don't know whether the patched module has been incorporated into any of the updates for any of the currently supported Mythbuntu versions. But clearly your odds of "out-of-the-box" support will be better with 8.10 than 8.04, since cx18 wasn't incorporated into the source tree until kernel 2.6.26, while Mythbuntu 8.04 is still on something like 2.6.24.

Cheers!

---

### Post by klc5555 on 2009-03-09
In rereading your original message I also noticed that you have an NVidia 6200 on order. 

If, when you add this card, you find you're having conflict problems between the cx18 driver and the NVidia proprietary drivers (one will load, but not the other), you'll be able to fix this small glitch by adding to your virtual memory allocation using the vmalloc=256m kernel parameter in grub. About which there have already been a couple of threads recently in this forum that you'll be able to find with a quick search if you need them.

---

### Post by mookie60 on 2009-03-09
Thank you, thank you.   I did #2 on your list first, as that was the simplest, and sure enough it worked.  Rebooted the machine a few times, a few recordings, and all still seems well.   And thanks for the tip on the Nvidia card, it should arrive today or tomorrow.

And to think I had already gotten an RMA# to return the card!

Thanks again

---

### Post by klc5555 on 2009-03-09
> **mookie60 said:**
> Thank you, thank you.   I did #2 on your list first, as that was the simplest, and sure enough it worked.  Rebooted the machine a few times, a few recordings, and all still seems well.   And thanks for the tip on the Nvidia card, it should arrive today or tomorrow.

And to think I had already gotten an RMA# to return the card!

Thanks again

Glad it all works! :D

The 1600 is very good as an analog-only card (better recording quality, I think, than the late "classic" PVR-150). I certainly can't recommend one for clear-QAM digital, but it sounds like that won't be a concern for you for some time.

All the best!

---

