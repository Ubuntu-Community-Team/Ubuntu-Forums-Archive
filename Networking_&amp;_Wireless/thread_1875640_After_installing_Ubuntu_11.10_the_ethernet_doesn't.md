---
title: "After installing Ubuntu 11.10 the ethernet doesn't work"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by TylerPizz on 2011-11-05
I upgraded to Ubuntu 11.10 and tried to use my ethernet connection any it no longer works, which wouldnt be a big issue if my wireless also didn't work. 

I have a Dell Inspiron 1521 and I would love to get atleast one of the drivers working so I can use my internet. 

Any suggestions? In other forums I've noticed people asking for this information if it helps. 

                                 ifconfig  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 root@Blueberry:/home/logan# /etc/network/interfaces  
 bash: /etc/network/interfaces: Permission denied  
 

root@Blueberry:/home/logan# /etc/resolv.conf  
 bash: /etc/resolv.conf: Permission denied  
 

root@Blueberry:/home/logan# lshw  
 blueberry                  
     description: Portable Computer  
     width: 32 bits  
     capabilities: smbios-2.4 dmi-2.4  
     configuration: boot=normal chassis=portable uuid=44454C4C-4600-1043-8034-B5C04F384631  
   *-core  
        description: Motherboard  
        product: 0KY766  
        vendor: Winbond Electronics  
        physical id: 0  
        serial: .5FC48F1.CN4864379F2608. 
      *-firmware  
           description: BIOS  
           vendor: Winbond Electronics  
           physical id: 0  
           version: A06  
           date: 02/03/2008  
           size: 64KiB  
           capacity: 960KiB  
           capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot  
      *-cpu  
           description: CPU  
           product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 400  
           bus info: cpu@0  
           version: 15.8.1  
           slot: Microprocessor  
           size: 800MHz  
           capacity: 1800MHz  
           width: 64 bits  
           clock: 100MHz  
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq  
           configuration: cores=2 enabledcores=2 threads=2  
         *-cache:0  
              description: L1 cache  
              physical id: 700  
              size: 128KiB  
              capacity: 128KiB  
              capabilities: internal write-back data  
         *-cache:1  
              description: L2 cache  
              physical id: 701  
              size: 256KiB  
              capacity: 512KiB  
              clock: 66MHz (15.0ns)  
              capabilities: pipeline-burst internal varies unified  
      *-memory  
           description: System Memory  
           physical id: 1000  
           slot: System board or motherboard  
           size: 2GiB  
         *-bank:0  
              description: DIMM DDR Synchronous 667 MHz (1.5 ns)  
              product: V916765G24QCFW-F5 
              vendor: ProMOS/Mosel Vitelic  
              physical id: 0  
              serial: B8A92C83  
              slot: DIMM_A  
              size: 1GiB  
              width: 64 bits  
              clock: 667MHz (1.5ns)  
         *-bank:1  
              description: DIMM DDR Synchronous 667 MHz (1.5 ns)  
              product: V916765G24QCFW-F5 
              vendor: ProMOS/Mosel Vitelic  
              physical id: 1  
              serial: BEA92C8D  
              slot: DIMM_B  
              size: 1GiB  
              width: 64 bits  
              clock: 667MHz (1.5ns)  
      *-pci:0  
           description: Host bridge  
           product: RS690 Host Bridge  
           vendor: ATI Technologies Inc  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 00  
           width: 32 bits  
           clock: 66MHz  
           configuration: latency=64  
         *-pci:0  
              description: PCI bridge  
              product: RS690 PCI to PCI Bridge (Internal gfx)  
              vendor: ATI Technologies Inc  
              physical id: 1  
              bus info: pci@0000:00:01.0 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pci ht normal_decode bus_master cap_list  
              resources: ioport:e000(size=4096) memory:fe900000-feafffff ioport:e0000000(size=268435456)  
            *-display  
                 description: VGA compatible controller  
                 product: RS690M [Radeon X1200 Series]  
                 vendor: ATI Technologies Inc  
                 physical id: 5  
                 bus info: pci@0000:01:05.0  
                 version: 00  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi vga_controller bus_master cap_list rom  
                 configuration: driver=radeon latency=64  
                 resources: irq:19 memory:e0000000-efffffff memory:fe9f0000-fe9fffff ioport:ee00(size=256) memory:fea00000-feafffff  
         *-pci:1  
              description: PCI bridge  
              product: RS690 PCI to PCI Bridge (PCI Express Port 2)  
              vendor: ATI Technologies Inc  
              physical id: 6  
              bus info: pci@0000:00:06.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:40 memory:fe800000-fe8fffff  
            *-network UNCLAIMED  
                 description: Network controller  
                 product: BCM4311 802.11b/g WLAN  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:0b:00.0  
                 version: 01  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress bus_master cap_list  
                 configuration: latency=0  
                 resources: memory:fe8fc000-fe8fffff  
         *-pci:2  
              description: PCI bridge  
              product: RS690 PCI to PCI Bridge (PCI Express Port 3)  
              vendor: ATI Technologies Inc  
              physical id: 7  
              bus info: pci@0000:00:07.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:41 ioport:d000(size=4096) memory:fe600000-fe7fffff ioport:f0000000(size=2097152)  
         *-storage  
              description: SATA controller  
              product: SB600 Non-Raid-5 SATA  
              vendor: ATI Technologies Inc  
              physical id: 12  
              bus info: pci@0000:00:12.0 
              logical name: scsi0  
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: storage pm ahci_1.0 bus_master cap_list emulated  
              configuration: driver=ahci latency=64  
              resources: irq:22 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=16) memory:80000000-800003ff  
            *-disk  
                 description: ATA Disk  
                 product: WDC WD1200BEVS-7  
                 vendor: Western Digital 
                 physical id: 0.0.0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/sda  
                 version: 01.0  
                 serial: WD-WXEX07513553 
                 size: 111GiB (120GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=0008c912  
               *-volume:0  
                    description: EXT4 volume  
                    vendor: Linux  
                    physical id: 1  
                    bus info: scsi@0:0.0.0,1  
                    logical name: /dev/sda1  
                    logical name: /  
                    version: 1.0  
                    serial: 37bb52fb-3c29-4eb9-aed8-0fdc91b67244  
                    size: 109GiB  
                    capacity: 109GiB  
                    capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized  
                    configuration: created=2011-05-19 19:22:31 filesystem=ext4 lastmountpoint=/ modified=2011-08-15 01:52:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered mounted=2011-11-05 03:13:44 state=mounted  
               *-volume:1  
                    description: Extended partition  
                    physical id: 2  
                    bus info: scsi@0:0.0.0,2  
                    logical name: /dev/sda2  
                    size: 1916MiB  
                    capacity: 1916MiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 1916MiB 
                       capabilities: nofs  
         *-usb:0  
              description: USB Controller  
              product: SB600 USB (OHCI0) 
              vendor: ATI Technologies Inc  
              physical id: 13  
              bus info: pci@0000:00:13.0 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:16 memory:ffb00000-ffb00fff  
         *-usb:1  
              description: USB Controller  
              product: SB600 USB (OHCI1) 
              vendor: ATI Technologies Inc  
              physical id: 13.1  
              bus info: pci@0000:00:13.1 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:17 memory:ffb01000-ffb01fff  
         *-usb:2  
              description: USB Controller  
              product: SB600 USB (OHCI2) 
              vendor: ATI Technologies Inc  
              physical id: 13.2  
              bus info: pci@0000:00:13.2 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:ffb02000-ffb02fff  
         *-usb:3  
              description: USB Controller  
              product: SB600 USB (OHCI3) 
              vendor: ATI Technologies Inc  
              physical id: 13.3  
              bus info: pci@0000:00:13.3 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:17 memory:ffb03000-ffb03fff  
         *-usb:4  
              description: USB Controller  
              product: SB600 USB (OHCI4) 
              vendor: ATI Technologies Inc  
              physical id: 13.4  
              bus info: pci@0000:00:13.4 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:ffb04000-ffb04fff  
         *-usb:5  
              description: USB Controller  
              product: SB600 USB Controller (EHCI)  
              vendor: ATI Technologies Inc  
              physical id: 13.5  
              bus info: pci@0000:00:13.5 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:20 memory:ffa80000-ffa800ff  
         *-serial  
              description: SMBus  
              product: SBx00 SMBus Controller  
              vendor: ATI Technologies Inc  
              physical id: 14  
              bus info: pci@0000:00:14.0 
              version: 14  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ht cap_list  
              configuration: driver=piix4_smbus latency=0  
              resources: irq:0 ioport:10c0(size=16)  
         *-ide  
              description: IDE interface 
              product: SB600 IDE  
              vendor: ATI Technologies Inc  
              physical id: 14.1  
              bus info: pci@0000:00:14.1 
              logical name: scsi4  
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ide bus_master emulated  
              configuration: driver=pata_atiixp latency=64  
              resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16)  
            *-cdrom  
                 description: DVD reader 
                 product: CDRWDVD TSL462D  
                 vendor: TSSTcorp  
                 physical id: 0.0.0  
                 bus info: scsi@4:0.0.0  
                 logical name: /dev/cdrom1  
                 logical name: /dev/cdrw1  
                 logical name: /dev/dvd1 
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 version: DE07  
                 capabilities: removable audio cd-r cd-rw dvd  
                 configuration: ansiversion=5 status=nodisc  
         *-multimedia  
              description: Audio device  
              product: SBx00 Azalia (Intel HDA)  
              vendor: ATI Technologies Inc  
              physical id: 14.2  
              bus info: pci@0000:00:14.2 
              version: 00  
              width: 64 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=HDA Intel latency=64  
              resources: irq:16 memory:febfc000-febfffff  
         *-isa  
              description: ISA bridge  
              product: SB600 PCI to LPC Bridge  
              vendor: ATI Technologies Inc  
              physical id: 14.3  
              bus info: pci@0000:00:14.3 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: isa bus_master  
              configuration: latency=0  
         *-pci:3  
              description: PCI bridge  
              product: SBx00 PCI to PCI Bridge  
              vendor: ATI Technologies Inc  
              physical id: 14.4  
              bus info: pci@0000:00:14.4 
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pci subtractive_decode bus_master  
              resources: memory:fe500000-fe5fffff  
            *-network UNCLAIMED  
                 description: Ethernet controller  
                 product: BCM4401-B0 100Base-TX  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:03:00.0  
                 version: 02  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm bus_master cap_list  
                 configuration: latency=64  
                 resources: memory:fe5fe000-fe5fffff  
            *-firewire  
                 description: FireWire (IEEE 1394)  
                 product: R5C832 IEEE 1394 Controller  
                 vendor: Ricoh Co Ltd  
                 physical id: 1  
                 bus info: pci@0000:03:01.0  
                 version: 05  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm ohci bus_master cap_list  
                 configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2  
                 resources: irq:23 memory:fe5fd800-fe5fdfff  
            *-generic:0  
                 description: SD Host controller  
                 product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter  
                 vendor: Ricoh Co Ltd  
                 physical id: 1.1  
                 bus info: pci@0000:03:01.1  
                 version: 22  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm bus_master cap_list  
                 configuration: driver=sdhci-pci latency=64  
                 resources: irq:20 memory:fe5fd500-fe5fd5ff  
            *-generic:1 UNCLAIMED  
                 description: System peripheral  
                 product: R5C592 Memory Stick Bus Host Adapter  
                 vendor: Ricoh Co Ltd  
                 physical id: 1.2  
                 bus info: pci@0000:03:01.2  
                 version: 12  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm bus_master cap_list  
                 configuration: latency=64  
                 resources: memory:fe5fd600-fe5fd6ff  
            *-generic:2  
                 description: System peripheral  
                 product: xD-Picture Card Controller  
                 vendor: Ricoh Co Ltd  
                 physical id: 1.3  
                 bus info: pci@0000:03:01.3  
                 version: 12  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: pm bus_master cap_list  
                 configuration: driver=r852 latency=64  
                 resources: irq:20 memory:fe5fd700-fe5fd7ff  
      *-pci:1  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 101  
           bus info: pci@0000:00:18.0  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:2  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] Address Map  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 102  
           bus info: pci@0000:00:18.1  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:3  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] DRAM Controller  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 103  
           bus info: pci@0000:00:18.2  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:4  
           description: Host bridge  
           product: K8 [Athlon64/Opteron] Miscellaneous Control  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 104  
           bus info: pci@0000:00:18.3  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=k8temp  
           resources: irq:0  
   *-battery  
        product: DELL TM98779  
        vendor: SMP  
        physical id: 1  
        slot: Sys. Battery Bay  
        capacity: 78000mWh  
        configuration: voltage=11.1V  
 root@Blueberry:/home/logan#

---

