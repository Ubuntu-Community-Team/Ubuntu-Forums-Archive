---
title: "Atheros AR9285/Ubuntu 12.04/HP G6 1220sd"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by BjarkiJod on 2012-06-06
Hello Ubuntu peeps.

I bought a new laptop a few months ago and directly installed a linux system to dual-boot with W7.

I now have a fresh install of Ubuntu 12.04 and it detects the WiFi card out of box. The range however is terrible, it detects maybe one connection, and most of the time it is not even my own. If I sit next to the router, it picks up my connection and I can connect, but as soon as I move two meters away, the connection drops. 
On W7, the card detects up to 15 available connections, but maybe 1 on Ubuntu.

**1. ****Machine Brand and Model (PC/Laptop)**:
HP G6 1220sd
2.4 GHz Intel Core i5-2430M.
4 GB DDR3.
Atheros AR9285 802.11 b/g/n.

**2.**[B] Wireless Brand, Model and Wireless Chipset:
lspci[/B]
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```[B]lsusb
[/B]```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink)

[B]3 ) check interface:
ifconfig[/B]
[CODE]
eth0      Link encap:Ethernet  HWaddr 10:1f:74:ca:66:30  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:feca:6630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154799080 (154.7 MB)  TX bytes:4073354 (4.0 MB)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16846 (16.8 KB)  TX bytes:16846 (16.8 KB)

wlan0     Link encap:Ethernet  HWaddr 38:59:f9:6d:27:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```[B]iwconfig
[/B]```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```[B]4 ) Check for modules:
lsmod
[/B]```

Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
ath9k                 117326  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              436455  1 ath9k
i915                  414672  3 
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
joydev                 17393  0 
drm_kms_helper         45466  1 i915
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  3 ath9k,mac80211,ath
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
rts_pstor             353215  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mei                    36570  0 
wmi                    18744  1 hp_wmi
mac_hid                13077  0 
psmouse                72919  0 
serio_raw              13027  0 
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 

```[B]

5 ) Kernel boot messages
dmesg
[/B]```

