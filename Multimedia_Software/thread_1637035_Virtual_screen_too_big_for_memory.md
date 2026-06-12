---
title: "Virtual screen too big for memory?"
date: 2010-12-03
forum: Multimedia Software
---

### Post by asgardian on 2010-12-03
Hello all.  This my first post, so bear with me  I'm trying to set up an older computer for a friend that does not have one  I've been using Ubuntu for a little over a year on a couple of systems, and this is the first time I have come across an issue I could not find an answer to.  During the boot sequence, and right before the GUI, I'm getting a "Low Graphics Mode" warning and it tells me that the "Virtual screen too big for memory; 5120k needed, 4096 K available" then it gives me some options, and the only one that seems to lead me anywhere is the "Load Ububntu in low res mode this once"  Ironically, once the Ubuntu GUI is booted up, the screen resolution is fine (1280x1024 actually - but it is an unknown monitor)  This happens every time I re-boot the system and is more of an annoyance then anything else, but since its to be a gift I'd like to get rid of this error message.  I've tried this on a second monitor, so I'm sure it's a graphics card issue - Here are the specs

Ubuntu 10.04 - fresh install and updated
Onboard graphics SiS 730 on a K7SEM motherboard
1.1 gig processor 
512K  ram
HP vs17 monitor

what more do you need in the way of info do you need to help?  Found a similar thread here (closed)
[http://ubuntuforums.org/showthread.php?t=516977](http://ubuntuforums.org/showthread.php?t=516977)
but it's old and it looks like xorg.conf is no longer used, as I do not have this file on either of my systems (though I have a xorg.conf.failsafe on the systems I'm trying to set up) and just in case, here is what the contents of this file is - 

***
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

***

so nothing really there that  I can see.

I've also tried manually setting the video output using these instructions thinking that the problem sounded pretty similar - 

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

but even setting it down to 640x480 at 16 bit still gave the error.

Anyone have any thoughts?  Thank you all for your time.

---

### Post by Yellow Pasque on 2010-12-04
The error occurs because you have 4MB of allocated video RAM. Looking at the mobo manual, you should be able to increase it up to 64MB in the BIOS (though I would try 32MB first).

If that fails, just use your xorg.conf.failsafe as regular xorg.conf and it will make the error message go away and automatically boot in "low-res" mode (i.e. use the vesa driver).

EDIT: Your BIOS calls it "system share memory size". See page 47 here: [http://www.scribd.com/doc/7341649/K7SEM1](http://www.scribd.com/doc/7341649/K7SEM1)

---

### Post by asgardian on 2010-12-04
Temüjin,

Thank you so much!  I was looking so hard for an OS solution that I did not think to poke around the BIOS.  Also a thank you for the link to scribd - I'll be bookmarking that one!  I set the BIOS shared memory to 32 as you suggested and it worked without a hitch!

---

### Post by idi0tf0wl on 2010-12-04
You should mark this as solved... I was all rarin' to help you.

---

### Post by asgardian on 2010-12-05
Sorry idi0tf0wl, new to the forums.  Thanks for the heads up!

---

