---
title: "Wireless internet freezing leading to a slow computer"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by Ameades on 2011-08-03
I first noticed the problem because my wireless internet will stop working.  The usb stick has its LED constantly on but it fails to connect.

I have tried some methods of restarting the networking, like "sudo restart network-manager", disabling and re-enabling the wireless and networking from the taskbar applet.  I tried removing the module and restarting it.

It might be a bigger problem because I'll find that things will randomly hand for awhile, like opening system monitor, or running terminal commands.  They do eventually run but only after several minutes.

A restart seems to get everything working again, but the problem comes back at random times.

I am willing to solve this right now as I have time, just let me know what info you need and I will post it.

Update: 

Some more info I forgot to include.  I am running Ubuntu 11.04.  It just froze again, I tried logging in and out but the internet still wouldn't work and things were hanging, I couldn't get file manager open.  I have even tried shutting down the computer and had it stall on the Ubuntu logo with the dots loading so I had to hard restart.

Note: I run Ubuntu on the classic set up because the Unity menu is broken.  It doesnt even appear when I log on.  Unity has been broken since I upgraded months ago, and this issue is only a week old, so I don't think this is the cause.



Here is some info to get started, please let me know what else.

```
andrew@Optimus-Prime:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
02:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
andrew@Optimus-Prime:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 003: ID 1737:0071 Linksys WUSB600N Dual-Band Wireless-N USB Network Adapter
Bus 001 Device 002: ID 04a9:1716 Canon, Inc. MP460 Composite
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
andrew@Optimus-Prime:~$ sudo lshw
[sudo] password for andrew: 
optimus-prime             
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=A06A001E-8C00-00FD-55A2-E0CB4EFD0207
  *-core
       description: Motherboard
       product: M4A78T-E
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 103946770001094
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3406
          date: 08/20/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Phenom(tm) II X6 1055T Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X6 1055T Processor
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 2800MHz
          capacity: 3300MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpb npt lbrv svm_lock nrip_save pausefilter
          configuration: cores=6 enabledcores=6
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 768KiB
             capacity: 768KiB
             capabilities: pipeline-burst internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: pipeline-burst internal varies
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 34
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 1066 MHz (0.9 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 1066 MHz (0.9 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
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
             resources: irq:40 ioport:c000(size=4096) memory:fbd00000-fbdfffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Juniper [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:46 memory:d0000000-dfffffff memory:fbdc0000-fbddffff ioport:c000(size=256) memory:fbda0000-fbdbffff
           *-multimedia
                description: Audio device
                product: Juniper HDMI Audio [Radeon HD 5700 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:44 memory:fbdfc000-fbdfffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:fbe00000-fbefffff
           *-network
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: e0:cb:4e:fd:02:07
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:fbec0000-fbefffff ioport:dc00(size=128)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 3)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:fbf00000-fbffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6315 Series Firewire Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:19 memory:fbfff800-fbffffff ioport:e800(size=256)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:43 ioport:b000(size=8) ioport:a000(size=4) ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=16) memory:fbcffc00-fbcfffff
           *-disk
                description: ATA Disk
                product: WDC WD10EALS-00Z
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCATR0688140
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8b711306
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: f40a-23b3
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-11-03 13:10:39 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 3c725b99-1fee-5d49-992e-1336fecdd5ae
                   size: 639GiB
                   capacity: 639GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2010-11-03 13:10:47 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@5:0.0.0,3
                   logical name: /dev/sda3
                   size: 292GiB
                   capacity: 292GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 280GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 11GiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fbcfd000-fbcfdfff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fbcfe000-fbcfefff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fbcff800-fbcff8ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fbcfb000-fbcfbfff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fbcfc000-fbcfcfff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fbcff400-fbcff4ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB7x0/SB8x0/SB9x0 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
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
             resources: irq:16 memory:fbcf4000-fbcf7fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
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
        *-usb:6
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fbcfa000-fbcfafff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:1e:e5:e0:4e:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.1.102 multicast=yes wireless=Ralink STA

```

```
andrew@Optimus-Prime:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_via      62470  1 
usbhid                 46956  0 
hid                    91020  1 usbhid
usblp                  18233  0 
snd_usb_audio         112426  1 
snd_hda_intel          33211  2 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
rt2870sta             450556  1 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
uvcvideo               72195  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               82052  1 uvcvideo
crc_ccitt              12667  1 rt2870sta
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
edac_core              53845  0 
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17078  1 videodev
edac_mce_amd           23464  0 
fglrx                2739144  118 
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
psmouse                73535  0 
k10temp                13119  0 
serio_raw              13166  0 
sp5100_tco             13744  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13303  0 
asus_atk0110           17976  0 
snd_timer              29602  2 snd_seq,snd_pcm
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_via,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
pata_atiixp            13165  0 
floppy                 74120  0 
libahci                26642  1 ahci
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
atl1e                  37715  0 
crc_itu_t              12707  1 firewire_core

```

Thanks,  I really need to solve this today as I can't be wasting time constantly restarting my computer.

---

### Post by Ameades on 2011-08-03
I am now starting to think that it might be a hardware issue.  I tried restarting X to see if that would do anything, I typed "sudo init 1" to try and get to single user mode and then was going to go back to init 2, but then the computer got stuck trying to boot to init 1 and I had to restart.  The fan on the computer was running full blast when it stuck.

How could I go about determining what hardware component it might be?

---

### Post by wildmanne39 on 2011-08-03
Hi, the problems you are having can be hard to find the cause. Here is a link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Also after your get booted into ubuntu after a freeze go right to the terminal and run this command to see if there are any error messages.
```
sudo tail -n25 /var/log/syslog
```
Also for freezing issues you should be in general section of the forum.

You should log out and click on your username then go to the bottom of the screen and choose ubuntu with no effects and see if you still have that issue.
Thank you

---

### Post by wildmanne39 on 2011-08-03
Hi, also You are using this driver fglrx for your video card it is know to cause problems here is a link on that.
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Thank you

---

### Post by Ameades on 2011-08-03
Thanks for the response wildmanne39.  I am currently reading through the links you provided and I will post any findings.  I will also run the 'tail' command as soon as the issue happens again and post the results.

---

### Post by Ameades on 2011-08-03
I think I have noticed in the syslog where the problem occured.  I believe it froze at 15:25:07 and then shortly after I had to reboot.

Here is the code.  Is there anything in there that would help?

