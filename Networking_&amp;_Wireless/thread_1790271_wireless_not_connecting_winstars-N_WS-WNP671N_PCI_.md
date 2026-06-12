---
title: "wireless not connecting winstars-N WS-WNP671N PCI (Ralink RT2860STA)"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by El_ on 2011-06-24
I use Ubuntu 11.04 on a PC clone desktop.
With ethernet cable connects automatically, despite compiling wlan0
not connected. Do not know what I installed Ubuntu 10.04 and 11.04 over 30 times and still the same. Try to manually connect to the network connection did not work either hidden and also deal with ipv4 address assigned and neither worked.

1 ) Machine Brand and Model (PC/Laptop):
   desktop pc, clon. 

2)lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
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
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Ralink corp. Device 3062

3)ifconfig
eth0      Link encap:Ethernet  direcciónHW 10:78:d2:89:33:46  
          Direc. inet:192.168.1.101  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::1278:d2ff:fe89:3346/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1912 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1654 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:2076491 (2.0 MB)  TX bytes:207618 (207.6 KB)
          Interrupción:42 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:20 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:20 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:0c:0b:44:b8:4a  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thr:ff
          Power Management:ff

iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

4)lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
vesafb                 13449  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_via      56765  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18159  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13456  0 
psmouse                73312  0 
parport_pc             32111  1 
serio_raw              12990  0 
lp                     13349  0 
i2c_piix4              13095  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2434640  128 
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
parport                36746  3 ppdev,parport_pc,lp
soundcore              12600  1 snd
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
eeprom_93cx6           12653  1 rt2800pci
ati_agp                13202  0 
k10temp                12951  0 
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
libahci                25548  1 ahci
r8169                  42534  0 
pata_atiixp            12968  0 

