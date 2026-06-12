---
title: "WIFi on ASUS X51Lseries"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by lannet on 2009-02-19
Helo all,

Please, I have problem with install and stan up WiFi driver for run Network comunications.
Please, You can write me one step-by-step and link for get package.

Thanks, Thanks, Thanks

Best Regards 
Martin - New users ubuntu

---

### Post by mikewhatever on 2009-02-19
Wifi drivers are usually installed by default, even if proprietary. The problem is, not all vendors choose to provide or even develop support for Linux. You should post some details on your wireless hardware to get you started. Enter the following into Terminal and post the output here.

**sudo lshw -C network**

---

### Post by lannet on 2009-02-19
network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:08:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:30:59:a5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:7a:a2:1a:91:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mikewhatever on 2009-02-20
Just as expected, Athros and Broadcom usually mean wireless trouble.

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by binbash on 2009-02-20
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

