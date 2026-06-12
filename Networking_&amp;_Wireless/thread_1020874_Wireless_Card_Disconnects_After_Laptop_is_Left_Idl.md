---
title: "Wireless Card Disconnects After Laptop is Left Idle"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by kyleflan on 2008-12-24
I have a problem with my wireless card: After my laptop is left idle for an hour or so, my wireless card drops my internet connection. I know it's not the network because other Windows computers are connected wirelessly to this network without a problem. Also, the wireless card works fine under Windows. (I dualboot XP and Ubuntu 8.10)

This only occurs when I leave my laptop idle; I've never had my connection dropped while using the computer. I was wondering if maybe Ubuntu was shutting off my wireless card after the laptop has been idle for x minutes? I went to System > Preferences > Power Management but didn't find any settings for hardware in relation to my problem.

When I come back to my laptop after the connection is disabled there's a window that has the name of the connection, a box for the WEP key, and other settings that have the correct settings for the card; however if I click connect, all that happens is that it continually "requests a network address from 2WIRE..." and then the same box is displayed again. I have to disable and re-enable networking a couple times before I can reconnect. 

Here's the output of lshw -C network for details of my card:
```
kyle@Kyle-Laptop-Linux:~$ sudo lshw -C network
[sudo] password for kyle: 
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:40:d0:3c:e7:23
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=128 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 01
       serial: 00:02:8a:9e:62:13
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.5.6 ip=192.168.0.2 latency=128 link=yes module=orinoco_pci multicast=yes wireless=IEEE 802.11b
```

And iwconfig
```
kyle@Kyle-Laptop-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"2WIRE635"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E4:9C:A3:B1   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/92  Signal level=-21 dBm  Noise level=-140 dBm
          Rx invalid nwid:0  Rx invalid crypt:59  Rx invalid frag:2
          Tx excessive retries:29  Invalid misc:0   Missed beacon:0

```

---

### Post by 73ckn797 on 2008-12-24
I use WICD on my laptop. I assume you are using the default network manager in Ubuntu.

Mine does not have a setting to put the wireless device to sleep but in the preferences I find a switch to automatically reconnect on lost connection. I do not know whether this would be your problem but thought I would pass along the info to stir your diagnosis.

---

### Post by kyleflan on 2008-12-26
I installed WICD, but I'm still having the same problem. One posivitve is that it's now easier to reconnect with WICD after the card loses the connection. (Auto-reconnect failed to automatically reconnect the connection, though.)

Any other ideas?

---

