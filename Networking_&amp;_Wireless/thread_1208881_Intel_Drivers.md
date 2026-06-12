---
title: "Intel Drivers"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by f0rtune on 2009-07-09
I am having trouble with my laptop and it's wifi.  I have an iwl-5100, and I have installed compat-wireless for the driver needs.  After installing, the guide said to just reboot the computer and the drivers will be used.

I am not completely sure that the drivers are being used, when I run airmon-ng it says the the chipset is unknown.  And I was able to use my card when I first installed Ubuntu 9.04.  I installed compat-wireless so I could inject packets and use the correct drivers.

So how would can I find out what drivers my computer is using, sorry I have never had this problem in linux before.

f0rtune

Edit:  I cannot am also not able to connect to WEP encrypted networks, i use this command:

iwconfig wlan0 essid myessid key 00:00:00:00:00:00
ifconfig wlan0 up
dhclient wlan0

but it doesn't connect

EDIT2:

Also I know that the AP doesn't have mac address filtering.

---

### Post by superprash2003 on 2009-07-10
post output of the following
1)lshw -C network
2)iwconfig

---

### Post by f0rtune on 2009-07-10
*-network DISABLED
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:1d:72:fe:06:45
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:18:43:f2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:38:7b:17:4d:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

and

wlan0     IEEE 802.11abgn  ESSID:"NETGEAR"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

smilies disabled*

---

### Post by f0rtune on 2009-07-11
I see that my card is using the iwalgn drivers, but I am still having problems.

I now cannot connect to any open networks nor wep encrypted networks.

I use these commands:

ifconfig wlan0 down
iwconfig wlan0 essid NETGEAR
ifconfig wlan0 up
dhclient wlan0

this would work before but now it doens't

please help,
Foxy

---

