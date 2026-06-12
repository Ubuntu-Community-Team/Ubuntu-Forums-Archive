---
title: "Wifi card recognized no signal"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by sbrelivet on 2011-07-25
Hello,

I have discovered the world of freewares not long ago and it surprised me! To go a bit further, I have installed Lubuntu 10.4 LTS on an old laptop: HP Pavilion zv5326 with 256 Mo RAM.

Everything works fine except the wifi.

iwconfig returns for wlan0:
IEEE 802.11b ESSID:"Livebox-afe5"
Mode: Managed Access Point: Not-Associated Tx-Power=0 dBm
Retry Long Limit:7 RTS thr:off Fragment thr:off
Power Management:off

Ifconfig returns nothing for wlan0

From what I understand, my wifi card is recognized so I do not need to install a driver with ndiswrapper, right?

What should I do then?
Is there a solution at all?

(Livebox-afe5 is the wifi connection I use with my other laptop.)

Thank you in advance if you can help :).

Kind regards,

Stéphane

---

### Post by mikewhatever on 2011-07-25
Hi, and welcome to the forum. 
Can you also post the output of the **lspci** command.

---

