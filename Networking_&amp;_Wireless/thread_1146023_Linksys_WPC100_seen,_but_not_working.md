---
title: "Linksys WPC100 seen, but not working"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by CTolley on 2009-05-02
I'm having a heck of a time getting my wifi to work.  I just installed Jaunty on the laptop, and the first boot after install everything worked fine.  I linked up to my network, surfed around and was a happy man.  I rebooted and had a 'keyring' error that I have since fixed.  Now I cannot connect to my network.  It seems as though the PCMIA card is seen by Ubuntu, but not used.  Meaning, I have options for wifi, it sees other wireless routers (my SSID is hidden), but there are no lights on the device.  Even the power LED is dead.  Is this a driver issue, did an update mess me up, what's going on?

---

### Post by CTolley on 2009-05-03
Bump with more information.

Gateway M305CRV notebook, Linksys WPC100 pcmia adapter

Wifi is 802.11G, WPA2 personal, SSID is not broadcasted, and I turned MAC filtering off on the router.  

lspci report:
> 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
02:02.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller 
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83) 
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01) 

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:e0:b8:57:06:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:18:39:18:fe:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:576 (576.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-18-39-18-FE-49-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

iwconfig:
> lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

lsmod:
> Module                  Size  Used by 
ath_pci                99224  0 
wlan                  210288  1 ath_pci 
ath_hal               198864  1 ath_pci 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat 
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96296  3 i915 
input_polldev          11912  0 
lp                     17156  0 
arc4                    9856  2 
ecb                    10752  2 
ath9k                 263224  0 
mac80211              217208  1 ath9k 
cfg80211               38032  1 mac80211 
led_class              12036  1 ath9k 
joydev                 18368  0 
pcmcia                 44748  0 
ppdev                  15620  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0 
ac97_bus                9856  1 snd_ac97_codec 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
psmouse                61972  0 
serio_raw              13316  0 
soundcore              15200  1 snd 
pcspkr                 10496  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm 
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket 
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic 
shpchp                 40212  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc 
video                  25360  0 
intel_agp              34108  1 
output                 11008  1 video 
agpgart                42696  3 drm,intel_agp 
e100                   41740  0 
mii                    13312  1 e100 
usb_storage            82880  1 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 

most of the dmesg:
> [    0.569892] ACPI: EC: driver started in interrupt mode 
[    0.569892] ACPI: No dock devices found. 
[    0.569892] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[    0.572152] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff] 
[    0.572160] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff] 
[    0.572167] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807] 
[    0.572190] pci 0000:00:02.0: supports D1 
[    0.572214] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff] 
[    0.572220] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff] 
[    0.572245] pci 0000:00:02.1: supports D1 
[    0.572327] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f] 
[    0.572384] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f] 
[    0.572449] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff] 
[    0.572497] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
[    0.572503] pci 0000:00:1d.7: PME# disabled 
[    0.572594] HPET not enabled in BIOS. You might try hpet=force boot option 
[    0.572603] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO 
[    0.572608] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO 
[    0.572631] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07] 
[    0.572641] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03] 
[    0.572648] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07] 
[    0.572656] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03] 
[    0.572664] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f] 
[    0.572672] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff] 
[    0.572726] pci 0000:00:1f.3: reg 20 io port: [0x1600-0x161f] 
[    0.572772] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff] 
[    0.572779] pci 0000:00:1f.5: reg 14 io port: [0x1880-0x18bf] 
[    0.572787] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff] 
[    0.572795] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff] 
[    0.572820] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold 
[    0.572825] pci 0000:00:1f.5: PME# disabled 
[    0.572858] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff] 
[    0.572865] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f] 
[    0.572899] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold 
[    0.572904] pci 0000:00:1f.6: PME# disabled 
[    0.572952] pci 0000:02:02.0: reg 10 32bit mmio: [0x000000-0x000fff] 
[    0.572963] pci 0000:02:02.0: supports D1 D2 
[    0.572966] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.572971] pci 0000:02:02.0: PME# disabled 
[    0.573011] pci 0000:02:08.0: reg 10 32bit mmio: [0xe0200000-0xe0200fff] 
[    0.573019] pci 0000:02:08.0: reg 14 io port: [0x3000-0x303f] 
[    0.573052] pci 0000:02:08.0: supports D1 D2 
[    0.573054] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.573059] pci 0000:02:08.0: PME# disabled 
[    0.573094] pci 0000:00:1e.0: transparent bridge 
[    0.573100] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff] 
[    0.573105] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe02fffff] 
[    0.573137] bus 00 -> node 0 
[    0.573146] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.573556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT] 
[    0.578832] ACPI: PCI Interrupt Link [LNKA] (IRQs *11) 
[    0.578981] ACPI: PCI Interrupt Link [LNKB] (IRQs *10) 
[    0.579128] ACPI: PCI Interrupt Link [LNKC] (IRQs 10) *0, disabled. 
[    0.579276] ACPI: PCI Interrupt Link [LNKD] (IRQs *11) 
[    0.579428] ACPI: PCI Interrupt Link [LNKE] (IRQs *11), disabled. 
[    0.579574] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled. 
[    0.579722] ACPI: PCI Interrupt Link [LNKG] (IRQs 11) *0, disabled. 
[    0.579869] ACPI: PCI Interrupt Link [LNKH] (IRQs *11) 
[    0.580091] ACPI: Power Resource [CFAN] (on) 
[    0.580160] ACPI: Power Resource [CFN2] (off) 
[    0.580160] ACPI: Power Resource [CFN3] (off) 
[    0.580194] ACPI: WMI: Mapper loaded 
[    0.580594] SCSI subsystem initialized 
[    0.580830] libata version 3.00 loaded. 
[    0.580945] usbcore: registered new interface driver usbfs 
[    0.580974] usbcore: registered new interface driver hub 
[    0.581164] usbcore: registered new device driver usb 
[    0.581960] PCI: Using ACPI for IRQ routing 
[    0.582099] Bluetooth: Core ver 2.13 
[    0.584393] NET: Registered protocol family 31 
[    0.584397] Bluetooth: HCI device and connection manager initialized 
[    0.584401] Bluetooth: HCI socket layer initialized 
[    0.584405] NET: Registered protocol family 8 
[    0.584407] NET: Registered protocol family 20 
[    0.584425] NetLabel: Initializing 
[    0.584427] NetLabel:  domain hash size = 128 
[    0.584430] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.584449] NetLabel:  unlabeled traffic allowed by default 
[    0.584565] AppArmor: AppArmor Filesystem Enabled 
[    0.584589] pnp: PnP ACPI init 
[    0.584589] ACPI: bus type pnp registered 
[    0.589721] pnp: PnP ACPI: found 8 devices 
[    0.589725] ACPI: ACPI bus type pnp unregistered 
[    0.589732] PnPBIOS: Disabled by ACPI PNP 
[    0.589748] system 00:04: ioport range 0x600-0x60f has been reserved 
[    0.589752] system 00:04: ioport range 0x800-0x807 has been reserved 
[    0.589756] system 00:04: ioport range 0x1000-0x107f has been reserved 
[    0.589759] system 00:04: ioport range 0x1180-0x11bf has been reserved 
[    0.624557] pci 0000:02:02.0: CardBus bridge, secondary bus 0000:03 
[    0.624561] pci 0000:02:02.0:   IO window: 0x003400-0x0034ff 
[    0.624567] pci 0000:02:02.0:   IO window: 0x003800-0x0038ff 
[    0.624572] pci 0000:02:02.0:   PREFETCH window: 0x88000000-0x8bffffff 
[    0.624578] pci 0000:02:02.0:   MEM window: 0x90000000-0x93ffffff 
[    0.624583] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02 
[    0.624587] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff 
[    0.624594] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff 
[    0.624600] pci 0000:00:1e.0:   PREFETCH window: 0x00000088000000-0x0000008bffffff 
[    0.624620] pci 0000:00:1e.0: setting latency timer to 64 
[    0.624878] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11 
[    0.624883] PCI: setting IRQ 11 as level-triggered 
[    0.624889] pci 0000:02:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[    0.624895] pci 0000:02:02.0: setting latency timer to 64 
[    0.624901] bus: 00 index 0 io port: [0x00-0xffff] 
[    0.624904] bus: 00 index 1 mmio: [0x000000-0xffffffff] 
[    0.624907] bus: 02 index 0 io port: [0x3000-0x3fff] 
[    0.624911] bus: 02 index 1 mmio: [0xe0200000-0xe02fffff] 
[    0.624915] bus: 02 index 2 mmio: [0x88000000-0x8bffffff] 
[    0.624918] bus: 02 index 3 io port: [0x00-0xffff] 
[    0.624920] bus: 02 index 4 mmio: [0x000000-0xffffffff] 
[    0.624923] bus: 03 index 0 io port: [0x3400-0x34ff] 
[    0.624926] bus: 03 index 1 io port: [0x3800-0x38ff] 
[    0.624929] bus: 03 index 2 mmio: [0x88000000-0x8bffffff] 
[    0.624931] bus: 03 index 3 mmio: [0x90000000-0x93ffffff] 
[    0.624945] NET: Registered protocol family 2 
[    0.625120] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.625589] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.626826] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.627554] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.627559] TCP reno registered 
[    0.627792] NET: Registered protocol family 1 
[    0.627986] checking if image is initramfs... it is 
[    1.128015] Switched to high resolution mode on CPU 0 
[    1.422077] Freeing initrd memory: 7342k freed 
[    1.422148] Simple Boot Flag at 0x36 set to 0x1 
[    1.422365] cpufreq: No nForce2 chipset. 
[    1.422554] audit: initializing netlink socket (disabled) 
[    1.422593] type=2000 audit(1241377870.420:1): initialized 
[    1.432514] highmem bounce pool size: 64 pages 
[    1.432523] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    1.434361] VFS: Disk quotas dquot_6.5.1 
[    1.434440] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    1.435479] fuse init (API version 7.10) 
[    1.435611] msgmni has been set to 1698 
[    1.435952] alg: No test for stdrng (krng) 
[    1.436042] io scheduler noop registered 
[    1.436045] io scheduler anticipatory registered 
[    1.436048] io scheduler deadline registered 
[    1.436076] io scheduler cfq registered (default) 
[    1.436100] pci 0000:00:02.0: Boot video device 
[    1.436188] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling 
[    1.441983] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    1.441999] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    1.442658] ACPI: AC Adapter [ACAD] (on-line) 
[    1.463752] ACPI: Battery Slot [BAT0] (battery present) 
[    1.463857] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0 
[    1.463861] ACPI: Power Button (FF) [PWRF] 
[    1.463926] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1 
[    1.464023] ACPI: Lid Switch [LID0] 
[    1.464085] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2 
[    1.464088] ACPI: Sleep Button (CM) [SLPB] 
[    1.466881] fan PNP0C0B:00: registered as cooling_device0 
[    1.466891] ACPI: Fan [FAN1] (on) 
[    1.468890] fan PNP0C0B:01: registered as cooling_device1 
[    1.468899] ACPI: Fan [FAN2] (off) 
[    1.469575] fan PNP0C0B:02: registered as cooling_device2 
[    1.469584] ACPI: Fan [FAN3] (off) 
[    1.469766] ACPI Warning (nspredef-0673): \_PR_.CPU0._PTC: Return Package is too small - found 1, expected 2 [20080926] 
[    1.469776] ACPI: Invalid _PTC data 
[    1.469952] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[    1.469980] processor ACPI_CPU:00: registered as cooling_device3 
[    1.474489] thermal LNXTHERM:01: registered as thermal_zone0 
[    1.477106] ACPI: Thermal Zone [THRM] (53 C) 
[    1.477170] isapnp: Scanning for PnP cards... 
[    1.831132] isapnp: No Plug & Play device found 
[    1.832976] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    1.833644] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10 
[    1.833649] PCI: setting IRQ 10 as level-triggered 
[    1.833655] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10 
[    1.833665] serial 0000:00:1f.6: PCI INT B disabled 
[    1.834665] brd: module loaded 
[    1.835189] loop: module loaded 
[    1.835332] Fixed MDIO Bus: probed 
[    1.835342] PPP generic driver version 2.4.2 
[    1.835432] input: Macintosh mouse button emulation as /devices/virtual/input/input3 
[    1.835479] Driver 'sd' needs updating - please use bus_type methods 
[    1.835494] Driver 'sr' needs updating - please use bus_type methods 
[    1.835603] ata_piix 0000:00:1f.1: version 2.12 
[    1.835616] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007) 
[    1.835884] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10 
[    1.835890] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10 
[    1.835964] ata_piix 0000:00:1f.1: setting latency timer to 64 
[    1.836195] scsi0 : ata_piix 
[    1.836527] scsi1 : ata_piix 
[    1.838097] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14 
[    1.838102] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15 
[    2.000517] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD0A, max UDMA/100 
[    2.000522] ata1.00: 78140160 sectors, multi 16: LBA48 
[    2.016465] ata1.00: configured for UDMA/100 
[    2.180307] ata2.00: ATAPI: Slimtype COMBO LSC-24082K, JGK1, max UDMA/33 
[    2.196269] ata2.00: configured for UDMA/33 
[    2.196706] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5 
[    2.196857] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB) 
[    2.196882] sd 0:0:0:0: [sda] Write Protect is off 
[    2.196886] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    2.196924] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.197026] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB) 
[    2.197046] sd 0:0:0:0: [sda] Write Protect is off 
[    2.197050] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    2.197086] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    2.197091]  sda: sda1 sda2 < sda5 > 
[    2.244644] sd 0:0:0:0: [sda] Attached SCSI disk 
[    2.244728] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    2.245378] scsi 1:0:0:0: CD-ROM            Slimtype COMBO LSC-24082K JGK1 PQ: 0 ANSI: 5 
[    2.247875] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray 
[    2.247880] Uniform CD-ROM driver Revision: 3.20 
[    2.248049] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[    2.248117] sr 1:0:0:0: Attached scsi generic sg1 type 5 
[    2.249032] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    2.249348] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11 
[    2.249355] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11 
[    2.249389] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[    2.249395] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    2.249498] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1 
[    2.253424] ehci_hcd 0000:00:1d.7: debug port 1 
[    2.253433] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported 
[    2.253444] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000 
[    2.268031] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00 
[    2.268138] usb usb1: configuration #1 chosen from 1 choice 
[    2.268177] hub 1-0:1.0: USB hub found 
[    2.268192] hub 1-0:1.0: 4 ports detected 
[    2.268353] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    2.268383] uhci_hcd: USB Universal Host Controller Interface driver 
[    2.268439] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[    2.268450] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[    2.268454] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[    2.268516] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
[    2.268542] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820 
[    2.268656] usb usb2: configuration #1 chosen from 1 choice 
[    2.268696] hub 2-0:1.0: USB hub found 
[    2.268711] hub 2-0:1.0: 2 ports detected 
[    2.269083] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11 
[    2.269088] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11 
[    2.269098] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[    2.269102] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[    2.269167] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
[    2.269192] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840 
[    2.269308] usb usb3: configuration #1 chosen from 1 choice 
[    2.269345] hub 3-0:1.0: USB hub found 
[    2.269360] hub 3-0:1.0: 2 ports detected 
[    2.269522] usbcore: registered new interface driver libusual 
[    2.269572] usbcore: registered new interface driver usbserial 
[    2.269589] USB Serial support registered for generic 
[    2.269610] usbcore: registered new interface driver usbserial_generic 
[    2.269613] usbserial: USB Serial Driver core 
[    2.269676] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    2.270946] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    2.270956] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    2.271122] mice: PS/2 mouse device common for all mice 
[    2.271342] rtc_cmos 00:01: RTC can wake from S4 
[    2.271393] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0 
[    2.271418] rtc0: alarms up to one month, y3k, 242 bytes nvram 
[    2.271525] device-mapper: uevent: version 1.0.3 
[    2.271686] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email] 
[    2.271754] device-mapper: multipath: version 1.0.5 loaded 
[    2.271758] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    2.271888] EISA: Probing bus 0 at eisa.0 
[    2.271898] Cannot allocate resource for EISA slot 1 
[    2.271902] Cannot allocate resource for EISA slot 2 
[    2.271905] Cannot allocate resource for EISA slot 3 
[    2.271927] EISA: Detected 0 cards. 
[    2.272055] cpuidle: using governor ladder 
[    2.272148] cpuidle: using governor menu 
[    2.272854] TCP cubic registered 
[    2.272957] NET: Registered protocol family 10 
[    2.273519] lo: Disabled Privacy Extensions 
[    2.273920] NET: Registered protocol family 17 
[    2.273948] Bluetooth: L2CAP ver 2.11 
[    2.273951] Bluetooth: L2CAP socket layer initialized 
[    2.273955] Bluetooth: SCO (Voice Link) ver 0.6 
[    2.273958] Bluetooth: SCO socket layer initialized 
[    2.274009] Bluetooth: RFCOMM socket layer initialized 
[    2.274022] Bluetooth: RFCOMM TTY layer initialized 
[    2.274025] Bluetooth: RFCOMM ver 1.10 
[    2.274076] IO APIC resources could be not be allocated. 
[    2.274131] Using IPI No-Shortcut mode 
[    2.274280] registered taskstats version 1 
[    2.274426]   Magic number: 9:848:191 
[    2.274535] rtc_cmos 00:01: setting system clock to 2009-05-03 19:11:12 UTC (1241377872) 
[    2.274539] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    2.274542] EDD information not available. 
[    2.275297] Freeing unused kernel memory: 532k freed 
[    2.275442] Write protecting the kernel text: 4128k 
[    2.275491] Write protecting the kernel read-only data: 1532k 
[    2.322406] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
[    2.580046] usb 1-3: new high speed USB device using ehci_hcd and address 2 
[    2.716999] usb 1-3: configuration #1 chosen from 1 choice 
[    2.724543] Initializing USB Mass Storage driver... 
[    2.737369] scsi2 : SCSI emulation for USB Mass Storage devices 
[    2.749939] usbcore: registered new interface driver usb-storage 
[    2.749946] USB Mass Storage support registered. 
[    2.750086] usb-storage: device found at 2 
[    2.750089] usb-storage: waiting for device to settle before scanning 
[    3.359763] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI 
[    3.359769] e100: Copyright(c) 1999-2006 Intel Corporation 
[    3.360110] ACPI: PCI Interrupt Link [LNKE] disabled and referenced, BIOS bug 
[    3.360200] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11 
[    3.360206] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11 
[    3.383714] e100 0000:02:08.0: PME# disabled 
[    3.411051] e100: eth0: e100_probe: addr 0xe0200000, irq 11, MAC addr 00:e0:b8:57:06:65 
[    5.284722] PM: Starting manual resume from disk 
[    5.284729] PM: Resume from partition 8:5 
[    5.284732] PM: Checking hibernation image. 
[    5.284961] PM: Resume from disk failed. 
[    5.308751] EXT3-fs: INFO: recovery required on readonly filesystem. 
[    5.308758] EXT3-fs: write access will be enabled during recovery. 
[    7.763830] usb-storage: device scan complete 
[    7.764998] scsi 2:0:0:0: Direct-Access     USB2.0   CardReader CF RW 0.0> PQ: 0 ANSI: 0 
[    7.766111] scsi 2:0:0:1: Direct-Access     USB2.0   CardReader Combo 0.0> PQ: 0 ANSI: 0 
[    7.769379] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
[    7.769474] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[    7.770815] sd 2:0:0:1: [sdc] Attached SCSI removable disk 
[    7.770881] sd 2:0:0:1: Attached scsi generic sg3 type 0 
[   11.880043] kjournald starting.  Commit interval 5 seconds 
[   11.880077] EXT3-fs: sda1: orphan cleanup on readonly fs 
[   11.880086] ext3_orphan_cleanup: deleting unreferenced inode 1417240 
[   11.880126] EXT3-fs: sda1: 1 orphan inode deleted 
[   11.880129] EXT3-fs: recovery complete. 
[   11.890655] EXT3-fs: mounted filesystem with ordered data mode. 
[   21.830129] udev: starting version 141 
[   22.216394] Linux agpgart interface v0.103 
[   22.254401] agpgart-intel 0000:00:00.0: Intel 855GM Chipset 
[   22.254693] agpgart-intel 0000:00:00.0: detected 8060K stolen memory 
[   22.256596] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000 
[   22.272268] acpi device:04: registered as cooling_device4 
[   22.272714] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/input/input5 
[   22.308584] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no) 
[   22.315192] parport_pc 00:05: reported by Plug and Play ACPI 
[   22.315269] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA] 
[   22.863683] intel_rng: FWH not detected 
[   22.946950] iTCO_vendor_support: vendor-support=0 
[   22.949660] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05 
[   22.949824] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060) 
[   22.949944] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   22.980272] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   23.419848] yenta_cardbus 0000:02:02.0: CardBus bridge found [107b:0402] 
[   23.419872] yenta_cardbus 0000:02:02.0: O2: res at 0x94/0xD4: 00/ea 
[   23.419876] yenta_cardbus 0000:02:02.0: O2: enabling read prefetch/write burst 
[   23.441006] input: PC Speaker as /devices/platform/pcspkr/input/input6 
[   23.549235] yenta_cardbus 0000:02:02.0: ISA IRQ mask 0x0038, PCI irq 11 
[   23.549241] yenta_cardbus 0000:02:02.0: Socket status: 30000821 
[   23.549247] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06 
[   23.549260] yenta_cardbus 0000:02:02.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff 
[   23.549266] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean. 
[   23.549567] yenta_cardbus 0000:02:02.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff 
[   23.549572] yenta_cardbus 0000:02:02.0: pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff 
[   23.656661] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume 
[   24.083464] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10 
[   24.083714] Intel ICH 0000:00:1f.5: setting latency timer to 64 
[   24.200073] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0 
[   24.200134] pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff] 
[   24.575615] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x1c4cb1, caps: 0x80471b/0x0 
[   24.606577] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7 
[   24.908066] intel8x0_measure_ac97_clock: measured 55313 usecs 
[   24.908072] intel8x0: clocking to 48000 
[   25.034818] ppdev: user-space parallel port driver 
[   25.572172] cfg80211: Calling CRDA to update world regulatory domain 
[   25.693313] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean. 
[   25.695122] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[   25.695905] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean. 
[   25.696631] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean. 
[   25.697496] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean. 
[   25.922527] cfg80211: World regulatory domain updated: 
[   25.922535] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   25.922540] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   25.922543] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   25.922547] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   25.922550] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   25.922554] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   25.944912] ath9k: 0.1 
[   25.944975] ath9k 0000:03:00.0: enabling device (0000 -> 0002) 
[   25.944991] ath9k 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   26.665482] phy0: Selected rate control algorithm 'ath9k_rate_control' 
[   26.773637] Registered led device: ath9k-phy0:radio 
[   26.773699] Registered led device: ath9k-phy0:assoc 
[   26.773764] Registered led device: ath9k-phy0:tx 
[   26.773823] Registered led device: ath9k-phy0:rx 
[   26.774791] phy0: Atheros 5416: mem=0xf81e0000, irq=11 
[   27.516298] lp0: using parport0 (interrupt-driven). 
[   28.219271] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k 
[   29.144028] EXT3 FS on sda1, internal journal 
[   32.485813] type=1505 audit(1241377902.709:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2006 
[   32.639740] type=1505 audit(1241377902.861:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2010 
[   32.652029] type=1505 audit(1241377902.877:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2010 
[   32.652121] type=1505 audit(1241377902.877:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2010 
[   32.652182] type=1505 audit(1241377902.877:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2010 
[   33.088702] type=1505 audit(1241377903.313:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2015 
[   33.089047] type=1505 audit(1241377903.313:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2015 
[   33.202861] type=1505 audit(1241377903.425:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2019 
[   46.267782] Marking TSC unstable due to TSC halts in idle 
[   48.624144] Clocksource tsc unstable (delta = -352376703 ns) 
[   51.789949] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   51.802295] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   52.507173] wlan0: authenticate with AP 00:1d:7e:c0:2c:0a 
[   52.508829] wlan0: authenticated 
[   52.508837] wlan0: associate with AP 00:1d:7e:c0:2c:0a 
[   52.510923] wlan0: RX AssocResp from 00:1d:7e:c0:2c:0a (capab=0x401 status=0 aid=2) 
[   52.510927] wlan0: associated 
[   52.519537] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   63.088137] wlan0: no IPv6 routers present 
[   78.816228] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen 
[   78.816240] ata1.00: cmd c8/00:08:07:02:b4/00:00:00:00:00/e0 tag 0 dma 4096 in 
[   78.816242]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout) 
[   78.816246] ata1.00: status: { DRDY } 
[   78.816280] ata1: soft resetting link 
[   78.996754] ata1.00: configured for UDMA/100 
[   78.996772] ata1: EH complete 
[   79.021055] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB) 
[   79.028450] sd 0:0:0:0: [sda] Write Protect is off 
[   79.028454] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[   79.038632] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   79.057875] [drm] Initialized drm 1.1.0 20060810 
[   79.656607] wlan0: disassociating by local choice (reason=3) 
[   79.791706] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11 
[   79.791714] pci 0000:00:02.0: setting latency timer to 64 
[   79.791995] [drm] Initialized i915 1.6.0 20080730 on minor 0 
[   79.920447] [drm:i915_setparam] *ERROR* unknown parameter 4 
[   79.920491] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   81.078489] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   82.362938] mtrr: no MTRR for e8000000,8000000 found 
[   86.569694] [drm:i915_setparam] *ERROR* unknown parameter 4 
[   86.569734] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[   87.401678] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[  109.560524] [drm:i915_getparam] *ERROR* Unknown parameter 6 
[  554.620176] usb 1-1: new high speed USB device using ehci_hcd and address 3 
[  554.807335] usb 1-1: configuration #1 chosen from 1 choice 
[  554.841059] scsi3 : SCSI emulation for USB Mass Storage devices 
[  554.858840] usb-storage: device found at 3 
[  554.858849] usb-storage: waiting for device to settle before scanning 
[  559.856763] usb-storage: device scan complete 
[  559.857851] scsi 3:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0 
[  560.283273] sd 3:0:0:0: [sdd] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[  560.284907] sd 3:0:0:0: [sdd] Write Protect is off 
[  560.284915] sd 3:0:0:0: [sdd] Mode Sense: 02 00 00 00 
[  560.284922] sd 3:0:0:0: [sdd] Assuming drive cache: write through 
[  560.292054] sd 3:0:0:0: [sdd] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[  560.408222] usb 1-1: reset high speed USB device using ehci_hcd and address 3 
[  560.964934] sd 3:0:0:0: [sdd] Write Protect is off 
[  560.964944] sd 3:0:0:0: [sdd] Mode Sense: 02 00 00 00 
[  560.964951] sd 3:0:0:0: [sdd] Assuming drive cache: write through 
[  560.964964]  sdd: sdd1 
[  560.967937] sd 3:0:0:0: [sdd] Attached SCSI removable disk 
[  560.970065] sd 3:0:0:0: Attached scsi generic sg4 type 0 
[  779.035413] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 1 
[  779.232429] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 2 
[  779.432209] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 3 
[  779.632236] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a timed out 
[  796.653603] usb 1-1: USB disconnect, address 3 
[  811.033070] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 1 
[  811.232159] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 2 
[  811.432221] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 3 
[  811.632207] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a timed out 
[  890.068641] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 1 
[  890.268179] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 2 
[  890.468177] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a try 3 
[  890.668106] wlan0: direct probe to AP 00:1d:7e:c0:2c:0a timed out 
[  899.954287] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  900.667883] wlan0: authenticate with AP 00:1d:7e:c0:2c:0a 
[  900.695671] wlan0: authenticated 
[  900.695685] wlan0: associate with AP 00:1d:7e:c0:2c:0a 
[  900.697817] wlan0: RX AssocResp from 00:1d:7e:c0:2c:0a (capab=0x401 status=0 aid=2) 
[  900.697827] wlan0: associated 
[  900.706502] wlan0: disassociating by local choice (reason=3) 
[ 1162.956365] ath_hal: module license 'Proprietary' taints kernel. 
[ 1162.960694] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413) 
[ 1162.982304] wlan: 0.9.4 
[ 1162.993113] ath_pci: 0.9.4 
[ 1284.424108] usb 1-1: new high speed USB device using ehci_hcd and address 4 
[ 1284.611494] usb 1-1: configuration #1 chosen from 1 choice 
[ 1284.653247] scsi4 : SCSI emulation for USB Mass Storage devices 
[ 1284.657098] usb-storage: device found at 4 
[ 1284.657106] usb-storage: waiting for device to settle before scanning 
[ 1289.656849] usb-storage: device scan complete 
[ 1289.657944] scsi 4:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0 
[ 1290.083360] sd 4:0:0:0: [sdd] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[ 1290.085490] sd 4:0:0:0: [sdd] Write Protect is off 
[ 1290.085498] sd 4:0:0:0: [sdd] Mode Sense: 02 00 00 00 
[ 1290.085504] sd 4:0:0:0: [sdd] Assuming drive cache: write through 
[ 1290.092607] sd 4:0:0:0: [sdd] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[ 1290.208219] usb 1-1: reset high speed USB device using ehci_hcd and address 4 
[ 1290.764895] sd 4:0:0:0: [sdd] Write Protect is off 
[ 1290.764905] sd 4:0:0:0: [sdd] Mode Sense: 02 00 00 00 
[ 1290.764912] sd 4:0:0:0: [sdd] Assuming drive cache: write through 
[ 1290.764923]  sdd: sdd1 
[ 1290.767875] sd 4:0:0:0: [sdd] Attached SCSI removable disk 
[ 1290.769867] sd 4:0:0:0: Attached scsi generic sg4 type 0 
[ 1317.317353] usb 1-1: USB disconnect, address 4 
[ 1317.321435] Buffer I/O error on device sdd1, logical block 501 
[ 1317.321447] lost page write due to I/O error on sdd1 
[ 1533.864100] usb 1-2: new high speed USB device using ehci_hcd and address 5 
[ 1534.051038] usb 1-2: configuration #1 chosen from 1 choice 
[ 1534.093737] scsi5 : SCSI emulation for USB Mass Storage devices 
[ 1534.097642] usb-storage: device found at 5 
[ 1534.097650] usb-storage: waiting for device to settle before scanning 
[ 1539.096758] usb-storage: device scan complete 
[ 1539.097862] scsi 5:0:0:0: Direct-Access     Generic  STORAGE DEVICE   1.25 PQ: 0 ANSI: 0 
[ 1539.529479] sd 5:0:0:0: [sdd] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[ 1539.530894] sd 5:0:0:0: [sdd] Write Protect is off 
[ 1539.530904] sd 5:0:0:0: [sdd] Mode Sense: 02 00 00 00 
[ 1539.530910] sd 5:0:0:0: [sdd] Assuming drive cache: write through 
[ 1539.536136] sd 5:0:0:0: [sdd] 256000 512-byte hardware sectors: (131 MB/125 MiB) 
[ 1539.537519] sd 5:0:0:0: [sdd] Write Protect is off 
[ 1539.537545] sd 5:0:0:0: [sdd] Mode Sense: 02 00 00 00 
[ 1539.537551] sd 5:0:0:0: [sdd] Assuming drive cache: write through 
[ 1539.537565]  sdd: sdd1 
[ 1539.543667] sd 5:0:0:0: [sdd] Attached SCSI removable disk 
[ 1539.543841] sd 5:0:0:0: Attached scsi generic sg4 type 0 

