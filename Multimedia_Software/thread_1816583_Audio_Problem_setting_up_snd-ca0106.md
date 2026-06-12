---
title: "Audio: Problem setting up snd-ca0106"
date: 2011-08-02
forum: Multimedia Software
---

### Post by blind3r on 2011-08-02
Hello everyone, 
I've been trying to setup my Creative Labs CA0106 Soundblaster on a Ubuntu 11.04 64bits.

I've followed the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") and others and the problem persists. It recognizes the HDA controller from the nvidia card and loads the correct module, I've tried to unplug the nvidia card and reconfigure alsa but still no luck.

Ubuntu recognizes the soundblaster card, but the snd-ca0106 module doesn't load. I've already tried to compile alsa and the same problem happens.
[http://www.alsa-project.org/db/?f=d273675121101fded3c7babebfa2e6dcd00840f2](http://www.alsa-project.org/db/?f=d273675121101fded3c7babebfa2e6dcd00840f2)

This configuration is after a clean install of ubuntu. If I try to run sudo modprobe snd-ca0106 the console hangs and only Ctrl-C stops it.

Help would be very appreciated, thank you.

---

### Post by blind3r on 2011-08-02
pretty please?

---

### Post by blind3r on 2011-08-03
bump!

---

### Post by blind3r on 2011-08-08
Really, someone out there must have some ideas on this, I've tried everything I could find but I must be missing something. 

Thank you for your time.

---

### Post by timmyd983 on 2011-09-01
I have the exact same issue

---

### Post by timmyd983 on 2011-09-01
edit /etc/default/grub and change the line to include "pci=use_crs":

GRUB_CMDLINE_LINUX_DEFAULT="splash pci=use_crs"


run 'sudo update-grub'  and reboot.

fixed it for me.

---