5) $dmesg
[    0.384458] system 00:0e: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.384462] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.384535] pnp: PnP ACPI: found 15 devices
[    0.384536] ACPI: ACPI bus type pnp unregistered
[    0.384539] PnPBIOS: Disabled by ACPI PNP
[    0.420185] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.420187] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.420190] pci 0000:00:02.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.420193] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.420196] pci 0000:00:05.0: PCI bridge to [bus 02-02]
[    0.420198] pci 0000:00:05.0:   bridge window [io  0xe000-0xefff]
[    0.420201] pci 0000:00:05.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.420203] pci 0000:00:05.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.420206] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.420208] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.420212] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.420216] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.420226] pci 0000:00:02.0: setting latency timer to 64
[    0.420229] pci 0000:00:05.0: setting latency timer to 64
[    0.420236] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.420238] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.420239] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.420241] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.420243] pci_bus 0000:00: resource 8 [mem 0x80000000-0xdfffffff]
[    0.420245] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.420247] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.420248] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.420250] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.420252] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.420254] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.420256] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.420258] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.420260] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.420261] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.420263] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.420265] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.420267] pci_bus 0000:03: resource 8 [mem 0x80000000-0xdfffffff]
[    0.420269] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.420293] NET: Registered protocol family 2
[    0.420338] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.420484] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.420880] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.421101] TCP: Hash tables configured (established 131072 bind 65536)
[    0.421103] TCP reno registered
[    0.421105] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.421113] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.421192] NET: Registered protocol family 1
[    1.188056] pci 0000:01:00.0: Boot video device
[    1.188066] PCI: CLS 64 bytes, default 64
[    1.188225] cpufreq-nforce2: No nForce2 chipset.
[    1.188314] audit: initializing netlink socket (disabled)
[    1.188321] type=2000 audit(1308942682.184:1): initialized
[    1.195418] highmem bounce pool size: 64 pages
[    1.195422] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.196676] VFS: Disk quotas dquot_6.5.2
[    1.196728] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.197247] fuse init (API version 7.16)
[    1.197368] msgmni has been set to 1702
[    1.197629] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.197659] io scheduler noop registered
[    1.197661] io scheduler deadline registered
[    1.197687] io scheduler cfq registered (default)
[    1.197782] pcieport 0000:00:02.0: setting latency timer to 64
[    1.197808] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.197842] pcieport 0000:00:05.0: setting latency timer to 64
[    1.197859] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    1.197904] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.197921] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.198023] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.224045] ACPI: Power Button [PWRB]
[    1.224104] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.224107] ACPI: Power Button [PWRF]
[    1.224215] ACPI: acpi_idle registered with cpuidle
[    1.244539] thermal LNXTHERM:00: registered as thermal_zone0
[    1.244541] ACPI: Thermal Zone [THRM] (30 C)
[    1.244575] ERST: Table is not found!
[    1.244633] isapnp: Scanning for PnP cards...
[    1.244658] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.265127] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.598532] isapnp: No Plug & Play device found
[    1.692705] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.696329] Linux agpgart interface v0.103
[    1.697272] brd: module loaded
[    1.697630] loop: module loaded
[    1.697688] i2c-core: driver [adp5520] using legacy suspend method
[    1.697690] i2c-core: driver [adp5520] using legacy resume method
[    1.697779] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.697800] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.698018] Fixed MDIO Bus: probed
[    1.698042] PPP generic driver version 2.4.2
[    1.698067] tun: Universal TUN/TAP device driver, 1.6
[    1.698068] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.698123] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.698135] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.698144] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.698167] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.698213] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.698227] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.698240] ehci_hcd 0000:00:12.2: debug port 1
[    1.698310] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
[    1.708043] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.708160] hub 1-0:1.0: USB hub found
[    1.708163] hub 1-0:1.0: 6 ports detected
[    1.708240] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.708256] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.708284] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.708331] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.708347] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.708360] ehci_hcd 0000:00:13.2: debug port 1
[    1.708385] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
[    1.720041] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.720165] hub 2-0:1.0: USB hub found
[    1.720168] hub 2-0:1.0: 6 ports detected
[    1.720232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.720246] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.720262] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.720289] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.720363] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
[    1.780152] hub 3-0:1.0: USB hub found
[    1.780158] hub 3-0:1.0: 3 ports detected
[    1.780218] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.780233] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.780264] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.784084] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
[    1.844141] hub 4-0:1.0: USB hub found
[    1.844148] hub 4-0:1.0: 3 ports detected
[    1.844217] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.844233] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.844259] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.844329] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
[    1.904156] hub 5-0:1.0: USB hub found
[    1.904162] hub 5-0:1.0: 3 ports detected
[    1.904222] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.904237] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.904265] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.908085] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8fb000
[    1.968141] hub 6-0:1.0: USB hub found
[    1.968147] hub 6-0:1.0: 3 ports detected
[    1.968207] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.968224] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.968256] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.968319] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe8fa000
[    2.028161] hub 7-0:1.0: USB hub found
[    2.028167] hub 7-0:1.0: 2 ports detected
[    2.028226] uhci_hcd: USB Universal Host Controller Interface driver
[    2.028345] i8042: PNP: PS/2 Controller [PNP0303:S2K,PNP0f03:S2M] at 0x60,0x64 irq 1,12
[    2.028729] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.028737] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.028858] mousedev: PS/2 mouse device common for all mice
[    2.028944] rtc_cmos 00:02: RTC can wake from S4
[    2.032054] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    2.032163] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.032190] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.032266] device-mapper: uevent: version 1.0.3
[    2.032328] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.032415] device-mapper: multipath: version 1.2.0 loaded
[    2.032419] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.032509] EISA: Probing bus 0 at eisa.0
[    2.032511] EISA: Cannot allocate resource for mainboard
[    2.032512] Cannot allocate resource for EISA slot 1
[    2.032514] Cannot allocate resource for EISA slot 2
[    2.032515] Cannot allocate resource for EISA slot 3
[    2.032516] Cannot allocate resource for EISA slot 4
[    2.032517] Cannot allocate resource for EISA slot 5
[    2.032518] Cannot allocate resource for EISA slot 6
[    2.032520] Cannot allocate resource for EISA slot 7
[    2.032521] Cannot allocate resource for EISA slot 8
[    2.032522] EISA: Detected 0 cards.
[    2.032617] cpuidle: using governor ladder
[    2.032619] cpuidle: using governor menu
[    2.032807] TCP cubic registered
[    2.032893] NET: Registered protocol family 10
[    2.033295] NET: Registered protocol family 17
[    2.033306] Registering the dns_resolver key type
[    2.033332] powernow-k8: Found 1 AMD Athlon(tm) II X2 250 Processor (2 cpu cores) (version 2.20.00)
[    2.033362] powernow-k8:    0 : pstate 0 (3000 MHz)
[    2.033364] powernow-k8:    1 : pstate 1 (2300 MHz)
[    2.033365] powernow-k8:    2 : pstate 2 (1800 MHz)
[    2.033366] powernow-k8:    3 : pstate 3 (800 MHz)
[    2.033481] Using IPI No-Shortcut mode
[    2.033556] PM: Hibernation image not present or could not be loaded.
[    2.033563] registered taskstats version 1
[    2.033759]   Magic number: 15:435:193
[    2.033798] acpi device:1f: hash matches
[    2.033845] rtc_cmos 00:02: setting system clock to 2011-06-24 19:11:23 UTC (1308942683)
[    2.033847] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.033849] EDD information not available.
[    2.033919] Freeing unused kernel memory: 700k freed
[    2.034107] Write protecting the kernel text: 5192k
[    2.034137] Write protecting the kernel read-only data: 2148k
[    2.046970] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.053915] <30>udev[62]: starting version 167
[    2.121593] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.121609] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.121639] r8169 0000:02:00.0: setting latency timer to 64
[    2.121683] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.122051] r8169 0000:02:00.0: eth0: RTL8102e at 0xf8036000, 10:78:d2:89:33:46, XID 04c00000 IRQ 42
[    2.138339] scsi0 : pata_atiixp
[    2.143780] scsi1 : pata_atiixp
[    2.144300] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.144303] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.144552] ahci 0000:00:11.0: version 3.0
[    2.144569] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.144666] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.144669] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    2.145539] scsi2 : ahci
[    2.145598] scsi3 : ahci
[    2.145653] scsi4 : ahci
[    2.145709] scsi5 : ahci
[    2.145793] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
[    2.145796] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
[    2.145798] ata5: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
[    2.145801] ata6: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
[    2.170708] usbcore: registered new interface driver uas
[    2.188049] Refined TSC clocksource calibration: 2993.498 MHz.
[    2.188054] Switching to clocksource tsc
[    2.316681] ata2.00: ATA-7: Maxtor 6E030L0, NAR61590, max UDMA/133
[    2.316684] ata2.00: 60058656 sectors, multi 16: LBA 
[    2.316689] ata2.00: limited to UDMA/33 due to 40-wire cable
[    2.332614] ata2.00: configured for UDMA/33
[    2.332784] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6E030L0   NAR6 PQ: 0 ANSI: 5
[    2.332937] sd 1:0:0:0: [sda] 60058656 512-byte logical blocks: (30.7 GB/28.6 GiB)
[    2.332945] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    2.332968] sd 1:0:0:0: [sda] Write Protect is off
[    2.332971] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.332988] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.335590]  sda: sda1
[    2.335811] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.464072] ata6: SATA link down (SStatus 0 SControl 300)
[    2.464137] ata5: SATA link down (SStatus 0 SControl 300)
[    2.636043] ata4: softreset failed (device not ready)
[    2.636047] ata4: applying SB600 PMP SRST workaround and retrying
[    2.636066] ata3: softreset failed (device not ready)
[    2.636068] ata3: applying SB600 PMP SRST workaround and retrying
[    2.808039] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.808066] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.810525] ata4.00: ATAPI: ATAPI   iHAS122, ZL07, max UDMA/100
[    2.811375] ata4.00: configured for UDMA/100
[    2.814475] ata3.00: ATA-7: SAMSUNG HD161GJ, 1AC01118, max UDMA7
[    2.814478] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.820984] ata3.00: configured for UDMA/133
[    2.821137] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD161GJ  1AC0 PQ: 0 ANSI: 5
[    2.821284] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.821317] sd 2:0:0:0: [sdb] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.821356] sd 2:0:0:0: [sdb] Write Protect is off
[    2.821358] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.821372] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.822723] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS122          ZL07 PQ: 0 ANSI: 5
[    2.826095] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.826099] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.826219] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.826284] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    2.865001]  sdb: sdb1 < sdb5 sdb6 sdb7 > sdb2 sdb3
[    2.865305] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.869883] Initializing USB Mass Storage driver...
[    2.870790] scsi6 : usb-storage 2-3:1.0
[    2.870997] usbcore: registered new interface driver usb-storage
[    2.870999] USB Mass Storage support registered.
[    3.395104] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[    3.868869] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.869496] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.870156] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    3.870743] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    3.871141] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    3.871243] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    3.871331] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    3.871420] sd 6:0:0:3: Attached scsi generic sg6 type 0
[    3.877487] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    3.879738] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    3.880486] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    3.881235] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    4.808630] Adding 1994748k swap on /dev/sdb7.  Priority:-1 extents:1 across:1994748k 
[    5.010887] <30>udev[370]: starting version 167
[    6.286318] type=1400 audit(1308953487.749:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=563 comm="apparmor_parser"
[    6.286582] type=1400 audit(1308953487.749:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=563 comm="apparmor_parser"
[    6.286752] type=1400 audit(1308953487.749:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=563 comm="apparmor_parser"
[    6.286903] type=1400 audit(1308953487.749:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=538 comm="apparmor_parser"
[    6.287171] type=1400 audit(1308953487.749:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=538 comm="apparmor_parser"
[    6.287347] type=1400 audit(1308953487.749:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=538 comm="apparmor_parser"
[    6.455591] cfg80211: Calling CRDA to update world regulatory domain
[    6.729293] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    6.729297] Disabling lock debugging due to kernel taint
[    6.776397] [fglrx] Maximum main memory to use for locked dma buffers: 1884 MBytes.
[    6.776557] [fglrx]   vendor: 1002 device: 954f count: 1
[    6.776897] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[    6.776907] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.776912] pci 0000:01:00.0: setting latency timer to 64
[    6.777124] [fglrx] Kernel PAT support is enabled
[    6.777141] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[    6.786005] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    6.790425] lp: driver loaded but no devices found
[    6.808075] parport_pc 00:06: reported by Plug and Play ACPI
[    6.808128] parport0: PC-style at 0x378, irq 7 [PCSPP]
[    6.848273] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[    6.848387] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[    6.904155] lp0: using parport0 (interrupt-driven).
[    6.940118] ppdev: user-space parallel port driver
[    6.954234] psmouse serio1: ID: 10 00 64
[    7.193032] rt2800pci 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    7.194977] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    7.194979] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.194981] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    7.194983] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.194985] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    7.194986] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.194988] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    7.194990] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.194991] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    7.194993] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.194995] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    7.194997] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.194998] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    7.195000] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195002] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    7.195003] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195005] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    7.195007] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195008] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    7.195010] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195012] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    7.195014] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195015] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    7.195017] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195019] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    7.195021] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.195022] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    7.195024] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (600 mBi, 2000 mBm)
[    7.317383] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    7.317842] Registered led device: rt2800pci-phy0::radio
[    7.317858] Registered led device: rt2800pci-phy0::assoc
[    7.317871] Registered led device: rt2800pci-phy0::quality
[    7.439075] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    7.439079] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439081] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    7.439083] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439085] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    7.439086] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439088] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    7.439090] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439091] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    7.439093] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439095] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    7.439097] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439098] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    7.439100] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439102] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    7.439104] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439105] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    7.439107] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439108] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    7.439110] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439112] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    7.439114] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439115] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    7.439117] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439119] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    7.439120] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439122] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[    7.439124] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[    7.439126] cfg80211: World regulatory domain updated:
[    7.439127] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.439129] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.439131] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.439133] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.439135] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.439136] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.455169] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    7.801428] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.856089] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    7.856141] HDA Intel 0000:01:00.1: irq 43 for MSI/MSI-X
[    7.856160] HDA Intel 0000:01:00.1: setting latency timer to 64
[    8.468750] vesafb: framebuffer at 0xd0000000, mapped to 0xf9f80000, using 3904k, total 3904k
[    8.468753] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[    8.468755] vesafb: scrolling: redraw
[    8.468757] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    8.468899] Console: switching to colour frame buffer device 144x54
[    8.468919] fb0: VESA VGA frame buffer device
[    9.262968] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
[    9.414896] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[   10.103185] type=1400 audit(1308953491.565:8: apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=922 comm="apparmor_parser"
[   10.103506] type=1400 audit(1308953491.565:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=922 comm="apparmor_parser"
[   10.231067] type=1400 audit(1308953491.693:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=941 comm="apparmor_parser"
[   10.231344] type=1400 audit(1308953491.693:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=941 comm="apparmor_parser"
[   11.649036] r8169 0000:02:00.0: eth0: link down
[   11.649043] r8169 0000:02:00.0: eth0: link down
[   11.649372] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.922986] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.447625] r8169 0000:02:00.0: eth0: link up
[   13.447812] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.595985] fglrx_pci 0000:01:00.0: irq 44 for MSI/MSI-X
[   13.596489] [fglrx] Firegl kernel thread PID: 1210
[   13.596534] [fglrx] Firegl kernel thread PID: 1211
[   13.596613] [fglrx] Firegl kernel thread PID: 1212
[   13.596833] [fglrx] IRQ 44 Enabled
[   13.913517] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   13.937501] EXT4-fs (sdb6): re-mounted. Opts: commit=0
[   14.514876] [fglrx] Gart USWC size:628 M.
[   14.514879] [fglrx] Gart cacheable size:247 M.
[   14.514883] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   14.514885] [fglrx] Reserved FB block: Unshared offset:fe07000, size:1f9000 
[   14.514887] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   22.475850] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   22.493408] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   22.495379] EXT4-fs (sdb6): re-mounted. Opts: commit=0
[   24.312014] eth0: no IPv6 routers present

