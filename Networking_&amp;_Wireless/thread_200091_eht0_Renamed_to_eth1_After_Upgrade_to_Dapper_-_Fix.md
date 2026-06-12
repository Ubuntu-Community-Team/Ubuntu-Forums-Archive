---
title: "eht0 Renamed to eth1 After Upgrade to Dapper - Fixed"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by Ben Armston on 2006-06-19
I've just dist-upgraded from Breezy to Dapper. After rebooting the network no longer came up. A quick *ifconfig* showed me that my only network card was now mapped to eth1. Under Breezy it was eth0.

Changing all instances of eth0 in */etc/network/interfaces* to eth1 provided a temporary solution. After a little searching on the internet a more permanent solution was found by changing the MAC address given for eth0 in */etc/iftab* to match the MAC address of my network card.

The contents of */etc/iftab* had not been changed by the upgrade, so I have no idea why this happened.  If you know of a better solution, please reply.

Thanks and I hope this helps someone else.
Ben.

---

### Post by Ben Armston on 2006-06-20
I've just remembered that about a month or two ago, my network card broke and I swapped it for a new one. All worked perfectly afterwards. This was done under Breezy and explains why the */etc/iftab* didn't match my network card.

So this thread probably isn't going to be of any help to anyone. :(

---

### Post by elamericano on 2006-06-21
[QUOTE=Ben Armston]So this thread probably isn't going to be of any help to anyone. :([/QUOTE]
Not so. I installed my partition image of dapper on a new computer of the same model, and everything worked, but I didn't understand why my ethernet and wireless devices were now 1 instead of 0. I'm glad I happened upon the explanation. Thanks.

---

