---
title: "Wireless 12.04 Atheros AR9485"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by patroskam on 2013-02-03
Hello everyone...Im relatively new to Ubuntu with some limited linux experience...I purchased a new Asus laptop and installed Ubuntu 12.04 from a flash drive. Everything installed and updated correctly with no errors. My wireless is giving me trouble however...I have looked around a lot and have not found anything that works as of yet. I dont know what kind of outputs anyone would like to see but I am happy to post them...again...Im new...
 
Problem:
 
My wireless is just WEP encrypted...the laptop sees my AP, connectes to it, lets me download, browse, or anything...when I move away from the access point by about 15 feet...the connected drops, comes back, drops, making it impossible to do anything. I walk back to the AP and all is well again...
 
 
Things I have tried:
 
disabled power managment, set for all users, blacklisted the asus_wmi module (which helped retain a connection but was slow until a reboot then didnt work anymore)
 
any ideas or direction is much appreciated. Thanks everyone...

---

### Post by ahallubuntu on 2013-02-03
~

---

### Post by patroskam on 2013-02-03
sudo lshw -C network

  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: dc:85:de:71:a1:57
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-36-generic-pae firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: 50:46:5d:98:fc:9d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff


iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"KaBlam!"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:62:5B:1A:2E   
          Bit Rate=13 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:361   Missed beacon:0

eth0      no wireless extensions.


lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)

---

### Post by ahallubuntu on 2013-02-03
~

---

### Post by patroskam on 2013-02-03
I tried that one as well...it still disconnects when I walk away from the access point...

---

### Post by patroskam on 2013-02-03
tried checking for driver updates, looked into ndiswrapper but havent gone that route yet...it works as long as I am near the AP ( a little slow but works)...
 
also I cant connect to any other AP's even if I am near them...not sure if that helps....
 
...random...

---

### Post by patroskam on 2013-02-05
Has anyone gotten this card working in 12.04?  I am really new to Ubuntu...is there something special I need to do to pull an old driver out and ensure and updated one is in there?  Or is this just a problem card that I will always have issues with?
 
Thanks everyone.

---

