---
title: "Broadcom 4312 card stopped working"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by jeremydicicco on 2010-06-11
I have an HP 2133 Mini-Note [KX869AT] with a Broadcom 4312 wireless card. I've had Ubuntu 10.04 on my machine for a few weeks now and everything was great until my wireless card abruptly stopped working. It doesn't detect any wireless networks, much less connect to them. I tried reinstalling the proprietary driver, but that hasn't worked. Any help would be greatly appreciated. Thanks.

Jeremy

---

### Post by snowpine on 2010-06-11
Start by checking the obvious things: Reboot and go into BIOS, make sure networking is enabled in BIOS. Also try if there is a key combination that toggles wifi on/off (Fn+F2 on my laptop).

Another thing you can try, if you recently did a kernel update, is to choose the old kernel from the GRUB menu... does your wifi work with the old kernel?

---