```
Aug  3 14:44:46 Optimus-Prime kernel: [ 1889.004906] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 14:46:41 Optimus-Prime kernel: [ 2004.010118] #
Aug  3 14:46:41 Optimus-Prime kernel: [ 2004.020117] #
Aug  3 14:46:46 Optimus-Prime kernel: [ 2009.005492] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 341
Aug  3 14:48:46 Optimus-Prime kernel: [ 2129.004620] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 478
Aug  3 14:50:41 Optimus-Prime kernel: [ 2244.010106] #
Aug  3 14:50:41 Optimus-Prime kernel: [ 2244.020107] #
Aug  3 14:50:46 Optimus-Prime kernel: [ 2249.004704] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 864
Aug  3 14:52:41 Optimus-Prime kernel: [ 2364.010100] #
Aug  3 14:52:46 Optimus-Prime kernel: [ 2369.003745] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 14:54:41 Optimus-Prime kernel: [ 2484.010095] #
Aug  3 14:54:41 Optimus-Prime kernel: [ 2484.020092] #
Aug  3 14:54:46 Optimus-Prime kernel: [ 2489.004214] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 715
Aug  3 14:56:41 Optimus-Prime kernel: [ 2604.010088] #
Aug  3 14:56:41 Optimus-Prime kernel: [ 2604.020085] #
Aug  3 14:56:46 Optimus-Prime kernel: [ 2609.003479] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 14:58:46 Optimus-Prime kernel: [ 2729.004350] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 712
Aug  3 15:00:46 Optimus-Prime kernel: [ 2849.004182] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 563
Aug  3 15:02:41 Optimus-Prime kernel: [ 2964.720100] #
Aug  3 15:02:46 Optimus-Prime kernel: [ 2969.004006] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 630
Aug  3 15:04:41 Optimus-Prime kernel: [ 3084.010069] #
Aug  3 15:04:46 Optimus-Prime kernel: [ 3089.003835] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 338
Aug  3 15:06:41 Optimus-Prime kernel: [ 3204.010061] #
Aug  3 15:06:46 Optimus-Prime kernel: [ 3209.004476] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 630
Aug  3 15:08:46 Optimus-Prime kernel: [ 3329.004338] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 712
Aug  3 15:10:46 Optimus-Prime kernel: [ 3449.004019] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 712
Aug  3 15:12:41 Optimus-Prime kernel: [ 3564.010165] #
Aug  3 15:12:46 Optimus-Prime kernel: [ 3569.003189] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 676
Aug  3 15:13:48 Optimus-Prime kernel: [ 3631.170081] #
Aug  3 15:14:46 Optimus-Prime kernel: [ 3689.004129] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 712
Aug  3 15:16:43 Optimus-Prime kernel: [ 3805.840033] #
Aug  3 15:16:46 Optimus-Prime kernel: [ 3809.003778] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:17:01 Optimus-Prime CRON[2398]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  3 15:18:46 Optimus-Prime kernel: [ 3929.003470] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:20:46 Optimus-Prime kernel: [ 4049.003679] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 864
Aug  3 15:22:46 Optimus-Prime kernel: [ 4169.003356] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:24:46 Optimus-Prime kernel: [ 4289.003834] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 189
Aug  3 15:25:07 Optimus-Prime kernel: [ 4309.940047] #
Aug  3 15:25:07 Optimus-Prime wpa_supplicant[1480]: CTRL-EVENT-DISCONNECTED bssid=00:1d:7e:1f:44:d8 reason=0
Aug  3 15:25:07 Optimus-Prime wpa_supplicant[1480]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Aug  3 15:25:07 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Aug  3 15:25:07 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug  3 15:25:17 Optimus-Prime kernel: [ 4320.060069] #
Aug  3 15:25:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 8 -> 3 (reason 11)
Aug  3 15:25:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): deactivating device (reason: 11).
Aug  3 15:25:22 Optimus-Prime wpa_supplicant[1480]: Trying to associate with 00:1d:7e:1f:44:d8 (SSID='Meades' Network' freq=2437 MHz)
Aug  3 15:25:22 Optimus-Prime kernel: [ 4325.059667] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 189
Aug  3 15:25:22 Optimus-Prime kernel: [ 4325.059793] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Aug  3 15:25:22 Optimus-Prime kernel: [ 4325.060032] #
Aug  3 15:25:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1942
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.776756] ---> RTMPFreeTxRxRingMemory
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.776775] <--- RTMPFreeTxRxRingMemory
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.790059] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.810054] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.830053] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.850053] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.870048] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.890045] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.910038] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.930035] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.950033] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4325.970155] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.104249] <-- RTMPAllocTxRxRingMemory, Status=0
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.106510] -->RTUSBVenderReset
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.106636] <--RTUSBVenderReset
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.190125] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.210122] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.230120] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.240120] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.250118] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.260117] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.270116] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.280114] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.290113] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.300111] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.310110] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.320108] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.330107] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.340106] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.350104] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.360104] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.370102] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.380101] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.390099] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.400098] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.410097] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.420095] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.430096] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.440092] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.450091] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.460090] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.470088] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.480090] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.490086] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.500085] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.510083] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.520082] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.530080] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.540079] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.550078] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.560077] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.570076] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.580074] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.590072] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.600071] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.610070] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.618818] 1. Phy Mode = 0
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.618819] 2. Phy Mode = 0
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.620070] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.630068] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.640068] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.650067] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.660066] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.670063] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.680063] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.690061] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.700059] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.710056] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.716806] 3. Phy Mode = 0
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.720055] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.727430] MCS Set = 00 00 00 00 00
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.730053] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.740053] #
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.748054] <==== rt28xx_init, Status=0
Aug  3 15:25:23 Optimus-Prime kernel: [ 4326.749675] 0x1300 = 000a4200
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) starting connection 'Auto Meades' Network'
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0/wireless): access point 'Auto Meades' Network' has security, but secrets are required.
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0/wireless): connection 'Auto Meades' Network' has security, and secrets exist.  No new secrets needed.
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Config: added 'ssid' value 'Meades' Network'
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Config: added 'scan_ssid' value '1'
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Config: added 'psk' value '<omitted>'
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  3 15:25:23 Optimus-Prime NetworkManager[926]: <info> Config: set interface ap_scan to 1
Aug  3 15:25:24 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug  3 15:25:24 Optimus-Prime kernel: [ 4326.780051] #
Aug  3 15:25:24 Optimus-Prime kernel: [ 4326.790047] #
Aug  3 15:25:34 Optimus-Prime kernel: [ 4336.790089] #
Aug  3 15:25:34 Optimus-Prime kernel: [ 4337.610029] wlan0: no IPv6 routers present
Aug  3 15:25:39 Optimus-Prime kernel: [ 4341.788973] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 140
Aug  3 15:25:39 Optimus-Prime kernel: [ 4341.920030] #
Aug  3 15:25:45 Optimus-Prime kernel: [ 4347.930102] #
Aug  3 15:25:49 Optimus-Prime wpa_supplicant[1480]: Trying to associate with 00:1d:7e:1f:44:d8 (SSID='Meades' Network' freq=2437 MHz)
Aug  3 15:25:49 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug  3 15:25:49 Optimus-Prime kernel: [ 4351.798481] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:25:49 Optimus-Prime kernel: [ 4351.798711] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Aug  3 15:25:49 Optimus-Prime kernel: [ 4351.800089] #
Aug  3 15:25:49 Optimus-Prime kernel: [ 4351.810085] #
Aug  3 15:25:49 Optimus-Prime wpa_supplicant[1480]: Associated with 00:1d:7e:1f:44:d8
Aug  3 15:25:49 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug  3 15:25:49 Optimus-Prime kernel: [ 4351.880075] #
Aug  3 15:25:49 Optimus-Prime kernel: [ 4351.960064] #
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  3 15:25:50 Optimus-Prime wpa_supplicant[1480]: WPA: Key negotiation completed with 00:1d:7e:1f:44:d8 [PTK=CCMP GTK=CCMP]
Aug  3 15:25:50 Optimus-Prime wpa_supplicant[1480]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:1f:44:d8 completed (reauth) [id=0 id_str=]
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Meades' Network'.
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug  3 15:25:50 Optimus-Prime kernel: [ 4352.870070] #
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> dhclient started with pid 2493
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug  3 15:25:50 Optimus-Prime dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug  3 15:25:50 Optimus-Prime dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug  3 15:25:50 Optimus-Prime dhclient: All rights reserved.
Aug  3 15:25:50 Optimus-Prime dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug  3 15:25:50 Optimus-Prime dhclient: 
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug  3 15:25:50 Optimus-Prime dhclient: Listening on LPF/wlan0/00:1e:e5:e0:4e:03
Aug  3 15:25:50 Optimus-Prime dhclient: Sending on   LPF/wlan0/00:1e:e5:e0:4e:03
Aug  3 15:25:50 Optimus-Prime dhclient: Sending on   Socket/fallback
Aug  3 15:25:50 Optimus-Prime dhclient: DHCPREQUEST of 192.168.1.102 on wlan0 to 255.255.255.255 port 67
Aug  3 15:25:50 Optimus-Prime dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Aug  3 15:25:50 Optimus-Prime dhclient: bound to 192.168.1.102 -- renewal in 41543 seconds.
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info>   address 192.168.1.102
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info>   prefix 24 (255.255.255.0)
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info>   gateway 192.168.1.1
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info>   hostname 'Optimus-Prime'
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info>   nameserver '192.168.1.1'
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Scheduling stage 5
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Done scheduling stage 5
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  3 15:25:50 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug  3 15:25:51 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug  3 15:25:51 Optimus-Prime NetworkManager[926]: <info> Policy set 'Auto Meades' Network' (wlan0) as default for IPv4 routing and DNS.
Aug  3 15:25:51 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) successful, device activated.
Aug  3 15:25:51 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  3 15:25:59 Optimus-Prime ntpdate[2538]: adjust time server 91.189.94.4 offset 0.080150 sec
Aug  3 15:26:41 Optimus-Prime kernel: [ 4404.010103] #
Aug  3 15:26:41 Optimus-Prime kernel: [ 4404.020108] #
Aug  3 15:26:46 Optimus-Prime kernel: [ 4409.003333] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:27:26 Optimus-Prime kernel: [ 4449.007105] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 515
Aug  3 15:28:26 Optimus-Prime kernel: [ 4509.007146] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 338
Aug  3 15:29:46 Optimus-Prime kernel: [ 4589.002865] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:31:21 Optimus-Prime kernel: [ 4684.020079] #
Aug  3 15:31:26 Optimus-Prime kernel: [ 4689.006896] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 478
Aug  3 15:33:21 Optimus-Prime kernel: [ 4804.010074] #
Aug  3 15:33:26 Optimus-Prime kernel: [ 4809.003839] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 515
Aug  3 15:34:11 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  3 15:34:11 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  3 15:35:21 Optimus-Prime kernel: [ 4924.020067] #
Aug  3 15:35:26 Optimus-Prime kernel: [ 4929.007292] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:37:21 Optimus-Prime kernel: [ 5044.010062] #
Aug  3 15:37:26 Optimus-Prime kernel: [ 5049.003711] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 715
Aug  3 15:39:21 Optimus-Prime kernel: [ 5164.020055] #
Aug  3 15:39:26 Optimus-Prime kernel: [ 5169.006836] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 563
Aug  3 15:41:21 Optimus-Prime kernel: [ 5284.020049] #
Aug  3 15:41:26 Optimus-Prime kernel: [ 5289.007027] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 563
Aug  3 15:43:21 Optimus-Prime kernel: [ 5404.020046] #
Aug  3 15:43:26 Optimus-Prime kernel: [ 5409.006821] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:45:21 Optimus-Prime kernel: [ 5524.020049] #
Aug  3 15:45:26 Optimus-Prime kernel: [ 5529.006171] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 478
Aug  3 15:47:21 Optimus-Prime kernel: [ 5644.010037] #
Aug  3 15:47:26 Optimus-Prime kernel: [ 5649.003405] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 423
Aug  3 15:49:26 Optimus-Prime kernel: [ 5769.003264] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 189
Aug  3 15:51:26 Optimus-Prime kernel: [ 5889.005903] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 15:53:26 Optimus-Prime kernel: [ 6009.005894] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 478
Aug  3 15:55:26 Optimus-Prime kernel: [ 6129.003608] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 478
Aug  3 15:57:21 Optimus-Prime kernel: [ 6244.010127] #
Aug  3 15:57:26 Optimus-Prime kernel: [ 6249.003423] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 490
Aug  3 15:59:21 Optimus-Prime kernel: [ 6364.020119] #
Aug  3 15:59:26 Optimus-Prime kernel: [ 6369.010650] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 16:01:21 Optimus-Prime kernel: [ 6484.010115] #
Aug  3 16:01:21 Optimus-Prime kernel: [ 6484.020114] #
Aug  3 16:01:26 Optimus-Prime kernel: [ 6489.008787] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 563
Aug  3 16:02:09 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  3 16:02:09 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  3 16:03:21 Optimus-Prime kernel: [ 6604.020107] #
Aug  3 16:03:26 Optimus-Prime kernel: [ 6609.010082] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 16:05:21 Optimus-Prime kernel: [ 6724.010103] #
Aug  3 16:05:26 Optimus-Prime kernel: [ 6729.007719] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 189
Aug  3 16:07:21 Optimus-Prime kernel: [ 6844.020101] #
Aug  3 16:07:26 Optimus-Prime kernel: [ 6849.010081] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 189
Aug  3 16:09:26 Optimus-Prime kernel: [ 6969.011333] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 16:11:05 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  3 16:11:05 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  3 16:11:21 Optimus-Prime kernel: [ 7084.010085] #
Aug  3 16:11:21 Optimus-Prime kernel: [ 7084.020083] #
Aug  3 16:11:26 Optimus-Prime kernel: [ 7089.007793] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 16:13:21 Optimus-Prime kernel: [ 7204.020077] #
Aug  3 16:13:26 Optimus-Prime kernel: [ 7209.010893] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 338
Aug  3 16:15:21 Optimus-Prime kernel: [ 7324.010073] #
Aug  3 16:15:26 Optimus-Prime kernel: [ 7329.004695] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 16:17:01 Optimus-Prime CRON[8768]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  3 16:17:26 Optimus-Prime kernel: [ 7449.005545] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 864
Aug  3 16:19:21 Optimus-Prime kernel: [ 7564.010060] #
Aug  3 16:19:26 Optimus-Prime kernel: [ 7569.007778] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 329
Aug  3 16:19:29 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  3 16:19:29 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
```

Also, I have tried to purge flgrx, except when I got to reinstall fglrx-modaliases, it cannot find that package and recommends fglrx.  Should I reinstall the fglrx package?

Thanks

---

### Post by wildmanne39 on 2011-08-03
Hi, it says you only need fglrx package if you want to be able to activate the driver through additional drivers, so you can do with out it.

As for that error message I am researching it.
Thank you

---

### Post by wildmanne39 on 2011-08-03
The disconnect you see is not the cause of the freezing that is a separate issue.

The disconnect can be caused by being to far away from your router.

