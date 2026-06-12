---
title: "Turn off/Change native wireless driver."
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by dpicker on 2006-06-11
I have a Netgear wg111v2 usb wireless adapter and it works out of the box in dapper.

However if i am downloading at fullspeed or the like for some time, then I seem to get disconnected. I have a feeling this could be to do with the adapter getting too hot maybe because it certainly gets hot. In fact it gets hot even when the connection is idle. I end up having to unplug the adapter for a while before being able to get connected again.

Maybe this isnt the reason but the point is my connection is unreliable and it isnt in windows and wasnt in breezy badger using ndiswrapper.

So how do I disable the driver dapper drake uses and switch back to ndiswrapper? I think it uses the realtek RTL8187L chipset (I have also heard the wg111v2 uses prism54? i'm not sure which)

Thanks

---

### Post by torx on 2006-06-12
blacklist it in

/etc/modprobe.d/blacklist

---

### Post by dpicker on 2006-06-12
Yeah but I don't know the exact name of the driver to put it in /etc/modporbe.d/blacklist

---

### Post by Dr. Nick on 2006-07-08
Little late, but if you see this run 

lsmod

from a terminal, Since its a usb card look at the "usbcore" line and it should tell you the module.

---

