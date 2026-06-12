---
title: "Internet help"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by _/0|-||\| on 2011-08-03
Ok, so i tried using the ubuntu 11.04 cd but it didnt work so i had to dig out my old ubuntu 8.04 livecd. I had a computer with windows xp totally get wasted and i decided to do a clean install with ubuntu 8.04 and update to the newer version, however i cannot get the internet to connect (wired), ive tried figuring out of there is a driver problem but was not able to figure it out. Ive been searching for hours and am drawing a blank, can anyone help with this?

---

### Post by Iowan on 2011-08-03
From a terminal (Applications>Accessories>Terminal) check **ifconfig -a** and **sudo lshw -C network**. Post results.

---

### Post by _/0|-||\| on 2011-08-03
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:ec:c0:03:48  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:853373 (833.3 KB)  TX bytes:18680 (18.2 KB)
          Interrupt:20 Base address:0xe400 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:ec:c0:03:48  
          inet addr:169.254.5.163  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104052 (101.6 KB)  TX bytes:104052 (101.6 KB)


sudo lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
        -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by bkratz on 2011-08-03
You need a capital C in that last command. Linux is particular about case and spacing.

---

### Post by _/0|-||\| on 2011-08-03
sorry bout that, forgot about it being case sensitive 


sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:16:ec:c0:03:48
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by Iowan on 2011-08-03
The avahi-address suggests the DHCP server didn't provide an IP - and avahi stepped in to "help" - which left eth0 in a subnet by itself. You can try running **sudo dhclient eth0** - I suspect it'll try for awhile and come back with something like "no offers received... sleeping."

---

### Post by _/0|-||\| on 2011-08-03
sorry it took so long to reply, for some reason my browser wasnt showing a responce, here is what happened



sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:ec:c0:03:48
Sending on   LPF/eth0/00:16:ec:c0:03:48
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


so what should i do now since every other device in the house has internet?

---

### Post by _/0|-||\| on 2011-08-04
Also, not only what should i do next, but i am finding a lot of information about ubuntu's around 8.10 or so are not supported, does this mean i cannot use 8.04 to get internet access? how should i handle this since this is the only computer not getting internet?

---

### Post by _/0|-||\| on 2011-08-04
I'm still doing searching (mostly because for some reason i cannot get a new boot disk to work on my problem computer) but am finding a lot of it may being a driver problem. How would i go about checking this in ubuntu?

---

### Post by lkjoel on 2011-08-04
Try Ubuntu 10.04.

---

