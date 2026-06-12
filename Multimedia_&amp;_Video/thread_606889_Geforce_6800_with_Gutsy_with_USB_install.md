---
title: "Geforce 6800 with Gutsy with USB install"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by ydoucare on 2007-11-08
Is there any way to install working drivers for this card on a USB/Persistent install?  As of now, I have to boot with the xforcevesa switch in order to get a working display (limited to 1024x768 of course).  If I do a regular boot either from the liveboot cd or my USB drive, my primary monitor is completely black, and my secondary is completely garbled with vertical lines covering the screen. 

I was really wanting to be able to play with some of the compiz functions without having to partition and install, but i'm not sure what other trouble i'm going to run into trying to get this card to work.

System:
EVGA nForce 3 250
Athlon 64 2800+ (754)
1 GB PC3200
Leadtek GeForce 6800 128 MB AGP
SB Audigy
Ubuntu 7.10 on a USB hard drive, followed instructions from pendrivelinux.com

Any help is appreciated

---

### Post by ydoucare on 2007-11-08
Apparently i'm an idiot, i've tried everything i've found in these forums to get this card to work and it won't, except with the vesa driver. :(

---

### Post by Jovec on 2007-11-08
For what it is worth, I've been able to boot off the live CD and install the proprietary nvidia drivers (pressing CTRL+ALT+BKSP after the install to kill/restart the xserver) and have it run until shutdown.

The corrupted video thing seems to be an issue with the "nv" driver in 7.10 from my limited experience.  It did the same thing for me with a 7600gs (vesa worked only), but the nvidia-glx-new drivers work fine.

Installing the drivers for you card should be as easy as using the Restricted Drivers Manager under System -> Administration from the desktop.  If not, try from a terminal (using CTRL+ALT+F1 if you're seeing the X screen corruption) with "sudo apt-get install nvidia-glx-new" Once installed, CTRL+ALT+F7 will get you back to the X server (which you'll then have to kil)l, or "sudo /etc/init.d/gdm restart"

---

### Post by ydoucare on 2007-11-08
> **Jovec said:**
> For what it is worth, I've been able to boot off the live CD and install the proprietary nvidia drivers (pressing CTRL+ALT+BKSP after the install to kill/restart the xserver) and have it run until shutdown.

The corrupted video thing seems to be an issue with the "nv" driver in 7.10 from my limited experience.  It did the same thing for me with a 7600gs (vesa worked only), but the nvidia-glx-new drivers work fine.

Installing the drivers for you card should be as easy as using the Restricted Drivers Manager under System -> Administration from the desktop.  If not, try from a terminal (using CTRL+ALT+F1 if you're seeing the X screen corruption) with "sudo apt-get install nvidia-glx-new" Once installed, CTRL+ALT+F7 will get you back to the X server (which you'll then have to kil)l, or "sudo /etc/init.d/gdm restart"

Yeah, i've tried installing from the restricted drivers manager, no go.  I've also tried installing from nvidia-glx from the terminal (not sure if the 6800 is supported under nvidia-glx-new?), no go there either.  After installing nvidia-glx it errored with "No Screens Found" upon starting X.  Re-ran xorg config a few times, but no dice there either.  Tried Envy too.  Also, if i let it just boot up with the corrupt display, I can't see the terminal either after hitting CTRL+ALT+F1, it's a complete garbled mess as well.   I suppose i'll just partition and do a real install and work from there.  

Thanks though

---

### Post by Jovec on 2007-11-08
> **ydoucare said:**
> (not sure if the 6800 is supported under nvidia-glx-new?)

Not sure if the only difference between nvidia-glx and nvidia-glx-new is just driver versions, although nvidia-glx-legacy is needed for everything earlier than a geforce 4 I think.  I'd try both -glx and -glx-new for your card.

If you have the nvidia-glx[-new] packaged downloaded and installed, try starting from scratch with "sudo dpkg-reconfigure -phigh xserver-xorg" From there, I suppose there are various ways to do the same thing:

- manually edit xorg.conf and change "vesa" or "nv" to "nvidia"
- sudo dpkg-reconfigue nvidia-glx[-new]
- sudo nvidia-glx-config enable
- gksudo nvidia-settings from inside X

post some logs/xorg.conf

Finally, do you have two monitors connected to your 6800?  Try unplugging one until you get the nvidia driver working.  I want to say that I had this same issue on my 7600gs with a fresh 7.10 install - two monitors connected resulted in a garbled X screen (outside of vesa driver), I unplugged one and got the nvidia driver working, then rebooted with the 2nd monitor and configured twinview.

Also, may be a dumb question, but do you have an F-lock key that needs to be enabled for your F keys to work?

---

### Post by ydoucare on 2007-11-08
Oddly enough, right after posting I decided to give it another try, this time it installed and worked fine just using the restricted driver manager.  And yes, I do have dual displays, got them setup with TwinView too.  Thanks for your help.

---

