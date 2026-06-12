---
title: "No Sound after USB Wireless Install"
date: 2012-04-26
forum: Multimedia Software
---

### Post by ExSuSEusr on 2012-04-26
I have a Azalia (HDA) sound card SBx00.

This afternoon I bought an installed a Linksys AE2500 wireless adapter for a net connection with this desktop.

I installed the adapter without any problems following these instructions:

[http://ubuntuforums.org/showthread.php?t=1805830&page=4](http://ubuntuforums.org/showthread.php?t=1805830&page=4)

Worked great - have a very decent connection now.  

HOWEVER - after reboot I had no sound.

When I go into Preferences --> Sound I see "Dummy Output" for my device.

So, I uninstalled and reinstalled alsa-base and pulse.  Rebooted... nothing.

When I run **sudo alsa force-reload**

I get: 

[B]Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).[/B]

I installed Alsamixer and can manipulate the levels, but no sound.  

My sound card is:

ioport:376 ioport:ff00(size=16)
        *-multimedia **UNCLAIMED**
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=64
             resources: memory:f7ff4000-f7ff7fff

Again the sound worked great before I installed the Linksys wireless USB adapter.

Any ideas?

---

### Post by ExSuSEusr on 2012-04-26
No one? I really need my sound working....

---

### Post by UltimateCat on 2012-04-26
My adapter is a Linksys also.  I had to find a driver for it and until I did I couldn't get online.

I think your new sound card is working fine especially if it's brand new. Sometimes tho even new thing aren't free of manufacturer defects.   You might need a driver to accommodate your new card.

You mentioned that your sound was fine until you installed the Linksys Adapter......more than likely you need a driver.

Try going to Google and trouble shoot your card or the manufacturer of your new card should offer a website or 1-800 # for support-

Hope this helps.

---

### Post by ExSuSEusr on 2012-04-26
Thanks for the info, but I think I might have confused you...

The sound card is "old" it was never replaced.  The USB network adapter is new - that is the item I installed today.  

The sound has been working fine for a couple of years now on this machine (since I built it).

But, today after I rebooted at the conclusion of getting the USB wireless adapter running - the sound was gone.

Here's some more information:

***alsa-base.conf:***

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
#options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
#options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
***sudo aplay -l***

> 
aplay: device_list:252: no soundcards found...***sudo lshw***

> unreal                    
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=E05E95E3-D311-DE11-A995-00248C660C0A
  *-core
       description: Motherboard
       product: M4A78-EM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MS1C93BC2L01804
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0312
          date: 02/16/2009
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.3.3
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
          configuration: cores=2 enabledcores=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.3.3
          size: 3200MHz
          capacity: 3200MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:f8000000-fbefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 8800 GTS 512]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:dc00(size=128) memory:fbee0000-fbefffff
        *-pci:1
             description: PCI bridge
             product: RS780/RS880 PCI to PCI bridge (PCIE port 5)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:24:8c:66:0c:0a
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:42 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbfc0000-fbfdffff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:c000(size=8) ioport:b000(size=4) ioport:a000(size=8) ioport:9000(size=4) ioport:8000(size=16) memory:f7fffc00-f7ffffff
           *-disk
                description: ATA Disk
                product: ST3500410AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: CC34
                serial: 5VM0W8XD
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=36c536c5
              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 06456dc3-5c7f-0349-acee-260104ef60f7
                   size: 292GiB
                   capacity: 292GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-06-06 00:44:43 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
        *-usb:0
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f7ffe000-f7ffefff
        *-usb:1
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f7ffd000-f7ffdfff
        *-usb:2
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f7fff800-f7fff8ff
        *-usb:3
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f7ffc000-f7ffcfff
        *-usb:4
             description: USB controller
             product: SB7x0 USB OHCI1 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f7ffb000-f7ffbfff
        *-usb:5
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f7fff400-f7fff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: SPD2413P
                vendor: PHILIPS
                physical id: 0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: GP03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: ST3250310AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@5:0.1.0
                logical name: /dev/sdb
                version: 3.AA
                serial: 5RY18GWE
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=50fc50fc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.1.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: af314acc-c7f5-4269-8ef2-6e29c6cf0e6d
                   size: 223GiB
                   capacity: 223GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2009-11-12 07:48:28 filesystem=ext4 lastmountpoint=/ modified=2012-04-26 19:11:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-26 21:54:42 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.1.0,2
                   logical name: /dev/sdb2
                   size: 9601MiB
                   capacity: 9601MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 9601MiB
                      capabilities: nofs
        [B]*-multimedia UNCLAIMED
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64
             resources: memory:f7ff4000-f7ff7fff[/B]
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-usb:6
             description: USB controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f7ffa000-f7ffafff
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
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 20:aa:4b:85:45:92
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwlhigh5 driverversion=1.57+Cisco Consumer Products LLC ip=192.168.1.106 link=yes multicast=yes wireless=IEEE 802.11gAs I said, the sound work just fine until I rebooted after installing the Linksys USB Wireless adapter.

For that I used the directions listed in the link in my OP.

I have uninstalled and reinstalled Alsa-base and pluseaudio two or three times....

In "Prefrences" --> "Sound" it still reads **"Dummy Output"** in the output device - there is no selection for any other devices.

---

### Post by ExSuSEusr on 2012-04-26
More information:

***find /lib/modules/`uname -r` | grep snd***


