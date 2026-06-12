---
title: "Both wired and wireless not working in Edubuntu 9.10 on HP netbook"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by bhwong on 2009-11-05
Wired issue: When I plug in or out the LAN cable in Ubuntu, nothing happen. But when I plug in before I boot up Ubuntu, it works! However, if I plug out, Ubuntu freeze! Why?

Wireless issue: Wireless cannot be found. When I run Hardware Driver from the System > Administrator, it prompt me to select one of the 2 available Broadcom wireless driver - B43 and STA. STA is proprietary and failed to get installed. B43 (fwcutter) is free and I have activated. But nothing happen as well.

---

### Post by albandy on 2009-11-05
I'm having the same problem with my hp netbook.

I've not solved the wired problem but I solved the wifi one.

Start wired
open a terminal
type sudo jockey-gtk
select the 2nd driver
when finished reboot

now you wifi should work

---

### Post by bhwong on 2009-11-06
I select the 2nd driver and it can't even boot up! Yet when I boot up from the DVD and reboot from harddisk, it boot up again. So weird!

---

### Post by CoolDreamZ on 2009-11-08
This thread may have the solution [1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

