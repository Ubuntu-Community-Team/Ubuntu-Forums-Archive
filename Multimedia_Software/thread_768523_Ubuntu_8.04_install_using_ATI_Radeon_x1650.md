---
title: "Ubuntu 8.04 install using ATI Radeon x1650"
date: 2008-04-26
forum: Multimedia Software
---

### Post by mjdorman321 on 2008-04-26
I have a HP Vectra VL400 running Ubuntu 8.04 LTSP server, with a problem. I used the S-Video-out of the  ATI Radeon x1650 I retrofitted into the PC to install Ubuntu in text-based mode. That worked fine, but when I rebooted, the splash screen appeared, and then the output stopped. I couldn't get a text prompt either. 

When I pressed the power switch to hard reset, the splash screen reappeared for the shutdown sequence. I booted in recovery mode, which worked, and tried to fix the xserver with the onscreen prompt. This didn't work.

Any ideas?

---

### Post by alof8k on 2008-06-29
I have the issue with the x1650 pro (512MB agp). I was able to install the liveCD but once i'm on a newly installed copy of ubuntu (hd), I cannot enable the ati driver via the restricted drivers applet.  it installs it fine, but the minute I reboot like it asks me to, then ubuntu doesn't even load! I tried to boot into recovery mode, and use the "fix x server" program and then boot into ubuntu.  this time, atleast I am able to get into the log in screen, but once I enter my username and password, then all I see is a white screen and my mouse courser.  It doesn't move from there.

Teh only "solution" i've found is to reset the system manually and then go back into the recovery mode.  but this time, choose "go to root prompt" and then use:

```
apt-get remove xorg-driver-fglrx
```

then rebooting the system and going into ubuntu allows me to atleast get into the desktop (but again, back to no 3d acceleration).

---

### Post by daedalas1981 on 2008-07-25
Same issue. 

Radeon x1650 Pro AGP 512 MB

The keyword is AGP. Seems to always not be supported.

I've done a fresh install of Hardy from a DVD and had the automatic VESA drivers work. But I can't use compiz or normal desktop effects. If I install the proprietary driver, I get the black screen of Death. If I use eNVY after a clean installation, I get the Login Screen, but then I get the white screen of Death. If I do a fresh install and use the latest driver from AMD's Ati Driver section, I get (3) screen flashes prior to the login screen, a pop-up window that says I have to re select a Video Card and Display, which only leads to low resolution mode.

I've removed Hardy and did a fresh install of Gutsy from a DVD. I can get the proprietary driver working without any screen problems, but I still can't use compiz or normal desktop effects.

AS I SAID earlier for you fast response people, AGP. I've heard that the PCI-e works, and there are demos on YouTube, But AGP is still out of the loop. I heard there is something you got to do to the AGPgart according to ATI. I don't know what AGPgart is, but it might help???

Sending out a S.O.S.

Please help out ATI AGP issues. Or Atleast help us get Compiz going.

---

