---
title: "dir 655 won't connect to ubuntu 10.04 on T410 laptop"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by polukas on 2010-09-18
running  Lenovo T410 and wireless won't connect at all, wired works fine but wireless can't even see any neighbored network , after lshw -c network i get this result
*-network DISABLED
       description: Wireless interface
       product: WiFi Link 6000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:0a:a6:bc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:35 memory:f2000000-f2001fff
**********
the funny thing is i have check marked as enable networking and wireless
and i have installed hardware and activated as well


please any suggestion would be great

---

### Post by mogambo on 2010-10-16
same issue for me too on 10.10

* have installed 64 bit Ubuntu but my *Wireless interface width is displayed as 32 bits. will that cause any issue on 64 bit OS ?

**sudo lshw -C network**

  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=180.0.1.20 latency=0 link=yes multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f2400000-f2403fff
r

---

### Post by mogambo on 2010-10-29
finally it worked for me 

Problem 
eth connection worked fine but when i used to connect through   wireless it was dead slow. I was able to access my router configuration screen through wireless connection but was unable/slow external website .


[LIST]
[*]Right-click on the Network Manager applet and choose Edit Connections.
[*]Edit your active internet connection, and go to the IPv4 Settings.
[*]Change 'Method' to 'Automatic (DHCP) addresses only'
[*]Enter into the 'DNS servers' field: 192.168.1.1
[*]Leave the 'Search domains' and 'DHCP client ID' entries blank
[/LIST]
more info on [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9119483&postcount=51](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9119483&postcount=51)


mogambo
:guitar:

---

