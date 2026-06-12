---
title: "Ubuntu 8.10 server: how to buit as an router with multiple Static IP"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by kenblat on 2009-03-29
I have an Internet connection (fiber Static IP) that provide 1 Front IP (connect to ISP)
123.234.2.156
255.255.255.252
123.234.2.155 (gw)

then we have another 7 IP (Route IP)
123.234.10.62 to 123.234.10.68
netmask 255.255.255.248
gw 123.234.2.155 (same as Front IP)

That mean if we goto 123.234.2.156 => user @ modem
and if we click 123.234.10.68 => user go through 123.234.2.156 (modem) and stop @ PC have IP 123.234.10.68 (local PC connect to modem) 

For this I config Draytek Vigor 2910 as below
WAN IP 
123.234.2.156
255.255.255.252
123.234.2.155 (gw)

Local IP
192.168.0.1 (enable DHCP)
255.255.255.0
and
Enable Routing IP (this feature at just below Local IP config)
123.234.10.62
255.255.255.248

Result: it's working like a charm! If one PC connect to router and get IP 192.168.0.x (via DHCP) this PC will have Internet IP 123.234.2.156

and another PC connect to router as well but manually config IP as 123.234.10.63 ( to 68 )
255.255.255.248
gw 123.234.10.62
Those PC will have an internet IP as one of those 6 available Static Route IP (this case is 123.234.10.63)

My question is **can we built one server using Unbutu server that have the same features like above**? My old ubuntu server work fine with one static IP + apache + shorewall but i don't know where to start and how to do by this way (multiple static IP both Front and route IP from ISP)

Ubuntu always cost me so much time for playing around. Everytime i finish one project one router (netgear, dlink) just been kicking aout hehhe

---

