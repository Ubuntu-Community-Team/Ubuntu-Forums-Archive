---
title: "Ubuntu12.04 HDMI audio fast playback"
date: 2014-04-08
forum: Multimedia Software
---

### Post by Navin_Sangtani on 2014-04-08
Hi all, I recently made the change from windows to linux specifically Ubuntu 12.04. I have installed it on my laptop and I am really happy with it, but I have a persistent issue and that is the audio over HDMI. The issue specifically is that, whenever I plug my laptop to my TV using a HDMI cable and change the sound to go through the TV speakers the the audio playback is faster than through the laptop speakers. I have tried searching for this problem for ages, and nobody seems to have an answer. Sorry, if this has been posted before but I have not been able to find it. 

Thank you in advance for your help.

Navin

P.S. Here are the specifications for my laptop (after running lshw)

```
navmeister@navmeiser-XPS-15-9530:~$ sudo lshw[sudo] password for navmeister: 
navmeiser-xps-15-9530     
    description: Portable Computer
    product: XPS 15 9530 (XPS 15 9530)
    vendor: Winbond Electronics
    version: A02
    serial: BLHCVZ1
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=portable sku=XPS 15 9530 uuid=44454C4C-4C00-1048-8043-C2C04F565A31
  *-core
       description: Motherboard
       product: XPS 15 9530
       vendor: Winbond Electronics
       physical id: 0
       version: A02
       serial: .BLHCVZ1.CN12963427005B.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A02
          date: 12/18/2013
          size: 64KiB
          capacity: 1984KiB
          capabilities: mca pci upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4200H CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 2f
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4200H CPU @ 2.80GHz
          slot: SOCKET 0
          size: 2801MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: CPU Internal L1
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: CPU Internal L2
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 6
             slot: CPU Internal L3
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5173QH0-YK0
             vendor: Samsung
             physical id: 0
             serial: 14E19200
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M471B5173QH0-YK0
             vendor: Samsung
             physical id: 1
             serial: 14E185F9
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 4th Gen Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:50 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:52 memory:f7e1c000-f7e1ffff
        *-generic:0 UNCLAIMED
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:f7e10000-f7e17fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:45 memory:f7e00000-f7e0ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:48 memory:f7e26000-f7e2600f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7e24000-f7e243ff
        *-multimedia:1
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:f7e18000-f7e1bfff
        *-pci:0
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:df200000-df3fffff ioport:df400000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 memory:f7d00000-f7dfffff
           *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 6b
                serial: 5c:51:4f:fa:66:1c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-19-generic firmware=22.1.7.0 ip=10.96.196.15 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:49 memory:f7d00000-f7d01fff
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: d5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 memory:f7c00000-f7cfffff
           *-generic
                description: Unassigned class
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:47 memory:f7c00000-f7c00fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7e23000-f7e233ff
        *-isa
             description: ISA bridge
             product: HM87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7e22000-f7e227ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7e21000-f7e210ff ioport:f040(size=32)
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: 8 Series Chipset Family Thermal Management Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f7e20000-f7e20fff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABF0
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: AM0P
             serial: 148XC7HWT
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ab25b
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: 674a7629-2802-4daf-a76f-692bed0092e6
                size: 7812MiB
                capacity: 7812MiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 458GiB
                capacity: 458GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 19GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 439GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: LITEONIT LMS-32L
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: DM51
             serial: TW0H9R7V550853AP3481
             size: 29GiB (32GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000e6c20
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                version: 1.0
                serial: 8510fd6c-837c-45f0-bb2c-3f463d4683ba
                size: 29GiB
                capacity: 29GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-04-07 16:58:08 filesystem=ext4 modified=2014-04-08 11:11:46 mounted=2014-04-08 11:10:58 state=clean
  *-battery
       description: Lithium-Ion Battery
       product: DELL H76MY39
       vendor: Simplo
       physical id: 1
       version: Not Specified
       serial: Not Specified
       slot: System Battery
       capacity: 61000mWh
       configuration: voltage=11.4V



```

---

### Post by Yellow Pasque on 2014-04-08
What kernel are you running?
```
uname -a
```

Have you tried this yet?
[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by Navin_Sangtani on 2014-04-09
Im running kernel: 3.11

```

navmeister@navmeiser-XPS-15-9530:~$ uname -a
Linux navmeiser-XPS-15-9530 3.11.0-19-generic #33~precise1-Ubuntu SMP Wed Mar 12 21:16:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

I have tried the solution you recommended but, when I tried the position fix quirking option it did nothing, and when I disabled pulse audio I was no longer able to output the audio over HDMI as the option was removed from the sound settings panel.

Navin

---

### Post by Yellow Pasque on 2014-04-09
The last suggestion I have is to try the latest sound module/driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by Navin_Sangtani on 2014-04-09
Thanks again, but the problem still persists. 

Navin

---

### Post by Yellow Pasque on 2014-04-10
At this point, it's probably best to file a bug. Make sure you give a link to your ALSA info, as Ubuntu 12.04 doesn't automatically gather all the info in one convenient document like later releases do: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Navin_Sangtani on 2014-07-07
Hi I recently upgraded the OS from 12.04 to 14.04 thinking that it would solve the issue, however, it did not. Fortunately I found this website, [http://www.pcurtis.com/defiant.htm](http://www.pcurtis.com/defiant.htm). Here I found out that by adding i915.disable_power_well=0 to the grub it fixed the problem. Hence, I will mark the thread as solved.

Navin

---

