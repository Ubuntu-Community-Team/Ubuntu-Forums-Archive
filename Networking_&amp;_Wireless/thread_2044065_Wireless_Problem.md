---
title: "Wireless Problem"
date: 2012-08-18
forum: Networking &amp; Wireless
---

### Post by WishForHelp on 2012-08-18
Hello,

I'm using a Packard Bell Easynote MX 64, and the Wireless isn't working, it keeps asking for a password (over and over again), was looking around here, but can't seem to find any solution... :(

So I hope that any of you can help me, as the Wireless is needed 100%, I never use an Internet Cable. (Unless now! :P)

I'm looking forward to any response!

EDIT: I'm using the Wicd Network Manager at the moment, but it's the same result.
EDIT2: On Windows XP & 7, it was working perfect, but I made a clean install with Ubuntu, no dualboot, and now, when I try to boot from an USB it gives me an error, so i'm stuck with Ubuntu now, It's much faster, but this is the huge problem I have.

---

### Post by bakegoodz on 2012-08-18
Can you get some more details about your system?
```

lspci -nnk | grep -iA2 net
sudo iwlist scan
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'

```

That last command should be copied and pasted if you are able to do that.

Check out this guide for asking wireless questions
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by WishForHelp on 2012-08-19
> **bakegoodz said:**
> Can you get some more details about your system?
```

lspci -nnk | grep -iA2 net
sudo iwlist scan
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'

```That last command should be copied and pasted if you are able to do that.

Check out this guide for asking wireless questions
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

Good morning,

Third command, which was asked for:

```
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
[   24.611341] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   24.611346] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   24.611429] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.611446] iwl3945 0000:03:00.0: setting latency timer to 64
[   25.384519] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   25.384526] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   25.384694] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[   25.390155] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.792967] type=1400 audit(1345375066.395:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=848 comm="apparmor_parser"
[   25.992984] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   26.067513] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.067877] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.235731] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   57.432048] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   57.632048] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   57.832046] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   59.612054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   59.612066] iwl3945 0000:03:00.0: On demand firmware reload
[   66.442440] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   66.640081] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   66.840080] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   67.044061] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   68.680033] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   68.680040] iwl3945 0000:03:00.0: On demand firmware reload
[   75.638472] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   75.836111] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   76.036071] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   76.236069] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   77.748040] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   77.748046] iwl3945 0000:03:00.0: On demand firmware reload
[   84.830346] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   85.028052] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   85.228083] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   85.432160] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   87.316043] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   87.316055] iwl3945 0000:03:00.0: On demand firmware reload
[  102.591443] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  102.788058] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  102.988065] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  103.188056] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  104.384050] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  104.384062] iwl3945 0000:03:00.0: On demand firmware reload
[  104.388468] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[  111.774349] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  111.972078] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  112.172092] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  112.372058] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  113.456034] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  113.456046] iwl3945 0000:03:00.0: On demand firmware reload
[  421.655198] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  421.852091] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  422.052080] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  422.252082] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  424.028032] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  424.028039] iwl3945 0000:03:00.0: On demand firmware reload
[  430.837046] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  431.036300] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  431.236067] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  431.436085] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  433.092051] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  433.092059] iwl3945 0000:03:00.0: On demand firmware reload
[  440.034668] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  440.232097] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  440.432104] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  440.632083] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  442.160075] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  442.160086] iwl3945 0000:03:00.0: On demand firmware reload
[  449.219515] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  449.416083] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  449.616057] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  449.816051] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  450.728032] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  450.728039] iwl3945 0000:03:00.0: On demand firmware reload
```

EDIT: I'll make "a guide wireless issue post",  excuse me :D

---

### Post by WishForHelp on 2012-08-19
1 ) Machine Brand and Model (PC/Laptop):

Packard Bell Easynote MX65

2 ) Wireless Brand, Model and Wireless Chipset:

 ```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5602 ALi Corp. M5602 Video Camera Controller
```

Use grep to get only information about the Wireless:

How to do this?

3 ) check interface:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:e6:9a:62 
          inet addr:84.198.56.238  Bcast:84.198.63.255  Mask:255.255.240.0
          inet6 addr: fe80::218:f3ff:fee6:9a62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5145 errors:1 dropped:1 overruns:1 frame:0
          TX packets:4144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4800829 (4.8 MB)  TX bytes:653158 (653.1 KB)
          Interrupt:16 Base address:0xd800
```

```
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35977 (35.9 KB)  TX bytes:35977 (35.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d3:e2:da 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```



```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
eth0      no wireless extensions.


If the Wireless interface name is wlan0 you can also use:

iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

4 ) Check for modules:

```
lsmod
Module                  Size  Used by
vesafb                 13516  1
snd_hda_codec_si3054    12864  1
snd_hda_codec_analog    75395  1
rfcomm                 38139  0
parport_pc             32114  0
bnep                   17830  2
ppdev                  12849  0
bluetooth             158438  10 rfcomm,bnep
joydev                 17393  0
arc4                   12473  2
gspca_m5602            51493  0
gspca_main             27654  1 gspca_m5602
videodev               86588  1 gspca_main
snd_hda_intel          32765  5
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
nvidia              10971098  32
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19068  0
psmouse                72919  0
r852                   17901  0
r592                   17808  0
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
serio_raw              13027  0
memstick               15857  1 r592
iwl3945                73152  0
iwl_legacy             71134  1 iwl3945
snd                    62064  18 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              436455  2 iwl3945,iwl_legacy
asus_laptop            23693  0
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
mac_hid                13077  0
cfg80211              178679  3 iwl3945,iwl_legacy,mac80211
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0
8139too                23283  0
8139cp                 26759  0
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0
sdhci                  28241  1 sdhci_pci
```

Search for the Wireless module:

How to do this?

---

### Post by WishForHelp on 2012-08-19
5 ) Kernel boot messages:

