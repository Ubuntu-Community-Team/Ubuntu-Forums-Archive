---
title: "Wierd problems with Laptop's (Asus A7D) wireless card"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by Phasmagon on 2006-05-09
Hello everybody,

I have a laptop (Asus A7D) which has a built-in wireless adaptor.
lspci states that it is:
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

When I first installed ubuntu dapper beta and after I updated the firmware, the adaptor was working only if I disabled and re-enabled it in Network Settings.

Then yesterday by updating to kernel 2.6.15-22, I cannot use this method to start my wireless NIC. The only way I found working is to give my Access Point's mac address manually with:

sudo iwconfig wlan0 ap xx:xx:xx:xx:xx:xx

and then:

sudo ifdown wlan0
and
sudo ifup wlan0

Is there anyone who can tell me how can my adaptor properly initialize, because it is very annoying, to have to do this every time my comupter starts?

---