6) $ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 10:78:d2:89:33:46
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:feae0000-feafffff
  *-network
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:0c:0b:44:b8:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:febf0000-febfffff

7)$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

8) $ lsb_release -d
Description:    Ubuntu 11.04

9)uname -mr
2.6.38-8-generic i686

10)(cable not connected eth0)
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

10) (with cable connected eth0)
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.


Not that I am wrong. Try setting manually to no avail not know if I did well. Ralink also downloaded from the rt2860sta and then compiled and did not work. Now I went to install Ubuntu 11.04 and change nothing but that which is above is what I have right now in the machine.

Thank you very much for the help I can provide.

El_

---

### Post by chili555 on 2011-06-24
May I see:```
lspci -nn | grep Network
```The title of your thread refers to RT2860 but I don't see it loaded in *lsmod*. Do you have it blacklisted? It shouldn't be necessary to compile it; it's included in the kernel by default.

---

### Post by El_ on 2011-06-25
1) 
"lspci -nn | grep Network"
03:00.0 Network controller [0280]: Ralink corp. Device [1814:3062]

2)
"sudo gedit /etc/modprobe.d/blacklist.conf"
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

When installing Ubuntu does not automatically connect to wlan0 eth0 when I plug in the cable when connecting at all times to install and / or reinstall does the same.
Thanks again.