```
[    0.393437] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.394589] ACPI: Lid Switch [LID]
[    0.394666] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.394674] ACPI: Power Button [PWRB]
[    0.394746] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.394752] ACPI: Sleep Button [SLPB]
[    0.394826] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.394831] ACPI: Power Button [PWRF]
[    0.398352] Marking TSC unstable due to TSC halts in idle
[    0.398361] ACPI: acpi_idle registered with cpuidle
[    0.427247] thermal LNXTHERM:00: registered as thermal_zone0
[    0.427252] ACPI: Thermal Zone [THRM] (34 C)
[    0.427300] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.427321] ACPI: Battery Slot [BAT0] (battery present)
[    0.427415] ERST: Table is not found!
[    0.427418] GHES: HEST is not enabled!
[    0.427570] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.436213] isapnp: Scanning for PnP cards...
[    0.489065] ACPI: Battery Slot [BAT0] (battery present)
[    0.627498] Freeing initrd memory: 13820k freed
[    0.790317] isapnp: No Plug & Play device found
[    0.844565] Linux agpgart interface v0.103
[    0.847727] brd: module loaded
[    0.849212] loop: module loaded
[    0.849514] ata_piix 0000:00:1f.1: version 2.13
[    0.849535] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.849598] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.850167] scsi0 : ata_piix
[    0.850319] scsi1 : ata_piix
[    0.852060] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.852065] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.852131] ata2: port disabled--ignoring
[    0.852737] Fixed MDIO Bus: probed
[    0.852772] tun: Universal TUN/TAP device driver, 1.6
[    0.852776] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.852883] PPP generic driver version 2.4.2
[    0.853070] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.853103] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.853131] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.853136] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.853221] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.853251] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.853266] ehci_hcd 0000:00:1d.7: debug port 1
[    0.857159] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.857187] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebfbc00
[    0.872026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.872256] hub 1-0:1.0: USB hub found
[    0.872263] hub 1-0:1.0: 8 ports detected
[    0.872408] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.872436] uhci_hcd: USB Universal Host Controller Interface driver
[    0.872463] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.872475] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.872480] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.872559] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.872591] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ec00
[    0.872805] hub 2-0:1.0: USB hub found
[    0.872812] hub 2-0:1.0: 2 ports detected
[    0.872924] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.872935] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.872940] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.873019] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.873066] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e880
[    0.873274] hub 3-0:1.0: USB hub found
[    0.873280] hub 3-0:1.0: 2 ports detected
[    0.873394] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.873405] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.873411] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.873488] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.873535] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[    0.873749] hub 4-0:1.0: USB hub found
[    0.873755] hub 4-0:1.0: 2 ports detected
[    0.873867] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    0.873877] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.873883] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.873962] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.874008] uhci_hcd 0000:00:1d.3: irq 22, io base 0x0000e480
[    0.874233] hub 5-0:1.0: USB hub found
[    0.874239] hub 5-0:1.0: 2 ports detected
[    0.874440] usbcore: registered new interface driver libusual
[    0.874524] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.876431] i8042: Detected active multiplexing controller, rev 1.1
[    0.877315] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.877324] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.877374] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.877423] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.877468] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.877700] mousedev: PS/2 mouse device common for all mice
[    0.878085] rtc_cmos 00:03: RTC can wake from S4
[    0.878269] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.878306] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.878400] device-mapper: uevent: version 1.0.3
[    0.878528] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.878584] EISA: Probing bus 0 at eisa.0
[    0.878593] Cannot allocate resource for EISA slot 1
[    0.878596] Cannot allocate resource for EISA slot 2
[    0.878599] Cannot allocate resource for EISA slot 3
[    0.878625] EISA: Detected 0 cards.
[    0.878641] cpufreq-nforce2: No nForce2 chipset.
[    0.878724] cpuidle: using governor ladder
[    0.878853] cpuidle: using governor menu
[    0.878857] EFI Variables Facility v0.08 2004-May-17
[    0.879317] TCP cubic registered
[    0.879520] NET: Registered protocol family 10
[    0.880539] NET: Registered protocol family 17
[    0.880546] Registering the dns_resolver key type
[    0.880578] Using IPI No-Shortcut mode
[    0.880806] PM: Hibernation image not present or could not be loaded.
[    0.880825] registered taskstats version 1
[    0.893782]   Magic number: 8:325:277
[    0.893837] tty tty14: hash matches
[    0.893929] rtc_cmos 00:03: setting system clock to 2012-08-19 11:17:21 UTC (1345375041)
[    0.894986] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.894989] EDD information not available.
[    0.910704] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.080685] ata1.00: ATA-6: ST980811A, 3.ALA, max UDMA/100
[    1.080694] ata1.00: 156301488 sectors, multi 16: LBA48
[    1.080711] ata1.01: ATAPI: MATSHITAUJ-850D, 1.00, max UDMA/33
[    1.096609] ata1.00: configured for UDMA/100
[    1.112477] ata1.01: configured for UDMA/33
[    1.115309] scsi 0:0:0:0: Direct-Access     ATA      ST980811A        3.AL PQ: 0 ANSI: 5
[    1.115644] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.115677] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.115736] sd 0:0:0:0: [sda] Write Protect is off
[    1.115741] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.115781] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.117772] scsi 0:0:1:0: CD-ROM            MATSHITA UJ-850D          1.00 PQ: 0 ANSI: 5
[    1.136603] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.136611] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.136929] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.137051] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.160627]  sda: sda1 sda2 < sda5 >
[    1.161642] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.161777] Freeing unused kernel memory: 740k freed
[    1.162235] Write protecting the kernel text: 5816k
[    1.162271] Write protecting the kernel read-only data: 2376k
[    1.162274] NX-protecting the kernel data: 4424k
[    1.184831] udevd[89]: starting version 175
[    1.188073] usb 1-8: new high-speed USB device number 2 using ehci_hcd
[    1.297653] sdhci: Secure Digital Host Controller Interface driver
[    1.297658] sdhci: Copyright(c) Pierre Ossman
[    1.298075] sdhci-pci 0000:06:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.298100] sdhci-pci 0000:06:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.299127] sdhci-pci 0000:06:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.299145] mmc0: no vmmc regulator found
[    1.312582] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.312656] Registered led device: mmc0::
[    1.314698] mmc0: SDHCI controller on PCI [0000:06:01.1] using DMA
[    1.314734] 8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.315924] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.315977] 8139too 0000:06:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.318190] 8139too 0000:06:07.0: eth0: RealTek RTL8139 at 0xd800, 00:18:f3:e6:9a:62, IRQ 16
[    1.318362] firewire_ohci 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.380592] firewire_ohci: Added fw-ohci device 0000:06:01.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x11
[    1.380658] sdhci-pci 0000:06:01.2: SDHCI controller found [1180:0843] (rev 1)
[    1.380699] sdhci-pci 0000:06:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.380761] sdhci-pci 0000:06:01.2: setting latency timer to 64
[    1.380782] mmc1: no vmmc regulator found
[    1.380921] Registered led device: mmc1::
[    1.382054] mmc1: SDHCI controller on PCI [0000:06:01.2] using DMA
[    1.632651] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.880192] firewire_core: created device fw0: GUID 00e018000377beb7, S400
[   24.238933] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.261953] udevd[310]: starting version 175
[   24.336375] lp: driver loaded but no devices found
[   24.345781] Adding 1047548k swap on /dev/sda5.  Priority:-1 extents:1 across:1047548k
[   24.419594] cfg80211: Calling CRDA to update world regulatory domain
[   24.462376] nvidia: module license 'NVIDIA' taints kernel.
[   24.462383] Disabling lock debugging due to kernel taint
[   24.476079] asus_laptop: Asus Laptop Support version 0.42
[   24.476249] asus_laptop:   T12J model detected
[   24.494021] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input5
[   24.587970] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   24.611341] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   24.611346] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   24.611429] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.611446] iwl3945 0000:03:00.0: setting latency timer to 64
[   24.736508] r592 0000:06:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   24.736520] r592 0000:06:01.3: setting latency timer to 64
[   24.784030] type=1400 audit(1345375065.387:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=518 comm="apparmor_parser"
[   24.784687] type=1400 audit(1345375065.387:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=518 comm="apparmor_parser"
[   24.785075] type=1400 audit(1345375065.387:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=518 comm="apparmor_parser"
[   24.989005] r592: driver successfully loaded
[   24.989098] r852 0000:06:01.4: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   24.989110] r852 0000:06:01.4: setting latency timer to 64
[   24.994295] r852: Non dma capable device detected, dma disabled
[   24.994318] r852: driver loaded successfully
[   25.166558] intel_rng: FWH not detected
[   25.174269] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:16/LNXVIDEO:00/input/input6
[   25.174419] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.183667] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.183683] nvidia 0000:01:00.0: setting latency timer to 64
[   25.183691] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   25.190086] NVRM: loading NVIDIA UNIX x86 Kernel Module  295.49  Mon Apr 30 23:30:07 PDT 2012
[   25.192895] leds_ss4200: no LED devices found
[   25.352200] cfg80211: World regulatory domain updated:
[   25.352205] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.352210] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.352214] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.352218] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.352222] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.352226] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.370180] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.370255] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   25.370300] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   25.379675] Linux video capture interface: v2.00
[   25.380890] gspca_main: v2.14.0 registered
[   25.381848] gspca_main: ALi m5602-2.14.0 probing 0402:5602
[   25.384519] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   25.384526] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   25.384694] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[   25.384991] Registered led device: phy0-led
[   25.385078] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   25.390155] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   25.485221] init: failsafe main process (736) killed by TERM signal
[   25.515238] gspca_m5602: Sensor reported 0xffff
[   25.538122] gspca_m5602: Detected a s5k83a sensor
[   25.538723] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x3aa0b4, caps: 0xa04713/0x200000/0x0
[   25.581245] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   25.615090] Bluetooth: Core ver 2.16
[   25.615177] NET: Registered protocol family 31
[   25.615181] Bluetooth: HCI device and connection manager initialized
[   25.615186] Bluetooth: HCI socket layer initialized
[   25.615189] Bluetooth: L2CAP socket layer initialized
[   25.615688] Bluetooth: SCO socket layer initialized
[   25.626575] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.626580] Bluetooth: BNEP filters: protocol multicast
[   25.634269] ppdev: user-space parallel port driver
[   25.639550] usbcore: registered new interface driver ALi m5602
[   25.688103] type=1400 audit(1345375066.291:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=809 comm="apparmor_parser"
[   25.689116] Bluetooth: RFCOMM TTY layer initialized
[   25.689123] Bluetooth: RFCOMM socket layer initialized
[   25.689127] Bluetooth: RFCOMM ver 1.11
[   25.694941] type=1400 audit(1345375066.295:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=809 comm="apparmor_parser"
[   25.743956] type=1400 audit(1345375066.343:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=839 comm="apparmor_parser"
[   25.768428] type=1400 audit(1345375066.371:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=840 comm="apparmor_parser"
[   25.773007] type=1400 audit(1345375066.375:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=840 comm="apparmor_parser"
[   25.773402] type=1400 audit(1345375066.375:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=840 comm="apparmor_parser"
[   25.792967] type=1400 audit(1345375066.395:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=848 comm="apparmor_parser"
[   25.916963] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   25.916968] vesafb: scrolling: redraw
[   25.916973] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   25.918714] vesafb: framebuffer at 0xc0000000, mapped to 0xf8c00000, using 3072k, total 3072k
[   25.918958] Console: switching to colour frame buffer device 128x48
[   25.918999] fb0: VESA VGA frame buffer device
[   25.992984] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   26.067513] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.067877] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.075157] 8139too 0000:06:07.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   36.432048] eth0: no IPv6 routers present
[   57.235731] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   57.432048] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   57.632048] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   57.832046] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   59.612054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   59.612066] iwl3945 0000:03:00.0: On demand firmware reload
[   59.612878] ieee80211 phy0: Hardware restart was requested
[   66.442440] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   66.640081] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   66.840080] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   67.044061] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   68.680033] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   68.680040] iwl3945 0000:03:00.0: On demand firmware reload
[   68.680818] ieee80211 phy0: Hardware restart was requested
[   75.638472] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   75.836111] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   76.036071] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   76.236069] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   77.748040] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   77.748046] iwl3945 0000:03:00.0: On demand firmware reload
[   77.748875] ieee80211 phy0: Hardware restart was requested
[   84.830346] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[   85.028052] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[   85.228083] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[   85.432160] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[   87.316043] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   87.316055] iwl3945 0000:03:00.0: On demand firmware reload
[   87.316986] ieee80211 phy0: Hardware restart was requested
[  102.591443] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  102.788058] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  102.988065] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  103.188056] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  104.384050] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  104.384062] iwl3945 0000:03:00.0: On demand firmware reload
[  104.388468] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[  104.388545] ieee80211 phy0: Hardware restart was requested
[  111.774349] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  111.972078] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  112.172092] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  112.372058] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  113.456034] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  113.456046] iwl3945 0000:03:00.0: On demand firmware reload
[  113.456857] ieee80211 phy0: Hardware restart was requested
[  421.655198] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  421.852091] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  422.052080] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  422.252082] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  424.028032] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  424.028039] iwl3945 0000:03:00.0: On demand firmware reload
[  424.029066] ieee80211 phy0: Hardware restart was requested
[  430.837046] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  431.036300] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  431.236067] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  431.436085] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  433.092051] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  433.092059] iwl3945 0000:03:00.0: On demand firmware reload
[  433.093003] ieee80211 phy0: Hardware restart was requested
[  440.034668] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  440.232097] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  440.432104] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  440.632083] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  442.160075] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  442.160086] iwl3945 0000:03:00.0: On demand firmware reload
[  442.161019] ieee80211 phy0: Hardware restart was requested
[  449.219515] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  449.416083] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  449.616057] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  449.816051] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  450.728032] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  450.728039] iwl3945 0000:03:00.0: On demand firmware reload
[  450.728822] ieee80211 phy0: Hardware restart was requested
[  787.630599] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  787.828061] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  788.028097] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  788.228064] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  789.804050] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  789.804061] iwl3945 0000:03:00.0: On demand firmware reload
[  789.804874] ieee80211 phy0: Hardware restart was requested
[  796.826555] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  797.028119] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  797.228038] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  797.428036] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  798.868060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  798.868071] iwl3945 0000:03:00.0: On demand firmware reload
[  798.869001] ieee80211 phy0: Hardware restart was requested
[  814.617004] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  814.816084] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  815.016089] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  815.216077] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  816.932073] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  816.932084] iwl3945 0000:03:00.0: On demand firmware reload
[  816.932885] ieee80211 phy0: Hardware restart was requested
[  823.798482] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  823.996063] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  824.196587] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  824.396049] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  826.000075] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  826.000086] iwl3945 0000:03:00.0: On demand firmware reload
[  826.004546] iwl3945 0000:03:00.0: Can't stop Rx DMA.
[  826.004665] ieee80211 phy0: Hardware restart was requested
[  832.987033] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  833.184064] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  833.388053] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  833.588068] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  835.068063] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  835.068074] iwl3945 0000:03:00.0: On demand firmware reload
[  835.069005] ieee80211 phy0: Hardware restart was requested
[  842.195999] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[  842.396060] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[  842.596080] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[  842.796063] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[  844.636045] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  844.636051] iwl3945 0000:03:00.0: On demand firmware reload
[  844.636807] ieee80211 phy0: Hardware restart was requested
[ 1151.636349] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1151.836085] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1152.036086] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1152.236104] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1153.720047] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1153.720054] iwl3945 0000:03:00.0: On demand firmware reload
[ 1153.720824] ieee80211 phy0: Hardware restart was requested
[ 1160.824057] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1161.024115] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1161.224134] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1161.424041] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1163.284053] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1163.284064] iwl3945 0000:03:00.0: On demand firmware reload
[ 1163.285022] ieee80211 phy0: Hardware restart was requested
[ 1170.030692] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1170.228092] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1170.428084] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1170.628085] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1172.348063] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1172.348074] iwl3945 0000:03:00.0: On demand firmware reload
[ 1172.348998] ieee80211 phy0: Hardware restart was requested
[ 1179.213858] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1179.412065] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1179.612101] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1179.812076] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1181.412054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1181.412065] iwl3945 0000:03:00.0: On demand firmware reload
[ 1181.412995] ieee80211 phy0: Hardware restart was requested
[ 1188.398816] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1188.596060] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1188.796057] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1188.996083] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1190.476055] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1190.476066] iwl3945 0000:03:00.0: On demand firmware reload
[ 1190.476870] ieee80211 phy0: Hardware restart was requested
[ 1197.608426] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1197.808104] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1198.008089] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1198.208080] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1200.040055] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1200.040067] iwl3945 0000:03:00.0: On demand firmware reload
[ 1200.040999] ieee80211 phy0: Hardware restart was requested
[ 1516.654517] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1516.852091] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1517.052081] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1517.252076] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1519.116043] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1519.116049] iwl3945 0000:03:00.0: On demand firmware reload
[ 1519.116839] ieee80211 phy0: Hardware restart was requested
[ 1525.835744] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1526.032058] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1526.232083] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1526.432071] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1528.180036] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1528.180048] iwl3945 0000:03:00.0: On demand firmware reload
[ 1528.181096] ieee80211 phy0: Hardware restart was requested
[ 1535.042484] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1535.240088] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1535.440092] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1535.640053] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1537.244060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1537.244071] iwl3945 0000:03:00.0: On demand firmware reload
[ 1537.244903] ieee80211 phy0: Hardware restart was requested
[ 1544.227462] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1544.424082] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1544.624095] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1544.824083] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1546.308114] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1546.308122] iwl3945 0000:03:00.0: On demand firmware reload
[ 1546.309108] ieee80211 phy0: Hardware restart was requested
[ 1561.982426] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1562.180065] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1562.380085] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1562.580063] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1564.376062] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1564.376073] iwl3945 0000:03:00.0: On demand firmware reload
[ 1564.377021] ieee80211 phy0: Hardware restart was requested
[ 1571.174638] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 1/3)
[ 1571.372143] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 2/3)
[ 1571.572218] wlan0: direct probe to 00:0c:f6:55:b2:42 (try 3/3)
[ 1571.772066] wlan0: direct probe to 00:0c:f6:55:b2:42 timed out
[ 1573.444054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1573.444060] iwl3945 0000:03:00.0: On demand firmware reload
[ 1573.444841] ieee80211 phy0: Hardware restart was requested
```

