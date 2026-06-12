---
title: "Intel Graphics not detected when ATI Radeon plugged"
date: 2012-05-27
forum: Multimedia Software
---

### Post by sirfocus on 2012-05-27
Hello
this is my first post in this forum. I hope I can help people here the same I hope you can solve my problems when I have them ^^

Well, my situation is that I'm trying to connect two screens to my computer, and for that I need to plug a second graphic card. My motherboard has an integrated Intel Graphics G41 and I have another ATI Radeon X300SE plugged in the PCIE connector. I'm running Ubuntu 12.04 64bits.

The problems is that when I plug the external graphic card, the integrated one stops being detected. 

Here you have some outputs:

**lspci | grep VGA** *before* plugging the ATI Radeon:

```
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
```**lspci | grep VGA** *after* plugging the ATI Radeon:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV370 5B60 [Radeon X300 (PCIE)]
```**lshw** after plugging ATI Radeon (sorry, it's in spanish):

```
ruta H/W           Dispositivo  Clase       Descripción
========================================================
                                system      System Product Name (To Be Filled By O.E.M.)
/0                              bus         P5G41T-M/USB3
/0/0                            memory      64KiB BIOS
/0/4                            processor   Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
/0/4/5                          memory      128KiB L1 caché
/0/4/6                          memory      8MiB L2 caché
/0/29                           memory      8GiB Memoria de sistema
/0/29/0                         memory      4GiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-
/0/29/1                         memory      4GiB DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-
/0/100                          bridge      4 Series Chipset DRAM Controller
/0/100/1                        bridge      4 Series Chipset PCI Express Root Port
/0/100/1/0                      display     RV370 5B60 [Radeon X300 (PCIE)]
/0/100/1/0.1                    display     RV370 [Radeon X300SE]
/0/100/1b                       multimedia  N10/ICH 7 Family High Definition Audio Controller
/0/100/1c                       bridge      N10/ICH 7 Family PCI Express Port 1
/0/100/1c.1                     bridge      N10/ICH 7 Family PCI Express Port 2
/0/100/1c.1/0      eth0         network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                     bridge      N10/ICH 7 Family PCI Express Port 3
/0/100/1c.2/0                   bus         uPD720200 USB 3.0 Host Controller
/0/100/1d                       bus         N10/ICH 7 Family USB UHCI Controller #1
/0/100/1d.1                     bus         N10/ICH 7 Family USB UHCI Controller #2
/0/100/1d.2                     bus         N10/ICH 7 Family USB UHCI Controller #3
/0/100/1d.3                     bus         N10/ICH 7 Family USB UHCI Controller #4
/0/100/1d.7                     bus         N10/ICH 7 Family USB2 EHCI Controller
/0/100/1e                       bridge      82801 PCI Bridge
/0/100/1e/0                     network     BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
/0/100/1f                       bridge      82801GB/GR (ICH7 Family) LPC Interface Bridge
/0/100/1f.1        scsi0        storage     82801G (ICH7 Family) IDE Controller
/0/100/1f.1/0.1.0  /dev/cdrom   disk        DVD_RW ND-3500AG
/0/100/1f.2        scsi2        storage     N10/ICH7 Family SATA Controller [IDE mode]
/0/100/1f.2/0      /dev/sda     disk        320GB WDC WD3200AAJS-2
/0/100/1f.2/0/1    /dev/sda1    volume      39GiB partición EXT4
/0/100/1f.2/0/2    /dev/sda2    volume      2244MiB Linux swap volumen
/0/100/1f.2/0/3    /dev/sda3    volume      195GiB partición EXT4
/0/100/1f.2/1      /dev/cdrom1  disk        DVDRAM GH15F
/1                 wlan1        network     Interfaz inalámbrica
/2                 wlan0        network     Interfaz inalámbrica

