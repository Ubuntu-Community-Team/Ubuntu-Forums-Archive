---
title: "Realtek r8169, only 100 Mbps"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by cdhln on 2010-10-28
I'm running Ubuntu Server 10.10, but have also tried this with Server 10.04.

My ZOTAC NM10-DTX WiFi with integrated Realtek R8169 Gbps Ethernet controller just give me 100 Mbps connection.

The router and cable works fine - I've connected the very same cable to another computer and it gets Gbps connection.

I've updated the drivers to newest (6.014.00), which is confirmed by lshw -C network.

ethtools eth0 states that the speed is 100 Mbps from autoneg, the other part advice mine to use 100 Mbps.

I've tried ethtools -s eth0 speed 1000 duplex full autoneg on/off (tried both), but then my card goes down to 10 Mbps half duplex.

What can I do? :confused:

---

### Post by cdhln on 2010-10-28
OK, I feel stupid now. I installed the 6.014.00 drivers for another card. My card wanted the 6.013.00. Now I get 1000 Mbps in ethtools. Sorry for wasting your time! :popcorn:

---

### Post by cdhln on 2010-10-29
UPDATE: Not solved. It was the linux drivers who fooled me, my new drivers  werent loaded at start. ethtools tell me that I have 1000 Mbps, but my  router shows blue light (blue = 100 Mbps, green = 1 Gbps), and I just  get 100 Mbps transfer speed with nfs. :confused:

---

### Post by refuser on 2010-10-29
+1
Bump!

---

### Post by cdhln on 2010-10-30
UPDATE: Tried with Ubuntu Desktop 10.04.1 32 Bit without success, same problem. I checked the chip on the motherboard, it's indeed RTL8110SC.

Some outputs people might be interested in:

lsmod | grep r816:
```

r8169                  31142  0 

```lshw -C network:
```

  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:f0:c3:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-server firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:03:0b.0
       logical name: eth0
       version: 10
       serial: 00:01:2e:2c:cc:fc
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.014.00-NAPI duplex=full firmware=N/A ip=192.168.1.200 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 ioport:e800(size=256) memory:febdfc00-febdfcff memory:febe0000-febfffff

```ethtool eth0:
```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

```

---

### Post by elico on 2010-10-30
i have the same card and it works fine on ubuntu 10.04 server 64BIT.
do you have VIRTUALBOX installed on one of your machines?

---

### Post by cdhln on 2010-10-30
> **elico said:**
> i have the same card and it works fine on ubuntu 10.04 server 64BIT.
do you have VIRTUALBOX installed on one of your machines?
Thanks for your reply. Do your card work with 1 Gbps speed, or just 100 Mbps? ethtool tell me 1000 Mbps with standard drivers, but just give me 100 Mbps. With realtek's newest drivers, I get 100 Mbps in ethtools and as real speed.

Nope, no VIRTUALBOX installed :confused:

---

### Post by MooPi on 2010-10-30
Can you post ```
iwconfig
```

---

### Post by kklein90 on 2010-10-30
Same issue here.  Only getting 100Mbs reported from ethtool and my file transfers are godawful.  I'm connected to a Linksys 5 port gig switch.

---

### Post by kklein90 on 2010-10-30
Also, this was not an issue when I was running 10.4, just since the upgrade and updates for 10.10.

---

### Post by cdhln on 2010-10-30
> **MooPi said:**
> Can you post ```
iwconfig
```
You mean ifconfig? iwconfig is just for wireless, right?

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:01:2e:2c:cc:fc  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe2c:ccfc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104534333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55040772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:153778633625 (153.7 GB)  TX bytes:4769073857 (4.7 GB)
          Interrupt:16 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22768 (22.7 KB)  TX bytes:22768 (22.7 KB)

```

---

### Post by cdhln on 2010-10-30
> **kklein90 said:**
> Also, this was not an issue when I was running 10.4, just since the upgrade and updates for 10.10.
You have the RTL8110SC chip too? Have you updated the drivers to 6.014.00? I also had to do some update so the machine loaded loaded the newest drivers everytime I reboot.

---

### Post by cdhln on 2010-11-02
UPDATE: Still not working.. Found a command which might help.

modinfo r8169:
```

filename:       /lib/modules/2.6.35-22-server/kernel/drivers/net/r8169.ko
version:        6.014.00-NAPI
license:        GPL
description:    RealTek RTL-8169 Gigabit Ethernet driver
author:         Realtek and the Linux r8169 crew <netdev@vger.kernel.org>
srcversion:     34F60A9209ED941EFF6985D
alias:          pci:v000010ECd00008169sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008167sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-22-server SMP mod_unload modversions 
parm:           speed:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           duplex:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           autoneg:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)

