---
title: "Wireless Worries For Intrepid Ibex"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by Vampyer on 2009-12-08
Hey guys,

I have an IBM/Lenovo X60s (with built in wifi) and I bought a network card for it, a Netgear WG511T. It's an Atheros chip and is supposed to work 'out of the box' but really doesn't :P

I'm a n00b but here's what I can gather so far:

*lspci | grep Network* - gives me details about the card "Atheros AR5001X+ Wireless Network Adapter (rev 01)"

*iwconfig* - gives me eth0 and lo, both with no wireless extensions

no wlan0! So I thought it could have been disabled and typed *sudo ifconfig wlan0 up* and got back "wlan0: ERROR while getting interface flags: No such device"!

hardware drivers (system>admin>hardware drivers) says that the drivers are installed and are in use :(

I don't know what to do...

if only superman were here to save me...

---

