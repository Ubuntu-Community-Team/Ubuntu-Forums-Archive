---
title: "wireless do not recognise WEP key"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by strauzen on 2010-05-16
I'm a total noob at this and will apreciate your help.

Ok my problem is the computer does recognise the wireless conections but when I put the wep key It just start trying to connect and then asks for it again, and this goes on and on and on. I'm pretty sure I got the key right so I have no idea whats going on. This happenet to me to with the previous version of ubuntu and also with fedora and instalations in virtual pc, or virtual box. Even normal instalations with partition. This time I'm using wubi.

Thanks for your help and sorry If I put too much information, I dind't get anything with the grep part, I must have done something wrong.

1) PC Brand and Model:
Easynote MX65 P 057

2) Wireless brand, model and chipset:

Using grep in lspci -nn I got this:
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

just in case I'll put the whole information:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

And here what I got with lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:0252 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 174f:a821 Syntek Web Cam - Packard Bell BU45, PB Easynote MX66-208W
Bus 001 Device 003: ID 1d0d:0213  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3) Interface
Here what I got with ifconfig:
eth0      Link encap:Ethernet  direcciónHW 00:1b:fc:45:ab:22  
          Direc. inet:192.168.1.5  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21b:fcff:fe45:ab22/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:12876 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:9748 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:16521345 (16.5 MB)  TX bytes:786121 (786.1 KB)
          Interrupción:16 Dirección base: 0xd800 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  direcciónHW 00:1b:77:13:c5:e4  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

And here with iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Grupalia"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off 

4) Modules
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10802  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
snd_hda_codec_si3054     4236  1 
snd_hda_codec_analog    78702  1 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    1473  2 
snd_timer              23553  2 snd_pcm,snd_seq
nouveau               515131  2 
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                79404  0 
iwlcore               124955  1 iwl3945
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
snd                    70978  17 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              238128  2 iwl3945,iwlcore
drm                   198770  4 nouveau,ttm,drm_kms_helper
usbhid                 40988  0 
hid                    83376  1 usbhid
video                  20623  0 
output                  2503  1 video
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
asus_laptop            20584  0 
ricoh_mmc               3416  0 
i2c_algo_bit            6024  1 nouveau
psmouse                64608  0 
serio_raw               4918  0 
intel_agp              29225  0 
led_class               3732  4 iwl3945,iwlcore,sdhci,asus_laptop
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
cfg80211              148386  3 iwl3945,iwlcore,mac80211
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            49833  1 
8139too                22245  0 
8139cp                 19541  0 
mii                     5237  2 8139too,8139cp
ohci1394               30260  0 
ieee1394               94675  1 ohci1394

5) Kernel boot Messages
well here I think I cant see al the information it gets me, once again I'm sorry if I put to mucho information but I cant get anything with the grep, I must be doing something wrong.

