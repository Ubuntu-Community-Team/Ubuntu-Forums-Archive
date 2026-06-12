---
title: "MSI Wind Wifi Not working properly"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by NinjaArmadillo on 2009-10-07
I just got a brand new MSI Wind U123, first thing I did was threw UNR on it.
Everything seems to work mint, except WIFI.
I can connect to my network, but a couple seconds later I get nothing from the wifi, in the system monitor I get some out traffic when I make site requests, but nothing comes in.
Ubuntu Netbook Remix (Jaynty Jackalope) (Stock with All updates)
Atheros AR928X Wireless
iwconfig gives:
```
wlan0	IEE 802.11bgn ESSID:"barbery"
	Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
	Bit Rate = 1Mb/s  RTS thr:off  Fragment thr=2352 B
	Power Management:off
	Link Quality=95/100  Signal level:-60 dBm  Noise level -121 dBm
	Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0  Invalid misc:0 Missed beacon:0
```

In the words of the immortal LeeLoo, Pllleaasss Haalllp!

---

### Post by trippyd on 2009-10-28
I don't remember where I read this, and I have read two versions, but one suggests that the fn key toggles still work within ubuntu, so you can try fn-F11, and you might get some love.

The other way would be to enable wifi in windows (when the u123 comes out of the box, it is disabled) with the same fn-F11, and then boot back to ubuntu.

---

### Post by newsman on 2009-10-28
I have the same problem... it appears to be connected but every now and then although it appears to be connected it does not receive anything from the network and requires a reconnection

> 
wlan0     802.11b/g linked  ESSID:"D-Link"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: edited 
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/100  Signal level=-62 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any idea?

---

