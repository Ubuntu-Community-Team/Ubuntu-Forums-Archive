---
title: "lubuntu amd64/ati no sound issue"
date: 2015-02-06
forum: Multimedia Software
---

### Post by floggin on 2015-02-06
Hi,
I'm a relatively new user so please bear with me. 

My laptop (Toshiba Satellite S50D-A) came with windows 8, and all hardware worked just fine. Everyone who has ever used windows 8 will agree that it had to go. I installed lubuntu 14.1 on the system (and ubuntu 17.1 and mint 17.1 cinnamon for that matter) and no matter what I do, I can't get the sound working. Nothing out of the headphones jack or the onboard speakers. I can't check the HDMI output as I don't own a TV.

I have uninstalled, and reinstalled alsamixer. I have tried pavucontrol. I have played with all the settings. Nothing is muted. When I am playing a media file I see the (supposed) output in the mixer, but I get nothing out of my speakers or headphones jack.

I have also run through the sound troubleshooting guide with no success.

Any help will be greatly appreciated! I will post lshw output and aplay -l output below, but just ask if you want to know anything else! Thanks

```
#jeff@lappy:~$ sudo lshw
[sudo] password for jeff: 
lappy                     
    description: Notebook
    product: Satellite S50D-A (PSKKWC)
    vendor: TOSHIBA
    version: PSKKWC-00G005
    serial: XD382514S
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=Type1Family sku=PSKKWC uuid=A07A6E42-1E40-E381-3A6D-0C54A50A2B3B
  *-core
       description: Motherboard
       product: VG10AD
       vendor: AMD
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: 1.20
          date: 09/10/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb uefi
     *-cpu
          description: CPU
          product: AMD A10-5745M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD A10-5745M APU with Radeon(tm) HD Graphics
          serial: NotSupport
          slot: Socket FT1
          size: 1100MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold vmmcall bmi1 cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 192KiB
             capacity: 192KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: M471B5173BH0-YK0
             vendor: Samsung
             physical id: 0
             serial: 364BA5A4
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 800 MHz (1.2 ns)
             product: M471B5173BH0-YK0
             vendor: Samsung
             physical id: 1
             serial: 364BA57C
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-display
             description: VGA compatible controller
             product: Richland [Radeon HD 8610G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:48 memory:d0000000-dfffffff ioport:5000(size=256) memory:f0300000-f033ffff
        *-multimedia:0
             description: Audio device
             product: Trinity HDMI Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f0344000-f0347fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:4000(size=4096) memory:f0200000-f02fffff ioport:e0000000(size=268435456)
           *-display
                description: Display controller
                product: Sun PRO [Radeon HD 8570A/8570M]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:49 memory:e0000000-efffffff memory:f0200000-f023ffff ioport:4000(size=256) memory:f0240000-f025ffff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:f0100000-f01fffff ioport:f0400000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8188EE Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 64:5a:04:a0:4b:c5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8188ee driverversion=3.16.0-30-generic firmware=N/A ip=192.168.250.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:16 ioport:3000(size=256) memory:f0100000-f0103fff
        *-pci:2
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:f1000000-f1ffffff ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: QCA8172 Fast Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 10
                serial: 0c:54:a5:0a:2b:3b
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
                resources: irq:47 memory:f1000000-f103ffff ioport:2000(size=128)
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0348000-f0349fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:45 ioport:5118(size=8) ioport:5124(size=4) ioport:5110(size=8) ioport:5120(size=4) ioport:5100(size=16) memory:f034f000-f034f7ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f034e000-f034efff
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f034d000-f034d0ff
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f034c000-f034cfff
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:17 memory:f034b000-f034b0ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 16
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:f0340000-f0343fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode
        *-usb:5
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:f034a000-f034afff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 4M
             serial: 93CIP3UKT
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=219e579c-89e0-4640-8a54-f603b505ff50 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: f617-ac2b
                size: 510MiB
                capacity: 511MiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 98977a03-33d8-4a5f-8ce1-7aace008eaa3
                size: 923GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-02-05 13:20:32 filesystem=ext4 lastmountpoint=/ modified=2015-02-06 12:17:21 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-02-06 12:17:21 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 294b9d2f-9cfc-4dda-a7dc-762ee73314f2
                size: 7372MiB
                capacity: 7373MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SU-208DB
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: TF01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Card  Reader
             vendor: Multiple
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             serial: AU6485
             capabilities: removable
             configuration: ansiversion=4 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb





Also;

jeff@lappy:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: 92HD99BXX Analog [92HD99BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by sudodus on 2015-02-06
Welcome to the Ubuntu Forums :-)

Often it helps if you install ***[COLOR=#0000cd]both[/COLOR] pulseaudio and pavucontrol***. Then try pavucontrol again.

You might have luck and find the correct setting quickly, but sometimes you have to test a lot of settings (for hours) before you find what is needed. Do the tweaking while playing some music, so that you notice, when the audio starts working.

---

### Post by floggin on 2015-02-07
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Often it helps if you install ***[COLOR=#0000cd]both[/COLOR] pulseaudio and pavucontrol***. Then try pavucontrol again.

You might have luck and find the correct setting quickly, but sometimes you have to test a lot of settings (for hours) before you find what is needed. Do the tweaking while playing some music, so that you notice, when the audio starts working.

Thanks for the reply sudodus!

I have definitely put some time in (of and on for a week now), pouring over the forums trying to find a solution. I am currently at the end of my rope.
I neglected to say that I had also installed pulse audio, but I don't know where else I can change more settings? I have tried ever combo available in pavucontrol and alsamixer. 
I am currently back on alsamixer, after reading the ALSA wiki entry i made sure that the sound card and not the HDMI was the system default.
Are there any configuration files people can recommend I look at??

---

### Post by sudodus on 2015-02-07
I can help with simple tricks like installing and using pavucontrol. But this seems to be more complicated. Let us hope someone who knows more about making audio work will chip in and help.

---

### Post by Rob Sayer on 2015-02-09
You could try selecting a different output in alsamixer.  A quick search didn't find much encouragement.  The best I can find is

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1222249](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1222249)

but it's not exactly written in novice friendly language.

---

### Post by Yellow Pasque on 2015-02-09
Here's my troubleshooting guide -
Step 1. Try latest sound module/driver:
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

2. If it still doesn't work after reboot, give more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

