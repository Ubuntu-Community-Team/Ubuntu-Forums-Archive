---
title: "ethernet in ubuntu 8.10"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by gianni8.10 on 2008-12-24
Hi, I've got a problem with my internet configuration, it is set exactly as in xp but it doesn't work.

When I surf in firefox, I am able to go only to some websites (albeit very slowly), for example mozilla.com, amazon.com, yahoo.com, but all the others don't work. Also going to ther router address doesn't work (192.168.1.1). Ping works with some websites.

thanks for the help

Here is the output of various commands.

the configuration is
ip 192.168.1.6
gateway 192.168.1.1
subnet 255.255.255.0

lshw -C network +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth1
       version: 10
       serial: 00:50:fc:fe:da:5d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.6 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:7c:d1:c7:94:f1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



lspci +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7100 GS (rev a1)


nm-tool +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:16:17:72:CD:7C

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes

  Wired Settings


- Device: eth1 ----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:50:FC:FE:DA:5D

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             212.216.172.62
    DNS:             212.216.112.112

---

### Post by 2hot6ft2 on 2008-12-24
Have you tried unplugging the router for at least 15 seconds and plugging it back in? Try bypassing the router and go straight to the modem, if it works properly that way then you know the problem is in the router. You'll need to restart the network. I would shut the pc down and switch the cables that way you don't get a spark of any kind and the pc will get a new ip address when you start it back up from the modem.

---

### Post by zeronothing on 2008-12-24
I was looking at your configuration and saw that your DNS is:

DNS: 212.216.172.62
DNS: 212.216.112.112

This is interesting because on your machine it would normally be the IP address of your router because your router is also technically a DNS server as well. I suppose not all routers would do this but most I believe do. so try changing your DNS to your routers IP address like:

192.168.1.1

Technically the DNS servers you mentioned in your post should work but try changing it to the routers IP address. this I would hope explain the problem your have trying to reach your routers web frontend. the DNS server you have configured probably doesnt know how to resolve the 192.168.1.1 address. hope this helps

---

### Post by gianni8.10 on 2008-12-24
Hi, thank you for your answers.
The modem is integrated in my router, anyway I've tried to shut it down and restart.

---

### Post by gianni8.10 on 2008-12-24
I've tried all the different dns configurations you suggested but it didn't work

Thanks anyway.
Other suggestions?

---

### Post by zeronothing on 2008-12-24
this is how one of my desktops is configured to work:

IP address: 192.168.0.5
subnet: 255.255.255.0
gateway: 192.168.0.1

DNS: 192.168.0.1


this is how I have my ubuntu machine configured. I like to give some machines at my house static IP address for different services.

---

