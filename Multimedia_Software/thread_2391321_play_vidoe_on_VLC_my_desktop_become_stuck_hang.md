---
title: "play vidoe on VLC my desktop become stuck hang"
date: 2018-05-08
forum: Multimedia Software
---

### Post by abartkorn on 2018-05-08
hello, help me pls,, 
my desktop running ubuntu 18.04
when i play movie using VLC ... movie stuck , VLC hang, desktop hang..
why??
before this, my desktop using ubuntu 17.10 , play movie via VLC smooth...

---

### Post by mörgæs on 2018-05-08
Hi, welcome to the fora.

First let's see the hardware. Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the command line, run it and post lshw.txt in CODE tags.

---

### Post by abartkorn on 2018-05-09
computer                    
    description: Desktop Computer
    ```
product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: P5P43TD PRO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0710
          date: 11/04/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.40GHz
          serial: [REMOVED]
          slot: LGA775
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 266MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti tpr_shadow vnmi flexpriority dtherm cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
             configuration: level=2
     *-memory
          description: System Memory
          physical id: 33
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:b000(size=4096) memory:fa000000-fe7fffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G96 [GeForce 9500 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:24 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:bc00(size=128) memory:c0000-dffff
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:a800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:a880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ac00(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f9fff000-f9fff3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-20-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:25 memory:f9ff8000-f9ffbfff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:1000(size=4096) memory:f0000000-f03fffff ioport:f8f00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:fea00000-feafffff ioport:f0400000(size=2097152)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:17 memory:feaff800-feafffff memory:feaff400-feaff47f memory:feaff000-feaff07f memory:feafec00-feafec7f
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:f0600000(size=2097152)
           *-storage
                description: SATA controller
                product: JMB361 AHCI/IDE
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:16 memory:fe9fe000-fe9fffff memory:fe9e0000-fe9effff
           *-ide
                description: IDE interface
                product: JMB361 AHCI/IDE
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:dc00(size=8) ioport:d880(size=4) ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=16)
        *-pci:4
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:c000(size=4096) memory:fe800000-fe8fffff ioport:f0800000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: b0
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
                resources: irq:17 memory:fe8c0000-fe8fffff ioport:cc00(size=128)
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:a080(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:a480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-20-generic uhci_hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: Microsoft
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@8:1
                   version: 4.30
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f9ffe000-f9ffe3ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-20-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: USB 2.0 Hub
                   vendor: Terminus Technology Inc.
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.11
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: USB hub
                      product: USB 2.0 Hub
                      vendor: Terminus Technology Inc.
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 1.11
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                    *-usb
                         description: Keyboard
                         physical id: 2
                         bus info: usb@2:1.4.2
                         version: 1.00
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-pci:5
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:feb00000-febfffff
           *-multimedia
                description: Multimedia audio controller
                product: CA0106/CA0111 [SB Live!/Audigy/X-Fi Series]
                vendor: Creative Labs
                physical id: 1
                bus info: pci@0000:06:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_ca0106 latency=64 maxlatency=20 mingnt=2
                resources: irq:17 ioport:ec00(size=32)
           *-network
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: enp6s2
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:18 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:9000(size=8) ioport:8c00(size=4) ioport:8880(size=8) ioport:8800(size=4) ioport:8480(size=16) ioport:8400(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9ffd000-f9ffd0ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:a000(size=8) ioport:9c00(size=4) ioport:9880(size=8) ioport:9800(size=4) ioport:9480(size=16) ioport:9400(size=16)
     *-scsi
          physical id: 1
          logical name: scsi3
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST1000DM010-2EP1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: CC43
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=d63cdbf2
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2017-10-10 11:34:58 filesystem=ext4 lastmountpoint=/ modified=2018-05-08 18:38:57 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-05-08 11:11:08 state=mounted
```

---

### Post by monkeybrain20122 on 2018-05-09
```
*-display
                description: VGA compatible controller
                product: G96 [GeForce 9500 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: **driver=nouveau** latency=0
```

Maybe noveau is not working out and you need to install Nvidia's driver?

---

### Post by abartkorn on 2018-05-10
How to install nvidia driver?

---

### Post by SeijiSensei on 2018-05-10
Choose "Additional Drivers" in the Software and Updates application.  It should detect your card and download and install the appropriate driver.

---

### Post by monkeybrain20122 on 2018-05-10
> **abartkorn said:**
> How to install nvidia driver?
```

sudo apt install nvidia-340-updates
```

Then run

```
sudo nvidia-xconfig
```

Then reboot.

Yours in an old card, nvidia-340 is the driver you need. See [here]("http://www.nvidia.com/Download/driverResults.aspx/130042/en-us").

P.S. you may wonder how do people find the names of packages to install. There are several ways but the easiest is to install synaptic and search there, it is a much better package manager than the software centre

```
sudo apt install synaptic
```

---

### Post by monkeybrain20122 on 2018-05-10
Oh once you get the nvidia driver working, don't forget to configure vlc to use hardware acceleration. Go to tools > preferences > videos > output and choose vdpau from the drop down; also tools > preferences >input and codecs settings > hardware acceleration decoding choose vdpau decoder from the drop down menu.

Choosing vdpau in tools > preferences > videos > output reduces cpu usage by a lot but has the side effect of not being able to view 360 degree videos (vlc 3.0 and above) so if you want to watch these videos just change this setting back to automatic, vdpau decoder in tools > preferences >input and codecs settings > hardware acceleration does not have any issue with 360 degree videos

P.S mpv is actually a more efficient video player than vlc to use hardware acceleration (both vdpau and vaapi) , if you want to reduce cpu usage I would give it a try.

---

### Post by abartkorn on 2018-05-12
thx all for help me.

---

### Post by monkeybrain20122 on 2018-05-12
"Additional Drivers" apparently doesn't work. Here on 16.04 I have nvidia-390.48 and have been using the gpu for 6 months but "Additional Drivers" reports no proprietary driver is installed (and none recommended). IIRC detecting additional driver is broken half the time since they replaced jokey with this junk around 2011/2012.

---