```

The "force phy operation. Deprecated by ethtool" part seems interesting. I have tried loading the module with both:
```

insmod ./src/r8169.ko speed=1000 duplex=1 autoneg=1
insmod ./src/r8169.ko speed=1000 duplex=1 autoneg=0

```
But the card just gets 100 Mbps.

---

### Post by al090187 on 2010-11-02
I had a very similar problem to yours, but now mine has got much worse.

I noticed the transfer speed to my server had dropped, to about 7mbit, so went down there and connection details stated it was connected at 10mbit, while the router light was green, indicating 1gbit. I found a thread giving the link to the new drivers, 6.013 i believe, and I installed them. The connection then worked at 100mbit. Since then it has been restarted several times, and the gigabit speeds eventually returned. 

Today, I turned it on, went back upstairs to access the media server, and couldn't find it. On returning to the server, the network icon showed no network adapters were available. 

Strangely, the router still shows a green light, which flashes, indicating network traffic on the port. 

I tried reinstalling the drivers, and restarted a couple of times, still no luck. 

The system is Ubuntu Server 10.04 with gui installed. The server is attached to a gigabit switch, with the internet modem attached to the switch. 

Any ideas?

---

### Post by cdhln on 2010-11-03
> **al090187 said:**
> I had a very similar problem to yours, but now mine has got much worse.

I noticed the transfer speed to my server had dropped, to about 7mbit, so went down there and connection details stated it was connected at 10mbit, while the router light was green, indicating 1gbit. I found a thread giving the link to the new drivers, 6.013 i believe, and I installed them. The connection then worked at 100mbit. Since then it has been restarted several times, and the gigabit speeds eventually returned. 

Today, I turned it on, went back upstairs to access the media server, and couldn't find it. On returning to the server, the network icon showed no network adapters were available. 

Strangely, the router still shows a green light, which flashes, indicating network traffic on the port. 

I tried reinstalling the drivers, and restarted a couple of times, still no luck. 

The system is Ubuntu Server 10.04 with gui installed. The server is attached to a gigabit switch, with the internet modem attached to the switch. 

Any ideas?
My problem is a bit different, but I guess similar since it's the same chip (yours is also RTL8110SC, right?). My router tell me it's just 100 Mbps. Have you tried the insmod /src/r8169.ko speed=1000 duplex=1 autoneg=1 (or 0?)?

---

### Post by cdhln on 2010-11-07
I've now also tried to remove the power from the computer as some have suggested for Realtek chips, without any luck :(

---

### Post by cdhln on 2010-11-19
A little update: seems like it was the chip which was broken, the store sent me a new motherboard today. I'll set as 'solved' when I get the motherboard and get it to work.

---

### Post by cdhln on 2010-11-25
> **cdhln said:**
> A little update: seems like it was the chip which was broken, the store sent me a new motherboard today. I'll set as 'solved' when I get the motherboard and get it to work.
I get 1 Gbps with a fresh system with my new motherboard. So my problem was faulty hardware.

---

### Post by copycat on 2011-01-16
> **cdhln said:**
> I get 1 Gbps with a fresh system with my new motherboard. So my problem was faulty hardware.

same problem here.
My internal card works fine, the r8169 with mtu 7000 for nfs shows 100Mb.

Driver update 6.013.00 didn't fix,  It is 10.04 lucid on MSI Media Live Backbone.  

I have read something about virtualbox.  I use KVM-qemu. Maybe it's the virtual adapters causing it.

---

### Post by nbusy on 2011-03-02
I've got the same issue (running 100Mbps).
How do you guys update the driver?
I've downloaded one from Realtek but it says that a kernel needs to be recompiled ???
I've no idea how to deal with it.
Please help.

---

### Post by Marko723 on 2011-03-05
I'm having the exact same problem.  I even installed ethtool and tried changing the speed to 10Mb/s, and when I query the card it says it's running at 1000Mb/s, but my switch (smart switch) reports it at 100Mb/s.
 
It seems that the card is locked at 100Mb/s and can't be changed.

---

### Post by xdevnull on 2011-03-15
rrrr...I had this running with the blob from Realtek.  It loads r816**8**, which has always worked.  Now with the latest Ubuntu (10.10 x64) update it loads r8169 - and I can't get it to stop.  I've updated it in blacklist.conf: 

#blacklist broken nic driver
blacklist r8169


But it still loads on restart.  Now I'm having trouble with getting r8168 to run at 1000.  All this started b/c I dual boot and windows does something weird to the card.  With the blob r8168 all was fine - now this.  It's pretty irritating that Ubuntu breaks when it updates.  Any help out there on how to get the working driver to load properly?

---

