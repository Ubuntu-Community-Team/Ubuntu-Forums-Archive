---
title: "Logitech quickcam Pro 9000 --&gt; Could not connect to video device (/dev0/vide0)"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by TACtech on 2007-12-09
I am using Ubuntu 7.10 and I have Logitech Quickcam Pro 9000 however i can't connect to it. When I lunch camorama I get this error message" Could not connect to video device (/dev0/vide0)"

It looks that my webcam is being recognized

```
 tac@TAC-X300:~$ lsusb
Bus 004 Device 003: ID 413c:9001 Dell Computer Corp. 
Bus 004 Device 002: ID 046d:0990 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

and uvcvideo module is loaded as well 

```


tac@TAC-X300:~$ lsmod
Module                  Size  Used by
af_packet              24840  4 
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
snd_rtctimer            4384  1 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
ipv6                  273892  12 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
container               5504  0 
video                  18060  0 
button                  8976  0 
dock                   10656  0 
ac                      6148  0 
sbs                    19592  0 
battery                11012  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sbp2                   24072  0 
lp                     12580  0 
snd_usb_audio          81024  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
pcmcia                 41388  0 
bcm43xx               127336  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ieee80211softmac       31360  1 bcm43xx
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211
irda                  202300  0 
yenta_socket           27532  2 
rsrc_nonstatic         14080  1 yenta_socket
snd_pcm                80388  9 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
uvcvideo               48644  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
joydev                 11328  0 
compat_ioctl32          2304  1 uvcvideo
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq                53232  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
snd_rawmidi            25728  2 snd_usb_lib,snd_seq_midi
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            18432  2 uvcvideo,videodev
snd_hwdep              10244  1 snd_usb_audio
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd                    54660  26 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_usb_audio,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device,snd_hwdep
soundcore               8800  1 snd
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
psmouse                39952  0 
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  6 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  4 
ata_piix               17540  3 
tg3                   110980  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sr_mod,sbp2,usb_storage,sg,sd_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 snd_usb_audio,snd_usb_lib,uvcvideo,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 


```

so I do not know what the problem is.
Does anybody have any idea what the solution could be to resolve this problem?
Let me know if you need any additional info.
Thank you all in advance.

---

### Post by Bunzinator on 2007-12-09
Same issue here.

The device has been created, it is recognised by caminfo, and qcset doesn´t like it. My guess is that the version of the uvcvideo module isn´t bleeding edge enough to support the camera.

Note that both apps complain about having video channel related issues.

```
xxxxx@xxxxx:~$ caminfo
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "UVC Camera (046d:0990)"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 960x720
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