```
Anybody can help me detecting both cards at the same time? Then I will have to fight against making both screens work but I need this first  :P

Thanks in advance!

---

### Post by ewz on 2012-05-27
Hello From what I know with on board graphics Cards is that when you plug in an AGP/PCIe/PCI Graphics Card it will automaticlly disable the on board card.

When I was setting up systems a few years ago, if you wanted duel Graphics you needed to ether have two graphics cards or one with duel ports, you couldn't use the intergrated graphics card. 

Maybe on new motherboards this has changed? I'm not sure 

hope this helps :)

---

### Post by sirfocus on 2012-05-28
Hi ewz
thanks for your answer :) a pity that it's disabled. Maybe I have any BIOS option that allows both graphic cards to work. I didn't check it. But is there no posibility that is ubuntu what disables it and not the motherboard?

Thanks!

---

### Post by Yellow Pasque on 2012-05-28
If it doesn't show in lspci, then it is definitely the BIOS that is disabling it (this is expected).

---

### Post by sirfocus on 2012-05-28
Hi everybody,

I achieved to activate dual mode in my BIOS. It had an option for it and now I have both graphic cards working but the monitor connected to the external graphic card has black screen (has video signal, but nothing appears). lspci detects both graphic cards but the new screen doesn't appear in the configuration (when I go to screen configuration I can only see one device, the one connected to the integrated card) so I cannot activate it. Does anybody know about a package or software necessary for making it work? In case it's not necessary, how can I make it be detected?

Thank you very much! ;)

EDIT: after rebooting the system, now the screen connected to the ATI card has no video signal and it goes into stand-by mode. The card is still detected by lspci.

EDIT2: xrandr seems to detect only one screen:

```
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+   60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1
```

---

### Post by ewz on 2012-05-29
hmmm I wonder if only the primary Driver is being loaded when Ubuntu starts, 

Do both screens work when you first turn on the computer?
I'm afraid the duel Video cards setups that I have done with Linux have always been the same make of card eg: Nvidia or ATI a few Matrox setups aswell, 

The other reason a monitor will go to standby is that it is out of range, 
the Resolution is to high maybe, or the Hsync - Vsync is is not detected properly 

Sorry I can't help more,

---

### Post by sirfocus on 2012-05-29
No, the screen connected to the ATI card never turns on, even during the POST. I guess the BIOS stablishes the integrated one as primary. But Ubuntu can detect the screen. Once Ubuntu starts it can be a problem of resolution, because the other screen is bigger and has higher resolution, but I cannot try it now as I am in the university. I will try when I arrive.

Anyway I think that Ubuntu should be able to deal with both cards if they are both detected. Yesterday I installed ATI drivers to try to wake up the ATI card, but then gnome-shell crashed and the card still didn't work. I uninstalled it and reinstalled the open drivers. I also tried installing KDE and here I had the same situation (integrated working, ATI no signal), but this time the working screen was detected as VGA-2, but still xrandr only showed this screen. 
I don't understand how it can know that there are two screens (or at least two outputs) and it only shows one in xrandr and the configuration. Any idea?

Thanks for your help!

EDIT: Now that I installed KDE and I have KDE startup screen, this screen appears in the second monitor and then the first monitor goes black. Then when everything is up the video goes back to the first monitor. Any help?

---

### Post by sirfocus on 2012-05-30
First of all, sorry for the double post but I think this info can be relevant.

Here you can see the output of dmseg just after the startup and after trying to change monitors configuration. As I said, the second screen does not appear in the configuration so the only change I could do was changing the resolution of the main screen. 
Anyway, during the startup with KDE screen, the second monitor is active and then deactivated once the startup ends, so maybe someone can draw a conclusion by checking the first dmesg. I only see a bunch of frequency updates.

**First dmesg (just after startup)**

```
[    0.920349] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.920370] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.920489] hub 2-0:1.0: USB hub found
[    0.920493] hub 2-0:1.0: 2 ports detected
[    0.920551] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.920559] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.920562] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.920602] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.920632] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c480
[    0.920743] hub 3-0:1.0: USB hub found
[    0.920746] hub 3-0:1.0: 2 ports detected
[    0.920803] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.920809] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.920812] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.920852] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.920880] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
[    0.920990] hub 4-0:1.0: USB hub found
[    0.920994] hub 4-0:1.0: 2 ports detected
[    0.921057] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.921063] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.921066] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.921109] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.921138] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c880
[    0.921255] hub 5-0:1.0: USB hub found
[    0.921259] hub 5-0:1.0: 2 ports detected
[    0.921332] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.921346] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    0.921350] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    0.921390] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 6
[    0.921533] xhci_hcd 0000:02:00.0: irq 18, io mem 0xfeafa000
[    0.921592] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    0.921598] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    0.921602] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    0.921606] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    0.921610] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    0.921758] xHCI xhci_add_endpoint called for root hub
[    0.921760] xHCI xhci_check_bandwidth called for root hub
[    0.921787] hub 6-0:1.0: USB hub found
[    0.921794] hub 6-0:1.0: 2 ports detected
[    0.921846] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    0.921888] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 7
[    0.924947] xHCI xhci_add_endpoint called for root hub
[    0.924949] xHCI xhci_check_bandwidth called for root hub
[    0.924980] hub 7-0:1.0: USB hub found
[    0.924990] hub 7-0:1.0: 2 ports detected
[    0.960104] usbcore: registered new interface driver libusual
[    0.960161] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.962947] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.962958] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.963082] mousedev: PS/2 mouse device common for all mice
[    0.963212] rtc_cmos 00:03: RTC can wake from S4
[    0.963306] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.963332] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.963404] device-mapper: uevent: version 1.0.3
[    0.963471] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.963477] cpuidle: using governor ladder
[    0.963479] cpuidle: using governor menu
[    0.963481] EFI Variables Facility v0.08 2004-May-17
[    0.963694] TCP cubic registered
[    0.963799] NET: Registered protocol family 10
[    0.964234] NET: Registered protocol family 17
[    0.964248] Registering the dns_resolver key type
[    0.964356] PM: Hibernation image not present or could not be loaded.
[    0.964366] registered taskstats version 1
[    0.990094]   Magic number: 12:234:478
[    0.990099] rtc rtc0: hash matches
[    0.990199] rtc_cmos 00:03: setting system clock to 2012-05-30 10:27:59 UTC (1338373679)
[    0.990223] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.990224] EDD information not available.
[    1.004211] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.078261] ata1.01: ATAPI: _NEC DVD_RW ND-3500AG, 2.58, max UDMA/33
[    1.078466] ata3.01: ATA-8: WDC WD3200AAJS-22B4A0, 01.03A01, max UDMA/133
[    1.078471] ata3.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.084332] ata4.01: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
[    1.085070] ata3.01: configured for UDMA/133
[    1.092213] ata1.01: configured for UDMA/33
[    1.093480] scsi 0:0:1:0: CD-ROM            _NEC     DVD_RW ND-3500AG 2.58 PQ: 0 ANSI: 5
[    1.094629] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.094633] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.094773] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.094905] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.095026] scsi 2:0:1:0: Direct-Access     ATA      WDC WD3200AAJS-2 01.0 PQ: 0 ANSI: 5
[    1.095138] sd 2:0:1:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.095167] sd 2:0:1:0: Attached scsi generic sg1 type 0
[    1.095197] sd 2:0:1:0: [sda] Write Protect is off
[    1.095201] sd 2:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    1.095228] sd 2:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.100155] ata4.01: configured for UDMA/100
[    1.105527] scsi 3:0:1:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ: 0 ANSI: 5
[    1.111384] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.111519] sr 3:0:1:0: Attached scsi CD-ROM sr1
[    1.111626] sr 3:0:1:0: Attached scsi generic sg2 type 5
[    1.127158]  sda: sda1 sda2 sda3
[    1.127498] sd 2:0:1:0: [sda] Attached SCSI disk
[    1.129021] Freeing unused kernel memory: 920k freed
[    1.129213] Write protecting the kernel read-only data: 12288k
[    1.134374] Freeing unused kernel memory: 1608k freed
[    1.138512] Freeing unused kernel memory: 1196k freed
[    1.155872] udevd[107]: starting version 175
[    1.186047] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.186071] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.186103] r8169 0000:03:00.0: setting latency timer to 64
[    1.186159] r8169 0000:03:00.0: irq 49 for MSI/MSI-X
[    1.186603] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xffffc90000c78000, bc:ae:c5:83:df:a0, XID 0c200000 IRQ 49
[    1.186606] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.187877] [drm] Initialized drm 1.1.0 20060810
[    1.198748] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.199594] [drm] radeon defaulting to kernel modesetting.
[    1.199597] [drm] radeon kernel modesetting enabled.
[    1.199666] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[    1.199674] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.199681] radeon 0000:01:00.0: setting latency timer to 64
[    1.199953] [drm] initializing kernel modesetting (RV380 0x1002:0x5B60 0x174B:0x0500).
[    1.199982] [drm] register mmio base: 0xD0000000
[    1.199984] [drm] register mmio size: 65536
[    1.209983] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.210023] i915 0000:00:02.0: setting latency timer to 64
[    1.216225] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.216278] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.216331] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.216376] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.260120] [drm] GPU not posted. posting now...
[    1.260141] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    1.344033] usb 1-4: new high-speed USB device number 3 using ehci_hcd
[    1.366847] [drm] Generation 2 PCI interface, using max accessible memory
[    1.366853] radeon 0000:01:00.0: VRAM: 128M 0x00000000B0000000 - 0x00000000B7FFFFFF (128M used)
[    1.366856] radeon 0000:01:00.0: GTT: 512M 0x0000000090000000 - 0x00000000AFFFFFFF
[    1.366894] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.366896] [drm] Driver supports precise vblank timestamp query.
[    1.366942] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
[    1.366947] radeon 0000:01:00.0: radeon: using MSI.
[    1.366968] [drm] radeon: irq initialized.
[    1.369920] [drm] Detected VRAM RAM=128M, BAR=128M
[    1.369923] [drm] RAM width 64bits DDR
[    1.370018] [TTM] Zone  kernel: Available graphics memory: 4023404 kiB.
[    1.370026] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    1.370028] [TTM] Initializing pool allocator.
[    1.370053] [drm] radeon: 128M of VRAM memory ready
[    1.370055] [drm] radeon: 512M of GTT memory ready.
[    1.370074] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.370626] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[    1.371455] [drm] PCIE GART of 512M enabled (table at 0x00000000B0040000).
[    1.371477] radeon 0000:01:00.0: WB enabled
[    1.371537] [drm] Loading R300 Microcode
[    1.373096] [drm] radeon: ring at 0x0000000090001000
[    1.373115] [drm] ring test succeeded in 1 usecs
[    1.373223] [drm] radeon: ib pool ready.
[    1.373294] [drm] ib test succeeded in 0 usecs
[    1.373448] [drm] Radeon Display Connectors
[    1.373450] [drm] Connector 0:
[    1.373452] [drm]   VGA
[    1.373454] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    1.373455] [drm]   Encoders:
[    1.373457] [drm]     CRT1: INTERNAL_DAC1
[    1.435481] [drm] fb mappable at 0xB00C0000
[    1.435484] [drm] vram apper at 0xB0000000
[    1.435485] [drm] size 4227072
[    1.435487] [drm] fb depth is 24
[    1.435488] [drm]    pitch is 5504
[    1.435630] Console: switching to colour frame buffer device 170x48
[    1.435651] fb0: radeondrmfb frame buffer device
[    1.435653] drm: registered panic notifier
[    1.435659] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[    1.476783] hub 1-4:1.0: USB hub found
[    1.476849] hub 1-4:1.0: 4 ports detected
[    1.482988] Refined TSC clocksource calibration: 2400.681 MHz.
[    1.482998] Switching to clocksource tsc
[    1.489939] mtrr: no more MTRRs available
[    1.489941] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    1.490300] i915 0000:00:02.0: irq 51 for MSI/MSI-X
[    1.490304] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.490306] [drm] Driver supports precise vblank timestamp query.
[    1.516027] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    1.516033] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    1.588024] usb 1-8: new high-speed USB device number 4 using ehci_hcd
[    1.607244] fbcon: inteldrmfb (fb1) is primary device
[    1.607247] fbcon: Remapping primary device, fb1, to tty 1-63
[    1.646168] fb1: inteldrmfb frame buffer device
[    1.646178] No ACPI video bus found
[    1.646222] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[    1.988026] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[    2.426038] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   14.478518] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.493249] udevd[365]: starting version 175
[   14.512725] lp: driver loaded but no devices found
[   14.546015] parport_pc 00:06: reported by Plug and Play ACPI
[   14.546125] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   14.566919] intel_rng: FWH not detected
[   14.575236] type=1400 audit(1338373693.080:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
[   14.575620] type=1400 audit(1338373693.080:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[   14.575841] type=1400 audit(1338373693.080:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[   14.577098] cfg80211: Calling CRDA to update world regulatory domain
[   14.598132] leds_ss4200: no LED devices found
[   14.602785] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   14.625778] Linux video capture interface: v2.00
[   14.626150] gspca_main: v2.14.0 registered
[   14.627993] gspca_main: ov519-2.14.0 probing 054c:0154
[   14.632908] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.632969] snd_hda_intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[   14.632998] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   14.640168] lp0: using parport0 (interrupt-driven).
[   14.672850] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.672854] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672856] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.672859] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672861] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.672864] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672866] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.672869] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672871] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.672873] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672876] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.672878] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672880] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.672883] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672885] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.672888] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672890] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.672892] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672894] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.672897] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672899] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.672902] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   14.672904] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.672907] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   14.672909] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.672911] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   14.672914] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   14.672916] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   14.678469] Adding 2297852k swap on /dev/sda2.  Priority:-1 extents:1 across:2297852k 
[   14.690434] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.691984] hda_codec: ALC887: BIOS auto-probing.
[   14.693511] Registered led device: b43-phy0::radio
[   14.693548] Broadcom 43xx driver loaded [ Features: PNL ]
[   14.714545] HDMI status: Codec=1 Pin=3 Presence_Detect=0 ELD_Valid=0
[   14.714637] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input3
[   14.714727] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   14.714797] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   14.714867] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.714940] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.715008] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.721275] ppdev: user-space parallel port driver
[   14.730574] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   14.730578] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730581] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   14.730583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730586] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   14.730588] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730590] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   14.730593] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730595] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   14.730598] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730600] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   14.730602] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730604] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   14.730607] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730609] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   14.730612] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730614] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   14.730616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730618] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   14.730621] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730623] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   14.730625] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730627] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   14.730630] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.730632] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.730635] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.730637] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   14.730639] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.730643] cfg80211: World regulatory domain updated:
[   14.730644] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.730647] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730649] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.730652] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.730654] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.730657] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.840061] usb 1-8: reset high-speed USB device number 4 using ehci_hcd
[   14.856493] input: ov519 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/input/input9
[   14.856684] usbcore: registered new interface driver ov519
[   14.864641] usbcore: registered new interface driver snd-usb-audio
[   15.010554] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.010558] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010561] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.010563] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010565] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.010568] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010570] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.010573] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010575] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.010578] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010580] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.010583] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010585] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.010588] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010590] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.010593] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010595] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.010597] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010599] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.010602] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010604] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.010606] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.010608] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.010611] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.010613] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.010616] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.010618] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   15.010620] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.010743] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[   15.011274] Registered led device: rt2800usb-phy1::radio
[   15.011303] Registered led device: rt2800usb-phy1::assoc
[   15.011336] Registered led device: rt2800usb-phy1::quality
[   15.011372] usbcore: registered new interface driver rt2800usb
[   15.280702] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.359949] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input10
[   15.451592] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: user_xattr
[   17.027071] init: failsafe main process (923) killed by TERM signal
[   17.131691] Bluetooth: Core ver 2.16
[   17.131712] NET: Registered protocol family 31
[   17.131714] Bluetooth: HCI device and connection manager initialized
[   17.131718] Bluetooth: HCI socket layer initialized
[   17.131720] Bluetooth: L2CAP socket layer initialized
[   17.131726] Bluetooth: SCO socket layer initialized
[   17.133602] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.133604] Bluetooth: BNEP filters: protocol multicast
[   17.136401] Bluetooth: RFCOMM TTY layer initialized
[   17.136405] Bluetooth: RFCOMM socket layer initialized
[   17.136407] Bluetooth: RFCOMM ver 1.11
[   17.147176] type=1400 audit(1338373695.652:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=992 comm="apparmor_parser"
[   17.147656] type=1400 audit(1338373695.652:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=992 comm="apparmor_parser"
[   17.170183] type=1400 audit(1338373695.676:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1030 comm="apparmor_parser"
[   17.170199] type=1400 audit(1338373695.676:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1031 comm="apparmor_parser"
[   17.170596] type=1400 audit(1338373695.676:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1031 comm="apparmor_parser"
[   17.170822] type=1400 audit(1338373695.676:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1031 comm="apparmor_parser"
[   17.171789] type=1400 audit(1338373695.676:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1034 comm="apparmor_parser"
[   17.342268] init: kdm main process (1091) killed by TERM signal
[   17.392853] vboxdrv: Found 4 processor cores.
[   17.393189] vboxdrv: fAsync=0 offMin=0x3ba offMax=0x1e57
[   17.393747] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   17.393751] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   17.399553] r8169 0000:03:00.0: eth0: link down
[   17.400425] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.400863] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.405705] vboxpci: IOMMU not found (not registered)
[   17.765008] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   17.765335] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   17.936057] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   18.005195] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.005481] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.151216] init: plymouth-stop pre-start process (1435) terminated with status 1
[   21.308238] wlan1: authenticate with 02:1e:58:41:f0:7b (try 1)
[   21.309875] wlan1: authenticated
[   21.364238] wlan1: associate with 02:1e:58:41:f0:7b (try 1)
[   21.366259] wlan1: RX AssocResp from 02:1e:58:41:f0:7b (capab=0x411 status=0 aid=1)
[   21.366264] wlan1: associated
[   21.375151] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   32.256050] wlan1: no IPv6 routers present
[   54.316040] ieee80211 phy1: wlan1: No probe response from AP 02:1e:58:41:f0:7b after 500ms, disconnecting.
[   54.501216] cfg80211: All devices are disconnected, going to restore regulatory settings
[   54.501231] cfg80211: Restoring regulatory settings
[   54.501237] cfg80211: Calling CRDA to update world regulatory domain
[   54.504964] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   54.504968] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504971] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   54.504974] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504976] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   54.504978] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504980] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   54.504983] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504985] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   54.504988] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504990] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   54.504993] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504995] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   54.504997] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.504999] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   54.505002] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505004] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   54.505007] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505009] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   54.505011] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505013] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   54.505016] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505018] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   54.505021] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505023] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   54.505025] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505027] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   54.505030] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505033] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   54.505036] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505038] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   54.505040] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505042] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   54.505045] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505047] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   54.505050] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505052] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   54.505054] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505056] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   54.505059] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505061] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   54.505063] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505065] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   54.505068] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505070] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   54.505073] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505075] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   54.505077] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505079] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   54.505082] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505084] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   54.505087] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505089] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   54.505091] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505093] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   54.505096] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505098] cfg80211: World regulatory domain updated:
[   54.505100] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   54.505103] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505105] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505108] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   54.505110] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   54.505112] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   55.828575] wlan1: authenticate with 02:1e:58:41:f0:7b (try 1)
[   55.830208] wlan1: authenticated
[   55.848065] wlan1: associate with 02:1e:58:41:f0:7b (try 1)
[   55.850198] wlan1: RX ReassocResp from 02:1e:58:41:f0:7b (capab=0x411 status=0 aid=1)
[   55.850201] wlan1: associated
[   68.308021] ieee80211 phy1: wlan1: No probe response from AP 02:1e:58:41:f0:7b after 500ms, disconnecting.
[   68.385100] cfg80211: All devices are disconnected, going to restore regulatory settings
[   68.385105] cfg80211: Restoring regulatory settings
[   68.385109] cfg80211: Calling CRDA to update world regulatory domain
[   68.388527] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   68.388531] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388534] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   68.388536] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388539] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   68.388541] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388543] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   68.388546] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388548] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   68.388551] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388553] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   68.388555] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388557] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   68.388560] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388562] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   68.388564] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388566] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   68.388569] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388571] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   68.388573] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388575] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   68.388578] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388580] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   68.388583] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388585] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   68.388587] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388589] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   68.388592] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388595] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   68.388598] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388600] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   68.388602] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388604] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   68.388607] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388609] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   68.388612] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388614] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   68.388616] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388618] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   68.388621] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388623] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   68.388625] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388627] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   68.388630] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388632] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   68.388635] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388636] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   68.388639] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388641] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   68.388644] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388646] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   68.388648] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388650] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   68.388653] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388655] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   68.388657] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388660] cfg80211: World regulatory domain updated:
[   68.388661] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   68.388664] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388666] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388669] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   68.388671] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   68.388674] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   69.685024] wlan1: authenticate with 02:1e:58:41:f0:7b (try 1)
[   69.884016] wlan1: authenticate with 02:1e:58:41:f0:7b (try 2)
[   70.084020] wlan1: authenticate with 02:1e:58:41:f0:7b (try 3)
[   70.284125] wlan1: authentication with 02:1e:58:41:f0:7b timed out
[   84.287312] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  101.540721] wlan1: authenticate with 02:1e:58:41:f0:7b (try 1)
[  101.547479] wlan1: authenticated
[  101.551588] wlan1: associate with 02:1e:58:41:f0:7b (try 1)
[  101.577838] wlan1: RX ReassocResp from 02:1e:58:41:f0:7b (capab=0x411 status=0 aid=1)
[  101.577842] wlan1: associated
[  101.586760] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  109.071638] show_signal_msg: 45 callbacks suppressed
[  109.071643] Xorg[1173]: segfault at c0 ip 00007f9b024bd558 sp 00007fff9f4443b0 error 4 in Xorg[7f9b02468000+1f0000]
[  113.712015] wlan1: no IPv6 routers present

