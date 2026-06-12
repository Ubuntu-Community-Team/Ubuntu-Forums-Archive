---
title: "Zoom 5001 PCI Cable Modem"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by LinGNUbie on 2012-05-30
I have a Zoom 5001 PCI Cable Modem that I am trying to get working correctly with Ubuntu 10.04.4 LTS (Server). It is currently working only partially with the tulip module as it is seen as a Conexant Lanfinity HCF Modem, so I am trying to port the old proprietary driver (Available at Zoom's [5001 Driver Page]("www.zoomtel.com/techsupport/cable/pci5001.shtml").), however the makefile is incorrect for modern ubuntu systems. I say only partially working  because (using the default tulip driver) it will connect and configure via dhcp, and traffic flows for only a few seconds, then the card seems to lose the connection and proceeds to renegotiate or resets itself.

a) Please bear in mind that my connection is spotty until I get this resolved!

b) Does anyone have this card working with a current release?

c) Is it possible to update the makefile so it will compile and install the module(s) on a current system?

d) Can anyone assist me or point me in the right direction with the creation of the driver on a current release from the original source?

Relevant Data:

Ubuntu 10.04.4 LTS
Kernel 2.6.32-41-generic-pae

PCI ID 0x14f1:0x1803

lshw
        *-network:0
             description: Ethernet interface
             product: HCF 56k Modem
             vendor: Conexant Systems, Inc.
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: eth0
             version: 08
             serial: 00:40:36:0a:39:e1
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=(Sorry MASKED) latency=160 maxlatency=40 mingnt=20 multicast=yes
             resources: irq:16 ioport:1800(size=256) memory:e8000000-e8003fff

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Ethernet controller: Conexant Systems, Inc. HCF 56k Modem (rev 08)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)

---

