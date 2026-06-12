---
title: "Wireless Belkin F5D8053 won't connect"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by rencemc on 2009-10-30
I was having trouble trying to get wireless working with Ubuntu 9.04 - then I loaded Ubuntu 9.10 yesterday.

Previously when I did an iwconfig, I would not see any wireless entries. Now I get 2 entries because I have 2 wireless adapters connected. I have a Linksys wireless-G adapter that works fine, but my Belkin F5D8053 does not connect. So the Linksys that works is wlan1 - my Belkin is wlan0. In the following cut & paste you can see the wireless entries and what happened when I tried to "up" wlan0. I appears that the adapter is fully recognized, but as I said, I cannot connect using the Belkin. I did try with just the Belkin connected and it still didn't work.

I appreciate any help that anyone can give me.

   Thanks,
        Terry

terry@terry-desktop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 802.11b/g Mode:Managed Access Point: Not-Associated
Bit Rate:0 kb/s
Retry min limit:7 RTS thr:off Fragment thr:off
[[COLOR=blue][COLOR=blue ! important][FONT=&quot][COLOR=blue ! important][FONT=&quot]Power [/FONT][/COLOR][COLOR=blue ! important][FONT=&quot]Management[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://geeks.pirillo.com/group/linux/forum/topics/cannot-get-wireless-working#"):off
Link Quality=0/100 Signal level=0 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan1 IEEE 802.11bg ESSID:"55Surrey"
Mode:Managed Frequency:2.462 GHz Access Point: 00:1D:7E:3D:B9:F3
Bit Rate=54 Mb/s Tx-Power=7 dBm
RTS thr=2347 B Fragment thr=2346 B
Link Quality=48/100 Signal level=48/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

terry@terry-desktop:~$ sudo ifconfig wlan0 up
[sudo] password for terry:
SIOCSIFFLAGS: Resource temporarily unavailable

---

### Post by The-Wise-Man on 2009-10-31
I have the Exact same problem, 2 weeks ago I noticed that my Linksys Wireless G adapter was overheating.. so I went bought a new networking setup... Spent more than I wanted to.. And my Belkin F5D8053 seems to be fully recognized but not operable in Ubuntu 8.10/9.04/9.10 and I plugged my Linksys card in when I use Ubuntu.

---

### Post by tht13 on 2009-10-31
hi, i have the same problem, i've been through the sites, and there is one with really good directions on what to do [https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)

so i have everything installed, i try to connect but it still does not recognise my password for my wifi network, what do i do? i enter the password, it spends about 3 minutes trying to connect and then asks for the password again. it will never connect!!!

---

### Post by rencemc on 2009-11-02
I have found no solution to the Belkin wireless issue. I just have to use my Linksys-G until a fix is found/given. These wireless issues have been around a long time. Linux will never make it to mainstream with incompatibilites like this. Only people like us who really want to play with linux and use its features will continue to use it. I still love it, but some the problems are so damn aggravating. It's a good learning experience though.

---

