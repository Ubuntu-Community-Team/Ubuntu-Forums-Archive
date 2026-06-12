---
title: "Wired connection doesn't connect"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by d4r3 on 2012-11-11
Hi. I realize there are many threads about this, but i have tried many solutions and nothing worked as of yet.

So the problem is, that the wired connection doesnt connect, it tries now and then and it always says 'wired network disconnected'. This happened after i've installed proprietary graphic drivers and they didnt work so i had to hard-restart the pc, then in grub chose safe graphic mode or something like that and once there the internet worked, but the icon showed it was disconnected. It said that the manager is not managing the connection. I changed that from false to true and it stopped working alltogether.  

I don't know where the problem is. I can only get online via phone thetering, so my surfing and researching capabilites are severely limited. I would appreciate any help i can get. 

d4r3

---

### Post by ajgreeny on 2012-11-11
It is unusual for a wired connection not to work.

What is the output of ```
ifconfig
``` in terminal, and what network hardware are you using, which you can see from ```
sudo lshw -c network
``` or ```
lspci
```

Are you connected to a router, and if so can you ping that in terminal with ```
ping -c 5 192.168.0.1
```I show the IP of my own router here, but yours may be different; look on the label or router manual info to find it if you don't know what it is.

---

### Post by d4r3 on 2012-11-11
ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:ff:7d:9a  
          inet6 addr: fe80::223:8bff:feff:7d9a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169250 (169.2 KB)  TX bytes:16105 (16.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9862 (9.8 KB)  TX bytes:9862 (9.8 KB)

usb0      Link encap:Ethernet  HWaddr 96:96:10:4a:30:51  
          inet addr:192.168.42.171  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::9496:10ff:fe4a:3051/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:292255 (292.2 KB)  TX bytes:100378 (100.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:65:3f:36:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

hardware:

```
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:3f:36:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-18-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:c0000000-c0001fff
  *-network
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:23:8b:ff:7d:9a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:c0500000-c0503fff ioport:4000(size=256)
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 96:96:10:4a:30:51
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.171 link=yes multicast=yes

```

I live in a student dorm and i dont know anything about a router, nothing is wrong on that end, everyone else's internet in the dorm works.

---

### Post by d4r3 on 2012-11-11
Also during boot it says "waiting up to 60 more seconds for network configuration", and now it boots without internet capabilities, the icon in the upper right corner is gone.

Sorry for double posting, im panicking and am pretty screwed without internet. Also wouldn't like to format again right now.

I have discovered the EDIT option :) :

It seems I have been victorious at last. I have reinstalled 12.04 (only had that usb thumb with me) and internet seemed fine. Updated to 12.10 and it stopped working again. Same thing. Well, as a last resort i have decided to reset iptables. That did the trick, if you can believe it.

I'm sorry for all the inconvenience i may have caused. Thanx for all the help.

---