---

### Post by WishForHelp on 2012-08-19
6 ) Network configuration:

```
~$ sudo lshw -C network
[sudo] password for frederik:
  *-network              
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:d3:e2:da
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.2.0-29-generic-pae firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:fe1ff000-fe1fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:e6:9a:62
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=84.198.56.238 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:d800(size=256) memory:feafe400-feafe4ff
```

7 ) Scan for networks:

```
~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:84:74:F8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm 
                    Encryption key:on
                    ESSID:"WirelessT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000086301bd8181
                    Extra: Last beacon: 4232ms ago
                    IE: Unknown: 0009576972656C65737354
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1E:58:3E:B0:6E
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm 
                    Encryption key:on
                    ESSID:"Wifi_8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014a90e7019b
                    Extra: Last beacon: 4864ms ago
                    IE: Unknown: 0006576966695F38
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0700E04C01020300
          Cell 03 - Address: 00:24:01:D4:B1:81
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm 
                    Encryption key:on
                    ESSID:"wifi13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002211676519b
                    Extra: Last beacon: 4584ms ago
                    IE: Unknown: 0006776966693133
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030002
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0700E04C01020300
          Cell 04 - Address: 58:6D:8F:63:95:B6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm 
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000033c9ec079fc
                    Extra: Last beacon: 4956ms ago
                    IE: Unknown: 000C000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 58:6D:8F:63:95:B5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm 
                    Encryption key:on
                    ESSID:"GVO-WL2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000033c9ec07186
                    Extra: Last beacon: 4960ms ago
                    IE: Unknown: 000747564F2D574C32
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.
```

