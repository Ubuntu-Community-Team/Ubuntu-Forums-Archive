---
title: "Ubuntu 10.04 on HP G62 can't get wireless"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by ecn on 2010-09-16
Hi,

I have just installed ubuntu 10.04 on my laptop (HP G62) and it is not detecting any wireless networks. I have installed it alongside windows and when i am on the windows side it detects the wireless networks fine.

I have tried looking at the wireless troubleshooting guide, but it says to obtain the windows driver for your system which i do not know how to do. It also says to install the ndisgtk package but when i click on this it says it could not find it.

Any help would be much appreciated

Thanks
ecn

---

### Post by ecn on 2010-09-16
oh and also when i type 'sudo lshw -C network' into the terminal i get...

  	 	 	 	p { margin-bottom: 0.21cm; }   *-network                
        description: Ethernet interface
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: eth0
        version: 02
        serial: 90:fb:a6:a3:46:51
        size: 10MB/s
        capacity: 100MB/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
        resources: irq:26 ioport:6000(size=256) memory:d0010000-d0010fff(prefetchable) memory:d0000000-d000ffff(prefetchable) memory:d0020000-d003ffff(prefetchable)
   *-network UNCLAIMED
        description: Network controller
        product: Broadcom Corporation
        vendor: Broadcom Corporation
        physical id: 0
        bus info: pci@0000:03:00.0
        version: 01
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list
        configuration: latency=0
        resources: memory:d1100000-d1103fff

---

### Post by devonbadman on 2010-09-16
I'm having the same trouble on my G62, but with the 10.10 beta instead. Unfortunately the chipset on the Broadcom wireless chip is 4313 on mine, which as far as I know isn't supported. There probably is a way round but I am yet to find it.

If I do find a way round, I'll let you know.

---

### Post by bkratz on 2010-09-16
@devonbadman

You might want to look through this thread about the 4313.

[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)

---

### Post by ecn on 2010-09-16
Hi again,

So anyone got any ideas what I should do? I don't know what sort of wireless chip I have, I have no idea how to find that out! Any suggestions at all would be good as I really like ubuntu but i def need the internet!!

Thanks

---

### Post by bkratz on 2010-09-16
> **ecn said:**
> Hi again,

So anyone got any ideas what I should do? I don't know what sort of wireless chip I have, I have no idea how to find that out! Any suggestions at all would be good as I really like ubuntu but i def need the internet!!

Thanks

This will give you the required information to determine what yours is.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by spd_demon on 2010-09-16
I just went through this with the 4313 chipset. This link helped and solved it.
Although I can't get the driver to load on start up.
 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Chimney Fish on 2010-09-30
I have 10.04 running in a wubi install on my G62, I was able to get my wireless up and working. heres the output of my 'sudo lshw -C network>

  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:ac:74:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.106 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0100000-d0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:d7:db:2e
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:2000(size=256) memory:d0010000-d0010fff(prefetchable) memory:d0000000-d000ffff(prefetchable) memory:d0020000-d002ffff(prefetchable)

I mounted the iso I downloaded in ubuntu [navigate to host dir. right click ubuntu iso, click 'open with archive mounter'] 

opened the mounted iso in nautilus, navigated to /pool/restricted/b/bcmwl/ and copied the package in that dir to my desktop and installed from there [mounted iso read-only] I believe the only dependency was the dpkg in /pool/main/d/dpkg/ After that I restarted and after login the red led turned white, and i was able to get online.

---

