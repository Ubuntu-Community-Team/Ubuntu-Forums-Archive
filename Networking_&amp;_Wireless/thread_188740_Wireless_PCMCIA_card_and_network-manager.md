---
title: "Wireless PCMCIA card and network-manager"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by mriya3 on 2006-06-04
I have a Siemens Gigaset PC Card 11 wireless adapter (Atmel at76c50x), and got two problems with network-manager after upgrade to dapper.

**Problem 1)**

In breezy, if I plugged the card, it would be "recognized" by network-manager, and clicking on the applet icon would show the list of available ap.

In dapper, I'm forced to reload NetworkManager to make it see the card (launching NetworkManager with the --no-daemon option shows that network manager does not react to card insertion). If I insert the card and then re-load NetworkManager it is recognized BUT then, because of problem 2, fails to get an IP addres with dhcp.

Note that udev initializes the card correctly (check with udevmonitor and hal-device-manager).

**Problem 2)**

When network-manager tries to get an ip for the wireless adapter, it fails because of an error with wpa_supplicant timed out. Doing everything manually with dhclient works without problem. Note: wireless network is not encrypted

In advance, thank you for help

---

### Post by sarutv on 2006-06-08
I think wireless support has gone down the drain in Dapper. You are not the only one -> [Dapper: Improvised Wireless!!!](http://www.ubuntuforums.org/showthread.php?t=191557&highlight=atmel+wireless)

---

