---
title: "Problems with Ethernet-USB adapter and ASIX driver"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by Horaci on 2009-04-28
I'm having some trouble getting my dlink dub-e100 adapter to work and I'm looking for some clues as to where to look next and hopefully avoid a system reinstall.

The thing is, if I boot with the ubuntu 7.10 CD, the adapter is detected and it seems to work just fine. The kernel used is 2.6.22-14-generic.

The problem comes if I boot with my installed ubuntu, which is the same as the CD plus many updates. For some reason dmesg reports:

asix: disagrees about version of symbol usbnet_unlink_rx_urbs
....

The kernel used is 2.6.22-16-generic.

Given that the live CD works fine, would there be any way of somehow reusing the driver that comes with the live CD on my "real" harddrive install, or at least start comparing things from there to hopefully find the root of my problem?

Ubuntu newbie here; any help will be appreciated.

---

