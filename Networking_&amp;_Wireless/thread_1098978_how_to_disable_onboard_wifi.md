---
title: "how to disable onboard wifi"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by enthy on 2009-03-17
Disable Wireless Connection
Hi;

i use xUbuntu 8.10 with NetworkManager Applet 0.7

i want to disable (desactived) ... my onboard wireless card...

- no i can't do that by the BIOS
- no i don't have a button for shutdown it
- i can't disable the driver with BootUp Manager
- i can't disable it by the Network Manager
- no i can't put a # on my file /etc/network/interfaces
because my file interfaces have just these line
auto lo
iface lo inet loopback

my config is:
eth0 my onboard lancard
eth1 nickname ipw2100 i want to disable it because my antenna is dead.
wifi0 an alias of eth1
ath0 my wireless pcmcia card i want to use it.

sorry for my english i'm a french canadian.

please reply me the file where i can edit my hardware configuration.

---