8 ) Ubuntu Version:

Description:    Ubuntu 12.04.1 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit):

3.2.0-29-generic-pae i686

10 ) Restarting the network:

```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by WishForHelp on 2012-08-20
Is there anyone who wants to investigate, all those "log-files"? [-o<

---

### Post by steeldriver on 2012-08-20
hi which ssid are you actually trying to connect to? the iwlist scan is showing nothing better than 

```
Cell 01 - Address: 00:1E:E5:84:74:F8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm 
                    Encryption key:eek:n
                    ESSID:"WirelessT"
```which is pretty low - maybe you are just too far from your router to maintain a connection?

---

### Post by WishForHelp on 2012-08-20
> **steeldriver said:**
> hi which ssid are you actually trying to connect to? the iwlist scan is showing nothing better than 

```
Cell 01 - Address: 00:1E:E5:84:74:F8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm 
                    Encryption key:eek:n
                    ESSID:"WirelessT"
```which is pretty low - maybe you are just too far from your router to maintain a connection?

I'm now at a friends house, but at my house I'm sitting near my router. on Windows 7 I can connect to it without problem, even on the highest floor at my house.  But here, on Ubuntu it keeps asking for a password...
I'm with my hand in my hair

---

### Post by steeldriver on 2012-08-20
well we need to eliminate things one at a time - please run the diagnostic commands when you are within range of a known good signal

there are some known issues with Intel wireless drivers in general but I'm not aware of any particular problems for the iwl3945 - but I'm not the wireless guru in these parts

btw what Ubuntu version are you running? I don't see that anywhere

also please use the CODE tags (highlight your text and press the # icon) when you post logs - it makes people much more likely to read them!

---

### Post by WishForHelp on 2012-08-20
> **steeldriver said:**
> well we need to eliminate things one at a time - please run the diagnostic commands when you are within range of a known good signal

there are some known issues with Intel wireless drivers in general but I'm not aware of any particular problems for the iwl3945 - but I'm not the wireless guru in these parts

btw what Ubuntu version are you running? I don't see that anywhere

also please use the CODE tags (highlight your text and press the # icon) when you post logs - it makes people much more likely to read them!

Ok, I'll get back here when the signal is good. ;)
I did the CODE tags, and isn't this the version of Ubuntu?

8 ) Ubuntu Version:

Description:    Ubuntu 12.04.1 LTS

I understand, if this is the version, that u didn't noticed it in the mess I posted. :lolflag:

-----------------------------------------------------------------------------------------------------------------------------------

Okay, we brought another Router to us, and it keeps asking for the Password again....
It's the NETGEAR wifi
```


Cell 03 - Address: 4C:60:DE:33:C2:C2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000170d9184
                    Extra: Last beacon: 2756ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000

eth0      Interface doesn't support scanning.

