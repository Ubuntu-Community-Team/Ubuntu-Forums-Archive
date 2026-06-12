---
title: "Wireless not working on Ubuntu 8.10"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by nepošten on 2009-02-19
Ok, first of all, I'm new to this forum, so I hardly know a thing about rules, so I apologise in advance.

I have a computer, with a dual boot. One is Windows xp sp3 and other is ubuntu 8.10. I have no physical connection to internet, just wireless connection. In windows the connection works fine, no comments, but when I installed Ubuntu I noticed, that my password automatically changes. When I input my password, the system is trying to log me in, but then, the windows pops out, asking whether I want to connect again or to cancel. But the password is not the same as I put it in, no, it is a looong password and I really don't know what to do. I have tried with iwconfig and sudo dhclient wlan0, but those things doesn't help me a thing. I don't know, is it a problem, that I use letters, that aren't English (like &#269;, &#382;, &#353;) or what? But those letters work fine with windows xp and I have a Slovenian language in Ubuntu. So if it works by loging into ubuntu, why not by loging into the net? I really don't know what to do, and after 2 days of har searching, I have decided to ask some professional ubuntu users for advice.

Regards, nepo&#353;ten

EDIT: Oh yeah, and i have a router and an access point for wireless.

---

### Post by Adam Yee on 2009-02-19
I pretty much have the same thing going on.  It happened about 3 days ago when Ubuntu automatic updates were found (7 total, 2 security, 5 recommended).  The next day, wireless couldn't connect.  Very frustrating.  No idea how to reset, refresh, yata yata.  I a new user to Ubuntu.  Intrepid is the first distribution I've used.

I connected via wired eth0 and installed the updates, but still no ability to connect via wireless wlan0.

My router network configuration seems correct, I haven't changed anything from when it was working before.  WEP key entered correctly.  Set to connect automatic DHCP.  While trying to connect, the network connection figure next to the volume speaker shows a green ball (me) and a grey ball (router).  I suppose this means my laptop isn't correctly asking for an address to connect to the network.

Obviously, it's not a hardware issue since I too have XP on dual boot and it can connect via wireless just fine.  Could it be a driver malfunction with kernel 2.6.27-11?  Did the updates mess up the network config or other somehow?

I'm not sure what info is needed to troubleshoot this issue, but I'm sure I can post it if asked.  Thank you everyone.

---

### Post by incubii on 2009-02-19
Hi guys, i had a similar issue with my Toshiba laptop. Windows would work great and Ubuntu worked great in 8.04, but going to 8.10 broke many things.

My solution was first to update the laptop to make sure everything was spankin new, but to also install [Wicd](http://wicd.sourceforge.net/) as the network manager instead of Gnome Network Manager.

Wicd i just so much better at connecting to wireless networks for me. It remembers all my settings and has more settings to change as well!

You should give it a shot

---

### Post by nepošten on 2009-02-20
Well, I would try it, but I'm not handy with ubuntu, so I followed the instructions, and typed "deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras" in softwarfe sources, third-party software, but an error occurs and i cannot find the wicd file...

If it would help you anything, here is my chipset
  *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2
          slot: Socket 775
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1 DISABLED
             description: L2 cache
             physical id: a
             slot: External Cache
             capabilities: synchronous external write-back
     *-cache:0
          description: L1 cache
          physical id: 9
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back
     *-cache:1 DISABLED
          description: L2 cache
          physical id: b
          slot: External Cache
          capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
     *-pci:0
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-system UNCLAIMED
             description: PIC
             product: P4M890 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: GeForce 7650 GS
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-pci:2
             description: PCI bridge
             product: P4M890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-disk
                description: ATA Disk
                product: ST3320820AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9QF2ZK4M
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8a93eb8c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: ca22a262-b360-7d41-aedb-30155c5f9270
                   size: 278GiB
                   capacity: 278GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-07 21:59:01 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 20GiB
                   capacity: 20GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: W95 FAT32 partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 20GiB
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRAM GSA-H42L
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM GDR8164B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 0U08
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 91
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8251 PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:19:db:5d:35:cd
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.180 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: VT8251 Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master
           *-pci:0
                description: PCI bridge
                product: VT8251 PCIE Root Port
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pci pciexpress pm msi ht bus_master cap_list
                configuration: driver=pcieport-driver
                resources: iomemory:90900-908ff
           *-pci:1
                description: PCI bridge
                product: VT8251 PCIE Root Port
                vendor: VIA Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pci pciexpress pm msi ht bus_master cap_list
                configuration: driver=pcieport-driver
                resources: iomemory:80800-807ff
           *-multimedia
                description: Audio device
                product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:4
             description: PCI bridge
             product: VT8251 PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master
           *-multimedia
                description: Multimedia controller
                product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 9
                bus info: pci@0000:07:09.0
                version: d1
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: c
                bus info: pci@0000:07:0c.0
                version: c0
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
     *-pci:1
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: P4M890 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: P4M890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-scsi
          physical id: 1
          bus info: usb@5:1.1
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: Flash HS-CF
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             version: 4.44
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: Flash HS-MS/SD
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@5:0.0.1
             logical name: /dev/sdc
             version: 4.44
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: Flash HS-SM
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@5:0.0.2
             logical name: /dev/sdd
             version: 4.44
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:2a:28:d9:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:bc:ff:a8:98:c1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 3
       logical name: vnet0
       serial: 9e:7d:ea:df:2f:55
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes

I'm using TRENDnet TEW-637AP access point and BARICADE SMC 7004VBR router.


Sorry for 2nd edit, but I found this code, so I decided to paste this too.
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated  
          Bit Rate:9 Mb/s   Tx-Power=17 dBm  
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B  
          Power Management: off
          Link Quality=44/100  Signal level:-32 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

