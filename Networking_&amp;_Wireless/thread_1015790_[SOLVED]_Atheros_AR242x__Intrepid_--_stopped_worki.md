---
title: "[SOLVED] Atheros AR242x / Intrepid -- stopped working over night"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by krisstaar on 2008-12-19
First time I got the atheros card working, was after installing linux-backports-modules for Intrepid. It stopped working once before after an update and I couldn't enable the wireless card from Network manager, but I got it working by removing and reinstalling the backports-modules.

Now, it seems to have stopped working over night. It was fine yesterday, but now it doesn't even attempt to connect. I have no idea why. I can connect to wlan with other laptops, so I don't think the problem is the network itself...

Details:
[LIST]
[*]Acer Aspire 5720z
[*]2.6.27-9-generic i686 kernel
[*]Ubuntu 8.10 Intrepid Ibex
[*]Atheros AR242x 802.11abg Wireless PCI Express Adapter
[/LIST]

ifconfig wlan0:
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:

```

dmesg
```
[   14.040369] ath5k 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.040389] ath5k 0000:06:00.0: setting latency timer to 64
[   14.040426] ath5k 0000:06:00.0: registered as 'phy0'
[   14.366543] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   32.998466] ath5k phy0: gain calibration timeout (2412MHz)
[   32.998475] ath5k phy0: can't reset hardware (-11)
[   33.367098] ath5k phy0: gain calibration timeout (2412MHz)
[   33.367107] ath5k phy0: can't reset hardware (-11)

```

lsmod:
```
ath5k                 116612  0 
mac80211              213424  1 ath5k
led_class              12164  2 acer_wmi,ath5k
cfg80211               45464  2 ath5k,mac80211

```

Network configuration:
```
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: XX:XX:XX:XX:XX:XX
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5787m-v3.22 ip=10.0.0.7 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I guess it's obvious what the problem is, but nwm says it's enabled...

Network scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```
Makes sence since wireless card supposedly is disabled...



Restart Networking:
```
 * Reconfiguring network interfaces...                                                              Ignoring unknown interface eth0=eth0.
                                                                                             [ OK ]
```

Are you smarter than me?
I.e. can you explain me how to fix? 

In advance, thanks.

---

### Post by krisstaar on 2008-12-19
Ttt

Edit: I reinstalled Ubuntu, and did what I had to do the first time to get it working. I have no clue why I couldn't enable wifi, but it works now. That's the important thing.

---

