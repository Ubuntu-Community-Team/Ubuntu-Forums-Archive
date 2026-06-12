---
title: "Kubuntu /etc/network/interfaces"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by GavinWalker on 2012-10-01
I've googled and had a search on /etc/network/interfaces  and all the various items I can find say it should read something like 
auto lo
iface lo...etc
auto eth0 ....etc
iface eth0 ..etc

Mine only reads 
auto lo
iface lo inet loopback


with no eth0 setup. However eth0 seems to work fine and it eth0 appears as you'd expect on ifconfig. I'm curious as to why it works without the eth0 being setup in the interfaces file. Is this a default setting or something to do with the way udev has set it up. The OS is Kubuntu 12.04 . Thanks in advance

---

### Post by bkratz on 2012-10-01
this is all that is in mine

auto lo
iface lo inet loopback


If you are using (K)network manager, I believe this is correct.

---

### Post by Iowan on 2012-10-01
> **GavinWalker said:**
> I'm curious as to why it works without the eth0 being setup in the interfaces file.I haven't tried Kubuntu, but I suspect there's a Network Manager-type program that's handling things...

---

### Post by mikewhatever on 2012-10-03
That file is used to configure networking on servers and machines that have no Network Manager. If you wish to use it, by all means, please do. It will work.

---

