---
title: "Kismet config on Asus Eee 1005HA"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by whiterabbit7500 on 2010-01-06
I've read through 99% of the other "kismet config" help threads, and can't find any help with this. 

lshw -C network output
```
*-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:72:d0:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=10.1.1.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:20:ea:f9
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```

.config file (The relevant part at least)
```
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=your_user_here

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath9k,wlan0,Wireless
```

Output I receive
```
whiterabbit@WR-h4x:/etc/kismet$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ath9k' in source 'ath9k,wlan0,Wireless'
Done.
```

I checked the driver name, which in my case is ath9k, set the interface to wlan0, and the name to Wireless. Should I be using something different? How can I get this working?

---

### Post by whiterabbit7500 on 2010-01-06
bump...nobody?

---

### Post by whiterabbit7500 on 2010-01-07
nothing? bump

---

### Post by pdc on 2010-01-07
this is what you have installed?

[http://www.kismetwireless.net/](http://www.kismetwireless.net/)

I note this link says

> IRC
Stop by #kismet on irc.freenode.net. 

often talking directly to such folks is best

---

### Post by linux nut on 2010-01-07
To get the wirless working u have to download the 2.6.30 kernel install it because it has the driver u need it worked for me. 
Download the following packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/").
 - linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb
 - linux-headers-2.6.30-020630_2.6.30-020630_all.deb
 - linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

---

### Post by whiterabbit7500 on 2010-01-07
> **linux nut said:**
> To get the wirless working u have to download the 2.6.30 kernel install it because it has the driver u need it worked for me. 
Download the following packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/").
 - linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb
 - linux-headers-2.6.30-020630_2.6.30-020630_all.deb
 - linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

I'm already running 2.6.31-16-generic

---

### Post by whiterabbit7500 on 2010-01-08
so i stopped by the kismet IRC, and tried to upgrade to the latest version of Kismet, but was unable to ./configure due to it nor finding libncurses, even though it is installed and updated.

anyone else have this problem before?

---

### Post by whiterabbit7500 on 2010-01-08
problem solved. I needed to add the *-dev packages as well for the compiler to work correctly.

---

### Post by mrdubelina on 2010-02-11
> **whiterabbit7500 said:**
> problem solved. I needed to add the *-dev packages as well for the compiler to work correctly.
problem solved. I needed to add the *-dev packages as well for the compiler to work correctly.

Am at exact same point as your earlier post using eee 1005ha with Karmic Netbook Remix but am pretty new to Linux.
How do I 'add the *-dev packages as well for the compiler to work correctly'? Thanx

---