---

### Post by chili555 on 2011-06-25
> When installing Ubuntu does not automatically connect to wlan0 eth0 when I plug in the cable when connecting at all times to install and / or reinstall does the same.I am afraid I do not understand what you are saying. I am sorry. Your wireless is being driven by rt2800pci. I see nothing incorrect. 

Are you saying that when you disconnect the ethernet cable that the wireless will not connect? Is this a laptop? Please run and post:```
rfkill list all
sudo iwlist wlan0 scan
```

---

### Post by El_ on 2011-06-25
Are you saying that when you disconnect the ethernet cable that the wireless will not connect? Yes
Is this a laptop? Nou this is Pc desktop.

"rfkill list all"
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

"sudo iwlist wlan0 scan"
[sudo] password for eluni: 
wlan0     No scan results

Thanks again

---

### Post by chili555 on 2011-06-25
Did you fill in wireless details in Network Manager? Please be sure that mode is set to Infrastructure and IPv4 is set to Automatic (DHCP). Do you see your network listed when you click the Network Manager icon?

Tell me more about the driver you downloaded from Ralink and compiled.

Let's have a look at:```
sudo cat /var/log/syslog | grep -e rt2 -e etwork | tail -n25
```Thanks.

---

### Post by El_ on 2011-06-26
Did you fill in wireless details in Network Manager? Data is not populated in the Network Manager.
 
Please be sure that mode is set to Infrastructure and IPv4 is set to Automatic (DHCP). Do you see your network listed when you click the Network Manager icon?

For example try the following: Edit the connections. In Wireless-Add: SSID: <NNNNN>. Mode: Infrastructure. Address MAC: <physical pci> MTU: Wireless automatic. Security: none. Settings IPV4: Method: Automatic (DHCP). Routes: if you do not address the example set by wh0 192.168.1.104. Netmask: 24. Gateway: none.

Connected "SSID:" NNNNN, not connect, nor do I see the network.

Downloaded from ralink [http://www.ralinktech.com/license_us.php?](http://www.ralinktech.com/license_us.php?) 
RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890).
I have not compiled.


"sudo cat /var/log/syslog | grep -e rt2 -e etwork | tail -n25"

Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> dhclient started with pid 2855
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info>   address 192.168.1.101
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info>   prefix 24 (255.255.255.0)
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info>   gateway 192.168.1.1
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info>   nameserver '192.168.1.1'
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Scheduling stage 5
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Done scheduling stage 5
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 25 22:11:35 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 25 22:11:36 eluni-pc NetworkManager[967]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun 25 22:11:36 eluni-pc NetworkManager[967]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 25 22:11:36 eluni-pc NetworkManager[967]: <info> Activation (eth0) successful, device activated.
Jun 25 22:11:36 eluni-pc NetworkManager[967]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 25 23:10:23 eluni-pc NetworkManager[967]: <info> (eth0): DHCPv4 state changed reboot -> renew
Jun 25 23:10:23 eluni-pc NetworkManager[967]: <info>   address 192.168.1.101
Jun 25 23:10:23 eluni-pc NetworkManager[967]: <info>   prefix 24 (255.255.255.0)
Jun 25 23:10:23 eluni-pc NetworkManager[967]: <info>   gateway 192.168.1.1
Jun 25 23:10:23 eluni-pc NetworkManager[967]: <info>   nameserver '192.168.1.1'
Jun 25 23:10:23 eluni-pc nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

---

### Post by chili555 on 2011-06-26
> Data is not populated in the Network Manager.Good! If things are working correctly, Network Manager should find and connect to your network without any help. Please make sure all details are removed and deleted except that the drop-down for Ad Hoc or Infrastructure is set to Infrastructure and the drop-down for Mode is set to Automatic (DHCP). All other areas should be blank.

Your syslog listing shows plenty of detail for eth0, your wired ethernet. It doesn't show us anything that helps us. Please detach the cable and try the scan again:```
sudo iwlist wlan0 scan
```With the ethernet cable still detached, please do:```
sudo /etc/init.d/network-manager restart
sudo cat /var/log/syslog | grep etwork | tail -n25
```If we need to compile, do you have the build tools and headers installed?```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by El_ on 2011-06-26
Used on Network Manager Connect to a wireless network hidden and not see any, network name, type the SSID name and did not establish any connection without SSID did not work.

