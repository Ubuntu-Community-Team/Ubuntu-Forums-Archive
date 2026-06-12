---
title: "new wireless card install"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by acutshall1 on 2009-08-11
New to U; I have a gig lan card that works fine however I bought a new netgear wg311 pci wireless card that was on the wiki recommended list by HJ Heins. Installed and went to synaptic  and loaded what I thought was the package for the card (madwifi). I set up the SSID etc however the card does not work; I tried un plugging the lan card to see if the wireless would kick in however it does not. I only get notification when I plug the lan card in.

I downloaded what I thought was a package from Madwifi however it turned out to be the files for the card; I am not familiar or savy enough with Linux to do a manaul intsall. Can I use this files to create a package with synaptic. 

thx :confused:

---

### Post by The Toxic Mite on 2009-08-11
Hey!

Can you go to Applications > Accessories > Terminal, and type in the following commands?:

```

sudo lshw -c network
lspci
iwconfig
ifconfig

```

Thanks :)

---

### Post by acutshall1 on 2009-08-11
> **The Toxic Mite said:**
> Hey!

Can you go to Applications > Accessories > Terminal, and type in the following commands?:

```

sudo lshw -c network
lspci
iwconfig
ifconfig

```Thanks :)


yes will try this evening when i return home. thx!

---

### Post by The Toxic Mite on 2009-08-11
> **acutshall1 said:**
> yes will try this evening when i return home. thx!

Ok :D

---

### Post by acutshall1 on 2009-08-11
> **The Toxic Mite said:**
> Hey!

Can you go to Applications > Accessories > Terminal, and type in the following commands?:

```

sudo lshw -c network
lspci
iwconfig
ifconfig

```Thanks :)

Here srae the results


*-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:d8:8e:db:cf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.1.10 latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:03:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:df:69:52:c2:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



thx!

---

### Post by acutshall1 on 2009-08-11
> **The Toxic Mite said:**
> Hey!

Can you go to Applications > Accessories > Terminal, and type in the following commands?:

```

sudo lshw -c network
lspci
iwconfig
ifconfig

```Thanks :)

For some reason I am getting more info when I run the same command, nt sure what changed. Anyone have any suggestions.

 *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:d8:8e:db:cf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.1.10 latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:03:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:f3:87:86:be:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
acutshall@mediabox1:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
03:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
acutshall@mediabox1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by acutshall1 on 2009-08-12
after 2 days of  *%^$%#  :twisted: with it I finally gave up, went down and bought a linksys wmp54g. I  installed it , booted up and presto! the OS found it and it works. here are the results

*-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:d8:8e:db:cf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A latency=0 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:03:0a.0
       logical name: wmaster0
       version: 01
       serial: 00:23:69:d8:d0:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.9 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:1e:e9:4f:2e:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

happy ending till next time :biggrin:

---

### Post by acutshall1 on 2009-08-12
:(  spoke too soon; network keeps disconnecting and asking me to re-authenticate....anyone know a fix?
thx

---

