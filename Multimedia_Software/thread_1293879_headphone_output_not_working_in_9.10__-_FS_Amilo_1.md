---
title: "headphone output not working in 9.10  - FS Amilo 1705 with VIA VT1708"
date: 2009-10-17
forum: Multimedia Software
---

### Post by Vaphell on 2009-10-17
i installed 9.10 on Fujitsu Siemens with VIA chipset, it works just fine but...
headphone jack mutes laptop speakers but there is no sound.

Issue is quite old. I had similar problem with 8.04, but in the case of Hardy i could make it work by downloading alsa sources, patching one file and performing the 'configure/make/make install' combo.

How to make it to work on 9.10? Tutorials i used in the past are unlikely to work - structure of kernel directories with drivers seems to be different so i can't follow them word by word. Any ideas?

/rant: why have these changes not been included in the official alsa for 2 years if not more? Is every user of these crappy via chipsets doomed to do manual labor every time he installs OS?

---

### Post by SeePU on 2009-10-26
Did you get it to work yet?

I was wondering if the VIA VT1708S audio chipset works in Linux (Ubuntu or whatever distro).  Maybe you need a certain kernel?

I checked the ALSA website and it looks like there is support with more recent versions of ALSA.

Make sure you have ver. 1.0.18rc3 or later?  ALSA is now at 1.0.21 so it should work out of the box?

---

### Post by Vaphell on 2009-11-03
no i haven't. god damn via chipsets :/

---