xxxxx@xxxxx:~$ qcset -i
qcset: ioctl VIDIOCGCHAN (Invalid argument)
```

---

### Post by asnd16 on 2007-12-13
same issue ! 
[http://ubuntuforums.org/showthread.php?p=3946186#post3946186]("http://ubuntuforums.org/showthread.php?p=3946186#post3946186")


ERRRR I just got the cam and would like it to work . . 
caminfo
CVideoDeviceInput: Warning: no channel info available.
Detected 1 Video4Linux devices.
Device node      : /dev/video0
Name of device   : "UVC Camera (046d:0990)"
Minimum size     : 48x32
Current size     : 0x0
Maximum size     : 960x720
Video inputs     : 1
 Input 0
  Name             : "(null)"
  Type             : Unknown
  Audio            : no
  Tuners           : 0
Audio inputs     : 0

---

### Post by rsambuca on 2007-12-13
I think you should install the latest uvcvideo drivers.

---

### Post by asnd16 on 2007-12-13
> **rsambuca said:**
> I think you should install the latest uvcvideo drivers.


how how how ?  I have done this! I believe !

---

### Post by rsambuca on 2007-12-13
Have you [done this]("http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC")?

---

### Post by asnd16 on 2007-12-13
yeah . . Funny there is no dev/video0 would this be an issue

Camestream error 
 camstream
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CVideoDeviceInput: Warning: no channel info available.

---

### Post by rsambuca on 2007-12-13
So have you installed the latest drivers directly from that site I linked to?

---

### Post by asnd16 on 2007-12-13
yeah I belive so. . is there a way to check?  When I try and veiw the folder "dev/video0"  none exists

---

### Post by rsambuca on 2007-12-13
Post the output of:

dmesg

---

### Post by asnd16 on 2007-12-13
Hey thanks for the help . . . I serriously would love this to work 

>  dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128736) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128736
[    0.000000]   HighMem    128736 ->   128736
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128736
[    0.000000] On node 0 totalpages: 128736
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123667 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F76F0 checksum 0
[    0.000000] ACPI: RSDP 000F76F0, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 1F6E557A, 0040 (r1 HP     308C      6040000  LTP        0)
[    0.000000] ACPI: FACP 1F6EAE88, 0074 (r1 HP     308C      6040000 LOHR       5F)
[    0.000000] ACPI: DSDT 1F6E59D6, 54B2 (r1 HP     308C      6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1F6FBFC0, 0040
[    0.000000] ACPI: APIC 1F6EAEFC, 0068 (r1 HP     308C      6040000 LOHR       5F)
[    0.000000] ACPI: BOOT 1F6EAFD8, 0028 (r1 HP     308C      6040000  LTP        1)
[    0.000000] ACPI: MCFG 1F6EAF9C, 003C (r1 HP     308C      6040000 LOHR       5F)
[    0.000000] ACPI: SSDT 1F6E57FA, 01D8 (r1 HP     308C         3001 INTL 20030224)
[    0.000000] ACPI: SSDT 1F6E56E6, 0114 (r1 HP     308C         3000 INTL 20030224)
[    0.000000] ACPI: SSDT 1F6E55BA, 012C (r1 HP     308C            1 INTL 20030224)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] Built 1 zonelists.  Total pages: 127731
[    0.000000] Kernel command line: root=UUID=9e8c99d3-8862-4905-ae71-222d8d287b0d ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1396.995 MHz processor.
[   22.309849] Console: colour VGA+ 80x25
[   22.310056] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   22.310329] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.327236] Memory: 498828k/514944k available (2015k kernel code, 15432k reserved, 916k data, 364k init, 0k highmem)
[   22.327248] virtual kernel memory layout:
[   22.327249]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   22.327251]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.327253]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   22.327254]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[   22.327256]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   22.327257]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   22.327259]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   22.327264] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.327308] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.407335] Calibrating delay using timer specific routine.. 2813.43 BogoMIPS (lpj=5626869)
[   22.407368] Security Framework v1.0.0 initialized
[   22.407376] SELinux:  Disabled at boot.
[   22.407395] Mount-cache hash table entries: 512
[   22.407545] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[   22.407561] CPU: L1 I cache: 32K, L1 D cache: 32K
[   22.407564] CPU: L2 cache: 1024K
[   22.407567] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000
[   22.407578] Compat vDSO mapped to ffffe000.
[   22.407591] Checking 'hlt' instruction... OK.
[   22.423454] SMP alternatives: switching to UP code
[   22.423669] Freeing SMP alternatives: 11k freed
[   22.423987] Early unpacking initramfs... done
[   22.842037] ACPI: Core revision 20070126
[   22.842125] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.870660] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[   22.870689] Total of 1 processors activated (2813.43 BogoMIPS).
[   22.870889] ENABLING IO-APIC IRQs
[   22.871097] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.015393] Brought up 1 CPUs
[   23.015526] Booting paravirtualized kernel on bare hardware
[   23.015609] Time: 22:50:14  Date: 11/13/107
[   23.015636] NET: Registered protocol family 16
[   23.015732] EISA bus registered
[   23.015748] ACPI: bus type pci registered
[   23.016254] PCI: PCI BIOS revision 2.10 entry at 0xfd850, last bus=7
[   23.016256] PCI: Using configuration type 1
[   23.016258] Setting up standard PCI resources
[   23.027164] ACPI: EC: Look up EC in DSDT
[   23.027689] ACPI: EC: GPE=0x1b, ports=0x66, 0x62
[   23.028720] ACPI: Interpreter enabled
[   23.028724] ACPI: (supports S0 S3 S4 S5)
[   23.028743] ACPI: Using IOAPIC for interrupt routing
[   23.034490] ACPI: EC: GPE=0x1b, ports=0x66, 0x62
[   23.034554] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.034570] PCI: Probing PCI hardware (bus 00)
[   23.035331] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   23.035336] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   23.035848] PCI: Transparent bridge - 0000:00:1e.0
[   23.035962] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.036244] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   23.036399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   23.038773] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   23.038878] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   23.038980] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.039080] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   23.039181] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   23.039280] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   23.039416] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   23.039517] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   23.039625] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.039637] pnp: PnP ACPI init
[   23.039646] ACPI: bus type pnp registered
[   23.041837] pnp: PnP ACPI: found 8 devices
[   23.041841] ACPI: ACPI bus type pnp unregistered
[   23.041845] PnPBIOS: Disabled by ACPI PNP
[   23.041899] PCI: Using ACPI for IRQ routing
[   23.041903] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.041908] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   23.041966] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   23.042019] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   23.059486] NET: Registered protocol family 8
[   23.059489] NET: Registered protocol family 20
[   23.059559] pnp: 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[   23.059564] pnp: 00:04: iomem range 0xf0000000-0xf0003fff could not be reserved
[   23.059568] pnp: 00:04: iomem range 0xf0004000-0xf0004fff could not be reserved
[   23.059572] pnp: 00:04: iomem range 0xf0005000-0xf0005fff could not be reserved
[   23.063354] Time: tsc clocksource has been installed.
[   23.089914] PCI: Bridge: 0000:00:1c.0
[   23.089916]   IO window: disabled.
[   23.089922]   MEM window: disabled.
[   23.089927]   PREFETCH window: disabled.
[   23.089936] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   23.089939]   IO window: 00003400-000034ff
[   23.089944]   IO window: 00003800-000038ff
[   23.089951]   PREFETCH window: 30000000-33ffffff
[   23.089957]   MEM window: 38000000-3bffffff
[   23.089963] PCI: Bridge: 0000:00:1e.0
[   23.089966]   IO window: 3000-3fff
[   23.089973]   MEM window: b0100000-b01fffff
[   23.089978]   PREFETCH window: 30000000-33ffffff
[   23.090014] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   23.090023] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.090038] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   23.090057] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 17
[   23.090065] PCI: Setting latency timer of device 0000:06:06.0 to 64
[   23.090083] NET: Registered protocol family 2
[   23.127392] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.127436] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   23.127614] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   23.127741] TCP: Hash tables configured (established 16384 bind 16384)
[   23.127745] TCP reno registered
[   23.139512] checking if image is initramfs... it is
[   23.591368] Switched to high resolution mode on CPU 0
[   23.958729] Freeing initrd memory: 7121k freed
[   23.958913] Simple Boot Flag at 0x36 set to 0x1
[   23.959223] audit: initializing netlink socket (disabled)
[   23.959240] audit(1197586214.112:1): initialized
[   23.961545] VFS: Disk quotas dquot_6.5.1
[   23.961608] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.961720] io scheduler noop registered
[   23.961723] io scheduler anticipatory registered
[   23.961727] io scheduler deadline registered
[   23.961745] io scheduler cfq registered (default)
[   23.961763] Boot video device is 0000:00:02.0
[   23.961947] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.962006] assign_interrupt_mode Found MSI capability
[   23.962012] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.962051] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.962231] isapnp: Scanning for PnP cards...
[   24.318605] isapnp: No Plug & Play device found
[   24.353722] Real Time Clock Driver v1.12ac
[   24.353846] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.354762] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 18
[   24.354773] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[   24.355461] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.355723] input: Macintosh mouse button emulation as /class/input/input0
[   24.355818] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.361922] i8042.c: Detected active multiplexing controller, rev 1.1.
[   24.365275] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.365284] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.365287] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.365290] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.365293] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.365526] mice: PS/2 mouse device common for all mice
[   24.365953] EISA: Probing bus 0 at eisa.0
[   24.365963] Cannot allocate resource for EISA slot 1
[   24.365966] Cannot allocate resource for EISA slot 2
[   24.365969] Cannot allocate resource for EISA slot 3
[   24.365992] EISA: Detected 0 cards.
[   24.366112] TCP cubic registered
[   24.366140] NET: Registered protocol family 1
[   24.366171] Using IPI No-Shortcut mode
[   24.366375]   Magic number: 3:137:856
[   24.366497]   hash matches device ptyv8
[   24.366514]   hash matches device ptysb
[   24.366791] Freeing unused kernel memory: 364k freed
[   24.907251] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.307758] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   25.507645] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   25.597804] AppArmor: AppArmor initialized<5>audit(1197586216.112:2):  type=1505 info="AppArmor initialized" pid=1190
[   25.604337] fuse init (API version 7.8)
[   25.609138] Failure registering capabilities with primary security module.
[   25.623397] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    3.176000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.176000] ACPI: Thermal Zone [THR0] (75 C)
[    3.176000] ACPI: Invalid passive threshold
[    3.176000] ACPI: Thermal Zone [THR1] (52 C)
[    3.180000] Time: acpi_pm clocksource has been installed.
[    3.256000] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    3.456000] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    3.652000] usbcore: registered new interface driver usbfs
[    3.652000] usbcore: registered new interface driver hub
[    3.652000] usbcore: registered new device driver usb
[    3.656000] USB Universal Host Controller Interface driver v3.0
[    3.656000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.656000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.656000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.656000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.656000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.656000] usb usb1: configuration #1 chosen from 1 choice
[    3.656000] hub 1-0:1.0: USB hub found
[    3.656000] hub 1-0:1.0: 2 ports detected
[    3.760000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.760000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.760000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.760000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.760000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[    3.760000] usb usb2: configuration #1 chosen from 1 choice
[    3.760000] hub 2-0:1.0: USB hub found
[    3.760000] hub 2-0:1.0: 2 ports detected
[    3.800000] SCSI subsystem initialized
[    3.804000] libata version 2.21 loaded.
[    3.840000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.864000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    3.864000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.864000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.864000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.864000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001860
[    3.864000] usb usb3: configuration #1 chosen from 1 choice
[    3.864000] hub 3-0:1.0: USB hub found
[    3.864000] hub 3-0:1.0: 2 ports detected
[    3.968000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 22
[    3.968000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.968000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.968000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.968000] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00001880
[    3.968000] usb usb4: configuration #1 chosen from 1 choice
[    3.968000] hub 4-0:1.0: USB hub found
[    3.968000] hub 4-0:1.0: 2 ports detected
[    4.072000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.072000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.072000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.072000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.072000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.072000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.072000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xb0040000
[    4.104000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    4.104000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.104000] usb usb5: configuration #1 chosen from 1 choice
[    4.104000] hub 5-0:1.0: USB hub found
[    4.104000] hub 5-0:1.0: 8 ports detected
[    4.136000] Clocksource tsc unstable (delta = -64026966 ns)
[    4.208000] ata_piix 0000:00:1f.1: version 2.11
[    4.208000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[    4.208000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.208000] scsi0 : ata_piix
[    4.208000] scsi1 : ata_piix
[    4.208000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.208000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.536000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[    4.536000] ata1.00: ATA-6: ST9120822A, 3.ALD, max UDMA/100
[    4.536000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    4.536000] ata1.01: ATAPI: MATSHITAUJ-840D, 1.02, max MWDMA2
[    4.552000] ata1.00: configured for UDMA/100
[    4.668000] usb 5-4: configuration #1 chosen from 1 choice
[    4.724000] ata1.01: configured for MWDMA2
[    4.724000] ata2: port disabled. ignoring.
[    4.724000] scsi 0:0:0:0: Direct-Access     ATA      ST9120822A       3.AL PQ: 0 ANSI: 5
[    4.724000] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-840D          1.02 PQ: 0 ANSI: 5
[    4.728000] 8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.728000] 8139cp 0000:06:07.0: Try the "8139too" driver instead.
[    4.728000] 8139too Fast Ethernet driver 0.9.28
[    4.728000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 18
[    4.732000] eth0: RealTek RTL8139 at 0xe0048000, 00:0a:e4:dc:82:e0, IRQ 18
[    4.732000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.744000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.744000] sd 0:0:0:0: [sda] Write Protect is off
[    4.744000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.744000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.744000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    4.744000] sd 0:0:0:0: [sda] Write Protect is off
[    4.744000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.744000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.744000]  sda: sda1 sda2 < sda5 >
[    4.824000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.832000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.832000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    4.848000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.848000] Uniform CD-ROM driver Revision: 3.20
[    4.848000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    4.908000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[    5.076000] Attempting manual resume
[    5.076000] swsusp: Resume From Partition 8:5
[    5.076000] PM: Checking swsusp image.
[    5.076000] PM: Resume from disk failed.
[    5.128000] kjournald starting.  Commit interval 5 seconds
[    5.128000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.164000] usb 5-5: configuration #1 chosen from 1 choice
[    5.164000] usbcore: registered new interface driver libusual
[    5.176000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    5.176000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    5.176000] Initializing USB Mass Storage driver...
[    5.176000] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.176000] usb-storage: device found at 2
[    5.176000] usb-storage: waiting for device to settle before scanning
[    5.176000] usbcore: registered new interface driver usb-storage
[    5.176000] USB Mass Storage support registered.
[   10.176000] usb-storage: device scan complete
[   10.176000] scsi 2:0:0:0: Direct-Access     WD       5000AAC External 1.65 PQ: 0 ANSI: 0
[   10.176000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   10.176000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.176000] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   10.176000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.176000] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   10.176000] sd 2:0:0:0: [sdb] Write Protect is off
[   10.176000] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   10.176000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.176000]  sdb: sdb1
[   10.180000] sd 2:0:0:0: [sdb] Attached SCSI disk
[   10.180000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   15.272000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.320000] agpgart: Detected an Intel 915GM Chipset.
[   15.320000] agpgart: Detected 7932K stolen memory.
[   15.340000] agpgart: AGP aperture is 256M @ 0xc0000000
[   15.360000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.368000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.940000] iTCO_vendor_support: vendor-support=0
[   17.124000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   17.156000] Yenta: CardBus bridge found at 0000:06:06.0 [103c:3081]
[   17.156000] Yenta: Enabling burst memory read transactions
[   17.156000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.156000] Yenta: Routing CardBus interrupts to PCI
[   17.156000] Yenta TI: socket 0000:06:06.0, mfunc 0x00001002, devctl 0x64
[   17.256000] Linux video capture interface: v2.00
[   17.288000] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   17.388000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   17.388000] Socket status: 30000007
[   17.388000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   17.388000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   17.388000] cs: IO port probe 0x3000-0x3fff: clean.
[   17.388000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   17.388000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   17.468000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
[   17.480000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 16
[   17.480000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   17.488000] usbcore: registered new interface driver uvcvideo
[   17.488000] USB Video Class driver (v0.1.0)
[   17.488000] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   17.820000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[   17.824000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.824000] cs: IO port probe 0x820-0x8ff: clean.
[   17.824000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.824000] cs: IO port probe 0xa00-0xaff: clean.
[   17.972000] input: PS/2 Mouse as /class/input/input2
[   17.988000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   17.992000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.992000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.012000] intel_rng: FWH not detected
[   18.092000] usbcore: registered new interface driver snd-usb-audio
[   18.404000] intel8x0_measure_ac97_clock: measured 55471 usecs
[   18.404000] intel8x0: clocking to 48000
[   19.400000] lp: driver loaded but no devices found
[   19.456000] ndiswrapper version 1.45 loaded (smp=yes)
[   19.528000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   19.528000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 18
[   19.536000] ndiswrapper: using IRQ 18
[   19.896000] wlan0: ethernet device 00:14:a5:2c:cc:a9 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   19.896000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   19.896000] usbcore: registered new interface driver ndiswrapper
[   19.948000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   19.960000] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[   20.428000] EXT3 FS on sda1, internal journal
[   21.876000] ACPI: Battery Slot [BAT0] (battery present)
[   22.000000] No dock devices found.
[   22.084000] input: Power Button (FF) as /class/input/input4
[   22.088000] ACPI: Power Button (FF) [PWRF]
[   22.140000] input: Lid Switch as /class/input/input5
[   22.144000] ACPI: Lid Switch [LID0]
[   22.188000] input: Sleep Button (CM) as /class/input/input6
[   22.188000] ACPI: Sleep Button (CM) [SLPB]
[   22.212000] input: Power Button (CM) as /class/input/input7
[   22.212000] ACPI: Power Button (CM) [PWB]
[   22.276000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.308000] ACPI: AC Adapter [AC] (on-line)
[   24.036000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   27.928000] ppdev: user-space parallel port driver
[   28.332000] [drm] Initialized drm 1.1.0 20060810
[   28.376000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[   28.380000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   29.124000] audit(1197586242.429:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4987 profile="/usr/sbin/cupsd"
[   29.292000] apm: BIOS not found.
[   32.784000] Failure registering capabilities with primary security module.
[   33.444000] Bluetooth: Core ver 2.11
[   33.444000] NET: Registered protocol family 31
[   33.444000] Bluetooth: HCI device and connection manager initialized
[   33.444000] Bluetooth: HCI socket layer initialized
[   33.480000] Bluetooth: L2CAP ver 2.8
[   33.480000] Bluetooth: L2CAP socket layer initialized
[   33.712000] Bluetooth: RFCOMM socket layer initialized
[   33.712000] Bluetooth: RFCOMM TTY layer initialized
[   33.712000] Bluetooth: RFCOMM ver 1.8
[   34.516000] NET: Registered protocol family 10
[   34.516000] lo: Disabled Privacy Extensions
[   34.516000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   38.400000] NET: Registered protocol family 17
[   49.788000] eth0: no IPv6 routers present
[   57.356000] UDF-fs: No VRS found
[   57.520000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   57.536000] ISOFS: changing to secondary root


---

### Post by ridgeland on 2007-12-14
rsambuca,
I'm also trying to get a Logitech Pro9000 to work.
I went to the Berlios site,
got to the step about compile with Ubuntu 6.06 (hope it works for 7.04)
I have build-essential
I cannot get kernel-headers --- neither with apt-get or synaptics.
apt-get message:
"Package kernel-headers is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or
is only available from another source"

What next?

Info:
When I plug in the webcam dmesg | tail gives:
```
[15127.761271] usb 2-6: USB disconnect, address 3
[15137.979267] usb 1-3: new high speed USB device using ehci_hcd and address 4
[15138.238675] usb 1-3: configuration #1 chosen from 1 choice
[15138.238755] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
```
lsusb shows:
Bus 001 Device 004: ID 046d:0990 Logitech, Inc. 
lsmod | grep uvc:
```
uvcvideo               42500  0 
videodev               28160  1 uvcvideo
v4l1_compat            15236  2 uvcvideo,videodev
v4l2_common            25216  2 uvcvideo,videodev
usbcore               134280  8 snd_usb_audio,uvcvideo,snd_usb_lib,usblp,usbhid,uhci_hcd,ehci_hcd

