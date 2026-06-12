---
title: "TRENDnet 300Mbps Mini Wireless N"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by rudiminty on 2012-12-31
I am new to Ubuntu and an running the 12.10 on amd64.

I purchased the TRENDnet wireless USB network adapter and it seemed to install itself with no intervention required.
I can view wireless networks in the area but when I attempt to authenticate, it keeps returning the same authenticate message asking for a password.  Even if I remove authentication on the wifi router, my ubuntu still keeps asking for authentication password?

Any help would be appreciated!

---

### Post by ZippyUbu on 2012-12-31
Hi,

Please open the terminal: 

```
sudo lshw -C Network
```...and post the results..

--
Zu

---

### Post by Benic on 2013-01-14
I'm having the same trouble with this wifi router. It has some connection problem with my Ubuntu desktop and my Android tablet, but not with Apple and Windows devices. Sometimes it connects, sometimes not and I have to unplug and replug the router. Pretty annoying... 

Here are my settings : 

```
lspci -v 
06:00.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
	Subsystem: Ralink corp. RT3060 Wireless 802.11n 1T/1R
	Flags: bus master, slow devsel, latency 32, IRQ 21
	Memory at ff500000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt3562sta
	Kernel modules: rt3562sta

```
```
iwconfig
ra0       Ralink STA  ESSID:"MEBC"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:D1:40:30:0D   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=98/100  Signal level:-68 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.
```

---

### Post by ZippyUbu on 2013-01-20
Hi, the original post is talking about a Wireless USB Adapter. If you are having trouble with your router, have you tried the manufacturers website for the latest firmware?

I assume the driver in use on Ubuntu may also not be correct "rt3562sta".  You may want to have a look at this [post.]("http://askubuntu.com/questions/84959/how-do-i-get-a-ralink-rt3060-wireless-card-working") Although this refers to the 2800 kernal module, your issue may be similar

---

