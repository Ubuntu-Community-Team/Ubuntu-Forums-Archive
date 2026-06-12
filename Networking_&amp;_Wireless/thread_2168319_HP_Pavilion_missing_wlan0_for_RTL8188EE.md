---
title: "HP Pavilion missing wlan0 for RTL8188EE"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by ukoda on 2013-08-17
I have a Chinese HP Pavilion 15-e006ax (E3A81PA#AB2) laptop which is having trouble with many things After installing Mint 15 / Unbuntu 13.04.  I would like to resolve the WiFi so I can stop tripping over network cables.  After install there was no wlan0 and no loaded WiFi modules.  The HP website Windows 8 drivers infers it has either Ralink 802.11 or Qualcomm Atheros AR9000, but physical inspection shows the module is actually a PCI Realtek RTL8188EE.  This is backed up by lshw which shows an unclaimed Realtek network device at pci:1.
```

hp-pavilion
    description: Notebook
    product: HP Pavilion 15 Notebook PC (E3A81PA#AB2)
    vendor: Hewlett-Packard
    version: 0885100000305B10000600100
    serial: 5CD3256PPD
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP S=PAV sku=E3A81PA#AB2 uuid=35434433-3235-3650-5044-A45D366DF484
  *-core
       description: Motherboard
       product: 1983
       vendor: Hewlett-Packard
       physical id: 0
       version: 01.11
       serial: PDQKH048J4U0AF
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.03
          date: 04/09/2013
          size: 1MiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: Empty
             slot: Bottom-Slot 1(top)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1L16BC4R1-B1HS
             vendor: A-DATA Technology
             physical id: 1
             serial: 000047AD
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: AMD A8-5550M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 26
          bus info: cpu@0
          version: AMD A8-5550M APU with Radeon(tm) HD Graphics
          serial: NotSupport
          slot: Socket FT1
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core arat cpb hw_pstate npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold bmi1 cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 27
             slot: L1 Cache
             size: 192KiB
             capacity: 192KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 28
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display
             description: VGA compatible controller
             product: Richland [Radeon HD 8550G]
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:47 memory:d0000000-dfffffff ioport:5000(size=256) memory:f0400000-f043ffff
        *-multimedia:0
             description: Audio device
             product: Trinity HDMI Audio Controller
             vendor: Advanced Micro Devices [AMD] nee ATI
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:f0444000-f0447fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:f0300000-f03fffff ioport:e0000000(size=268435456)
           *-display UNCLAIMED
                description: Display controller
                product: Sun [Radeon HD 8600M Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:e0000000-efffffff memory:f0300000-f033ffff ioport:4000(size=256) memory:f0340000-f035ffff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 10h-1fh) Processor Root Port
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:f0200000-f02fffff
           *-network UNCLAIMED
                description: Network controller
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:3000(size=256) memory:f0200000-f0203fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:f0448000-f0449fff
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:46 ioport:5118(size=8) ioport:5124(size=4) ioport:5110(size=8) ioport:5120(size=4) ioport:5100(size=16) memory:f044e000-f044e7ff
        *-usb:1
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f044d000-f044dfff
        *-usb:2
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f044c000-f044c0ff
        *-usb:3
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f044b000-f044bfff
        *-usb:4
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:f044a000-f044a0ff
        *-serial UNCLAIMED
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 16
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:f0440000-f0443fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
        *-pci:3
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f0100000-f01fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:48 memory:f0100000-f0100fff
        *-pci:4
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:f0000000-f00fffff ioport:f0500000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 07
                serial: a4:5d:36:6d:f4:84
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=10.11.1.124 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:49 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff memory:f0500000-f050ffff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
          vendor: Advanced Micro Devices [AMD]
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
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Advanced Micro Devices [AMD]
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
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: DXT0
             serial: S19HNEAD515018Y
             size: 111GiB (120GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=e11e3666-7722-4f34-a3ef-fc58fd3b03fd sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: a861-bddb
                size: 93MiB
                capacity: 93MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 68c1c34a-7fd7-4939-bb88-5486116c2e8f
                size: 108GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-07-16 01:35:02 filesystem=ext4 lastmountpoint=/ modified=2013-08-17 19:02:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-08-17 19:02:48 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: f76dc0ab-6327-4ac7-a297-1290cf5b9248
                size: 3292MiB
                capacity: 3292MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GU70N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: U703
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: PI06047
       vendor: 11-85
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V
```

My research suggests that the correct driver is rtlwifi which I have loaded with modprobe and added to /etc/modules.  lsmod out shows it as in use.
```
Module                  Size  Used by
snd_hda_codec_realtek    78399  1 
snd_hda_codec_hdmi     36913  1 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
dm_multipath           22843  0 
scsi_dh                14843  1 dm_multipath
ghash_clmulni_intel    13259  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
uvcvideo               80847  0 
microcode              22881  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
rtsx_pci_ms            13011  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
memstick               16554  1 rtsx_pci_ms
videodev              129260  2 uvcvideo,videobuf2_core
psmouse                95870  0 
k10temp                13126  0 
i2c_piix4              13266  0 
joydev                 17377  0 
serio_raw              13215  0 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
parport_pc             28152  0 
bnep                   18036  2 
rfcomm                 42641  0 
ppdev                  17073  0 
bluetooth             228619  10 bnep,rfcomm
mac_hid                13205  0 
rtlwifi                79673  0 
mac80211              606457  1 rtlwifi
binfmt_misc            17500  1 
cfg80211              510937  2 mac80211,rtlwifi
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
nls_iso8859_1          12713  1 
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
rtsx_pci_sdmmc         17475  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67446  0 
radeon                937749  2 
ahci                   25731  3 
i2c_algo_bit           13413  1 radeon
libahci                31364  1 ahci
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
wmi                    19070  1 hp_wmi
drm                   286313  4 ttm,drm_kms_helper,radeon
video                  19390  0 
```

However iwconfig only shows eth0 and lo.  The output from dmesg is.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=68c1c34a-7fd7-4939-bb88-5486116c2e8f ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006e000-0x000000000006ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000085fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000086000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009a734fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009a735000-0x000000009af35fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009af36000-0x000000009f5aefff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f5af000-0x000000009fabefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009fabf000-0x000000009fbbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009fbbf000-0x000000009fbfefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009fbff000-0x000000009fbfffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009fc00000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed80fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000012effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0x9fbfe000  ACPI 2.0=0x9fbfe014  SMBIOS=0x9fabef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006e000) (0MB)
[    0.000000] efi: mem02: type=10, attr=0xf, range=[0x000000000006e000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000086000) (0MB)
[    0.000000] efi: mem04: type=0, attr=0xf, range=[0x0000000000086000-0x0000000000088000) (0MB)
[    0.000000] efi: mem05: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001445000) (19MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000001445000-0x0000000002000000) (11MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003345000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000003345000-0x000000003430c000) (783MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x000000003430c000-0x000000003617e000) (30MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x000000003617e000-0x0000000071026000) (942MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000071026000-0x0000000097fb0000) (623MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x0000000097fb0000-0x0000000097fd0000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000097fd0000-0x000000009a51b000) (37MB)
[    0.000000] efi: mem15: type=4, attr=0xf, range=[0x000000009a51b000-0x000000009a735000) (2MB)
[    0.000000] efi: mem16: type=0, attr=0xf, range=[0x000000009a735000-0x000000009af36000) (8MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x000000009af36000-0x000000009afac000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x000000009afac000-0x000000009b191000) (1MB)
[    0.000000] efi: mem19: type=1, attr=0xf, range=[0x000000009b191000-0x000000009b1af000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x000000009b1af000-0x000000009c6e6000) (21MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x000000009c6e6000-0x000000009cf68000) (8MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x000000009cf68000-0x000000009d25f000) (2MB)
[    0.000000] efi: mem23: type=2, attr=0xf, range=[0x000000009d25f000-0x000000009d269000) (0MB)
[    0.000000] efi: mem24: type=4, attr=0xf, range=[0x000000009d269000-0x000000009d26b000) (0MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x000000009d26b000-0x000000009d26d000) (0MB)
[    0.000000] efi: mem26: type=4, attr=0xf, range=[0x000000009d26d000-0x000000009d394000) (1MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x000000009d394000-0x000000009d39c000) (0MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x000000009d39c000-0x000000009d3a8000) (0MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x000000009d3a8000-0x000000009d3aa000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x000000009d3aa000-0x000000009d3d6000) (0MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x000000009d3d6000-0x000000009d3da000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x000000009d3da000-0x000000009d525000) (1MB)
[    0.000000] efi: mem33: type=3, attr=0xf, range=[0x000000009d525000-0x000000009d526000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x000000009d526000-0x000000009d552000) (0MB)
[    0.000000] efi: mem35: type=3, attr=0xf, range=[0x000000009d552000-0x000000009d553000) (0MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x000000009d553000-0x000000009d554000) (0MB)
[    0.000000] efi: mem37: type=3, attr=0xf, range=[0x000000009d554000-0x000000009d555000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x000000009d555000-0x000000009d557000) (0MB)
[    0.000000] efi: mem39: type=3, attr=0xf, range=[0x000000009d557000-0x000000009d55a000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x000000009d55a000-0x000000009d55c000) (0MB)
[    0.000000] efi: mem41: type=3, attr=0xf, range=[0x000000009d55c000-0x000000009d55e000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x000000009d55e000-0x000000009d561000) (0MB)
[    0.000000] efi: mem43: type=3, attr=0xf, range=[0x000000009d561000-0x000000009d562000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x000000009d562000-0x000000009d563000) (0MB)
[    0.000000] efi: mem45: type=3, attr=0xf, range=[0x000000009d563000-0x000000009d566000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x000000009d566000-0x000000009d568000) (0MB)
[    0.000000] efi: mem47: type=3, attr=0xf, range=[0x000000009d568000-0x000000009d5c3000) (0MB)
[    0.000000] efi: mem48: type=4, attr=0xf, range=[0x000000009d5c3000-0x000000009d5cb000) (0MB)
[    0.000000] efi: mem49: type=3, attr=0xf, range=[0x000000009d5cb000-0x000000009d5d1000) (0MB)
[    0.000000] efi: mem50: type=4, attr=0xf, range=[0x000000009d5d1000-0x000000009d5de000) (0MB)
[    0.000000] efi: mem51: type=7, attr=0xf, range=[0x000000009d5de000-0x000000009d5e3000) (0MB)
[    0.000000] efi: mem52: type=4, attr=0xf, range=[0x000000009d5e3000-0x000000009d614000) (0MB)
[    0.000000] efi: mem53: type=7, attr=0xf, range=[0x000000009d614000-0x000000009d615000) (0MB)
[    0.000000] efi: mem54: type=4, attr=0xf, range=[0x000000009d615000-0x000000009d63e000) (0MB)
[    0.000000] efi: mem55: type=7, attr=0xf, range=[0x000000009d63e000-0x000000009d640000) (0MB)
[    0.000000] efi: mem56: type=4, attr=0xf, range=[0x000000009d640000-0x000000009d648000) (0MB)
[    0.000000] efi: mem57: type=7, attr=0xf, range=[0x000000009d648000-0x000000009d649000) (0MB)
[    0.000000] efi: mem58: type=4, attr=0xf, range=[0x000000009d649000-0x000000009d668000) (0MB)
[    0.000000] efi: mem59: type=3, attr=0xf, range=[0x000000009d668000-0x000000009d669000) (0MB)
[    0.000000] efi: mem60: type=4, attr=0xf, range=[0x000000009d669000-0x000000009f1af000) (27MB)
[    0.000000] efi: mem61: type=3, attr=0xf, range=[0x000000009f1af000-0x000000009f5af000) (4MB)
[    0.000000] efi: mem62: type=5, attr=0x800000000000000f, range=[0x000000009f5af000-0x000000009f7af000) (2MB)
[    0.000000] efi: mem63: type=6, attr=0x800000000000000f, range=[0x000000009f7af000-0x000000009f9bf000) (2MB)
[    0.000000] efi: mem64: type=0, attr=0xf, range=[0x000000009f9bf000-0x000000009fabf000) (1MB)
[    0.000000] efi: mem65: type=10, attr=0xf, range=[0x000000009fabf000-0x000000009fbbf000) (1MB)
[    0.000000] efi: mem66: type=9, attr=0xf, range=[0x000000009fbbf000-0x000000009fbff000) (0MB)
[    0.000000] efi: mem67: type=4, attr=0xf, range=[0x000000009fbff000-0x000000009fc00000) (0MB)
[    0.000000] efi: mem68: type=7, attr=0xf, range=[0x0000000100000000-0x000000012f000000) (752MB)
[    0.000000] efi: mem69: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem70: type=0, attr=0x0, range=[0x000000009fc00000-0x00000000d0000000) (772MB)
[    0.000000] efi: mem71: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem72: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem73: type=11, attr=0x8000000000000001, range=[0x00000000fec10000-0x00000000fec11000) (0MB)
[    0.000000] efi: mem74: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
[    0.000000] efi: mem75: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem76: type=11, attr=0x8000000000000000, range=[0x00000000ffc00000-0x0000000100000000) (4MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion 15 Notebook PC/1983, BIOS F.03 04/09/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x12f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 00009FBBD000 mask FFFFFFFFF000 uncachable
[    0.000000]   3 base 0000FFC00000 mask FFFFFFC00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000012f000000 aka 4848M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9fc00 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff88000007c000] 7c000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x9fbfffff]
[    0.000000]  [mem 0x00000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x9fbfffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x9fbfffff @ [mem 0x1fffe000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x12effffff]
[    0.000000]  [mem 0x100000000-0x12effffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x12effffff @ [mem 0x9d63e000-0x9d63ffff]
[    0.000000] RAMDISK: [mem 0x3430c000-0x3617dfff]
[    0.000000] ACPI: RSDP 000000009fbfe014 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 000000009fbfe120 000A4 (v01 HPQOEM SLIC-MPC 00000001 HP   01000013)
[    0.000000] ACPI: FACP 000000009fbfc000 0010C (v05 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: DSDT 000000009fbe7000 108CE (v01 HPQOEM 1983     F0000000 ACPI 00040000)
[    0.000000] ACPI: FACS 000000009fb7a000 00040
[    0.000000] ACPI: UEFI 000000009fbfd000 00236 (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: HPET 000000009fbfb000 00038 (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: APIC 000000009fbfa000 00084 (v03 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: MCFG 000000009fbf9000 0003C (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: ASF! 000000009fbf8000 000A5 (v32 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: BOOT 000000009fbe6000 00028 (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: SLIC 000000009fbe5000 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: WDRT 000000009fbe4000 00047 (v01 HPQOEM 1983     00000000 HP   00040000)
[    0.000000] ACPI: WDAT 000000009fbe3000 001AC (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: FPDT 000000009fbe1000 00044 (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: MSDM 000000009fbe0000 00055 (v03 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: SSDT 000000009fbdf000 009F8 (v01 HPQOEM 1983     00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 000000009fbdd000 01F6E (v02 HPQOEM 1983     00000001 ACPI 00040000)
[    0.000000] ACPI: VFCT 000000009fbd7000 05084 (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: BGRT 000000009fbd6000 00038 (v01 HPQOEM 1983     00000001 HP   00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000012effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x12effffff]
[    0.000000]   NODE_DATA [mem 0x12effb000-0x12effffff]
[    0.000000]  [ffffea0000000000-ffffea0004bfffff] PMD -> [ffff88012b200000-ffff88012e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x12effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0006dfff]
[    0.000000]   node   0: [mem 0x00070000-0x00085fff]
[    0.000000]   node   0: [mem 0x00100000-0x9a734fff]
[    0.000000]   node   0: [mem 0x9af36000-0x9f5aefff]
[    0.000000]   node   0: [mem 0x9fbff000-0x9fbfffff]
[    0.000000]   node   0: [mem 0x100000000-0x12effffff]
[    0.000000] On node 0 totalpages: 843043
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 7 pages reserved
[    0.000000]   DMA zone: 3885 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10103 pages used for memmap
[    0.000000]   DMA32 zone: 636472 pages, LIFO batch:31
[    0.000000]   Normal zone: 3008 pages used for memmap
[    0.000000]   Normal zone: 189504 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000006e000 - 0000000000070000
[    0.000000] PM: Registered nosave memory: 0000000000086000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000009a735000 - 000000009af36000
[    0.000000] PM: Registered nosave memory: 000000009f5af000 - 000000009fabf000
[    0.000000] PM: Registered nosave memory: 000000009fabf000 - 000000009fbbf000
[    0.000000] PM: Registered nosave memory: 000000009fbbf000 - 000000009fbff000
[    0.000000] PM: Registered nosave memory: 000000009fc00000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
[    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed80000
[    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed81000
[    0.000000] PM: Registered nosave memory: 00000000fed81000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] e820: [mem 0xd0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88012ec00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 829861
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=68c1c34a-7fd7-4939-bb88-5486116c2e8f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 8c000000
[    0.000000] PM: Registered nosave memory: 000000008c000000 - 0000000090000000
[    0.000000] Memory: 3092392k/4964352k available (7006k kernel code, 1592180k absent, 279780k reserved, 6238k data, 992k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 13631488 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2095.979 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4191.95 BogoMIPS (lpj=8383916)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.006447] Security Framework initialized
[    0.006457] AppArmor: AppArmor initialized
[    0.006458] Yama: becoming mindful.
[    0.006781] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.008037] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008676] Mount-cache hash table entries: 256
[    0.008862] Initializing cgroup subsys cpuacct
[    0.008865] Initializing cgroup subsys memory
[    0.008874] Initializing cgroup subsys devices
[    0.008875] Initializing cgroup subsys freezer
[    0.008877] Initializing cgroup subsys blkio
[    0.008878] Initializing cgroup subsys perf_event
[    0.008881] Initializing cgroup subsys hugetlb
[    0.008905] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.008909] tseg: 009fc00000
[    0.008911] CPU: Physical Processor ID: 0
[    0.008912] CPU: Processor Core ID: 0
[    0.008914] mce: CPU supports 7 MCE banks
[    0.008928] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.008928] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.008928] tlb_flushall_shift: 5
[    0.009043] Freeing SMP alternatives: 24k freed
[    0.010751] ACPI: Core revision 20121018
[    0.021727] ftrace: allocating 26689 entries in 105 pages
[    0.032185] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071836] smpboot: CPU0: AMD A8-5550M APU with Radeon(tm) HD Graphics (fam: 15, model: 13, stepping: 01)
[    0.176037] Performance Events: 
[    0.176039] perf: AMD core performance counters detected
[    0.176042] AMD PMU driver.
[    0.176045] ... version:                0
[    0.176046] ... bit width:              48
[    0.176047] ... generic registers:      6
[    0.176048] ... value mask:             0000ffffffffffff
[    0.176049] ... max period:             00007fffffffffff
[    0.176050] ... fixed-purpose events:   0
[    0.176051] ... event mask:             000000000000003f
[    0.177143] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.188204] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.217919] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.177230] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.231019] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.233166] Brought up 4 CPUs
[    0.233169] smpboot: Total of 4 processors activated (16767.83 BogoMIPS)
[    0.234170] devtmpfs: initialized
[    0.235282] EVM: security.selinux
[    0.235283] EVM: security.SMACK64
[    0.235285] EVM: security.capability
[    0.235465] PM: Registering ACPI NVS region [mem 0x0006e000-0x0006ffff] (8192 bytes)
[    0.235467] PM: Registering ACPI NVS region [mem 0x9fabf000-0x9fbbefff] (1048576 bytes)
[    0.236427] regulator-dummy: no parameters
[    0.236478] NET: Registered protocol family 16
[    0.236814] ACPI: bus type pci registered
[    0.236941] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.236944] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.242449] PCI: Using configuration type 1 for base access
[    0.243637] bio: create slab <bio-0> at 0
[    0.243749] ACPI: Added _OSI(Module Device)
[    0.243751] ACPI: Added _OSI(Processor Device)
[    0.243753] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.243757] ACPI: Added _OSI(Processor Aggregator Device)
[    0.246329] ACPI: EC: Look up EC in DSDT
[    0.248943] ACPI: Executed 1 blocks of module-level executable AML code
[    0.254001] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.346027] ACPI: Interpreter enabled
[    0.346034] ACPI: (supports S0 S3 S4 S5)
[    0.346066] ACPI: Using IOAPIC for interrupt routing
[    0.752467] ACPI: EC: GPE = 0x5, I/O: command/status = 0x66, data = 0x62
[    0.752637] ACPI: No dock devices found.
[    0.752643] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.752743] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.752745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.753217] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.753242] PCI host bridge to bus 0000:00
[    0.753245] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.753247] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.753249] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.753251] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.753253] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.753255] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.753256] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.753258] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.753260] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.753262] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.753263] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.753265] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.753267] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.753268] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.753270] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.753272] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.753273] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xf7ffffff]
[    0.753275] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    0.753277] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    0.753285] pci 0000:00:00.0: [1022:1410] type 00 class 0x060000
[    0.753371] pci 0000:00:01.0: [1002:990d] type 00 class 0x030000
[    0.753379] pci 0000:00:01.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.753385] pci 0000:00:01.0: reg 14: [io  0x5000-0x50ff]
[    0.753390] pci 0000:00:01.0: reg 18: [mem 0xf0400000-0xf043ffff]
[    0.753427] pci 0000:00:01.0: supports D1 D2
[    0.753441] pci 0000:00:01.1: [1002:9902] type 00 class 0x040300
[    0.753449] pci 0000:00:01.1: reg 10: [mem 0xf0444000-0xf0447fff]
[    0.753491] pci 0000:00:01.1: supports D1 D2
[    0.753509] pci 0000:00:02.0: [1022:1412] type 01 class 0x060400
[    0.753552] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.753616] pci 0000:00:04.0: [1022:1414] type 01 class 0x060400
[    0.753661] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.753776] pci 0000:00:10.0: [1022:7814] type 00 class 0x0c0330
[    0.753801] pci 0000:00:10.0: reg 10: [mem 0xf0448000-0xf0449fff 64bit]
[    0.753909] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.753952] pci 0000:00:11.0: [1022:7804] type 00 class 0x010601
[    0.753972] pci 0000:00:11.0: reg 10: [io  0x5118-0x511f]
[    0.753983] pci 0000:00:11.0: reg 14: [io  0x5124-0x5127]
[    0.753993] pci 0000:00:11.0: reg 18: [io  0x5110-0x5117]
[    0.754003] pci 0000:00:11.0: reg 1c: [io  0x5120-0x5123]
[    0.754014] pci 0000:00:11.0: reg 20: [io  0x5100-0x510f]
[    0.754024] pci 0000:00:11.0: reg 24: [mem 0xf044e000-0xf044e7ff]
[    0.754086] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
[    0.754100] pci 0000:00:12.0: reg 10: [mem 0xf044d000-0xf044dfff]
[    0.754177] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
[    0.754625] pci 0000:00:12.2: reg 10: [mem 0xf044c000-0xf044c0ff]
[    0.756922] pci 0000:00:12.2: supports D1 D2
[    0.756924] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.756951] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
[    0.756965] pci 0000:00:13.0: reg 10: [mem 0xf044b000-0xf044bfff]
[    0.757040] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
[    0.757431] pci 0000:00:13.2: reg 10: [mem 0xf044a000-0xf044a0ff]
[    0.759750] pci 0000:00:13.2: supports D1 D2
[    0.759752] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.759778] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
[    0.759859] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
[    0.759881] pci 0000:00:14.2: reg 10: [mem 0xf0440000-0xf0443fff 64bit]
[    0.759950] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.759967] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
[    0.760057] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
[    0.760110] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
[    0.760187] pci 0000:00:15.0: supports D1 D2
[    0.760216] pci 0000:00:15.1: [1022:43a1] type 01 class 0x060400
[    0.760293] pci 0000:00:15.1: supports D1 D2
[    0.760321] pci 0000:00:18.0: [1022:1400] type 00 class 0x060000
[    0.760341] pci 0000:00:18.1: [1022:1401] type 00 class 0x060000
[    0.760358] pci 0000:00:18.2: [1022:1402] type 00 class 0x060000
[    0.760377] pci 0000:00:18.3: [1022:1403] type 00 class 0x060000
[    0.760400] pci 0000:00:18.4: [1022:1404] type 00 class 0x060000
[    0.760417] pci 0000:00:18.5: [1022:1405] type 00 class 0x060000
[    0.760485] pci 0000:01:00.0: [1002:6660] type 00 class 0x038000
[    0.760501] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.760514] pci 0000:01:00.0: reg 18: [mem 0xf0300000-0xf033ffff 64bit]
[    0.760523] pci 0000:01:00.0: reg 20: [io  0x4000-0x40ff]
[    0.760539] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.760588] pci 0000:01:00.0: supports D1 D2
[    0.760590] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
[    0.768747] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.768755] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    0.768759] pci 0000:00:02.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.768764] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.768824] pci 0000:02:00.0: [10ec:8179] type 00 class 0x028000
[    0.768841] pci 0000:02:00.0: reg 10: [io  0x3000-0x30ff]
[    0.768867] pci 0000:02:00.0: reg 18: [mem 0xf0200000-0xf0203fff 64bit]
[    0.768950] pci 0000:02:00.0: supports D1 D2
[    0.768952] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.776740] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.776748] pci 0000:00:04.0:   bridge window [io  0x3000-0x3fff]
[    0.776752] pci 0000:00:04.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.776869] pci 0000:00:14.4: PCI bridge to [bus 03] (subtractive decode)
[    0.776879] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.776881] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.776883] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.776885] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.776887] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.776889] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.776890] pci 0000:00:14.4:   bridge window [mem 0x000cc000-0x000cffff] (subtractive decode)
[    0.776892] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.776894] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.776896] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.776897] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.776899] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.776901] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.776903] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.776905] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.776906] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xf7ffffff] (subtractive decode)
[    0.776908] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    0.776910] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    0.776984] pci 0000:04:00.0: [10ec:5229] type 00 class 0xff0000
[    0.777007] pci 0000:04:00.0: reg 10: [mem 0xf0100000-0xf0100fff]
[    0.777146] pci 0000:04:00.0: supports D1 D2
[    0.777148] pci 0000:04:00.0: PME# supported from D1 D2 D3hot
[    0.784768] pci 0000:00:15.0: PCI bridge to [bus 04]
[    0.784781] pci 0000:00:15.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.784865] pci 0000:05:00.0: [10ec:8136] type 00 class 0x020000
[    0.784887] pci 0000:05:00.0: reg 10: [io  0x2000-0x20ff]
[    0.784919] pci 0000:05:00.0: reg 18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    0.784939] pci 0000:05:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.784953] pci 0000:05:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.785030] pci 0000:05:00.0: supports D1 D2
[    0.785032] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.792759] pci 0000:00:15.1: PCI bridge to [bus 05]
[    0.792770] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    0.792775] pci 0000:00:15.1:   bridge window [mem 0xf0000000-0xf00fffff]
[    0.792827] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
[    0.792899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.792944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB0._PRT]
[    0.792988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SPB1._PRT]
[    0.793179]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.793438]  pci0000:00: ACPI _OSC control (0x19) granted
[    0.794768] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.794839] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.794922] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.795005] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.795069] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.795112] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.795155] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.795200] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.795418] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.795425] vgaarb: loaded
[    0.795426] vgaarb: bridge control possible 0000:00:01.0
[    0.795648] SCSI subsystem initialized
[    0.795650] ACPI: bus type scsi registered
[    0.795737] libata version 3.00 loaded.
[    0.795760] ACPI: bus type usb registered
[    0.795785] usbcore: registered new interface driver usbfs
[    0.795795] usbcore: registered new interface driver hub
[    0.795826] usbcore: registered new device driver usb
[    0.795940] PCI: Using ACPI for IRQ routing
[    0.797961] PCI: pci_cache_line_size set to 64 bytes
[    0.798055] e820: reserve RAM buffer [mem 0x0006e000-0x0006ffff]
[    0.798057] e820: reserve RAM buffer [mem 0x00086000-0x0008ffff]
[    0.798059] e820: reserve RAM buffer [mem 0x9a735000-0x9bffffff]
[    0.798061] e820: reserve RAM buffer [mem 0x9f5af000-0x9fffffff]
[    0.798062] e820: reserve RAM buffer [mem 0x9fc00000-0x9fffffff]
[    0.798064] e820: reserve RAM buffer [mem 0x12f000000-0x12fffffff]
[    0.798158] NetLabel: Initializing
[    0.798160] NetLabel:  domain hash size = 128
[    0.798161] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.798173] NetLabel:  unlabeled traffic allowed by default
[    0.798344] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.798348] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.800373] Switching to clocksource hpet
[    0.807672] AppArmor: AppArmor Filesystem Enabled
[    0.807703] pnp: PnP ACPI init
[    0.807719] ACPI: bus type pnp registered
[    0.807903] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.807906] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.807909] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.807911] system 00:00: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.807913] system 00:00: [mem 0xfed80000-0xfed81fff] could not be reserved
[    0.807917] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.808172] pnp 00:01: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.808221] pnp 00:02: [dma 4]
[    0.808240] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.808318] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.808374] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.808399] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.808436] pnp 00:06: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    0.808470] pnp 00:07: Plug and Play ACPI device, IDs SYN1e96 SYN1e00 SYN0002 PNP0f13 (active)
[    0.808556] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.808561] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.808571] system 00:08: [io  0x04d6] has been reserved
[    0.808573] system 00:08: [io  0x0680-0x06ff] has been reserved
[    0.808575] system 00:08: [io  0x077a] has been reserved
[    0.808578] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.808580] system 00:08: [io  0x0c14] has been reserved
[    0.808582] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.808584] system 00:08: [io  0x0c6c] has been reserved
[    0.808587] system 00:08: [io  0x0c6f] has been reserved
[    0.808589] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    0.808591] system 00:08: [io  0x0840-0x0847] has been reserved
[    0.808594] system 00:08: [io  0x0380-0x0387] has been reserved
[    0.808597] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.808686] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.808689] system 00:09: [mem 0xffc00000-0xffffffff] has been reserved
[    0.808692] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.809031] pnp 00:0a: Plug and Play ACPI device, IDs HPQ6007 (active)
[    1.008825] pnp: PnP ACPI: found 11 devices
[    1.008830] ACPI: ACPI bus type pnp unregistered
[    1.016303] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    1.016308] pci 0000:05:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    1.016419] pci 0000:00:15.1: BAR 15: assigned [mem 0xf0500000-0xf05fffff pref]
[    1.016423] pci 0000:01:00.0: BAR 6: assigned [mem 0xf0340000-0xf035ffff pref]
[    1.016426] pci 0000:00:02.0: PCI bridge to [bus 01]
[    1.016429] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    1.016433] pci 0000:00:02.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    1.016436] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    1.016441] pci 0000:00:04.0: PCI bridge to [bus 02]
[    1.016443] pci 0000:00:04.0:   bridge window [io  0x3000-0x3fff]
[    1.016447] pci 0000:00:04.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    1.016452] pci 0000:00:14.4: PCI bridge to [bus 03]
[    1.016464] pci 0000:00:15.0: PCI bridge to [bus 04]
[    1.016470] pci 0000:00:15.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    1.016479] pci 0000:05:00.0: BAR 6: assigned [mem 0xf0500000-0xf050ffff pref]
[    1.016481] pci 0000:00:15.1: PCI bridge to [bus 05]
[    1.016484] pci 0000:00:15.1:   bridge window [io  0x2000-0x2fff]
[    1.016490] pci 0000:00:15.1:   bridge window [mem 0xf0000000-0xf00fffff]
[    1.016494] pci 0000:00:15.1:   bridge window [mem 0xf0500000-0xf05fffff pref]
[    1.016534] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.016536] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.016538] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.016540] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.016542] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.016544] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.016546] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    1.016548] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.016550] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.016552] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.016554] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    1.016556] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    1.016558] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    1.016560] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    1.016562] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    1.016564] pci_bus 0000:00: resource 19 [mem 0xd0000000-0xf7ffffff]
[    1.016566] pci_bus 0000:00: resource 20 [mem 0xfc000000-0xfed3ffff]
[    1.016568] pci_bus 0000:00: resource 21 [mem 0xfed45000-0xffffffff]
[    1.016570] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    1.016572] pci_bus 0000:01: resource 1 [mem 0xf0300000-0xf03fffff]
[    1.016574] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    1.016576] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    1.016578] pci_bus 0000:02: resource 1 [mem 0xf0200000-0xf02fffff]
[    1.016581] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    1.016582] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    1.016584] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    1.016586] pci_bus 0000:03: resource 7 [mem 0x000c0000-0x000c3fff]
[    1.016588] pci_bus 0000:03: resource 8 [mem 0x000c4000-0x000c7fff]
[    1.016590] pci_bus 0000:03: resource 9 [mem 0x000c8000-0x000cbfff]
[    1.016592] pci_bus 0000:03: resource 10 [mem 0x000cc000-0x000cffff]
[    1.016594] pci_bus 0000:03: resource 11 [mem 0x000d0000-0x000d3fff]
[    1.016596] pci_bus 0000:03: resource 12 [mem 0x000d4000-0x000d7fff]
[    1.016598] pci_bus 0000:03: resource 13 [mem 0x000d8000-0x000dbfff]
[    1.016600] pci_bus 0000:03: resource 14 [mem 0x000dc000-0x000dffff]
[    1.016602] pci_bus 0000:03: resource 15 [mem 0x000e0000-0x000e3fff]
[    1.016604] pci_bus 0000:03: resource 16 [mem 0x000e4000-0x000e7fff]
[    1.016606] pci_bus 0000:03: resource 17 [mem 0x000e8000-0x000ebfff]
[    1.016608] pci_bus 0000:03: resource 18 [mem 0x000ec000-0x000effff]
[    1.016610] pci_bus 0000:03: resource 19 [mem 0xd0000000-0xf7ffffff]
[    1.016612] pci_bus 0000:03: resource 20 [mem 0xfc000000-0xfed3ffff]
[    1.016614] pci_bus 0000:03: resource 21 [mem 0xfed45000-0xffffffff]
[    1.016616] pci_bus 0000:04: resource 1 [mem 0xf0100000-0xf01fffff]
[    1.016618] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    1.016620] pci_bus 0000:05: resource 1 [mem 0xf0000000-0xf00fffff]
[    1.016622] pci_bus 0000:05: resource 2 [mem 0xf0500000-0xf05fffff pref]
[    1.016661] NET: Registered protocol family 2
[    1.016852] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    1.017004] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    1.017112] TCP: Hash tables configured (established 32768 bind 32768)
[    1.017148] TCP: reno registered
[    1.017159] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.017184] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.017258] NET: Registered protocol family 1
[    1.017273] pci 0000:00:01.0: Boot video device
[    1.643793] PCI: CLS 64 bytes, default 64
[    1.643861] Trying to unpack rootfs image as initramfs...
[    2.151361] Freeing initrd memory: 31176k freed
[    2.161277] PCI-DMA: Disabling AGP.
[    2.161281] PCI-DMA: More than 4GB of RAM and no IOMMU
[    2.161281] falling back to iommu=soft.
[    2.161283] More than 4GB of memory but GART IOMMU not available.
[    2.161284] falling back to iommu=soft.
[    2.161285] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.161288] software IO TLB [mem 0x93fb0000-0x97fb0000] (64MB) mapped at [ffff880093fb0000-ffff880097faffff]
[    2.161409] Simple Boot Flag at 0x44 set to 0x1
[    2.161567] LVT offset 0 assigned for vector 0x400
[    2.161603] perf: AMD IBS detected (0x000000ff)
[    2.162015] Initialise module verification
[    2.162058] audit: initializing netlink socket (disabled)
[    2.162077] type=2000 audit(1376722963.056:1): initialized
[    2.188383] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.190365] VFS: Disk quotas dquot_6.5.2
[    2.190413] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.191165] fuse init (API version 7.20)
[    2.191272] msgmni has been set to 6193
[    2.191929] Key type asymmetric registered
[    2.191933] Asymmetric key parser 'x509' registered
[    2.191995] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.192078] io scheduler noop registered
[    2.192080] io scheduler deadline registered (default)
[    2.192087] io scheduler cfq registered
[    2.192236] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    2.192457] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.192517] pciehp 0000:00:02.0:pcie04: HPC vendor_id 1022 device_id 1412 ss_vid 1022 ss_did 1234
[    2.192548] pciehp 0000:00:02.0:pcie04: service driver pciehp loaded
[    2.192553] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.192629] efifb: probing for efifb
[    2.193080] efifb: framebuffer at 0xd0000000, mapped to 0xffffc90008d00000, using 4224k, total 4224k
[    2.193082] efifb: mode is 1366x768x32, linelength=5632, pages=1
[    2.193083] efifb: scrolling: redraw
[    2.193085] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.195602] Console: switching to colour frame buffer device 170x48
[    2.197881] fb0: EFI VGA frame buffer device
[    2.304396] ACPI: AC Adapter [ACAD] (on-line)
[    2.304480] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    2.304486] ACPI: Power Button [PWRB]
[    2.304566] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    2.305076] ACPI: Lid Switch [LID]
[    2.305175] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    2.305180] ACPI: Power Button [PWRF]
[    2.305327] ACPI: acpi_idle registered with cpuidle
[    2.709997] thermal LNXTHERM:00: registered as thermal_zone0
[    2.710001] ACPI: Thermal Zone [THRM] (71 C)
[    2.710053] GHES: HEST is not enabled!
[    2.710224] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.712156] Linux agpgart interface v0.103
[    2.714362] brd: module loaded
[    2.715593] loop: module loaded
[    2.715973] libphy: Fixed MDIO Bus: probed
[    2.716036] tun: Universal TUN/TAP device driver, 1.6
[    2.716037] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.716248] PPP generic driver version 2.4.2
[    2.716316] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.716319] ehci-pci: EHCI PCI platform driver
[    2.716360] ehci-pci 0000:00:12.2: EHCI Host Controller
[    2.716366] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    2.716379] QUIRK: Enable AMD PLL fix
[    2.716382] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.716394] ehci-pci 0000:00:12.2: debug port 1
[    2.716437] ehci-pci 0000:00:12.2: irq 17, io mem 0xf044c000
[    2.726570] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    2.726613] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.726615] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.726617] usb usb1: Product: EHCI Host Controller
[    2.726619] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    2.726621] usb usb1: SerialNumber: 0000:00:12.2
[    2.726832] hub 1-0:1.0: USB hub found
[    2.726836] hub 1-0:1.0: 5 ports detected
[    2.727065] ehci-pci 0000:00:13.2: EHCI Host Controller
[    2.727071] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    2.727077] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    2.727089] ehci-pci 0000:00:13.2: debug port 1
[    2.727120] ehci-pci 0000:00:13.2: irq 17, io mem 0xf044a000
[    2.738566] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.738617] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.738620] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.738623] usb usb2: Product: EHCI Host Controller
[    2.738625] usb usb2: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    2.738627] usb usb2: SerialNumber: 0000:00:13.2
[    2.738841] hub 2-0:1.0: USB hub found
[    2.738846] hub 2-0:1.0: 5 ports detected
[    2.739044] ehci-platform: EHCI generic platform driver
[    2.739057] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.739155] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    2.739163] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    2.739191] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf044d000
[    2.798502] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    2.798507] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.798509] usb usb3: Product: OHCI Host Controller
[    2.798511] usb usb3: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    2.798513] usb usb3: SerialNumber: 0000:00:12.0
[    2.798741] hub 3-0:1.0: USB hub found
[    2.798749] hub 3-0:1.0: 5 ports detected
[    2.798942] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.798948] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    2.798965] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf044b000
[    2.858429] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    2.858433] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.858436] usb usb4: Product: OHCI Host Controller
[    2.858438] usb usb4: Manufacturer: Linux 3.8.0-19-generic ohci_hcd
[    2.858440] usb usb4: SerialNumber: 0000:00:13.0
[    2.858609] hub 4-0:1.0: USB hub found
[    2.858621] hub 4-0:1.0: 5 ports detected
[    2.858791] uhci_hcd: USB Universal Host Controller Interface driver
[    2.858902] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    2.858908] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
[    2.859161] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    2.859168] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    2.859175] xhci_hcd 0000:00:10.0: irq 43 for MSI/MSI-X
[    2.859181] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    2.859186] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    2.859290] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    2.859293] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.859294] usb usb5: Product: xHCI Host Controller
[    2.859296] usb usb5: Manufacturer: Linux 3.8.0-19-generic xhci_hcd
[    2.859298] usb usb5: SerialNumber: 0000:00:10.0
[    2.859367] xHCI xhci_add_endpoint called for root hub
[    2.859369] xHCI xhci_check_bandwidth called for root hub
[    2.859389] hub 5-0:1.0: USB hub found
[    2.859413] hub 5-0:1.0: 2 ports detected
[    2.859482] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    2.859485] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    2.862511] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    2.862513] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.862515] usb usb6: Product: xHCI Host Controller
[    2.862517] usb usb6: Manufacturer: Linux 3.8.0-19-generic xhci_hcd
[    2.862519] usb usb6: SerialNumber: 0000:00:10.0
[    2.862582] xHCI xhci_add_endpoint called for root hub
[    2.862584] xHCI xhci_check_bandwidth called for root hub
[    2.862601] hub 6-0:1.0: USB hub found
[    2.862632] hub 6-0:1.0: 2 ports detected
[    2.863006] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.868544] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.868554] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.868842] mousedev: PS/2 mouse device common for all mice
[    2.869029] rtc_cmos 00:04: RTC can wake from S4
[    2.869149] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.869176] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    2.869277] device-mapper: uevent: version 1.0.3
[    2.869391] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.869457] cpuidle: using governor ladder
[    2.869592] cpuidle: using governor menu
[    2.869595] ledtrig-cpu: registered to indicate activity on CPUs
[    2.869597] EFI Variables Facility v0.08 2004-May-17
[    2.899731] ashmem: initialized
[    2.899860] TCP: cubic registered
[    2.899964] NET: Registered protocol family 10
[    2.900141] NET: Registered protocol family 17
[    2.900154] Key type dns_resolver registered
[    2.900683] Loading module verification certificates
[    2.901636] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[    2.901647] registered taskstats version 1
[    2.904628] Key type trusted registered
[    2.907027] Key type encrypted registered
[    2.910097] rtc_cmos 00:04: setting system clock to 2013-08-17 07:02:43 UTC (1376722963)
[    2.910150] powernow-k8: this CPU is not supported anymore, using acpi-cpufreq instead.
[    2.911415] acpi-cpufreq: overriding BIOS provided _PSD data
[    2.911834] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.911836] EDD information not available.
[    2.936640] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.950932] ACPI: Battery Slot [BAT0] (battery present)
[    2.953822] Freeing unused kernel memory: 992k freed
[    2.954043] Write protecting the kernel read-only data: 12288k
[    2.960018] Freeing unused kernel memory: 1176k freed
[    2.965459] Freeing unused kernel memory: 1080k freed
[    2.987481] udevd[112]: starting version 175
[    3.125355] Disabling lock debugging due to kernel taint
[    3.140502] [drm] Initialized drm 1.1.0 20060810
[    3.150337] ahci 0000:00:11.0: version 3.0
[    3.150600] ahci 0000:00:11.0: irq 46 for MSI/MSI-X
[    3.150694] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0xb impl SATA mode
[    3.150698] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part sxs 
[    3.152297] acpi device:00: registered as cooling_device4
[    3.152375] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    3.152431] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    3.153664] scsi0 : ahci
[    3.153932] scsi1 : ahci
[    3.154188] acpi device:06: registered as cooling_device5
[    3.154241] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    3.154290] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input5
[    3.154341] wmi: Mapper loaded
[    3.157955] tsc: Refined TSC clocksource calibration: 2096.083 MHz
[    3.157960] Switching to clocksource tsc
[    3.161094] scsi2 : ahci
[    3.164403] scsi3 : ahci
[    3.164594] ata1: SATA max UDMA/133 abar m2048@0xf044e000 port 0xf044e100 irq 46
[    3.164601] ata2: SATA max UDMA/133 abar m2048@0xf044e000 port 0xf044e180 irq 46
[    3.164604] ata3: DUMMY
[    3.164609] ata4: SATA max UDMA/133 abar m2048@0xf044e000 port 0xf044e280 irq 46
[    3.166273] [drm] radeon defaulting to kernel modesetting.
[    3.166277] [drm] radeon kernel modesetting enabled.
[    3.166319] checking generic (d0000000 420000) vs hw (d0000000 10000000)
[    3.166321] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
[    3.166344] Console: switching to colour dummy device 80x25
[    3.169588] [drm] initializing kernel modesetting (ARUBA 0x1002:0x990D 0x103C:0x1983).
[    3.169686] [drm] register mmio base: 0xF0400000
[    3.169690] [drm] register mmio size: 262144
[    3.169727] [drm] ACPI VFCT contains a BIOS for 00:01.0 1002:990d, size 20480
[    3.169748] ATOM BIOS: HP
[    3.169793] radeon 0000:00:01.0: VRAM: 768M 0x0000000000000000 - 0x000000002FFFFFFF (768M used)
[    3.169798] radeon 0000:00:01.0: GTT: 512M 0x0000000030000000 - 0x000000004FFFFFFF
[    3.170543] [drm] Detected VRAM RAM=768M, BAR=256M
[    3.170547] [drm] RAM width 32bits DDR
[    3.170794] [TTM] Zone  kernel: Available graphics memory: 1587164 kiB
[    3.170797] [TTM] Initializing pool allocator
[    3.170802] [TTM] Initializing DMA pool allocator
[    3.170839] [drm] radeon: 768M of VRAM memory ready
[    3.170843] [drm] radeon: 512M of GTT memory ready.
[    3.170872] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.170875] [drm] Driver supports precise vblank timestamp query.
[    3.170920] radeon 0000:00:01.0: irq 47 for MSI/MSI-X
[    3.170935] radeon 0000:00:01.0: radeon: using MSI.
[    3.171285] [drm] radeon: irq initialized.
[    3.171292] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    3.172400] [drm] Loading ARUBA Microcode
[    3.173424] rtsx_pci 0000:04:00.0: irq 48 for MSI/MSI-X
[    3.173450] rtsx_pci 0000:04:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 48
[    3.178408] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.179598] r8169 0000:05:00.0: irq 49 for MSI/MSI-X
[    3.180235] r8169 0000:05:00.0 eth0: RTL8106e at 0xffffc9000408e000, a4:5d:36:6d:f4:84, XID 04900000 IRQ 49
[    3.197130] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[    3.197263] radeon 0000:00:01.0: WB enabled
[    3.197267] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000030000c00 and cpu addr 0xffff880122ec9c00
[    3.197270] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000030000c04 and cpu addr 0xffff880122ec9c04
[    3.197273] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000030000c08 and cpu addr 0xffff880122ec9c08
[    3.197275] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000030000c0c and cpu addr 0xffff880122ec9c0c
[    3.197277] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000030000c10 and cpu addr 0xffff880122ec9c10
[    3.216601] [drm] ring test on 0 succeeded in 2 usecs
[    3.216665] [drm] ring test on 3 succeeded in 2 usecs
[    3.216674] [drm] ring test on 4 succeeded in 1 usecs
[    3.222219] usb 2-4: new high-speed USB device number 2 using ehci-pci
[    3.236498] [drm] ib test on ring 0 succeeded in 0 usecs
[    3.237022] [drm] ib test on ring 3 succeeded in 0 usecs
[    3.237543] [drm] ib test on ring 4 succeeded in 1 usecs
[    3.239843] [drm] radeon atom DIG backlight initialized
[    3.239845] [drm] Radeon Display Connectors
[    3.239847] [drm] Connector 0:
[    3.239848] [drm]   eDP-1
[    3.239849] [drm]   HPD1
[    3.239851] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    3.239852] [drm]   Encoders:
[    3.239853] [drm]     LCD1: INTERNAL_UNIPHY2
[    3.239855] [drm] Connector 1:
[    3.239856] [drm]   VGA-1
[    3.239857] [drm]   HPD2
[    3.239858] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    3.239859] [drm]   Encoders:
[    3.239860] [drm]     CRT1: INTERNAL_UNIPHY2
[    3.239861] [drm]     CRT1: NUTMEG
[    3.239862] [drm] Connector 2:
[    3.239864] [drm]   HDMI-A-1
[    3.239864] [drm]   HPD3
[    3.239866] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    3.239867] [drm]   Encoders:
[    3.239868] [drm]     DFP1: INTERNAL_UNIPHY
[    3.291204] [drm] Internal thermal controller without fan control
[    3.291230] [drm] radeon: power management initialized
[    3.408408] usb 2-4: New USB device found, idVendor=0bda, idProduct=571c
[    3.408413] usb 2-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    3.408416] usb 2-4: Product: HP Truevision HD
[    3.408418] usb 2-4: Manufacturer: DDFEQ01RS4N31N
[    3.408420] usb 2-4: SerialNumber: 200901010001
[    3.489750] ata4: SATA link down (SStatus 0 SControl 300)
[    3.549647] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    3.653476] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.653532] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.716527] usb 3-1: New USB device found, idVendor=1bcf, idProduct=0007
[    3.716530] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    3.716533] usb 3-1: Product: USB Optical Mouse
[    3.733663] usbcore: registered new interface driver usbhid
[    3.733667] usbhid: USB HID core driver
[    3.737217] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input6
[    3.737389] hid-generic 0003:1BCF:0007.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:12.0-1/input0
[    4.421765] ata1.00: ATA-9: Samsung SSD 840 Series, DXT08B0Q, max UDMA/133
[    4.421770] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.422371] ata1.00: configured for UDMA/133
[    4.422465] ata2.00: ATAPI: hp       DVDRAM GU70N, U703, max UDMA/100
[    4.422576] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXT0 PQ: 0 ANSI: 5
[    4.422946] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    4.422982] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.423042] sd 0:0:0:0: [sda] Write Protect is off
[    4.423045] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.423074] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.424992] ata2.00: configured for UDMA/100
[    4.425751]  sda: sda1 sda2 sda3
[    4.426233] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GU70N     U703 PQ: 0 ANSI: 5
[    4.426564] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.428653] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.428659] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.428830] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.428928] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.478478] [drm] fb mappable at 0xD114C000
[    4.478482] [drm] vram apper at 0xD0000000
[    4.478484] [drm] size 4325376
[    4.478485] [drm] fb depth is 24
[    4.478486] [drm]    pitch is 5632
[    4.478729] fbcon: radeondrmfb (fb0) is primary device
[    6.549188] Console: switching to colour frame buffer device 170x48
[    6.551510] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    6.551513] radeon 0000:00:01.0: registered panic notifier
[    6.551727] [drm] Initialized radeon 2.29.0 20080528 for 0000:00:01.0 on minor 0
[    6.870829] xor: automatically using best checksumming function:
[    6.909917]    avx       :  3653.000 MB/sec
[    6.912297] device-mapper: dm-raid45: initialized v0.2594b
[    6.949682] Btrfs loaded
[    6.974144] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    6.974149] EXT4-fs (sda2): write access will be enabled during recovery
[    7.180798] EXT4-fs (sda2): recovery complete
[    7.188256] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    7.405184] Adding 3372028k swap on /dev/sda3.  Priority:-1 extents:1 across:3372028k SS
[    7.427270] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    7.481796] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.486415] udevd[529]: starting version 175
[    7.510591] lp: driver loaded but no devices found
[    7.532424] cfg80211: Calling CRDA to update world regulatory domain
[    7.584283] cfg80211: World regulatory domain updated:
[    7.584288] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.584291] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.584293] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.584295] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.584296] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.584298] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.630919] Bluetooth: Core ver 2.16
[    7.630941] NET: Registered protocol family 31
[    7.630944] Bluetooth: HCI device and connection manager initialized
[    7.630953] Bluetooth: HCI socket layer initialized
[    7.630957] Bluetooth: L2CAP socket layer initialized
[    7.630963] Bluetooth: SCO socket layer initialized
[    7.633418] init: avahi-cups-reload main process (605) terminated with status 1
[    7.637518] ppdev: user-space parallel port driver
[    7.637997] Bluetooth: RFCOMM TTY layer initialized
[    7.638012] Bluetooth: RFCOMM socket layer initialized
[    7.638014] Bluetooth: RFCOMM ver 1.11
[    7.639267] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.639269] Bluetooth: BNEP filters: protocol multicast
[    7.639274] Bluetooth: BNEP socket layer initialized
[    7.793128] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMB0 1 (20121018/utaddress-251)
[    7.793139] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.799458] Linux video capture interface: v2.00
[    7.828535] microcode: CPU0: patch_level=0x06001119
[    7.829883] microcode: CPU1: patch_level=0x06001119
[    7.829895] microcode: CPU2: patch_level=0x06001119
[    7.829908] microcode: CPU3: patch_level=0x06001119
[    7.830916] uvcvideo: Found UVC 1.00 device HP Truevision HD (0bda:571c)
[    7.832393] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    7.842807] input: HP Truevision HD as /devices/pci0000:00/0000:00:13.2/usb2/2-4/2-4:1.0/input/input7
[    7.842956] usbcore: registered new interface driver uvcvideo
[    7.842959] USB Video Class driver (1.1.1)
[    7.893510] device-mapper: multipath: version 1.5.1 loaded
[    7.917764] kvm: Nested Virtualization enabled
[    7.917769] kvm: Nested Paging enabled
[    7.980670] init: failsafe main process (826) killed by TERM signal
[    8.077733] hda-intel 0000:00:01.1: Force to non-snoop mode
[    8.077797] snd_hda_intel 0000:00:01.1: irq 50 for MSI/MSI-X
[    8.102165] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input8
[    8.120364] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input9
[    8.120465] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[    8.135731] input: HP WMI hotkeys as /devices/virtual/input/input11
[    8.293561] r8169 0000:05:00.0 eth0: link down
[    8.293585] r8169 0000:05:00.0 eth0: link down
[    8.293607] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.294113] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.683990] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xf00133/0x240000/0xa2400, board id: 2665, fw id: 1317286
[    8.728467] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[    9.165082] init: plymouth-stop pre-start process (1477) terminated with status 1
[   10.082330] r8169 0000:05:00.0 eth0: link up
[   10.082346] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   10.086716] r8169 0000:05:00.0 eth0: link down
[   11.569646] r8169 0000:05:00.0 eth0: link up
[   89.458297] systemd-timedated[2324]: /etc/localtime should be a symbolic link to a timezone data file in /usr/share/zoneinfo/.
[  422.385526] systemd-timedated[2440]: /etc/localtime should be a symbolic link to a timezone data file in /usr/share/zoneinfo/.
```

I have run out of ideas of what to try next and a search of the forums has not helps so far.  So I'm open to suggestions.  Based on the problems getting it boot and unresolved video and audio problems I would not recommend this laptop for Linux.  A shame as HP have been good for me in the past.

---

### Post by praseodym on 2013-08-17
The driver is rtl8192ce, but it need additional parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtlwifi
sudo modprobe -v rtl8192ce
```
Alternatively, update the driver according to this:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r)
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

