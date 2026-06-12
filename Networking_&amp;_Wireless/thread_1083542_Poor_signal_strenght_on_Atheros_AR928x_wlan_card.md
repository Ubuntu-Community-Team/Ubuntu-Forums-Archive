---
title: "Poor signal strenght on Atheros AR928x wlan card"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by mravljica on 2009-03-01
Hi!

I have found similar threads but none is related to Intrepid. So basically the problem is that the signal showing is poor compared to windows installation on the same machine (see signature below). From iwconfig I got this:
------------------
wlan0     IEEE 802.11bgn  ESSID:"STUPAR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:0E:6A:4E   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Encryption key: off
          Power Management: off
          Link Quality=45/100  Signal level:-66 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
------------------

I look at the Bit Rate and saw 1 Mb/s :shock: How is this possible when I got under windows 54 Mb/s connection with signal quality over 90 at the same place in another room. In some places in the house where I don't have signal under ubuntu, I have signal under windows nearly 50%.

Is there some additional wlan configuration possible under ubuntu?

Now I am using ath9k module which was installed automatically with ubuntu installation.

Regards,
Sasa

edit: I got the same issue under live-cd, ubuntu, kubuntu.

---

### Post by mravljica on 2009-11-09
The same issue is in 9.10 Karmic.

Anyone?

---

