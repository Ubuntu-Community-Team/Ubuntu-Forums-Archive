---
title: "Can't get wlan0 to show up in backtrack 5."
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by sent17inel on 2011-06-12
I have the output of my lshw and the blacklist_ath-pic.conf.  its from a fresh install. My wireless card works fine in the past 4 or 5 versions of ubuntu and I heard that backtrack 5 was using an ubuntu kernel so I'm not sure why it wouldn't work out of the box. Any know what's wrong here??

> root@bt:~# lshw
bt                        
    description: Notebook
    product: Satellite L655D
    vendor: TOSHIBA
    version: PSK2LU-001003
    serial: 5A120726W
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=A0A3E13C-4360-DF11-A197-C80AA9835D2D
  *-core
       description: Motherboard
       product: Guam
       vendor: AMD Corp.
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: 1.70 (09/09/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Athlon(tm) II P320 Dual-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 20
          bus info: cpu@0
          version: AMD Athlon(tm) II P320 Dual-Core Processor
          serial: NotSupport
          slot: Socket S1G4
          size: 2100MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a 3dnowprefetch osvw ibs skinit wdt nodeid_msr npt lbrv svm_lock nrip_save cpufreq
        *-cache:0
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 22
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 3GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: M471B5673FH0-CF8
             vendor: Samsung
             physical id: 0
             serial: 667DD8C0
             slot: DIMM0
             size: 2GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM Synchronous 1066 MHz (0.9 ns)
             product: 8JSF12864HZ-1G1F1
             vendor: Micron Technology
             physical id: 1
             serial: 33F179A1
             slot: DIMM1
             size: 1GiB
             width: 8 bits
             clock: 1066MHz (0.9ns)
     *-pci:0
          description: Host bridge
          product: RS880 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: Toshiba America Info Systems
             vendor: Toshiba America Info Systems
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:b000(size=4096) memory:d4100000-d42fffff ioport:c0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff ioport:b000(size=256) memory:d4200000-d420ffff memory:d4100000-d41fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:7000(size=16384) memory:d3100000-d40fffff ioport:d0000000(size=16777216)
           *-network UNCLAIMED
                description: Network controller
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: ioport:7000(size=256) memory:d3100000-d3103fff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:6000(size=4096) memory:d3000000-d30fffff
           *-network
                description: Ethernet interface
                product: AR8152 v1.1 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: c1
                serial: c8:0a:a9:83:5d:2d
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:42 memory:d3000000-d303ffff ioport:6000(size=128)
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:19 ioport:c038(size=8) ioport:c04c(size=4) ioport:c030(size=8) ioport:c048(size=4) ioport:c010(size=16) memory:d4307000-d43073ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54503
                vendor: Hitachi
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: PB3O
                serial: 100305PBP30016CWK81L
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c4890
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 439a49e9-3b48-4283-ad9d-1cdc4a00e739
                   size: 147GiB
                   capacity: 147GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-06-11 21:30:55 filesystem=ext4 lastmountpoint=/8?????r?x(?????r????pZ?????????????????X?g?? modified=2011-06-12 06:25:29 mounted=2011-06-12 06:28:58 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 150GiB
                   capacity: 150GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8088MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 136GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 5963MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ890ES
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.80
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d4306000-d4306fff
        *-usb:1
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d4307600-d43076ff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d4305000-d4305fff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d4307500-d43075ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 41
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 40
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d4300000-d4303fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 40
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
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-pci:4
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=16384) memory:d2000000-d2ffffff ioport:d1000000(size=16777216)
        *-usb:4
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d4304000-d4304fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d4307400-d43074ff
     *-pci:1
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
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
          product: Family 10h Processor Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb
root@bt:~# 


modprobe.d > blacklist-ath_pci.conf 

> 
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci

---

### Post by superduperlinuxperson on 2011-06-12
sorry, wrong tab!

go to your propreiraty drivers and try looking around for broadcom drivers

---

### Post by josephmills on 2011-06-12
```

description: Network controller
product: RTL8191SEvB Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
version: 10
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: ioport:7000(size=256) memory:d3100000-d3103fff
```
could we please see a 
```
lsmod
``` thanks

---

### Post by sent17inel on 2011-06-12
> **josephmills said:**
> ```

description: Network controller
product: RTL8191SEvB Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
version: 10
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: ioport:7000(size=256) memory:d3100000-d3103fff
```
could we please see a 
```
lsmod
``` thanks

```
root@bt:~# lsmod
Module                  Size  Used by
dm_crypt               16476  0 
snd_hda_codec_conexant    46971  1 
snd_hda_intel          25353  0 
snd_hda_codec          88363  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6666  1 snd_hda_codec
snd_pcm_oss            39737  0 
snd_mixer_oss          15545  1 snd_pcm_oss
snd_pcm                83404  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            29952  0 
joydev                 10865  0 
snd_seq_midi            5676  0 
snd_rawmidi            21765  1 snd_seq_midi
snd_seq_midi_event      6708  2 snd_seq_oss,snd_seq_midi
snd_seq                54693  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21990  2 snd_pcm,snd_seq
snd_seq_device          6265  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    65330  12 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap           3782  0 
rfkill                 18476  0 
soundcore               7208  1 snd
uvcvideo               63153  0 
psmouse                60384  0 
snd_page_alloc          8117  2 snd_hda_intel,snd_pcm
wmi                     9912  0 
shpchp                 28122  0 
videodev               72410  1 uvcvideo
lp                      9893  0 
sp5100_tco              5156  0 
v4l2_compat_ioctl32     7512  1 videodev
serio_raw               4784  0 
atl1c                  33635  0 
i2c_piix4               8911  0 
edac_core              44664  0 
mac_hid                 3869  0 
parport                34080  1 lp
edac_mce_amd           14922  0 
k10temp                 3383  0 
radeon                961662  2 
ttm                    64930  1 radeon
drm_kms_helper         32506  1 radeon
ahci                   21302  2 
usb_storage            48102  0 
drm                   204443  5 radeon,ttm,drm_kms_helper
uas                     8788  0 
i2c_algo_bit            5564  1 radeon
libahci                21959  1 ahci
video                  12530  0 
```

---

### Post by sent17inel on 2011-06-13
bump

---

### Post by sent17inel on 2011-06-16
bump

---

### Post by crispy_420 on 2011-06-17
Doesn't Backtrack force you to manually start any network device?

'ifconfig wlan0 up'

Or what ever your card gets listed as...

Maybe check this out too:

[http://ubuntuforums.org/showthread.php?t=1635892](http://ubuntuforums.org/showthread.php?t=1635892)

---

### Post by sent17inel on 2011-06-17
> **crispy_420 said:**
> Doesn't Backtrack force you to manually start any network device?

'ifconfig wlan0 up'

Or what ever your card gets listed as...

Maybe check this out too:

[http://ubuntuforums.org/showthread.php?t=1635892](http://ubuntuforums.org/showthread.php?t=1635892)

I tried that. It said "wlan0: ERROR while getting interface flags: No such device

I did another lshw but this time with parameters. heres the output.

```
root@bt:~# lshw -class network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:d3100000-d3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: c8:0a:a9:83:5d:2d
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:d3000000-d303ffff ioport:6000(size=128)
root@bt:~# 
```

---

### Post by sent17inel on 2011-06-17
got it to work installing wireless drivers from source code.

---

### Post by crispy_420 on 2011-06-17
Then can this be called solved? 

Backtrack is a great tool but I have only used it as a LiveCD. As a tip, maybe look into a wireless card that just works. Check with them for the models that support "other" features that some do not. I know I my Intel based card supports packet injection that helps with testing the security of wifi while many cards are unable to to this.

Is your current card a mini-pci or mini-pcie?

---

