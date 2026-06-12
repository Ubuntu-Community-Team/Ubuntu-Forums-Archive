---
title: "Force Ubuntu to use eth1 instead of eth0"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by grapnell on 2009-08-12
I have a broadcom built-in card on my motherboard, and the b44 driver continually disconnects.  as far as I know, this is a known problem.  I have installed a second card, an intel card, in which ubuntu recognizes perfectly, and dhcp assigns an IP address to it with no problem, however, it seems that ubuntu still tries to use the eth0 card instead of the new eth1 as its default.  How do I tell ubuntu to forget about eth0 and use eth1?

Thanks for any help.

---

### Post by grapnell on 2009-08-12
bump? anyone?

---

### Post by superprash2003 on 2009-08-12
try this [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by kerry_s on 2009-08-12
you need to edit /etc/udev/rules.d/70-persistent-net.rules

you should find your devices listed in the order they were detected, on the end will be NAME="eth0" just change it to NAME="eth1" & the other to NAME="eth0", reboot and it should be all good.

---

### Post by Iowan on 2009-08-12
There *might* be a way to effectively disable eth0 by defining it in */etc/network/interfaces* as "manual", and leave eth1 under NM control. I haven't tried it, so ...

A BIOS disable might also be effective.

---

### Post by slakkie on 2009-08-12
You can change the metric of the interface so it will prefer the intel over the broadcom. Lower metrics take precedence over higher ones.

---

