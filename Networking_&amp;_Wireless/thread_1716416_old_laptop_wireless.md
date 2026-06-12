---
title: "old laptop wireless"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by cmcanulty on 2011-03-28
I have the B43 legacy wireless driver showing activated and in use. The wireless light is on but I can't get the wireless to work. Any ideas. It is an old Compaq Presario 2500 with 512 RAM . The nm-tool command shows
```
 Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43legacy
  State:             unavailable
  Default:           no
  HW Address:        00:90:4B:61:34:C0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


```
here is some more code that may help
```
owner@Presario2500:~$ sudo lshw -C network
[sudo] password for owner: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:10 memory:d0002000-d0003fff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a8:6f:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.53 latency=90 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:10 ioport:2400(size=256) memory:d0006000-d0006fff memory:34000000-3400ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:61:34:c0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
owner@Presario2500:~$ 

```
Also at the top of the panel it shows under wireless device not ready (firmware missing)

---

### Post by TBABill on 2011-03-28
```
sudo apt-get install b43-fwcutter
```

---

### Post by cmcanulty on 2011-03-28
I already installed that but when I added a few utilities from the software center it suddenly picked up a signal. Thanks

---