I tried wireless Edit: "Ad Hoc" and also "Infrastucture" and also: "It requires IPv4 address for this connection is complete" and checking and unchecking does not establish connection.

Result is the same with Ethernet connected or disconnected:
"sudo iwlist wlan0 scan"
wlan0     No scan results

With the ethernet cable still detached, please do: result.

"sudo /etc/init.d/network-manager restart"
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop network-manager ; start network-manager. The restart(8) utility is also available.
network-manager stop/waiting
network-manager start/running, process 2369

"sudo cat /var/log/syslog | grep etwork | tail -n25"
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> dhclient started with pid 2376
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info>   address 192.168.1.101
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info>   prefix 24 (255.255.255.0)
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info>   gateway 192.168.1.1
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info>   nameserver '192.168.1.1'
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Scheduling stage 5
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Done scheduling stage 5
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 26 19:05:51 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 26 19:05:52 elinu-pc NetworkManager[2369]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun 26 19:05:52 elinu-pc NetworkManager[2369]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 26 19:05:52 elinu-pc NetworkManager[2369]: <info> Activation (eth0) successful, device activated.
Jun 26 19:05:52 elinu-pc NetworkManager[2369]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.


With the ethernet cable still detached, please do: Disconnected result.

"sudo /etc/init.d/network-manager restart"
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop network-manager ; start network-manager. The restart(8) utility is also available.
network-manager stop/waiting
network-manager start/running, process 2270