```**Second dmesg (after trying conf changes, only new messages shown)**

```
[  496.304076] ieee80211 phy1: wlan1: No probe response from AP 02:1e:58:41:f0:7b after 500ms, disconnecting.
[  496.385164] cfg80211: All devices are disconnected, going to restore regulatory settings
[  496.385171] cfg80211: Restoring regulatory settings
[  496.385176] cfg80211: Calling CRDA to update world regulatory domain
[  496.388691] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  496.388695] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388697] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  496.388700] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388702] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  496.388705] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388707] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  496.388709] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388712] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  496.388714] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388716] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  496.388719] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388721] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  496.388724] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388726] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  496.388728] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388730] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  496.388733] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388735] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  496.388738] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388740] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  496.388742] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388744] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  496.388747] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388749] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  496.388752] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388754] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  496.388756] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388760] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  496.388762] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388764] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  496.388767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388769] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  496.388772] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388774] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  496.388776] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388778] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  496.388781] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388783] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  496.388786] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388788] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  496.388791] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388793] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  496.388795] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388797] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  496.388800] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388802] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  496.388804] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388806] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  496.388809] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388811] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  496.388814] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388816] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  496.388819] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388821] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  496.388823] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388826] cfg80211: World regulatory domain updated:
[  496.388827] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  496.388830] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388833] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388835] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  496.388837] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  496.388840] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  497.684705] wlan1: authenticate with 02:1e:58:41:f0:7b (try 1)
[  497.884022] wlan1: authenticate with 02:1e:58:41:f0:7b (try 2)
[  498.084034] wlan1: authenticate with 02:1e:58:41:f0:7b (try 3)
[  498.090265] wlan1: authenticated
[  498.108243] wlan1: associate with 02:1e:58:41:f0:7b (try 1)
[  498.265681] wlan1: RX ReassocResp from 02:1e:58:41:f0:7b (capab=0x411 status=0 aid=1)
[  498.265685] wlan1: associated

