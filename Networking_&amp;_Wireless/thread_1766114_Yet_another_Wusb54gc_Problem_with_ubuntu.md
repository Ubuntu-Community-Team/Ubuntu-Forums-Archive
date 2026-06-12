---
title: "Yet another Wusb54gc Problem with ubuntu"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by spogman1 on 2011-05-23
Hi all! im having trouble installing windows drivers with ndiswrapper to get the wireless usb adapter to work with ubuntu.

I downloaded some drivers and installed them with ndis wrapper
i got [COLOR="Lime"]this error:[/COLOR] 
> Module could not be loaded. Error was:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

Is the ndiswrapper module installed?

so i hit ok on that window and i get another error, [COLOR="lime"]it reads:[/COLOR]
> Unable to see if hardware is present

Then i hit ok again and it says its detecting the rt2870 driver and it says hardware is present. so i opened the terminal [COLOR="Lime"]and typed:[/COLOR]
> ndiswrapper -l

To see if it really installed. [COLOR="Lime"]this is my result:[/COLOR]

> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
	device (1737:0077) present (alternate driver: rt2800usb)


What do i do?! its installed but still not detecting my usb adapter!! 

[COLOR="Red"]HELP[/COLOR]


(I will post Screenshots of all the scenarios listed if you want!)

---