"sudo cat /var/log/syslog | grep etwork | tail -n25"
Jun 26 18:57:22 aaaeo-pc NetworkManager[2270]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:14.4/0000:03:00.0/ieee80211/phy0/rfkill0) (driver <unknown>)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> Networking is enabled by state file
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): carrier is OFF
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): now managed
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): bringing up device.
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): preparing device.
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (eth0): deactivating device (reason: 2).
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/eth0
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): now managed
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): bringing up device.
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): preparing device.
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): deactivating device (reason: 2).
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): device state change: 2 -> 3 (reason 42)

If we need to compile, do you have the build tools and headers installed? Yes

"sudo apt-get install build-essential linux-headers-generic"
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
build-essential ya está en su versión más reciente.
linux-headers-generic ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

---

### Post by chili555 on 2011-06-27
> Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): now managed
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): bringing up device.
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): preparing device.
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): deactivating device (reason: 2).
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 26 18:57:22 elinu-pc NetworkManager[2270]: <info> (wlan0): device state change: 2 -> 3 (reason 42)This all looks pretty hopeful. The activation process goes from state 1 to 2 and on to 3. We don't see any errors or any place where the interface wlan0 stops moving towards connecting and is inactivated. If we saw an error or problem, that would give us something to work on. What we actually do see is the interface and Network Manager are progressing along towards success and then the syslog ends. 

