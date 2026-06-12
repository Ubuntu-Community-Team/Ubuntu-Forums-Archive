---
title: "No Wlan0"
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by TecSoft on 2006-01-28
I need help for a new problem that has come up. I have succesfully installed NDISWRAPPER 1.1. I added my .inf file using NDISGTK. I did ndiswrapepr -m and modprobe ndiswrapper and those worked. Now when I do iwconfig there is no wlan0. And on the other ones it says no wireless... What can I do to get my wlan0 to show up so I can configure my connection?

---

### Post by Lambert on 2006-01-28
Not knowing what chipset/driver you're using with ndiswrapper, did you also copy the .sys file or a .bin  into the same directory as your .inf file? If no interface is showing up then the driver is not functioning and something is missing or it's the wrong driver for that device.

Sometimes you have to try a few different drivers to find the one that works for your device. If there's one available on the ndiswrapper wiki (list page)  use that one for your device as it's been verified to work. If you pulled from your cd, these don't always work.

---

### Post by TecSoft on 2006-01-28
I read the WIKI and it said for NETGEAR WG121 to get V2.00 on the CD that is what I have V200. I installed that driver. IN the driver folder there is a .cat file(i think).inf and .sys

---

