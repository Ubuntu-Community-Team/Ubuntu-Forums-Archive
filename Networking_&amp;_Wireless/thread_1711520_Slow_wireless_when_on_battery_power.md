---
title: "Slow wireless when on battery power"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2011-03-21
I have a problem with my wireless where when running the laptop from the battery the connection is very slow. When the laptop is connected to the power supply everything is fine, but the moment it's disconnected and run on the battery the speed drops when browsing the Internet or accessing files on other computers on my network

The laptop is a Samsung SF310
Wireless chipset is BCM4313

```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Wistron NeWeb Corp. Device 051a
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4c00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl
```

In attempt to fix this I installed the latest drivers from the [Broadcom site ]("http://www.broadcom.com/support/802.11/linux_sta.php") using [this guide]("http://www.broadcom.com/docs/linux_sta/README.txt")

When I enabled these drivers everything worked well. I did speed test and got the same speeds I get when connected via Ethernet:

Ping 51ms
DL 4.31
UL 0.65

So I set the drivers to load at boot using [this forum post]("http://ubuntuforums.org/showpost.php?p=8556440&postcount=2") as a guide as the steps in the Broadcom guide didn't work and rebooted the laptop on battery power.  The wireless connected fine, but the slow speed problem had returned. Running a speed test got the following results

Ping 235
DL 0.54
UL 0.30

So I ran iwconfig when running from battery and then from power supply.



```
xxxx@xxxx ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:215  Noise level:160
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

As can be seen the signal quality is 5 and signal level 215

```
xxxx@xxxx ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:214  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
```

And when connected via the power supply the signal level is 5 and signal level 214.

There may be some kind of power saving issue, although there are no relevant setting in the BIOS and I can't see anything in the various wireless control pannels. I have other wireless drivers and there are no problem with those.

Anyone got any ideas what's causing this?

---

### Post by FooAtari on 2011-03-21
Typical, five mins after I post this, [I find a fix]("http://uselessuseofcat.com/?p=67") :)

There might be a better fix, but this will do for the moment until/if I find something better.

---