You could try to capture more of syslog hoping we see what happens or any errors after this:> <info> (wlan0): device state change: 2 -> 3 (reason 42)If you prefer, we could conclude that rt2800pci isn't going to work satisfactorily at all and blacklist it. We could then carefully examine RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890) to be certain that it claims your device: > 03:00.0 Network controller [0280]: Ralink corp. Device [1814:3062]I doubt that it does; I think rt3562sta drives your device.

I am very willing to help you in any way.

---

### Post by El_ on 2011-06-27
I created a new SSID on the router called Mar - key, 23 digits and symbols.

Connecting to a hidden network, and Mar wrote:

It always ends up not connecting.

I will try to do the following:

sudo cat /var/log/syslog | grep etwork | tail -n25
Jun 27 13:17:54 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 27 13:17:54 elinu-pc NetworkManager[857]: <info> Config: set interface ap_scan to 1
Jun 27 13:17:54 elinu-pc NetworkManager[857]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <warn> Activation (wlan0) failed for access point (Mar)
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <info> Marking connection 'Mar' invalid.
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <warn> Activation (wlan0) failed.
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jun 27 13:18:54 elinu-pc NetworkManager[857]: <info> (wlan0): deactivating device (reason: 0).
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) starting connection 'Mar'
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0/wireless): connection 'Mar' requires no security.  No secrets needed.
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Config: added 'ssid' value 'Mar'
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Config: added 'scan_ssid' value '1'
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> Config: set interface ap_scan to 1
Jun 27 13:19:53 elinu-pc NetworkManager[857]: <info> (wlan0): supplicant connection state:  disconnected -> scanning


1- Use the linux driver for the CD of the plate. Here I ask a favor, you can tell me exactly how to build this right?.