```

Thanks everybody!

EDIT: I think Xorg log can be usefull:

```
[   111.404] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   111.404] X Protocol Version 11, Revision 0
[   111.404] Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
[   111.404] Current Operating System: Linux sirfocus-sobremesa 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64
[   111.404] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=b0f4ec82-58d4-4c03-a9d2-c05c8440ef21 ro quiet splash vt.handoff=7
[   111.404] Build Date: 07 May 2012  11:43:21PM
[   111.404] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support) 
[   111.404] Current version of pixman: 0.24.4
[   111.404]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   111.404] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   111.404] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May 30 12:29:49 2012
[   111.404] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   111.404] (==) No Layout section.  Using the first Screen section.
[   111.404] (==) No screen section available. Using defaults.
[   111.404] (**) |-->Screen "Default Screen Section" (0)
[   111.404] (**) |   |-->Monitor "<default monitor>"
[   111.404] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   111.405] (==) Automatically adding devices
[   111.405] (==) Automatically enabling devices
[   111.405] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   111.405]     Entry deleted from font path.
[   111.405] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   111.405]     Entry deleted from font path.
[   111.405] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   111.405]     Entry deleted from font path.
[   111.405] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   111.405]     Entry deleted from font path.
[   111.405] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   111.405]     Entry deleted from font path.
[   111.405] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   111.405] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   111.405] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   111.405] (II) Loader magic: 0x7f8e633b3b00
[   111.405] (II) Module ABI versions:
[   111.405]     X.Org ANSI C Emulation: 0.4
[   111.405]     X.Org Video Driver: 11.0
[   111.405]     X.Org XInput driver : 16.0
[   111.405]     X.Org Server Extension : 6.0
[   111.405] (--) PCI:*(0:0:2:0) 8086:2e32:1043:836d rev 3, Mem @ 0xcfc00000/4194304, 0xa0000000/268435456, I/O @ 0x0000cc00/8
[   111.406] (--) PCI: (0:1:0:0) 1002:5b60:174b:0500 rev 0, Mem @ 0xb0000000/134217728, 0xd0000000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[   111.406] (--) PCI: (0:1:0:1) 1002:5b70:174b:0501 rev 0, Mem @ 0xefff0000/65536
[   111.406] (II) Open ACPI successful (/var/run/acpid.socket)
[   111.406] (II) LoadModule: "extmod"
[   111.406] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   111.406] (II) Module extmod: vendor="X.Org Foundation"
[   111.406]     compiled for 1.11.3, module version = 1.0.0
[   111.406]     Module class: X.Org Server Extension
[   111.406]     ABI class: X.Org Server Extension, version 6.0
[   111.406] (II) Loading extension MIT-SCREEN-SAVER
[   111.406] (II) Loading extension XFree86-VidModeExtension
[   111.406] (II) Loading extension XFree86-DGA
[   111.406] (II) Loading extension DPMS
[   111.406] (II) Loading extension XVideo
[   111.406] (II) Loading extension XVideo-MotionCompensation
[   111.406] (II) Loading extension X-Resource
[   111.406] (II) LoadModule: "dbe"
[   111.406] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   111.407] (II) Module dbe: vendor="X.Org Foundation"
[   111.407]     compiled for 1.11.3, module version = 1.0.0
[   111.407]     Module class: X.Org Server Extension
[   111.407]     ABI class: X.Org Server Extension, version 6.0
[   111.407] (II) Loading extension DOUBLE-BUFFER
[   111.407] (II) LoadModule: "glx"
[   111.407] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   111.407] (II) Module glx: vendor="X.Org Foundation"
[   111.407]     compiled for 1.11.3, module version = 1.0.0
[   111.407]     ABI class: X.Org Server Extension, version 6.0
[   111.407] (==) AIGLX enabled
[   111.407] (II) Loading extension GLX
[   111.407] (II) LoadModule: "record"
[   111.407] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   111.407] (II) Module record: vendor="X.Org Foundation"
[   111.407]     compiled for 1.11.3, module version = 1.13.0
[   111.407]     Module class: X.Org Server Extension
[   111.407]     ABI class: X.Org Server Extension, version 6.0
[   111.407] (II) Loading extension RECORD
[   111.407] (II) LoadModule: "dri"
[   111.408] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   111.408] (II) Module dri: vendor="X.Org Foundation"
[   111.408]     compiled for 1.11.3, module version = 1.0.0
[   111.408]     ABI class: X.Org Server Extension, version 6.0
[   111.408] (II) Loading extension XFree86-DRI
[   111.408] (II) LoadModule: "dri2"
[   111.408] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   111.408] (II) Module dri2: vendor="X.Org Foundation"
[   111.408]     compiled for 1.11.3, module version = 1.2.0
[   111.408]     ABI class: X.Org Server Extension, version 6.0
[   111.408] (II) Loading extension DRI2
[   111.408] (==) Matched intel as autoconfigured driver 0
[   111.408] (==) Matched vesa as autoconfigured driver 1
[   111.408] (==) Matched fbdev as autoconfigured driver 2
[   111.408] (==) Assigned the driver to the xf86ConfigLayout
[   111.408] (II) LoadModule: "intel"
[   111.408] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   111.409] (II) Module intel: vendor="X.Org Foundation"
[   111.409]     compiled for 1.11.3, module version = 2.17.0
[   111.409]     Module class: X.Org Video Driver
[   111.409]     ABI class: X.Org Video Driver, version 11.0
[   111.409] (II) LoadModule: "vesa"
[   111.409] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   111.409] (II) Module vesa: vendor="X.Org Foundation"
[   111.409]     compiled for 1.11.3, module version = 2.3.0
[   111.409]     Module class: X.Org Video Driver
[   111.409]     ABI class: X.Org Video Driver, version 11.0
[   111.409] (II) LoadModule: "fbdev"
[   111.409] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   111.409] (II) Module fbdev: vendor="X.Org Foundation"
[   111.409]     compiled for 1.11.3, module version = 0.4.2
[   111.409]     ABI class: X.Org Video Driver, version 11.0
[   111.409] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   111.409] (II) VESA: driver for VESA chipsets: vesa
[   111.409] (II) FBDEV: driver for framebuffer: fbdev
[   111.409] (++) using VT number 7

