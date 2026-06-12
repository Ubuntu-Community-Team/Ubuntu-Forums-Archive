---
title: "HDMI video and sound is not working corectly"
date: 2011-01-10
forum: Multimedia Software
---

### Post by papaeric on 2011-01-10
Hello! I'm having a hard time with my hdmi output on my HP G60-128CA laptop to my HDTV.
For now I'm getting video only with the Nvidia 173 driver no mater if I'm on 10.04 or  10.10. In the 2 cases, the sound is not passing. Let me add that all the options in sound preferences are available and all the speakers tests i did whit aplay worked ( no error messages), and no muted devices in alsamixer.
In all my web searching one thing is strange to me: i didn't find a lot of problems regarding the hdmi display output whit the latest nvidia driver.
Can anyone help.

---

### Post by BicyclerBoy on 2011-01-10
As I understand.
nvidia 256 is working for most people (hdmi audio).
AFAIK version 173 does not support HD audio.

You also are recommended to use alsa 1.0.23 modules in the kernel build.

I don't have any idea what your video hardware is, do you ?

Do you think you will should have HD audio over HDMI ?
Or do you have S/PDIF digital pass thru' routed over HDMI ?

---

### Post by papaeric on 2011-01-10
Hardware:
```
eric-portable-amd
    description: Notebook
    product: HP G60 Notebook PC
    vendor: Hewlett-Packard
    version: F.54
    serial: 2CE837N2NB
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=0564E3A0-88E1-11DD-BF08-9F4918FBDAEA
  *-core
       description: Motherboard
       product: 303C
       vendor: Wistron
       physical id: 0
       version: 08.60
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.54 (08/18/2009)
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon Dual-Core QL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.3.1
          slot: Socket A
          size: 950MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DRAM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 32 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 5
          bus info: cpu@1
          version: 15.3.1
          size: 950MHz
          capacity: 950MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1a00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:c0080000-c00fffff
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: nVidia Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0006000-c0006fff
     *-usb:1
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:17 memory:c0007000-c00070ff
     *-usb:2
          description: USB Controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0008000-c0008fff
     *-usb:3
          description: USB Controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:16 memory:c0007400-c00074ff
     *-ide:0
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:19 memory:c0000000-c0003fff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
     *-ide:1
          description: IDE interface
          product: MCP78S [GeForce 8200] SATA Controller (non-AHCI mode)
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi3
          logical name: scsi4
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:25 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:c0004000-c0005fff
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW TS-L633L
             vendor: TSSTcorp
             physical id: 0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 0400
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk
             description: ATA Disk
             product: ST9320421ASG
             vendor: Seagate
             physical id: 1
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: SD14
             serial: 5TJ0P78W
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00055540
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: b860-a7d5
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-09-02 18:22:49 filesystem=ntfs label=Réservé au système state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 347920d6-ba04-b34b-890e-10cc33ee2cc1
                size: 153GiB
                capacity: 153GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2010-09-02 18:22:53 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sda3
                size: 142GiB
                capacity: 142GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 54GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 2429MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 85GiB
     *-network
          description: Ethernet interface
          product: MCP77 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1d:72:7b:77:97
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm ht bus_master cap_list
          resources: ioport:4000(size=4096) memory:c1000000-c1ffffff ioport:c4000000(size=469762048)
        *-display
             description: VGA compatible controller
             product: C77 [GeForce 8200M G]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:20 memory:c1000000-c1ffffff memory:d0000000-dfffffff(prefetchable) memory:c4000000-c5ffffff(prefetchable) ioport:4000(size=128) memory:c6000000-c601ffff(prefetchable)
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport
          resources: irq:24 memory:c2000000-c20fffff
        *-network
             description: Wireless interface
             product: AR928X Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:07:00.0
             logical name: wlan0
             version: 01
             serial: 00:23:4d:4b:26:ee
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath9k ip=192.167.1.19 latency=0 multicast=yes wireless=IEEE 802.11abgn
             resources: irq:23 memory:c2000000-c200ffff
     *-pci:3
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 11h [Turion X2, Athlon X2, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: d
          bus info: usb@1:1
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
```

Here is my aplay -l:
**** Liste des PLAYBACK périphériques ****
carte  0: NVidia [HDA NVidia], périphérique 0 : CONEXANT Analog [CONEXANT Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: NVidia [HDA NVidia], périphérique 1 : Conexant Digital [Conexant Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: NVidia [HDA NVidia], périphérique 3 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

---