### Post by ukoda on 2013-08-17
Thanks Praseodym, I tried the first option which does load the rtl8192ce but there is still no wlan0 and I notice rtlwifi is still loaded.  Here is the new lsmod output:
```
Module                  Size  Used by
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
kvm_amd                59717  0 
kvm                   443165  1 kvm_amd
parport_pc             28152  0 
ghash_clmulni_intel    13259  0 
ppdev                  17073  0 
uvcvideo               80847  0 
aesni_intel            55399  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
videodev              129260  2 uvcvideo,videobuf2_core
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
snd_hda_codec_realtek    78399  1 
microcode              22881  0 
dm_multipath           22843  0 
scsi_dh                14843  1 dm_multipath
k10temp                13126  0 
snd_hda_codec_hdmi     36913  1 
bnep                   18036  2 
rfcomm                 42641  0 
joydev                 17377  0 
i2c_piix4              13266  0 
bluetooth             228619  10 bnep,rfcomm
psmouse                95870  0 
serio_raw              13215  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
binfmt_misc            17500  1 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
nls_iso8859_1          12713  1 
rtl8192ce              53594  0 
rtlwifi                79673  1 rtl8192ce
rtl8192c_common        48779  1 rtl8192ce
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192ce
mac_hid                13205  0 
cfg80211              510937  2 mac80211,rtlwifi
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
rtsx_pci_sdmmc         17475  0 
radeon                937749  2 
r8169                  67446  0 
i2c_algo_bit           13413  1 radeon
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
ahci                   25731  3 
libahci                31364  1 ahci
drm                   286313  4 ttm,drm_kms_helper,radeon
wmi                    19070  1 hp_wmi
video                  19390  0 

```

