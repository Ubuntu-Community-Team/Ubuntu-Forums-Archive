---
title: "Wireless connected, NM icon indicates disconnected (!)"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by quonsar on 2010-06-22
i set up my wireless router. i have 10.04 on my netbook and it connects and functions just fine, however the icon in the panel displays as if i were disconnected. how to get it to indicate properly?

---

### Post by Iowan on 2010-06-22
You used NEtwork Manager to set up the connection (as opposed to */etc/network/interfaces*)?

---

### Post by quonsar on 2010-06-23
yes, i did. i configured the router, turned on my netbook, the SSID was shown in the applet, i clicked, entered the key and connected. it connects fine everytime i boot now, but as soon as the "connected to Auto [my ssid here]" notification appears, the nm-applet icon goes back to the disconnected pixmap with the red "!" on it.

clicking on it displays all the correct information, its just the pixmap that is wrong. strange.

---

### Post by quonsar on 2010-06-23
bump?

---

### Post by Timothy Benton on 2010-07-03
I'm having the same problem.
Lenovo S10e, Broadcom wireless, Ubuntu Netbook Remix 10.04

---

### Post by rhd on 2010-09-10
Ditto. I've got a screenshot attached.

---

### Post by javawarrior on 2010-10-24
I am having this issue too on a dell inspiron 1721 running up to date ubuntu 10.04.1. The network hardware is as follows:

description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation

I am writing because I noticed that desktop user accounts on this machine (mine is a custom/admin account) do not have this problem. Any ideas anyone?

Oddly, whilst I was in the process of writing this, the NM icon seemed to fix itself. I am now in the vicinity of 2 wireless networks both of which I can join. Maybe this made a difference.

---

### Post by Craigwell on 2011-01-18
I believe this is partially an issue with some Broadcom devices. Ubuntu and Broadcom do not go together so well. 

I originally had to find a workaround to get my BCM4328 802.11a/b/g/n wireless working (PITA), and when recently reinstalling 10.04LTS, I chose to use one of the proprietary drivers that comes with it (STA driver), and although it does work fine, I have the symptom you describe.

Working on a solution now.

---

