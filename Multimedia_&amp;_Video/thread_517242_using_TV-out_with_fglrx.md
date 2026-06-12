---
title: "using TV-out with fglrx"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by Vonagio on 2007-08-04
I have installed fglrx OK, everything works fine on my monitor but I don't know how to set up xorg.conf (if that is actually what needs changing) to enable tv-out. I have been searching for a few hours and I'm unable to find any articles/threads that explain this.

I have an ATI X1250 with outputs: DVI, VGA, HDMI, S-Video/VHS, RCA video out (on Asus M2A-VM HDMI motherboard). DVI and VGA work fine, I cannot get output on the RCA or s-video, and have not tested HDMI. If possible I would like to use the RCA connected to a scart adaptor or RCA input on a PAL-I television as the main display (this is a mythtv box).

I am not very good with xorg.conf or indeed with ubuntu as a whole, so please explain thoroughly! Thanks

---

### Post by Kubunteando on 2007-08-05
Try to check the command aticonfig in a console.

That may help you.

---

### Post by hg42 on 2007-08-07
you know, you have to enable HDMI in the BIOS?
Hmm, it was on by default on my board, but perhaps you or someone else disabled it?

---

### Post by Vonagio on 2007-08-07
I've tried playing around with some settings in aticonfig, but the xserver crashes whatever options i choose.

hg42: Are you running feisty on the same mobo? could you show your xorg.conf, I assume mine will be almost identical (maybe the tv area and monitor size will be different - I am in PAL-I and using a 12x10 resolution). I have enabled the HDMI port and switched the tv-out to PAL in the BIOS.

Thanks (I would post my working xorg.conf but its the standard fglrx (using aticonfig --initial).

---

### Post by Vonagio on 2007-08-13
I've still not had any luck with using tv-out. Can anyone help some more?

I will need to use it over s-video because I don't have any hdmi capable tvs.

Thanks

---

### Post by tseliot on 2007-08-13
> **Vonagio said:**
> I have installed fglrx OK, everything works fine on my monitor
Which version of the driver did you install?

---

### Post by Vonagio on 2007-08-13
I've tried both 8.28.8 and 8.39.4 with Envy and just the latest with apt-get. I do sometimes have problems with mythtv playback (it stutters) so this might be part of the problem. It is very hit-or-miss :confused:

---

### Post by Vonagio on 2007-08-13
Now I'm totally stuck, I've tried installing from apt-get, installing with envy and installing from the ati site.

With the initial install from apt-get I got the correct output from fglrxinfo, it installed driver 8.28.8. Playback in Mythtv was impossible (with about 1 frame a second).

Installing with envy both 8.28.8 and 8.39.4 resulted in the same thing.

Installing with the driver package from the ati site outputted the mesa3d from fglrxinfo, and playback is a little better but is still too slow (i guess about 10-15fps).

Now I'm stuck with mesa3d whatever I try and do...

Oh and I can't use the opensource driver included in xorg....

Any help just getting smooth playback would be great, let alone tv-out :mad:

Thanks

---

### Post by theRealGBee on 2008-05-03
This thread is a little old, but I figure that anyone looking for information and finding it in a google search would appreciate an update.

I have a Radeon X1250 based board. Using version 8.4 (April 2008 ) of the fglrx driver, compiled and installed using the official installer, I have TV-Out using S-Video working just fine and MythTV video is perfect too. 

XVideo support wasn't added for this chipset until version 8.3 and MythTV depends on this for video playback. 8.3 was released in March 2008 but 8.4 was the first version which just worked perfectly. I've no idea what driver version Hardy ships with, but I'd recommended using the official installer instead as that guarantees you get the latest version - [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

To avoid confusion over version numbers, they changed the numbering scheme last year. 8.39.4 was followed by 7.11, 7.12, 8.1 etc with the major version number referring to the year (2007) and the minor version number the month.

P.S. The opensource driver didn't work for me and given the rapid progress and great tools (amdcccl) of the proprietary driver I'd recommend trying that first.

---

### Post by laga on 2008-05-03
As a follow-up to theRealGBee's posting: it's probably a better idea to use envy-ng instead of installing the driver directly from ATI's website. Envy-ng retains the magic that makes the drivers actually work on an Ubuntu system :)

---

