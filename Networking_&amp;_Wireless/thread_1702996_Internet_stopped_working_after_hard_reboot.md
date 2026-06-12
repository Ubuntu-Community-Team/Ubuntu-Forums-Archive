---
title: "Internet stopped working after hard reboot"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by asghlan on 2011-03-08
[SOLVED]

Hi,

last night I did a hard reboot on my computer running ubuntu 10.04. Previously the internet has worked just fine, but now it simply won't connect. On the networking icon on the desktop, there's just a red exclamation mark, and when I click it, it says "networking disabled". The hardware seems to be fine: everything else works.

I'm connecting via Ethernet cable to a modem, and the modem works fine (wlan works, internet works when I shut down wlan and connect the cable to my laptop).

"lspci" lists the following as Ethernet controller:
 02:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller

/etc/network/interfaces reads:
auto lo
iface lo inet loopback

When I try to ping some address, it says "network unreachable".

Is this correct? If it is, is there anything else I could try?

Thanks.

EDIT: okay, I solved to problem by running "sudo dhclient". For some reason, that makes the internet work again, although it still says "networking disabled" when I click on the networking icon on desktop.

---

