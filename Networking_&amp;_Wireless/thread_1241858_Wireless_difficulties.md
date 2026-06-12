---
title: "Wireless difficulties"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by aquascrotum on 2009-08-16
Hi all

Despite having been through the wars trying to get my own machines wireless connection to work in Jaunty about 4 months ago, I've decided to try again with my folks Dell desktop.

To start:
Chip is a Broadcom BCM4318.

Output from lshw -C network

```
kyle@HomeDell:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:9f:44:ae
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 ip=192.168.0.5 latency=0 module=e1000e multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:8c:01:b9:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 42:70:78:0b:d1:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Output from iwconfig

```
kyle@HomeDell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Output from sudo iwlist scanning

```
kyle@HomeDell:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.
```

Not sure where to go from here. Goes without saying that Wicd (and network manager before it) are saying there are no wifi networks to connect to.

---

### Post by Metaljaz on 2009-08-16
Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:
(Make sure you are using a wired internet connection)

sudo apt-get update
sudo apt-get install b43-fwcutter

Then Go under System > Administration > Hardware Drivers and make sure the driver is activated. If it is activated in the top right hand corner look for the icon for wireless internet connection. Click on the connection to use it.
Make sure you unplug your wired connection.

---

### Post by aquascrotum on 2009-08-17
Sorry, posted this in haste - running the driver configuration tool (or whatever it was called) picked up the driver and installed it, everything working hunky dory now :)

---

