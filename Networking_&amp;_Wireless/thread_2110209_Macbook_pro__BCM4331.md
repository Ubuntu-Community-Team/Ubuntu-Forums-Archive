---
title: "Macbook pro / BCM4331"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by MADtesla on 2013-01-29
Hello, i did my HW by trying several methods mentioned on the forum and even youtube clips to solve my problem with the wireless connection but i must admit i failed.

i cant establish a wireless connection on Ubuntu using my Macbook pro these are some of the info that could help you guys to figuer out what is the problem :

tesla@teslaMC:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
01:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
03:00.0 FireWire (IEEE 1394): LSI Corporation FW643 [TrueFire] PCIe 1394b Controller (rev 08)
===========
tesla@teslaMC:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.
===========
tesla@teslaMC:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 40:6c:8f:35:20:5e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=57765-v1.37 ip=192.168.11.48 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff

============


So could someone help me !? i am lost i even tried the troubleS.

---

### Post by kc1di on 2013-01-29
Hello MADtesla and welcome to Ubuntu,

There are some difficulties in getting you card set up.

but [here is a page]("https://help.ubuntu.com/community/MacBookPro8-2#Wireless") that will tell you how to do it.
you'll have to use the terminal but it's really not that bad.

before you do any of it make sure to clean up what you've already done. 
by removing any drivers you may have already installed.

---

### Post by MADtesla on 2013-01-30
Hello,

Thank you for the fast reply, i did try what is suggested in the link that you provided me with, to the third step : Edit the /etc/modprobe.d/blacklist.conf and add the line. which i couldnt apply. and i skipped the last step to, i restarted my computer, and the wireless was wroking and i was able to detect my wireless router. BUT i was not able to connect to the network, it kept asking for the password over and over again which i am sure it is correct. i tired to Create a new network with the same name and password as my wireless connection and it established a connection, but i was not able to go online ?

aslo as you suggested to remove any drive before applying these steps i really cant remember if i did, and how to remove it, is there a way to check ?

i followed some insruction on a website to install the network manager and update it, thats as far i could remember ?

Thank you for the help.


i must also put out there that i had the same problem with my Playstation 3 to connect to the network although i am sure of the password.

I DO NOT HAVE THIS PROBLEM IN MY OSX whcih is on the same computer Macbook Pro as Ubuntu.

My wirless router is Buffalo WZR-HP-G450H

:confused:

---

### Post by Bucky Ball on 2013-01-30
*Thread moved to **Networking & Wireless***

Welcome to the forums. 

The router make/model generally, if ever, has anything to do with it. If it is working for your OSX that is not the issue. It is something on your local machine in Ubuntu. Have you tried setting up the network manually by right clicking on the network icon and 'Edit Connections'? Add password, network name, security etc in there. Please give the output of:

```
sudo lshw -C network
```

Network Manager is already installed (the network icon) and please tell which Ubuntu release you are using.

---

### Post by MADtesla on 2013-01-30
OK, yeah i guess your right, but i had to point that out.

Well am suing Ubuntu 12.04, and the sudo lshw -c network

tesla@teslaMC:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM57765 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 40:6c:8f:35:20:5e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.123 duplex=full firmware=57765-v1.37 ip=192.168.11.48  latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:a0400000-a040ffff memory:a0410000-a041ffff
  *-network
       description: Network controller
       product: BCM4331 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:a0600000-a0603fff

Aslo yeah i did try the Eddit connection. and i was able to establish a connection with the wireless router doing manually as you suggested, but after it connected i cant open any website. it even connects automatically when i turn on Ubuntu.

---

### Post by Bucky Ball on 2013-01-30
Are you by any chance running a static IP for your machine on your LAN? If so, you may need to add the DNS IPs manually in Network Manager (Edit Connections).

If the wireless is connecting automatically, that's a good sign. Hopefully an easy tweak. When connected, could you give the output of:

iwconfig

* Also, this might help:

[http://ubuntuforums.org/showthread.php?t=1966236](http://ubuntuforums.org/showthread.php?t=1966236)

Try insalling b43-fwcutter & firmware-b43-installer from Software Centre first and restart to see if it takes effect. They may already be disabled in Additional Drivers if you have a look there first.

---