[    0.989412] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.989420] ACPI: Power Button [PWRF]
[    0.997388] [Firmware Bug]: Invalid critical threshold (0)
[    0.998913] thermal LNXTHERM:00: registered as thermal_zone0
[    0.998919] ACPI: Thermal Zone [TZ01] (65 C)
[    0.998964] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.998982] ACPI: Battery Slot [BAT0] (battery present)
[    0.999051] ERST: Table is not found!
[    0.999056] GHES: HEST is not enabled!
[    0.999190] isapnp: Scanning for PnP cards...
[    0.999283] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.060051] ACPI: Battery Slot [BAT0] (battery present)
[    1.310435] Freeing initrd memory: 13800k freed
[    1.353194] isapnp: No Plug & Play device found
[    1.397191] Linux agpgart interface v0.103
[    1.397423] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.397569] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.400102] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.400382] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    1.404090] brd: module loaded
[    1.405994] loop: module loaded
[    1.406288] ahci 0000:00:1f.2: version 3.0
[    1.406333] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.406432] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    1.420337] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl SATA mode
[    1.420345] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.420357] ahci 0000:00:1f.2: setting latency timer to 64
[    1.429508] scsi0 : ahci
[    1.429718] scsi1 : ahci
[    1.429885] scsi2 : ahci
[    1.430051] scsi3 : ahci
[    1.430223] scsi4 : ahci
[    1.430387] scsi5 : ahci
[    1.430644] ata1: SATA max UDMA/133 abar m2048@0xc2607000 port 0xc2607100 irq 40
[    1.430650] ata2: DUMMY
[    1.430653] ata3: DUMMY
[    1.430656] ata4: DUMMY
[    1.430662] ata5: SATA max UDMA/133 abar m2048@0xc2607000 port 0xc2607300 irq 40
[    1.430667] ata6: DUMMY
[    1.431671] Fixed MDIO Bus: probed
[    1.431717] tun: Universal TUN/TAP device driver, 1.6
[    1.431722] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.431844] PPP generic driver version 2.4.2
[    1.432084] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.432123] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.432155] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.432163] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.432293] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.432342] ehci_hcd 0000:00:1a.0: debug port 2
[    1.436240] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.436294] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc2609000
[    1.448271] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.448580] hub 1-0:1.0: USB hub found
[    1.448590] hub 1-0:1.0: 2 ports detected
[    1.448728] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.448758] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.448765] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.448872] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.448915] ehci_hcd 0000:00:1d.0: debug port 2
[    1.452816] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.452847] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xc2608000
[    1.468240] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.468528] hub 2-0:1.0: USB hub found
[    1.468536] hub 2-0:1.0: 2 ports detected
[    1.468674] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.468702] uhci_hcd: USB Universal Host Controller Interface driver
[    1.468814] usbcore: registered new interface driver libusual
[    1.468922] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.478388] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.478402] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.478718] mousedev: PS/2 mouse device common for all mice
[    1.479151] rtc_cmos 00:06: RTC can wake from S4
[    1.479353] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.479397] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.479526] device-mapper: uevent: version 1.0.3
[    1.479703] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.479773] EISA: Probing bus 0 at eisa.0
[    1.479778] EISA: Cannot allocate resource for mainboard
[    1.479783] Cannot allocate resource for EISA slot 1
[    1.479787] Cannot allocate resource for EISA slot 2
[    1.479792] Cannot allocate resource for EISA slot 3
[    1.479796] Cannot allocate resource for EISA slot 4
[    1.479800] Cannot allocate resource for EISA slot 5
[    1.479805] Cannot allocate resource for EISA slot 6
[    1.479809] Cannot allocate resource for EISA slot 7
[    1.479814] Cannot allocate resource for EISA slot 8
[    1.479818] EISA: Detected 0 cards.
[    1.479836] cpufreq-nforce2: No nForce2 chipset.
[    1.480168] cpuidle: using governor ladder
[    1.480710] cpuidle: using governor menu
[    1.480715] EFI Variables Facility v0.08 2004-May-17
[    1.481176] TCP cubic registered
[    1.481459] NET: Registered protocol family 10
[    1.482557] NET: Registered protocol family 17
[    1.482590] Registering the dns_resolver key type
[    1.482630] Using IPI No-Shortcut mode
[    1.482947] PM: Hibernation image not present or could not be loaded.
[    1.482970] registered taskstats version 1
[    1.497845] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.505421]   Magic number: 0:589:994
[    1.505948] rtc_cmos 00:06: setting system clock to 2012-06-06 16:58:51 UTC (1339001931)
[    1.507884] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.507890] EDD information not available.
[    1.747910] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.747956] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.749470] ata1.00: ATA-8: Hitachi HTS547550A9E384, JE3OA50A, max UDMA/100
[    1.749481] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.751174] ata1.00: configured for UDMA/100
[    1.751661] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54755 JE3O PQ: 0 ANSI: 5
[    1.751746] ata5.00: ATAPI: hp      DVD A  DS8A5LH, 1H68, max UDMA/100
[    1.752156] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.752230] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.752243] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.752499] sd 0:0:0:0: [sda] Write Protect is off
[    1.752514] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.752731] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.753187] ata5.00: configured for UDMA/100
[    1.757275] scsi 4:0:0:0: CD-ROM            hp       DVD A  DS8A5LH   1H68 PQ: 0 ANSI: 5
[    1.759882] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.763558] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.763568] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.764081] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.764333] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.825279]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.827576] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.827819] Freeing unused kernel memory: 740k freed
[    1.828206] Write protecting the kernel text: 5828k
[    1.828263] Write protecting the kernel read-only data: 2376k
[    1.828267] NX-protecting the kernel data: 4412k
[    1.869486] udevd[104]: starting version 175
[    1.895646] Refined TSC clocksource calibration: 2394.560 MHz.
[    1.895662] Switching to clocksource tsc
[    1.904542] hub 1-1:1.0: USB hub found
[    1.904644] hub 1-1:1.0: 6 ports detected
[    1.938275] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.938334] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.938405] r8169 0000:02:00.0: setting latency timer to 64
[    1.938538] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
[    1.940115] r8169 0000:02:00.0: eth0: RTL8105e at 0xf843c000, 10:1f:74:ca:66:30, XID 00a00000 IRQ 41
[    2.015520] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.148709] hub 2-1:1.0: USB hub found
[    2.148801] hub 2-1:1.0: 6 ports detected
[    2.423009] usb 2-1.5: new high-speed USB device number 3 using ehci_hcd
[    2.499878] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.499889] EXT4-fs (sda6): write access will be enabled during recovery
[    6.656542] EXT4-fs (sda6): recovery complete
[    6.657784] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    9.304286] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.615734] Adding 1951740k swap on /dev/sda5.  Priority:-1 extents:1 across:1951740k 
[    9.626627] udevd[406]: starting version 175
[   10.585788] lp: driver loaded but no devices found
[   10.753906] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.754685] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.754699] mei 0000:00:16.0: setting latency timer to 64
[   10.754820] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[   10.825353] wmi: Mapper loaded
[   11.223221] [drm] Initialized drm 1.1.0 20060810
[   11.412237] cfg80211: Calling CRDA to update world regulatory domain
[   11.655563] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   11.666673] rts_pstor: module is from the staging directory, the quality is unknown, you have been warned.
[   11.668863] Initializing Realtek PCIE storage driver...
[   11.668924] rts_pstor 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.669043] Resource length: 0x1000
[   11.669072] Original address: 0xc1500000, remapped address: 0xf843e000
[   11.669080] pci->irq = 18
[   11.669084] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 18
[   11.669129] rts_pstor 0000:03:00.0: setting latency timer to 64
[   11.822707] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.822723] i915 0000:00:02.0: setting latency timer to 64
[   11.824165] input: HP WMI hotkeys as /devices/virtual/input/input4
[   11.857703] mtrr: type mismatch for b0000000,10000000 old: write-back new: write-combining
[   11.857711] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   11.858560] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   11.858572] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.858576] [drm] Driver supports precise vblank timestamp query.
[   11.858643] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.873495] scsi6 : SCSI emulation for PCI-Express Mass Storage devices
[   11.873972] rts_pstor: waiting for device to settle before scanning
[   12.100308] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.100339] ath9k 0000:01:00.0: setting latency timer to 64
[   12.152020] ath: EEPROM regdomain: 0x60
[   12.152028] ath: EEPROM indicates we should expect a direct regpair map
[   12.152038] ath: Country alpha2 being used: 00
[   12.152044] ath: Regpair used: 0x60
[   12.152052] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.152060] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152066] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.152073] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152078] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.152085] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152091] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.152098] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152103] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.152110] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152115] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.152122] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152127] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.152134] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152139] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.152146] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152151] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.152158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152163] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.152170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152175] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.152182] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152188] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   12.152194] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152200] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   12.152206] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.152212] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   12.152219] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.154259] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.436726] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.436737] cfg80211: World regulatory domain updated:
[   12.436742] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.436750] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.436757] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.436763] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.436770] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.436776] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.489413] Linux video capture interface: v2.00
[   12.498383] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[   12.503337] fbcon: inteldrmfb (fb0) is primary device
[   12.503588] Console: switching to colour frame buffer device 170x48
[   12.503687] fb0: inteldrmfb frame buffer device
[   12.503694] drm: registered panic notifier
[   12.532369] acpi device:1f: registered as cooling_device4
[   12.532973] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   12.533151] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.533247] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.544507] uvcvideo: Found UVC 1.00 device HP Webcam-101 (05c8:021e)
[   12.550603] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   12.559065] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input7
[   12.559232] usbcore: registered new interface driver uvcvideo
[   12.559237] USB Video Class driver (1.1.1)
[   12.615347] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.616809] Registered led device: ath9k-phy0
[   12.616834] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8a40000, irq=16
[   12.871390] rts_pstor: device scan complete
[   12.871628] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   12.871756] Bad LUN (0:1)
[   12.871943] Bad target number (1:0)
[   12.872076] Bad target number (2:0)
[   12.872203] Bad target number (3:0)
[   12.872328] Bad target number (4:0)
[   12.872453] Bad target number (5:0)
[   12.872576] Bad target number (6:0)
[   12.872700] Bad target number (7:0)
[   12.873342] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   12.873671] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   13.036954] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.037106] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   13.037185] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   13.556739] type=1400 audit(1338994743.563:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=546 comm="apparmor_parser"
[   13.557002] type=1400 audit(1338994743.563:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=547 comm="apparmor_parser"
[   13.557031] type=1400 audit(1338994743.563:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=695 comm="apparmor_parser"
[   13.557926] type=1400 audit(1338994743.563:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=546 comm="apparmor_parser"
[   13.558614] type=1400 audit(1338994743.567:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=546 comm="apparmor_parser"
[   13.558641] type=1400 audit(1338994743.567:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=695 comm="apparmor_parser"
[   13.558670] type=1400 audit(1338994743.567:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=547 comm="apparmor_parser"
[   13.559539] type=1400 audit(1338994743.567:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=695 comm="apparmor_parser"
[   13.559572] type=1400 audit(1338994743.567:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=547 comm="apparmor_parser"
[   14.025891] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   14.026129] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.026420] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.026685] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.151345] init: failsafe main process (741) killed by TERM signal
[   16.236859] ppdev: user-space parallel port driver
[   16.763077] type=1400 audit(1338994746.775:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=846 comm="apparmor_parser"
[   16.954892] Bluetooth: Core ver 2.16
[   16.954933] NET: Registered protocol family 31
[   16.954938] Bluetooth: HCI device and connection manager initialized
[   16.954945] Bluetooth: HCI socket layer initialized
[   16.954949] Bluetooth: L2CAP socket layer initialized
[   16.954961] Bluetooth: SCO socket layer initialized
[   16.987899] Bluetooth: RFCOMM TTY layer initialized
[   16.987916] Bluetooth: RFCOMM socket layer initialized
[   16.987921] Bluetooth: RFCOMM ver 1.11
[   17.118417] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.118426] Bluetooth: BNEP filters: protocol multicast
[   18.565762] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.569249] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.961047] r8169 0000:02:00.0: eth0: link down
[   18.961093] r8169 0000:02:00.0: eth0: link down
[   18.961450] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.962709] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.048984] audit_printk_skb: 3 callbacks suppressed
[   19.048994] type=1400 audit(1338994749.063:13): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=900 comm="apparmor_parser"
[   19.050394] type=1400 audit(1338994749.067:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=900 comm="apparmor_parser"
[   19.051129] type=1400 audit(1338994749.067:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=900 comm="apparmor_parser"
[   19.061483] type=1400 audit(1338994749.075:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=905 comm="apparmor_parser"
[   19.062944] type=1400 audit(1338994749.079:17): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=905 comm="apparmor_parser"
[   19.070890] type=1400 audit(1338994749.087:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=899 comm="apparmor_parser"
[   19.083529] type=1400 audit(1338994749.099:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=903 comm="apparmor_parser"
[   19.084891] type=1400 audit(1338994749.099:20): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=903 comm="apparmor_parser"
[   19.092576] type=1400 audit(1338994749.107:21): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=907 comm="apparmor_parser"
[   19.133094] type=1400 audit(1338994749.147:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=901 comm="apparmor_parser"
[   20.631953] r8169 0000:02:00.0: eth0: link up
[   20.632118] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.956333] eth0: no IPv6 routers present
[   36.911850] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   36.911860] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   36.947456] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   36.947459] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.027472] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.027483] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.101392] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   37.101403] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.243004] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.243007] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.299479] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   37.299484] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.370301] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.370311] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.455071] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   37.455074] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.526148] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.526151] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.590693] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   37.590696] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.661294] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.661304] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.737577] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   37.737588] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.808960] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.808971] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.886809] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   37.886813] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   37.957164] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   37.957168] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.024859] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.024863] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.097575] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.097585] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.161314] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.161317] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.231722] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.231732] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.295397] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.295400] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.367280] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.367283] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.428288] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.428291] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.498379] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.498390] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.563053] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.563063] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.634653] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.634657] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.692492] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.692496] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.762078] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.762088] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.829936] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.829946] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.901967] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   38.901977] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   38.969392] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   38.969395] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   39.041409] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   39.041419] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   39.109874] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[   39.109884] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[   39.180794] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[   39.180797] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[ 2410.748104] ACPI Error: No handler for Region [CMS0] (f74228d0) [SystemCMOS] (20110623/evregion-373)
[ 2410.748111] ACPI Error: Region SystemCMOS (ID=5) has no handler (20110623/exfldio-292)
[ 2410.748117] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q33] (Node f74291f8), AE_NOT_EXIST (20110623/psparse-536)

