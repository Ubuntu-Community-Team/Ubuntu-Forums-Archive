---
title: "Wanting to fix WPA Wifi issues... having a hard time"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by inspired on 2009-06-29
Hi folks,
I've never managed to get wifi to work on my laptop when the wifi connection uses WPA for the password. It works okay(ish) with WEP and on unsecured connections. On WEP it does drop the connection far more often than I would like though... perhaps every 2 to 20 minutes, at a guess.

I tried to resolve this WPA issue a year or so ago with no luck. I found such a mix of info offering solutions, and lots of people with this issue. That was with Ubuntu 8.04 and 8.09.
I now have 9.04 and I had hoped the issue would have sorted itself out. It remains.

I would greatly appreciate it if someone pointed me in the right direction to fixing this once and for all. I am finding it tedious getting people (friends, etc.) to reconfigure their routers to use WEP whilst I am visiting them, not to mention the obvious potential security issues I then present them with as a result.

iwconfig provides the following:
```
eth1      IEEE 802.11b  ESSID:"Rorer"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:E4:E3:22   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

```
I am not sure why my wireless is being labeled eth1 rather than wlan1 or something like that.

Some of the solutions I found suggested disabling NetworkManager, which meant hard coding the settings. Not much good on a laptop, with which I connect to many different networks. Other (outdated) solutions mentioned install wpasupplicant, but that is already installed. Whether or not that needs some custom configuration, I am not sure.

**I'd love some help with this.**
Let me know what more info I can provide.

This computer is a compaq nx7010 with an Intel Pro/Wireless 2100 chipset
```
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation Device 2522
        Flags: bus master, medium devsel, latency 128, IRQ 5
        Memory at 90000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ipw2100
        Kernel modules: ipw2100
```
With thanks,

Jonathan

PS. Using WEP at the moment, and connection has dropped three times whilst writing this. Agghhh...

---

### Post by inspired on 2009-06-30
I managed to sort out the WEP issues... in terms of disconnections... by changing the channel on the router from the default (6) over to 10.

Keen to sort out the WPA issue though... as I move from place to place a lot.

Jonathan

---

