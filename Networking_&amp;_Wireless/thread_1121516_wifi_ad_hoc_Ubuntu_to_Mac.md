---
title: "wifi ad hoc Ubuntu to Mac"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by benotpower on 2009-04-10
Hi,

I'm trying to share my internet connection from my Mac Mini to my laptop running Unbuntu 8.1, using the built-in Airport.

OK for setting up everything on the Mac, "create network" with WEP key, etc.

Wireless card seems to be OK on the Medion laptop (Intel 3945ABG), I can see the network in the network manager.

When I try to connect, the 2 green bubbles turn around for a while, the mouse-over message says "requesting network address from server" or something similar... and then nothing :mad:

Its works on the same machine when booted with Vista.

Any Idea?

Thanks!

---

### Post by superprash2003 on 2009-04-10
you may want to try setting up static ip instead.. when connected in vista.. post output of **ipconfig **from the command prompt..

---

### Post by benotpower on 2009-04-10
so IPconfig returns in Vista :

IPv6: fe80::f4be:94c3:etc... etc.
IPv4: 10.0.2.2
Mask: 255.255.255.0
bridge: 10.0.2.1

But funny thing, I had to edit manually the connection to force WEP identification.

what to do with Ubuntu now?

Thanks!

---

### Post by benotpower on 2009-04-10
also, in Ubuntu Network Tools, cannot see or edit (configure button grayed) the settings for Wlan0.

why?

---

### Post by benotpower on 2009-04-10
_progress :_

got a working connection with IPv4 settings in network manager set to **Link-Local Only**

however, no internet that way :-(

I don't know anything about these IPv4 settings. Tried with the ones I got in Vista on an ipconfig output but no luck...

Where to look?

---

### Post by superprash2003 on 2009-04-11
dont use identical ips.. look under system->preferences->network configuratin

---

### Post by benotpower on 2009-04-11
eh.... sorry but identical to what? network configuration and where? what is IPS?

I don't know where to find the IPv4 settings. I can assign randomly IP, mask, bridge... but DNS and routes? no idea :-(

not that I have not try to read every documentation / wiki on the subject, but really this info is nowhere to be found.

---

### Post by superprash2003 on 2009-04-13
you should not use the same ip address for ubuntu and windows , it would cause a conflict.. when you setup ip address manually enter different ips for both machines..

---

