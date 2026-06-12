---
title: "Ethernet&amp;Wireless Problems!"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by JethroGillgren on 2011-06-13
Hi All

Am having problems getting back online, both Wireless and Ethernet are spending a minute trying to connect then disconnecting with No error messages.
Connection works fine on other computers and on my Windows Partition. It only broke recently, just before i upgraded to the new version. It will connect to BTFon but i don't have access to that.

I would greatly appreciate any help/suggestions. Have tried following documentation answers but have become stuck/not worked.
Thanks So much for any help!
Jethro

> 
jethro@ubuntu:~$ cat /etc/issue
Ubuntu 11.04 \n \l



jethro@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)




jethro@ubuntu:~$ sudo lshw -C network
[sudo] password for jethro: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:b6:5b:d7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:f9fff000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:92:c1:9d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:f9bfe000-f9bfffff










jethro@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:1B:77:B6:5B:D7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BTHomeHub2-RWN8: Infra, 00:21:04:AD:B0:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    BTFON:           Infra, 0A:21:04:AD:B0:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    BTOpenzone:      Infra, 06:21:04:AD:B0:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    TP-LINK_E7C04B:  Infra, D8:5D:4C:E7:C0:4A, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             disconnected
  Default:           no
  HW Address:        00:1C:23:92:C1:9D

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on





Using the nm-tool command while trying to connect either wired/wireless shows it gets stuck on State: getting IP Configuration.

---

### Post by JethroGillgren on 2011-06-14
Any Ideas? I Don't really want to do a clean install it took long enough to get everything I wanted compiled lol.

---

### Post by JethroGillgren on 2011-06-14
Deleted the partition and did new install same problem. I didn't change any settings on the HomeHub when it stopped working so am at a loss. Reconfiguring the router from scratch now.

---

### Post by wilbyforce on 2011-06-14
Didn't you search this forum for "Homehub" before taking such drastic action?

---

### Post by JethroGillgren on 2011-06-14
This Solved it for me:

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

I had tried changing the IP settings in a similar solution but must have hashed it up.

---

