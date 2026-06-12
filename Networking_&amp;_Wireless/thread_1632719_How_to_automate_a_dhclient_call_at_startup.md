---
title: "How to automate a dhclient call at startup?"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by smantscheff on 2010-11-28
For test purposes I'm running Ubuntu 10.10 from a USB stick with a USB WLAN stick.
The system finds the WLAN router and acquires an IP6 address, but no IP4 address.
With "dhclient wlan0" though it does get an IP4 address and connects o.k.
How do I setup the system so that this dhclient call is done by the system at startup (or whenever it is necessary)?

---

### Post by uncaspi on 2010-11-29
If you mean running live cd from a pendrive, it cannot be done due to the livecd files are copied to the ram of the pc and everything you save on the ramdisk are lost when you reboot.

---

