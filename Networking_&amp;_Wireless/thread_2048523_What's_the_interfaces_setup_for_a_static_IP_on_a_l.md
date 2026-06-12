---
title: "What's the interfaces setup for a static IP on a linksys router?"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by linuxvstheworld on 2012-08-26
My dad has challenged me to make a linux file server, and I've found out how to set a static ip, but i'm not sure how the beginning should go for a linksys router.
Following code beginning
[PHP]auto lo
iface lo inet loopback
[/PHP]

I don't know if I should change that or not.....

---

### Post by Iowan on 2012-08-26
Leave those two lines...
You'll eventually want the server to get the same address each time. You can either set up a static address, or set up a static lease in the router.

---

### Post by chili555 on 2012-08-27
The usual setup for a static IP is something like:```
auto lo
iface lo inet loopback  

auto eth0
iface eth0 inet static
address 192.168.1.101 [COLOR="Red"]<--an address outside the DHCP range in the router[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1  [COLOR="Red"]<--the procedure for Ubuntu 12.04 and later[/COLOR]
```Of course, substitute your exact details here. Please be sure Network Manager is not installed if you intend to use manual methods.

Post back if you need additional guidance.

---

### Post by linuxvstheworld on 2012-08-28
Thanks guys for the help, but I was wondering if it was possible to set up a static IP using the 'edit connections' option, and set your IP there. Will that work?

---

### Post by chili555 on 2012-08-28
It certainly will. I didn't think you were running Network Manager, also known as the 'edit connections' option, on a server. But if you are, it should work as well.

---

### Post by linuxvstheworld on 2012-08-30
Thanks! Marking this as solved!

---

