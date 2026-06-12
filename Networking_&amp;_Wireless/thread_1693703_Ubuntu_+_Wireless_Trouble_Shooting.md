---
title: "Ubuntu + Wireless Trouble Shooting"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by whitneybdy on 2011-02-23
1.  While running Ubunu 10.10 on my HP G60-445DX the once working wireless driver stopped being responsive.  The terminal output read as such:
>   *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter 0: hp-wifi: Wireless LAN
 Soft blocked: yes
 Hard blocked: no
1: phy0: Wireless LAN
 Soft blocked: yes
 Hard blocked: no
lo Interface doesn't support scanning.
 eth0 Interface doesn't support scanning.
 wlan0 Interface doesn't support scanning : Network is down
 wlan0 IEEE 802.11bg ESSID:off/any
          Mode:Managed Access Point: Not-Associated Tx-Power=off
          Retry long limit:7 RTS thr:off Fragment thr:off
          Power Management:off
 [main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true


2.  Ran BIOS to turn the driver on that way (it had gotten turned off, but not my own willful decision).  The driver turned on, but while running Ubuntu, it still would not connect or recognize the network.  I also used the following commands in the terminal without luck:
> rfkill unblock all
 sudo rfkill unblock all


3.  After reading[ this post]("http://ubuntuforums.org/showthread.php?t=1683816") and another Ubuntu page that listed supported drivers, I deducted that my nVidia card must not work in Ubuntu.  **Keep in mind, I have been running Ubuntu for about eight weeks without a problem**, but I had run a software update around the same time that my wireless stopped working.

4.  Installed Ubuntu 10.04 per the last suggested step.  My wireless is still not working, however, unlike step 1, my terminal now reads:
>   *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:e0:f7:6a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.101 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:56:02:4b:be
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff

5.  I repeated step 2 but without luck.  While I can input my network ID and password (which I was unable to do while working through the issue with Ubuntu 10.10), it still will not connect to the network.  My network card now is not ENABLED, DISABLED, CLAIMED, or UNCLAIMED which is an issue I had not expected to encounter.


Please help.

---

