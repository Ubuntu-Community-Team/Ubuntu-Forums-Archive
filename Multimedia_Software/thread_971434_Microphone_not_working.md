---
title: "Microphone not working"
date: 2008-11-05
forum: Multimedia Software
---

### Post by MajinSaha on 2008-11-05
Hi all !
I have troubles with making my microphone work on my Toshiba laptop, AMD64.
I can hear my voice clearly in Vista, but in Ubuntu ( Hardy ) it's just quiet ! I tried both in Sound Recorder and in Skype. The last one is the reason why I need sound recording. What should I do ?
Thanks.

---

### Post by alwayshere on 2008-11-05
go to sound icon at top bar and duouble click it 
then click prefrences and mark capture and adjust volume to full .
all should be good now 
hey Audacity is  real good for sound recording etc find it in add and remove

---

### Post by MajinSaha on 2008-11-07
I tried that before and after your post. It doesn't help.:( If you want information on my computer and system, I can provide.

---

### Post by MajinSaha on 2008-11-10
Hello !?

---

### Post by loell on 2008-11-10
i suspect that this is a intel audio..

to be sure can you give your system info?

```
sudo lshw
```

post it here..

---

### Post by MajinSaha on 2008-11-10
That's too much of an output. Hope it's ok to post this whole thing.

    description: Computer
    product: Satellite M305D
    vendor: TOSHIBA
    version: PSMDYU-00C005
    serial: 78180036W
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific cpus=1 uuid=80437845-38BD-DC11-9E87-001E68A052E7
  *-core
       description: Motherboard
       product: Satellite M305D
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: 78180036W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.50 (06/13/2008)
          size: 109KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb ieee1394boot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-70
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.3.1
          slot: Socket M2/S1G1
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: S1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: S2
             size: 2GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: Toshiba America Info Systems
             vendor: Toshiba America Info Systems
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS780MC [Radeon HD 3100 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Marvell Technology Group Ltd.
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 12
                serial: 00:1e:68:a0:52:e7
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Advanced Micro Devices [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 5)
             vendor: Advanced Micro Devices [AMD]
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR5418 802.11abgn Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wifi0
                version: 01
                serial: 00:21:63:2b:69:f1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.142 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: TOSHIBA MK2552GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LV01
                serial: 68TDP1X3T
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0c120c11
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 900f-3fa5
                   size: 1498MiB
                   capacity: 1500MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-05-30 17:49:38 filesystem=ntfs label=TOSHIBA SYSTEM VOLUME state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /host
                   logical name: /boot
                   version: 3.1
                   serial: f22f4c16-9553-e947-8546-f4febe997019
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-05-30 17:50:55 filesystem=ntfs label=SQ004740V04 mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB700/SB800 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB700/SB800 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: TSSTcorp CDDVDW TS-L633P
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   logical name: /media/cdrom0
                   version: TO01
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/hda
                      logical name: /media/cdrom0
                      configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 1
                bus info: pci@0000:09:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 module=ohci1394
           *-system
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.2
                bus info: pci@0000:09:01.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 1.3
                bus info: pci@0000:09:01.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=64
     *-pci:1
          description: Host bridge
          product: Family 11h HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 11h DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 11h Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by loell on 2008-11-11
you're using the snd_hda_intel driver.

is this on intrepid?

---

### Post by MajinSaha on 2008-11-11
I'm not sure what you mean by interpid and how to check it. Can you please explain ?

---

### Post by sirebral on 2008-11-11
It might be the simple route.

Double Click on your Sound icon in your panel, check you Recording tabs, and make sure your volume is set high enough.

---

### Post by MajinSaha on 2008-11-13
This solution was given before and it's not working.

---

