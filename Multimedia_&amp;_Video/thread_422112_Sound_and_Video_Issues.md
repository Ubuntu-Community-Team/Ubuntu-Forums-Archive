---
title: "Sound and Video Issues"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by LindsaySlater on 2007-04-24
Hello all! I am once again plagued by problems that can all be traced back to my silly install method. I used a desktop to install Edgy onto a laptop hard disk, then put the disk back into the laptop... Had issues with the Xserver, but cleared them up for the most part.. Now, as it stands, I am stuck in 800x600 resolution, and I have no sound... Minimal screen space I can live with, I suppose.. But the lack of sound is getting quite annoying... I do hear the occasional beeps, when plugging in or unplugging the power cord, but I think that those can be traced back to the BIOS, though when running any other system, these beeps are not heard. So it's unlikely. When I attempt to open Volume Control, I get the message: > No volume control GStreamer plugins and/or devices found. 
Another message that comes up is this one, when attempting to open Totem: > Totem could not startup. Could not open resource for writing.
The sound device that I have in my system is a Crystal Semiconductors CS4237B, and the video card is a NeoMagic 2160.  

If anyone could help me that would be wonderful!

---

### Post by Talon2 on 2007-04-24
> **LindsaySlater said:**
> Hello all! I am once again plagued by problems that can all be traced back to my silly install method. I used a desktop to install Edgy onto a laptop hard disk, then put the disk back into the laptop... Had issues with the Xserver, but cleared them up for the most part.. Now, as it stands, I am stuck in 800x600 resolution, and I have no sound... Minimal screen space I can live with, I suppose.. But the lack of sound is getting quite annoying... I do hear the occasional beeps, when plugging in or unplugging the power cord, but I think that those can be traced back to the BIOS, though when running any other system, these beeps are not heard. So it's unlikely. When I attempt to open Volume Control, I get the message: 
Another message that comes up is this one, when attempting to open Totem: 
The sound device that I have in my system is a Crystal Semiconductors CS4237B, and the video card is a NeoMagic 2160.  

If anyone could help me that would be wonderful!

Concerning the CS4237b:  If memory serves me correctly that is an ISA sound chipset.  I'm pretty sure there is a driver for it but you'll need to install it. I don't think Ubuntu detects any ISA cards.  Something along the lines of "modconf" should help.

---

### Post by LindsaySlater on 2007-04-24
How, exactly, might I go about using such a command? Bear in mind, I am quite new to Linux, and I am slightly scared of the true powers of the kernel... lol

---

### Post by LindsaySlater on 2007-04-25
Now, here's the funky thing... I have just discovered that there is some sort of system beep... but NOWHERE, can I find anything related to ALSA on here... I checked Synaptic, and it claims that Alsa is installed... but even typing alsa -help in Terminal gets me nowhere... What's going on here? If I need to post any more information, just say so, and where to find it. Thanks again!

---

### Post by enpey on 2007-04-25
Hey Lindsay,

You might want to try following this guide and see if any of this helps...

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Hope you get it all sorted soon
Nathan

---

### Post by LindsaySlater on 2007-05-04
Sorry, I've been trying this over and over and over for the past week... and so far, no luck.. I guess it is possible to live without sound... but it really sucks... Not going to give up though... Does anybody else know where to look???

---