```

---

### Post by WishForHelp on 2012-08-21
Bump? :-$:p

---

### Post by WishForHelp on 2012-08-23
Can someone please take a look at it?
AND I have a good signal at post #11

---

### Post by bhargo on 2012-08-23
Hi all...I am using dell inspiron mini 1018 version.

I had installed ubantu .I used wireless for a while.now, I cannot connect to wireless .The problem seems to be "wireless disabled by hardware switch". 

Can any one please help me? 
rfkill list  command gave the following result...in case that helps..

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


Thanks in advance

---

### Post by WishForHelp on 2012-08-23
> **bhargo said:**
> Hi all...I am using dell inspiron mini 1018 version.

I had installed ubantu .I used wireless for a while.now, I cannot connect to wireless .The problem seems to be "wireless disabled by hardware switch". 

Can any one please help me? 
rfkill list  command gave the following result...in case that helps..

0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


Thanks in advance

You should make an own thread, and hope u will be helped. ;)
Don't you have a hardware switch to turn wifi on/off on ur laptop?
Anyways, my problem still exists....
Looking on the net for similar issues, but nothing works, guess it's time to go to Windows soon, can't keep working with an ethernet Cable, I need my wifi...

---

### Post by steeldriver on 2012-08-23
I was hoping one of the wireless gurus would step in but since they haven't I've done some poking around

The Intel drivers in general are fussy about 802.11n support among other things (I just had to set 11n_disable=1 to get my Thinkpad with iwl4965 working) however I don't believe the iwl3945 driver has an equivalent parameter - you can check with

```
modinfo iwl3945
```It *does* appear to have params for encryption and scanning so you could play with those - I found a couple of sites suggesting enabling the hw_scan may help (at least for 11.10) i.e.

```
sudo modprobe -rf iwl3945
sudo modprobe iwl3945 disable_hw_scan=0
```

Try it and see - it will revert on reboot so no harm giving it a shot

---

### Post by WishForHelp on 2012-08-24
> **steeldriver said:**
> I was hoping one of the wireless gurus would step in but since they haven't I've done some poking around

The Intel drivers in general are fussy about 802.11n support among other things (I just had to set 11n_disable=1 to get my Thinkpad with iwl4965 working) however I don't believe the iwl3945 driver has an equivalent parameter - you can check with

```
modinfo iwl3945
```It *does* appear to have params for encryption and scanning so you could play with those - I found a couple of sites suggesting enabling the hw_scan may help (at least for 11.10) i.e.

```
sudo modprobe -rf iwl3945
sudo modprobe iwl3945 disable_hw_scan=0
```Try it and see - it will revert on reboot so no harm giving it a shot

Hi,

Thanks for your response, but... it didn't worked, I"m very good with Windows solutions, but don't know anything about Ubuntu...

I think it's a lost case....

Thanks though, and if u have more suggestions, please post. :-(


I found a file in modprobe.d with:

```
 alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```Will this revert on boot also? Because i need to enter hw_scan=0 in terminal u said, but maybe this file/ ubuntu thinks it is more important then the command itself?


--------------

It's irritating that is keeps asking for a password every minute

-------------------

```
 [  655.666385] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  655.666546] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[  655.667112] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  655.690864] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[  666.388075] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  666.388087] iwl3945 0000:03:00.0: On demand firmware reload
[  675.452058] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  675.452069] iwl3945 0000:03:00.0: On demand firmware reload
[  685.016080] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  685.016091] iwl3945 0000:03:00.0: On demand firmware reload
[  694.080060] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  694.080071] iwl3945 0000:03:00.0: On demand firmware reload
[  703.144062] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  703.144073] iwl3945 0000:03:00.0: On demand firmware reload
[  712.208055] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  712.208066] iwl3945 0000:03:00.0: On demand firmware reload
[  721.772026] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[  721.772033] iwl3945 0000:03:00.0: On demand firmware reload
[ 1029.836052] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1029.836063] iwl3945 0000:03:00.0: On demand firmware reload
[ 1038.900054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1038.900066] iwl3945 0000:03:00.0: On demand firmware reload
[ 1048.464068] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1048.464079] iwl3945 0000:03:00.0: On demand firmware reload
[ 1057.528062] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1057.528074] iwl3945 0000:03:00.0: On demand firmware reload
[ 1066.592038] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1066.592046] iwl3945 0000:03:00.0: On demand firmware reload
[ 1076.164046] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1076.164053] iwl3945 0000:03:00.0: On demand firmware reload
[ 1084.740027] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1084.740033] iwl3945 0000:03:00.0: On demand firmware reload
[ 1396.808054] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1396.808065] iwl3945 0000:03:00.0: On demand firmware reload
[ 1406.372075] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1406.372087] iwl3945 0000:03:00.0: On demand firmware reload
[ 1415.436049] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1415.436060] iwl3945 0000:03:00.0: On demand firmware reload
[ 1424.500026] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1424.500033] iwl3945 0000:03:00.0: On demand firmware reload
[ 1433.564034] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1433.564041] iwl3945 0000:03:00.0: On demand firmware reload
[ 1443.128055] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1443.128066] iwl3945 0000:03:00.0: On demand firmware reload
[ 1452.192034] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1452.192040] iwl3945 0000:03:00.0: On demand firmware reload
[ 1762.756066] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1762.756077] iwl3945 0000:03:00.0: On demand firmware reload
[ 1771.820065] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1771.820076] iwl3945 0000:03:00.0: On demand firmware reload
[ 1781.384033] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1781.384040] iwl3945 0000:03:00.0: On demand firmware reload
[ 1790.448066] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1790.448077] iwl3945 0000:03:00.0: On demand firmware reload
[ 1799.512061] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1799.512072] iwl3945 0000:03:00.0: On demand firmware reload
[ 1809.076049] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1809.076055] iwl3945 0000:03:00.0: On demand firmware reload
[ 1818.140039] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[ 1818.140045] iwl3945 0000:03:00.0: On demand firmware reload