```

Thanks for helping

---

### Post by rsambuca on 2007-12-14
@ridgeland - I think the packages you need can be found in synaptic under 'linux-headers-generic', and 'linux-headers-<yourkernelversion>-generic'.  Try installing those first, and then installing the uvcvideo drivers.

---

### Post by ridgeland on 2007-12-15
rsambuca,
I already had the linux-headers- files showing in synaptics as installed.
So I followed through with the edit to makefile and sudo make and sudo make install.  Seems to compile everything OK, no errors or warnings.  uvcvideo.ko is a new size 750KB, old was 50KB.
Still doesn't work.  So I booted the PC, still doesn't work. 
I only have Ekiga and camorama for tests.  Ekiga says there is no video device, camorama says it cannot to video device /dev/video0.   $ ls -al /dev/vi* shows that /dev/video0 is there.  Sudo camorama gets the same message.  If I unplug the webcam /dev/video0 goes away.  I tried the Berlios suggestion of removing the module and then plugging in the webcam still no luck.

Info as before is the same except there is now an additional line in lsmod | grep uvc:
compat_ioctl32          2304  1 uvcvideo
I'm not sure I'm using the same partition (and OS) as before.  I've tried a couple of Ubuntu's, all the same PC though.

---

### Post by rsambuca on 2007-12-15
Sorry guys, I am out of ideas here.

---

### Post by asnd16 on 2007-12-15
damm

---

### Post by jlidgard on 2007-12-19
I've got a similar problem with a Quickcam Messenger (046d:08da).
The driver loads OK & generates  /dev/video0.
I can get camorama to run only by using sudo camorama.
Permissions for this link are set as:
crw-rw---- 1 root video 81, 0 2007-12-19 12:40 /dev/video0
I have tried adding users to video group as suggested elsewhere but to no avail.
Any ideas? (Have compiled & loaded the latest gspca driver gspcav1-20071214.tar.gz)

---

### Post by ridgeland on 2007-12-19
Hi jlidgard,
Welcome to UbuntuForums!

I tried Fedora8 and SuSE10.3 but did not get my webcam working there either.  I even went so far as installing the webcam on my old PC in WinXP.  That showed me the camera does work.  Sudo camorama did not work for me.
I'll try some more after the holidays.  I have lots of bookmarks to chase down in Ubuntu, Fedora and SuSE.  I'll post back if any breakthrough.

---

### Post by kreucher on 2008-01-03
Same problem here. Using svn rev 159 and Quickcam Pro 9000.

Exact same camorama error, sudo make no difference. I _CAN_ however capture a still image using [http://staticwave.ca/source/uvccapture](http://staticwave.ca/source/uvccapture)

[17281183.432000] usbcore: registered new driver uvcvideo
[17282643.052000] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "UVC Camera (046d:0990)"
        bus_info                : "0000:00:1d.7"
        version                 : 0.1.0
        capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

Ubuntu 6.06.1 LTS

If anyone finds a solution, please post, and I will do the same.

---

### Post by ridgeland on 2008-01-14
Some success with SuSE 10.3
Following
[http://en.opensuse.org/HCL/Web_Cameras](http://en.opensuse.org/HCL/Web_Cameras)
I was able to get my Logitech Pro 9000 to work in kopete.
Then I tried a fresh install of SuSE 10.3 with the webcam already connected.  This time all I needed was to add the "RPM has" for Kopete's parent package and it worked.  Very simple.
The camera works in Kopete but Ekiga still gives an error message of "video driver doesn't support requested video format".
Although Ubuntu is my main OS I find it useful to dual-boot+ with SuSE and Fedora.  Also I leave partitions to play with other distros like Mint and Mandriva.

Ed:  I just tried a fresh install of Ubuntu 7.10 with the camera connected first.  Then added Kopete and the camera shows an image.  Adjusting color settings resulted in some image breakup in horizontal bars.  SuSE had better image, but it's working in Ubuntu 7.10.

---

### Post by donmiguel on 2008-02-09
did you guys find a proper solution? i have the exact same problem..

---

### Post by donmiguel on 2008-02-09
nevermind! I found the problem [here]("http://ubuntuforums.org/showthread.php?t=118517&p=963173").

> Now, UVC only supports the v4l2 API, not the v4l API, so this may be the problem with camorama, as (I believe) it only understand v4l. Ekiga, however, understands v4l2, and the webcam works perfectly with Ekiga.

So, camoramo simply doesn't seem to support v4l2.
Concerning Skype: I first went into EKIGA, configured there the cam (on v4l2 so it would work) and voilà, Skype tought that now it would also show me a picture when testing.. cool, skype totaly works under peer pressure :D

---

### Post by revel42 on 2008-02-18
Hi Guys

I also have the 9000. I have got some things to work.

Downloaded the driver from svn.berlios.de

Only the latest version of luvcview (20070512) compiles for me. And it only worked after I changed the privileges on dev/video0 to 777. [noob] Isn't this dangerous?? [/noob] Messing with the groups setup didn't seem to help.

Ekiga works (probably only with 777), at least in internal test mode. The video looks fine and the sound test works both recording my voice and playing it back.

Skype sucks. The sound recorded from the microphone is garbled nearly beyond recognition, which is actually more interesting than if it recorded nothing at all. There is no sign that Skype can see the video device. I have tried the ekiga trick to get skype working, no good for me.

---

### Post by fx|RabBit on 2008-04-08
first of all you should of course not change your/dev/video0 attributes to 777 but you ought to add your user to groups video and audio, for if you take a look, /dev/video0 belongs to user root and group video.
such as /dev/dspX belongs to user root and group audio
so do 
sudo adduser yourname audio
sudo adduser yourname video

this should resolve the problem for all of you having the "no device found" error (in case you got a /dev/video0).

further what concerns the freezing, cracking, dropping dead errors, those are mostly related to the following problem:
if you have a resolution set in your /home/yorname/.Skype/yourSkypeUser/conf.xml that is not supported by skype it closes immediately.
if you have the standard resolution and skype "drops dead" after a while or does funny things like
freezing the lower third of the picture while capturing on the upper two thirds this is due to a bug and i cant tell whether it is to be located in the uvcvideo driver or in skype or in debian/ubuntu in general.
however, when skype discovers that it can't deliver the default resolution - be it due to lack of network bandwith oder lack of harware power - it switches back to a lower resolution.
and that is exactly when the error occurs.

to circumvent this edit your  /home/yorname/.Skype/yourSkypeUser/conf.xml and add the following:
<video>
            <CaptureHeight>120</CaptureHeight>
            <CaptureWidth>160</CaptureWidth>
            <Fps>10</Fps>
</video>

these values set your resolution to 160x120pixels at 10frames per second.
this might not be too pretty but it keeps skype from crashing.
the values btw can differ according to hardware and bandwith so do experiment a little to find your optimal settings.
have fun!:popcorn:

ps.: you might consider using a different webcam:lolflag:

---

### Post by ridgeland on 2008-04-08
Thanks fx|RabBit,
I had only gotten Skype to be stable in SuSE.  Now with the edit to  config.xml Skype is stable in Ubuntu 8.04 for me.  Resolution is not great but now I have a starting point for fine tuning.
Thanks again.

---

