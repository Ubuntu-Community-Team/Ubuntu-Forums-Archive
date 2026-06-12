---
title: "Kismet Config"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by tfdelaney on 2012-11-19
I'm trying to configure my Kismet.conf.  I keep getting this message:

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'r8169' in source 'r8169,eth0,realtec'
Done.


Here is my lshw:

*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:f6:45:fc
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:5000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff

I have my laptop plugged into ehternet because for some reason my wireless is not turning on.  Any help with the above and the wireless situation would be greatly appreciated.
Thanks,
Tom

---

### Post by chili555 on 2012-11-20
From *man kismet*:> NAME
     kismet — *Wireless* sniffing and monitoringSo your wired ethernet details are completely meaningless to Kismet. 

Let's troubleshoot the wireless:```
lspci -nn | grep 0280
lsusb
rfkill list all
```Thanks.

---

### Post by dmatsumoto on 2013-04-12
Hi chili555, I was also under the impression that kismet_server can run under ubuntu with a wired connection.  People have been running kismet_drone on routers running OpenWRT, and then running the server on ubuntu.  And from the kismet website, they say:

14. Drone Remotes

    Remote Kismet drones are designed to turn Kismet into a stationary, 
    distibuted IDS system.  Drones support all of the capture sources Kismet
    supports, and can have multiple cards per drone.  Drones capture wireless
    data and report it over a secondary connection (typically wired ethernet),
    and have very minimal hardware requirements.

It seems that most people here are doing everything with ubuntu, but there must be some people that want to just run kismet_server on ubuntu and merely log whatever packets kismet_drone captures over the wireless network.

I've looked high and low for information on configuring kismet_server, and have come up short.  Your helpful posts here in the "Configuring Kismet" thread were great to read, and the whole time I thought I might have a chance of using the info in lshw and ifconfig to make kismet happy with my kismet.conf, but I have failed at every attempt so far.  Your post concerns me because I'm worried now that what I'm trying to do is impossible.  Yet the kismet website implies that it should be doable!

---

### Post by chili555 on 2013-04-12
> there must be some people that want to just run kismet_server on ubuntu and merely log whatever packets kismet_drone captures over the wireless network.

I've looked high and low for information on configuring kismet_server, and have come up short.I am quite sure it can be done, because it *is* being done, however, it's very far outside my area of meager knowledge. I suspect you'd get a bit more useful information here: [http://www.dd-wrt.com/phpBB2/](http://www.dd-wrt.com/phpBB2/)

---

