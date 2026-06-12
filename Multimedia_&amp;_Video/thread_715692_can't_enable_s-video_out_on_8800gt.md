---
title: "can't enable s-video out on 8800gt"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by asparker on 2008-03-05
I've been struggling with 7.10 64bit for awhile now but I'm getting closer. The thing I can't get working is the S-video out. In the Nvidia settings, twinview is gray and unclickable and I haven't been able to find any solutions on the forums.


[INDENT]Here's what I've got:

Gigabyte G33M-DS2R
Core2 Duo E6750 @ 3.4ghz
Generic 1gig 1066 RAM @ 1020ghz   X2
AVA Forsa 8800gt with 512 MB
Ubuntu 7.10 64bit[/INDENT]


I think I've narrowed the problem down to two possible causes but I'm new to Linux and am not sure where to go from here.


_Possibility 1 - Could it just be a poorly written driver?_

I had some problems with the Nvidia driver in XP. It couldn't automatically detect my TV and it wouldn't let me change the settings on my own. I had to run a registry hack that allowed me to override the S-Video out signal settings and force NTSC. On my Ubuntu install, I couldn't manually install the driver (explanation below) so I used Envy to install NVIDIA-Linux-x86_64-169.12-pkg2. Could my current problem be similar? Is there a workaround?


_Possibility 2 - I had some major install issues, Could it be something deeper that messed up during installation?_

I had a lot of trouble installing Ubuntu via the live CD or the alternate install CD. My machine would show "Kernel direct mapping tables up to 100000000 @8000-d000" and then reboot. I managed to get past this by installing in low graphics mode at 800x600x16 but after rebooting the same thing kept happening. I did some searching and though I'm not sure why, adding the "vga=771" boot parameter every time makes Ubuntu boot right up.

I ran the update manager and then tried to manually install the Nvidia drivers unsuccessfully. Neither Ctrl+Alt+F1 nor booting into recovery mode seem to be working properly. The screen just goes black and everything freezes. From what I understand (I'm new.) I need to do this so I can install my drivers in text mode. 

Eventually I broke down and used Envy to install the NVIDIA-Linux-x86_64-169.12-pkg2 driver. Except for the fact that I have to add the "vga=771" boot parameter and I can't seem to run in text mode, everything but twinview seems ok. Compiz fusion is great and as far as I've noticed so far, all 3D acceleration is working.

If there's a problem with X server or some other part of the GUI that's causing the twinview issue, does anyone know how I could fix it?

Wow, that got long FAST! I tried to be as through as I could be. Thanks in advance to anyone who can help me. I've been trying to move to Ubuntu for awhile now but every machine I own seems to have it's own difficulties and I end up sticking with XP. Hopefully not this time...

---

### Post by xc3RnbFO8P on 2008-03-05
> Possibility 2 - I had some major install issues, Could it be something deeper that messed up during installation?

Yes, install again.

---

### Post by asparker on 2008-03-05
> **Ringi said:**
> Yes, install again.

I wanted to avoid that because it takes time and I'm pretty sure I'll just run into the same install issues but you're probably right.

I'll try the alternative install disk again and if that doesn't work I'll pull out my Nvidia card and try installing my with onboard Intel graphics chip instead.

---

### Post by xc3RnbFO8P on 2008-03-06
Burn a new Ubuntu CD (8x), dont use wireless (usb) when you install. Check Cd before you install.

---

