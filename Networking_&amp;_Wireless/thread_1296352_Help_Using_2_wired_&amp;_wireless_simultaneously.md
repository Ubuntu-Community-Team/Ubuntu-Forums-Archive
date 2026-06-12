---
title: "Help: Using 2 wired &amp; wireless simultaneously"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by W1nTry on 2009-10-20
I am trying to use my wired connection for access into a LAN and my wireless for internet. There is no DHCP on the wired connection and I have to manually assign an IP address. When I try to do so, it is NOT taking a gateway ip, instead it holds 0.0.0.0. Also once they 2 are connected, I can no longer browse the internet.

---

### Post by t0mppa on 2009-10-20
Why don't you run **netstat -nre** from the terminal and post the results. Also, can you post your */etc/network/interfaces* contents or the terminal commands you're using to set up the interfaces?

---

### Post by W1nTry on 2009-10-21
Here are the results of netstat -nre:

[FONT=Lucida Console]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.69.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
10.189.0.0      0.0.0.0         255.255.224.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.69.1    0.0.0.0         UG    0      0        0 wlan0

[/FONT]*etc/network/interfaces* :
auto lo
iface lo inet loopback

And a screenshot for good measure:
[[IMG]http://img80.imageshack.us/img80/546/networkg.th.jpg[/IMG]]("http://img80.imageshack.us/i/networkg.jpg/")

[FONT=Lucida Console]Just be looking at it I would think it SHOULD work, however once the Wired ethernet port is connected I can no longer browse the internet, though I can access the LAN.
[/FONT]

---

### Post by jward3010 on 2009-10-21
Problem is, network-manager where you're trying to configure the interfaces doesn't support anymore than one connection at a time. You'll have to add this stuff to your interfaces file.

Here's a good example of an interfaces file: [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

