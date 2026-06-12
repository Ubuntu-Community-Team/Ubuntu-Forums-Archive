---
title: "Acer Aspire 5610Z Wireless Configuration"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by B12 on 2009-11-10
I followed the guide on:

[http://ubuntuforums.org/showthread.php?t=466764](http://ubuntuforums.org/showthread.php?t=466764)

However, this doesn't seem to help in locating any routers with Ubuntu 9.10.

i.e., when I open wifi-radar, no wireless networks show up.

I've tried googling/searching several times for a solution, but have yet to solve it.

Here's some info on my hardware/installed drivers:

```
b12core@b12core-laptop:~$ sudo ndiswrapper -l
[sudo] password for b12core: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
b12core@b12core-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:a8:5c:0f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:21 memory:d0000000-d0001fff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0002000-d0003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:20:8b:09
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
b12core@b12core-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

b12core@b12core-laptop:~$ 


```

Any help provided would be appreciated.

^^ thanks in advance.

---

### Post by t0mppa on 2009-11-10
The problem here is that your wired card uses the b44 driver, which loads the ssb module. And since ssb is also used by b43, it automatically hogs up the wireless card as well (shows up as b43-pci-bridge), since it's loaded before ndiswrapper. You'll need to unload all three, then load ndiswrapper first and the b44 afterwards with:```
sudo modprobe -r b44 b43 ssb ndiswraper
sudo modprobe ndiswrapper
sudo modprobe b44
```

That way the ssb only deals with your wired card, since the wireless is already associated with ndiswrapper and both interfaces should work just fine.

---

