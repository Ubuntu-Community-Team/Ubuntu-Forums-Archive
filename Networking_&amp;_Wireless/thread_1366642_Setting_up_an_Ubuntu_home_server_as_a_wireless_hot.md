---
title: "Setting up an Ubuntu home server as a wireless hotspot"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by jaredvann on 2009-12-28
So I am thinking about turning an old computer into a home server running Ubuntu to share files across my computers and I have been looking at free software that you can use to turn the server into a  router that provides more control and a built in firewall by having two network adapters. If I did this could I plug a wireless adapter in and use it as a wireless router as well?

---

### Post by shredder12 on 2009-12-30
> **jaredvann said:**
> So I am thinking about turning an old computer into a home server running Ubuntu to share files across my computers and I have been looking at free software that you can use to turn the server into a  router that provides more control and a built in firewall by having two network adapters.
Yes, I think it can be easily done.. you can either use dhcp server and firestarter along with a wireless router to enable internet sharing thru wireless. 
or I am not sure about this one but you may try using the "share with other computers" option in Ipv4 settings in network manager to share internet with other computers on a particular interface
>  If I did this could I plug a wireless adapter in and use it as a wireless router as well?

not sure about this one.

---

### Post by iponeverything on 2009-12-30
> **jaredvann said:**
> If I did this could I plug a wireless adapter in and use it as a wireless router as well?

This depends of whether or not the driver for card supports "AP" mode.  I use atheros card that is using a madwifi driver that does.

---