sudo lshw -C network:
> *-network               
       description: Ethernet interface 
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 83 
       serial: 00:e0:b8:57:06:65 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s 
  *-network 
       description: Wireless interface 
       product: AR5008 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 1 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:18:39:18:fe:49 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn 

iwlist scan:
> lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wmaster0  Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:1D:7E:C0:2C:0A 
                    ESSID:"linksys" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=18/100  Signal level:-75 dBm  Noise level=-87 dBm 
                    Encryption key:off 
                    IE: Unknown: 00076C696E6B737973 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD09001018020014000000 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:tsf=00000051bdd2f185 
                    Extra: Last beacon: 208ms ago 

I'm running Ubuntu 9.04

---

### Post by tmdavis on 2009-05-05
I have a similar issue.  In fact, I have had this issue since Hardy.  Basically, the Ubuntu Network Manager doesn't support hidden WPA networks.  The problem can be found in the Network Manager applet.  There are a number of bug reports on the issue, but after six months no fix has been made.  The typical answer to the bug is change your network to be visible.  This is not a fix.  The corporate policy at my company prohibits me from implementing that change.  (Another typical response is to use WCID instead, but that isn't stock Ubuntu, and even if it was, it still doesn't work for me.)  Moreover, hidden SSIDs are a basic wireless networking feature.  The fact that Ubuntu doesn't fully support them is ridiculous!  In my opinion, this is a high visibility issue in Ubuntu.  One that reflects poorly on the community.  Why would a company embrace an OS that doesn't properly support something so basic as wireless networking?

---

### Post by CTolley on 2009-05-06
I can feel your annoyance, but from what I've been reading it has more to do with manufacturers supporting the platform.  They don't have any 'reason' to since most consumers use the OS supplied by Best Buy...  I have another card I'm going to try once I figure out where I packed it.  But again, I bought the stuff when I used Windows, in the future I will search for compatible hardware before purchase.  

In 9.04 the Network Manager supports hidden networks just fine, as far as I can tell.  When I try to link up, the wireless light on my router indicates communication, they just don't shake hands like nice components for whatever reason.

---

### Post by tmdavis on 2009-05-07
Have you tried making your network visible?  I have no trouble connecting to my visible WPA network at home, it's just the hidden WPA network at work that gives me trouble.

---

### Post by CTolley on 2009-05-08
I tried that, no-go.  I also disabled MAC filtering, made it unsecure, and just totally dumbed down the system, to no avail.  It just bothers me because it worked when I first installed 9.04, then it stopped after a restart and never came back up.  But, this patch or that patch could have plugged a security hole, and a side-effect was to kill an unsupported hardware.  I don't know, pure speculation.

---

### Post by ganatronic on 2009-05-10
Agree - it definitely seems like addressing this should be a priority. I would love to be able to connect to wireless networks.

---