> 
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd-rawmidi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq-midi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq-midi-emul.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq-dummy.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq-device.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq-midi-event.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/seq/snd-seq-virmidi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd-hwdep.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd-timer.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd-page-alloc.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/oss/snd-mixer-oss.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd-hrtimer.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/core/snd-pcm.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/synth/snd-util-mem.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/synth/emux/snd-emux-synth.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8782.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-sgtl5000.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8961.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8962.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8985.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8731.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8940.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-cs4271.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8995.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ssm2602.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8900.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4104.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8523.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-max98088.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8753.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8804.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4642.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-max9877.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-alc5623.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8960.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm1250-ev1.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-uda1380.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic26.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8996.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8711.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic32x4.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8903.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-lm4857.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8994.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-l3.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-da7210.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8510.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8737.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8728.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8955.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm9090.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-rt5631.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8991.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ad193x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8990.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ads117x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm9081.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-pcm3008.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8580.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8978.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8904.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm5100.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8750.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320dac33.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8741.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-88pm860x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8727.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-max98095.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4671.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-adau1373.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8400.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8993.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ad73311.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wl1273.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8988.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8350.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm-hubs.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8974.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-cs42l51.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm2000.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-uda134x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-cs4270.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic3x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8971.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-max9850.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-cx20442.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8983.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4535.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ak4641.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-tpa6130a2.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8776.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-dfbmcs320.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-spdif.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-wm8770.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-adav80x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-ad1836.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-sta32x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-tlv320aic23.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/codecs/snd-soc-jz4740-codec.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/soc/snd-soc-core.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/snd-usb-audio.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/caiaq/snd-usb-caiaq.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/usx2y/snd-usb-us122l.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/usx2y/snd-usb-usx2y.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/misc/snd-ua101.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/6fire/snd-usb-6fire.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/usb/snd-usbmidi-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-aloop.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-mts64.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-mtpav.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/opl4/snd-opl4-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/opl4/snd-opl4-synth.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/vx/snd-vx-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-dummy.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-virmidi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-portman2x4.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/snd-serial-u16550.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/opl3/snd-opl3-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/drivers/opl3/snd-opl3-synth.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pcmcia/pdaudiocf/snd-pdaudiocf.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pcmcia/vx/snd-vxpocket.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/es1688/snd-es1688-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/es1688/snd-es1688.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/opti9xx/snd-opti93x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-ad1848.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/opti9xx/snd-miro.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/opti9xx/snd-opti92x-cs4231.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/msnd
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/msnd/snd-msnd-classic.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/msnd/snd-msnd-pinnacle.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/msnd/snd-msnd-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-es18xx.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-azt2320.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/galaxy/snd-azt1605.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/galaxy/snd-azt2316.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/cs423x/snd-cs4236.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/cs423x/snd-cs4231.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-sscape.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/ad1816a/snd-ad1816a.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-sc6000.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-adlib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/ad1848/snd-ad1848.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/wavefront/snd-wavefront.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/wss/snd-wss-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sb8.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sb16-csp.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sb16-dsp.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sb16.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sb-common.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sb8-dsp.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-emu8000-synth.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-jazz16.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/sb/snd-sbawe.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-als100.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-opl3sa2.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/snd-cmi8330.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/gus/snd-interwave-stb.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/gus/snd-gus-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/gus/snd-gusclassic.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/gus/snd-gusmax.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/gus/snd-gusextreme.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/isa/gus/snd-interwave.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/other/snd-ak4xxx-adda.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/other/snd-ak4117.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/other/snd-pt2258.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/other/snd-ak4113.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/other/snd-tea575x-tuner.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/other/snd-ak4114.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/snd-tea6330t.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/snd-cs8427.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/i2c/snd-i2c.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-es1968.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ymfpci/snd-ymfpci.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-ad1889.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/rme9652/snd-rme9652.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/rme9652/snd-hdsp.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/rme9652/snd-hdspm.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/nm256/snd-nm256.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/oxygen/snd-oxygen.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/oxygen/snd-virtuoso.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/oxygen/snd-oxygen-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/au88x0/snd-au8810.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/au88x0/snd-au8830.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/au88x0/snd-au8820.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/cs5535audio/snd-cs5535audio.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-cs5530.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-darla20.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-darla24.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-gina20.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-indigodj.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-layla20.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-echo3g.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-layla24.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-indigoiox.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-indigoio.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-mia.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-indigodjx.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-gina24.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-mona.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/echoaudio/snd-indigo.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/emu10k1/snd-emu10k1x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ctxfi/snd-ctxfi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/trident/snd-trident.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/vx222/snd-vx222.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-ens1370.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-es1938.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ice1712/snd-ice17xx-ak4xxx.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ice1712/snd-ice1712.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ice1712/snd-ice1724.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-atiixp.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-als4000.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/mixart/snd-mixart.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/riptide/snd-riptide.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-cmipci.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/korg1212/snd-korg1212.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/aw2/snd-aw2.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-via82xx.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-via82xx-modem.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-als300.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/asihpi/snd-asihpi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-cs4281.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ali5451/snd-ali5451.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-ens1371.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/pcxhr/snd-pcxhr.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/lola/snd-lola.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-atiixp-modem.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-hdmi.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-ca0132.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-azt3328.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/lx6464es/snd-lx6464es.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-rme96.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/ca0106/snd-ca0106.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-maestro3.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/cs46xx/snd-cs46xx.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-rme32.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-sis7019.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-bt87x.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-fm801.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/pci/snd-sonicvibes.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/firewire/snd-firewire-speakers.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/firewire/snd-firewire-lib.ko
/lib/modules/3.2.0-23-generic-pae/kernel/sound/firewire/snd-isight.ko


---

