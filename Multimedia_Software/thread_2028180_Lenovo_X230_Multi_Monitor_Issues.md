---
title: "Lenovo X230 Multi Monitor Issues"
date: 2012-07-17
forum: Multimedia Software
---

### Post by SJrX on 2012-07-17
I'm having some issues with multiple monitor support on my new Lenovo X230. It is incredibly difficult to get the monitor configuration setup correctly via KRandR.

All of these issues seem to be related to the use of the display port, when I use just VGA and the built in screen it is fine.

First: If I boot up with the display port plugged in, X never starts and I just see a console with:

[drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:7]
[drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:7]
[drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:7]
[drm:drm_crtc_helper_set_config] *ERROR* failed to set mode on [CRTC:7]

Second: When I switch via KRandR to try and get it to work, often times X turns off then never turns back on (with the same messages in console, until I yank the Display Port, then X resumes). 

Other times the screen will switch and think it's completed, but the other monitor is dark.

I can normally switch this by switching the resolution of the new DVI screen to something else and back again, then it will finally come back on.

This is incredibly fragile and annoying, and was hoping to fix it.

I'm running Kubuntu 12.04 x64-bit edition:

Here is the output of lshw:
hilbert                   
    description: Notebook
    product: 2306CTO (LENOVO_MT_2306)
    vendor: LENOVO
    version: ThinkPad X230
    serial: R9PGD5K
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad X230 power-on_password=disabled sku=LENOVO_MT_2306 uuid=811AFBCF-5C52-CB11-83C7-9CB3C8B2AC68
  *-core
       description: Motherboard
       product: 2306CTO
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZM4R2681GB
       slot: Not Available
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3520M CPU @ 2.90GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3520M CPU @ 2.90GHz
          serial: None
          slot: CPU Socket - U3E1
          size: 1200MHz
          capacity: 1200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 3
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 4
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 5
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 2
          slot: L1-Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: CMSX8GX3M1A1600C1
             vendor: AMI
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: CMSX8GX3M1A1600C1
             vendor: AMI
             physical id: 1
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: e
          version: G2ET31WW (1.11 )
          date: 05/24/2012
          size: 128KiB
          capacity: 11MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Ivy Bridge Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:43 memory:f2520000-f252ffff
        *-communication:0
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:46 memory:f2535000-f253500f
        *-communication:1
             description: Serial controller
             product: Panther Point KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:50b0(size=8) memory:f253c000-f253cfff
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: 3c:97:0e:03:42:e0
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-3 ip=142.103.225.54 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:44 memory:f2500000-f251ffff memory:f253b000-f253bfff ioport:5080(size=32)
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f253a000-f253a3ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f2530000-f2533fff
        *-pci:0
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:f1d00000-f24fffff ioport:f0400000(size=8388608)
           *-generic
                description: System peripheral
                product: MMC/SD Host Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f1d00000-f1d000ff
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f1c00000-f1cfffff
           *-network DISABLED
                description: Wireless interface
                product: Centrino Advanced-N 6205
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 34
                serial: 8c:70:5a:b9:bd:c4
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.3.6-030306-generic firmware=17.168.5.3 build 42301 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:47 memory:f1c00000-f1c01fff
        *-pci:2
             description: PCI bridge
             product: Panther Point PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:f1400000-f1bfffff ioport:f0c00000(size=8388608)
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f2539000-f25393ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Panther Point 6 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:50a8(size=8) ioport:50bc(size=4) ioport:50a0(size=8) ioport:50b8(size=4) ioport:5060(size=32) memory:f2538000-f25387ff
        *-serial UNCLAIMED
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f2534000-f25340ff ioport:efa0(size=32)
     *-scsi
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: PLEXTOR PX-128M3
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1.00
             serial: 002212110795
             size: 119GiB (128GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00058b92
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 90196b93-56db-4a38-a62e-db390af38646
                size: 23GiB
                capacity: 23GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-06-28 20:52:08 filesystem=ext4 lastmountpoint=/ modified=2012-06-28 21:03:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-07-12 13:34:21 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /home
                version: 1.0
                serial: 63973d2b-3950-4ea2-a233-252115715b61
                size: 95GiB
                capacity: 95GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2012-06-28 20:52:10 filesystem=ext4 lastmountpoint=/home modified=2012-07-12 13:34:21 mount.fstype=ext4 mount.options=rw,relatime,user_xattr,barrier=1,data=ordered mounted=2012-07-12 13:34:21 state=mounted
  *-battery
       product: 45N1027
       vendor: SANYO
       physical id: 1
       slot: Rear
       capacity: 93240mWh
       configuration: voltage=11.1V

---

### Post by BurntSushi on 2012-10-04
Were you able to make any progress on this? (I'm experiencing the same issue on a T430.)

---

### Post by SJrX on 2012-10-04
Not really, I use autorandr, and just deal with the fallout. I've determined that it's only the first time I activate the monitor. I did open a bug with freedesktop, but haven't had time to follow up with it. There has been some progress, but it's a hassle and I'm too busy.

[https://bugs.freedesktop.org/show_bug.cgi?id=52973](https://bugs.freedesktop.org/show_bug.cgi?id=52973)

---

