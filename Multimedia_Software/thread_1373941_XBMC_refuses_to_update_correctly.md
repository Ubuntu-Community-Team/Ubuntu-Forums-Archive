---
title: "XBMC refuses to update correctly"
date: 2010-01-06
forum: Multimedia Software
---

### Post by MeBrains on 2010-01-06
28/12/2009 I installed Ubuntu minimal AMD64 and followed the following guide to install it as an HTPC using XBMC. Note that that date was after XBMC's 9.11 official release.

Guide: [http://www.springydevelopment.co.uk/2009/11/08/minimal-install-of-xbmc-on-ubuntu-karmic-koala/](http://www.springydevelopment.co.uk/2009/11/08/minimal-install-of-xbmc-on-ubuntu-karmic-koala/)

... give and take really minor adaptions, since the guide is not entirely 1 on 1.

The process installed XBMC Beta 1 though.

Now, when I do:
- sudo apt-get update / upgrade

The result is:
```

The following packages have been kept back:
  xbmc xbmc-common xbmc-scripts-example xbmc-skin-confluence xbmc-skin-pm3-hd
  xbmc-web-pm3

```- sudo aptitidu upgrade -> results in:
```

The following packages have unmet dependencies:
  libsdl1.2debian-alsa: Conflicts: libsdl1.2debian-pulseaudio but 1.2.13-4ubuntu4 is to be installed.
  libsdl1.2debian-pulseaudio: Conflicts: libsdl1.2debian-alsa but 1.2.13-4ubuntu4 is installed.

```- sudo aptitude -> g -> results in a list of 45 files which will be automatically removed. Some of these are libvdpau1, pkg-config, pmount, xinit, xserver-common, xserver-xorg, *-core, *-input-all, *-evdev, *-mouse, *-synaptics etc. A lot of which are needed as aptitude reports by the package xbmc-common, which I suppose XBMC needs to operate.

I do not want to "autoremove". I did that before and that resulted in having a corrupted system and hence the new installation of 28/12.

Any idea what is wrong? Why wasn't the official release installed and was Beta1 chosen instead? Why does Aptitude propose to have all these necessary packages deleted? And of course, why am I not able to upgrade to XBMC's latest and final version? How can I?

---

### Post by MeBrains on 2010-01-07
not a single reply... not even - I have the same problem...

* bump *

---

### Post by MeBrains on 2010-01-09
I still have the same problem.

xbmc's final release is now almost three weeks old and it will not update correctly...

---

### Post by MeBrains on 2010-01-12
why is this not getting any replies? somebody must have some clue and / or experience the same problem?! I searched through the forums already (before posting this thread!) and found lots of persons with the same problem, but with no definite answers!

I already tried launchpadding this, but the site failed...

---

### Post by jbird80 on 2010-01-12
I have experience the same issue I just haven't had time to sit and trouble shoot... Maybe this weekend. I will post any solutions I come up with.

---

