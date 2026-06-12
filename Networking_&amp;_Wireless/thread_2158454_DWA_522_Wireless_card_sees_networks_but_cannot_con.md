---
title: "DWA 522 Wireless card sees networks but cannot connect to it."
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by dide101 on 2013-06-29
Ok: First: have I googled this? Yes

currently using ubuntu 12.04 LTS

DWA 522 Network card
AMD athlon X3 425 processor
EVGA GT 240 Graphics card (which I still have to driver-wrestle with...for that i need the internet)
and a Gigabyte 970A UD3 motherboard
Samsung 840 series SSD
Corsair 8 gigs of XMB3 Ram

my lshw -C network output:
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 94:de:80:24:53:11
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:74 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff
  *-network
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wlan0
       version: 01
       serial: 00:18:e7:c4:5a:32
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-23-generic firmware=N/A latency=168 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fe100000-fe10ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

and the iwconfig output:

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

MY PROBLEM:

The issue occurs when I try to sign onto a specific wireless network, the computer recognizes distinc wireless networks but it cannot connect to a specific network, described similarly to the statement [here:]("http://askubuntu.com/questions/233774/ubuntu-12-10-recognizes-wireless-but-does-not-connect-intel-centrino-n-1000?rq=1")

I can see my home network but cannot connect to it, it says connecting then the popup says "disconnected, you are now offline



I've followed the Wireless connection tutorial found [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

In which I've added pci = noapci to my GNU2  boot

I've checked the supported drivers page and it says that this wireless card is supported on ubuntu

I've followed [this]("https://help.ubuntu.com/community/WifiDocs/Device/DWA-552") tutorial with installing the driver with ndiswrapper

I've tried turning off and on my security both from nothing, to wep, to wpa2. 

i cannot sudo apt-get update because i lack an internet connection, everything else i've been usb'ing over to the newly built computer. 


Have I overlooked something? 

Thank you so much!

---