[   111.411] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   111.411] (WW) Falling back to old probe method for vesa
[   111.411] (WW) Falling back to old probe method for fbdev
[   111.411] (II) Loading sub module "fbdevhw"
[   111.411] (II) LoadModule: "fbdevhw"
[   111.411] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   111.411] (II) Module fbdevhw: vendor="X.Org Foundation"
[   111.411]     compiled for 1.11.3, module version = 0.0.2
[   111.411]     ABI class: X.Org Video Driver, version 11.0
[   111.411] drmOpenDevice: node name is /dev/dri/card0
[   111.411] drmOpenDevice: open result is 9, (OK)
[   111.411] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   111.411] drmOpenDevice: node name is /dev/dri/card0
[   111.411] drmOpenDevice: open result is 9, (OK)
[   111.411] drmOpenByBusid: drmOpenMinor returns 9
[   111.411] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   111.412] drmOpenDevice: node name is /dev/dri/card1
[   111.412] drmOpenDevice: open result is 9, (OK)
[   111.412] drmOpenByBusid: drmOpenMinor returns 9
[   111.412] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   111.412] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   111.412] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   111.412] (==) intel(0): RGB weight 888
[   111.412] (==) intel(0): Default visual is TrueColor
[   111.412] (II) intel(0): Integrated Graphics Chipset: Intel(R) G41
[   111.412] (--) intel(0): Chipset: "G41"
[   111.412] (**) intel(0): Relaxed fencing enabled
[   111.412] (**) intel(0): Wait on SwapBuffers? enabled
[   111.412] (**) intel(0): Triple buffering? enabled
[   111.412] (**) intel(0): Framebuffer tiled
[   111.412] (**) intel(0): Pixmaps tiled
[   111.412] (**) intel(0): 3D buffers tiled
[   111.412] (**) intel(0): SwapBuffers wait enabled
[   111.412] (==) intel(0): video overlay key set to 0x101fe
[   111.479] (II) intel(0): Output VGA2 has no monitor section
[   111.563] (II) intel(0): EDID for output VGA2
[   111.563] (II) intel(0): Manufacturer: GSM  Model: 4e61  Serial#: 198881
[   111.563] (II) intel(0): Year: 2008  Week: 1
[   111.563] (II) intel(0): EDID Version: 1.3
[   111.563] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   111.563] (II) intel(0): Sync:  Separate  Composite
[   111.563] (II) intel(0): Max Image Size [cm]: horiz.: 43  vert.: 27
[   111.563] (II) intel(0): Gamma: 2.20
[   111.563] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   111.563] (II) intel(0): First detailed timing is preferred mode
[   111.563] (II) intel(0): redX: 0.640 redY: 0.352   greenX: 0.288 greenY: 0.628
[   111.563] (II) intel(0): blueX: 0.147 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[   111.563] (II) intel(0): Supported established timings:
[   111.563] (II) intel(0): 720x400@70Hz
[   111.563] (II) intel(0): 640x480@60Hz
[   111.563] (II) intel(0): 640x480@75Hz
[   111.563] (II) intel(0): 800x600@56Hz
[   111.563] (II) intel(0): 800x600@60Hz
[   111.563] (II) intel(0): 800x600@75Hz
[   111.563] (II) intel(0): 832x624@75Hz
[   111.563] (II) intel(0): 1024x768@60Hz
[   111.563] (II) intel(0): 1024x768@75Hz
[   111.563] (II) intel(0): 1280x1024@75Hz
[   111.563] (II) intel(0): 1152x864@75Hz
[   111.563] (II) intel(0): Manufacturer's mask: 0
[   111.563] (II) intel(0): Supported standard timings:
[   111.563] (II) intel(0): #0: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   111.563] (II) intel(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   111.563] (II) intel(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   111.563] (II) intel(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   111.563] (II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   111.563] (II) intel(0): Supported detailed timing:
[   111.563] (II) intel(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
[   111.563] (II) intel(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[   111.563] (II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[   111.563] (II) intel(0): Supported detailed timing:
[   111.563] (II) intel(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
[   111.563] (II) intel(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[   111.563] (II) intel(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[   111.563] (II) intel(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 155 MHz
[   111.563] (II) intel(0): Monitor name: M208WA
[   111.563] (II) intel(0): EDID (in hex):
[   111.563] (II) intel(0):     00ffffffffffff001e6d614ee1080300
[   111.563] (II) intel(0):     011201030c2b1b78eacfc5a35a49a025
[   111.563] (II) intel(0):     125054a76b80950f950081808140714f
[   111.563] (II) intel(0):     0101010101017c2e90a0601a1e403020
[   111.563] (II) intel(0):     3600b20e1100001a21399030621a2740
[   111.563] (II) intel(0):     68b03600b20e1100001c000000fd0038
[   111.563] (II) intel(0):     4b1c530f000a202020202020000000fc
[   111.563] (II) intel(0):     004d32303857410a2020202020200005
[   111.563] (II) intel(0): EDID vendor "GSM", prod id 20065
[   111.563] (II) intel(0): Using EDID range info for horizontal sync
[   111.563] (II) intel(0): Using EDID range info for vertical refresh
[   111.563] (II) intel(0): Printing DDC gathered Modelines:
[   111.563] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   111.563] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   111.563] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   111.563] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   111.563] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   111.563] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   111.563] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   111.563] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   111.563] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   111.563] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   111.563] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   111.563] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   111.563] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   111.563] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   111.563] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   111.563] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   111.563] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   111.563] (II) intel(0): Printing probed modes for output VGA2
[   111.563] (II) intel(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   111.563] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   111.563] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   111.563] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   111.564] (II) intel(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   111.564] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   111.564] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   111.564] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   111.564] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[   111.564] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   111.564] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   111.564] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   111.564] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   111.564] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   111.564] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   111.564] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   111.564] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   111.564] (II) intel(0): Output VGA2 connected
[   111.564] (II) intel(0): Using exact sizes for initial modes
[   111.564] (II) intel(0): Output VGA2 using initial mode 1680x1050
[   111.564] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   111.564] (II) intel(0): Kernel page flipping support detected, enabling
[   111.564] (**) intel(0): Display dimensions: (430, 270) mm
[   111.564] (**) intel(0): DPI set to (99, 98)
[   111.564] (II) Loading sub module "fb"
[   111.564] (II) LoadModule: "fb"
[   111.564] (II) Loading /usr/lib/xorg/modules/libfb.so
[   111.564] (II) Module fb: vendor="X.Org Foundation"
[   111.564]     compiled for 1.11.3, module version = 1.0.0
[   111.564]     ABI class: X.Org ANSI C Emulation, version 0.4
[   111.564] (II) Loading sub module "dri2"
[   111.564] (II) LoadModule: "dri2"
[   111.564] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   111.564] (II) Module dri2: vendor="X.Org Foundation"
[   111.564]     compiled for 1.11.3, module version = 1.2.0
[   111.564]     ABI class: X.Org Server Extension, version 6.0
[   111.564] (II) UnloadModule: "vesa"
[   111.564] (II) Unloading vesa
[   111.564] (II) UnloadModule: "fbdev"
[   111.564] (II) Unloading fbdev
[   111.564] (II) UnloadModule: "fbdevhw"
[   111.564] (II) Unloading fbdevhw
[   111.564] (==) Depth 24 pixmap format is 32 bpp
[   111.565] (II) intel(0): [DRI2] Setup complete
[   111.565] (II) intel(0): [DRI2]   DRI driver: i965
[   111.565] (II) intel(0): Allocated new frame buffer 1728x1050 stride 7168, tiled
[   111.573] (II) UXA(0): Driver registered support for the following operations:
[   111.573] (II)         solid
[   111.573] (II)         copy
[   111.573] (II)         composite (RENDER acceleration)
[   111.573] (II)         put_image
[   111.573] (II)         get_image
[   111.573] (==) intel(0): Backing store disabled
[   111.573] (==) intel(0): Silken mouse enabled
[   111.573] (II) intel(0): Initializing HW Cursor
[   111.573] (EE) intel(0): Couldn't create pixmap for fbcon
[   111.620] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   111.620] (==) intel(0): DPMS enabled
[   111.620] (==) intel(0): Intel XvMC decoder enabled
[   111.620] (II) intel(0): Set up textured video
[   111.620] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   111.620] (II) intel(0): direct rendering: DRI2 Enabled
[   111.620] (==) intel(0): hotplug detection: "enabled"
[   111.621] (--) RandR disabled
[   111.621] (II) Initializing built-in extension Generic Event Extension
[   111.621] (II) Initializing built-in extension SHAPE
[   111.621] (II) Initializing built-in extension MIT-SHM
[   111.621] (II) Initializing built-in extension XInputExtension
[   111.621] (II) Initializing built-in extension XTEST
[   111.621] (II) Initializing built-in extension BIG-REQUESTS
[   111.621] (II) Initializing built-in extension SYNC
[   111.621] (II) Initializing built-in extension XKEYBOARD
[   111.621] (II) Initializing built-in extension XC-MISC
[   111.621] (II) Initializing built-in extension SECURITY
[   111.621] (II) Initializing built-in extension XINERAMA
[   111.621] (II) Initializing built-in extension XFIXES
[   111.621] (II) Initializing built-in extension RENDER
[   111.621] (II) Initializing built-in extension RANDR
[   111.621] (II) Initializing built-in extension COMPOSITE
[   111.621] (II) Initializing built-in extension DAMAGE
[   111.629] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   111.629] (II) AIGLX: enabled GLX_INTEL_swap_event
[   111.629] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   111.629] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   111.629] (II) AIGLX: Loaded and initialized i965
[   111.629] (II) GLX: Initialized DRI2 GL provider for screen 0
[   111.629] (II) intel(0): Setting screen physical size to 444 x 277
[   111.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   111.642] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   111.642] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   111.642] (II) LoadModule: "evdev"
[   111.642] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   111.642] (II) Module evdev: vendor="X.Org Foundation"
[   111.642]     compiled for 1.11.3, module version = 2.7.0
[   111.642]     Module class: X.Org XInput Driver
[   111.642]     ABI class: X.Org XInput driver, version 16.0
[   111.642] (II) Using input driver 'evdev' for 'Power Button'
[   111.642] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   111.642] (**) Power Button: always reports core events
[   111.642] (**) evdev: Power Button: Device: "/dev/input/event1"
[   111.642] (--) evdev: Power Button: Vendor 0 Product 0x1
[   111.642] (--) evdev: Power Button: Found keys
[   111.642] (II) evdev: Power Button: Configuring as keyboard
[   111.642] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   111.642] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   111.642] (**) Option "xkb_rules" "evdev"
[   111.642] (**) Option "xkb_model" "pc105"
[   111.642] (**) Option "xkb_layout" "es"
[   111.644] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFBD4FDC8093CCB415CD73029FDA64F4B077A3E7.xkm
[   111.645] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   111.645] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   111.645] (II) Using input driver 'evdev' for 'Power Button'
[   111.645] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   111.645] (**) Power Button: always reports core events
[   111.645] (**) evdev: Power Button: Device: "/dev/input/event0"
[   111.645] (--) evdev: Power Button: Vendor 0 Product 0x1
[   111.645] (--) evdev: Power Button: Found keys
[   111.645] (II) evdev: Power Button: Configuring as keyboard
[   111.645] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   111.645] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   111.645] (**) Option "xkb_rules" "evdev"
[   111.645] (**) Option "xkb_model" "pc105"
[   111.645] (**) Option "xkb_layout" "es"
[   111.645] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event3)
[   111.645] (II) No input driver specified, ignoring this device.
[   111.645] (II) This device may have been added with another device file.
[   111.646] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event4)
[   111.646] (II) No input driver specified, ignoring this device.
[   111.646] (II) This device may have been added with another device file.
[   111.646] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event5)
[   111.646] (II) No input driver specified, ignoring this device.
[   111.646] (II) This device may have been added with another device file.
[   111.646] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event6)
[   111.646] (II) No input driver specified, ignoring this device.
[   111.646] (II) This device may have been added with another device file.
[   111.646] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event7)
[   111.646] (II) No input driver specified, ignoring this device.
[   111.646] (II) This device may have been added with another device file.
[   111.646] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event8)
[   111.647] (II) No input driver specified, ignoring this device.
[   111.647] (II) This device may have been added with another device file.
[   111.647] (II) config/udev: Adding input device ov519 (/dev/input/event9)
[   111.647] (**) ov519: Applying InputClass "evdev keyboard catchall"
[   111.647] (II) Using input driver 'evdev' for 'ov519'
[   111.647] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   111.647] (**) ov519: always reports core events
[   111.647] (**) evdev: ov519: Device: "/dev/input/event9"
[   111.647] (--) evdev: ov519: Vendor 0x54c Product 0x154
[   111.647] (--) evdev: ov519: Found keys
[   111.647] (II) evdev: ov519: Configuring as keyboard
[   111.647] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2/input/input9/event9"
[   111.647] (II) XINPUT: Adding extended input device "ov519" (type: KEYBOARD, id 8)
[   111.647] (**) Option "xkb_rules" "evdev"
[   111.647] (**) Option "xkb_model" "pc105"
[   111.647] (**) Option "xkb_layout" "es"
[   111.647] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   111.647] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   111.647] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   111.647] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   111.647] (**) AT Translated Set 2 keyboard: always reports core events
[   111.647] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   111.648] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   111.648] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   111.648] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   111.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   111.648] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   111.648] (**) Option "xkb_rules" "evdev"
[   111.648] (**) Option "xkb_model" "pc105"
[   111.648] (**) Option "xkb_layout" "es"
[   111.648] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event10)
[   111.648] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[   111.648] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[   111.648] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   111.648] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[   111.648] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event10"
[   111.648] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[   111.648] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[   111.648] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[   111.648] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[   111.648] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[   111.648] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[   111.648] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[   111.648] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[   111.648] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   111.648] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[   111.648] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 10)
[   111.648] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[   111.649] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[   111.649] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[   111.649] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[   111.649] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[   111.649] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[   111.649] (II) No input driver specified, ignoring this device.
[   111.649] (II) This device may have been added with another device file.
[   112.211] (II) intel(0): EDID vendor "GSM", prod id 20065
[   112.211] (II) intel(0): Using hsync ranges from config file
[   112.211] (II) intel(0): Using vrefresh ranges from config file
[   112.211] (II) intel(0): Printing DDC gathered Modelines:
[   112.211] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   112.211] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   112.211] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   112.211] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   112.211] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   112.211] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   112.211] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   112.211] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   112.211] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   112.212] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   112.212] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   112.212] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   112.212] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   112.212] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   112.212] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   112.212] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   112.212] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   112.379] (II) intel(0): EDID vendor "GSM", prod id 20065
[   112.379] (II) intel(0): Using hsync ranges from config file
[   112.379] (II) intel(0): Using vrefresh ranges from config file
[   112.379] (II) intel(0): Printing DDC gathered Modelines:
[   112.379] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   112.379] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   112.379] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   112.379] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   112.379] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   112.379] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   112.379] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   112.379] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   112.379] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   112.379] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   112.379] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   112.379] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   112.379] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   112.379] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   112.379] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   112.379] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   112.379] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   124.263] (II) intel(0): EDID vendor "GSM", prod id 20065
[   124.263] (II) intel(0): Using hsync ranges from config file
[   124.263] (II) intel(0): Using vrefresh ranges from config file
[   124.263] (II) intel(0): Printing DDC gathered Modelines:
[   124.263] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   124.263] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   124.263] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   124.263] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   124.263] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   124.263] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   124.263] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   124.263] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   124.263] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   124.263] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   124.263] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   124.263] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   124.263] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   124.263] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   124.263] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   124.263] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   124.263] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   124.427] (II) intel(0): EDID vendor "GSM", prod id 20065
[   124.427] (II) intel(0): Using hsync ranges from config file
[   124.427] (II) intel(0): Using vrefresh ranges from config file
[   124.427] (II) intel(0): Printing DDC gathered Modelines:
[   124.427] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   124.427] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   124.427] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   124.427] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   124.427] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   124.427] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   124.427] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   124.427] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   124.427] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   124.427] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   124.427] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   124.427] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   124.427] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   124.427] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   124.427] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   124.427] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   124.427] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   124.527] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.067] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.076] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.079] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.085] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.089] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.093] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.097] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.101] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.105] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.108] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.112] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.115] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.119] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.123] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.127] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.130] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   126.138] (II) XKB: reuse xkmfile /var/lib/xkb/server-8925C31C35A2851FB56E469C3641E1CDAC1128A2.xkm
[   145.015] (II) intel(0): EDID vendor "GSM", prod id 20065
[   145.015] (II) intel(0): Using hsync ranges from config file
[   145.015] (II) intel(0): Using vrefresh ranges from config file
[   145.015] (II) intel(0): Printing DDC gathered Modelines:
[   145.015] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   145.015] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   145.015] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   145.015] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   145.015] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   145.015] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   145.015] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   145.015] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   145.015] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   145.015] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   145.015] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   145.015] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   145.015] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   145.015] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   145.015] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   145.015] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   145.015] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   422.475] (II) intel(0): EDID vendor "GSM", prod id 20065
[   422.475] (II) intel(0): Using hsync ranges from config file
[   422.475] (II) intel(0): Using vrefresh ranges from config file
[   422.475] (II) intel(0): Printing DDC gathered Modelines:
[   422.475] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   422.475] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   422.475] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   422.475] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   422.475] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   422.475] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   422.475] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   422.475] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   422.475] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   422.475] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   422.475] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   422.475] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   422.475] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   422.475] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   422.475] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   422.475] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   422.475] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   425.531] (II) intel(0): EDID vendor "GSM", prod id 20065
[   425.531] (II) intel(0): Using hsync ranges from config file
[   425.531] (II) intel(0): Using vrefresh ranges from config file
[   425.531] (II) intel(0): Printing DDC gathered Modelines:
[   425.531] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   425.531] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   425.531] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   425.531] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   425.531] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   425.531] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   425.531] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   425.531] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   425.531] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   425.531] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   425.531] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   425.531] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   425.531] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   425.531] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   425.531] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   425.531] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   425.531] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   505.247] (II) intel(0): EDID vendor "GSM", prod id 20065
[   505.247] (II) intel(0): Using hsync ranges from config file
[   505.247] (II) intel(0): Using vrefresh ranges from config file
[   505.247] (II) intel(0): Printing DDC gathered Modelines:
[   505.247] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   505.247] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   505.247] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   505.247] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   505.247] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   505.247] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   505.247] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   505.247] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   505.247] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   505.247] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   505.247] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   505.247] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   505.247] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   505.247] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   505.247] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   505.247] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   505.247] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   510.471] (II) intel(0): EDID vendor "GSM", prod id 20065
[   510.471] (II) intel(0): Using hsync ranges from config file
[   510.471] (II) intel(0): Using vrefresh ranges from config file
[   510.471] (II) intel(0): Printing DDC gathered Modelines:
[   510.471] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   510.471] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   510.471] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   510.471] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   510.471] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   510.471] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   510.471] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   510.471] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   510.471] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   510.471] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   510.471] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   510.471] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   510.471] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   510.471] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   510.471] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   510.471] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   510.471] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   511.055] (II) intel(0): EDID vendor "GSM", prod id 20065
[   511.055] (II) intel(0): Using hsync ranges from config file
[   511.055] (II) intel(0): Using vrefresh ranges from config file
[   511.055] (II) intel(0): Printing DDC gathered Modelines:
[   511.055] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   511.055] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   511.055] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   511.055] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   511.055] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   511.055] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   511.055] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   511.055] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   511.055] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   511.055] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   511.055] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   511.055] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   511.055] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   511.055] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   511.055] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   511.055] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   511.055] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   511.243] (II) intel(0): EDID vendor "GSM", prod id 20065
[   511.243] (II) intel(0): Using hsync ranges from config file
[   511.243] (II) intel(0): Using vrefresh ranges from config file
[   511.243] (II) intel(0): Printing DDC gathered Modelines:
[   511.243] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   511.243] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   511.243] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   511.243] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   511.243] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   511.243] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   511.243] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   511.243] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   511.243] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   511.243] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   511.243] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   511.243] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   511.243] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   511.243] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   511.243] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   511.243] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   511.243] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   511.407] (II) intel(0): EDID vendor "GSM", prod id 20065
[   511.407] (II) intel(0): Using hsync ranges from config file
[   511.407] (II) intel(0): Using vrefresh ranges from config file
[   511.407] (II) intel(0): Printing DDC gathered Modelines:
[   511.407] (II) intel(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   511.407] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   511.407] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   511.407] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   511.407] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   511.407] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   511.407] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   511.407] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   511.407] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   511.407] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   511.407] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   511.407] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   511.407] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   511.407] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   511.407] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   511.407] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   511.407] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   534.079] (II) intel(0): Allocated new frame buffer 1472x900 stride 6144, tiled
[   541.432] (II) intel(0): Allocated new frame buffer 1728x1050 stride 7168, tiled
```

---

### Post by axFelix on 2012-09-24
Bumping this topic because I'm having the exact same behaviour the OP describes and I've been tearing my hair out trying to solve it.

---

### Post by sirfocus on 2012-09-24
Hi axFelix,

I finally solved it this way: [http://www.cyberciti.biz/tips/create-a-xorgconf-file.html](http://www.cyberciti.biz/tips/create-a-xorgconf-file.html)
Basically you have to stop xorg, generate a new configuration file and it should work. In my case the new configuration file gave me an error (number of screens don't match...something), but it's working and I can configure the double screen without any problem :)

Sorry, forgot to post the soluction, so good that I was suscribed :P

---

### Post by axFelix on 2012-09-24
I'm glad you were subscribed -- and I can't believe the solution, after hours of me trying to fix X.conf, is just to let it configure itself! Geez do I wish these things were documented ...

... of course, it's not working right for me. One guess: the auto-generated X.conf wanted to use the open "radeon" driver for my Radeon, instead of the Catalyst "fglrx" driver. Unfortunately, my Radeon (7850) is too new to be supported by the open driver, so I needed to change it back ... and this got X to crash again. Sigh ...

---

### Post by sirfocus on 2012-09-24
I think it'll be difficult to fix if your card is not supported. I discovered that, as, appart from the radeon, I also had the Intel chip, when I installed the specific driver, this last one stopped working and I could only see the radeon screen. So, if you have two different cards and you cannot use both with the open driver...I really have no idea of what you can do... ¿you have excatly the same configuration as me? I mean ATI + Intel...?

---

### Post by axFelix on 2012-09-24
I've got a Radeon 7850 and Intel HD 3000 (i5-2500k), having exactly the same symptoms you described (iGPU display only displaying the boot logo and then being invisible to X).

it shouldn't be more than a few months before the open Radeon driver supports my card, but I'm not sure why I bought such a fancy new card if not to use the better 3D acceleration in fglrx... what I really need to do is convince myself to stop wrestling with it -- I'm just surprised that this configuration (two mid-end mainstream products both released within 6 and 18 months ago) is unsupported.

---