I assume the second option just results in a more recent driver?  Anymore suggestions?

---

### Post by ukoda on 2013-08-18
Ok the finer points of this are eluding me.  From what I can tell my missing wlan0 will magically appear after a reboot once the right drivers are loaded and they find the hardware?  I guess even though what I think are the right drivers are listed lsmod only means the drivers are loaded by the kernel but does not mean they will actually do anything?  And the "unclaimed" status shown by lshw indicates I have either the wrong driver or the wrong parameters to the driver?

---

### Post by praseodym on 2013-08-18
Obviously, the current driver doesn’t support your card very well. Tried the update?

---

### Post by ukoda on 2013-08-18
I get a build error with the update:
```
make -C /lib/modules/3.8.0-19-generic/build M=/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;rtl_pci_probe&#8217;
make[2]: *** [/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [all] Error 2

```
I guess I missing a build dependency, not that I'm building as root?

---

### Post by praseodym on 2013-08-18
Check:
```

ifconfig -a
iwconfig
dmesg | grep rtl8
lspci -nnk | grep -iA2 net
cat /etc/resolv.conf
rfkill list
```
Obviously the driver cannot be build with kernel 3.8

---

### Post by ukoda on 2013-08-18
I get a build error with the update:
```
make -C /lib/modules/3.8.0-19-generic/build M=/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
In file included from /root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.c:39:0:
/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/pci.h:247:15: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rtl_pci_probe’
make[2]: *** [/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o] Error 1
make[1]: *** [_module_/root/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-19-generic'
make: *** [all] Error 2

```
I guess I missing a build dependency, not that I'm building as root?

