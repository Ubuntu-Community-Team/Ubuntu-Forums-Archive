---
title: "Enabling and using wireless nic (Linksys WMP110)"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by Jabop on 2008-12-21
I have a fresh install of 8.10 on this machine and I'm trying to use my Linksys WMP110 wireless card. I've searched google, and this forum, to no avail. Similar problems do exist with this card, but the solutions provided have not helped my problem.

Could anyone get me on the right path to use my wireless card? If you need anymore information, just let me know and I'll be happy to provide. 

Here is some commonly sought output for this problem:

```
jacob@jacob-home:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
02:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8052 PCI-E ASF Gigabit Ethernet Controller (rev 22)
06:00.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
06:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

```

```
jacob@jacob-home:~$ sudo lshw -C Network
  *-network DISABLED      
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 22
       serial: 00:01:29:a2:94:60
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: 88E8052 PCI-E ASF Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 22
       serial: 00:01:29:a2:94:3d
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=1GB/s
  *-network UNCLAIMED
       description: Network controller
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:90:7f:ff:54:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```
jacob@jacob-home:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

```
jacob@jacob-home:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

```

Thanks in advance,
Jacob

---

### Post by martunes13 on 2008-12-23
Hi Jabop,

I have exactly the same card.  I installed ndiswrapper and used the windows XP drivers.  If you can connect thru wired internet, go to synaptic package manager. Search for ndisgtk, this is the gui for ndiswrapper.  When you choose ndisgtk, it'll also install ndiswrapper.  Go to system -> administration -> wireless drivers.  Then install the XP driver.  You can find the XP driver in the windows driver cd. Make sure you're using the XP driver.  Load net5416.inf in ndisgtk. This should install the driver.  Reboot your computer and you'll have working wireless.

---

