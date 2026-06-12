---
title: "ESS1869 Help"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by tailsfan on 2006-07-09
Ubuntu will not detect my ESS 1869 Audiodrive soundcard, How do I configure it so that I can get it to work with Ubuntu, I already tried going to [www.alsa-project.org](www.alsa-project.org) and the site is down?

---

### Post by Robert.Zapata on 2006-12-21
I just installed 6.10 on a Compaq Deskpro ENM/P600 w/512 MB RAM and I'm having the same issue.

I'm not 100% sure but I think the sound card is a ESS1869. I'm reading the following info:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ESS+Technology&card=.&chip=ES18xx&module=es18xx)

---

### Post by az on 2006-12-21
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

I also think it's the snd-es18xx driver.  See that page for an explanation of why it's not autodetected.

---

### Post by Riverside on 2007-01-13
I have just installed Dapper on an ancient Compaq Deskpro and had the same issue.  I was fortunate to find the fix here:

[http://ubuntuforums.org/archive/index.php/t-3647.html](http://ubuntuforums.org/archive/index.php/t-3647.html)

The fix is contained in nlogax's posting of April 17th, 2005, 08:12 PM, however he misses something out,  The full fix is:

1.  Create a file in /etc/modprobe.d called snd-es18xx and put the following line in it:

options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

2.  Edit /etc/modules to add snd-es18xx on a line by itself, e.g.:

  ---- begin example /etc/modules ----
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
snd-es18xx
  ---- end example /etc/modules ----

This ensures that module snd-es18xx is loaded each time the machine is rebooted.

3.  Reboot.

That's it!  Sound (via the onboard speaker) on my old Compaq Deskpro now working perfectly.

---