[    0.369940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.370069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.381818] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[    0.381958] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 12)
[    0.382096] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[    0.382232] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 12)
[    0.382367] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 12) *0, disabled.
[    0.382509] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 12)
[    0.382645] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 12)
[    0.382782] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 12)
[    0.382926] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.382934] vgaarb: loaded
[    0.383061] SCSI subsystem initialized
[    0.383176] libata version 3.00 loaded.
[    0.383256] usbcore: registered new interface driver usbfs
[    0.383268] usbcore: registered new interface driver hub
[    0.383299] usbcore: registered new device driver usb
[    0.383454] ACPI: WMI: Mapper loaded
[    0.383456] PCI: Using ACPI for IRQ routing
[    0.383463] pci 0000:00:1c.2: BAR 13: can't allocate resource
[    0.383465] pci 0000:00:1c.2: BAR 14: can't allocate resource
[    0.383467] pci 0000:00:1c.2: BAR 15: can't allocate resource
[    0.383719] NetLabel: Initializing
[    0.383721] NetLabel:  domain hash size = 128
[    0.383723] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.383741] NetLabel:  unlabeled traffic allowed by default
[    0.383781] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.383786] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.390073] Switching to clocksource tsc
[    0.392071] AppArmor: AppArmor Filesystem Enabled
[    0.392091] pnp: PnP ACPI init
[    0.392107] ACPI: bus type pnp registered
[    0.394421] pnp: PnP ACPI: found 13 devices
[    0.394424] ACPI: ACPI bus type pnp unregistered
[    0.394438] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.394448] system 00:08: ioport range 0x250-0x25f has been reserved
[    0.394452] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.394454] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.394457] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.394460] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.394463] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.394466] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.394469] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.394472] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.394475] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.394481] system 00:0a: ioport range 0x400-0x41f has been reserved
[    0.394484] system 00:0a: ioport range 0x250-0x25f has been reserved
[    0.394487] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.394490] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.394493] system 00:0a: iomem range 0xfec18000-0xfec1ffff has been reserved
[    0.394496] system 00:0a: iomem range 0xfec20000-0xfec27fff has been reserved
[    0.394505] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.394511] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.394514] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.394517] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.394520] system 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[    0.399324] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.399327] pci 0000:00:01.0:   IO window: disabled
[    0.399331] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe0fffff
[    0.399335] pci 0000:00:01.0:   PREFETCH window: 0x000000bdf00000-0x000000ddefffff
[    0.399341] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.399344] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.399351] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
[    0.399356] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
[    0.399364] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.399368] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.399374] pci 0000:00:1c.1:   MEM window: 0xfe100000-0xfe1fffff
[    0.399379] pci 0000:00:1c.1:   PREFETCH window: 0x00000080400000-0x000000805fffff
[    0.399387] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.399391] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.399397] pci 0000:00:1c.2:   MEM window: 0x80600000-0x807fffff
[    0.399402] pci 0000:00:1c.2:   PREFETCH window: 0x00000080800000-0x000000809fffff
[    0.399411] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.399415] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.399421] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
[    0.399426] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.399447]   alloc irq_desc for 16 on node -1
[    0.399449]   alloc kstat_irqs on node -1
[    0.399458] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.399463] pci 0000:00:01.0: setting latency timer to 64
[    0.399473] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.399477] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.399482] pci 0000:00:1c.0: setting latency timer to 64
[    0.399492] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.399496]   alloc irq_desc for 17 on node -1
[    0.399498]   alloc kstat_irqs on node -1
[    0.399501] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.399507] pci 0000:00:1c.1: setting latency timer to 64
[    0.399516] pci 0000:00:1c.2: enabling device (0100 -> 0103)
[    0.399520]   alloc irq_desc for 18 on node -1
[    0.399521]   alloc kstat_irqs on node -1
[    0.399525] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.399554] pci 0000:00:1c.2: setting latency timer to 64
[    0.399562] pci 0000:00:1e.0: setting latency timer to 64
[    0.399567] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.399570] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.399573] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfe0fffff]
[    0.399575] pci_bus 0000:01: resource 2 pref mem [0xbdf00000-0xddefffff]
[    0.399578] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.399580] pci_bus 0000:02: resource 1 mem: [0x80000000-0x801fffff]
[    0.399583] pci_bus 0000:02: resource 2 pref mem [0x80200000-0x803fffff]
[    0.399585] pci_bus 0000:03: resource 0 io:  [0x2000-0x2fff]
[    0.399588] pci_bus 0000:03: resource 1 mem: [0xfe100000-0xfe1fffff]
[    0.399590] pci_bus 0000:03: resource 2 pref mem [0x80400000-0x805fffff]
[    0.399593] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.399595] pci_bus 0000:04: resource 1 mem: [0x80600000-0x807fffff]
[    0.399597] pci_bus 0000:04: resource 2 pref mem [0x80800000-0x809fffff]
[    0.399600] pci_bus 0000:06: resource 0 io:  [0xd000-0xdfff]
[    0.399602] pci_bus 0000:06: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.399605] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.399607] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.399652] NET: Registered protocol family 2
[    0.399807] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.400713] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.403523] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.404307] TCP: Hash tables configured (established 262144 bind 65536)
[    0.404310] TCP reno registered
[    0.404446] NET: Registered protocol family 1
[    0.404603] pci 0000:01:00.0: Boot video device
[    0.404686] Simple Boot Flag at 0x52 set to 0x1
[    0.404894] Scanning for low memory corruption every 60 seconds
[    0.405065] audit: initializing netlink socket (disabled)
[    0.405078] type=2000 audit(1274016313.399:1): initialized
[    0.415036] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.416504] VFS: Disk quotas dquot_6.5.2
[    0.416571] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.417220] fuse init (API version 7.13)
[    0.417307] msgmni has been set to 4001
[    0.417536] alg: No test for stdrng (krng)
[    0.417596] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.417601] io scheduler noop registered
[    0.417603] io scheduler anticipatory registered
[    0.417605] io scheduler deadline registered
[    0.417643] io scheduler cfq registered (default)
[    0.417796]   alloc irq_desc for 24 on node -1
[    0.417799]   alloc kstat_irqs on node -1
[    0.417809] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.417816] pcieport 0000:00:01.0: setting latency timer to 64
[    0.417946]   alloc irq_desc for 25 on node -1
[    0.417948]   alloc kstat_irqs on node -1
[    0.417957] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.417968] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.418122]   alloc irq_desc for 26 on node -1
[    0.418124]   alloc kstat_irqs on node -1
[    0.418133] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.418144] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.418301]   alloc irq_desc for 27 on node -1
[    0.418303]   alloc kstat_irqs on node -1
[    0.418312] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.418322] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.418436] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.418576] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.418751] ACPI: AC Adapter [AC0] (on-line)
[    0.418835] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.419939] ACPI: Lid Switch [LID]
[    0.419988] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.419995] ACPI: Power Button [PWRB]
[    0.420048] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.420054] ACPI: Sleep Button [SLPB]
[    0.420100] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.420103] ACPI: Power Button [PWRF]
[    0.420979] ACPI Warning: Incorrect checksum in table [SSDT] - 83, should be 44 (20090903/tbutils-314)
[    0.420986] ACPI: SSDT 000000007ffd7a40 00CC3 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.423553] Monitor-Mwait will be used to enter C-1 state
[    0.423587] Monitor-Mwait will be used to enter C-2 state
[    0.423593] Marking TSC unstable due to TSC halts in idle
[    0.423654] processor LNXCPU:00: registered as cooling_device0
[    0.423902] ACPI Warning: Incorrect checksum in table [SSDT] - 11, should be D7 (20090903/tbutils-314)
[    0.423908] ACPI: SSDT 000000007ffd8710 004A4 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.424496] Switching to clocksource hpet
[    0.429807] processor LNXCPU:01: registered as cooling_device1
[    0.434690] thermal LNXTHERM:01: registered as thermal_zone0
[    0.434699] ACPI: Thermal Zone [THRM] (56 C)
[    0.436277] Linux agpgart interface v0.103
[    0.436317] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.437730] brd: module loaded
[    0.438246] loop: module loaded
[    0.438340] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.438451] ata_piix 0000:00:1f.2: version 2.13
[    0.438472]   alloc irq_desc for 19 on node -1
[    0.438474]   alloc kstat_irqs on node -1
[    0.438481] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.438488] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.438538] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.438639] scsi0 : ata_piix
[    0.438713] scsi1 : ata_piix
[    0.439960] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.439963] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.440388] Fixed MDIO Bus: probed
[    0.440425] PPP generic driver version 2.4.2
[    0.440462] tun: Universal TUN/TAP device driver, 1.6
[    0.440464] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.440565] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.440587]   alloc irq_desc for 23 on node -1
[    0.440589]   alloc kstat_irqs on node -1
[    0.440594] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.440610] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.440614] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.440647] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.440675] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.440687] ehci_hcd 0000:00:1d.7: debug port 1
[    0.444583] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.444601] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebfbc00
[    0.462799] ACPI: Battery Slot [BAT0] (battery present)
[    0.470024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.470167] usb usb1: configuration #1 chosen from 1 choice
[    0.470200] hub 1-0:1.0: USB hub found
[    0.470210] hub 1-0:1.0: 8 ports detected
[    0.470295] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.470316] uhci_hcd: USB Universal Host Controller Interface driver
[    0.470363] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.470374] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.470377] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.470415] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.470449] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ec00
[    0.470548] usb usb2: configuration #1 chosen from 1 choice
[    0.470576] hub 2-0:1.0: USB hub found
[    0.470584] hub 2-0:1.0: 2 ports detected
[    0.470635] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.470642] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.470646] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.470678] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.470716] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[    0.470808] usb usb3: configuration #1 chosen from 1 choice
[    0.470834] hub 3-0:1.0: USB hub found
[    0.470840] hub 3-0:1.0: 2 ports detected
[    0.470887] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.470894] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.470897] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.470938] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.470975] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    0.471064] usb usb4: configuration #1 chosen from 1 choice
[    0.471096] hub 4-0:1.0: USB hub found
[    0.471108] hub 4-0:1.0: 2 ports detected
[    0.471155]   alloc irq_desc for 22 on node -1
[    0.471157]   alloc kstat_irqs on node -1
[    0.471163] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    0.471170] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.471173] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.471209] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.471244] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000e480
[    0.471334] usb usb5: configuration #1 chosen from 1 choice
[    0.471363] hub 5-0:1.0: USB hub found
[    0.471370] hub 5-0:1.0: 2 ports detected
[    0.471472] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.473227] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.474103] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.474110] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.474140] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.474164] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.474191] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.474336] mice: PS/2 mouse device common for all mice
[    0.474511] rtc_cmos 00:03: RTC can wake from S4
[    0.474555] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.474587] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.474724] device-mapper: uevent: version 1.0.3
[    0.474853] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.474926] device-mapper: multipath: version 1.1.0 loaded
[    0.474929] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.475138] cpuidle: using governor ladder
[    0.475226] cpuidle: using governor menu
[    0.475585] TCP cubic registered
[    0.475713] NET: Registered protocol family 10
[    0.476171] lo: Disabled Privacy Extensions
[    0.476459] NET: Registered protocol family 17
[    0.477207] PM: Resume from disk failed.
[    0.477227] registered taskstats version 1
[    0.477805]   Magic number: 10:946:432
[    0.477908] rtc_cmos 00:03: setting system clock to 2010-05-16 13:25:14 UTC (1274016314)
[    0.477912] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.477914] EDD information not available.
[    0.506604] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.538245] Freeing initrd memory: 8446k freed
[    0.640829] ata2.00: ATAPI: Optiarc DVD RW AD-5540A, 2.62, max UDMA/33
[    0.640969] ata1.00: ATA-7: ST9120822AS, 3.ALC, max UDMA/133
[    0.640972] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.680699] ata2.00: configured for UDMA/33
[    0.680798] ata1.00: configured for UDMA/133
[    0.680950] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.AL PQ: 0 ANSI: 5
[    0.681151] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.681218] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    0.681269] sd 0:0:0:0: [sda] Write Protect is off
[    0.681271] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.681298] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.681483]  sda:
[    0.682888] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-5540A  2.62 PQ: 0 ANSI: 5
[    0.685751] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.685756] Uniform CD-ROM driver Revision: 3.20
[    0.685918] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.686014] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.707484]  sda1 sda2 < sda5 >
[    0.720552] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.720584] Freeing unused kernel memory: 876k freed
[    0.721022] Write protecting the kernel read-only data: 7680k
[    0.737221] udev: starting version 151
[    0.833151] ohci1394 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.837906] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.902104] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    0.906216] 8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    0.908640] 8139too Fast Ethernet driver 0.9.28
[    0.908682] 8139too 0000:06:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.910051] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    0.910149] eth0: RealTek RTL8139 at 0xd800, 00:1b:fc:45:ab:22, IRQ 16
[    1.051964] usb 1-2: configuration #1 chosen from 1 choice
[    1.058619] Initializing USB Mass Storage driver...
[    1.058753] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.058862] usbcore: registered new interface driver usb-storage
[    1.058865] USB Mass Storage support registered.
[    1.058952] usb-storage: device found at 3
[    1.058954] usb-storage: waiting for device to settle before scanning
[    1.170047] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    1.534078] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    1.570474] usb 1-8: configuration #1 chosen from 1 choice
[    1.850053] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.035686] usb 2-1: configuration #1 chosen from 1 choice
[    2.220257] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800038ce080]
[    6.050306] usb-storage: device scan complete
[    6.050986] scsi 2:0:0:0: Direct-Access     TDK LoR  Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[    6.051497] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.052720] sd 2:0:0:0: [sdb] 15843328 512-byte logical blocks: (8.11 GB/7.55 GiB)
[    6.053284] sd 2:0:0:0: [sdb] Write Protect is off
[    6.053291] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    6.053296] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.620095] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.620105]  sdb: sdb1
[    6.622337] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.622344] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   17.701376] udev: starting version 151
[   17.820645] lp: driver loaded but no devices found
[   17.839173] intel_rng: FWH not detected
[   17.937353] cfg80211: Calling CRDA to update world regulatory domain
[   18.005986] ricoh-mmc: Ricoh MMC Controller disabling driver
[   18.005989] ricoh-mmc: Copyright(c) Philip Langdale
[   18.006024] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   18.006050] ricoh-mmc: Controller is now disabled.
[   18.007786] asus_laptop: Asus Laptop Support version 0.42
[   18.012157] sdhci: Secure Digital Host Controller Interface driver
[   18.012160] sdhci: Copyright(c) Pierre Ossman
[   18.013396] sdhci-pci 0000:06:01.1: SDHCI controller found [1180:0822] (rev 19)
[   18.013419] sdhci-pci 0000:06:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   18.015481] Registered led device: mmc0::
[   18.016520] mmc0: SDHCI controller on PCI [0000:06:01.1] using PIO
[   18.048444] usbcore: registered new interface driver hiddev
[   18.050795] asus_laptop:   T12J model detected
[   18.051602] cfg80211: World regulatory domain updated:
[   18.051605]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.051608]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.051611]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.051614]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.051616]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.051619]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.051808] input: Logitech  USB WheelMouse      as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input6
[   18.051928] generic-usb 0003:062A:0252.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech  USB WheelMouse     ] on usb-0000:00:1d.0-1/input0
[   18.051956] usbcore: registered new interface driver usbhid
[   18.051959] usbhid: v2.6:USB HID core driver
[   18.058767] type=1505 audit(1274009132.074:2):  operation="profile_load" pid=653 name="/sbin/dhclient3"
[   18.059451] type=1505 audit(1274009132.074:3):  operation="profile_load" pid=653 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.059817] type=1505 audit(1274009132.074:4):  operation="profile_load" pid=653 name="/usr/lib/connman/scripts/dhclient-script"
[   18.085128] acpi device:19: registered as cooling_device2
[   18.085733] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:15/LNXVIDEO:00/input/input7
[   18.085851] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.105690] [drm] Initialized drm 1.1.0 20060810
[   18.131982] input: Asus Laptop extra buttons as /devices/virtual/input/input8
[   18.136696] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   18.196142] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   18.196147] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   18.196297] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.196311] iwl3945 0000:03:00.0: setting latency timer to 64
[   18.214694] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.214702] nouveau 0000:01:00.0: setting latency timer to 64
[   18.219125] [drm] nouveau 0000:01:00.0: failed to evaluate _DSM: 5
[   18.224091] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x046700a3)
[   18.224332] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[   18.224351] [drm] nouveau 0000:01:00.0: ... BIOS signature not found
[   18.224354] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[   18.288058] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.288063] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.288282]   alloc irq_desc for 28 on node -1
[   18.288284]   alloc kstat_irqs on node -1
[   18.288340] iwl3945 0000:03:00.0: irq 28 for MSI/MSI-X
[   18.294232] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.375531]   alloc irq_desc for 21 on node -1
[   18.375535]   alloc kstat_irqs on node -1
[   18.375548] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.375613] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.380878] [drm] nouveau 0000:01:00.0: ... appears to be valid
[   18.380882] [drm] nouveau 0000:01:00.0: BIT BIOS found
[   18.380886] [drm] nouveau 0000:01:00.0: Bios version 05.72.22.46
[   18.380889] [drm] nouveau 0000:01:00.0: TMDS table script pointers not stubbed
[   18.380892] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
[   18.380895] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[   18.380898] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 10 2
[   18.380901] [drm] nouveau 0000:01:00.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[   18.380904] [drm] nouveau 0000:01:00.0:   1: 0x00001130: type 0x30 idx 1 tag 0x07
[   18.380907] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   18.380910] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[   18.380912] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[   18.380915] [drm] nouveau 0000:01:00.0:   5: 0x00000340: type 0x40 idx 3 tag 0xff
[   18.380917] [drm] nouveau 0000:01:00.0:   6: 0x00002431: type 0x31 idx 4 tag 0x08
[   18.380920] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 03005323 00000004
[   18.380923] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01010300 00000028
[   18.380925] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04021312 00000000
[   18.380928] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 020323f1 00c0c080
[   18.380940] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDFB7
[   18.381006] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE2E6
[   18.560231] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE884
[   18.560262] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE9FF
[   18.580155] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEC58
[   18.595132] [TTM] Zone  kernel: Available graphics memory: 1028948 kiB.
[   18.595144] [drm] nouveau 0000:01:00.0: 64 MiB VRAM
[   18.597176] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[   18.598368] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[   18.599491] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[   18.599502] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[   18.599511] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[   18.687007] [drm] nouveau 0000:01:00.0: Detected a LVDS connector
[   18.793478] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[   18.793516] [drm] nouveau 0000:01:00.0: Detected a DVI-D connector
[   18.793546] [drm] nouveau 0000:01:00.0: Detected a TV connector
[   18.795979] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds encoder (output 0)
[   18.795983] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
[   18.795987] [drm] nouveau 0000:01:00.0: 0xD0EB: Parsing digital output script table
[   18.810069] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   18.887240] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000
[   18.926000] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   19.070030] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 1)
[   19.070035] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 2)
[   19.070038] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 3)
[   19.172231] Adding 261112k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:3 across:35137692k 
[   19.230175] [drm] nouveau 0000:01:00.0: allocated 1280x800 fb: 0x49000, bo ffff88004faad600
[   19.230275] fb0: nouveaufb frame buffer device
[   19.230277] registered panic notifier
[   19.230283] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[   19.231978] vga16fb: initializing
[   19.231981] vga16fb: mapped to 0xffff8800000a0000
[   19.231984] vga16fb: not registering due to another framebuffer present
[   19.253038] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 0 using output A
[   19.253042] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
[   19.253046] [drm] nouveau 0000:01:00.0: 0xD14C: Parsing digital output script table
[   19.430053] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds encoder (output 0)
[   19.430060] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
[   19.430066] [drm] nouveau 0000:01:00.0: 0xD0DC: Parsing digital output script table
[   19.430079] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC 0 using output A
[   19.432795] Console: switching to colour frame buffer device 160x50
[   19.500379] type=1505 audit(1274009133.522:5):  operation="profile_load" pid=863 name="/usr/share/gdm/guest-session/Xsession"
[   19.506045] type=1505 audit(1274009133.522:6):  operation="profile_replace" pid=864 name="/sbin/dhclient3"
[   19.506789] type=1505 audit(1274009133.522:7):  operation="profile_replace" pid=864 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.507174] type=1505 audit(1274009133.522:8):  operation="profile_replace" pid=864 name="/usr/lib/connman/scripts/dhclient-script"
[   19.511338] type=1505 audit(1274009133.532:9):  operation="profile_load" pid=868 name="/usr/bin/evince"
[   19.530587] type=1505 audit(1274009133.552:10):  operation="profile_load" pid=868 name="/usr/bin/evince-previewer"
[   19.542620] type=1505 audit(1274009133.562:11):  operation="profile_load" pid=868 name="/usr/bin/evince-thumbnailer"
[   19.621882] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   19.640793] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   19.708771] Registered led device: iwl-phy0::radio
[   19.708795] Registered led device: iwl-phy0::assoc
[   19.708874] Registered led device: iwl-phy0::RX
[   19.708891] Registered led device: iwl-phy0::TX
[   19.731173] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.732483] eth0: link down
[   19.732800] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.763968] ppdev: user-space parallel port driver
[   20.202088] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   20.203206] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   33.916679] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   33.917085] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   44.460032] eth0: no IPv6 routers present
[   50.698949] wlan0: deauthenticating from 00:16:38:f2:bc:e9 by local choice (reason=3)
[   50.700251] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 1)
[   50.893959] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 2)
[   51.093264] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 3)
[   51.294693] wlan0: direct probe to AP 00:16:38:f2:bc:e9 timed out
[   63.547932] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 1)
[   63.740035] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 2)
[   63.940064] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 3)
[   64.140052] wlan0: direct probe to AP 00:16:38:f2:bc:e9 timed out
[   76.434355] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 1)
[   76.632562] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 2)
[   76.832583] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 3)
[   77.030060] wlan0: direct probe to AP 00:16:38:f2:bc:e9 timed out
[   89.283651] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 1)
[   89.480066] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 2)
[   89.680074] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 3)
[   89.880059] wlan0: direct probe to AP 00:16:38:f2:bc:e9 timed out
[  102.168808] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 1)
[  102.363606] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 2)
[  102.560038] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 3)
[  102.762576] wlan0: direct probe to AP 00:16:38:f2:bc:e9 timed out
[  110.375909] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 1)
[  110.570049] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 2)
[  110.772575] wlan0: direct probe to AP 00:16:38:f2:bc:e9 (try 3)
[  110.970049] wlan0: direct probe to AP 00:16:38:f2:bc:e9 timed out

