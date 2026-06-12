---
title: "wireless suddenly disabled"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by badzeugene on 2010-04-09
i connected to wireless network once a few days ago, and today, when i try to connect to wireless, it says 'wireless is disabled'. below is the result for testing..
FOR lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:43:01:58
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.1.31 latency=0 multicast=yes
       resources: irq:29 memory:f9ffc000-f9ffffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:01:cf:5b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f9efe000-f9efffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

FOR iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

Currently using Ubuntu Karmic, Dell XPS M1530

---

### Post by badzeugene on 2010-04-09
anyone... please...

---

### Post by andy341 on 2010-04-09
I did the following in a previous posting in the forum:
Go:
 
 System > Administration > Hardware Drivers
 
 Activate the one that was not activated. It now works! Yes!

---

### Post by Bullitdodger on 2010-04-10
> **andy341 said:**
> I did the following in a previous posting in the forum:
Go:
 
 System > Administration > Hardware Drivers
 
 Activate the one that was not activated. It now works! Yes!

I've got the same problem. Nothing shows up in:  System > Administration > Hardware Drivers....?

---

### Post by chili555 on 2010-04-10
> **badzeugene said:**
> anyone... please...Please post:```
rfkill list
dmesg | grep iwlagn
```Thanks.

---

