---
title: "Radeon HD 2600 driver Failure Help?"
date: 2009-04-04
forum: Multimedia Software
---

### Post by shnurui on 2009-04-04
I'm trying to get my ATI Radeon HD 2600 XT AGP 512 to run on this donated mb, Ubuntu installs and runs fine but If i turn on the legacy driver, it BSODs on me when I reboot.

The driver from ATI doesn't specifiy if it is AGP or PCI or PCIe, so I'm not sure I'm even downloading the right catalyst driver.

And the autoupdated one is the one that crashed my system:/

Once I've reinstalled I can get the specs from that machine:/

And of corse I don't know if the audio portion is working because I don't have a monitor with HDMI audio in.

---

### Post by shnurui on 2009-04-05
Once I've got it to black screen I've figured out how to get it to not freeze.

Hit the grub, fix, choose fix xserver from the grub menu, reboot.

Now how do I install this .run file, Envy isn't working.

---

### Post by shnurui on 2009-04-05
Once I've got it to black screen I've figured out how to get it to not freeze.

Hit the grub, fix, choose fix xserver from the grub menu, reboot.

Now how do I install this .run file, Envy isn't working.

---

### Post by shnurui on 2009-04-05
==hit the grub
hit Escape to access the grub,
choose a Recovery mode,
Select Fix Xserver
Reboot,
option failsafe Gnome
log in

If you don't you'll get the Blizzard-
And why is it I have to awnser my own questions?

---

### Post by xc3RnbFO8P on 2009-04-05
Read this:
[http://ubuntuforums.org/showthread.php?t=1114048&highlight=reinstall+video+driver+terminal]("http://ubuntuforums.org/showthread.php?t=1114048&highlight=reinstall+video+driver+terminal")

---

### Post by shnurui on 2009-04-06
apparently half the problem was I was still in hardy(8.4) upgraded to iberion and now the linux driver installs fine, but freezes the computer when I try to access anything.

---

