---
title: "Broadcom 4312"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by xartilon on 2011-06-24
I just recently upgraded to Ubuntu 11.04. 
 
I have tried all the guides and so on to get this wireless card to work, but nothing has been worked so far.
 
I installed the drive that comes up under "Additional Drivers," and the wireless card shows up, as well as wireless conncections. When I click on a wireless connection, it tries to connect, but after a minute or so it says "Wireless Network Disconnected."
 
This is what lspci -v says:
 
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
 Subsystem: Dell Wireless 1395 WLAN Mini-Card
 Flags: bus master, fast devsel, latency 0, IRQ 17
 Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: wl
 Kernel modules: wl, ssb

And this is what iwconfig says: 
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
 
I'm on a Dell Inspiron 1525, and the ethernet works. 
 
Thanks.

---