---

### Post by ukoda on 2013-08-18
Hi praseodym, thanks for the help.  Sorry about the duplicate post, the connection here in China is unreliable.

Here is the output you asked for:
```
==== ifconfig -a ====
eth0      Link encap:Ethernet  HWaddr a4:5d:36:6d:f4:84  
          inet addr:10.11.1.124  Bcast:10.11.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a65d:36ff:fe6d:f484/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34430603 (34.4 MB)  TX bytes:2532178 (2.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148145 (148.1 KB)  TX bytes:148145 (148.1 KB)

==== iwconfig ====
eth0      no wireless extensions.

lo        no wireless extensions.

==== dmesg | grep rtl8 ====
==== lspci -nnk | grep -iA2 net ====
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:1983]
	Kernel driver in use: r8169
==== /etc/resolv.conf ====
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search CHANGED.co.nz

# OpenDNS Fallback (configured by Linux Mint in /etc/resolvconf/resolv.conf.d/tail).
nameserver 208.67.222.222
nameserver 208.67.220.220

==== rfkill list ====

```

---

### Post by praseodym on 2013-08-18
Obviously, the driver cannot be build with kernel 3.8 and (here) 3.9. Bad luck.

Check if any available driver supports your device:

```
modprobe -c | grep -i "10EC.*8179" 
```
Tried Ubuntu 12.04 or the live-cd of 13.10 (unstable!!!)?

Edit: I know that this driver can be build with kernel 3.5 of 12.04

---

