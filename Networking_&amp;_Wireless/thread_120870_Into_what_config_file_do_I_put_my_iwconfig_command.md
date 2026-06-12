---
title: "Into what config file do I put my iwconfig commands?"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by Brian Kendig on 2006-01-23
I'm using Xubuntu with Xfce, so I don't have the fancy GNOME utilities for setting up a wireless network. I know the commands I need to run - "iwconfig ath0 essid mywirelessnetwork" and "iwconfig ath0 key s:mypassword" will get me online wirelessly - so all I need to know is, what's the proper config file to put these settings into so that my laptop will connect to my wireless network automatically on boot?

---

### Post by Lambert on 2006-01-23
/etc/network/interfaces

You can read about it with 

man interfaces 

or

zcat /usr/share/doc/ifupdown/examples/network-interfaces.gz

but basically it looks like this for a dhcp setup.

iface ath0 inet dhcp
wireless-essid ____
wireless-mode managed
wireless-key restricted s:______


then if you want to start at boot then add a line

auto ath0

---