```[B]

6 ) Network configuration
sudo lshw -C network
[/B]```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 38:59:f9:6d:27:6a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c2500000-c250ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 10:1f:74:ca:66:30
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.73 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff

```[B]

7 ) Scan for networks
iwlist scan
[/B]```

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:F7:8E:B0:DF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000027f244bead6
                    Extra: Last beacon: 9332ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000

eth0      Interface doesn't support scanning.

```[B]

8 ) Ubuntu Version: 
lsb_release -d
[/B]```

Description:    Ubuntu 12.04 LTS

```[B]9 ) Kernel/architecture (including 32 vs. 64 bit):
uname -mr
[/B]```

3.2.0-24-generic-pae i686

```[B]

10 ) Restarting the network:
sudo /etc/init.d/networking restart
[/B]```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```I have been searching for a solution since February, tried 5 different distros, always the same story. Detects the WiFi card, but cannot connect to anything. The card is not hard/soft blocked.

Any suggestions?

Kind regards,
Bjarki.

---

### Post by BjarkiJod on 2012-06-06
I was connected to the internet with a cable when these commands were performed.

---

### Post by praseodym on 2012-06-06
Hi,

obviously its not a Ubuntu problem, if it occurs with several distros. Check, if the router firmware is up-to-date and/or if a MAC-filter is activated in your router interface.

BTW: Try pure WPA2-AES (CCMP) encryption in your wifi, thats more stable and more secure.

---

### Post by BjarkiJod on 2012-06-06
Thank you for your reply praseodym.

I know this is not a Ubuntu problem, but a compatibility issue between linux distros and AR9285 - or in my case at least.

However I don't think this has anything to do with the router settings, as it does not matter where I am. The same thing happens when I go over to a friend's house and try to connect over there.

I was wondering if anyone knew of a solution/tweak that could solve this problem.
[]("http://ubuntuforums.org/member.php?u=1411497")

---

### Post by praseodym on 2012-06-06
The other distros also have kernel 3.x? Deactivate the hardware encryption of the driver, most of the time this helps:
> 
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

---

### Post by BjarkiJod on 2012-06-06
Thanks again for your swift replies praseodym.

I disabled the hardware encryption, rebooted, but can still only see one WiFi connection.

I have tried Ubuntu 10.04 and 12.04, Linux Mint 12 and 13, Fedora 16 and 17, and OpenSUSE 12.1. Most of them having kernel 3.x.

---

### Post by praseodym on 2012-06-06
Which channel do you use? Please show

> iwlist chan
sudo iwlist scan
rfkill list
dmesg | grep country
Tried a fixed channel, e.g. 1 or 6? Router-reset?

---

### Post by BjarkiJod on 2012-06-06
iwlist chan
```

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.

