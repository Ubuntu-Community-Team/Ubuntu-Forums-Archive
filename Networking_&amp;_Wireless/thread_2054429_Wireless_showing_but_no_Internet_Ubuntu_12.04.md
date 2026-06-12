---
title: "Wireless showing but no Internet Ubuntu 12.04"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by Langney on 2012-09-07
Hi there sorry I keep coming In here giving you guys headaches but I have another problem. I have the WNDA3100 USB wireless card thingy which worked on Ubuntu 10.04 no problems but I upgraded this morning and got connected through wireless as normal but for some reason the connection drops whist still showing connected. I've messed up my update through update manager now twice. The only temp solution I can find Is by opening up my wireless manager and resetting the connection. Even then It only lasts like 30 seconds. Any Idea's on what I can do? 


Thanks In advance

---

### Post by Langney on 2012-09-08
Hello? Anyone?

---

### Post by greatsirkain on 2012-09-08
check that it's connecting to the correct connection & that you've provided the network password after the upgrade? When I upgraded it did the same, I just clicked on the wireless icon and found it was trying to automatically connect to my next door neighbors internet. If that doesn't work try restarting your router followed by resetting if you still can't connect. 
You can tell if you're at least connected to your router/modem usually by going to 192.168.1.254  in your internet browser if you get a page then you are connected and it probably is a router/ISP problem

Edit:
Also if you can get to your routers settings make sure it's providing enough IP addresses for the amount of devices connecting to it

---

### Post by steeldriver on 2012-09-08
I think there are a couple of different versions of that card - can you please open a terminal window and do

```
lsusb
``````
lshw -C network
```so we can double check the chipset / driver?

---

### Post by Langney on 2012-09-09
Hi there. It's Version 3. Funny thing Is It works on Ubuntu 10.04 and Windows perfectly. So not an ISP problem or modem problem :)

Any Idea's as at the moment I'm stuck on my Whinedows box :(

---

### Post by greatsirkain on 2012-09-11
Hi :) If it's up for 30 seconds but then drops it sounds like your card is working fine just it's not supplying the correct details to the modem, that's why I wanted to see if you could get a stable connection just to it & not the internet. Upgrades can be funny and stop things working (just ask my soundcard :P ) so don't go on what you can do on different versions, concentrate on this one. And if you could post the usb and network hardware lists that steeldriver asked for, that way he can see exactly what the OS sees & tell if something's wrong

---

### Post by GothFraex on 2012-09-23
Hello, I've been having the same problems as Langney. I have no problem connecting to my network but I can only access the internet for a few minutes at a time before I need to reconnect. I've had this problem for more than a month and can't seem to find a solution. 

Here's the output of the commands above:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:c335 Z-Star Microelectronics Corp.
``````
  *-network               
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:b5:57:0d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0014.0401.2010 ip=192.168.0.12 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:f6000000-f6003fff
  *-network
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:13:77:ff:f2:74
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fa000000-fa003fff ioport:5000(size=256) memory:f4000000-f401ffff

```

Thanks in advance for any help :)

---