6) Network configuration

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:13:c5:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:fe1ff000-fe1fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:1b:fc:45:ab:22
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:d800(size=256) memory:feafe400-feafe4ff

7) Network scan
Ok this is weird I made three atemps and got three diferent results so I'll put all three:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

^[[Awlan0     Scan completed :
          Cell 01 - Address: 00:16:38:F2:BC:E9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"Grupalia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000efb9beb183
                    Extra: Last beacon: 2230ms ago
                    IE: Unknown: 000847727570616C6961
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
          Cell 02 - Address: 00:02:CF:CE:B1:A5
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WLAN_C3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f4c967c1b6
                    Extra: Last beacon: 2480ms ago
                    IE: Unknown: 0007574C414E5F4333
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010A
                    IE: Unknown: 050C020300020000000000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C


8 )Ubuntu version
Description:    Ubuntu 10.04 LTS

9) Kernel/architecture
2.6.32-21-generic x86_64

10) Restarting Networks
And here I got 2 diferent results:

 * Reconfiguring network interfaces...                                                              Ignoring unknown interface eth0=eth0.
                                                                                             [ OK ]
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces..

---

### Post by Bucky Ball on 2010-05-16
System->Admin->Network. Click wireless and properties. Are the details in there the same as your AP (access point)/router?