```

sudo iwlist scan
```

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:F7:8E:B0:DF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028475cf12a7
                    Extra: Last beacon: 704ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9C0050F204104A00011010440001021041000100103B00010310470010000000000000000110000013F78EB0DF1021001242656C6B696E20436F72706F726174696F6E1023000C534D435742523134532D4E3210240007302E30302E30391042000A4A3734313432363136381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
          Cell 02 - Address: 00:1D:68:E0:FF:DF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"SpeedTouchFDCF2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002725eb4c245
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 00105370656564546F756368464443463244
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

```

rfkill list
```

1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

'dmesg | grep country' does not return anything.

---

### Post by praseodym on 2012-06-06
One of these 2 networks is yours? Try channel 1 plus pure WPA2-AES encryption, mixed encryption (like shown here) causes troubles.

For the number of channels:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE [COLOR="Red"]#DE for Germany, replace it with your country code[/COLOR]
iw reg get
```
Check after all changes:

```
iwlist chan
iwconfig
cat /etc/resolv.conf
route -n
sudo iwlist scan
```
Maybe strange charcters in the Key? How many letter-figure combinations does the key have? For WPA2-AES it should be at least 8

---

### Post by BjarkiJod on 2012-06-06
iwlist chan
```

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.

```

iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search lan

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:F7:8E:B0:DF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"SMC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002849e367114
                    Extra: Last beacon: 708ms ago
                    IE: Unknown: 0003534D43
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9C0050F204104A00011010440001021041000100103B00010310470010000000000000000110000013F78EB0DF1021001242656C6B696E20436F72706F726174696F6E1023000C534D435742523134532D4E3210240007302E30302E30391042000A4A3734313432363136381054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000100000000000000000000000000000000000000
          Cell 02 - Address: 00:1D:68:E0:FF:DF
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SpeedTouchFDCF2D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000272871b133e
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 00105370656564546F756368464443463244
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00

eth0      Interface doesn't support scanning.

```

