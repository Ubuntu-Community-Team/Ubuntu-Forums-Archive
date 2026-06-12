---
title: "BCM4312 Wireless-- Driver Problem"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by jmgilchr on 2009-09-08
EDIT: Okay, I have a Broadcom 4312 802.11b/g Wireless thing

from lspci:

> b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Subsystem: Dell Device [1028:000b]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


I also have the b43 device driver

from dmesg:
> [   86.660285] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]


from lsmod | grep b43

> b43                   138248  0 
ssb                    37668  1 b43
mac80211              231424  1 b43
cfg80211               43664  2 b43,mac80211
input_polldev           4624  1 b43
led_class               4968  2 b43,sdhci


For whatever reason, however, my Network Manager fails to see my wireless device!

I'm running 9.04 jaunty, the 2.6.29 kernel....just don't know what is wrong.

---

### Post by jmgilchr on 2009-09-08
bump

---

### Post by ductiletoaster on 2009-09-08
Have you tried looking at the STICKY at the top of this Category

[http://ubuntuforums.org/showthread.php?t=1176117]("http://ubuntuforums.org/showthread.php?t=1176117")

.... i hope that helps cuz other than that im not sure good luck hope that thread helps

And just incase your not sure on the main post there are some links for different setups. Try the 
**Linksys WMP54GS v 1.1**
Chipset: Broadcom BCM4318 (not the same as urs but maybe might have some helpful info)

---

### Post by Cuba71 on 2009-09-10
Try this link for drivers

[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by Ayuthia on 2009-09-10
The b43 module does not work with your chipset(14e4:4315) until 2.6.32 if I recall correctly.  Like Cuba71 mentions, the Broadcom STA option is available for you.  You should be able to activate that through System->Administration->Hardware Drivers instead of going to the website to compile and install.  You will also need to blacklist the b43 and ssb modules:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