```

A stuck queue , and a firmware reload every time, isn't normal, is it?

---

### Post by chili555 on 2012-08-24
> **WishForHelp said:**
> 
A stuck queue , and a firmware reload every time, isn't normal, is it?Nope.

Please try:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 fw_restart=1
```Also, there is an updated iwl3945 driver here; you might try:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```Then reboot and check:```
dmesg | grep iwl
```When you reboot, the firmware restart parameter will go away; reload it and see if it helps.

---

### Post by WishForHelp on 2012-08-24
> **chili555 said:**
> Nope.

Please try:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 fw_restart=1
```Also, there is an updated iwl3945 driver here; you might try:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```Then reboot and check:```
dmesg | grep iwl
```When you reboot, the firmware restart parameter will go away; reload it and see if it helps.

Thanks for the response, I did all the things u said here, but didn't worked, sadly enough.
What about that file in modprobe.d I found, is that causing a problem?

This is the dmesg command:

```
dmesg | grep iwl
[   26.074554] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   26.074559] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   26.074652] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.074669] iwl3945 0000:03:00.0: setting latency timer to 64
[   26.129798] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   26.129804] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.129968] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   26.685666] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.817305] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[  204.404439] iwl3945 0000:03:00.0: PCI INT A disabled
[  204.474076] iwl3945: Unknown symbol il_pm_ops (err 0)
[  204.474100] iwl3945: Unknown symbol il_eeprom_free (err 0)
[  204.474136] iwl3945: Unknown symbol il_rx_queue_alloc (err 0)
[  204.474157] iwl3945: Unknown symbol il_prep_station (err 0)
[  204.474199] iwl3945: Unknown symbol il_poll_bit (err 0)
[  204.474215] iwl3945: Unknown symbol il_mac_bss_info_changed (err 0)
[  204.474231] iwl3945: Unknown symbol il_send_cmd_pdu (err 0)
[  204.474247] iwl3945: Unknown symbol il_alloc_txq_mem (err 0)
[  204.474270] iwl3945: Unknown symbol il_usecs_to_beacons (err 0)
[  204.474287] iwl3945: Unknown symbol ieee80211_free_hw (err -2)
[  204.474303] iwl3945: Unknown symbol il_hdl_spectrum_measurement (err 0)
[  204.474323] iwl3945: Unknown symbol il_setup_scan_deferred_work (err 0)
[  204.474343] iwl3945: Unknown symbol il_scan_cancel (err 0)
[  204.474359] iwl3945: Unknown symbol il_free_channel_map (err 0)
[  204.474375] iwl3945: Unknown symbol il_hdl_csa (err 0)
[  204.474390] iwl3945: Unknown symbol il_bcast_addr (err 0)
[  204.474424] iwl3945: Unknown symbol il_set_bit (err 0)
[  204.474444] iwl3945: Unknown symbol il_read_targ_mem (err 0)
[  204.474464] iwl3945: Unknown symbol il_add_station_common (err 0)
[  204.474485] iwl3945: Unknown symbol il_hdl_pm_debug_stats (err 0)
[  204.474501] iwl3945: Unknown symbol il_tx_cmd_protection (err 0)
[  204.474520] iwl3945: Unknown symbol ieee80211_register_hw (err -2)
[  204.474540] iwl3945: Unknown symbol il_tx_cmd_complete (err 0)
[  204.474556] iwl3945: Unknown symbol il_check_rxon_cmd (err 0)
[  204.474572] iwl3945: Unknown symbol il_irq_handle_error (err 0)
[  204.474588] iwl3945: Unknown symbol il_rx_queue_space (err 0)
[  204.474604] iwl3945: Unknown symbol ieee80211_restart_hw (err -2)
[  204.474622] iwl3945: Unknown symbol ieee80211_rate_control_unregister (err -2)
[  204.474645] iwl3945: Unknown symbol il_setup_watchdog (err 0)
[  204.474660] iwl3945: Unknown symbol ieee80211_wake_queue (err -2)
[  204.474685] iwl3945: Unknown symbol il_apm_stop (err 0)
[  204.474700] iwl3945: Unknown symbol ieee80211_find_sta (err -2)
[  204.474716] iwl3945: Unknown symbol il_add_beacon_time (err 0)
[  204.474732] iwl3945: Unknown symbol il_cmd_queue_free (err 0)
[  204.474747] iwl3945: Unknown symbol il_apm_init (err 0)
[  204.474765] iwl3945: Unknown symbol ieee80211_tx_status_irqsafe (err -2)
[  204.474781] iwl3945: Unknown symbol il_scan_cancel_timeout (err 0)
[  204.474800] iwl3945: Unknown symbol il_leds_exit (err 0)
[  204.474816] iwl3945: Unknown symbol il_isr (err 0)
[  204.474849] iwl3945: Unknown symbol il_restore_stations (err 0)
[  204.474865] iwl3945: Unknown symbol il_mac_add_interface (err 0)
[  204.474892] iwl3945: Unknown symbol il_eeprom_init (err 0)
[  204.474908] iwl3945: Unknown symbol il_queue_space (err 0)
[  204.474926] iwl3945: Unknown symbol il_remove_station (err 0)
[  204.474959] iwl3945: Unknown symbol il_cancel_scan_deferred_work (err 0)
[  204.474975] iwl3945: Unknown symbol il_dealloc_bcast_stations (err 0)
[  204.474990] iwl3945: Unknown symbol il_mac_hw_scan (err 0)
[  204.475011] iwl3945: Unknown symbol il_send_add_sta (err 0)
[  204.475027] iwl3945: Unknown symbol il_setup_rx_scan_handlers (err 0)
[  204.475043] iwl3945: Unknown symbol il_set_decrypted_flag (err 0)
[  204.475058] iwl3945: Unknown symbol il_mac_remove_interface (err 0)
[  204.475077] iwl3945: Unknown symbol il_set_tx_power (err 0)
[  204.475094] iwl3945: Unknown symbol il_mac_sta_remove (err 0)
[  204.475110] iwl3945: Unknown symbol il_leds_init (err 0)
[  204.475132] iwl3945: Unknown symbol _il_poll_bit (err 0)
[  204.475149] iwl3945: Unknown symbol ieee80211_rx (err -2)
[  204.475165] iwl3945: Unknown symbol il_clear_bit (err 0)
[  204.475182] iwl3945: Unknown symbol il_mac_config (err 0)
[  204.475204] iwl3945: Unknown symbol il_txq_mem (err 0)
[  204.475221] iwl3945: Unknown symbol _il_grab_nic_access (err 0)
[  204.475237] iwl3945: Unknown symbol il_rx_queue_update_write_ptr (err 0)
[  204.475251] iwl3945: Unknown symbol ieee80211_wake_queues (err -2)
[  204.475267] iwl3945: Unknown symbol il_full_rxon_required (err 0)
[  204.475281] iwl3945: Unknown symbol ieee80211_rate_control_register (err -2)
[  204.475309] iwl3945: Unknown symbol il_tx_queue_free (err 0)
[  204.475327] iwl3945: Unknown symbol il_mac_tx_last_beacon (err 0)
[  204.475355] iwl3945: Unknown symbol il_send_bt_config (err 0)
[  204.475370] iwl3945: Unknown symbol il_set_rxon_channel (err 0)
[  204.475388] iwl3945: Unknown symbol il_mac_conf_tx (err 0)
[  204.475406] iwl3945: Unknown symbol il_mac_reset_tsf (err 0)
[  204.475421] iwl3945: Unknown symbol il_fill_probe_req (err 0)
[  204.475439] iwl3945: Unknown symbol il_hdl_pm_sleep (err 0)
[  204.475457] iwl3945: Unknown symbol il_get_channel_info (err 0)
[  204.475473] iwl3945: Unknown symbol il_alloc_all (err 0)
[  204.475486] iwl3945: Unknown symbol ieee80211_stop_queue (err -2)
[  204.475501] iwl3945: Unknown symbol il_get_lowest_plcp (err 0)
[  204.475517] iwl3945: Unknown symbol il_tx_queue_init (err 0)
[  204.475530] iwl3945: Unknown symbol ieee80211_stop_queues (err -2)
[  204.475546] iwl3945: Unknown symbol il_send_cmd_sync (err 0)
[  204.475561] iwl3945: Unknown symbol il_connection_init_rx_config (err 0)
[  204.475579] iwl3945: Unknown symbol il_set_rxon_hwcrypto (err 0)
[  204.475599] iwl3945: Unknown symbol il_init_geos (err 0)
[  204.475616] iwl3945: Unknown symbol il_bg_watchdog (err 0)
[  204.475637] iwl3945: Unknown symbol il_get_passive_dwell_time (err 0)
[  204.475653] iwl3945: Unknown symbol rate_control_send_low (err -2)
[  204.475680] iwl3945: Unknown symbol ieee80211_unregister_hw (err -2)
[  204.475698] iwl3945: Unknown symbol il_hdl_error (err 0)
[  204.475713] iwl3945: Unknown symbol il_send_rxon_timing (err 0)
[  204.475743] iwl3945: Unknown symbol il_wr_prph (err 0)
[  204.475760] iwl3945: Unknown symbol il_free_geos (err 0)
[  204.475776] iwl3945: Unknown symbol il_txq_update_write_ptr (err 0)
[  204.475794] iwl3945: Unknown symbol il_power_initialize (err 0)
[  204.475811] iwl3945: Unknown symbol il_rd_prph (err 0)
[  204.475832] iwl3945: Unknown symbol il_mac_change_interface (err 0)
[  204.475849] iwl3945: Unknown symbol il_get_active_dwell_time (err 0)
[  204.475866] iwl3945: Unknown symbol il_send_cmd (err 0)
[  204.475882] iwl3945: Unknown symbol il_get_free_ucode_key_idx (err 0)
[  204.475899] iwl3945: Unknown symbol il_clear_ucode_stations (err 0)
[  204.475915] iwl3945: Unknown symbol il_power_update_mode (err 0)
[  204.475930] iwl3945: Unknown symbol il_init_channel_map (err 0)
[  204.625631] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  204.625636] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  204.625724] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  204.625747] iwl3945 0000:03:00.0: setting latency timer to 64
[  204.666158] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[  204.666164] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  204.666325] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[  204.666822] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  204.691958] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

```

Those unknown symbols are probably from the custom theme I installed

---

### Post by chili555 on 2012-08-24
> What about that file in modprobe.d I found, is that causing a problem?Perhaps. What is it named? Let's remove it:```
sudo rm /etc/modprobe.d/<file_you_found>
sudo modprobe -r iwl3945
sudo modprobe iwl3945 fw_restart=1
```How is it now?```
dmesg | grep iwl | tail -n10
```

---

### Post by WishForHelp on 2012-08-24
Ok, going to do it now ):P



     File: IWL3945.conf

with inside:
     
 alias wlan0 iwl3945 options iwl3945 disable_hw_scan=1 

=> This is the file, I probably made it myself when trying stuff I found on the net :o


Okay did your commands, and this is the result:


dmesg | grep iwl | tail -n10```

