---
title: "no sound with intel hda audio and 64-bit jaunty"
date: 2009-07-16
forum: Multimedia Software
---

### Post by wizard10000 on 2009-07-16
Known issue from what I can see, but the Fedora fix posted to Launchpad (adding /etc/modprobe.d/snd-hda-intel.conf) doesn't work, just as it didn't for some users there.

Motherboard is Gigabyte GA-EX58-UD3R running a Core i7 920 - lspci says sound chipset is Intel 82801JI.

Anybody got a fix?

thanks -

---

### Post by wizard10000 on 2009-07-19
Solved.  The problem was policykit - some upgrade in the last week denied access to soundcard and TV tuner card.  Fixed now.

---

