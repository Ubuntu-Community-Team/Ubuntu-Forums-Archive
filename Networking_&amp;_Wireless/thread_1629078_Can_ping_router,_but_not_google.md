---
title: "Can ping router, but not google"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by hozzy on 2010-11-23
I tried to get Ubuntu 10.10 up and running last night, almost worked, but wireless card isn't working. I have another machine in the house running ubuntu 10.4 and it works fine.

I have searched around a bit in the forums and can't find anything that really helps me, so I thought I would make my own post.

The wireless card is an Intel PRO/Wireless 2200BG, which I think is part of core (i think i read that somewhere).

I think the problem might have something to do with the ip address (currently 192.168.0.100), i remember having issues in the past with that, but I could be wrong. when I run iwconfig i get

```
lo    no wireless extensions
eth0 no wireless extensions
eth1 IEE 802.11gb...
```
When I type ifconfig i get```
eth1 inet addr:192.168.0.100 bcast:192.168.0.255 mask:255.255.255.0...
```
I don't know if this is enough info to do anything with, but an help would be much appreciated. Thanks.

---

### Post by pricetech on 2010-11-23
Is it a fixed IP or are you using DHCP ??

---

### Post by hozzy on 2010-11-23
I have tried both static and DHCP, both with no luck. I remember when I used windows I had to use a static ip once. The other Ubuntu used DHCP. The wireless modem is my land lord and don't have any access to it.

---

### Post by hozzy on 2010-11-23
I took a usb wireless card from work, put it into the computer and now I can connect to the internet, so that makes me think it is my wireless card, I would still like to get my old wireless card working though (PRO/Wireless 2200BG [Calexico2] Network Connection). Any ideas?

---

