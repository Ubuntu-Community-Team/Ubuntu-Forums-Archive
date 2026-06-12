---
title: "wireless not connected at full speed"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by hanlin on 2009-11-14
After the upgrade to Karmic, I've noticed that my wireless has been very slow. I couldn't figure out why, until today, when I saw that it was only connected at 54M. I have an intel 4965 wireless card with a 802.11n router. I know for a fact that it used to connect to the router at 130M (at least that's what the router software says). But now, it's only connected at 54M. The router shouldn't be an issue since other computers on the wireless network are connected at 130M. Any ideas why this laptop can't connect at full speeds?

---

### Post by djbon2112 on 2009-11-28
I seem to be having the same issue. My n card and n router only show a connection of 26 Mb/s!

---

### Post by jgrocha on 2009-12-10
Same problem here, with Ubuntu Karmic 9.10.

My Wireless AP is "Wireless N" (SMC WBR14-3GN). Another laptop, with *another* operating system can archive the 130Mbps.

My Ubuntu laptop (ASUS G70), with "Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k", can only operate at 54Mbps.

The output of "[FONT="Courier New"]iwlist wlan0 scan[/FONT]", only reports speeds up to 54Mbps. I think the problem is on the reported speed.
If the iwlist output doesn't show the 130Mbps speed, it is impossible to do something like:
[FONT="Courier New"]sudo iwconfig wlan0 rate 130M[/FONT]

The output of [FONT="Courier New"]iwconfig[/FONT]:

[B]wlan0     IEEE 802.11abgn  ESSID:"POR8033"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:CF:CC:D7:0E   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

More comments are welcome.

---

