---
title: "Updated my Ubuntu 11.04 to Version 12.04, wireless off and on"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by SUPERFITTER on 2012-08-07
I updated my Ubuntu 11.04 to Version 12.04 on my laptop.  Now my wireless cuts out on a regular basis.   After a few key taps or if I'm lucky I can get something to download if I start it after signing into my wireless network.  I see a few have had success by disabling  IPV6.   I have gone to Network Connections > Wireless > (My user name) > edit > IPV6 Settings > and changed (Automatic to Ignore).  I cannot find a key to enable or keep this setting.   
 What am I doing wrong?   
 Is there a better way to enable and keep my wireless going?   
 Thank You in advance!

---

### Post by SUPERFITTER on 2012-08-09
found the Specifications for this machine: 

eMachineM6809 Notebook[COLOR=#ffffff]eMachines® M6809 Notebook[/COLOR]
 
Processor Mobile AMD Athlon&#8482; 64 3200+ Processor
64-bit Architecture operates at 2.00 GHz System Bus uses HyperTransport&#8482; Technology operating at 1600 MHz Level 2 cache
1 MB
BIOS
Manufacturer Phoenix Technologies
CMOS battery CR2032 Lithium 
Notebook battery [8-cell Lithium-ion]("file:///emachines/Mobile/eMachines/Shared/M6410su5.shtml") (Li4402A Li-Ion) Memory [512 MB DDR PC2700 SO-DIMM]("file:///emachines/Mobile/eMachines/Shared/M6410su13.shtml") 
External power source [120 Watt power supply]("file:///emachines/Mobile/eMachines/Shared/M6410su4.shtml") (PA-1121-0 
Video ATI® Mobility RADEON&#8482; 9600 
64 MB DDR shared video memory Audio
PC2001 Compliant AC '97 Audio 
Built-in Stereo Speakers 
Hard drive [80 GB]("file:///emachines/Mobile/eMachines/Shared/M6410su12.shtml")
Primary optical drive
[DVD +/- RW Drive]("file:///emachines/Mobile/eMachines/Shared/M6410su7.shtml") Lite-On IT Corp. SDW-431S (Write maximum: 2.4X DVD+R/RW, 2X DVD-R/RW, 6X CD-R, 10X CD-RW; Reads 24X CD, 8X DVD) 
Modem 56K ITU V.92 Fax/Modem 
Network interface
10/100Mbps built-in Ethernet Wireless
802.11g built-in wireless (up to 54Mbps)

---

### Post by SUPERFITTER on 2012-08-15
Anyone have the same problem or a solution?

```
[    0.330390] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.330446] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.330580] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0002800
[    0.340030] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.340240] hub 1-0:1.0: USB hub found
[    0.340246] hub 1-0:1.0: 6 ports detected
[    0.340349] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.340370] uhci_hcd: USB Universal Host Controller Interface driver
[    0.340411] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.340424] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.340477] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.340503] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001c80
[    0.340659] hub 2-0:1.0: USB hub found
[    0.340664] hub 2-0:1.0: 2 ports detected
[    0.340726] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.340733] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.340776] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.340795] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001ca0
[    0.340943] hub 3-0:1.0: USB hub found
[    0.340947] hub 3-0:1.0: 2 ports detected
[    0.341008] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKD] -> GSI 21 (level, low) -> IRQ 21
[    0.341015] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.341054] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.341073] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001cc0
[    0.341212] hub 4-0:1.0: USB hub found
[    0.341216] hub 4-0:1.0: 2 ports detected
[    0.341329] usbcore: registered new interface driver libusual
[    0.341378] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.346315] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.346323] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.346946] mousedev: PS/2 mouse device common for all mice
[    0.348139] rtc_cmos 00:02: RTC can wake from S4
[    0.348270] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.348316] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.348403] device-mapper: uevent: version 1.0.3
[    0.348487] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.348527] EISA: Probing bus 0 at eisa.0
[    0.348531] EISA: Cannot allocate resource for mainboard
[    0.348533] Cannot allocate resource for EISA slot 1
[    0.348536] Cannot allocate resource for EISA slot 2
[    0.348538] Cannot allocate resource for EISA slot 3
[    0.348541] Cannot allocate resource for EISA slot 4
[    0.348543] Cannot allocate resource for EISA slot 5
[    0.348546] Cannot allocate resource for EISA slot 6
[    0.348548] Cannot allocate resource for EISA slot 7
[    0.348550] Cannot allocate resource for EISA slot 8
[    0.348553] EISA: Detected 0 cards.
[    0.348565] cpufreq-nforce2: No nForce2 chipset.
[    0.348601] cpuidle: using governor ladder
[    0.348655] cpuidle: using governor menu
[    0.348657] EFI Variables Facility v0.08 2004-May-17
[    0.348917] TCP cubic registered
[    0.349069] NET: Registered protocol family 10
[    0.349750] NET: Registered protocol family 17
[    0.350588] Registering the dns_resolver key type
[    0.350613] Using IPI No-Shortcut mode
[    0.351489] PM: Hibernation image not present or could not be loaded.
[    0.351507] registered taskstats version 1
[    0.373503] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.561810] ACPI: Battery Slot [BAT0] (battery present)
[    0.847743] isapnp: No Plug & Play device found
[    0.900227] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    0.952836] Freeing initrd memory: 13808k freed
[    0.977142]   Magic number: 8:387:656
[    0.977284] rtc_cmos 00:02: setting system clock to 2012-08-18 23:38:37 UTC (1345333117)
[    0.977289] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    0.977331] powernow-k8: fid 0xc (2000 MHz), vid 0x6
[    0.977334] powernow-k8: fid 0x8 (1600 MHz), vid 0xe
[    0.977336] powernow-k8: fid 0x0 (800 MHz), vid 0x18
[    0.978034] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.978039] EDD information not available.
[    0.978315] Freeing unused kernel memory: 712k freed
[    0.979151] Write protecting the kernel text: 5616k
[    0.979248] Write protecting the kernel read-only data: 2324k
[    1.024829] udevd[80]: starting version 175
[    1.323454] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.323516] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.323528] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.323539] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.323549] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.323559] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.375171] usbcore: registered new interface driver usbhid
[    1.375180] usbhid: USB HID core driver
[    1.405026] via_rhine: v1.10-LK1.5.0 2010-10-09 Written by Donald Becker
[    1.411698] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[    1.411744] pata_via 0000:00:11.1: version 0.3.4
[    1.411771] pata_via 0000:00:11.1: power state changed by ACPI to D0
[    1.411781] pata_via 0000:00:11.1: power state changed by ACPI to D0
[    1.411801] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 23 (level, low) -> IRQ 23
[    1.415647] scsi0 : pata_via
[    1.419438] scsi1 : pata_via
[    1.420845] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1ce0 irq 14
[    1.420854] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1ce8 irq 15
[    1.421341] via-rhine 0000:00:12.0: power state changed by ACPI to D0
[    1.421354] via-rhine 0000:00:12.0: power state changed by ACPI to D0
[    1.421434] ACPI: PCI Interrupt Link [ALKB] disabled and referenced, BIOS bug
[    1.421503] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 23
[    1.421509] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[    1.421522] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKB] -> GSI 23 (level, low) -> IRQ 23
[    1.433116] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xd0002c00, 00:03:25:10:cf:7a, IRQ 23
[    1.433833] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1
[    1.440279] firewire_ohci 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.504126] firewire_ohci: Added fw-ohci device 0000:00:13.0, OHCI v1.0, 4 IR + 8 IT contexts, quirks 0x11
[    1.560135] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input5
[    1.560535] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.1-2/input0
[    1.584648] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[    1.584658] ata1.00: 156301488 sectors, multi 16: LBA48 
[    1.590655] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    1.596152] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input6
[    1.597874] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.1-2/input1
[    1.600517] ata1.00: configured for UDMA/100
[    1.600809] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[    1.601255] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.601373] sd 0:0:0:0: [sda] Write Protect is off
[    1.601382] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.601435] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.602067] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.659205]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.660194] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.764392] ata2.00: ATAPI: Slimtype DVDRW SDW-431S, MBS2, max UDMA/33
[    1.780254] ata2.00: configured for UDMA/33
[    1.781305] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SDW-431S   MBS2 PQ: 0 ANSI: 5
[    1.783109] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.783117] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.783887] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.784294] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.004327] firewire_core: created device fw0: GUID 00032521290089f8, S400
[    2.599179] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   24.612209] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.683973] udevd[305]: starting version 175
[   24.712495] Adding 519164k swap on /dev/sda7.  Priority:-1 extents:1 across:519164k 
[   25.042710] lp: driver loaded but no devices found
[   25.043171] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   25.201952] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.284058] yenta_cardbus 0000:00:0a.0: CardBus bridge found [161f:2032]
[   25.284088] yenta_cardbus 0000:00:0a.0: Using CSCINT to route CSC interrupts to PCI
[   25.284096] yenta_cardbus 0000:00:0a.0: Routing CardBus interrupts to PCI
[   25.284107] yenta_cardbus 0000:00:0a.0: TI: mfunc 0x01001002, devctl 0x44
[   25.523922] yenta_cardbus 0000:00:0a.0: ISA IRQ mask 0x00f0, PCI irq 17
[   25.523934] yenta_cardbus 0000:00:0a.0: Socket status: 30000006
[   25.575727] cfg80211: Calling CRDA to update world regulatory domain
[   26.083073] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:11/LNXVIDEO:00/input/input7
[   26.083515] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.410086] [drm] Initialized drm 1.1.0 20060810
[   26.530036] type=1400 audit(1345347543.047:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=542 comm="apparmor_parser"
[   26.531308] type=1400 audit(1345347543.047:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=542 comm="apparmor_parser"
[   26.532082] type=1400 audit(1345347543.051:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=542 comm="apparmor_parser"
[   26.533368] type=1400 audit(1345347543.051:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=586 comm="apparmor_parser"
[   26.534630] type=1400 audit(1345347543.051:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=586 comm="apparmor_parser"
[   26.535368] type=1400 audit(1345347543.051:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=586 comm="apparmor_parser"
[   26.790696] irda_init()
[   26.790735] NET: Registered protocol family 23
[   26.885064] psmouse serio1: synaptics: Touchpad model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008/0x0
[   26.921856] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   27.225530] init: failsafe main process (599) killed by TERM signal
[   27.261809] ppdev: user-space parallel port driver
[   27.300226] Bluetooth: Core ver 2.16
[   27.301962] NET: Registered protocol family 31
[   27.301970] Bluetooth: HCI device and connection manager initialized
[   27.301978] Bluetooth: HCI socket layer initialized
[   27.301984] Bluetooth: L2CAP socket layer initialized
[   27.302000] Bluetooth: SCO socket layer initialized
[   27.371085] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   27.420381] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.420390] Bluetooth: BNEP filters: protocol multicast
[   27.432279] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   27.432291] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432300] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   27.432309] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432316] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   27.432324] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432331] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   27.432340] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432347] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   27.432355] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432362] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   27.432371] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432378] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   27.432386] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432393] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   27.432402] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432409] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   27.432417] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432424] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   27.432433] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432439] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   27.432448] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   27.432455] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   27.432464] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   27.432471] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   27.432479] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   27.432486] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   27.432495] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   27.544399] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   27.548259] Registered led device: b43-phy0::tx
[   27.548400] Registered led device: b43-phy0::rx
[   27.548525] Registered led device: b43-phy0::radio
[   27.548653] Broadcom 43xx driver loaded [ Features: PNL ]
[   27.917445] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x300-0x307 0x370-0x377
[   27.944648] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   27.945574] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   27.946334] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   27.947182] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   27.947246] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   27.947309] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   27.947372] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   28.074467] type=1400 audit(1345347544.591:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=737 comm="apparmor_parser"
[   28.075962] type=1400 audit(1345347544.591:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=737 comm="apparmor_parser"
[   28.235675] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.235690] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235698] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.235708] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235715] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.235724] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235731] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.235739] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235746] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.235755] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235762] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.235770] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235777] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.235786] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235793] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.235801] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235808] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.235817] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235823] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.235832] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235839] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.235847] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235854] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   28.235863] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.235870] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   28.235878] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.235885] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   28.235894] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.235903] cfg80211: World regulatory domain updated:
[   28.235908] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.235916] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235924] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.235932] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.235939] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.235947] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.264144]  clean.
[   28.303513] type=1400 audit(1345347544.819:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=771 comm="apparmor_parser"
[   28.463670] [drm] radeon defaulting to kernel modesetting.
[   28.463682] [drm] radeon kernel modesetting enabled.
[   28.463869] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.465964] type=1400 audit(1345347544.983:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=779 comm="apparmor_parser"
[   28.488285] [drm] initializing kernel modesetting (RV350 0x1002:0x4E50 0x161F:0x2032).
[   28.488336] [drm] register mmio base: 0xD0100000
[   28.488342] [drm] register mmio size: 65536
[   28.488646] agpgart-amd64 0000:00:00.0: AGP 3.5 bridge
[   28.488673] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   28.488766] radeon 0000:01:00.0: putting AGP V3 device into 8x mode
[   28.488777] radeon 0000:01:00.0: GTT: 256M 0xE0000000 - 0xEFFFFFFF
[   28.488785] [drm] Generation 2 PCI interface, using max accessible memory
[   28.488796] radeon 0000:01:00.0: VRAM: 128M 0x00000000D8000000 - 0x00000000DFFFFFFF (64M used)
[   28.488823] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   28.488828] [drm] Driver supports precise vblank timestamp query.
[   28.488880] [drm] radeon: irq initialized.
[   28.491665] [drm] Detected VRAM RAM=128M, BAR=128M
[   28.491674] [drm] RAM width 128bits DDR
[   28.581055] [TTM] Zone  kernel: Available graphics memory: 441666 kiB.
[   28.581065] [TTM] Zone highmem: Available graphics memory: 641830 kiB.
[   28.581071] [TTM] Initializing pool allocator.
[   28.581127] [drm] radeon: 64M of VRAM memory ready
[   28.581133] [drm] radeon: 256M of GTT memory ready.
[   28.581208] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   28.583590] radeon 0000:01:00.0: WB disabled
[   28.617553] [drm] Loading R300 Microcode
[   28.781035] [drm] radeon: ring at 0x00000000E0001000
[   28.781064] [drm] ring test succeeded in 1 usecs
[   28.781613] [drm] radeon: ib pool ready.
[   28.781744] [drm] ib test succeeded in 0 usecs
[   28.789931] [drm] Panel ID String: SEC                     
[   28.789940] [drm] Panel Size 1280x800
[   28.801429] [drm] radeon legacy LVDS backlight initialized
[   28.801868] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   28.808311] [drm] No TV DAC info found in BIOS
[   28.808978] [drm] Radeon Display Connectors
[   28.808985] [drm] Connector 0:
[   28.808989] [drm]   VGA
[   28.808996] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   28.809001] [drm]   Encoders:
[   28.809006] [drm]     CRT1: INTERNAL_DAC1
[   28.809010] [drm] Connector 1:
[   28.809014] [drm]   LVDS
[   28.809017] [drm]   Encoders:
[   28.809021] [drm]     LCD1: INTERNAL_LVDS
[   28.809026] [drm] Connector 2:
[   28.809029] [drm]   S-video
[   28.809033] [drm]   Encoders:
[   28.809037] [drm]     TV1: INTERNAL_DAC2
[   28.809162] [drm] radeon: power management initialized
[   28.924284] [drm] fb mappable at 0xD8040000
[   28.924293] [drm] vram apper at 0xD8000000
[   28.924298] [drm] size 4096000
[   28.924302] [drm] fb depth is 24
[   28.924307] [drm]    pitch is 5120
[   28.924784] fbcon: radeondrmfb (fb0) is primary device
[   28.927116] Console: switching to colour frame buffer device 160x50
[   28.927209] fb0: radeondrmfb frame buffer device
[   28.927214] drm: registered panic notifier
[   28.927233] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0
[   29.184706] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.186856] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.271788] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   30.086390] snd_via82xx_modem 0000:00:11.6: power state changed by ACPI to D0
[   30.086405] snd_via82xx_modem 0000:00:11.6: power state changed by ACPI to D0
[   30.086489] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[   30.086566] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   30.086573] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   30.086603] snd_via82xx_modem 0000:00:11.6: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   30.088605] snd_via82xx_modem 0000:00:11.6: setting latency timer to 64
[   30.598397] snd_via82xx 0000:00:11.5: power state changed by ACPI to D0
[   30.598411] snd_via82xx 0000:00:11.5: power state changed by ACPI to D0
[   30.598433] snd_via82xx 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   30.598585] snd_via82xx 0000:00:11.5: setting latency timer to 64
[   31.581064] init: gdm main process (947) killed by TERM signal
[   32.549596] init: plymouth-upstart-bridge main process (650) killed by TERM signal
[   32.842300] init: anacron main process (939) killed by TERM signal
[   33.535404] init: plymouth-stop pre-start process (1251) terminated with status 1
[   46.608026] eth0: no IPv6 routers present
dennis@dennis:~$ sudo lshw -C network
[sudo] password for dennis: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:cf:7a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=10.10.10.103 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:1800(size=256) memory:d0002c00-d0002cff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:a6:39:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-29-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg
dennis@dennis:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

dennis@dennis:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
dennis@dennis:~$ lsb_release -d
Description:    Ubuntu 12.04 LTS
dennis@dennis:~$ uname -mr
3.2.0-29-generic i686
dennis@dennis:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
dennis@dennis:~$
```

---

### Post by SUPERFITTER on 2012-08-19
```
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grep is already the newest version.
rfkill is already the newest version.
The following packages were automatically installed and are no longer required:
  libunity6 unity-2d-launcher linux-headers-3.2.0-27
  linux-headers-3.2.0-27-generic icc-profiles-free libid3tag0
  linux-headers-3.2.0-27-generic-pae libnatpmp1 unity-2d-places libllvm2.9
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  hwinfo libhal1 libhd16
0 upgraded, 3 newly installed, 0 to remove and 89 not upgraded.
Need to get 776 kB of archives.
After this operation, 2,235 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libhal1 i386 0.5.14-8 [76.8 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe libhd16 i386 16.0-2.1 [681 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe hwinfo i386 16.0-2.1 [18.2 kB]
Fetched 776 kB in 1s (724 kB/s)
Selecting previously unselected package libhal1.
(Reading database ... 226405 files and directories currently installed.)
Unpacking libhal1 (from .../libhal1_0.5.14-8_i386.deb) ...
Selecting previously unselected package libhd16.
Unpacking libhd16 (from .../libhd16_16.0-2.1_i386.deb) ...
Selecting previously unselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_16.0-2.1_i386.deb) ...
Processing triggers for man-db ...
Setting up libhal1 (0.5.14-8) ...
Setting up libhd16 (16.0-2.1) ...
Setting up hwinfo (16.0-2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0000000-d0001fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:10:cf:7a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=10.10.10.103 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:1800(size=256) memory:d0002c00-d0002cff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:96:a6:39:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-29-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:15:B1:AC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Bonkowski-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003858598ecd7
                    Extra: Last beacon: 852ms ago
                    IE: Unknown: 000B426F6E6B6F77736B692D4E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A88000236915B1AC1021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033031311054000800060050F2040001101100114C696E6B737973205752543136304E763210080002008C103C000101
          Cell 02 - Address: 00:16:B6:B6:53:35
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"SUPERFITTER1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000211ce4f6183
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 000C535550455246495454455231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000

eth0      Interface doesn't support scanning.

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/8251 PCI bridge [K8M890/K8T800/K8T890 South] [1106:b188]
00:0a.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410]
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
00:10.0 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
00:13.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV350 [Mobility Radeon 9600 M10] [1002:4e50]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
H/W path           Device      Class          Description
=========================================================
                               system         Computer
/0                             bus            Shadow-K8
/0/0                           memory         97KiB BIOS
/0/4                           processor      Mobile AMD Athlon(tm) 64 Processor
/0/4/7                         memory         128KiB L1 cache
/0/4/8                         memory         1MiB L2 cache
/0/a                           memory         1280MiB System Memory
/0/a/0                         memory         1GiB DIMM DRAM Synchronous
/0/a/1                         memory         256MiB DIMM DRAM Synchronous
/0/100                         bridge         VT8385 [K8T800 AGP] Host Bridge
/0/100/1                       bridge         VT8237/8251 PCI bridge [K8M890/K8T
/0/100/1/0                     display        RV350 [Mobility Radeon 9600 M10]
/0/100/a                       bridge         CB1410 Cardbus Controller
/0/100/c                       network        BCM4306 802.11b/g Wireless LAN Con
/0/100/10                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                    bus            USB 2.0
/0/100/11                      bridge         VT8235 ISA Bridge
/0/100/11.1        scsi0       storage        VT82C586A/B/VT82C686/A/B/VT823x/A/
/0/100/11.1/0      /dev/sda    disk           80GB IC25N080ATMR04-0
/0/100/11.1/0/1    /dev/sda1   volume         49GiB Windows NTFS volume
/0/100/11.1/0/2    /dev/sda2   volume         25GiB Extended partition
/0/100/11.1/0/2/5  /dev/sda5   volume         509MiB Linux swap / Solaris partit
/0/100/11.1/0/2/6  /dev/sda6   volume         24GiB Linux filesystem partition
/0/100/11.1/0/2/7  /dev/sda7   volume         507MiB Linux swap / Solaris partit
/0/100/11.1/1      /dev/cdrom  disk           DVDRW SDW-431S
/0/100/11.5                    multimedia     VT8233/A/8235/8237 AC97 Audio Cont
/0/100/11.6                    communication  AC'97 Modem Controller
/0/100/12          eth0        network        VT6102 [Rhine-II]
/0/100/13                      bus            VT6306/7/8 [Fire II(M)] IEEE 1394 
/0/101                         bridge         K8 [Athlon64/Opteron] HyperTranspo
/0/102                         bridge         K8 [Athlon64/Opteron] Address Map
/0/103                         bridge         K8 [Athlon64/Opteron] DRAM Control
/0/104                         bridge         K8 [Athlon64/Opteron] Miscellaneou
/1                 wlan0       network        Wireless interface
Linux dennis 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 athlon i386 GNU/Linux
[    0.000000] found SMP MP-table at [c00f82d0] f82d0
[    0.008655] SMP alternatives: switching to UP code
[    0.081377] ACPI: No dock devices found.
[    0.081380] HEST: Table not found.
[    0.090292] i2c-core: driver [aat2870] using legacy suspend method
[    0.090295] i2c-core: driver [aat2870] using legacy resume method
[    0.090514] usbcore: registered new interface driver usbfs
[    0.090528] usbcore: registered new interface driver hub
[    0.090557] usbcore: registered new device driver usb
[    0.104138] pnp: PnP ACPI: found 9 devices
[    0.140894] Switching to clocksource acpi_pm
[    0.249063] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.249556] ACPI: Lid Switch [LID]
[    0.251236] ERST: Table is not found!
[    0.340240] hub 1-0:1.0: USB hub found
[    0.340659] hub 2-0:1.0: USB hub found
[    0.340943] hub 3-0:1.0: USB hub found
[    0.341212] hub 4-0:1.0: USB hub found
[    0.341329] usbcore: registered new interface driver libusual
[    0.847743] isapnp: No Plug & Play device found
[    0.900227] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    0.977289] powernow-k8: Found 1 Mobile AMD Athlon(tm) 64 Processor 3200+ (1 cpu cores) (version 2.20.00)
[    0.978034] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.323454] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.323516] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.323528] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.323539] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.323549] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.323559] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.375171] usbcore: registered new interface driver usbhid
[    1.375180] usbhid: USB HID core driver
[    1.411698] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[    1.433116] via-rhine 0000:00:12.0: eth0: VIA Rhine II at 0xd0002c00, 00:03:25:10:cf:7a, IRQ 23
[    1.433833] via-rhine 0000:00:12.0: eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1
[    1.560135] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.0/input/input5
[    1.560535] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:10.1-2/input0
[    1.596152] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:10.1/usb3/3-2/3-2:1.1/input/input6
[    1.597874] logitech 0003:046D:C517.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:10.1-2/input1
[   24.612209] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.042710] lp: driver loaded but no devices found
[   25.284058] yenta_cardbus 0000:00:0a.0: CardBus bridge found [161f:2032]
[   27.371085] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   27.548259] Registered led device: b43-phy0::tx
[   27.548400] Registered led device: b43-phy0::rx
[   27.548525] Registered led device: b43-phy0::radio
[   28.801868] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   28.808311] [drm] No TV DAC info found in BIOS
[   28.927116] Console: switching to colour frame buffer device 160x50
[   29.184706] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.186856] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.271788] via-rhine 0000:00:12.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   46.608026] eth0: no IPv6 routers present
    Release Date: 08/11/2004
    Manufacturer: eMachine
    Product Name: Shadow-K8
    Serial Number: N304 5600 00082
    Manufacturer: eMachine
    Product Name: Shadow-K8
    Serial Number: None
    Manufacturer: eMachine
    Serial Number: None
    Manufacturer: AuthenticAMD
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
> hal.1: read hal dataprocess 3832: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
11: PCI 0c.0: 0282 WLAN controller                              
  [Created at pci.318]
  Unique ID: y9sn.XtkqyMya3Y4
  SysFS ID: /devices/pci0000:00/0000:00:0c.0
  SysFS BusID: 0000:00:0c.0
  Hardware Class: network
  Model: "Askey eMachines M6805 802.11g Built-in Wireless"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4320 "BCM4306 802.11b/g Wireless LAN Controller"
  SubVendor: pci 0x144f "Askey Computer Corp."
  SubDevice: pci 0x7050 "eMachines M6805 802.11g Built-in Wireless"
  Revision: 0x03
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xd0000000-0xd0001fff (rw,non-prefetchable)
  IRQ: 18 (1196 events)
  HW Address: 00:90:96:a6:39:5f
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004320sv0000144Fsd00007050bc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 12.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.OR+pqLEx8F6
  SysFS ID: /devices/pci0000:00/0000:00:12.0
  SysFS BusID: 0000:00:12.0
  Hardware Class: network
  Model: "VIA VT6102 [Rhine II] Embeded Ethernet Controller on VT8235"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3065 "VT6102 [Rhine-II]"
  SubVendor: pci 0x1106 "VIA Technologies, Inc."
  SubDevice: pci 0x0102 "VT6102 [Rhine II] Embeded Ethernet Controller on VT8235"
  Revision: 0x74
  Driver: "via-rhine"
  Driver Modules: "via_rhine"
  Device File: eth0
  I/O Ports: 0x1800-0x18ff (rw)
  Memory Range: 0xd0002c00-0xd0002cff (rw,non-prefetchable)
  IRQ: 23 (11491 events)
  HW Address: 00:03:25:10:cf:7a
  Link detected: yes
  Module Alias: "pci:v00001106d00003065sv00001106sd00000102bc02sc00i00"
  Driver Info #0:
    Driver Status: via-rhine is active
    Driver Activation Cmd: "modprobe via-rhine"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root       727  0.0  0.3  31164  5092 ?        Ssl  Aug18   0:00 NetworkManager
root       839  0.0  0.1   5940  1812 ?        Ss   Aug18   0:00 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
root      1395  0.0  0.0   2908  1232 ?        S    Aug18   0:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-39074bbf-07f0-4d11-bdcc-4b0bb7e90da8-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
nobody    1405  0.0  0.0   5384  1136 ?        S    Aug18   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec
dennis    3846  0.0  0.0   4368   792 pts/0    S+   00:08   0:00 egrep --color=auto wpa|icd|etwork
Module                  Size  Used by
snd_via82xx            24719  2 
gameport               15060  1 snd_via82xx
snd_via82xx_modem      18377  5 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
radeon                733687  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
arc4                   12473  2 
parport_pc             32114  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
b43                   342643  0 
joydev                 17393  0 
bluetooth             158438  7 bnep
ppdev                  12849  0 
i2c_viapro             12969  0 
via_ircc               26781  0 
ttm                    65344  1 radeon
irda                  185517  1 via_ircc
binfmt_misc            17292  1 
drm_kms_helper         45466  1 radeon
snd                    62064  21 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197692  5 radeon,ttm,drm_kms_helper
psmouse                87213  0 
k8temp                 12905  0 
mac80211              436455  1 b43
video                  19068  0 
crc_ccitt              12595  1 irda
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              14635  1 snd
serio_raw              13027  0 
i2c_algo_bit           13199  1 radeon
pcmcia                 39791  0 
cfg80211              178679  2 b43,mac80211
bcma                   25651  1 b43
yenta_socket           27428  0 
mac_hid                13077  0 
pcmcia_rsrc            18367  1 yenta_socket
shpchp                 32325  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_logitech           22024  0 
ff_memless             12945  1 hid_logitech
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
via_rhine              27413  0 
usbhid                 41906  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
crc_itu_t              12627  1 firewire_core
pata_via               13428  2 
ssb                    50691  1 b43
dennis@dennis:~$
```

---

### Post by JohnXPS on 2012-08-19
I am having a similar problem with my Dell XPS 17 laptop. Wireless works OK most of the time but an intensive use of it (for example letting Update Manager update) fails. If I hardwire, the update will work as always. This was never a problem until I upgraded to 12.04.

---

### Post by SUPERFITTER on 2012-08-19
> **JohnXPS said:**
> I am having a similar problem with my Dell XPS 17 laptop. Wireless works OK most of the time but an intensive use of it (for example letting Update Manager update) fails. If I hardwire, the update will work as always. This was never a problem until I upgraded to 12.04.
 
I wish I knew more about this problem so I could fix it. This was a short term problem for me until I upgraded to 12.04, now I cannot stay connected.:(

---

### Post by wildmanne39 on 2012-08-20
Hi SUPERFITTER, no it will not work for you.
Thanks

---

### Post by wildmanne39 on 2012-08-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by SUPERFITTER on 2012-08-20
Wild Man 

Thank You for the help!

```
*************** info trace ****************



**** uname -a ****


Linux dennis 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 athlon i386 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"


**** lspci ****


00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Askey Computer Corp. eMachines M6805 802.11g Built-in Wireless [144f:7050]
    Kernel driver in use: b43-pci-bridge
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
    Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235 [1106:0102]
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine


**** lsusb ****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser


**** iwconfig ****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_via82xx            24719  2 
snd_via82xx_modem      18377  5 
gameport               15060  1 snd_via82xx
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
rfcomm                 38139  0 
snd_pcm                80845  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_mpu401_uart        13865  1 snd_via82xx
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_seq_midi           13132  0 
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
arc4                   12473  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon                733687  3 
psmouse                87213  0 
b43                   342643  0 
snd                    62064  21 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
i2c_viapro             12969  0 
pcmcia                 39791  0 
joydev                 17393  0 
k8temp                 12905  0 
snd_page_alloc         14115  3 snd_via82xx,snd_via82xx_modem,snd_pcm
soundcore              14635  1 snd
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
mac80211              436455  1 b43
drm                   197692  5 radeon,ttm,drm_kms_helper
video                  19068  0 
via_ircc               26781  0 
irda                  185517  1 via_ircc
cfg80211              178679  2 b43,mac80211
i2c_algo_bit           13199  1 radeon
bcma                   25651  1 b43
mac_hid                13077  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
crc_ccitt              12595  1 irda
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_logitech           22024  0 
ff_memless             12945  1 hid_logitech
usbhid                 41906  1 hid_logitech
hid                    77367  2 hid_logitech,usbhid
firewire_ohci          40180  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_via               13428  2 
via_rhine              27413  0 
ssb                    50691  1 b43


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.10.10.103
    Prefix:          24 (255.255.255.0)
    Gateway:         10.10.10.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Bonkowski-N:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WEP
    SUPERFITTER1:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WEP




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Bonkowski-N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d8151170
                    Extra: Last beacon: 648ms ago
                    IE: Unknown: 000B426F6E6B6F77736B692D4E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000700000000000000000000000000000000000000
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A88000236915B1AC1021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033031311054000800060050F2040001101100114C696E6B737973205752543136304E763210080002008C103C000101
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"SUPERFITTER1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002d864c183
                    Extra: Last beacon: 100ms ago
                    IE: Unknown: 000C535550455246495454455231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000



**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search hsd1.mi.comcast.net


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    1.137614] b43-pci-bridge 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.137654] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    1.137660] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    1.137665] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    1.137670] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    1.137676] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    1.173541] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0c.0
[   34.646259] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   34.717295] Registered led device: b43-phy0::tx
[   34.717347] Registered led device: b43-phy0::rx
[   34.717394] Registered led device: b43-phy0::radio
[   36.000054] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   36.056082] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.056427] ADDRCONF(NETDEV_UP): wlan0: link is not ready


**************** done ********************
```

---

### Post by wildmanne39 on 2012-08-20
Hi, go into your router and change your security to wpa2 only if you have that option, it works best for linux, then go into network manager and change the security to wpa/wpa2.

Make your wireless setting match the screenshots.

You need to have your wired connection unplugged to stay connected by wireless.
Reboot
Thanks

---

### Post by wildmanne39 on 2012-08-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by JohnXPS on 2012-08-20
I found a solution in another thread which so far has solved my problem (haven't done extensive testing but at least Update Manager ran to completion) :

[http://ubuntuforums.org/search.php?searchid=87381394](http://ubuntuforums.org/search.php?searchid=87381394)
"Faulty wireless connection centrino advanced-N 6230"

I'm not sure if my pasted-in link will work.

MY Dell XPS 17 laptop uses the Intel Centrino advanced N 6230, as did the model in the link. It appears to have been a combination of power management issues and hardware encryption - according to the thread.

Thanks Wild Man!

---

### Post by SUPERFITTER on 2012-08-21
Hi Wild Man

I entered all the information, but it would not allow me to save anything?

---

### Post by wildmanne39 on 2012-08-21
Hi, what happens when you try to save the settings network manager? after you close it and reopen it the settings have changed back to previous settings?

If so then you have another issue that you need to deal with before we can continue.

Did the settings save in your router?
Thanks

---

### Post by SUPERFITTER on 2012-08-21
> **Wild Man said:**
> Hi, what happens when you try to save the settings network manager? after you close it and reopen it the settings have changed back to previous settings?
 
If so then you have another issue that you need to deal with before we can continue.
 
Did the settings save in your router?
Thanks
 
The settings did not save.  
I had no problems with the router until I updated to 12.04, everything worked great. I was online instantly and never lost a connection.

---

### Post by wildmanne39 on 2012-08-21
Hi, in the resolve file where did this come from > search hsd1.mi.comcast.net? did you set that manually?

You need to remove it and reboot, that might help.
Thanks

---

### Post by SUPERFITTER on 2012-08-22
**** resolv ****

 # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) #     [SIZE=2]**DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN**[/SIZE] nameserver 127.0.0.1

[B]search hsd1.mi.comcast.net"


? did you set that manually?"[/B], I don't know where this came from? 




 Should I run this again:
 wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script 

 in terminal and just delete this line?

---

### Post by wildmanne39 on 2012-08-22
Hi, please do:
```
gksu gedit /etc/resolv.conf
```
then remove [COLOR="Red"]search hsd1.mi.comcast.net[/COLOR]
save, close gedit and reboot.
Thanks

---

### Post by SUPERFITTER on 2012-08-22
Wild Man
I ran:
 
Code:
gksu gedit /etc/resolv.conf 
 
then remove [COLOR=red]search hsd1.mi.comcast.net[/COLOR]
save, close gedit and reboot.
 
 
I ran post #8 again:
 
dennis@dennis:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2012-08-22 16:25:32-- [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 107.20.132.92, 50.16.185.216, 184.72.255.242, ...
Connecting to dl.dropbox.com (dl.dropbox.com)|107.20.132.92|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1453 (1.4K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2012-08-22 16:25:32-- [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropbox.com:80.
HTTP request sent, awaiting response... 200 OK
Length: 1453 (1.4K) [text/plain]
Saving to: `wireless_script'
 
100%[======================================>] 1,453 --.-K/s in 0s 
 
2012-08-22 16:25:33 (40.0 MB/s) - `wireless_script' saved [1453/1453]
 
[sudo] password for dennis: 
dennis@dennis:~$ 
 
 
Then I ran Post #10 again and still could not save.  Is there another step I should take from here?

---

### Post by SUPERFITTER on 2012-08-29
Anyone know what happened to Wild Man.  MIA 6 days, is he sick??????????????   

I see other posts are 6 days without a post from Wild Man.  Is there anyone that can help us out at this time?  

Thanks in advance!

---

### Post by wildmanne39 on 2012-09-01
Hi, I am sorry that I am not around much I had to take a job and I work a lot.

I have no more idea's how to fix your issue with out trying a clean install since you can not save your settings, you might start a new thread on that issue.
Thanks

---

### Post by SUPERFITTER on 2012-09-02
Thank You Wild Man 

I understand the need to work in these difficult times. I might have to reinstall Ubuntu to find the problem.

I started this post:

[http://ubuntuforums.org/showthread.php?p=12209018#post12209018](http://ubuntuforums.org/showthread.php?p=12209018#post12209018)

---

### Post by SUPERFITTER on 2012-09-02
Wild Man

I did a clean install and had no wireless.  I then when to my old post and followed it to get my wireless working again.

[http://ubuntuforums.org/showthread.php?t=1785620](http://ubuntuforums.org/showthread.php?t=1785620)

I want to thank you and [chili555]("http://ubuntuforums.org/member.php?u=35909")  again for your help:)

---

### Post by wildmanne39 on 2012-09-02
Hi, your welcome! I am glad you have it working now.
Enjoy

---