ESSID is the name of your router. It is showing 'Not Associated'

Configuration: 'Auto DHCP config' if your router is serving you an ip or 'static' if you are sending one.

One other thing: Have you plugged in an ethernet cable and gotten all updates??? You could be missing something for your wireless card and that would probably be remedied. Try that if you haven't.

---

### Post by strauzen on 2010-05-16
Ok I don't know how to look my AP, and I don't know if I got the tab you said because in admin I had no network properties panel. In the other hand I got to someplace where I could edit my connection and it was marked DHCP while its suposed to be static only there isn't any sta
tic option.
and in the SSID its marked the name of my router so I gess it is correct.

On the other hand yes I got my ethernet cable connected got all the updates and it didn't help, the problem persists.

Anyway I can get the info I'm missing?

---

### Post by Bucky Ball on 2010-05-16
If you are sending a static IP and the router is sending one DHCP you are never going to connect. Get into the router admin page (usually put the IP of the router into Firefox and you should get the admin) and switch off DHCP server on the router. Check all details.

---

### Post by strauzen on 2010-05-17
no, I explained miself badly, linux its considering it a DHCP while my ruter has a static one, but in linux config options for the wireless I see nowhere the option to change it to static, when I open the menu I have other options, I'll put them here this afternoon, right now I don't have acces to it. Thanks

