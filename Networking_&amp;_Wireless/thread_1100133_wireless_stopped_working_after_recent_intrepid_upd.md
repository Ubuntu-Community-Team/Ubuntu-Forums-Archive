---
title: "wireless stopped working after recent intrepid updates"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by dugh on 2009-03-18
In the past day or two my networkmanager applet stopped showing any wireless networks and doesn't even try to connect or find anything.

I am using ndiswrapper and bcmwl5 native driver on a Dell D820 laptop.

I didn't know if it might be a conflict with recent kernel upgrades (now at 2.6.27-14 kernel).  But booting to the kernel before still had no wireless working.

Wired connections are still working fine.

The only thing i see in syslog is "wlan0: Link is not ready"


iwconfig gives this output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

ndiswrapper -l
```

bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: wl)

```

lshw -c network

```

  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4b:6a:42
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:72:72:f9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5752-v3.19 ip=192.168.0.102 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:4c:b3:95:10:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

---

### Post by tjlane on 2009-03-18
i had the same thing happen on an hp pavilion dv4 with the same wireless card. I'm looking for a solution right now, but I'm still new to all this. If I find anything I'll be sure to post.

---

### Post by dugh on 2009-03-19
I totally removed ndiswrapper and compiled my own version but still the same issue.

I think it's some configuration line missing somewhere that was overwritten by the latest updates.

---

### Post by dugh on 2009-03-19
It was a switch on the side of my laptop that must have accidentally been pushed and turned off the wireless card.

doh

---

