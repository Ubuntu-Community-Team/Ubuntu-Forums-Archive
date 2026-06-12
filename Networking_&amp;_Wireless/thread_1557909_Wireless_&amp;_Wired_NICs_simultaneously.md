---
title: "Wireless &amp; Wired NICs simultaneously"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by Cacks on 2010-08-21
Hi Guys,
 
I'm running Ubuntu 10.04 Server. I can't get my Wireless Card & Wired Card to work at the same time. My interfaces file is incorrect, when I comment out 1 of the interfaces the other works. I have attached my interfaces file. What am I doing wrong?
 
Cheers for any help
 
 
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto wlan0
iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1
wireless-essid XXXXXXX
wireless-mode Managed
wireless-keymode restricted
wireless-key XXXXXXXXX
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1

---

### Post by Iowan on 2010-08-21
Two interfaces in the same subnet tends to cause problems (and violates Spanning Tree Protocol), but you might be able to bridge them...
Ordinarily, the "network" ends with "0" (eg. 192.168.1.0), but network and broadcast addresses are optional.

---

### Post by magog45 on 2010-08-21
I'm having the same trouble I believe with a Gateway laptop running 9.04, wired connection works fine but not wireless. My interfaces file only shows the loopback device but running lspci -v in terminal shows both wired and wireless controller. I'll keep an eye on this thread, hopefully someone will know the answer or I might even figure it out

thx

---