[ 1556.004819] iwl3945 0000:03:00.0: PCI INT A disabled
[ 1565.177907] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 1565.177913] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 1565.178006] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1565.178030] iwl3945 0000:03:00.0: setting latency timer to 64
[ 1565.218465] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1565.218471] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 1565.218633] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[ 1565.219092] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 1565.350893] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
```

In my eyes, this outcome looks better now, (as an Ubuntu noob :D), but it still doesn't connect (:

---

### Post by chili555 on 2012-08-24
Does it try and fail or what? What are its symptoms?

---

### Post by WishForHelp on 2012-08-24
> **chili555 said:**
> Does it try and fail or what? What are its symptoms?

The symptoms are: Asking for a password 1000x an hour, acting like it's connecting, but then fails, then It shows the symbol when using a cable, then 2 mins later, the wifi symbols shows up + prompt to enter password, which is the correct password...

I installed the Original Network Manager back 2 days ago, because the WICD was even worse IMO. :eek:

Don't even want to know the hours i've spent looking on every possible site, to find a solution, this forum is my last possibility I guess.

---

### Post by chili555 on 2012-08-24
Well, as long as its 1000x an hour, we'll help. If it were only 800x we'd say it was too trivial. j/k.

Please try two other things. There is a newer driver here:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic-pae
```After that's done, reboot and let us have a report.

If the issue persists, try:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 swcrypto=0
```Again, let us hear a report.

---

### Post by WishForHelp on 2012-08-24
I tried the backports module and it said I had it already, on page 2 u said me to download it already, so I did the other command, and by report you mean the dmesg thing?



dmesg | grep iwl | tail -n10
```

[ 1456.224647] iwl3945 0000:03:00.0: PCI INT A disabled
[ 1465.423660] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 1465.423666] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 1465.423758] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1465.423782] iwl3945 0000:03:00.0: setting latency timer to 64
[ 1465.464280] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1465.464286] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 1465.464455] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[ 1465.464925] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 1465.682942] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
```dmesg | grep iwl

```
[   26.025530] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   26.025536] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   26.025629] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.025645] iwl3945 0000:03:00.0: setting latency timer to 64
[   26.080752] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   26.080759] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.080925] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[   26.092429] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.346963] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[ 1456.224647] iwl3945 0000:03:00.0: PCI INT A disabled
[ 1465.423660] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 1465.423666] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 1465.423758] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1465.423782] iwl3945 0000:03:00.0: setting latency timer to 64
[ 1465.464280] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 1465.464286] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 1465.464455] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[ 1465.464925] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[ 1465.682942] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

```Believe me, I would be happier if it was 'only' 800x an hour :)
If the wifi part is fixed, i'm afraid I need to make another thread about built in webcams & microphones, not working either, I feel that the devil is with me on this laptop

---

### Post by chili555 on 2012-08-24
> I tried the backports module and it said I had it already, on page 2 u said me to download it alreadyOops! Sorry about that. I'll check back later. Time for pizza and an adult beverage. See you a bit later.

---

### Post by WishForHelp on 2012-08-24
> **chili555 said:**
> Oops! Sorry about that. I'll check back later. Time for pizza and an adult beverage. See you a bit later.

That's fine, thanks for the suggestions already! 
):P

---

### Post by WishForHelp on 2012-08-26
I have the Network Manager Log here:

```
Aug 25 00:11:02 frederik-EasyNote-MX65 NetworkManager[824]: <warn> Activation (wlan0/wireless): association took too long.
Aug 25 00:11:02 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 25 00:11:02 frederik-EasyNote-MX65 NetworkManager[824]: <warn> Activation (wlan0/wireless): asking for new secrets
Aug 25 00:11:02 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 25 00:11:02 frederik-EasyNote-MX65 NetworkManager[824]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <warn> No agents were available for this request.
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <warn> Activation (wlan0) failed for access point (Timo's Wifi)
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Marking connection 'Timo's Wifi' invalid.
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <warn> Activation (wlan0) failed.
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 25 00:11:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Auto-activating connection 'Timo's Wifi'.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) starting connection 'Timo's Wifi'
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0/wireless): access point 'Timo's Wifi' has security, but secrets are required.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0/wireless): connection 'Timo's Wifi' has security, and secrets exist.  No new secrets needed.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Config: added 'ssid' value 'Timo's Wifi'
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Config: added 'scan_ssid' value '1'
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Config: added 'psk' value '<omitted>'
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> Config: set interface ap_scan to 1
Aug 25 00:16:36 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 25 00:16:40 frederik-EasyNote-MX65 wpa_supplicant[897]: Trying to authenticate with 4c:60:de:33:c2:c2 (SSID='Timo's Wifi' freq=2462 MHz)
Aug 25 00:16:40 frederik-EasyNote-MX65 NetworkManager[824]: <info> (wlan0): supplicant interface state: scanning -> authenticating
```

Maybe it gives people any ideas?

---

### Post by chili555 on 2012-08-27
Your dmesg logs above look very clean. It appears that we have cleaned up all this:> [  204.474076] iwl3945: Unknown symbol il_pm_ops (err 0)
[  204.474100] iwl3945: Unknown symbol il_eeprom_free (err 0)
[  204.474136] iwl3945: Unknown symbol il_rx_queue_alloc (err 0)
[  204.474157] iwl3945: Unknown symbol il_prep_station (err 0)
[  204.474199] iwl3945: Unknown symbol il_poll_bit (err 0)And this:> [   68.680033] iwl3945 0000:03:00.0: Queue 0 stuck for 2000 ms.
[   68.680040] iwl3945 0000:03:00.0: On demand firmware reloadLet's verify. I'd like you to try one driver parameter and then give me the whole dmesg file. Please do:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 swcrypto=0
dmesg > wish.txt
zip wish.zip wish.txt
```Find the file wish.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box. Thanks.

---

### Post by WishForHelp on 2012-08-27
I found the file, I hope it's uploaded.

---

### Post by chili555 on 2012-08-27
> [   26.489170] [COLOR="Red"]ndiswrapper[/COLOR] (import:232): unknown symbol: STREAM.SYS:'StreamClassDeviceNotification'
[   26.489183] ndiswrapper (import:232): unknown symbol: STREAM.SYS:'StreamClassStreamNotification'
[   26.489193] ndiswrapper (import:232): unknown symbol: STREAM.SYS:'StreamClassQueryMasterClockSync'
[   26.489202] ndiswrapper (import:232): unknown symbol: STREAM.SYS:'StreamClassRegisterAdapter'
[   26.489232] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bisoncam'
[   26.489341] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bisoncam'
[   26.489417] usbcore: registered new interface driver ndiswrapperDid you try to get this device going with ndiswrapper? What is 'bisoncam'? If it is not a wireless adapter, I highly doubt ndiswrapper is going to work.

I wonder if ndiswrapper is interfering.

---

### Post by WishForHelp on 2012-08-27
I installed ndiswrapper this night, to try it with the official drivers from the website, but no luck either... I'll remove it
Bisoncam was the driver for the built in webcam & microphone who aren't workign either, and ndiswrapper didn't solve it.
The green light of the cam is turned on when I try to test him, but i get a blank/white screen. But this are problems for later.

I installed 3 drivers with it, 2 drivers for the webcam (from the site), one driver says hardware available YES, the other one says NO.
Then I installed the Wireless driver -> Hardware available => NO. This is the official wireless driver, and this one doesn't see the hardware? Strange.

---

### Post by chili555 on 2012-08-27
I suggest you remove ndiswrapper altogether and then see how your wireless is doing:```
sudo apt-get remove --purge ndiswrapper*
```> This is the official wireless driver, and this one doesn't see the hardware? Strange. ndiswrapper is a complicated subject; some say a black art. Some drivers are more 'official' than others. Since, so far, we don't need or want it, let's leave it at that for now.

---

### Post by WishForHelp on 2012-08-27
I removed it. ;)

