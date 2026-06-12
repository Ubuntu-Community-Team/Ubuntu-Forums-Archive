---
title: "Cant use my Belkin G wireless USB F5D7050"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Ahmedio on 2009-06-24
I can't use my Wireless USB because Ubuntu doesnt support it, but I browsed the web and heard that people actually managed to get it to work. i need some help. thanks in advance and sorry if im in the wrong forum section.

I use Ubuntu 8.10 Intreped 

this is what i get when i run iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:Off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:Off   Fragment thr:Off
          Power Management:Off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Also my hardware drivers section is completely empty. HELP ME!!:(

P.S. I get that when i have my Belkin USB inserted

---

### Post by Ahmedio on 2009-06-24
Bump. please someone help

---

### Post by mattgyver83 on 2009-06-24
I actually have this dongle and use it without any problems.  I think the issue is that you have not wraped the drivers with ndiswrapper.

If you have the CD that came with it the drivers are on the cd and you can copy them from there, if not you can search the net and find them.  Then just read on how to wrap drivers with ndiswrapper, its very basic.

---

### Post by Ahmedio on 2009-06-24
i did that and i ran the INF file and now its working thanks.

---

