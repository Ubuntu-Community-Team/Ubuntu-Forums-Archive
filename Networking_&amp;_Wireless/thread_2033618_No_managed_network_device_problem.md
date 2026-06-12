---
title: "No managed network device problem"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by caracena on 2012-07-26
Hi guys, first post here.

I've installed Ubuntu 12.04 64-bits on an ESXi 5 host and also installed the desktop. Everything worked fine but I wanted to install it again becouse I'd enable the partition encryption which is a pain in the but for testing purposes.

I deleted the image from the disk (using vSphere Client from another PC), created the new VM and installed again, and again, and again but I can't manage the network from Ubuntu. This is whats happening:

[LIST]
[*]Ubuntu can connect to the internet (I can install stuff and updates)
[*]The MAC address that shows up in Ubuntu is real (I cann see my router assigning a dynamic IP to it)
[*]The Ubuntu VM in ESXi says the MAC is automatic and matches the one that Ubuntu has
[*]Even after I swith from DHCP to STATIC in Ubuntu, the router still assign an IP to it
[*]Even after I assign a static IP to Ubuntu FROM the router using it's MAC address, the router gives Ubuntu a DHCP IP
[*]GNOME says there are no managed devices and no network connection (even after it downloads the updates)
[/LIST]

What can be happening? I've tried the rebuild "70-persistent-net.rules" trick found in [http://ehealth-aussie.blogspot.com.ar/2010/06/static-ip-on-debian-based-guest-vm.html](http://ehealth-aussie.blogspot.com.ar/2010/06/static-ip-on-debian-based-guest-vm.html) but nothing changes.

Any clues? I know this is probably NOT Ubuntu's but ESXi fault but maybe someone here knows what to do? It worked fine the first fresh install.

Thanks in advance!

Cesar

---

