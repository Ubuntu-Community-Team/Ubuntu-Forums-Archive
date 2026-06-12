---
title: "dual homed host help?"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by bootzz42 on 2009-02-23
Hello all, this is my first ever post, so don't beat me up to much....
ive searched and searched but i cant seam to find a solution that works for me...


ok, so i have a old dell box(server edition 8.10) that I am planing to install snort on and put between my my router and my LAN. 

So my problems start with configuring /etc/network/interfaces....
i found this guide to help me out [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

so i edited the interfaces file to:



auto lo
iface lo inet loopback

auto eth0 eth1
mapping eth0 eth1
     script /usr/share/doc/ifupdown/examples/get-mac-address.sh
     map aa:bb:cc:dd:ee:ff net
     map 11:22:33:44:55:66 lan

iface net inet dhcp
     
iface lan inet static
     address 10.o.o.1
     netmask 255.255.255.0
     


then when i run .../networking restart    it fails

any suggestions????

---

### Post by darsque on 2009-02-23
Is your setup really set to 10.o.o.1 as these should be 0 zeros not the letter o.

---

