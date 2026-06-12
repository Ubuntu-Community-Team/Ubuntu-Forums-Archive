---
title: "printer usb/Apple Time Capsule on a subnet"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by alexKleider on 2009-08-12
I've read the archives pertaining to setting the ability to mount the TC volume onto a linux machine ([http://ubuntuforums.org/showthread.php?t=670535&page=2](http://ubuntuforums.org/showthread.php?t=670535&page=2) -'ytene' posted a very clear solution in the spring of '08) but I have another hurdle to overcome: the TC is connected to my local area network (10.0.0.0) (via a hub, NOT directly to my aDSL Modem) and has been assigned (by my DHCP server) the address 10.0.0.7. The Mac computer (OS X) connected to it has been assigned an address on a different network (10.0.1.0). It seems clear then that the router component of the TC has set up a subnet for itself or atleast for the Mac. There is a printer attached (by usb) to the Time Capsule and I'd like to use it from my linux laptop connected to the 10.0.0.0 network. I have the printer's url as seen from cups running on the mac. So there are two issues:
1. how to mount the TC when it is on a subnet
2. how to configure cups on the laptop so that it can be a client of the printer attached by usb to the Time Capsule.
The latter is actually of more interest to me than the former but somehow my sense is that the former may be necessary as a first step towards the latter.
cheers,
ak

---

