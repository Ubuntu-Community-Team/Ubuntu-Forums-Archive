---
title: "WiFi extremely slow. Atheros AR9285 on Ubuntu 12.10"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by ninovolador on 2012-12-07
Hi guys, 
mi wireless conection is extremely slow. I have a 20 Mb/s conection, and torrents are downloading max at 150 KB/s.

I had this problem before, and was solved by entering "echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf" at the terminal. A few days ago, it came back.

 I tried changing the kernel, currently i am trying with 3.5.0-17-generic i686, and have tried with 0-18, 0-19 and  3.6.9-030609.201

Notice the high amount of "Invalid misc:" in iwconfig (dont know what that means, but doesn't look good)
```
 IEEE 802.11bgn  ESSID:"rodriguezmoreno"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1D:CE:89:2C:93   
          Bit Rate=65 Mb/s   Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:97  Invalid misc:2754   Missed beacon:0
```

If you can help me, or help me reporting the problem so other can be benefited i will be thankful.

(sorry the terrible english, i don't speak it very well, nor write it)

---

