---
title: "No wired or wireless connection"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by jonny_bowes on 2011-05-06
So I had 11.04 beta and after the official release I updated,rebooted and lost all wifi and wired connectivity.

On an Inspiron 9300

lshw -C network gives 

*-network:0 UNCLAIMED

For my Broadcom BCM4401-B0 100Base-TX

and

*-network:1 DISABLED

For my wirless interface Intel PRO/Wireless 2200BG

---

### Post by jonny_bowes on 2011-05-06
Ive gottent the wifi working via the Fn+F2 keys

rfkill list all gives

john@john-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

My wired connection is still down so i still need help on this

But now ive no Green WiFi light anymore? No major issue but....

---