---

### Post by Bucky Ball on 2010-05-17
Yes your router has a static one. This IP is used for your gateway if you were to set up a static IP on your machine.

What I am saying is this: Besides having its own IP, your router will be set up as a DHCP server, ie, it will serve and assign an IP to every machine on your network, or DHCP server will be off, in which case it is serving a static, or the same, IP to each machine every boot. Or, it is not set to either in which case you have your machine set up and sending a static IP (which is what my three machines are doing).

So, you need to check on your router to make sure it is serving you an IP and check in your network set up to make sure your wireless is set to Configuration=Auto Configuration (DHCP).

---

### Post by strauzen on 2010-05-18
Ok, right now I have a problem that my father lost theinfo about the router and we don't have nor the password that we changed nor the keys we need if we restarted it. Are there other things we can do to try and solve this? I have windows in this same pc and I have no problem with the conection, there must be something to be done. Thanks again for your help.

---

### Post by onthatday7yearsago on 2010-05-18
If you can no longer access the administrative setting on your router then you're going to have issues. Most have a hard reset button somewhere which will perform a factory restore if pressed long enough. This should restore the original login for the router, which should be googleable without too much issue for most routers. Then you can restore your old settings and actually be sure that you have the right keys.

---

### Post by strauzen on 2010-05-18
yep, but my router have a security if you reset it you must put in some keys before it lets you connect to it, and we also misplaced those papers, I'm waiting for my father to call the persons responsable for it see if they can give us new keys, too bad for me he doesn't want me messing with the router settings so I depend on him.

