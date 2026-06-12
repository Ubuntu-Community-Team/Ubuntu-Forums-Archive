---
title: "blacklist snd_aw2 does not work"
date: 2009-01-11
forum: Mythbuntu
---

### Post by orlande on 2009-01-11
I want to use DVB-S2 card Technotrend budget-pci-320 with chip SAA7146. mythbuntu does not load the correct driver.

# lspci -vnn
03:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7146 [1131:7146] (rev 01)
Subsystem: Technotrend Systemtechnik GmbH Device [13c2:1019]
Flags: bus master, medium devsel, latency 32, IRQ 3
Memory at fdcfe000 (32-bit, non-prefetchable) [size=512]
Kernel modules: snd-aw2

Although the module snd_aw2 is blacklisted, snd_aw2 does not want to go away.
/etc/modprobe.d/blacklist
and
blacklist-oss -> /lib/linux-sound-base/noOSS.modprobe.conf
contain a line: blacklist snd_aw2

What else can I do to permanently remove the module snd_aw2?

---