---

### Post by chili555 on 2012-08-27
And, after a reboot, how does your garden grow? That's southern USA-speak for 'how does your wireless work?' Any clues here:```
dmesg | grep iwl
```

---

### Post by WishForHelp on 2012-08-27
I'm not a gardener, so I really have no idea, seems to be good in my opinion the dmesg log, but still, the wireless isn't working.

```
[   24.977890] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   24.977894] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   24.977972] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.977988] iwl3945 0000:03:00.0: setting latency timer to 64
[   25.409703] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   25.409709] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   25.409877] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[   25.434623] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   26.461440] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[  119.320385] iwl3945 0000:03:00.0: PCI INT A disabled
[  131.864832] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  131.864837] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[  131.864930] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  131.864953] iwl3945 0000:03:00.0: setting latency timer to 64
[  131.905413] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[  131.905418] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  131.905579] iwl3945 0000:03:00.0: irq 44 for MSI/MSI-X
[  131.906038] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  131.937573] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
```

---

### Post by chili555 on 2012-08-27
Looks perfect! Let's see:```
rfkill list all
iwconfig
nm-tools
```Thanks.

---

### Post by WishForHelp on 2012-08-27
rfkill list all
1```
: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```nm-tools
```
Opdracht &#8216;nm-tools&#8217; niet gevonden, bedoelde u:
 Opdracht &#8216;nm-tool&#8217; uit pakket &#8216;network-manager&#8217; (main)
nm-tools: opdracht niet gevonden
```

nm-tools translation: 'not found, did you mean: nm-tool from the packet 'network manager'?

---

### Post by chili555 on 2012-08-27
> did you mean: nm-tool from the packet 'network manager'?That's a pretty smart computer you have there: it catches my mistakes and it speaks Dutch!

Sorry about that:```
nm-tool
```...with no 's.'

---

### Post by WishForHelp on 2012-08-27
> **chili555 said:**
> That's a pretty smart computer you have there: it catches my mistakes and it speaks Dutch!

Sorry about that:```
nm-tool
```...with no 's.'

U know Dutch or u saw that in one of my logs? Yea, should've seen that myself '-s' the correction was right before my nose lol. :D

```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:18:DE:D3:E2:DA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Timo's Wifi:     Infra, 4C:60:DE:33:C2:C2, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    wifi13:          Infra, 00:24:01:D4:B1:81, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    Connectify- Shani: Infra, 00:25:D3:8F:C2:2F, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Sitecom55B242:   Infra, 00:0C:F6:55:B2:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA
    GVO-WL2:         Infra, 58:6D:8F:63:95:B5, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:18:F3:E6:9A:62

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4

```

---

### Post by chili555 on 2012-08-27
> U know Dutch or u saw that in one of my logs?I had a little help from Google translate. I have answered whole threads in Spanish using nothing but Google translate. I know it's often a bit clumsy, but it works well enough.

Network Manager will disallow a wireless connection if wired is available as it is here:> IPv4 Settings:
    Address:         192.168.1.3Would you please detach the ethernet cable, wait a few moments for NM to notice the change in state, and try to connect. If it doesn't, let us see:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```We have cleaned up a lot of errors and warnings already.

---

### Post by WishForHelp on 2012-08-27
Hablas espangol, si -> Or sthing like that is the only thing I know :p

Sadly enough I have to answer with a negative response...

```
Aug 28 00:13:30 frederik-EasyNote-MX65 NetworkManager[806]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 28 00:13:31 frederik-EasyNote-MX65 NetworkManager[806]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0/wireless): connection 'Timo's Wifi' has security, and secrets exist.  No new secrets needed.
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Config: added 'ssid' value 'Timo's Wifi'
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Config: added 'scan_ssid' value '1'
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Config: added 'psk' value '<omitted>'
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> Config: set interface ap_scan to 1
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 28 00:13:38 frederik-EasyNote-MX65 NetworkManager[806]: <info> (wlan0): supplicant interface state: scanning -> authenticating
```

I hope that your magic hat isn't almost empty

Even without a password, fail to connect

---

### Post by chili555 on 2012-08-28
When you click on the Network Manager icon, have you added to or changed any settings there? In most cases, except for one change, no human intervention is required; additional settings are not helpful.

The exception is IPv6. It should be set to 'Ignore.' Please see attached.

All other changes or additions should be removed.

---

### Post by WishForHelp on 2012-08-28
Didn't changed anything to the NM, nor to my wifi itself, I can't connect to any wifi, even without a password. I'll take a look at your attachment now. WIll edit this post later. ):P

I only changed my DNS on the wired network.

Edit: The IPV6 was 'automatic', but I set it to ignore but no connection yet

---

### Post by WishForHelp on 2012-08-30
Out of idea's? 

:(

---

### Post by WishForHelp on 2012-09-01
Linux mint no succes either, from live CD Booted, so still stuck with Ubuntu...

Going to try other distro's now.

If any of you have any suggestions, please, post them.
If we/I can't get this solved within 2 weeks, I need to say goodbye to linux... With pain in the heart, but the only way to use the laptop on the normal way is trough Wifi... :frown:

SMall edit, just in case: even without a password, it fails to connect

---

### Post by jmate24 on 2012-09-01
try going to your driver manufacturers website and see if you can download the latest driver for linux then compile and install it manually.

---

### Post by WishForHelp on 2012-09-01
> **jmate24 said:**
> try going to your driver manufacturers website and see if you can download the latest driver for linux then compile and install it manually.

What if they don't have Drivers for linux?
Tried Ndiswrapper already but no luck

---

### Post by westie457 on 2012-09-01
Hi, this is an idea that may or may not work.

Referring to the screenshot in post #43 - the Edit Connection window - in the 'Wireless' tab check the mode of the connection. In most cases it should be set to 'Infrastructure'. Try changing that  to 'Adhoc'.
Close out of the edit window, wait a few seconds to see if it connects automatically. If not then choose your connection, input the password and it should work.

This is something I tried a while ago with a rejected connection even though the password was correct.

chilli555 has already done most of the work with you and covered a lot of stuff that I know nothing about.

If the above suggestion does not work then it is easy enough to change back.

---

### Post by WishForHelp on 2012-09-02
> **westie457 said:**
> Hi, this is an idea that may or may not work.

Referring to the screenshot in post #43 - the Edit Connection window - in the 'Wireless' tab check the mode of the connection. In most cases it should be set to 'Infrastructure'. Try changing that  to 'Adhoc'.
Close out of the edit window, wait a few seconds to see if it connects automatically. If not then choose your connection, input the password and it should work.

This is something I tried a while ago with a rejected connection even though the password was correct.

chilli555 has already done most of the work with you and covered a lot of stuff that I know nothing about.

If the above suggestion does not work then it is easy enough to change back.


> chilli555 has already done most of the work with you and covered a lot of stuff that I know nothing about.

Me neither :p

I tried your suggestion, but when I set it to Adhoc, I can't click the save button. It expects me to have a WEP encryption, but this isn't the case

---