2 - I can pass before the full file cd to see if I have to do something special before compiling.

3 - Before this, I re-download Ubuntu 11.04 if something did not download it before, and install it again from a pendrive.

4 - Here are several options: Pray for a mythological god. Climbing the Himalayas and see a Tibetan monk. To walk the Great Wall of China and back. See pass-ralink technicians and WinStars to tell you that does not work on all machines. And last make a fire and place the plate Viking pci ralink on it. A joke all this.

I can not thank you for your patience and I apologize to distract your attention.

A hug.

---

### Post by El_ on 2011-06-27
Maybe this can help. The file on CD plate is beginning to 2009 and was down from ralink is starting with 2010. I sent an email requesting in this case the driver. "Inf", but not this one, it must be very busy answering many mail. Thanks again.

---

### Post by chili555 on 2011-06-27
This can not help. I just built the module and it reports:> # modinfo /home/chili/Desktop/Forum/L_/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.ko
filename:       /home/chili/Desktop/Forum/L_/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt2860sta.ko
license:        GPL
version:        2.4.0.0
srcversion:     0EA2D071E08BE7D02E2F7F0
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38.2 SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
Your device isn't listed:> 03:00.0 Network controller [0280]: Ralink corp. Device [[COLOR="Red"]1814:3062[/COLOR]]
As I said, rt3652sta is correct for your device:```
$ modinfo rt3562sta | grep 3062
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]3062[/COLOR]sv*sd*bc*sc*i*
```If you'd like to compile rt3562sta, go here and download DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz : [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) 

It's referred to as 3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592)

Download it to your desktop. Right click it and select 'Extract Here.' Open the folder that appears when you extract the file and find the folder called os; inside is a folder called linux; inside is a file called config.mk. With a text editor, please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Proofread, save and close the text editor.

Now open a terminal and we'll blacklist rt2800pci:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
cd Desktop/2010
```Press the Tab key and the remainder will fill in. If your system is in another language than English, substitute the name of 'Desktop' in your command. Back in the terminal, do:```
make
make install
echo rt3562sta >> /etc/modules
exit
```Reboot and tell us if your wireless is working.

---

### Post by El_ on 2011-06-28
It works, I am connected to wlan0. Actually if not for you I never would have connected, but Ubuntu never doubt or you or the people using their time to help make it great this system. Really very, very grateful. I lack words and emotions to thank him. Course will copy the link to the Ubuntu people of my country to have this information and address if they have the same card. Again many, thank you very much and best for you. A warm hug.

---

### Post by chili555 on 2011-06-28
I am very grateful for your kind words and thoughts. It makes me very happy to know I have friends all over the world that I have helped, in some small way, to begin their steps into the fascinating world of Ubuntu Linux.

When Update Manager brings you a later kernel version, called linux-image in Ubuntu, you will need to compile a new module:```
sudo su
cd Desktop/2010
```Press the Tab key and the remainder will fill in. If your system is in another language than English, substitute the name of 'Desktop' in your command. Back in the terminal, do:```

[COLOR="Red"]make clean[/COLOR]
make
make install
exit
```I'm very glad it's working.

---

### Post by xpd777 on 2011-06-28
Hi, this thread looks promising. I have the same problem except that my wlan0 is Ralink 3062F. I followed the instructions:

sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
cd Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
make
make install
echo rt3562sta >> /etc/modules
exit


rebooted. and wlan is disabled




01:04.0 Network controller: Ralink corp. Device 3062
	Subsystem: Ralink corp. Device 3062
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at ec000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci

---

### Post by chili555 on 2011-06-29
> Kernel driver in use: rt2860
Kernel modules: rt3562sta, rt2800pciIt looks like too many conflicting modules are loading. Let's check. Please run and post:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by hoyer801 on 2011-12-03
I just purchased this exact same wireless adapter without checking for Linux compatibility. While I'm not exactly a Linux beginner, this thread really made my life easier and drastically reduced the time of googling for exactly where to find these drivers and how best to install them. 

Thanks, chili555

---

