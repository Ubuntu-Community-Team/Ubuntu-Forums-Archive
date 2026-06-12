---
title: "Sharing PC Internet with Cell Phone via bluetooth"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by ahmed.s.m on 2009-09-15
Hi all!

I want to share my dial up Internet connection with my P1i via bluetooth :) I read some article from blogs and web sites, but I can't use my computer's Internet connection in my smartphone.

My computer's information:

Distribution: Kubuntu 9.04 with KDE 4.2.2
Linux kernel version: 2.6.28-11-generic
Modem: Conexant HSF
Dialup network device: ppp0

At first, I installed "Firestarter" and "Blueman Applet"(because I don't like KBluetooth4 :) ). In Firestarter's preferneces window and Firewall==>Network Settings part, I choosed "Dialup device (ppp0)" as Internet connected network device and also "Unknown device (pan0)" as local network connected device. I checked "Enable Internet connection sharing" and "Enable DHCP for the local network". In Blueman Applet's Local Services window, I check the "Network Access Point (NAP)" box in Services part. I think I used the default settings in "NAP Settings" part: DHCP server type: dnsmasq, IP Address: 192.168.0.1 and checked "Enable Routing (NAT)" box.

In my P1i's "Internet accounts", I created a new account named "BT" (short for BlueTooth ;) ) and in Its "Devices" tab, I added my computer's Bluetooth (ahmad-desktop). In "IP config" part, I choosed "IPv4" and I entered "192.168.0.1" as the "IP address" and "255.255.255.0" as the Gateway (I left Netmask number). When I want to connect to the Internet via bluetooth while I'm using my computer's dialup connection in Kubuntu, the default web browser (or some others like Opera Mobile and Opera Mini), it tries to search and find computer's Bluetooth and I choose "ahmad-desktop", but the P1i doesn't connect to the Internet.

Could you help me? :)

* I think it should be solved with iptable (or it's graphical interface "Firestarter") and squid. What's you idea?

---

### Post by guliverza on 2011-07-14
ye.... I want it too...
anyone can help us?

---

