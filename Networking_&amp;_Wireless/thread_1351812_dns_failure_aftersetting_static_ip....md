---
title: "dns failure aftersetting static ip..."
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by grambo on 2009-12-10
before i get started, yes i blame my router, but my wife likes vonage...

long story short, my dlink wireless n router died and I've had to resort to using a WRTP54G as my router.  It does not support IP reservations, so to use any of its port forwarding I have to setup my ubuntu box as a static ip.  Quick note on the system, it's an Asus EEEBox with an Atom processor, original install was 8.10, but was upgraded to 9.10 a couple weeks ago.

I modified /etc/network/interfaces to read as follows:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 10.0.0.2
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1

a quick "sudo /etc/init.d/networking restart" and the ip is set, no problem, but there's no more dns.  So I tried editing /etc/resolv.conf only to find that it is being ignored since /usr/sbin/named is running.  So then I modify /etc/bind/ to read as follows:

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
server 4.2.2.4

...and still no dns.  Am I doing something blatantly wrong here?

---

### Post by gordintoronto on 2009-12-11
I think it's

nameserver 4.2.2.4

---

