---
title: "Wireless connection in ubuntu minimal install, no ethernet"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by Buce on 2009-07-10
I'm trying to get WEP wireless working on an ubuntu minimal install. I have no ethernet, so I can only install packages from the CD's repos.

Here's the output of 'sudo lshw -C network':
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:a8:6a:50
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.1.11 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:23:41:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
```

And the commands I've used to try to manually get wireless working:
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid 'network ESSID'
sudo iwconfig wlan0 key s:[ASCII key]
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

The output of that last command gives:
```
There is already a pid file /var/run/dhclient.pid with pid 4900
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:02:a8:6a:50
Sending on   LPF/wlan0/00:13:02:a8:6a:50
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And then pinging google gives an 'unknown host' error, as you might expect. Can anyone spot what I'm doing wrong? Is there anything else I should try?

---

### Post by Buce on 2009-07-10
The output of 'lspci | grep Network':
```
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

The router I'm trying to connect to is a mac airport. How can I find the channel to use in the command 'iwconfig wlan0 channel 11'?

---

### Post by superprash2003 on 2009-07-10
is your wifi card able to detect wifi networks? output of **sudo iwlist scanning**

---

### Post by Buce on 2009-07-13
> **Buce said:**
> sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid 'network ESSID'
sudo iwconfig wlan0 key s:[ASCII key]
sudo dhclient wlan0

Trying these commands after a reboot worked for some reason. Hm.

---

