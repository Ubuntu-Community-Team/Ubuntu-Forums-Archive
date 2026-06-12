---
title: "Wi-Fi system crashes after heavy use"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by beboylips on 2012-08-25
Hello Community,

I have a problem with my WiFi in the following sense: when I use BitTorrent (transmission) for unspecified legal activities and those activities are transmitted at high speed for a period of time (usually around 10 minutes or so), the wifi connection dies (disconnects) and I can't reconnect to any AP without restarting my computer. 

I have the following specs:

Toshiba Satellite A660 i3-M350

Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

Ubuntu 64-bit 12.04.1 + all recent updates

Thank you.

---

### Post by andymurn on 2012-08-25
Before chasing out the wifi gremlins have you tried using a wired connection for a bit to make sure it's just the wifi that is causing the problem? Does turning the wireless adapter off and on again fix it?

---

### Post by beboylips on 2012-08-26
Yes I did try over wired, works fine. And restarting the adapter does not help, surprisingly. Neither does restarting NetworkManager and/or wpa_supplicant.

---

### Post by Hawkoon on 2012-11-26
Hi beboylips,

did you ever get to the bottom this problem?

I am struggling with the exact same issue (I tried both transmission and deluge with 12.04 Ubuntu server) only thing I don't need to reboot my server to bring wifi back up, running 
"sudo /etc/init.d/networking restart" does the trick.


~H

---

### Post by beboylips on 2012-11-26
Hey,

I never really found a real solution to the problem, besides reducing the maximum number of simultaneous connections to something around or below 50. 

What hardware you're running, specifically, which wireless NIC?

-Beboy

---

### Post by Hawkoon on 2012-11-27
It is an old HP notebook (NC4000, 1GB RAM, 1.5GHz Pentium M) that runs as headless server, with Gigabit LAN and an Atheros Communications Inc. AR5212/AR5213 Wireless Network Adapter. The system drive is actually just an USB memory stick (it is a lot more quiet than any HDD, requires less power and is cheaper to replace)  and it has been working happily for some 2 years serving my music collection from an externally connected drive. I have never experienced performance issues, but then I think MPD is pretty lean anyway and there isn't really much else going on, until now.

Anyway, last night I was skimming through lots of Google hits on this issue. Some folks kicked out the default network-manager and switched to wicd and it seemed to solve the problem. So I'll try that next. If that fails I ll probably just setup a cron job to periodically check the wifi status and to restart the network-manager. Luckily, unlike you, I don't need to reboot my system to bring wifi back to working.

---

### Post by Hawkoon on 2012-12-01
OK, just a quick update. Changing to wicd didn't solve the problem for me. In fact things got even worse since LAN too was affected now, not just wifi. So I kicked out wicd and tried reducing the number of simultaneous connections to 50 and then 20, but even then wifi crashed regularly after some period of downloading. So I will use a cronjob now to check and restart wifi at some interval.

~H

---

