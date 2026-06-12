---
title: "Intel Centrino 6300N dies periodically on 12.10"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by plargiblarg on 2013-01-13
Apologies if I do something wrong, I'm a bit new here - 

just got a thinkpad t430 with intel centrino ultimate 6300N wireless controller, and recently started dual booting Ubuntu. Usually upon first boot wireless is working fine, but after suspending and then coming back to it, the controller isn't even detected half the time, or else it just doesn't work.

When not working:

lspci -vv gives
```
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev ff) (prog-if ff)
	!!! Unknown header type 7f

```
The 7f error only just started happening, perhaps because i took the advice from this thread: [http://ubuntuforums.org/showthread.php?t=1978457&page=1](http://ubuntuforums.org/showthread.php?t=1978457&page=1)
Before that it would say something along the lines of "Illegal vendor ID".

iwconfig wlan0 gives nothing

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:21:cc:d7:56:4a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-3 ip=192.168.2.89 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:f2500000-f251ffff memory:f253b000-f253bfff ioport:5080(size=32)

```


When it starts working again I will post details of the output.

Thanks for any help you can give!

---