Run these commands please and maybe we can figure it out.
```
sudo iwlist scan
```
```
uname -a
```
```
nm-tool
```
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
lsusb
```
and post the results here.
Thank you

---

### Post by Ameades on 2011-08-03
I just rebooted, but had to do it in safe mode as the screen would appear black.  I think I needed the fglrx package so I have reinstalled it.

Aside from that, I have another syslog for you here:  

```
andrew@Optimus-Prime:~$ sudo tail -n25 /var/log/syslog
[sudo] password for andrew: 
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.700046] #
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.710046] #
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.720028] #
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.730073] #
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.740055] #
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.745066] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x1022
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.745070] 	Request Value=0x9814!
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.750036] #
Aug  3 16:49:51 Optimus-Prime kernel: [ 9394.760042] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.770058] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.780042] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.790046] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.800049] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.810045] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.820048] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.830046] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.840049] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.845057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1704
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.850039] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.860038] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.870047] #
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.880027] #
Aug  3 16:49:52 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  3 16:49:52 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  3 16:49:52 Optimus-Prime kernel: [ 9394.890043] #
andrew@Optimus-Prime:~$ sudo tail -n100 /var/log/syslog
^CAug  3 16:55:21 Optimus-Prime kernel: [ 9724.750043] #
Aug  3 16:55:21 Optimus-Prime kernel: [ 9724.760051] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.770055] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.780043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.785045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.790048] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.800043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.810043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.820041] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.830043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.840043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.850043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.860043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.870043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.880043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.885045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.890048] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.900043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.910043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.920047] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.930043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.940043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.950042] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.960043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.970040] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.980038] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.985039] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9724.990048] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.000053] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.010049] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.020052] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.030047] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.040057] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.050049] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.060041] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.070044] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.080044] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.085046] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.090053] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.100048] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.110044] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.120043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.130043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.140043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.150043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.160043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.170044] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.180043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.185045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.190067] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.200050] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.210043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.220043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.230043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.240051] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.250042] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.260054] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.270063] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.280043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.285045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.290051] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.300048] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.310041] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.320043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.330043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.340040] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.350043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.360049] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.370050] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.380041] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.385043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.390046] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.400034] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.410045] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.420043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.430043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.440048] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.450043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.460049] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.470043] #
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <error> [1312404922.709366] [nm-device-wifi.c:1548] nm_device_wifi_set_mode(): (wlan0): error setting mode 2
Aug  3 16:55:22 Optimus-Prime wpa_supplicant[1480]: Failed to initiate AP scan.
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.480043] #
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.485045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.486046] NICLoadFirmware: MCU is not ready
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.486047] NICLoadFirmware failed, Status[=0x00000001]
Aug  3 16:55:22 Optimus-Prime kernel: [ 9725.486050] rt28xx Initialized fail!
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) starting connection 'Auto Meades' Network'
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  disconnected -> inactive
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): supplicant connection state:  scanning -> inactive
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  3 16:55:22 Optimus-Prime NetworkManager[926]: <info> (wlan0): bringing up device.
andrew@Optimus-Prime:~$ sudo tail -n100 /var/log/syslog
Aug  3 17:00:38 Optimus-Prime kernel: [10041.100050] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.110049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.120049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.130049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.140049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.150049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.160049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.170049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.180043] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.185050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:38 Optimus-Prime kernel: [10041.190101] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.200046] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.210028] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.220048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.230051] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.240049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.250047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.260040] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.270036] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.280033] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.285035] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:38 Optimus-Prime kernel: [10041.290049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.300054] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.310052] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.320048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.330048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.340047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.350045] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.360045] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.370053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.380062] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.385063] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:38 Optimus-Prime kernel: [10041.390056] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.400053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.410053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.420048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.430048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.440048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.450047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.460047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.470047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.480048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.485050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:38 Optimus-Prime kernel: [10041.490052] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.500053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.510053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.520048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.530047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.540046] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.550048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.560048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.570047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.580046] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.585047] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:38 Optimus-Prime kernel: [10041.590045] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.600053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.610069] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.620069] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.630047] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.640051] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.650051] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.660049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.670049] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.680053] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.685054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:38 Optimus-Prime kernel: [10041.690055] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.700048] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.710051] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.720055] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.730055] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.740055] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.750054] #
Aug  3 17:00:38 Optimus-Prime kernel: [10041.760049] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.770034] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.780047] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.785049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:39 Optimus-Prime kernel: [10041.790050] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.800054] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.810020] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.820038] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.830032] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.840036] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.850043] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.860031] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.870050] #
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 5 -> 9 (reason 4)
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <warn> Activation (wlan0) failed for access point (Meades' Network)
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <info> Marking connection 'Auto Meades' Network' invalid.
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <warn> Activation (wlan0) failed.
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <warn> (wlan0): link timed out.
Aug  3 17:00:39 Optimus-Prime wpa_supplicant[1480]: Failed to initiate AP scan.
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <info> (wlan0): deactivating device (reason: 0).
Aug  3 17:00:39 Optimus-Prime NetworkManager[926]: <error> [1312405239.110114] [nm-device-wifi.c:1548] nm_device_wifi_set_mode(): (wlan0): error setting mode 2
Aug  3 17:00:39 Optimus-Prime kernel: [10041.880051] #
Aug  3 17:00:39 Optimus-Prime kernel: [10041.885055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:00:39 Optimus-Prime kernel: [10041.886056] NICLoadFirmware: MCU is not ready
Aug  3 17:00:39 Optimus-Prime kernel: [10041.886058] NICLoadFirmware failed, Status[=0x00000001]
Aug  3 17:00:39 Optimus-Prime kernel: [10041.886061] rt28xx Initialized fail!
andrew@Optimus-Prime:~$ sudo tail -n100 /var/log/syslog
Aug  3 17:05:54 Optimus-Prime kernel: [10357.470028] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.480039] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.490031] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.500039] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.510027] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.520040] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.530035] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.540039] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.550027] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.560039] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.565044] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:54 Optimus-Prime kernel: [10357.570052] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.580044] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.590052] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.600049] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.610048] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.620048] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.630048] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.640053] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.650051] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.660045] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.665048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:54 Optimus-Prime kernel: [10357.670052] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.680047] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.690048] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.700048] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.710037] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.720048] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.730047] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.740053] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.750053] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.760054] #
Aug  3 17:05:54 Optimus-Prime kernel: [10357.765056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:55 Optimus-Prime kernel: [10357.770065] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.780049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.790049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.800049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.810066] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.820049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.830049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.840050] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.850049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.860049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.865050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:55 Optimus-Prime kernel: [10357.870058] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.880040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.890039] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.900042] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.910048] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.920047] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.930049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.940052] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.950041] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.960038] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.965040] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:55 Optimus-Prime kernel: [10357.970063] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.980040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10357.990049] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.000060] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.010039] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.020064] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.030053] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.040047] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.050046] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.060040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.065043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:55 Optimus-Prime kernel: [10358.070030] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.080039] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.090040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.100040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.110030] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.120040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.130040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.140046] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.150034] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.160041] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.165043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:55 Optimus-Prime kernel: [10358.170040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.180039] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.190040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.200039] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.210053] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.220040] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.230029] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.240061] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.250045] #
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 5 -> 9 (reason 4)
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <warn> Activation (wlan0) failed for access point (Meades' Network)
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <info> Marking connection 'Auto Meades' Network' invalid.
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <warn> Activation (wlan0) failed.
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  3 17:05:55 Optimus-Prime wpa_supplicant[1480]: Failed to initiate AP scan.
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <info> (wlan0): deactivating device (reason: 0).
Aug  3 17:05:55 Optimus-Prime NetworkManager[926]: <error> [1312405555.489793] [nm-device-wifi.c:1548] nm_device_wifi_set_mode(): (wlan0): error setting mode 2
Aug  3 17:05:55 Optimus-Prime kernel: [10358.260046] #
Aug  3 17:05:55 Optimus-Prime kernel: [10358.265048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  3 17:05:55 Optimus-Prime kernel: [10358.266049] NICLoadFirmware: MCU is not ready
Aug  3 17:05:55 Optimus-Prime kernel: [10358.266051] NICLoadFirmware failed, Status[=0x00000001]
Aug  3 17:05:55 Optimus-Prime kernel: [10358.266053] rt28xx Initialized fail!
andrew@Optimus-Prime:~$ 

```


And here are the commands you asked for:

```
andrew@Optimus-Prime:~$ sudo iwlist scan
[sudo] password for andrew: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:1F:44:D8
                    Protocol:802.11b/g/n
                    ESSID:"Meades' Network"
                    Mode:Managed
                    Channel:6
                    Quality:65/100  Signal level:-64 dBm  Noise level:-71 dBm
                    Encryption key:on
                    Bit Rates:130 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 90:E6:BA:7D:5D:1A
                    Protocol:802.11b/g
                    ESSID:"WLAN"
                    Mode:Managed
                    Channel:11
                    Quality:10/100  Signal level:-86 dBm  Noise level:-71 dBm
                    Encryption key:off
                    Bit Rates:11 Mb/s


```

```
andrew@Optimus-Prime:~$ uname -a
Linux Optimus-Prime 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
andrew@Optimus-Prime:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        E0:CB:4E:FD:02:07

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto Meades' Network] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connected
  Default:           yes
  HW Address:        00:1E:E5:E0:4E:03

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    lindasnetwork:   Infra, 00:23:69:A5:8D:03, Freq 2437 MHz, Rate 0 Mb/s, Strength 3 WEP
    WiredPente-guest:Infra, 98:FC:11:54:09:6D, Freq 2437 MHz, Rate 16 Mb/s, Strength 3
    WiredPente:      Infra, 98:FC:11:54:09:6B, Freq 2437 MHz, Rate 16 Mb/s, Strength 3 WPA WPA2
    *Meades' Network:Infra, 00:1D:7E:1F:44:D8, Freq 2437 MHz, Rate 2 Mb/s, Strength 91 WPA2
    WLAN:            Infra, 90:E6:BA:7D:5D:1A, Freq 2462 MHz, Rate 0 Mb/s, Strength 10

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



```

```
andrew@Optimus-Prime:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: e0:cb:4e:fd:02:07
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:fbec0000-fbefffff ioport:dc00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:1e:e5:e0:4e:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.1.102 multicast=yes wireless=Ralink STA

```

Nothing for lspci -nn | grep 0280

```
andrew@Optimus-Prime:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1737:0071 Linksys WUSB600N Dual-Band Wireless-N USB Network Adapter
Bus 001 Device 003: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 002: ID 04a9:1716 Canon, Inc. MP460 Composite
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think that is all.  Thanks for your interest!

---

### Post by wildmanne39 on 2011-08-03
Hi, is Meades the network you are connecting too?

If so try changing the wpa2 setting to wpa/wpa2 and see if that helps.
Thank you

---

### Post by wildmanne39 on 2011-08-03
Hi, also run these two commands please:
```
lsmod | grep rt2
```
```
dmesg | grep rt2
```
Thank you

---

### Post by Ameades on 2011-08-03
Yes that is the network.  I have changed the wireless from WPA2/AES to WPA Personal/AES.

Do you think booting back into an older kernel might help solve this?

And I have to run to hockey now for a couple hours so I wont be able to post any scripts until I return.  

Thanks!

---

### Post by wildmanne39 on 2011-08-03
Hi, it might, you can boot to an older kernel and see.

---

### Post by Ameades on 2011-08-03
Good hockey game, my team won 7-2 and I got you a goal.

```
andrew@Optimus-Prime:~$ lsmod | grep rt2
rt2870sta             450556  1 
crc_ccitt              12667  1 rt2870sta
andrew@Optimus-Prime:~$ dmesg | grep rt2
[   10.327608] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   10.330936] usbcore: registered new interface driver rt2870
[   17.250872] <==== rt28xx_init, Status=0
[   18.629832] <==== rt28xx_init, Status=0
[  191.700225] <==== rt28xx_init, Status=0

```

But I have to head out for the night now and wont be able to respond until tomorrow afternoon after work.  Hopefully well keep at it and figure this out!

---

### Post by wildmanne39 on 2011-08-03
Hi, I am glad you won your game.

The output from the last two commands looks good.

Since you change your setting to wpa/aes did your connection improve?

---

### Post by Ameades on 2011-08-04
Yes, so far since I changed the encryption the problem hasn't reoccured.  I hope that was the solution, otherwise I'll be posting again. 

Thanks for you help!

---

### Post by wildmanne39 on 2011-08-04
Hi, your welcome!would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by Ameades on 2011-08-04
It appears that wasn't the solution.  I could taste the irony as a minute after I marked the thread solved, the wireless froze again.  

What other things can we look at as a solution?

---

### Post by wildmanne39 on 2011-08-04
Hi, are you sure the internet froze? or did the everything freeze?

---

### Post by Ameades on 2011-08-04
It was the exact same problem as before, the wireless stops working.  I then open up the terminal to try and run some commands to see what it up, and then that starts hanging.  If I try and reconnect or anything from the drop down wireless menu from it wont work.  The wireless symbol in the panel shows its connected for awhile and then shows that it is disconnected, ie there is a long delay before showing that the internet is down.

---

### Post by wildmanne39 on 2011-08-04
Hi, right after it freezes run this command again so we can see what it says now.
```
sudo tail -n100 /var/log/syslog
```
I think it is a problem with your system freezing and not the wireless freezing.

When I researched it, there were many people with the wireless issue and what I told you to do fixed there problem, but they did not have the system freezing.

Did you do a clean install or did you upgrade to 11.04?

---

### Post by Basher101 on 2011-08-04
Hey, do you have another access point you can connect to (if you havent already tried) and see if you have the same issues there?

---

### Post by Ameades on 2011-08-04
Here is the syslog.  The problem started at 22:32:05 to 07.  It might have started a bit earlier even.  If you need any more info I will collect another as soon as it happens again.

I do not have any other wireless in the area that I can connect to.  Non of the other computers connected to the network wirelessly are having any problems at all

I upgraded to 11.04 from 10.10.  I hope I don't have to do a clean re-install but if that is what it takes then I might have to.

```
andrew@Optimus-Prime:~$ sudo tail -n350 /var/log/syslog
Aug  4 22:32:05 Optimus-Prime modem-manager[963]: <info>  Loaded plugin AnyData
Aug  4 22:32:05 Optimus-Prime modem-manager[963]: <info>  Loaded plugin MotoC
Aug  4 22:32:05 Optimus-Prime modem-manager[963]: <info>  Loaded plugin Novatel
Aug  4 22:32:05 Optimus-Prime modem-manager[963]: <info>  Loaded plugin Huawei
Aug  4 22:32:05 Optimus-Prime modem-manager[963]: <info>  Loaded plugin Option High-Speed
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: init!
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: update_system_hostname
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPluginIfupdown: management mode: unmanaged
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth0, iface: eth0)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-6/net/wlan0, iface: wlan0)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-6/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: end _init.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    Ifupdown: get unmanaged devices count: 0
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: (39895392) ... get_connections.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: (39895392) ... get_connections (managed=false): return empty list.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]:    Ifupdown: get unmanaged devices count: 0
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> Networking is enabled by state file
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): carrier is OFF
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): new Ethernet device (driver: 'ATL1E' ifindex: 2)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): now managed
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): bringing up device.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): preparing device.
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (eth0): deactivating device (reason: 2).
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0/net/eth0
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <error> [1312511525.460232] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (wlan0): new 802.11 WiFi device (driver: 'usb' ifindex: 3)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (wlan0): now managed
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Aug  4 22:32:05 Optimus-Prime NetworkManager[944]: <info> (wlan0): bringing up device.
Aug  4 22:32:05 Optimus-Prime gdm-binary[935]: WARNING: Unable to find users: no seat-id found
Aug  4 22:32:05 Optimus-Prime kernel: [   19.600576] ATL1E 0000:02:00.0: irq 45 for MSI/MSI-X
Aug  4 22:32:05 Optimus-Prime kernel: [   19.600997] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  4 22:32:05 Optimus-Prime kernel: [   19.680169] #
Aug  4 22:32:05 Optimus-Prime kernel: [   19.710049] #
Aug  4 22:32:05 Optimus-Prime kernel: [   19.750159] #
Aug  4 22:32:05 Optimus-Prime kernel: [   19.770032] #
Aug  4 22:32:05 Optimus-Prime kernel: [   19.800153] #
Aug  4 22:32:05 Optimus-Prime kernel: [   19.830152] #
Aug  4 22:32:05 Optimus-Prime kernel: [   19.848908] type=1400 audit(1312511525.688:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1047 comm="apparmor_parser"
Aug  4 22:32:05 Optimus-Prime kernel: [   19.849145] type=1400 audit(1312511525.688:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1048 comm="apparmor_parser"
Aug  4 22:32:05 Optimus-Prime kernel: [   19.935380] <-- RTMPAllocTxRxRingMemory, Status=0
Aug  4 22:32:05 Optimus-Prime kernel: [   19.937634] -->RTUSBVenderReset
Aug  4 22:32:05 Optimus-Prime kernel: [   19.937756] <--RTUSBVenderReset
Aug  4 22:32:05 Optimus-Prime init: apport pre-start process (1111) terminated with status 1
Aug  4 22:32:05 Optimus-Prime cron[1121]: (CRON) INFO (pidfile fd = 3)
Aug  4 22:32:05 Optimus-Prime acpid: starting up with proc fs
Aug  4 22:32:05 Optimus-Prime anacron[1164]: Anacron 2.3 started on 2011-08-04
Aug  4 22:32:05 Optimus-Prime cron[1170]: (CRON) STARTUP (fork ok)
Aug  4 22:32:05 Optimus-Prime cron[1170]: (CRON) INFO (Running @reboot jobs)
Aug  4 22:32:05 Optimus-Prime acpid: 34 rules loaded
Aug  4 22:32:05 Optimus-Prime acpid: waiting for events: event logging is off
Aug  4 22:32:05 Optimus-Prime init: apport post-stop process (1163) terminated with status 1
Aug  4 22:32:05 Optimus-Prime udev-configure-printer: add /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.1
Aug  4 22:32:05 Optimus-Prime anacron[1164]: Normal exit (0 jobs run)
Aug  4 22:32:05 Optimus-Prime udev-configure-printer: add /devices/pci0000:00/0000:00:12.2/usb1/1-2/1-2:1.1/usb/lp0
Aug  4 22:32:05 Optimus-Prime kernel: [   20.000127] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.020123] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.040122] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.050120] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.060119] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.068142] vboxdrv: Found 6 processor cores.
Aug  4 22:32:05 Optimus-Prime kernel: [   20.068400] vboxdrv: fAsync=0 offMin=0x4e6 offMax=0x5ed4
Aug  4 22:32:05 Optimus-Prime kernel: [   20.068447] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug  4 22:32:05 Optimus-Prime kernel: [   20.068449] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
Aug  4 22:32:05 Optimus-Prime kernel: [   20.070118] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.080116] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.090115] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.100114] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.110112] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.120110] #
Aug  4 22:32:05 Optimus-Prime kernel: [   20.130109] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.140108] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.150107] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.157042] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Aug  4 22:32:06 Optimus-Prime kernel: [   20.160105] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.170104] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.180103] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.190101] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.200101] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.210103] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.213250] fglrx_pci 0000:01:00.0: irq 46 for MSI/MSI-X
Aug  4 22:32:06 Optimus-Prime kernel: [   20.213719] [fglrx] Firegl kernel thread PID: 1300
Aug  4 22:32:06 Optimus-Prime kernel: [   20.213810] [fglrx] Firegl kernel thread PID: 1301
Aug  4 22:32:06 Optimus-Prime kernel: [   20.213856] [fglrx] Firegl kernel thread PID: 1302
Aug  4 22:32:06 Optimus-Prime kernel: [   20.214099] [fglrx] IRQ 46 Enabled
Aug  4 22:32:06 Optimus-Prime kernel: [   20.220098] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.230096] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.240095] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.250094] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.260092] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.270090] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.280089] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.290088] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.300089] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.320084] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.330082] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.340206] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.350084] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.360081] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.370081] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.380076] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.390075] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.400081] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.410074] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.413340] [fglrx] Gart USWC size:1240 M.
Aug  4 22:32:06 Optimus-Prime kernel: [   20.413342] [fglrx] Gart cacheable size:491 M.
Aug  4 22:32:06 Optimus-Prime kernel: [   20.413346] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Aug  4 22:32:06 Optimus-Prime kernel: [   20.413348] [fglrx] Reserved FB block: Unshared offset:f91f000, size:3e1000 
Aug  4 22:32:06 Optimus-Prime kernel: [   20.413350] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Aug  4 22:32:06 Optimus-Prime kernel: [   20.430070] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.450067] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.458565] 1. Phy Mode = 0
Aug  4 22:32:06 Optimus-Prime kernel: [   20.458567] 2. Phy Mode = 0
Aug  4 22:32:06 Optimus-Prime kernel: [   20.460071] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.470191] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.480190] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.490191] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.500188] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.510187] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.520185] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.530182] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.535959] RTMPSetPhyMode: channel is out of range, use first channel=1 
Aug  4 22:32:06 Optimus-Prime kernel: [   20.540182] #
Aug  4 22:32:06 Optimus-Prime kernel: [   20.550681] 3. Phy Mode = 0
Aug  4 22:32:06 Optimus-Prime kernel: [   20.555557] MCS Set = 00 00 00 00 00
Aug  4 22:32:06 Optimus-Prime NetworkManager[944]: <info> (wlan0): preparing device.
Aug  4 22:32:06 Optimus-Prime NetworkManager[944]: <info> (wlan0): deactivating device (reason: 2).
Aug  4 22:32:06 Optimus-Prime avahi-daemon[942]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21e:e5ff:fee0:4e03.
Aug  4 22:32:06 Optimus-Prime avahi-daemon[942]: New relevant interface wlan0.IPv6 for mDNS.
Aug  4 22:32:06 Optimus-Prime avahi-daemon[942]: Network interface enumeration completed.
Aug  4 22:32:06 Optimus-Prime avahi-daemon[942]: Registering new address record for fe80::21e:e5ff:fee0:4e03 on wlan0.*.
Aug  4 22:32:06 Optimus-Prime avahi-daemon[942]: Registering HINFO record with values 'X86_64'/'LINUX'.
Aug  4 22:32:06 Optimus-Prime kernel: [   20.564804] <==== rt28xx_init, Status=0
Aug  4 22:32:06 Optimus-Prime kernel: [   20.566426] 0x1300 = 000a4260
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: URI matches without serial number: usb://Canon/MP460
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: No serial number URI matches so using those without
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:12.2/usb1/1-2
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: URI of print queue: usb://Canon/MP460, normalized: canon mp460
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: URI of detected printer: usb://Canon/MP460, normalized: canon mp460
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: Queue ipp://localhost:631/printers/Canon-MP460 has matching device URI
Aug  4 22:32:06 Optimus-Prime udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:12.2/usb1/1-2
Aug  4 22:32:06 Optimus-Prime gdm-session-worker[1336]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug  4 22:32:07 Optimus-Prime avahi-daemon[942]: Interface wlan0.IPv6 no longer relevant for mDNS.
Aug  4 22:32:07 Optimus-Prime avahi-daemon[942]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::21e:e5ff:fee0:4e03.
Aug  4 22:32:07 Optimus-Prime avahi-daemon[942]: Withdrawing address record for fe80::21e:e5ff:fee0:4e03 on wlan0.
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
Aug  4 22:32:07 Optimus-Prime kernel: [   21.236801] ---> RTMPFreeTxRxRingMemory
Aug  4 22:32:07 Optimus-Prime kernel: [   21.236822] <--- RTMPFreeTxRxRingMemory
Aug  4 22:32:07 Optimus-Prime kernel: [   21.240087] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.290080] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.300079] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.360074] #
Aug  4 22:32:07 Optimus-Prime anacron[1457]: Anacron 2.3 started on 2011-08-04
Aug  4 22:32:07 Optimus-Prime anacron[1457]: Normal exit (0 jobs run)
Aug  4 22:32:07 Optimus-Prime kernel: [   21.529804] <-- RTMPAllocTxRxRingMemory, Status=0
Aug  4 22:32:07 Optimus-Prime kernel: [   21.530809] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.537794] -->RTUSBVenderReset
Aug  4 22:32:07 Optimus-Prime kernel: [   21.537919] <--RTUSBVenderReset
Aug  4 22:32:07 Optimus-Prime kernel: [   21.570042] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.580041] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.590040] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.600038] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.610037] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.630034] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.650031] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.670029] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.690026] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.710028] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.740144] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.770021] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.880124] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.890124] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.898872] 1. Phy Mode = 0
Aug  4 22:32:07 Optimus-Prime kernel: [   21.898874] 2. Phy Mode = 0
Aug  4 22:32:07 Optimus-Prime kernel: [   21.900125] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.910121] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.920122] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.930119] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.940119] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.950118] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.960117] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.970116] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.980114] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.990110] #
Aug  4 22:32:07 Optimus-Prime kernel: [   21.996610] 3. Phy Mode = 0
Aug  4 22:32:07 Optimus-Prime kernel: [   22.000110] #
Aug  4 22:32:07 Optimus-Prime kernel: [   22.007242] MCS Set = 00 00 00 00 00
Aug  4 22:32:07 Optimus-Prime kernel: [   22.010109] #
Aug  4 22:32:07 Optimus-Prime kernel: [   22.020108] #
Aug  4 22:32:07 Optimus-Prime kernel: [   22.028107] <==== rt28xx_init, Status=0
Aug  4 22:32:07 Optimus-Prime kernel: [   22.029730] 0x1300 = 000a4260
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <info> modem-manager is now available
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <info> Trying to start the supplicant...
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant manager state:  down -> idle
Aug  4 22:32:07 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
Aug  4 22:32:08 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant interface state:  starting -> ready
Aug  4 22:32:08 Optimus-Prime kernel: [   22.210083] #
Aug  4 22:32:09 Optimus-Prime kernel: [   23.474120] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Successfully called chroot.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Successfully dropped privileges.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Successfully limited resources.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Running.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Canary thread running.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Watchdog thread running.
Aug  4 22:32:09 Optimus-Prime avahi-daemon[942]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::21e:e5ff:fee0:4e03.
Aug  4 22:32:09 Optimus-Prime avahi-daemon[942]: New relevant interface wlan0.IPv6 for mDNS.
Aug  4 22:32:09 Optimus-Prime avahi-daemon[942]: Registering new address record for fe80::21e:e5ff:fee0:4e03 on wlan0.*.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Successfully made thread 1540 of process 1540 (n/a) owned by '1000' high priority at nice level -11.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Supervising 1 threads of 1 processes of 1 users.
Aug  4 22:32:09 Optimus-Prime init: plymouth-stop pre-start process (1586) terminated with status 1
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Successfully made thread 1600 of process 1540 (n/a) owned by '1000' RT at priority 5.
Aug  4 22:32:09 Optimus-Prime rtkit-daemon[1542]: Supervising 2 threads of 1 processes of 1 users.
Aug  4 22:32:10 Optimus-Prime rtkit-daemon[1542]: Successfully made thread 1609 of process 1540 (n/a) owned by '1000' RT at priority 5.
Aug  4 22:32:10 Optimus-Prime rtkit-daemon[1542]: Supervising 3 threads of 1 processes of 1 users.
Aug  4 22:32:10 Optimus-Prime anacron[1747]: Anacron 2.3 started on 2011-08-04
Aug  4 22:32:10 Optimus-Prime anacron[1747]: Normal exit (0 jobs run)
Aug  4 22:32:10 Optimus-Prime kernel: [   25.107511] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
Aug  4 22:32:11 Optimus-Prime rtkit-daemon[1542]: Successfully made thread 1876 of process 1540 (n/a) owned by '1000' RT at priority 5.
Aug  4 22:32:11 Optimus-Prime rtkit-daemon[1542]: Supervising 4 threads of 1 processes of 1 users.
Aug  4 22:32:11 Optimus-Prime rtkit-daemon[1542]: Successfully made thread 1877 of process 1540 (n/a) owned by '1000' RT at priority 5.
Aug  4 22:32:11 Optimus-Prime rtkit-daemon[1542]: Supervising 5 threads of 1 processes of 1 users.
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) starting connection 'Auto Meades' Network'
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  4 22:32:13 Optimus-Prime kernel: [   27.208080] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 333
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0/wireless): access point 'Auto Meades' Network' has security, but secrets are required.
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Aug  4 22:32:13 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  4 22:32:13 Optimus-Prime kernel: [   27.900079] #
Aug  4 22:32:14 Optimus-Prime kernel: [   28.910069] #
Aug  4 22:32:15 Optimus-Prime kernel: [   29.910061] #
Aug  4 22:32:16 Optimus-Prime kernel: [   30.910053] #
Aug  4 22:32:17 Optimus-Prime kernel: [   31.910042] #
Aug  4 22:32:18 Optimus-Prime kernel: [   32.720042] wlan0: no IPv6 routers present
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0/wireless): connection 'Auto Meades' Network' has security, and secrets exist.  No new secrets needed.
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Config: added 'ssid' value 'Meades' Network'
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Config: added 'scan_ssid' value '1'
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Config: added 'psk' value '<omitted>'
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> Config: set interface ap_scan to 1
Aug  4 22:32:18 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug  4 22:32:20 Optimus-Prime kernel: [   34.999979] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Aug  4 22:32:23 Optimus-Prime wpa_supplicant[1480]: Trying to associate with 00:1d:7e:1f:44:d8 (SSID='Meades' Network' freq=2437 MHz)
Aug  4 22:32:23 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug  4 22:32:23 Optimus-Prime kernel: [   37.870087] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 482
Aug  4 22:32:23 Optimus-Prime kernel: [   37.870347] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
Aug  4 22:32:23 Optimus-Prime wpa_supplicant[1480]: Associated with 00:1d:7e:1f:44:d8
Aug  4 22:32:23 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug  4 22:32:23 Optimus-Prime kernel: [   38.080097] #
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug  4 22:32:24 Optimus-Prime wpa_supplicant[1480]: WPA: Key negotiation completed with 00:1d:7e:1f:44:d8 [PTK=CCMP GTK=CCMP]
Aug  4 22:32:24 Optimus-Prime wpa_supplicant[1480]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:1f:44:d8 completed (auth) [id=0 id_str=]
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Meades' Network'.
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> dhclient started with pid 1926
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug  4 22:32:24 Optimus-Prime dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug  4 22:32:24 Optimus-Prime dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug  4 22:32:24 Optimus-Prime dhclient: All rights reserved.
Aug  4 22:32:24 Optimus-Prime dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug  4 22:32:24 Optimus-Prime dhclient: 
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug  4 22:32:24 Optimus-Prime dhclient: Listening on LPF/wlan0/00:1e:e5:e0:4e:03
Aug  4 22:32:24 Optimus-Prime dhclient: Sending on   LPF/wlan0/00:1e:e5:e0:4e:03
Aug  4 22:32:24 Optimus-Prime dhclient: Sending on   Socket/fallback
Aug  4 22:32:24 Optimus-Prime dhclient: DHCPREQUEST of 192.168.1.102 on wlan0 to 255.255.255.255 port 67
Aug  4 22:32:24 Optimus-Prime dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Aug  4 22:32:24 Optimus-Prime dhclient: bound to 192.168.1.102 -- renewal in 34853 seconds.
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info>   address 192.168.1.102
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info>   prefix 24 (255.255.255.0)
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info>   gateway 192.168.1.1
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info>   hostname 'Optimus-Prime'
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info>   nameserver '192.168.1.1'
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Scheduling stage 5
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Done scheduling stage 5
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  4 22:32:24 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug  4 22:32:24 Optimus-Prime avahi-daemon[942]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.102.
Aug  4 22:32:24 Optimus-Prime avahi-daemon[942]: New relevant interface wlan0.IPv4 for mDNS.
Aug  4 22:32:24 Optimus-Prime avahi-daemon[942]: Registering new address record for 192.168.1.102 on wlan0.IPv4.
Aug  4 22:32:25 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug  4 22:32:25 Optimus-Prime NetworkManager[944]: <info> Policy set 'Auto Meades' Network' (wlan0) as default for IPv4 routing and DNS.
Aug  4 22:32:25 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) successful, device activated.
Aug  4 22:32:25 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  4 22:32:27 Optimus-Prime kernel: [   42.010074] #
Aug  4 22:32:32 Optimus-Prime kernel: [   47.002591] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 333
Aug  4 22:32:36 Optimus-Prime ntpdate[1973]: step time server 91.189.94.4 offset 0.547430 sec
Aug  4 22:33:08 Optimus-Prime kernel: [   82.010128] #
Aug  4 22:33:13 Optimus-Prime kernel: [   87.002953] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 333
Aug  4 22:33:42 Optimus-Prime kernel: [  116.230076] #
Aug  4 22:34:13 Optimus-Prime kernel: [  147.002474] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 623
Aug  4 22:35:33 Optimus-Prime kernel: [  227.009196] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 342
Aug  4 22:37:08 Optimus-Prime kernel: [  322.010077] #
Aug  4 22:37:13 Optimus-Prime kernel: [  327.002775] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 193
Aug  4 22:39:08 Optimus-Prime kernel: [  442.010113] #
Aug  4 22:39:08 Optimus-Prime kernel: [  442.020111] #
Aug  4 22:39:13 Optimus-Prime kernel: [  447.002443] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 482
Aug  4 22:41:13 Optimus-Prime kernel: [  567.007272] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 815
Aug  4 22:43:08 Optimus-Prime kernel: [  682.010060] #
Aug  4 22:43:13 Optimus-Prime kernel: [  687.002117] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 333
Aug  4 22:45:09 Optimus-Prime kernel: [  803.420035] #
Aug  4 22:45:13 Optimus-Prime kernel: [  807.002771] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 634
Aug  4 22:47:09 Optimus-Prime kernel: [  923.420072] #
Aug  4 22:47:13 Optimus-Prime kernel: [  927.002967] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 482
Aug  4 22:47:43 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  4 22:47:43 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  4 22:49:13 Optimus-Prime kernel: [ 1047.007055] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 333

```

---

### Post by wildmanne39 on 2011-08-04
Hi, there are new messages but the old one is not there so that part looks like it is fixed. I am going to do some research, it may take a while.

---

### Post by Ameades on 2011-08-04
Excellent, thank you.  That last syslog wasn't the best so as soon as it happens again I will collect a better one.  I do need to head to bed now though as I am up at 6am.

Please let me know your findings!

---

### Post by wildmanne39 on 2011-08-05
Hi, I found this bug report [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/686320](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/686320)
for this error 
> WiFi enabled by radio killswitch; enabled by state file

It says it is fixed in an updated network manager, so you might see if you can upgrade network manager.
Thank you

---

### Post by Ameades on 2011-08-08
I'm checking out that bug now.

How would I go about updating my network manager.

Also, here are a couple more syslogs, collected immediately after the internet stopped working.

```
[sudo] password for andrew: 
Aug  5 19:42:41 Optimus-Prime kernel: [76254.140045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.150046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.160045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.170046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.180045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.185056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.190039] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.200038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.210049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.220052] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.230050] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.240038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.250050] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.260054] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.270046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.280045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.285056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x132c
Aug  5 19:42:41 Optimus-Prime kernel: [76254.285058] 	Request Value=0x0004!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.290065] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.300046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.310039] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.320044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.330050] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.340049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.350046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.360045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.370042] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.380044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.385055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.390034] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.400033] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.410044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.420046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.430041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.440035] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.450031] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.460031] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.470049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.480041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.485052] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x132e
Aug  5 19:42:41 Optimus-Prime kernel: [76254.485056] 	Request Value=0x0000!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.490034] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.500031] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.510049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.520046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.530047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.540049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.550049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.560033] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.570078] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.580058] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.585066] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.590032] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.600037] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.610044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.620048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.630058] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.640068] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.650041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.660053] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.670047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.680055] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.685062] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x1328
Aug  5 19:42:41 Optimus-Prime kernel: [76254.685066] 	Request Value=0x0f0a!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.690037] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.700059] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.710047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.720058] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.730052] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.740044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.750042] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.760047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.770041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.780038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.785046] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.790025] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.800039] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.810047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.820043] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.830048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.840051] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.850044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.860048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.870044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.880046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.885057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x132a
Aug  5 19:42:41 Optimus-Prime kernel: [76254.885059] 	Request Value=0x0005!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.890038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.900040] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.910049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.920049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.930048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.940046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.950045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.960048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.970047] #
Aug  5 19:42:41 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  5 19:42:41 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  5 19:42:41 Optimus-Prime kernel: [76254.980061] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.985071] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
andrew@Optimus-Prime:~$ sudo tail -n400 /var/log/syslog
Aug  5 19:48:07 Optimus-Prime kernel: [76580.390063] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.400051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.410051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.420047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.430051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.440047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.450051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.460056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.470057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.480051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.485056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.490055] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.500051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.510047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.520051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.530047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.540051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.550051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.560056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.570057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.580050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.585053] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.590055] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.600051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.610051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.620051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.630048] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.640051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.650058] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.660057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.670056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.680051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.685053] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.690054] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.700051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.710051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.720051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.730053] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.740071] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.750057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.760060] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.770054] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.780052] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.785057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.790059] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.800053] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.810050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.820050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.830050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.840047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.850050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.860049] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.870048] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.881071] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.886076] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.890096] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.900065] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.910057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.920056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.930059] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.940056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.950048] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.960052] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.970056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.980051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.985055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76580.990051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.000047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.010052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.020047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.030052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.040054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.050046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.060054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.070052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.080043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.085046] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.090051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.100047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.110042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.120054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.130040] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.140055] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.150056] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.160051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.170050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.180037] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.185040] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.190050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.200049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.210050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.220050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.230050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.240050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.250050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.260047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.270051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.280050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.285052] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.290045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.300042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.310044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.320042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.330044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.340042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.350044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.360043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.370044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.380067] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.385069] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.390053] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.400048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.410041] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.420044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.430049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.440045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.450043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.460051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.470045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.480043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.485049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.490046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.500041] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.510039] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.520042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.530051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.540044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.550042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.560048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.570048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.580054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.585060] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.590046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.600044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.610042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.620044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.630043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.640042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.650042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.660048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.670048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.680043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.685048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.690045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.700042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.710044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.720044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.730046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.740030] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.750079] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.760050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.770048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.780049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.785056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.790050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.800050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.810046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.820050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.830050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.840049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.850050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.860046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.870052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.880046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.885050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.890081] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.900059] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.910063] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.920058] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.930056] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.940062] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.950073] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.960062] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.970062] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.980060] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.985067] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76581.990061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.000056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.010052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.020050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.030051] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.040057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.050051] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.060061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.070060] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.080052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.085055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.090056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.100051] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.110052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.120056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.130052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.140052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.150052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.160054] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.170052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.180052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.185055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.190056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.200052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.210058] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.220052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.230055] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.240062] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.250059] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.260060] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.270057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.280057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.285064] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.290061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.300057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.310068] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.320052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.330058] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.340057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.350057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.360057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.370052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.380057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.385062] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.390061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.400057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.410052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.420057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.430057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.440057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.450057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.460057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.470057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.480052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.485055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.490061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.500057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.510057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.520052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.530057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.540057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.550057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.560053] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.570041] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.580056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.585060] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.590064] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.600056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.610052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.620052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.630052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.640052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.650052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.660053] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.670048] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.680052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.685054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.690055] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.700052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.710052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.720052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.730059] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.740073] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.750050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.760052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.770049] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.780046] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.785049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.790054] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.800050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.810050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.820050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.830052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.840050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.850050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.860044] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.870036] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.880064] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.885076] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.890092] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.900052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.910060] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.920056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.930073] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.940062] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.950062] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.960058] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.970040] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.980063] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.985066] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76582.990075] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.000060] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.010056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.020057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.030058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.040058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.050058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.060054] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.070040] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.080042] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.085045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.090055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.100050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.110052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.120044] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.130035] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.140052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.150051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.160049] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.170040] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.180061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.185064] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.190064] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.200060] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.210049] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.220051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.230056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.240067] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.250052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.260058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.270062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.280052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.285055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.290062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.300057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.310052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.320048] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.330051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.340051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.350052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.360057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.370063] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.380052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.385054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.390061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.400057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.410051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.420051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.430062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.440058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.450052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.460056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.470062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.480051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.485054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.490061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.500057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.510051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.520051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.530051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.540051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.550052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.560057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.570063] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.580051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.585054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.590061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.600057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.610052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.620051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.630051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.640051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.650051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.660057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.670057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.680052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.685054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.690055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.700058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.710059] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.720052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.730052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.740056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.750051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.760055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.770055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.780059] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.785065] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.790062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.800055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.810055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.820050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.830049] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.840050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.850050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.860054] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.870055] #
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <error> [1312588090.888312] [nm-device-wifi.c:1548] nm_device_wifi_set_mode(): (wlan0): error setting mode 2
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) starting connection 'Auto Meades' Network'
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  disconnected -> inactive
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): bringing up device.
Aug  5 19:48:10 Optimus-Prime kernel: [76583.880076] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.885088] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.886090] NICLoadFirmware: MCU is not ready
Aug  5 19:48:10 Optimus-Prime kernel: [76583.886092] NICLoadFirmware failed, Status[=0x00000001]
Aug  5 19:48:10 Optimus-Prime kernel: [76583.886095] rt28xx Initialized fail!
```


And another 

```
Aug  8 12:00:17 Optimus-Prime kernel: [  840.660048] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.670049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.680048] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.690047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.700046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.705048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f0
Aug  8 12:00:17 Optimus-Prime kernel: [  840.705049] 	Request Value=0x2170!
Aug  8 12:00:17 Optimus-Prime kernel: [  840.710054] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.720045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.730049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.740050] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.750055] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.760049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.770049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.780049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.790049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.800049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.805050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f2
Aug  8 12:00:17 Optimus-Prime kernel: [  840.805052] 	Request Value=0x4b30!
Aug  8 12:00:17 Optimus-Prime kernel: [  840.810055] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.820049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.830049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.840043] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.850048] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.860047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.870045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.880045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.890046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.900047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.905048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f4
Aug  8 12:00:17 Optimus-Prime kernel: [  840.905050] 	Request Value=0xc206!
Aug  8 12:00:17 Optimus-Prime kernel: [  840.910051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.920047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.930045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.940046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.950053] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.960051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.970054] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.980049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.990049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.000047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.005049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f6
Aug  8 12:00:17 Optimus-Prime kernel: [  841.005051] 	Request Value=0xd26c!
Aug  8 12:00:17 Optimus-Prime kernel: [  841.010054] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.020058] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.030058] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.040046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.050051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.060051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.070050] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.080060] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.090061] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.100050] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.105051] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f8
Aug  8 12:00:17 Optimus-Prime kernel: [  841.105053] 	Request Value=0x806d!
Aug  8 12:00:17 Optimus-Prime kernel: [  841.110056] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.120049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.130049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.140051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.150049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.160049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.170049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.180049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.190049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.200049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.205050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33fa
Aug  8 12:00:18 Optimus-Prime kernel: [  841.205052] 	Request Value=0xe518!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.210054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.220043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.230050] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.240055] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.250040] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.260049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.270049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.280048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.290049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.300048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.305050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33fc
Aug  8 12:00:18 Optimus-Prime kernel: [  841.305051] 	Request Value=0x7025!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.310054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.320049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.330055] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.340049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.350049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.360043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.370093] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.380042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.390041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.400043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.405045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33fe
Aug  8 12:00:18 Optimus-Prime kernel: [  841.405046] 	Request Value=0x3003!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.410050] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.420043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.430041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.440041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.450041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.460043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.470042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.480043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.490043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.500040] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.505042] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3400
Aug  8 12:00:18 Optimus-Prime kernel: [  841.505043] 	Request Value=0x114c!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.510049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.520043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.530041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.540043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.550041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.560043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.570042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.580039] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.590041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.600038] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.605039] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3402
Aug  8 12:00:18 Optimus-Prime kernel: [  841.605040] 	Request Value=0x4cc2!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.610048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.620042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.630041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.640043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.650044] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.660045] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.670045] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.680050] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.690051] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.700040] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.705041] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3404
Aug  8 12:00:18 Optimus-Prime kernel: [  841.705042] 	Request Value=0x25e5!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.710053] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.720051] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.730047] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.740051] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.750063] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.760048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.770043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.780043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.790043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.800043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.805044] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3406
Aug  8 12:00:18 Optimus-Prime kernel: [  841.805046] 	Request Value=0x0570!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.810049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.820043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.830043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.840049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.850033] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.860049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.870049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.880045] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.890049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.900048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.905050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3408
Aug  8 12:00:18 Optimus-Prime kernel: [  841.905051] 	Request Value=0x2575!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.910054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.920049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.930049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.940049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.950049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.960049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.970041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.980049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.990054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.000041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.005043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x340a
Aug  8 12:00:18 Optimus-Prime kernel: [  842.005044] 	Request Value=0x8007!
Aug  8 12:00:18 Optimus-Prime kernel: [  842.010052] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.020043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.030043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.040043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.050043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.060043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.070043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.080066] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.090059] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.100037] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.105038] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x340c
Aug  8 12:00:18 Optimus-Prime kernel: [  842.105044] 	Request Value=0x1502!
Aug  8 12:00:18 Optimus-Prime kernel: [  842.110054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.120047] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.130049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.140049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.150047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.160049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.170047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.180045] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.190049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.200048] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.205050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x340e
Aug  8 12:00:19 Optimus-Prime kernel: [  842.205051] 	Request Value=0xd225!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.210052] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.220039] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.230033] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.240057] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.250062] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.260049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.270049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.280049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.290049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.300040] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.305042] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3410
Aug  8 12:00:19 Optimus-Prime kernel: [  842.305043] 	Request Value=0xd26c!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.310054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.320049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.330049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.340048] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.350041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.360055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.370049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.380049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.390047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.400049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.405050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3412
Aug  8 12:00:19 Optimus-Prime kernel: [  842.405051] 	Request Value=0xe56d!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.410054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.420049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.430049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.440047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.450049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.460049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.470054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.480040] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.490047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.500053] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.505063] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3414
Aug  8 12:00:19 Optimus-Prime kernel: [  842.505065] 	Request Value=0xb447!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.510050] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.520044] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.530041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.540041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.550041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.560092] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.570042] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.580043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.590043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.600043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.605045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3416
Aug  8 12:00:19 Optimus-Prime kernel: [  842.605046] 	Request Value=0x1409!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.610049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.620043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.630041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.640043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.650043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.660043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.670043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.680043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.690047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.700041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.705043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3418
Aug  8 12:00:19 Optimus-Prime kernel: [  842.705044] 	Request Value=0x44e5!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.710049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.720040] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.730038] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.740050] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.750046] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.760031] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.770048] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.780046] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.790067] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.800047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.805048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x341a
Aug  8 12:00:19 Optimus-Prime kernel: [  842.805049] 	Request Value=0xe320!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.810054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.820045] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.830049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.840059] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.850053] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.860043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.870049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.880046] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.890062] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.900056] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.905058] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x341c
Aug  8 12:00:19 Optimus-Prime kernel: [  842.905059] 	Request Value=0xe50b!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.910060] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.920059] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.930055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.940058] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.950054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.960054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.970054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.980054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.990054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.000054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.005056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x341e
Aug  8 12:00:19 Optimus-Prime kernel: [  843.005058] 	Request Value=0x643a!
Aug  8 12:00:19 Optimus-Prime kernel: [  843.010063] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.020051] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.030075] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.040070] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.050069] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.060055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.070055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.080054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.090069] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.100051] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.105053] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3420
Aug  8 12:00:19 Optimus-Prime kernel: [  843.105054] 	Request Value=0x6002!
Aug  8 12:00:19 Optimus-Prime kernel: [  843.110057] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.120052] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.130060] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.140051] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.150046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.160048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.170048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.180047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.190047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.200046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.205048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3422
Aug  8 12:00:20 Optimus-Prime kernel: [  843.205050] 	Request Value=0xe505!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.210051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.220042] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.230051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.240045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.250036] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.260048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.270047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.280047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.290046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.300047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.305048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3424
Aug  8 12:00:20 Optimus-Prime kernel: [  843.305050] 	Request Value=0xb43a!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.310052] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.320047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.330062] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.340053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.350047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.360047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.370047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.380045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.390047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.400047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.405048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3426
Aug  8 12:00:20 Optimus-Prime kernel: [  843.405049] 	Request Value=0x0403!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.410053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.420045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.430047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.440052] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.450050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.460047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.470050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.480044] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.490047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.500047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.505048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3428
Aug  8 12:00:20 Optimus-Prime kernel: [  843.505049] 	Request Value=0x6cc2!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.510052] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.520045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.530046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.540051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.550045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.560060] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.570056] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.580049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.590050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.600056] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.605057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x342a
Aug  8 12:00:20 Optimus-Prime kernel: [  843.605059] 	Request Value=0x6dd2!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.610046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.620032] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.630050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.640053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.650049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.660049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.670039] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.680033] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.690046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.700049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.705051] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x342c
Aug  8 12:00:20 Optimus-Prime kernel: [  843.705052] 	Request Value=0x7090!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.710055] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.720049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.730049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.740051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.750030] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.760042] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.770043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.780043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.790043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.800043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.805044] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x342e
Aug  8 12:00:20 Optimus-Prime kernel: [  843.805046] 	Request Value=0xe546!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.810049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.820043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.830043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.840046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.850037] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.860048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.870049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.880045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.890048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.900046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.905048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3430
Aug  8 12:00:20 Optimus-Prime kernel: [  843.905049] 	Request Value=0xf02d!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.910053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.920048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.930047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.940049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.950044] #
Aug  8 12:00:20 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  8 12:00:20 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  8 12:00:20 Optimus-Prime kernel: [  843.960058] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.970061] #

```

---

### Post by Ameades on 2011-08-08
I'm checking out that bug now.  The freezes seem to be happening more often now.

How would I go about updating my network manager.

Also, here are a couple more syslogs, collected immediately after the internet stopped working.

```
[sudo] password for andrew: 
Aug  5 19:42:41 Optimus-Prime kernel: [76254.140045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.150046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.160045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.170046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.180045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.185056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.190039] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.200038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.210049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.220052] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.230050] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.240038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.250050] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.260054] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.270046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.280045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.285056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x132c
Aug  5 19:42:41 Optimus-Prime kernel: [76254.285058] 	Request Value=0x0004!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.290065] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.300046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.310039] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.320044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.330050] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.340049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.350046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.360045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.370042] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.380044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.385055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.390034] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.400033] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.410044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.420046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.430041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.440035] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.450031] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.460031] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.470049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.480041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.485052] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x132e
Aug  5 19:42:41 Optimus-Prime kernel: [76254.485056] 	Request Value=0x0000!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.490034] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.500031] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.510049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.520046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.530047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.540049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.550049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.560033] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.570078] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.580058] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.585066] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.590032] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.600037] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.610044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.620048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.630058] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.640068] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.650041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.660053] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.670047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.680055] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.685062] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x1328
Aug  5 19:42:41 Optimus-Prime kernel: [76254.685066] 	Request Value=0x0f0a!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.690037] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.700059] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.710047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.720058] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.730052] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.740044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.750042] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.760047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.770041] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.780038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.785046] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
Aug  5 19:42:41 Optimus-Prime kernel: [76254.790025] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.800039] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.810047] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.820043] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.830048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.840051] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.850044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.860048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.870044] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.880046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.885057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x132a
Aug  5 19:42:41 Optimus-Prime kernel: [76254.885059] 	Request Value=0x0005!
Aug  5 19:42:41 Optimus-Prime kernel: [76254.890038] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.900040] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.910049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.920049] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.930048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.940046] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.950045] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.960048] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.970047] #
Aug  5 19:42:41 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  5 19:42:41 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  5 19:42:41 Optimus-Prime kernel: [76254.980061] #
Aug  5 19:42:41 Optimus-Prime kernel: [76254.985071] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x1718
andrew@Optimus-Prime:~$ sudo tail -n400 /var/log/syslog
Aug  5 19:48:07 Optimus-Prime kernel: [76580.390063] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.400051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.410051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.420047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.430051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.440047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.450051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.460056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.470057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.480051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.485056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.490055] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.500051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.510047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.520051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.530047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.540051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.550051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.560056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.570057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.580050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.585053] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.590055] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.600051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.610051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.620051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.630048] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.640051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.650058] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.660057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.670056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.680051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.685053] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.690054] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.700051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.710051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.720051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.730053] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.740071] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.750057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.760060] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.770054] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.780052] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.785057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.790059] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.800053] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.810050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.820050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.830050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.840047] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.850050] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.860049] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.870048] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.881071] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.886076] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:07 Optimus-Prime kernel: [76580.890096] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.900065] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.910057] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.920056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.930059] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.940056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.950048] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.960052] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.970056] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.980051] #
Aug  5 19:48:07 Optimus-Prime kernel: [76580.985055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76580.990051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.000047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.010052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.020047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.030052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.040054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.050046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.060054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.070052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.080043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.085046] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.090051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.100047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.110042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.120054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.130040] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.140055] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.150056] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.160051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.170050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.180037] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.185040] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.190050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.200049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.210050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.220050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.230050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.240050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.250050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.260047] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.270051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.280050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.285052] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.290045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.300042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.310044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.320042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.330044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.340042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.350044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.360043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.370044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.380067] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.385069] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.390053] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.400048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.410041] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.420044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.430049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.440045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.450043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.460051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.470045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.480043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.485049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.490046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.500041] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.510039] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.520042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.530051] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.540044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.550042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.560048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.570048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.580054] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.585060] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.590046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.600044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.610042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.620044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.630043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.640042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.650042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.660048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.670048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.680043] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.685048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.690045] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.700042] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.710044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.720044] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.730046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.740030] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.750079] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.760050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.770048] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.780049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.785056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.790050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.800050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.810046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.820050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.830050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.840049] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.850050] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.860046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.870052] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.880046] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.885050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:08 Optimus-Prime kernel: [76581.890081] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.900059] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.910063] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.920058] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.930056] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.940062] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.950073] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.960062] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.970062] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.980060] #
Aug  5 19:48:08 Optimus-Prime kernel: [76581.985067] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76581.990061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.000056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.010052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.020050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.030051] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.040057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.050051] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.060061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.070060] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.080052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.085055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.090056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.100051] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.110052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.120056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.130052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.140052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.150052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.160054] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.170052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.180052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.185055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.190056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.200052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.210058] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.220052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.230055] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.240062] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.250059] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.260060] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.270057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.280057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.285064] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.290061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.300057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.310068] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.320052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.330058] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.340057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.350057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.360057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.370052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.380057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.385062] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.390061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.400057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.410052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.420057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.430057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.440057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.450057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.460057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.470057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.480052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.485055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.490061] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.500057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.510057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.520052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.530057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.540057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.550057] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.560053] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.570041] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.580056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.585060] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.590064] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.600056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.610052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.620052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.630052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.640052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.650052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.660053] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.670048] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.680052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.685054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.690055] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.700052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.710052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.720052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.730059] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.740073] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.750050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.760052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.770049] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.780046] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.785049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.790054] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.800050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.810050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.820050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.830052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.840050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.850050] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.860044] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.870036] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.880064] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.885076] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:09 Optimus-Prime kernel: [76582.890092] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.900052] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.910060] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.920056] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.930073] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.940062] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.950062] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.960058] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.970040] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.980063] #
Aug  5 19:48:09 Optimus-Prime kernel: [76582.985066] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76582.990075] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.000060] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.010056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.020057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.030058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.040058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.050058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.060054] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.070040] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.080042] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.085045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.090055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.100050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.110052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.120044] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.130035] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.140052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.150051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.160049] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.170040] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.180061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.185064] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.190064] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.200060] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.210049] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.220051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.230056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.240067] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.250052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.260058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.270062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.280052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.285055] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.290062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.300057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.310052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.320048] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.330051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.340051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.350052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.360057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.370063] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.380052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.385054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.390061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.400057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.410051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.420051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.430062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.440058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.450052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.460056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.470062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.480051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.485054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.490061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.500057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.510051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.520051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.530051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.540051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.550052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.560057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.570063] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.580051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.585054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.590061] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.600057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.610052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.620051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.630051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.640051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.650051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.660057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.670057] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.680052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.685054] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.690055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.700058] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.710059] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.720052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.730052] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.740056] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.750051] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.760055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.770055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.780059] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.785065] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.790062] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.800055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.810055] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.820050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.830049] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.840050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.850050] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.860054] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.870055] #
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <error> [1312588090.888312] [nm-device-wifi.c:1548] nm_device_wifi_set_mode(): (wlan0): error setting mode 2
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) starting connection 'Auto Meades' Network'
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): supplicant connection state:  disconnected -> inactive
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug  5 19:48:10 Optimus-Prime NetworkManager[944]: <info> (wlan0): bringing up device.
Aug  5 19:48:10 Optimus-Prime kernel: [76583.880076] #
Aug  5 19:48:10 Optimus-Prime kernel: [76583.885088] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=IN, Req=0x7, Index=0x400
Aug  5 19:48:10 Optimus-Prime kernel: [76583.886090] NICLoadFirmware: MCU is not ready
Aug  5 19:48:10 Optimus-Prime kernel: [76583.886092] NICLoadFirmware failed, Status[=0x00000001]
Aug  5 19:48:10 Optimus-Prime kernel: [76583.886095] rt28xx Initialized fail!
```


And another 

```
Aug  8 12:00:17 Optimus-Prime kernel: [  840.660048] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.670049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.680048] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.690047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.700046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.705048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f0
Aug  8 12:00:17 Optimus-Prime kernel: [  840.705049] 	Request Value=0x2170!
Aug  8 12:00:17 Optimus-Prime kernel: [  840.710054] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.720045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.730049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.740050] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.750055] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.760049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.770049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.780049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.790049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.800049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.805050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f2
Aug  8 12:00:17 Optimus-Prime kernel: [  840.805052] 	Request Value=0x4b30!
Aug  8 12:00:17 Optimus-Prime kernel: [  840.810055] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.820049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.830049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.840043] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.850048] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.860047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.870045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.880045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.890046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.900047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.905048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f4
Aug  8 12:00:17 Optimus-Prime kernel: [  840.905050] 	Request Value=0xc206!
Aug  8 12:00:17 Optimus-Prime kernel: [  840.910051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.920047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.930045] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.940046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.950053] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.960051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.970054] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.980049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  840.990049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.000047] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.005049] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f6
Aug  8 12:00:17 Optimus-Prime kernel: [  841.005051] 	Request Value=0xd26c!
Aug  8 12:00:17 Optimus-Prime kernel: [  841.010054] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.020058] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.030058] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.040046] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.050051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.060051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.070050] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.080060] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.090061] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.100050] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.105051] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33f8
Aug  8 12:00:17 Optimus-Prime kernel: [  841.105053] 	Request Value=0x806d!
Aug  8 12:00:17 Optimus-Prime kernel: [  841.110056] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.120049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.130049] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.140051] #
Aug  8 12:00:17 Optimus-Prime kernel: [  841.150049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.160049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.170049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.180049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.190049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.200049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.205050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33fa
Aug  8 12:00:18 Optimus-Prime kernel: [  841.205052] 	Request Value=0xe518!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.210054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.220043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.230050] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.240055] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.250040] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.260049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.270049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.280048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.290049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.300048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.305050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33fc
Aug  8 12:00:18 Optimus-Prime kernel: [  841.305051] 	Request Value=0x7025!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.310054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.320049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.330055] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.340049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.350049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.360043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.370093] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.380042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.390041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.400043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.405045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x33fe
Aug  8 12:00:18 Optimus-Prime kernel: [  841.405046] 	Request Value=0x3003!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.410050] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.420043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.430041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.440041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.450041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.460043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.470042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.480043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.490043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.500040] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.505042] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3400
Aug  8 12:00:18 Optimus-Prime kernel: [  841.505043] 	Request Value=0x114c!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.510049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.520043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.530041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.540043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.550041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.560043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.570042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.580039] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.590041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.600038] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.605039] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3402
Aug  8 12:00:18 Optimus-Prime kernel: [  841.605040] 	Request Value=0x4cc2!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.610048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.620042] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.630041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.640043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.650044] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.660045] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.670045] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.680050] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.690051] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.700040] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.705041] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3404
Aug  8 12:00:18 Optimus-Prime kernel: [  841.705042] 	Request Value=0x25e5!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.710053] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.720051] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.730047] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.740051] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.750063] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.760048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.770043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.780043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.790043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.800043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.805044] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3406
Aug  8 12:00:18 Optimus-Prime kernel: [  841.805046] 	Request Value=0x0570!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.810049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.820043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.830043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.840049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.850033] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.860049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.870049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.880045] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.890049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.900048] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.905050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3408
Aug  8 12:00:18 Optimus-Prime kernel: [  841.905051] 	Request Value=0x2575!
Aug  8 12:00:18 Optimus-Prime kernel: [  841.910054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.920049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.930049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.940049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.950049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.960049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.970041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.980049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  841.990054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.000041] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.005043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x340a
Aug  8 12:00:18 Optimus-Prime kernel: [  842.005044] 	Request Value=0x8007!
Aug  8 12:00:18 Optimus-Prime kernel: [  842.010052] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.020043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.030043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.040043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.050043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.060043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.070043] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.080066] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.090059] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.100037] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.105038] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x340c
Aug  8 12:00:18 Optimus-Prime kernel: [  842.105044] 	Request Value=0x1502!
Aug  8 12:00:18 Optimus-Prime kernel: [  842.110054] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.120047] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.130049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.140049] #
Aug  8 12:00:18 Optimus-Prime kernel: [  842.150047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.160049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.170047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.180045] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.190049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.200048] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.205050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x340e
Aug  8 12:00:19 Optimus-Prime kernel: [  842.205051] 	Request Value=0xd225!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.210052] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.220039] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.230033] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.240057] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.250062] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.260049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.270049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.280049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.290049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.300040] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.305042] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3410
Aug  8 12:00:19 Optimus-Prime kernel: [  842.305043] 	Request Value=0xd26c!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.310054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.320049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.330049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.340048] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.350041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.360055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.370049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.380049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.390047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.400049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.405050] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3412
Aug  8 12:00:19 Optimus-Prime kernel: [  842.405051] 	Request Value=0xe56d!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.410054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.420049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.430049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.440047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.450049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.460049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.470054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.480040] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.490047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.500053] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.505063] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3414
Aug  8 12:00:19 Optimus-Prime kernel: [  842.505065] 	Request Value=0xb447!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.510050] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.520044] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.530041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.540041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.550041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.560092] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.570042] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.580043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.590043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.600043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.605045] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3416
Aug  8 12:00:19 Optimus-Prime kernel: [  842.605046] 	Request Value=0x1409!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.610049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.620043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.630041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.640043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.650043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.660043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.670043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.680043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.690047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.700041] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.705043] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3418
Aug  8 12:00:19 Optimus-Prime kernel: [  842.705044] 	Request Value=0x44e5!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.710049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.720040] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.730038] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.740050] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.750046] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.760031] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.770048] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.780046] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.790067] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.800047] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.805048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x341a
Aug  8 12:00:19 Optimus-Prime kernel: [  842.805049] 	Request Value=0xe320!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.810054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.820045] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.830049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.840059] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.850053] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.860043] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.870049] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.880046] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.890062] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.900056] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.905058] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x341c
Aug  8 12:00:19 Optimus-Prime kernel: [  842.905059] 	Request Value=0xe50b!
Aug  8 12:00:19 Optimus-Prime kernel: [  842.910060] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.920059] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.930055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.940058] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.950054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.960054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.970054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.980054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  842.990054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.000054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.005056] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x341e
Aug  8 12:00:19 Optimus-Prime kernel: [  843.005058] 	Request Value=0x643a!
Aug  8 12:00:19 Optimus-Prime kernel: [  843.010063] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.020051] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.030075] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.040070] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.050069] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.060055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.070055] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.080054] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.090069] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.100051] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.105053] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3420
Aug  8 12:00:19 Optimus-Prime kernel: [  843.105054] 	Request Value=0x6002!
Aug  8 12:00:19 Optimus-Prime kernel: [  843.110057] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.120052] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.130060] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.140051] #
Aug  8 12:00:19 Optimus-Prime kernel: [  843.150046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.160048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.170048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.180047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.190047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.200046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.205048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3422
Aug  8 12:00:20 Optimus-Prime kernel: [  843.205050] 	Request Value=0xe505!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.210051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.220042] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.230051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.240045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.250036] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.260048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.270047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.280047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.290046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.300047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.305048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3424
Aug  8 12:00:20 Optimus-Prime kernel: [  843.305050] 	Request Value=0xb43a!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.310052] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.320047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.330062] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.340053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.350047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.360047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.370047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.380045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.390047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.400047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.405048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3426
Aug  8 12:00:20 Optimus-Prime kernel: [  843.405049] 	Request Value=0x0403!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.410053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.420045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.430047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.440052] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.450050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.460047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.470050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.480044] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.490047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.500047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.505048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3428
Aug  8 12:00:20 Optimus-Prime kernel: [  843.505049] 	Request Value=0x6cc2!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.510052] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.520045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.530046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.540051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.550045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.560060] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.570056] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.580049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.590050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.600056] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.605057] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x342a
Aug  8 12:00:20 Optimus-Prime kernel: [  843.605059] 	Request Value=0x6dd2!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.610046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.620032] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.630050] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.640053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.650049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.660049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.670039] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.680033] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.690046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.700049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.705051] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x342c
Aug  8 12:00:20 Optimus-Prime kernel: [  843.705052] 	Request Value=0x7090!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.710055] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.720049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.730049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.740051] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.750030] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.760042] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.770043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.780043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.790043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.800043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.805044] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x342e
Aug  8 12:00:20 Optimus-Prime kernel: [  843.805046] 	Request Value=0xe546!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.810049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.820043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.830043] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.840046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.850037] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.860048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.870049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.880045] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.890048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.900046] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.905048] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Index=0x3430
Aug  8 12:00:20 Optimus-Prime kernel: [  843.905049] 	Request Value=0xf02d!
Aug  8 12:00:20 Optimus-Prime kernel: [  843.910053] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.920048] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.930047] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.940049] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.950044] #
Aug  8 12:00:20 Optimus-Prime sudo: pam_sm_authenticate: Called
Aug  8 12:00:20 Optimus-Prime sudo: pam_sm_authenticate: username = [andrew]
Aug  8 12:00:20 Optimus-Prime kernel: [  843.960058] #
Aug  8 12:00:20 Optimus-Prime kernel: [  843.970061] #

```

---

### Post by wildmanne39 on 2011-08-08
Hi, try this please:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add these three lines:
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```
save and close gedit.
Then reboot, and see if it is better.

Open synaptic and click on network manager and see if there is an update for it,if so install it.
Thank you

---

### Post by Ameades on 2011-08-09
I have tried black listing the modules.  It did not work.  The freezes are happening more often now, I would say at least once an hour.  If this keeps it up I think I am just going to have to do a fresh install.

Do you have any more ideas?  Thanks

---

### Post by wildmanne39 on 2011-08-09
Hi, not at the moment, I am running a high fever, I asked an expert to help out while I am sick so he will probably pop in tonight or tomorrow.

I am sorry I have not been able to resolve this issue.
Thank you

---

### Post by Ameades on 2011-08-09
No worries.  Thanks for your help.  Hope you start feeling better!

---

### Post by Ameades on 2011-08-10
Okay I have run out of options.  I have attached another two syslogs.  I blacklisted rt2870sta and then modprobe'd it in the first log, and then I tried to restart network-manager in the second.

Can anyone please take a look and help me out.  Otherwise I am going to have to do a clean install tonight because I cannot have my computer freezing every hour.

The second syslog is 18MB so here is dropbox link: [URL="http://dl.dropbox.com/u/6575523/Large%20Syslog%20File"]http://dl.dropbox.com/u/6575523/Large%20Syslog%20File
[/URL]

Thanks.

```
Aug 10 18:08:19 Optimus-Prime kernel: [  233.283867] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
Aug 10 18:08:19 Optimus-Prime kernel: [  233.288927] rtusb init --->
Aug 10 18:08:19 Optimus-Prime kernel: [  233.289046] === pAd = ffffc900148e7000, size = 502256 ===
Aug 10 18:08:19 Optimus-Prime kernel: [  233.289048] <-- RTMPAllocAdapterBlock, Status=0
Aug 10 18:08:19 Optimus-Prime kernel: [  233.289704] usbcore: registered new interface driver rt2870
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-6/net/wlan0, iface: wlan0)
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.2/usb1/1-6/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <error> [1313014099.132803] [nm-device-wifi.c:3100] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <info> (wlan0): new 802.11 WiFi device (driver: 'usb' ifindex: 4)
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <info> (wlan0): now managed
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Aug 10 18:08:19 Optimus-Prime NetworkManager[972]: <info> (wlan0): bringing up device.
Aug 10 18:08:19 Optimus-Prime kernel: [  233.490148] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.520144] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.599015] <-- RTMPAllocTxRxRingMemory, Status=0
Aug 10 18:08:19 Optimus-Prime kernel: [  233.601259] -->RTUSBVenderReset
Aug 10 18:08:19 Optimus-Prime kernel: [  233.601383] <--RTUSBVenderReset
Aug 10 18:08:19 Optimus-Prime kernel: [  233.670124] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.680124] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.690123] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.700122] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.710120] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.720118] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.730117] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.740116] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.750115] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.760113] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.770112] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.780111] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.790109] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.800108] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.810106] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.820105] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.830104] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.840102] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.850101] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.860100] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.870099] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.880097] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.890096] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.900095] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.910093] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.920092] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.930090] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.940089] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.950088] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.960087] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.970086] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.980084] #
Aug 10 18:08:19 Optimus-Prime kernel: [  233.990082] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.000081] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.010080] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.020079] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.030077] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.040076] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.050075] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.060073] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.070072] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.080070] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.090069] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.100068] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.110067] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.120065] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.130064] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.140062] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.150061] #
Aug 10 18:08:19 Optimus-Prime kernel: [  234.159433] 1. Phy Mode = 0
Aug 10 18:08:19 Optimus-Prime kernel: [  234.159435] 2. Phy Mode = 0
Aug 10 18:08:20 Optimus-Prime kernel: [  234.160060] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.170059] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.180058] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.190057] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.200186] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.210054] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.220053] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.230052] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.236684] RTMPSetPhyMode: channel is out of range, use first channel=1 
Aug 10 18:08:20 Optimus-Prime kernel: [  234.240055] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.250050] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.257172] 3. Phy Mode = 0
Aug 10 18:08:20 Optimus-Prime kernel: [  234.260179] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.267796] MCS Set = 00 00 00 00 00
Aug 10 18:08:20 Optimus-Prime kernel: [  234.270051] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.280043] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.288421] <==== rt28xx_init, Status=0
Aug 10 18:08:20 Optimus-Prime NetworkManager[972]: <info> (wlan0): preparing device.
Aug 10 18:08:20 Optimus-Prime NetworkManager[972]: <info> (wlan0): deactivating device (reason: 2).
Aug 10 18:08:20 Optimus-Prime kernel: [  234.290063] 0x1300 = 000a4200
Aug 10 18:08:20 Optimus-Prime NetworkManager[972]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
Aug 10 18:08:20 Optimus-Prime kernel: [  234.866533] ---> RTMPFreeTxRxRingMemory
Aug 10 18:08:20 Optimus-Prime kernel: [  234.866550] <--- RTMPFreeTxRxRingMemory
Aug 10 18:08:20 Optimus-Prime kernel: [  234.870091] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.880090] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.890091] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.900085] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.910085] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.920084] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.930085] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.940081] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.950081] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.960081] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.970077] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.980077] #
Aug 10 18:08:20 Optimus-Prime kernel: [  234.990077] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.000073] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.010072] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.020087] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.030069] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.040068] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.060065] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.080062] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.100060] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.120057] #
Aug 10 18:08:20 Optimus-Prime kernel: [  235.140054] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.160052] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.180049] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.200048] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.220048] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.240048] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.260038] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.280046] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.306445] <-- RTMPAllocTxRxRingMemory, Status=0
Aug 10 18:08:21 Optimus-Prime kernel: [  235.308659] -->RTUSBVenderReset
Aug 10 18:08:21 Optimus-Prime kernel: [  235.308784] <--RTUSBVenderReset
Aug 10 18:08:21 Optimus-Prime kernel: [  235.320154] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.360025] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.540125] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.550125] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.560124] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.570122] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.580120] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.590120] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.600118] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.610119] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.630114] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.640113] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.650112] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.660110] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.669732] 1. Phy Mode = 0
Aug 10 18:08:21 Optimus-Prime kernel: [  235.669734] 2. Phy Mode = 0
Aug 10 18:08:21 Optimus-Prime kernel: [  235.670110] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.680107] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.690108] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.700109] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.710103] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.720103] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.730101] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.740100] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.750100] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.760099] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.767595] 3. Phy Mode = 0
Aug 10 18:08:21 Optimus-Prime kernel: [  235.770095] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.778219] MCS Set = 00 00 00 00 00
Aug 10 18:08:21 Optimus-Prime kernel: [  235.780093] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.790093] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.798843] <==== rt28xx_init, Status=0
Aug 10 18:08:21 Optimus-Prime kernel: [  235.800091] #
Aug 10 18:08:21 Optimus-Prime kernel: [  235.805590] 0x1300 = 000a4200
Aug 10 18:08:21 Optimus-Prime NetworkManager[972]: <info> (wlan0): supplicant interface state:  starting -> ready
Aug 10 18:08:21 Optimus-Prime NetworkManager[972]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Aug 10 18:08:21 Optimus-Prime kernel: [  235.900079] #
Aug 10 18:08:26 Optimus-Prime kernel: [  241.004661] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 482
Aug 10 18:08:27 Optimus-Prime kernel: [  241.640062] #
Aug 10 18:08:28 Optimus-Prime kernel: [  242.640054] #
Aug 10 18:08:29 Optimus-Prime kernel: [  243.640046] #
Aug 10 18:08:30 Optimus-Prime kernel: [  244.640037] #
Aug 10 18:08:31 Optimus-Prime kernel: [  245.640030] #
Aug 10 18:08:32 Optimus-Prime kernel: [  246.680014] wlan0: no IPv6 routers present
Aug 10 18:08:35 Optimus-Prime kernel: [  249.640119] #
Aug 10 18:08:35 Optimus-Prime kernel: [  249.650119] #
Aug 10 18:08:36 Optimus-Prime kernel: [  250.640112] #
Aug 10 18:08:37 Optimus-Prime kernel: [  251.650102] #
Aug 10 18:08:38 Optimus-Prime kernel: [  252.650094] #
Aug 10 18:08:39 Optimus-Prime kernel: [  253.650086] #
Aug 10 18:08:40 Optimus-Prime kernel: [  254.650077] #
Aug 10 18:08:41 Optimus-Prime kernel: [  255.650069] #
Aug 10 18:08:41 Optimus-Prime kernel: [  255.660070] #
Aug 10 18:08:42 Optimus-Prime kernel: [  256.650060] #
Aug 10 18:08:46 Optimus-Prime kernel: [  261.009075] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 333
Aug 10 18:08:49 Optimus-Prime kernel: [  263.650126] #
Aug 10 18:08:50 Optimus-Prime kernel: [  264.650117] #
Aug 10 18:08:51 Optimus-Prime kernel: [  265.650110] #
Aug 10 18:08:52 Optimus-Prime kernel: [  266.650102] #
Aug 10 18:08:53 Optimus-Prime kernel: [  267.650093] #
Aug 10 18:08:53 Optimus-Prime kernel: [  267.660093] #
Aug 10 18:08:55 Optimus-Prime kernel: [  269.650077] #
Aug 10 18:08:56 Optimus-Prime kernel: [  270.650068] #
Aug 10 18:08:57 Optimus-Prime kernel: [  271.650060] #
Aug 10 18:08:58 Optimus-Prime kernel: [  272.650052] #
Aug 10 18:08:59 Optimus-Prime kernel: [  273.650044] #
Aug 10 18:09:00 Optimus-Prime kernel: [  274.650036] #
Aug 10 18:09:00 Optimus-Prime wpa_supplicant[1063]: No network configuration found for the current AP
Aug 10 18:09:00 Optimus-Prime wpa_supplicant[1063]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Aug 10 18:09:00 Optimus-Prime kernel: [  274.710027] #
Aug 10 18:09:00 Optimus-Prime wpa_supplicant[1063]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Aug 10 18:09:01 Optimus-Prime wpa_supplicant[1063]: last message repeated 3 times
Aug 10 18:09:01 Optimus-Prime kernel: [  275.260081] #
Aug 10 18:09:01 Optimus-Prime kernel: [  275.270077] #

```

---

### Post by Ameades on 2011-08-11
Unfortunately I could not wait any longer and had to do a clean install.  The problem is no longer an issue.

---

