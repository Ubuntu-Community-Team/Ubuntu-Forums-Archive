---
title: "NIC Not Detected"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by afhkhan on 2009-10-28
Hello Everyone,

I am very new to linux and Ubuntu and bought a new acer laptop (Acer Aspire 5732z) and duly removed windows and installed Ubuntu 9.04 desktop. After the installation I have found that the network card is not installed. Pls advise where I coudl download appropriate driver and how to install it.

Any help is deeply appreciated.

Many Thanks,
afhkhan

---

### Post by chili555 on 2009-10-28
Let's ask the computer what kind of ethernet card it has. Open a terminal and do:```
sudo lshw -C network
```Post the result and we will proceed.

---

### Post by afhkhan on 2009-10-28
> **chili555 said:**
> Let's ask the computer what kind of ethernet card it has. Open a terminal and do:```
sudo lshw -C network
```Post the result and we will proceed.


This is the result I get. I appreciate all the efforts.

*-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 0c:60:76:34:07:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 
802.11bgn
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:95:83:bf:a5:bf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by chili555 on 2009-10-28
May we assume you want to get the ethernet going, and not the wireless (which appears to be 'going' quite well)? If so, please let us see the result of:```
sudo lspci -nn | grep 05:00
```I am already afraid of the answer! Do you have any internet connectivity, with the wireless, perhaps, in case we need to download a few files?

---

### Post by afhkhan on 2009-10-28
> **chili555 said:**
> May we assume you want to get the ethernet going, and not the wireless (which appears to be 'going' quite well)? If so, please let us see the result of:```
sudo lspci -nn | grep 05:00
```I am already afraid of the answer! Do you have any internet connectivity, with the wireless, perhaps, in case we need to download a few files?

The output result is as follows:

05:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1062] (rev c0)

**I am not able to connect to internet thru wireless as well.**

---

### Post by chili555 on 2009-10-28
> [COLOR="DarkOrange"][1969:1062][/COLOR]Ouch!

Here is another thread with exactly the same device: [http://ubuntuforums.org/showthread.php?t=1297854](http://ubuntuforums.org/showthread.php?t=1297854)

The short version is that the driver is not included in version 9.04, but is included in version 9.10. If you have a relatively new installation, it may be far easier to download and install 9.10. See post #33.

There is an *atl1c* driver out there somewhere, but it is a bit difficult to compile and install.

Please let us know what you want to do.

---

### Post by afhkhan on 2009-10-28
> **chili555 said:**
> Ouch!

Here is another thread with exactly the same device: [http://ubuntuforums.org/showthread.php?t=1297854](http://ubuntuforums.org/showthread.php?t=1297854)

The short version is that the driver is not included in version 9.04, but is included in version 9.10. If you have a relatively new installation, it may be far easier to download and install 9.10. See post #33.

There is an *atl1c* driver out there somewhere, but it is a bit difficult to compile and install.

Please let us know what you want to do.


As suggested I will do a fresh installation of Ubuntu 9.10 which releases in a day or so... [:)]

**Many thanks to Chili555....Your time and efforts are appreciated and respected**

---

### Post by chili555 on 2009-10-28
Thank you very much for your very kind comments. Please post again if we can help you in any way!

---

### Post by afhkhan on 2009-10-30
Hi!

I have installed Ubuntu 9.10 and everything is resolved. Many thanks fr all your help :)

---

