---
title: "Vpn (pptp) down when smth changes in net config"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by dettaglio on 2009-08-16
I share eth0 connection with another PC connected via eth1. eth0 leads to LAN, not internet. Internet connection is made with VPN, in fact it's a PPTP connection created by an ad-hoc shell script.

When the other PC turns on or off, and eth1 "blinks" (goes down and up in few seconds), my PPTP connection goes down and I have to re-connect to internet calling that script.

1) Is it possible to make this automatic or any way to make the PPTP "harder", that it doesn't go down when any other connection changes?

I've noticed another problem: a "Home network" connection (with fixed IP 192.168.0.1) that was set up for eth1, was used by Network Connection manager for eth0 (that should be set up with DHCP). So,

2) is there a way to tie a connection to a certain ethernet card?

(Why such a strange internet connection? Well, it's my ethernet ISP that works this way. Ethernet cable gives access to LAN with some services like forums and DC hubs, and for internet with real IP you need VPN. Certainly, there is only this ad-hoc script and no support is provided to Linux users.)

---