Neither of those connections are the ones that I am trying to connect to. I guess they belong to the neighbours :)

---

### Post by praseodym on 2012-06-06
Uninstall the package "resolvconf", it doesnt work properly:

```
sudo apt-get remove --purge resolvconf
sudo /etc/init.d/networking restart
```
Check:
```
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by BjarkiJod on 2012-06-06
Removed and rebooted.

cat /etc/resolv.conf
```
# Generated by NetworkManager
domain lan
search lan
nameserver 127.0.0.1

```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

Still only the one WiFi connection.

---

### Post by praseodym on 2012-06-06
Change in the networkmanager->wireless->IPv4-settings to "Automatic (DHCP), addresses only" and add
> 
8.8.8.8, 8.8.4.4

in "DNS-servers". Restart the network.

---

### Post by BjarkiJod on 2012-06-06
But I am not connected to a WiFi connection, I'm using a cable right now. So I cannot access a WiFi connection in order to change the settings.

---

### Post by praseodym on 2012-06-06
Did you setup a wireless connection there? If yes, you can change the settings.

In most Linux systems wired is always preferred. Try to connect without cable.

---

### Post by BjarkiJod on 2012-06-06
I have not been able to set up a wireless connection because the NetworkManager cannot find my home-network. That's why I'm using a cable right now :)

---

### Post by CPL2010 on 2012-06-26
Atheros AR9285.

There are three ways to fix this under any linux distro and even windows distros (same buggy nonsense on the windows side of the world I'm afraid).

First and best way

1)  Remove Atheros 9285 miniwan adapter from the disposable HP or Acer laptop and throw it away.
2)  Go buy anything but Atheros AR9285 (ath9k) and put it in the miniwan port pci slot in the laptop or get a usb wireless adapter.  Save yourself the annoyance by spending 20 bucks.

Second way - for the cheap disposable laptops.

1)  change the boot priority to have the laptop boot from network first and if it's an AMD CPU C50 or E850...disable the second core in the BIOS.  Update your BIOS btw, the one out of the box on the walmart disposables are out of date by at least 5 years.
2)  Remove that god awful crap network manager for gnome and start the network service in the startup and not under gnome.
3)  Plus the stuff other folks mentioned in here.  The wireless will connect and drop once a minute, but hey, it's "working".

Third way - for those with the atheros XP drivers handy.
1)  install WINE and ndiswrapper, uninstall ALL old wireless managers
2)  use XP drivers to manage Atheros wireless.
3)  edit XP setting to boost range and antenna strength to 


Otherwise.  The usual stuff to boost wireless performance is also there.

Move the wireless router to another channel other than the default of 6, which phones, cell phones, Home security system and practically everything sit on.

For improvements in speed of browsing.  

First step.  Turn on the firewall which is disabled by default in ubuntu.
second step.  Install FasterFox and put it on Optimized.
third step.  Disable everything IPv6, it's garbage and DOA after it left the IEEE.  it's nice we have more IP addresses nobody cares about or manages, but it slows things down to a crawl.  it's garbage tech, disable it in everyway possible.
Fourth step.  Turn on your Router Firewall, most vendors ship routers with nothing enabled.

My favorite thign to do for teh ATH9K series of anything though is take it out of the device and throw it away then replace it.  It's cheap junk, don't let it drive you crazy anymore than it has.

---

### Post by leunam12 on 2012-12-03
Ha, I get better performance with a USB wireless adapter that I bought at a garage sale for $0.50 than with the Atheros AR9285. Now I can see my home networks and I can have internet from my bedroom

---