Also I don't know if I forgot to mention, but I tried to connect to a friends router with WEP security and I had exactly the same problem.

Ok got a look at the router, DHCP is enabled, the SSID linux gives me the correct one, and BSSID it didn't got it but I put the one in the router config, but it still asks me for the WEP key

I don't know what else to look

---

### Post by strauzen on 2010-05-18
Ive also seen that my key is 64bit but I don't get that option from the network manager o.O even though in my friends router he had a 128bit key and I had the same problem as here. I'm completely lost

Ive tried now to connect with Wicd to be able to connect with a 64bit key and he allways sends me a bad password error while Im sure I got it right

---

### Post by strauzen on 2010-05-19
I've put out my secuity and It doesn't connect, after a while triying it doesn't connect, so it musn't be the security protocols, any ideas?

---

### Post by pbenerjee on 2010-06-04
> **strauzen said:**
> Ive also seen that my key is 64bit but I don't get that option from the network manager o.O even though in my friends router he had a 128bit key and I had the same problem as here. I'm completely lost

Ive tried now to connect with Wicd to be able to connect with a 64bit key and he allways sends me a bad password error while Im sure I got it right

Hi Strauzen, I am an absolute newbie but I have some info to share for you. I connect from Lucid Lynx to WiFi network at home using WEP encryption using 5 lettered and 13 lettered passwords. Both work well.
I connect to WIFi network of my mobile phone, which uses a software called WMWiFiRouter. In that software, the password set up prompt mentions that it uses 128 bit encryption. It connects from Lucid Lynx pretty fine.

So, I think Ubuntu connects with WiFi networks using 128 bit WEP encryption

---

