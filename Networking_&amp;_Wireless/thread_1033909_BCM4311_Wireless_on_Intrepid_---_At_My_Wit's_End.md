---
title: "BCM4311 Wireless on Intrepid --- At My Wit's End"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by DanielGr on 2009-01-07
I've scoured the forums and the internet at large for solutions to my wireless problem. I'm running 8.10 on an Asus F5R with a Broadcom BCM4311 wireless card. I had been running 8.04 on this same machine with a Windows Vista partition. The wireless worked fine with that installation. On reboot I would have to toggle the wireless on off switch (by this I mean a physical switch on the side of the computer) before the led showing that the wireless was on would light up and it would work.

I now have just 8.10---no more Vista. When I toggle the switch the led either doesn't light up or light's up for a split second only. And the wireless never works.

I've tried ndiswrapper, b43-fwcutter, the Broadcom STA driver, all of it to no avail.

Please tell me someone has a solution.

---

### Post by Ayuthia on 2009-01-07
Can you please let us know which revision of the 4311 you have (rev 01 or 02--just go into the Terminal and type lspci -nn and look for your wireless card and you should be able to find the revision)?

You can first try the following (this one will test the b43 option):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo /etc/init.d/networking restart
sudo iwlist scan
```

If that does not work, try (this one is testing the Broadcom STA wl module):
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```

And finally the ndiswrapper:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
sudo iwlist scan
```

---

### Post by DanielGr on 2009-01-07
Hi,

I have rev 01 apparently:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

I've tried those three options already, but I'm not opposed to giving it another try. Thanks.

---

### Post by DanielGr on 2009-01-07
Nope, none of it works. The first is the most promissing, as nothing throws up a red flag, but it still doesn't work. What should I be looking for in the output of "iwlist scan"?

---

### Post by Ayuthia on 2009-01-07
> **DanielGr said:**
> Nope, none of it works. The first is the most promissing, as nothing throws up a red flag, but it still doesn't work. What should I be looking for in the output of "iwlist scan"?

It should return a list of wireless sites.

Can you post the results of lshw -C network and attach the results of dmesg?  The file can be found in /var/log.  The dmesg might help provide some clues on why you cannot connect.

Also, what driver are you using for ndiswrapper?  Can you post the results of ndiswrapper -l?

---

### Post by DanielGr on 2009-01-08
This is the result of lshw -C network

```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1b:fc:3a:bc:d2
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 duplex=full firmware=L2 ip=192.168.2.7 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:92:df:e9:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:bf:47:1c:ce:84
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

ndiswrapper -l returns nothing actually. hmm.

---

### Post by DanielGr on 2009-01-08
This is the result of lshw -C network

```
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: a0
       serial: 00:1b:fc:3a:bc:d2
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 duplex=full firmware=L2 ip=192.168.2.7 latency=0 link=yes module=atl2 multicast=yes port=twisted pair speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:92:df:e9:af
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:bf:47:1c:ce:84
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

ndiswrapper -l returns nothing actually. hmm.

---

