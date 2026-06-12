---
title: "Have to reset router a lot"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by randumnumber on 2011-01-09
hello all, I just installed 10.04 on my parents computer and they are loving it, but one problem has been happening which wasn't happening under windows. They are using an external USB wifi connector which i had been using on my network with a linux machine, so i know it works fine.

The problem is that about every 5th time they boot the computer it doesnt make a network connection, the LINK light on the usb wifi device doesnt blink and the indicator for NETWORK MANAGER just spins in circles. They then have to reset the router and reboot(yes reboot not just try to connect again) the computer. 

The usb is a WUSB54G.


secondly at my own home I have 2 ubuntu 10.04 (one wired one wireless) machines and my roommates have windows machines. I very rarely turn my machines on and off but they turn theirs on and off every time they use them, They are constantly asking me to reset the router.

I thought maybe it was a conflict with windows and linux on the same network, or that the dhcp pool was being depleted because of the constant connect and reconnect, but now that my parents machine is showing the same problems, i am not sure what to think.


If anyone has had this happen to them please give me some pointers on how to trouble shoot it. Thanks.

---

### Post by mail2345 on 2011-01-09
What kind of router do you have, and are you running any P2P apps on any of the computers?

---

### Post by isee on 2011-01-09
NetworkManager itself could be a possible culprit I believe.  I had to do the same thing (although with 9.10 Karmic), and how I solved the problem was installing wicd as the network manager.

Just a thought.

---

### Post by randumnumber on 2011-01-09
> **mail2345 said:**
> What kind of router do you have, and are you running any P2P apps on any of the computers?

At my home I run torrents, my parents however do not. At home I have a Netgear wgr614 v7. My parents have a linksys router the WRT54GS i think..im not there so i dont know what version it is.

I think it is weird that at my house the windows computers are the ones having issues, while at my parents house the Ubuntu computer is the one having connection issues.

---

### Post by randumnumber on 2011-01-09
> **isee said:**
> NetworkManager itself could be a possible culprit I believe.  I had to do the same thing (although with 9.10 Karmic), and how I solved the problem was installing wicd as the network manager.

Just a thought.

Do you have a combined windows/ubuntu network? Which computers were effected? I will try this at home and see if it works for us. If so i will do it for my parents, they are not tech savvy so it would have to be set and forget or they will never figure out how to use it. lol.

---

### Post by isee on 2011-01-09
> Do you have a combined windows/ubuntu network?

No, I've only dual-booted, so either Windows or Ubuntu, but not both.  I had no problems with Windows connection to the network, but Ubuntu would have wireless connection problems like yours, and it was resolved by switching network managers.

---

### Post by randumnumber on 2011-01-10
> **isee said:**
> No, I've only dual-booted, so either Windows or Ubuntu, but not both.  I had no problems with Windows connection to the network, but Ubuntu would have wireless connection problems like yours, and it was resolved by switching network managers.

Thanks i will try this at my parents house and see if it works, my home issues are still to be resolved :/

---

