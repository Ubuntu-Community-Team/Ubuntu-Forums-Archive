---
title: "How to remove an interface (tun0)"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by alohs on 2010-09-20
Hey there,
i  am using openvpn on my laptop. I had to give the laptop for repair so i swapped the hdd in another laptop.

Now i have a tun0 relict in my system, so openvpn creates a tun1 interface and messes up all the routes.

So i am wondering how can i delete the tun0 interface from my ubuntu?

---

### Post by Iowan on 2010-09-20
I'm not sure if that is defined in */etc/network/interfaces*.   Otherwise, check */etc/udev/rules.d/70-persistent-net.rules*.

---

### Post by alohs on 2010-09-21
In both are only the eth0 and the loopback interface listed.
However i find the tun0 interface in following places:
"/sys/devices/virtual/net" - there is a file for tun0 ( looks like a config file?)
"/sys/class/net" - there is a link to the config file, can't delete or move the link even with root rights.

"mv: cannot remove `tun0': Operation not permitted"


:confused:

---

### Post by alohs on 2010-09-21
I fixed the Problem, through reinstalling openvpn

---

