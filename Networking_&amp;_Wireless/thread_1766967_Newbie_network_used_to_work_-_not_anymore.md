---
title: "Newbie: network used to work - not anymore"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by sgouros on 2011-05-25
Hello from a linux newbie
   
  After  trying to setup my network for the 10th time I give up. (It used to work pretty well with my static IP but after a change to a DHCP router and back to the static router, nothing works). Note that I have no network problems when I dual boot to windows with my static ip settings.
   
  Could anybody help me?
   
     
  Many thanks in advance
   
   
  My system:
   
   
   
  ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:1d:92:21:39:ec  
            inet addr:10.133.4.208  Bcast:10.133.4.223  Mask:255.255.255.224
            inet6 addr: fe80::21d:92ff:fe21:39ec/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:1740 errors:0 dropped:0 overruns:0 frame:0
            TX packets:553 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:150456 (150.4 KB)  TX bytes:33677 (33.6 KB)
            Interrupt:43 Base address:0xa000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:310 errors:0 dropped:0 overruns:0 frame:0
            TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:29178 (29.1 KB)  TX bytes:29178 (29.1 KB)
   
   
  iwconfig
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  vboxnet0  no wireless extensions.
   
   
   
  iwlist scan
  lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  vboxnet0  Interface doesn't support scanning.
   
   
   
  sudo /etc/init.d/networking restart
  * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                           [ OK ]
   
   
  route
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  10.133.4.192    *               255.255.255.224 U     1      0        0 eth0
  link-local      *               255.255.0.0     U     1000   0        0 eth0
  sudo default         10.133.4.193    0.0.0.0         UG    0      0        0 eth0
   
   
   
  sudo gedit /etc/network/interfaces
  auto lo
  iface lo inet loopback
   
   
  sudo lspci
  00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
  00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
  00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
  00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
  00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
  00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
  00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
  00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
  00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
  00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface  Bridge (rev 01)
  00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
  00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
  00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
  01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
  03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
   
   
  sudo lshw
  sgouroslinux              
      description: Desktop Computer
      product: MS-7379
      vendor: MICRO-STAR INTERNATIONAL CO.,LTD
      version: 2.0
      serial: To Be Filled By O.E.M.
      width: 64 bits
      capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
      configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-001D922139EC
    *-core
         description: Motherboard
         product: MS-7379
         vendor: MICRO-STAR INTERNATIONAL CO.,LTD
         physical id: 0
         version: 2.0
         serial: To be filled by O.E.M.
         slot: To Be Filled By O.E.M.
       *-firmware
            description: BIOS
            vendor: American Megatrends Inc.
            physical id: 0
            version: V7.1 (08/08/2007)
            size: 64KiB
            capacity: 448KiB
            capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
       *-cpu
            description: CPU
            product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
            vendor: Intel Corp.
            physical id: 4
            bus info: cpu@0
            version: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
            serial: To Be Filled By O.E.M.
            slot: CPU 1
            size: 1869MHz
            width: 64 bits
            clock: 267MHz
            capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
          *-cache:0
               description: L1 cache
               physical id: 5
               slot: L1-Cache
               size: 64KiB
               capacity: 64KiB
               capabilities: internal write-back data
          *-cache:1
               description: L2 cache
               physical id: 6
               slot: L2-Cache
               size: 2MiB
               capacity: 2MiB
               capabilities: internal write-back instruction
       *-memory
            description: System Memory
            physical id: a
            slot: System board or motherboard
            size: 1GiB
          *-bank:0
               description: DIMM SDRAM Synchronous
               product: PartNum0
               vendor: Manufacturer0
               physical id: 0
               serial: SerNum0
               slot: DIMM0
               size: 1GiB
               width: 64 bits
          *-bank:1
               description: DIMM [empty]
               product: PartNum1
               vendor: Manufacturer1
               physical id: 1
               serial: SerNum1
               slot: DIMM1
       *-pci
            description: Host bridge
            product: 82G33/G31/P35/P31 Express DRAM Controller
            vendor: Intel Corporation
            physical id: 100
            bus info: pci@0000:00:00.0
            version: 02
            width: 32 bits
            clock: 33MHz
          *-pci:0
               description: PCI bridge
               product: 82G33/G31/P35/P31 Express PCI Express Root Port
               vendor: Intel Corporation
               physical id: 1
               bus info: pci@0000:00:01.0
               version: 02
               width: 32 bits
               clock: 33MHz
               capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
               configuration: driver=pcieport
               resources: irq:40 memory:fc000000-feafffff ioport:d0000000(size=268435456)
             *-display
                  description: VGA compatible controller
                  product: NV44 [GeForce 6200 TurboCache(TM)]
                  vendor: nVidia Corporation
                  physical id: 0
                  bus info: pci@0000:01:00.0
                  version: a1
                  width: 64 bits
                  clock: 33MHz
                  capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                  configuration: driver=nvidia latency=0
                  resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:feae0000-feafffff
          *-multimedia
               description: Audio device
               product: N10/ICH 7 Family High Definition Audio Controller
               vendor: Intel Corporation
               physical id: 1b
               bus info: pci@0000:00:1b.0
               version: 01
               width: 64 bits
               clock: 33MHz
               capabilities: pm msi pciexpress bus_master cap_list
               configuration: driver=HDA Intel latency=0
               resources: irq:44 memory:fbffc000-fbffffff
          *-pci:1
               description: PCI bridge
               product: N10/ICH 7 Family PCI Express Port 1
               vendor: Intel Corporation
               physical id: 1c
               bus info: pci@0000:00:1c.0
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
               configuration: driver=pcieport
               resources: irq:41 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
          *-pci:2
               description: PCI bridge
               product: N10/ICH 7 Family PCI Express Port 3
               vendor: Intel Corporation
               physical id: 1c.2
               bus info: pci@0000:00:1c.2
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
               configuration: driver=pcieport
               resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:40400000(size=2097152)
             *-network
                  description: Ethernet interface
                  product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                  vendor: Realtek Semiconductor Co., Ltd.
                  physical id: 0
                  bus info: pci@0000:03:00.0
                  logical name: eth0
                  version: 01
                  serial: 00:1d:92:21:39:ec
                  size: 100MB/s
                  capacity: 1GB/s
                  width: 64 bits
                  clock: 33MHz
                  capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                  configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.133.4.208 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                  resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff
          *-usb:0
               description: USB Controller
               product: N10/ICH 7 Family USB UHCI Controller #1
               vendor: Intel Corporation
               physical id: 1d
               bus info: pci@0000:00:1d.0
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: uhci bus_master
               configuration: driver=uhci_hcd latency=0
               resources: irq:23 ioport:dc00(size=32)
          *-usb:1
               description: USB Controller
               product: N10/ICH 7 Family USB UHCI Controller #2
               vendor: Intel Corporation
               physical id: 1d.1
               bus info: pci@0000:00:1d.1
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: uhci bus_master
               configuration: driver=uhci_hcd latency=0
               resources: irq:19 ioport:d880(size=32)
          *-usb:2
               description: USB Controller
               product: N10/ICH 7 Family USB UHCI Controller #3
               vendor: Intel Corporation
               physical id: 1d.2
               bus info: pci@0000:00:1d.2
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: uhci bus_master
               configuration: driver=uhci_hcd latency=0
               resources: irq:18 ioport:d800(size=32)
          *-usb:3
               description: USB Controller
               product: N10/ICH 7 Family USB UHCI Controller #4
               vendor: Intel Corporation
               physical id: 1d.3
               bus info: pci@0000:00:1d.3
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: uhci bus_master
               configuration: driver=uhci_hcd latency=0
               resources: irq:16 ioport:d480(size=32)
          *-usb:4
               description: USB Controller
               product: N10/ICH 7 Family USB2 EHCI Controller
               vendor: Intel Corporation
               physical id: 1d.7
               bus info: pci@0000:00:1d.7
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: pm debug ehci bus_master cap_list
               configuration: driver=ehci_hcd latency=0
               resources: irq:23 memory:fbffbc00-fbffbfff
          *-pci:3
               description: PCI bridge
               product: 82801 PCI Bridge
               vendor: Intel Corporation
               physical id: 1e
               bus info: pci@0000:00:1e.0
               version: e1
               width: 32 bits
               clock: 33MHz
               capabilities: pci subtractive_decode bus_master cap_list
          *-isa
               description: ISA bridge
               product: 82801GB/GR (ICH7 Family) LPC Interface  Bridge
               vendor: Intel Corporation
               physical id: 1f
               bus info: pci@0000:00:1f.0
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: isa bus_master cap_list
               configuration: latency=0
          *-ide:0
               description: IDE interface
               product: 82801G (ICH7 Family) IDE Controller
               vendor: Intel Corporation
               physical id: 1f.1
               bus info: pci@0000:00:1f.1
               logical name: scsi0
               version: 01
               width: 32 bits
               clock: 33MHz
               capabilities: ide bus_master emulated
               configuration: driver=ata_piix latency=0
               resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
             *-cdrom
                  description: DVD-RAM writer
                  product: DVDRAM GSA-H10A
                  vendor: HL-DT-ST
                  physical id: 0.0.0
                  bus info: scsi@0:0.0.0
                  logical name: /dev/cdrom
                  logical name: /dev/cdrw
                  logical name: /dev/dvd
                  logical name: /dev/dvdrw
                  logical name: /dev/scd0
                  logical name: /dev/sr0
                  version: JL02
                  capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                  configuration: ansiversion=5 status=nodisc
          *-ide:1
               description: IDE interface
               product: N10/ICH7 Family SATA IDE Controller
               vendor: Intel Corporation
               physical id: 1f.2
               bus info: pci@0000:00:1f.2
               logical name: scsi2
               logical name: scsi3
               version: 01
               width: 32 bits
               clock: 66MHz
               capabilities: ide pm bus_master cap_list emulated
               configuration: driver=ata_piix latency=0
               resources: irq:19 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16)
             *-disk:0
                  description: ATA Disk
                  product: WDC WD2500AAJS-0
                  vendor: Western Digital
                  physical id: 0
                  bus info: scsi@2:0.0.0
                  logical name: /dev/sda
                  version: 01.0
                  serial: WD-WMART0227369
                  size: 232GiB (250GB)
                  capabilities: partitioned partitioned:dos
                  configuration: ansiversion=5 signature=00007e28
                *-volume:0
                     description: Windows NTFS volume
                     physical id: 1
                     bus info: scsi@2:0.0.0,1
                     logical name: /dev/sda1
                     version: 3.1
                     serial: 70b389ea-0373-764f-a6b5-d837dc0f162d
                     size: 64GiB
                     capacity: 64GiB
                     capabilities: primary bootable ntfs initialized
                     configuration: clustersize=4096 created=2007-02-12 11:34:30 filesystem=ntfs label=DISA Win C: state=clean
                *-volume:1
                     description: Windows NTFS volume
                     physical id: 2
                     bus info: scsi@2:0.0.0,2
                     logical name: /dev/sda2
                     version: 3.1
                     serial: 40594eb8-0aba-7543-a0de-8ce172af28fe
                     size: 168GiB
                     capacity: 168GiB
                     capabilities: primary extended partitioned partitioned:extended ntfs initialized
                     configuration: clustersize=4096 created=2008-01-21 15:20:38 filesystem=ntfs label=Backup Linux Files K: state=clean
                   *-logicalvolume
                        description: Linux filesystem partition
                        physical id: 5
                        logical name: /dev/sda5
                        logical name: /Disk1Partition2
                        capacity: 168GiB
                        configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
             *-disk:1
                  description: ATA Disk
                  product: SAMSUNG SP2504C
                  physical id: 1
                  bus info: scsi@2:0.1.0
                  logical name: /dev/sdb
                  version: VT10
                  serial: S09QJ13LC14092
                  size: 232GiB (250GB)
                  capabilities: partitioned partitioned:dos
                  configuration: ansiversion=5 signature=dbfddbfd
                *-volume:0
                     description: Linux swap volume
                     physical id: 1
                     bus info: scsi@2:0.1.0,1
                     logical name: /dev/sdb1
                     version: 1
                     serial: b93141dd-cec2-4bb2-841a-573bdbe780f7
                     size: 1906MiB
                     capacity: 1906MiB
                     capabilities: primary nofs swap initialized
                     configuration: filesystem=swap pagesize=4096
                *-volume:1
                     description: Extended partition
                     physical id: 2
                     bus info: scsi@2:0.1.0,2
                     logical name: /dev/sdb2
                     size: 231GiB
                     capacity: 231GiB
                     capabilities: primary extended partitioned partitioned:extended
                   *-logicalvolume:0
                        description: Linux filesystem partition
                        physical id: 5
                        logical name: /dev/sdb5
                        logical name: /home
                        capacity: 167GiB
                        configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered state=mounted
                   *-logicalvolume:1
                        description: Linux filesystem partition
                        physical id: 6
                        logical name: /dev/sdb6
                        logical name: /
                        capacity: 63GiB
                        configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
             *-disk:2
                  description: ATA Disk
                  product: SAMSUNG HD300LJ
                  physical id: 2
                  bus info: scsi@3:0.0.0
                  logical name: /dev/sdc
                  version: ZT10
                  serial: S0D7J1FL502101
                  size: 279GiB (300GB)
                  capabilities: partitioned partitioned:dos
                  configuration: ansiversion=5 signature=1e721e72
                *-volume
                     description: Windows NTFS volume
                     physical id: 1
                     bus info: scsi@3:0.0.0,1
                     logical name: /dev/sdc1
                     logical name: /media/Disa Files D:_
                     version: 3.1
                     serial: fae97f17-d259-1a4d-8ddb-fbac2b03aab4
                     size: 279GiB
                     capacity: 279GiB
                     capabilities: primary ntfs initialized
                     configuration: clustersize=4096 created=2011-04-05 13:28:10 filesystem=ntfs label=Disa Files D: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
             *-disk:3
                  description: ATA Disk
                  product: SAMSUNG HD300LJ
                  physical id: 3
                  bus info: scsi@3:0.1.0
                  logical name: /dev/sdd
                  version: ZT10
                  serial: S0D7J1CLA17509
                  size: 279GiB (300GB)
                  capabilities: partitioned partitioned:dos
                  configuration: ansiversion=5 signature=0000def6
                *-volume
                     description: EXT4 volume
                     vendor: Linux
                     physical id: 1
                     bus info: scsi@3:0.1.0,1
                     logical name: /dev/sdd1
                     logical name: /Disk4Partition1
                     version: 1.0
                     serial: a816134a-9d7e-4790-9000-56b5950a0a76
                     size: 279GiB
                     capacity: 279GiB
                     capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                     configuration: created=2011-05-04 11:48:41 filesystem=ext4 lastmountpoint=/Disk4Partition1&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;7;&#65533;D&#65533;$&#65533;&#65533;&#65533;&#65533;<&#65533;&#65533;&#65533;&#65533;a&*&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; modified=2011-05-25 08:27:27 mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered mounted=2011-05-25 08:27:27 state=mounted
          *-serial UNCLAIMED
               description: SMBus
               product: N10/ICH 7 Family SMBus Controller
               vendor: Intel Corporation
               physical id: 1f.3
               bus info: pci@0000:00:1f.3
               version: 01
               width: 32 bits
               clock: 33MHz
               configuration: latency=0
               resources: ioport:400(size=32)
    *-network DISABLED
         description: Ethernet interface
         physical id: 1
         logical name: vboxnet0
         serial: 0a:00:27:00:00:00
         capabilities: ethernet physical
         configuration: broadcast=yes multicast=yes

---

