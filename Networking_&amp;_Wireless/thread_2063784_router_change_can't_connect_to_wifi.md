---
title: "router change: can't connect to wifi"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by Nuc72 on 2012-09-27
Hi Guys!

I've got the following problem: after a router change my Xubuntu desktop PC can't connect to wifi. It sees the available networks (my wifi network also), but it cannot connect: a popup window appears again and again and ask for the password (naturally I've typed the proper password before).
My DELL laptop can connect to wifi under Windows7 and Xubuntu 12.04 also.
My desktop PC can connect to wifi under Windows7 (it's a dual boot system).
The desktop PC should connect to wifi through a USB TP-LINK TL-WN321G dongle receiver.
I've tried it on Xubuntu 12.04 64bit with the latest kernel, a freshly installed 12.04 64bit with kernel 3.2.0.23 and a freshly installed 11.10 64bit with kernel 3.0.0.12 - without success.

Infos:
lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 005 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 001 Device 005: ID 0424:2640 Standard Microsystems Corp. USB 2.0 Hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 006: ID 0424:4060 Standard Microsystems Corp. Ultra Fast Media Reader
```lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
```ifconfig:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7584 (7.5 KB)  TX bytes:7584 (7.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:cd:ba:7d:91  
          inet6 addr: fe80::223:cdff:feba:7d91/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:8944 (8.9 KB)
```iwconfig:
```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```lsmod:
```
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  4 
bluetooth             166112  10 bnep,rfcomm
arc4                   12529  2 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
mac80211              310872  2 rt2x00usb,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
usb_storage            57901  0 
uas                    18027  0 
asus_atk0110           18078  0 
radeon               1015995  2 
psmouse                73882  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd                    68266  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  4 radeon,ttm,drm_kms_helper
sp5100_tco             13791  0 
i2c_algo_bit           13423  1 radeon
i2c_piix4              13301  0 
wmi                    19256  0 
soundcore              12680  1 snd
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
shpchp                 37345  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
xhci_hcd               78641  0 
pata_atiixp            13164  0 
ahci                   26002  3 
libahci                26861  1 ahci
```dmesg:
```
[    0.641866] pci 0000:00:11.0: reg 14: [io  0xc000-0xc003]
[    0.641873] pci 0000:00:11.0: reg 18: [io  0xb000-0xb007]
[    0.641880] pci 0000:00:11.0: reg 1c: [io  0xa000-0xa003]
[    0.641887] pci 0000:00:11.0: reg 20: [io  0x9000-0x900f]
[    0.641893] pci 0000:00:11.0: reg 24: [mem 0xfe8ffc00-0xfe8fffff]
[    0.641908] pci 0000:00:11.0: set SATA to AHCI mode
[    0.641933] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.641943] pci 0000:00:12.0: reg 10: [mem 0xfe8fe000-0xfe8fefff]
[    0.641993] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.642006] pci 0000:00:12.2: reg 10: [mem 0xfe8ff800-0xfe8ff8ff]
[    0.642056] pci 0000:00:12.2: supports D1 D2
[    0.642057] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.642060] pci 0000:00:12.2: PME# disabled
[    0.642074] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.642084] pci 0000:00:13.0: reg 10: [mem 0xfe8fd000-0xfe8fdfff]
[    0.642133] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.642146] pci 0000:00:13.2: reg 10: [mem 0xfe8ff400-0xfe8ff4ff]
[    0.642195] pci 0000:00:13.2: supports D1 D2
[    0.642196] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.642199] pci 0000:00:13.2: PME# disabled
[    0.642214] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.642264] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.642273] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.642280] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.642287] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.642293] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.642300] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.642325] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.642341] pci 0000:00:14.2: reg 10: [mem 0xfe8f8000-0xfe8fbfff 64bit]
[    0.642381] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.642384] pci 0000:00:14.2: PME# disabled
[    0.642393] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.642445] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.642474] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.642484] pci 0000:00:14.5: reg 10: [mem 0xfe8fc000-0xfe8fcfff]
[    0.642530] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
[    0.642540] pci 0000:00:16.0: reg 10: [mem 0xfe8f7000-0xfe8f7fff]
[    0.642589] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
[    0.642602] pci 0000:00:16.2: reg 10: [mem 0xfe8ff000-0xfe8ff0ff]
[    0.642651] pci 0000:00:16.2: supports D1 D2
[    0.642652] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.642655] pci 0000:00:16.2: PME# disabled
[    0.642668] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.642679] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.642687] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.642697] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.642707] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.642739] pci 0000:01:05.0: [1002:9715] type 0 class 0x000300
[    0.642746] pci 0000:01:05.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.642749] pci 0000:01:05.0: reg 14: [io  0xe000-0xe0ff]
[    0.642753] pci 0000:01:05.0: reg 18: [mem 0xfeaf0000-0xfeafffff]
[    0.642761] pci 0000:01:05.0: reg 24: [mem 0xfe900000-0xfe9fffff]
[    0.642770] pci 0000:01:05.0: supports D1 D2
[    0.642797] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.642800] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.642802] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.642805] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.642834] pci 0000:02:00.0: [1033:0194] type 0 class 0x000c03
[    0.642847] pci 0000:02:00.0: reg 10: [mem 0xfebfe000-0xfebfffff 64bit]
[    0.642899] pci 0000:02:00.0: PME# supported from D0 D3hot
[    0.642901] pci 0000:02:00.0: PME# disabled
[    0.648055] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.648059] pci 0000:00:05.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.648062] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.648065] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.648113] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.648116] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.648119] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.648122] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.648124] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.648125] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.648127] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.648128] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.648130] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xdfffffff] (subtractive decode)
[    0.648131] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.648142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.648232] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.648254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.648277] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.648367]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.648452]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.650944] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[    0.650983] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[    0.651023] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[    0.651061] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *9 10 11 14 15)
[    0.651091] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.651115] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.651138] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.651161] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 14 15) *0
[    0.651224] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.651226] vgaarb: loaded
[    0.651227] vgaarb: bridge control possible 0000:01:05.0
[    0.651336] SCSI subsystem initialized
[    0.651353] libata version 3.00 loaded.
[    0.651353] usbcore: registered new interface driver usbfs
[    0.651353] usbcore: registered new interface driver hub
[    0.651353] usbcore: registered new device driver usb
[    0.651353] PCI: Using ACPI for IRQ routing
[    0.657647] PCI: pci_cache_line_size set to 64 bytes
[    0.657692] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.657694] reserve RAM buffer: 00000000cff80000 - 00000000cfffffff 
[    0.657753] NetLabel: Initializing
[    0.657754] NetLabel:  domain hash size = 128
[    0.657755] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.657762] NetLabel:  unlabeled traffic allowed by default
[    0.657787] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.657790] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.659809] Switching to clocksource hpet
[    0.659823] Switched to NOHz mode on CPU #3
[    0.659836] Switched to NOHz mode on CPU #0
[    0.659817] Switched to NOHz mode on CPU #2
[    0.659812] Switched to NOHz mode on CPU #1
[    0.659836] AppArmor: AppArmor Filesystem Enabled
[    0.659836] pnp: PnP ACPI init
[    0.659836] ACPI: bus type pnp registered
[    0.659836] pnp 00:00: [bus 00-ff]
[    0.659836] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.659836] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.659836] pnp 00:00: [io  0x0d00-0xffff window]
[    0.659836] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.659836] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.659836] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
[    0.659836] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.659836] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.659846] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.659848] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.659872] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.660193] pnp 00:02: [dma 4]
[    0.660194] pnp 00:02: [io  0x0000-0x000f]
[    0.660196] pnp 00:02: [io  0x0081-0x0083]
[    0.660197] pnp 00:02: [io  0x0087]
[    0.660198] pnp 00:02: [io  0x0089-0x008b]
[    0.660199] pnp 00:02: [io  0x008f]
[    0.660201] pnp 00:02: [io  0x00c0-0x00df]
[    0.660220] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.660225] pnp 00:03: [io  0x0070-0x0071]
[    0.660232] pnp 00:03: [irq 8]
[    0.660247] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.660252] pnp 00:04: [io  0x0061]
[    0.660266] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.660271] pnp 00:05: [io  0x00f0-0x00ff]
[    0.660274] pnp 00:05: [irq 13]
[    0.660290] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.660462] pnp 00:06: [mem 0xfed00000-0xfed003ff]
[    0.660479] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.660679] pnp 00:07: [io  0x0060]
[    0.660681] pnp 00:07: [io  0x0064]
[    0.660682] pnp 00:07: [mem 0xfec00000-0xfec00fff]
[    0.660684] pnp 00:07: [mem 0xfee00000-0xfee00fff]
[    0.660710] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.660712] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.660714] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.660803] pnp 00:08: [io  0x0010-0x001f]
[    0.660804] pnp 00:08: [io  0x0022-0x003f]
[    0.660806] pnp 00:08: [io  0x0062-0x0063]
[    0.660807] pnp 00:08: [io  0x0065-0x006f]
[    0.660808] pnp 00:08: [io  0x0072-0x007f]
[    0.660809] pnp 00:08: [io  0x0080]
[    0.660810] pnp 00:08: [io  0x0084-0x0086]
[    0.660812] pnp 00:08: [io  0x0088]
[    0.660813] pnp 00:08: [io  0x008c-0x008e]
[    0.660814] pnp 00:08: [io  0x0090-0x009f]
[    0.660815] pnp 00:08: [io  0x00a2-0x00bf]
[    0.660816] pnp 00:08: [io  0x00b1]
[    0.660817] pnp 00:08: [io  0x00e0-0x00ef]
[    0.660819] pnp 00:08: [io  0x04d0-0x04d1]
[    0.660820] pnp 00:08: [io  0x040b]
[    0.660821] pnp 00:08: [io  0x04d6]
[    0.660822] pnp 00:08: [io  0x0c00-0x0c01]
[    0.660823] pnp 00:08: [io  0x0c14]
[    0.660824] pnp 00:08: [io  0x0c50-0x0c51]
[    0.660825] pnp 00:08: [io  0x0c52]
[    0.660827] pnp 00:08: [io  0x0c6c]
[    0.660829] pnp 00:08: [io  0x0c6f]
[    0.660830] pnp 00:08: [io  0x0cd0-0x0cd1]
[    0.660831] pnp 00:08: [io  0x0cd2-0x0cd3]
[    0.660833] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.660834] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.660835] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.660836] pnp 00:08: [io  0x0b00-0x0b3f]
[    0.660837] pnp 00:08: [io  0x0800-0x089f]
[    0.660839] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.660840] pnp 00:08: [io  0x0b00-0x0b1f]
[    0.660841] pnp 00:08: [io  0x0b20-0x0b3f]
[    0.660842] pnp 00:08: [io  0x0900-0x090f]
[    0.660844] pnp 00:08: [io  0x0910-0x091f]
[    0.660845] pnp 00:08: [io  0xfe00-0xfefe]
[    0.660846] pnp 00:08: [io  0x0060]
[    0.660847] pnp 00:08: [io  0x0064]
[    0.660848] pnp 00:08: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.660850] pnp 00:08: [mem 0xffb80000-0xffbfffff]
[    0.660851] pnp 00:08: [mem 0xfec10000-0xfec1001f]
[    0.660853] pnp 00:08: [mem 0xfed40000-0xfed44fff]
[    0.660854] pnp 00:08: [mem 0xfed80000-0xfed80fff]
[    0.660855] pnp 00:08: [mem 0x00000000-0xffffffffffffffff disabled]
[    0.660904] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.660906] system 00:08: [io  0x040b] has been reserved
[    0.660908] system 00:08: [io  0x04d6] has been reserved
[    0.660909] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.660911] system 00:08: [io  0x0c14] has been reserved
[    0.660913] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.660914] system 00:08: [io  0x0c52] has been reserved
[    0.660916] system 00:08: [io  0x0c6c] has been reserved
[    0.660917] system 00:08: [io  0x0c6f] has been reserved
[    0.660919] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.660921] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.660923] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.660924] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.660926] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.660928] system 00:08: [io  0x0b00-0x0b3f] has been reserved
[    0.660929] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.660931] system 00:08: [io  0x0b00-0x0b1f] has been reserved
[    0.660933] system 00:08: [io  0x0b20-0x0b3f] has been reserved
[    0.660935] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.660937] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.660938] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.660941] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.660943] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.660945] system 00:08: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.660947] system 00:08: [mem 0xfed80000-0xfed80fff] has been reserved
[    0.660949] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.661044] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
[    0.661046] pnp 00:09: [io  0x0230-0x023f]
[    0.661047] pnp 00:09: [io  0x0290-0x029f]
[    0.661048] pnp 00:09: [io  0x0300-0x030f]
[    0.661049] pnp 00:09: [io  0x0a30-0x0a3f]
[    0.661075] system 00:09: [io  0x0230-0x023f] has been reserved
[    0.661077] system 00:09: [io  0x0290-0x029f] has been reserved
[    0.661078] system 00:09: [io  0x0300-0x030f] has been reserved
[    0.661080] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.661082] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.661108] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    0.661134] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.661137] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.661202] pnp 00:0b: [mem 0x00000000-0x0009ffff]
[    0.661204] pnp 00:0b: [mem 0x000c0000-0x000cffff]
[    0.661205] pnp 00:0b: [mem 0x000e0000-0x000fffff]
[    0.661207] pnp 00:0b: [mem 0x00100000-0xcfffffff]
[    0.661208] pnp 00:0b: [mem 0xfec00000-0xffffffff]
[    0.661234] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.661236] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.661238] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.661240] system 00:0b: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.661242] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.661244] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.661301] pnp: PnP ACPI: found 12 devices
[    0.661302] ACPI: ACPI bus type pnp unregistered
[    0.666614] PCI: max bus depth: 1 pci_try_num: 2
[    0.666626] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.666628] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.666630] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
[    0.666632] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.666635] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.666636] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.666638] pci 0000:00:05.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.666640] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.666643] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.666644] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.666647] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.666650] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.666666] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.666668] pci 0000:00:05.0: setting latency timer to 64
[    0.666673] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.666675] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.666676] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.666678] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.666679] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.666681] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.666682] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.666684] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
[    0.666685] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.666687] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.666688] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.666690] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.666691] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.666692] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.666694] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.666695] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.666719] NET: Registered protocol family 2
[    0.666822] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.667640] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.669570] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.669804] TCP: Hash tables configured (established 524288 bind 65536)
[    0.669806] TCP reno registered
[    0.669813] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.669838] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.669931] NET: Registered protocol family 1
[    0.669939] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    1.504108] pci 0000:01:05.0: Boot video device
[    1.504130] PCI: CLS 64 bytes, default 64
[    1.505152] PCI-DMA: Disabling AGP.
[    1.505223] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    1.505224] PCI-DMA: using GART IOMMU.
[    1.505227] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.508279] audit: initializing netlink socket (disabled)
[    1.508293] type=2000 audit(1348795171.504:1): initialized
[    1.528160] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.542651] VFS: Disk quotas dquot_6.5.2
[    1.542691] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.543110] fuse init (API version 7.16)
[    1.543162] msgmni has been set to 7414
[    1.543509] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.543538] io scheduler noop registered
[    1.543539] io scheduler deadline registered
[    1.543563] io scheduler cfq registered (default)
[    1.543719] pcieport 0000:00:05.0: setting latency timer to 64
[    1.543746] pcieport 0000:00:05.0: irq 40 for MSI/MSI-X
[    1.543824] pcieport 0000:00:05.0: Signaling PME through PCIe PME interrupt
[    1.543825] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.543828] pcie_pme 0000:00:05.0:pcie01: service driver pcie_pme loaded
[    1.543837] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.543851] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.543925] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.543928] ACPI: Power Button [PWRB]
[    1.543954] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.543956] ACPI: Power Button [PWRF]
[    1.543970] ACPI: acpi_idle registered with cpuidle
[    1.543996] ACPI: processor limited to max C-state 1
[    1.736926] ERST: Table is not found!
[    1.736967] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.748966] Linux agpgart interface v0.103
[    1.749553] brd: module loaded
[    1.749822] loop: module loaded
[    1.749989] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.750010] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.750216] Fixed MDIO Bus: probed
[    1.750229] PPP generic driver version 2.4.2
[    1.750253] tun: Universal TUN/TAP device driver, 1.6
[    1.750254] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.750298] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.750337] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.750357] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.750395] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.750401] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.750414] QUIRK: Enable AMD PLL fix
[    1.750422] ehci_hcd 0000:00:12.2: debug port 1
[    1.750438] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
[    1.760065] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.760143] hub 1-0:1.0: USB hub found
[    1.760146] hub 1-0:1.0: 5 ports detected
[    1.760256] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.760266] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.760294] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.760299] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.760314] ehci_hcd 0000:00:13.2: debug port 1
[    1.760324] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe8ff400
[    1.772062] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.772133] hub 2-0:1.0: USB hub found
[    1.772135] hub 2-0:1.0: 5 ports detected
[    1.772244] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.772255] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.772278] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.772284] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.772299] ehci_hcd 0000:00:16.2: debug port 1
[    1.772308] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe8ff000
[    1.784063] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.784135] hub 3-0:1.0: USB hub found
[    1.784137] hub 3-0:1.0: 4 ports detected
[    1.784192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.784261] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.784271] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.784292] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.784310] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe8fe000
[    1.844103] hub 4-0:1.0: USB hub found
[    1.844108] hub 4-0:1.0: 5 ports detected
[    1.844232] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.844244] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.844266] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.844278] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fd000
[    1.904104] hub 5-0:1.0: USB hub found
[    1.904109] hub 5-0:1.0: 5 ports detected
[    1.904233] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.904243] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.904263] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.904275] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fc000
[    1.964107] hub 6-0:1.0: USB hub found
[    1.964112] hub 6-0:1.0: 2 ports detected
[    1.964226] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.964236] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.964257] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.964269] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe8f7000
[    2.024105] hub 7-0:1.0: USB hub found
[    2.024109] hub 7-0:1.0: 4 ports detected
[    2.024172] uhci_hcd: USB Universal Host Controller Interface driver
[    2.024214] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    2.024559] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.024565] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.024652] mousedev: PS/2 mouse device common for all mice
[    2.024718] rtc_cmos 00:03: RTC can wake from S4
[    2.024778] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.024795] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.024865] device-mapper: uevent: version 1.0.3
[    2.024905] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    2.024910] cpuidle: using governor ladder
[    2.024911] cpuidle: using governor menu
[    2.024912] EFI Variables Facility v0.08 2004-May-17
[    2.025049] TCP cubic registered
[    2.025119] NET: Registered protocol family 10
[    2.025406] NET: Registered protocol family 17
[    2.025416] Registering the dns_resolver key type
[    2.025473] PM: Hibernation image not present or could not be loaded.
[    2.025480] registered taskstats version 1
[    2.036533]   Magic number: 12:496:307
[    2.036561] tty tty36: hash matches
[    2.036610] rtc_cmos 00:03: setting system clock to 2012-09-28 01:19:33 UTC (1348795173)
[    2.036623] powernow-k8: Found 1 AMD Phenom(tm) II X4 965 Processor (4 cpu cores) (version 2.20.00)
[    2.036647] powernow-k8:    0 : pstate 0 (3400 MHz)
[    2.036648] powernow-k8:    1 : pstate 1 (2700 MHz)
[    2.036649] powernow-k8:    2 : pstate 2 (2200 MHz)
[    2.036650] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.037069] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.037071] EDD information not available.
[    2.038174] Freeing unused kernel memory: 984k freed
[    2.038343] Write protecting the kernel read-only data: 10240k
[    2.038509] Freeing unused kernel memory: 20k freed
[    2.041728] Freeing unused kernel memory: 1400k freed
[    2.052636] udevd[121]: starting version 173
[    2.072043] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.075206] ahci 0000:00:11.0: version 3.0
[    2.075229] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.075322] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    2.075324] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.077266] scsi0 : ahci
[    2.077776] scsi1 : ahci
[    2.077957] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.077976] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    2.077979] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.078013] scsi2 : ahci
[    2.078073] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    2.078146] scsi3 : ahci
[    2.078212] ata1: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 19
[    2.078215] ata2: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 19
[    2.078217] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 19
[    2.078220] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 19
[    2.078281] xhci_hcd 0000:02:00.0: irq 17, io mem 0xfebfe000
[    2.078325] xhci_hcd 0000:02:00.0: irq 41 for MSI/MSI-X
[    2.078330] xhci_hcd 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.078333] xhci_hcd 0000:02:00.0: irq 43 for MSI/MSI-X
[    2.078337] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    2.078340] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    2.078463] xHCI xhci_add_endpoint called for root hub
[    2.078465] xHCI xhci_check_bandwidth called for root hub
[    2.078483] hub 8-0:1.0: USB hub found
[    2.078488] hub 8-0:1.0: 2 ports detected
[    2.078550] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.078573] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.081589] xHCI xhci_add_endpoint called for root hub
[    2.081590] xHCI xhci_check_bandwidth called for root hub
[    2.081606] hub 9-0:1.0: USB hub found
[    2.081610] hub 9-0:1.0: 2 ports detected
[    2.081859] scsi4 : pata_atiixp
[    2.081929] scsi5 : pata_atiixp
[    2.081992] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.081994] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.209338] hub 1-1:1.0: USB hub found
[    2.209405] hub 1-1:1.0: 3 ports detected
[    2.320066] usb 1-2: new high speed USB device number 3 using ehci_hcd
[    2.396103] ata3: SATA link down (SStatus 0 SControl 300)
[    2.400077] ata4: SATA link down (SStatus 0 SControl 300)
[    2.504057] Refined TSC clocksource calibration: 3415.139 MHz.
[    2.504066] Switching to clocksource tsc
[    2.568052] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.568074] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.569712] ata2.00: ATAPI: Optiarc DVD RW AD-5260S, 1.00, max UDMA/100
[    2.569901] ata1.00: ATA-8: WDC WD5002AALX-00J37A0, 15.01H15, max UDMA/133
[    2.569903] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.571042] ata1.00: configured for UDMA/133
[    2.571180] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5002AALX-0 15.0 PQ: 0 ANSI: 5
[    2.571291] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.571308] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.571400] sd 0:0:0:0: [sda] Write Protect is off
[    2.571403] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.571426] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.571719] ata2.00: configured for UDMA/100
[    2.573676] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-5260S  1.00 PQ: 0 ANSI: 5
[    2.575817] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.575820] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.575894] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.575932] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.585747]  sda: sda1 sda2 sda3 sda4
[    2.586000] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.929503] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[    2.968032] usb 5-1: new low speed USB device number 2 using ohci_hcd
[    3.216674] usb 1-1.1: new high speed USB device number 5 using ehci_hcd
[    3.317173] hub 1-1.1:1.0: USB hub found
[    3.317280] hub 1-1.1:1.0: 3 ports detected
[    3.580041] usb 4-5: new low speed USB device number 2 using ohci_hcd
[    3.840634] usb 1-1.1.1: new high speed USB device number 6 using ehci_hcd
[    9.696067] udevd[399]: starting version 173
[    9.721659] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.723444] MCE: In-kernel MCE decoding enabled.
[    9.725536] lp: driver loaded but no devices found
[    9.728936] EDAC MC: Ver: 2.1.0
[    9.735790] AMD64 EDAC driver v3.4.0
[    9.736439] wmi: Mapper loaded
[    9.737223] EDAC amd64: DRAM ECC disabled.
[    9.737229] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    9.737230]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    9.737231]  (Note that use of the override may cause unknown side effects.)
[    9.744112] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    9.744405] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    9.744471] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[    9.747101] [drm] Initialized drm 1.1.0 20060810
[    9.760464] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input2
[    9.760572] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:13.0-1/input0
[    9.771322] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input3
[    9.771719] generic-usb 0003:0603:00F2.0002: input,hiddev0,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:13.0-1/input1
[    9.772021] [drm] radeon defaulting to kernel modesetting.
[    9.772023] [drm] radeon kernel modesetting enabled.
[    9.773989] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.773993] radeon 0000:01:05.0: setting latency timer to 64
[    9.774119] [drm] initializing kernel modesetting (RS880 0x1002:0x9715 0x1043:0x843E).
[    9.774140] [drm] register mmio base: 0xFEAF0000
[    9.774141] [drm] register mmio size: 65536
[    9.774732] ATOM BIOS: 113
[    9.774749] radeon 0000:01:05.0: VRAM: 368M 0x00000000C0000000 - 0x00000000D6FFFFFF (368M used)
[    9.774751] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
[    9.776986] [drm] Detected VRAM RAM=368M, BAR=256M
[    9.776989] [drm] RAM width 32bits DDR
[    9.778394] [TTM] Zone  kernel: Available graphics memory: 1899268 kiB.
[    9.778396] [TTM] Initializing pool allocator.
[    9.778412] [drm] radeon: 368M of VRAM memory ready
[    9.778414] [drm] radeon: 512M of GTT memory ready.
[    9.778428] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.778429] [drm] Driver supports precise vblank timestamp query.
[    9.778446] [drm] radeon: irq initialized.
[    9.778450] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    9.778578] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb4/4-5/4-5:1.0/input/input4
[    9.778662] generic-usb 0003:046D:C05A.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:12.0-5/input0
[    9.778680] usbcore: registered new interface driver usbhid
[    9.778681] usbhid: USB HID core driver
[    9.779073] [drm] Loading RS780 Microcode
[    9.786928] type=1400 audit(1348787981.245:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=629 comm="apparmor_parser"
[    9.787237] type=1400 audit(1348787981.245:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=629 comm="apparmor_parser"
[    9.787431] type=1400 audit(1348787981.245:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=629 comm="apparmor_parser"
[    9.804690] usbcore: registered new interface driver uas
[    9.805229] Initializing USB Mass Storage driver...
[    9.810628] cfg80211: Calling CRDA to update world regulatory domain
[    9.810847] scsi6 : usb-storage 1-1.1.1:1.0
[    9.812396] usbcore: registered new interface driver usb-storage
[    9.812398] USB Mass Storage support registered.
[    9.827810] cfg80211: World regulatory domain updated:
[    9.827812] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.827814] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.827816] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.827818] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.827819] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.827820] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.832828] radeon 0000:01:05.0: WB enabled
[    9.864645] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.864696] [drm] ring test succeeded in 1 usecs
[    9.864777] [drm] radeon: ib pool ready.
[    9.864826] [drm] ib test succeeded in 0 usecs
[    9.865030] [drm] Radeon Display Connectors
[    9.865032] [drm] Connector 0:
[    9.865033] [drm]   VGA
[    9.865034] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    9.865036] [drm]   Encoders:
[    9.865037] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    9.865038] [drm] Connector 1:
[    9.865039] [drm]   DVI-D
[    9.865039] [drm]   HPD1
[    9.865041] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    9.865042] [drm]   Encoders:
[    9.865043] [drm]     DFP3: INTERNAL_KLDSCP_LVTMA
[    9.874584] [drm] Radeon display connector VGA-1: No monitor connected or invalid EDID
[    9.918120] hda_codec: ALC892: BIOS auto-probing.
[    9.926048] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    9.938352] [drm] Radeon display connector DVI-D-1: Found valid EDID
[    9.938375] [drm] radeon: power management initialized
[   10.032949] [drm] fb mappable at 0xD0141000
[   10.032952] [drm] vram apper at 0xD0000000
[   10.032953] [drm] size 9216000
[   10.032954] [drm] fb depth is 24
[   10.032954] [drm]    pitch is 7680
[   10.033009] fbcon: radeondrmfb (fb0) is primary device
[   10.033125] Console: switching to colour frame buffer device 240x75
[   10.033153] fb0: radeondrmfb frame buffer device
[   10.033154] drm: registered panic notifier
[   10.033159] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
[   10.076438] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.076440] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076442] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.076444] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076445] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.076447] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076448] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.076449] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076451] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.076452] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076453] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.076455] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076456] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.076457] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076459] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.076460] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076461] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.076463] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076464] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.076466] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076467] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.076468] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076469] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.076471] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076472] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.076474] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.076475] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.076476] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   10.078062] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.078390] Registered led device: rt73usb-phy0::radio
[   10.078402] Registered led device: rt73usb-phy0::assoc
[   10.078415] Registered led device: rt73usb-phy0::quality
[   10.079441] usbcore: registered new interface driver rt73usb
[   10.147643] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[   10.646443] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.677972] type=1400 audit(1348787982.137:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=893 comm="apparmor_parser"
[   10.678173] type=1400 audit(1348787982.137:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=894 comm="apparmor_parser"
[   10.678536] type=1400 audit(1348787982.137:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=894 comm="apparmor_parser"
[   10.678735] type=1400 audit(1348787982.137:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=894 comm="apparmor_parser"
[   10.679817] type=1400 audit(1348787982.137:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=897 comm="apparmor_parser"
[   10.680041] type=1400 audit(1348787982.141:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=898 comm="apparmor_parser"
[   10.680212] type=1400 audit(1348787982.141:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=897 comm="apparmor_parser"
[   10.733200] init: failsafe main process (836) killed by TERM signal
[   10.734559] init: apport pre-start process (930) terminated with status 1
[   10.742302] init: apport post-stop process (960) terminated with status 1
[   10.823355] scsi 6:0:0:0: Direct-Access     Generic  Ultra HS-SD/MMC  1.82 PQ: 0 ANSI: 0
[   10.868583] Bluetooth: Core ver 2.16
[   10.868612] NET: Registered protocol family 31
[   10.868614] Bluetooth: HCI device and connection manager initialized
[   10.868616] Bluetooth: HCI socket layer initialized
[   10.868617] Bluetooth: L2CAP socket layer initialized
[   10.868778] Bluetooth: SCO socket layer initialized
[   10.869920] Bluetooth: RFCOMM TTY layer initialized
[   10.869923] Bluetooth: RFCOMM socket layer initialized
[   10.869924] Bluetooth: RFCOMM ver 1.11
[   10.870141] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.870142] Bluetooth: BNEP filters: protocol multicast
[   11.036225] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   11.052317] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   11.605530] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[   11.797496] init: plymouth-stop pre-start process (1242) terminated with status 1
[   12.113671] ppdev: user-space parallel port driver
[   12.117136] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[   13.973978] wlan0: direct probe to e8:40:f2:50:94:98 (try 1/3)
[   14.172045] wlan0: direct probe to e8:40:f2:50:94:98 (try 2/3)
[   14.372041] wlan0: direct probe to e8:40:f2:50:94:98 (try 3/3)
[   14.572042] wlan0: direct probe to e8:40:f2:50:94:98 timed out
[   33.374083] wlan0: direct probe to e8:40:f2:50:94:98 (try 1/3)
[   33.572052] wlan0: direct probe to e8:40:f2:50:94:98 (try 2/3)
[   33.772053] wlan0: direct probe to e8:40:f2:50:94:98 (try 3/3)
[   33.972053] wlan0: direct probe to e8:40:f2:50:94:98 timed out
[   52.757938] wlan0: direct probe to e8:40:f2:50:94:98 (try 1/3)
[   52.956054] wlan0: direct probe to e8:40:f2:50:94:98 (try 2/3)
[   53.156067] wlan0: direct probe to e8:40:f2:50:94:98 (try 3/3)
[   53.356058] wlan0: direct probe to e8:40:f2:50:94:98 timed out
[   59.680048] wlan0: authenticate with 00:1d:0f:e4:c3:b0 (try 1)
[   59.880051] wlan0: authenticate with 00:1d:0f:e4:c3:b0 (try 2)
[   59.901195] wlan0: authenticated
[   59.946892] wlan0: associate with 00:1d:0f:e4:c3:b0 (try 1)
[   59.955435] wlan0: RX AssocResp from 00:1d:0f:e4:c3:b0 (capab=0x421 status=0 aid=7)
[   59.955437] wlan0: associated
[   59.967707] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.967756] cfg80211: Calling CRDA for country: HU
[   59.969971] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   59.969974] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969976] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   59.969977] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969979] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   59.969980] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969981] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   59.969983] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969984] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   59.969986] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969987] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   59.969988] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969990] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   59.969991] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969992] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   59.969994] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969995] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   59.969996] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.969998] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   59.969999] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.970000] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   59.970002] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.970003] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   59.970005] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.970006] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   59.970007] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   59.970008] cfg80211: Disabling freq 2484 MHz
[   59.970010] cfg80211: Regulatory domain changed to country: HU
[   59.970011] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   59.970013] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   59.970014] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   59.970016] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   59.970017] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   70.704052] wlan0: no IPv6 routers present
[   80.215663] wlan0: deauthenticating from 00:1d:0f:e4:c3:b0 by local choice (reason=3)
[   80.230099] cfg80211: All devices are disconnected, going to restore regulatory settings
[   80.230110] cfg80211: Restoring regulatory settings
[   80.230120] cfg80211: Calling CRDA to update world regulatory domain
[   80.236969] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   80.236980] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.236987] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   80.236995] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237000] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   80.237007] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237012] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   80.237018] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237023] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   80.237030] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237035] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   80.237041] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237047] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   80.237053] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237058] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   80.237064] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237070] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   80.237076] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237081] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   80.237088] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237093] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   80.237099] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237104] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   80.237111] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237116] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   80.237122] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237128] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   80.237134] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   80.237141] cfg80211: World regulatory domain updated:
[   80.237145] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   80.237152] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   80.237158] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   80.237164] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   80.237170] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   80.237176] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   84.302094] wlan0: authenticate with 00:1d:0f:e4:c3:b0 (try 1)
[   84.311544] wlan0: authenticated
[   84.331081] wlan0: associate with 00:1d:0f:e4:c3:b0 (try 1)
[   84.528087] wlan0: associate with 00:1d:0f:e4:c3:b0 (try 2)
[   84.541010] wlan0: RX ReassocResp from 00:1d:0f:e4:c3:b0 (capab=0x421 status=0 aid=8)
[   84.541019] wlan0: associated
[   84.554590] cfg80211: Calling CRDA for country: HU
[   84.561498] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   84.561508] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561515] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   84.561522] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561528] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   84.561534] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561539] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   84.561546] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561551] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   84.561557] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561562] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   84.561569] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561574] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   84.561580] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561586] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   84.561592] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561597] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   84.561604] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561609] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   84.561615] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561620] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   84.561627] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561632] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   84.561638] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561643] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   84.561650] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   84.561655] cfg80211: Disabling freq 2484 MHz
[   84.561662] cfg80211: Regulatory domain changed to country: HU
[   84.561666] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   84.561672] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   84.561678] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   84.561684] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   84.561690] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   88.490501] wlan0: deauthenticating from 00:1d:0f:e4:c3:b0 by local choice (reason=3)
[   88.578128] cfg80211: All devices are disconnected, going to restore regulatory settings
[   88.578136] cfg80211: Restoring regulatory settings
[   88.578147] cfg80211: Calling CRDA to update world regulatory domain
[   88.585118] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   88.585128] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585135] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   88.585143] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585148] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   88.585154] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585160] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   88.585166] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585171] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   88.585178] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585183] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   88.585189] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585194] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   88.585201] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585206] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   88.585212] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585217] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   88.585223] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585229] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   88.585235] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585240] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   88.585246] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585252] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   88.585258] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585263] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   88.585269] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585275] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   88.585281] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[   88.585288] cfg80211: World regulatory domain updated:
[   88.585292] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   88.585298] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   88.585305] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   88.585311] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   88.585317] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   88.585323] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   95.520068] wlan0: no IPv6 routers present
```lshw:
```
  *-network               
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:23:cd:ba:7d:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.0.0-12-generic firmware=1.7 link=no multicast=yes wireless=IEEE 802.11bg
```Can You help me? Thank You in advance!

---

### Post by Nuc72 on 2012-09-27
Interesting result:
I've put the wifi dongle to another USB port and it works. It's weird, because it worked so far in the 'old' port, and as I wrote it worked under Windows7.

???

---

