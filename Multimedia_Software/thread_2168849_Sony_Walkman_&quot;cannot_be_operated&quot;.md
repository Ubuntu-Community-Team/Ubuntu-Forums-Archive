---
title: "Sony Walkman &quot;cannot be operated&quot;"
date: 2013-08-19
forum: Multimedia Software
---

### Post by dovah on 2013-08-19
Hello everybody!
I've got an issue with my Sony Walkman player (it worked well before a recent update, in ubuntu LTS), it displays "Connected usb-The player cannot be operated", it seems mounted but when I try to transfert some mp3s it won't respond and the window closes.

Here is the output  dmesg before attaching the device: ```
[    0.814178] NET: Registered protocol family 10
[    0.814586] NET: Registered protocol family 17
[    0.814591] Registering the dns_resolver key type
[    0.814799] PM: Hibernation image not present or could not be loaded.
[    0.814814] registered taskstats version 1
[    0.821702]   Magic number: 9:476:894
[    0.821795] rtc_cmos 00:06: setting system clock to 2013-08-19 16:53:08 UTC (1376931188)
[    0.822236] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.822239] EDD information not available.
[    0.847711] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.074172] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.076338] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.077807] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.077816] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.086168] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.131242] ata1.00: ATA-8: TOSHIBA MQ01ABD050, AX002J, max UDMA/100
[    1.131250] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.132594] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.132926] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.132935] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.134332] ata1.00: configured for UDMA/100
[    1.134606] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD0 AX00 PQ: 0 ANSI: 5
[    1.134750] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.134756] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.134759] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.134814] sd 0:0:0:0: [sda] Write Protect is off
[    1.134817] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.134879] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.218748] hub 1-1:1.0: USB hub found
[    1.218814] hub 1-1:1.0: 4 ports detected
[    1.247797]  sda: sda1 sda2 < sda5 >
[    1.248500] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.250060] Freeing unused kernel memory: 924k freed
[    1.250212] Write protecting the kernel read-only data: 12288k
[    1.255539] Freeing unused kernel memory: 1592k freed
[    1.259698] Freeing unused kernel memory: 1188k freed
[    1.284139] udevd[107]: starting version 175
[    1.330084] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.347376] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.347398] r8169 0000:03:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.347435] r8169 0000:03:00.2: (unregistered net_device): unknown MAC, using family default
[    1.347452] r8169 0000:03:00.2: setting latency timer to 64
[    1.347544] r8169 0000:03:00.2: irq 42 for MSI/MSI-X
[    1.347936] r8169 0000:03:00.2: eth0: RTL8168b/8111b at 0xffffc9000061e000, 50:46:5d:49:da:6b, XID 08800800 IRQ 42
[    1.347940] r8169 0000:03:00.2: eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[    1.462908] hub 2-1:1.0: USB hub found
[    1.462972] hub 2-1:1.0: 4 ports detected
[    1.574040] hub 3-0:1.0: unable to enumerate USB device on port 1
[    1.601995] Refined TSC clocksource calibration: 1795.920 MHz.
[    1.602005] Switching to clocksource tsc
[    1.646054] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[    1.729820] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.081919] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[    2.786325] Initializing USB Mass Storage driver...
[    2.786485] scsi4 : usb-storage 4-1:1.0
[    2.786559] usbcore: registered new interface driver usb-storage
[    2.786561] USB Mass Storage support registered.
[    3.785789] scsi 4:0:0:0: Direct-Access     Seagate  Expansion        0608 PQ: 0 ANSI: 6
[    3.786292] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    3.786468] sd 4:0:0:0: [sdb] 976773167 512-byte logical blocks: (500 GB/465 GiB)
[    3.786834] sd 4:0:0:0: [sdb] Write Protect is off
[    3.786837] sd 4:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[    3.787203] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.788885]  sdb: sdb1
[    3.790074] sd 4:0:0:0: [sdb] Attached SCSI disk
[    9.983143] Adding 4073468k swap on /dev/sda5.  Priority:-1 extents:1 across:4073468k 
[    9.993416] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.024450] udevd[420]: starting version 175
[   10.056067] lp: driver loaded but no devices found
[   10.090135] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.093490] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.093499] mei 0000:00:16.0: setting latency timer to 64
[   10.093570] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   10.119570] [drm] Initialized drm 1.1.0 20060810
[   10.147739] Initializing Realtek PCIE storage driver...
[   10.147758] --- 23:42:54 ---
[   10.147776] rts_bpp 0000:03:00.0: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[   10.151280] Resource length: 0x10000
[   10.151350] Original address: 0xf7c00000, remapped address: 0xffffc900050c0000
[   10.151354] pci->irq = 16
[   10.151357] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[   10.151372] rts_bpp 0000:03:00.0: setting latency timer to 64
[   10.158327] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.168220] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.168226] i915 0000:00:02.0: setting latency timer to 64
[   10.191381] scsi5 : SCSI emulation for Realtek BarossaPlusPlus card reader
[   10.282717] wmi: Mapper loaded
[   10.306572] rts_bpp: waiting for device to settle before scanning
[   10.410692] cfg80211: Calling CRDA to update world regulatory domain
[   10.472170] Bluetooth: Core ver 2.16
[   10.472192] NET: Registered protocol family 31
[   10.472194] Bluetooth: HCI device and connection manager initialized
[   10.472197] Bluetooth: HCI socket layer initialized
[   10.472199] Bluetooth: L2CAP socket layer initialized
[   10.472205] Bluetooth: SCO socket layer initialized
[   10.473045] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   10.473051] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.473053] [drm] Driver supports precise vblank timestamp query.
[   10.473090] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.480152] Bluetooth: RFCOMM TTY layer initialized
[   10.480158] Bluetooth: RFCOMM socket layer initialized
[   10.480161] Bluetooth: RFCOMM ver 1.11
[   10.484428] ppdev: user-space parallel port driver
[   10.543747] type=1400 audit(1376931198.224:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=847 comm="apparmor_parser"
[   10.544307] type=1400 audit(1376931198.224:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=847 comm="apparmor_parser"
[   10.575425] type=1400 audit(1376931198.256:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=858 comm="apparmor_parser"
[   10.575905] type=1400 audit(1376931198.256:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
[   10.576186] type=1400 audit(1376931198.256:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
[   10.582856] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.582860] Bluetooth: BNEP filters: protocol multicast
[   10.665627] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.665643] ath9k 0000:02:00.0: setting latency timer to 64
[   10.694078] ath: EEPROM regdomain: 0x60
[   10.694081] ath: EEPROM indicates we should expect a direct regpair map
[   10.694085] ath: Country alpha2 being used: 00
[   10.694087] ath: Regpair used: 0x60
[   10.722203] asus_wmi: ASUS WMI generic driver loaded
[   10.723677] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.723681] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723684] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.723687] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723690] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.723693] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723695] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.723698] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723700] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.723703] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723706] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.723709] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723711] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.723714] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723716] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.723719] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723722] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.723725] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723727] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.723730] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723732] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.723735] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723737] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.723740] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723743] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.723746] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723748] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.723753] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.724283] asus_wmi: Initialization: 0x1
[   10.724322] asus_wmi: BIOS WMI version: 7.9
[   10.724366] asus_wmi: SFUN value: 0x4a0877
[   10.736297] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
[   10.736361] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.788004] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.788009] cfg80211: World regulatory domain updated:
[   10.788011] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.788014] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.788017] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.788019] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.788022] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.788025] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.794975] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.795903] Registered led device: ath9k-phy0
[   10.795912] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90015a00000, irq=17
[   10.802021] Linux video capture interface: v2.00
[   10.805049] uvcvideo: Found UVC 1.00 device USB Camera (13d3:5165)
[   10.819558] init: failsafe main process (912) killed by TERM signal
[   10.852873] input: USB Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[   10.854052] usbcore: registered new interface driver uvcvideo
[   10.854056] USB Video Class driver (1.1.1)
[   10.877254] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   10.877989] asus_wmi: Backlight controlled by ACPI video driver
[   10.891116] psmouse serio4: elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.
[   10.946964] type=1400 audit(1376931198.624:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1038 comm="apparmor_parser"
[   10.952434] type=1400 audit(1376931198.632:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1038 comm="apparmor_parser"
[   10.952708] type=1400 audit(1376931198.632:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1038 comm="apparmor_parser"
[   10.953165] type=1400 audit(1376931198.632:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1037 comm="apparmor_parser"
[   10.953563] type=1400 audit(1376931198.632:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1037 comm="apparmor_parser"
[   10.962597] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input6
[   11.004953] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.005680] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.020079] r8169 0000:03:00.2: eth0: link down
[   11.020479] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.020945] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.173728] init: alsa-restore main process (1100) terminated with status 19
[   11.193869] fbcon: inteldrmfb (fb0) is primary device
[   11.195106] Console: switching to colour frame buffer device 170x48
[   11.195133] fb0: inteldrmfb frame buffer device
[   11.195136] drm: registered panic notifier
[   11.209185] ACPI Error: Current brightness invalid (20110623/video-384)
[   11.223222] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   11.223316] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.223620] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.223672] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.223754] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   11.223787] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   11.303040] rts_bpp: device scan complete
[   11.303160] scsi 5:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   11.303192] Bad LUN (0:1)
[   11.303260] Bad target number (1:0)
[   11.303320] Bad target number (2:0)
[   11.303360] Bad target number (3:0)
[   11.303396] Bad target number (4:0)
[   11.303431] Bad target number (5:0)
[   11.303464] Bad target number (6:0)
[   11.303499] Bad target number (7:0)
[   11.304493] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   11.306467] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   11.789798] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
[   11.789976] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.791050] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.804223] vboxdrv: Found 2 processor cores.
[   11.804537] vboxdrv: fAsync=0 offMin=0x1dc offMax=0xa74
[   11.804597] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   11.804599] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   11.821203] vboxpci: IOMMU not found (not registered)
[   12.148638] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15000000, was 12060000
[   12.262441] init: plymouth-stop pre-start process (1395) terminated with status 1
[   12.478718] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   13.830174] wlan0: authenticate with 7c:03:d8:b0:01:be (try 1)
[   13.832625] wlan0: authenticated
[   13.859701] wlan0: associate with 7c:03:d8:b0:01:be (try 1)
[   13.865575] wlan0: RX AssocResp from 7c:03:d8:b0:01:be (capab=0x431 status=0 aid=5)
[   13.865580] wlan0: associated
[   13.870721] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.871098] cfg80211: Calling CRDA for country: FR
[   13.875423] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.875429] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875431] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.875435] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875437] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.875440] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875442] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.875445] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875448] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.875451] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875453] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.875456] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875458] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.875461] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875463] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.875466] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875469] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.875472] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875474] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.875477] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875479] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.875482] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875484] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.875487] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875490] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.875493] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875495] cfg80211: Disabling freq 2484 MHz
[   13.875500] cfg80211: Regulatory domain changed to country: FR
[   13.875502] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.875504] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.875507] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.875509] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.875512] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   23.930872] wlan0: no IPv6 routers present
[   32.755870] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[  224.486468] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 15000000
[ 6956.970042] usb 3-2: new high-speed USB device number 3 using xhci_hcd
[ 6956.988601] scsi6 : usb-storage 3-2:1.0
[ 6957.986555] scsi 6:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 6957.992648] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 6961.000973] ready
[ 6961.001219] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.107633] sd 6:0:0:0: [sdd] Write Protect is off
[ 6961.107645] sd 6:0:0:0: [sdd] Mode Sense: 3b 00 00 00
[ 6961.217606] sd 6:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6961.219241] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.440868]  sdd: sdd1
[ 6961.440881] sdd: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 6961.441609] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.657867]  sdd: sdd1
[ 6961.657877] sdd: p1 size 17179869180 extends beyond EOD, truncated
[ 6961.661115] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.877373] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[ 6973.806420] usb 3-2: USB disconnect, device number 3
[ 6973.815205] sd 6:0:0:0: [sdd] Synchronizing SCSI cache
[ 6973.815280] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6974.036607] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 6974.308513] usb 3-2: new full-speed USB device number 5 using xhci_hcd
[ 6974.308676] usb 3-2: Device not responding to set address.
[ 6974.512592] usb 3-2: Device not responding to set address.
[ 6974.716390] usb 3-2: device not accepting address 5, error -71
[ 6974.828337] usb 3-2: new full-speed USB device number 6 using xhci_hcd
[ 6974.828500] usb 3-2: Device not responding to set address.
[ 6975.032426] usb 3-2: Device not responding to set address.
[ 6975.236217] usb 3-2: device not accepting address 6, error -71
[ 6975.348185] usb 3-2: new full-speed USB device number 7 using xhci_hcd
[ 6975.348314] usb 3-2: Device not responding to set address.
[ 6975.552260] usb 3-2: Device not responding to set address.
[ 6975.756049] usb 3-2: device not accepting address 7, error -71
[ 6975.868023] usb 3-2: new full-speed USB device number 8 using xhci_hcd
[ 6975.868179] usb 3-2: Device not responding to set address.
[ 6976.072104] usb 3-2: Device not responding to set address.
[ 6976.275867] usb 3-2: device not accepting address 8, error -71
[ 6976.275926] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 6987.908204] usb 3-2: new full-speed USB device number 9 using xhci_hcd
[ 6987.924839] usb 3-2: not running at top speed; connect to a high speed hub
[ 6987.927462] scsi7 : usb-storage 3-2:1.0
[ 6988.357998] usb 3-2: USB disconnect, device number 9
[ 6988.627966] usb 3-2: new full-speed USB device number 10 using xhci_hcd
[ 6988.644624] usb 3-2: not running at top speed; connect to a high speed hub
[ 6988.647718] scsi8 : usb-storage 3-2:1.0
[ 6988.701884] usb 3-2: USB disconnect, device number 10
[ 6989.099801] usb 3-2: new full-speed USB device number 11 using xhci_hcd
[ 6989.099838] usb 3-2: Device not responding to set address.
[ 6989.303795] usb 3-2: Device not responding to set address.
[ 6989.507683] usb 3-2: device not accepting address 11, error -71
[ 6989.563700] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 6990.995211] usb 3-2: new high-speed USB device number 13 using xhci_hcd
[ 6991.013606] scsi9 : usb-storage 3-2:1.0
[ 6991.526910] usb 3-2: USB disconnect, device number 13
[ 7171.695752] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
[ 7171.699242] WARNING! power/level is deprecated; use power/control instead
[ 7172.137658] usb 4-1: USB disconnect, device number 2
[ 7172.553683] usb 4-1: new SuperSpeed USB device number 3 using xhci_hcd
[ 7172.573528] scsi10 : usb-storage 4-1:1.0
[ 7173.697110] usb 4-1: USB disconnect, device number 3
[ 7216.959376] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 7217.259244] usb 3-2: new full-speed USB device number 15 using xhci_hcd
[ 7217.275942] usb 3-2: not running at top speed; connect to a high speed hub
[ 7217.278597] scsi11 : usb-storage 3-2:1.0
[ 7218.275899] scsi 11:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 7218.277499] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 7219.286834] ready
[ 7219.287077] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7219.393943] sd 11:0:0:0: [sdb] Write Protect is off
[ 7219.393954] sd 11:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 7219.503884] sd 11:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7219.506891] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7219.727647]  sdb: sdb1
[ 7219.727660] sdb: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 7219.728269] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7219.947441]  sdb: sdb1
[ 7219.947452] sdb: p1 size 17179869180 extends beyond EOD, truncated
[ 7219.949198] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7220.163633] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 7280.655077] usb 3-2: USB disconnect, device number 15
[ 7280.661855] sd 11:0:0:0: [sdb] Synchronizing SCSI cache
[ 7280.661933] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 7296.250146] usb 3-2: new high-speed USB device number 16 using xhci_hcd
[ 7296.268927] scsi12 : usb-storage 3-2:1.0
[ 7297.266700] scsi 12:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 7297.268222] sd 12:0:0:0: Attached scsi generic sg1 type 0
[ 7298.277709] ready
[ 7298.278028] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7298.385194] sd 12:0:0:0: [sdb] Write Protect is off
[ 7298.385205] sd 12:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 7298.495131] sd 12:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7298.496753] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7298.715520]  sdb: sdb1
[ 7298.715533] sdb: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 7298.716333] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7298.935392]  sdb: sdb1
[ 7298.935403] sdb: p1 size 17179869180 extends beyond EOD, truncated
[ 7298.937805] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7299.154904] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 7693.599825] usb 3-2: USB disconnect, device number 16
[ 7693.608280] sd 12:0:0:0: [sdb] Synchronizing SCSI cache
[ 7693.608371] sd 12:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 7693.879700] usb 3-2: new full-speed USB device number 17 using xhci_hcd
[ 7693.879857] usb 3-2: Device not responding to set address.
[ 7694.083621] usb 3-2: Device not responding to set address.
[ 7694.287540] usb 3-2: device not accepting address 17, error -71
[ 7694.343544] hub 3-0:1.0: unable to enumerate USB device on port 2
dovah@Asus-X501A:~$ 
```

and after: ```
[    1.218814] hub 1-1:1.0: 4 ports detected
[    1.247797]  sda: sda1 sda2 < sda5 >
[    1.248500] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.250060] Freeing unused kernel memory: 924k freed
[    1.250212] Write protecting the kernel read-only data: 12288k
[    1.255539] Freeing unused kernel memory: 1592k freed
[    1.259698] Freeing unused kernel memory: 1188k freed
[    1.284139] udevd[107]: starting version 175
[    1.330084] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.347376] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.347398] r8169 0000:03:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.347435] r8169 0000:03:00.2: (unregistered net_device): unknown MAC, using family default
[    1.347452] r8169 0000:03:00.2: setting latency timer to 64
[    1.347544] r8169 0000:03:00.2: irq 42 for MSI/MSI-X
[    1.347936] r8169 0000:03:00.2: eth0: RTL8168b/8111b at 0xffffc9000061e000, 50:46:5d:49:da:6b, XID 08800800 IRQ 42
[    1.347940] r8169 0000:03:00.2: eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[    1.462908] hub 2-1:1.0: USB hub found
[    1.462972] hub 2-1:1.0: 4 ports detected
[    1.574040] hub 3-0:1.0: unable to enumerate USB device on port 1
[    1.601995] Refined TSC clocksource calibration: 1795.920 MHz.
[    1.602005] Switching to clocksource tsc
[    1.646054] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[    1.729820] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.081919] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[    2.786325] Initializing USB Mass Storage driver...
[    2.786485] scsi4 : usb-storage 4-1:1.0
[    2.786559] usbcore: registered new interface driver usb-storage
[    2.786561] USB Mass Storage support registered.
[    3.785789] scsi 4:0:0:0: Direct-Access     Seagate  Expansion        0608 PQ: 0 ANSI: 6
[    3.786292] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    3.786468] sd 4:0:0:0: [sdb] 976773167 512-byte logical blocks: (500 GB/465 GiB)
[    3.786834] sd 4:0:0:0: [sdb] Write Protect is off
[    3.786837] sd 4:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[    3.787203] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.788885]  sdb: sdb1
[    3.790074] sd 4:0:0:0: [sdb] Attached SCSI disk
[    9.983143] Adding 4073468k swap on /dev/sda5.  Priority:-1 extents:1 across:4073468k 
[    9.993416] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.024450] udevd[420]: starting version 175
[   10.056067] lp: driver loaded but no devices found
[   10.090135] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.093490] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.093499] mei 0000:00:16.0: setting latency timer to 64
[   10.093570] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   10.119570] [drm] Initialized drm 1.1.0 20060810
[   10.147739] Initializing Realtek PCIE storage driver...
[   10.147758] --- 23:42:54 ---
[   10.147776] rts_bpp 0000:03:00.0: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[   10.151280] Resource length: 0x10000
[   10.151350] Original address: 0xf7c00000, remapped address: 0xffffc900050c0000
[   10.151354] pci->irq = 16
[   10.151357] rtsx_acquire_irq: chip->msi_en = 0, pci->irq = 16
[   10.151372] rts_bpp 0000:03:00.0: setting latency timer to 64
[   10.158327] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.168220] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.168226] i915 0000:00:02.0: setting latency timer to 64
[   10.191381] scsi5 : SCSI emulation for Realtek BarossaPlusPlus card reader
[   10.282717] wmi: Mapper loaded
[   10.306572] rts_bpp: waiting for device to settle before scanning
[   10.410692] cfg80211: Calling CRDA to update world regulatory domain
[   10.472170] Bluetooth: Core ver 2.16
[   10.472192] NET: Registered protocol family 31
[   10.472194] Bluetooth: HCI device and connection manager initialized
[   10.472197] Bluetooth: HCI socket layer initialized
[   10.472199] Bluetooth: L2CAP socket layer initialized
[   10.472205] Bluetooth: SCO socket layer initialized
[   10.473045] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   10.473051] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.473053] [drm] Driver supports precise vblank timestamp query.
[   10.473090] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   10.480152] Bluetooth: RFCOMM TTY layer initialized
[   10.480158] Bluetooth: RFCOMM socket layer initialized
[   10.480161] Bluetooth: RFCOMM ver 1.11
[   10.484428] ppdev: user-space parallel port driver
[   10.543747] type=1400 audit(1376931198.224:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=847 comm="apparmor_parser"
[   10.544307] type=1400 audit(1376931198.224:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=847 comm="apparmor_parser"
[   10.575425] type=1400 audit(1376931198.256:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=858 comm="apparmor_parser"
[   10.575905] type=1400 audit(1376931198.256:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
[   10.576186] type=1400 audit(1376931198.256:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
[   10.582856] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.582860] Bluetooth: BNEP filters: protocol multicast
[   10.665627] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.665643] ath9k 0000:02:00.0: setting latency timer to 64
[   10.694078] ath: EEPROM regdomain: 0x60
[   10.694081] ath: EEPROM indicates we should expect a direct regpair map
[   10.694085] ath: Country alpha2 being used: 00
[   10.694087] ath: Regpair used: 0x60
[   10.722203] asus_wmi: ASUS WMI generic driver loaded
[   10.723677] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.723681] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723684] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.723687] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723690] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.723693] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723695] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.723698] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723700] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.723703] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723706] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   10.723709] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723711] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   10.723714] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723716] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   10.723719] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723722] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   10.723725] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723727] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   10.723730] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723732] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   10.723735] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723737] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   10.723740] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723743] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   10.723746] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.723748] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   10.723753] cfg80211: 2474000 KHz - 2494000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   10.724283] asus_wmi: Initialization: 0x1
[   10.724322] asus_wmi: BIOS WMI version: 7.9
[   10.724366] asus_wmi: SFUN value: 0x4a0877
[   10.736297] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input4
[   10.736361] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.788004] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   10.788009] cfg80211: World regulatory domain updated:
[   10.788011] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.788014] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.788017] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.788019] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.788022] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.788025] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.794975] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.795903] Registered led device: ath9k-phy0
[   10.795912] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90015a00000, irq=17
[   10.802021] Linux video capture interface: v2.00
[   10.805049] uvcvideo: Found UVC 1.00 device USB Camera (13d3:5165)
[   10.819558] init: failsafe main process (912) killed by TERM signal
[   10.852873] input: USB Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[   10.854052] usbcore: registered new interface driver uvcvideo
[   10.854056] USB Video Class driver (1.1.1)
[   10.877254] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   10.877989] asus_wmi: Backlight controlled by ACPI video driver
[   10.891116] psmouse serio4: elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.
[   10.946964] type=1400 audit(1376931198.624:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1038 comm="apparmor_parser"
[   10.952434] type=1400 audit(1376931198.632:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1038 comm="apparmor_parser"
[   10.952708] type=1400 audit(1376931198.632:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1038 comm="apparmor_parser"
[   10.953165] type=1400 audit(1376931198.632:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1037 comm="apparmor_parser"
[   10.953563] type=1400 audit(1376931198.632:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1037 comm="apparmor_parser"
[   10.962597] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input6
[   11.004953] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.005680] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.020079] r8169 0000:03:00.2: eth0: link down
[   11.020479] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.020945] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.173728] init: alsa-restore main process (1100) terminated with status 19
[   11.193869] fbcon: inteldrmfb (fb0) is primary device
[   11.195106] Console: switching to colour frame buffer device 170x48
[   11.195133] fb0: inteldrmfb frame buffer device
[   11.195136] drm: registered panic notifier
[   11.209185] ACPI Error: Current brightness invalid (20110623/video-384)
[   11.223222] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   11.223316] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.223620] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.223672] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.223754] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   11.223787] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   11.303040] rts_bpp: device scan complete
[   11.303160] scsi 5:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   11.303192] Bad LUN (0:1)
[   11.303260] Bad target number (1:0)
[   11.303320] Bad target number (2:0)
[   11.303360] Bad target number (3:0)
[   11.303396] Bad target number (4:0)
[   11.303431] Bad target number (5:0)
[   11.303464] Bad target number (6:0)
[   11.303499] Bad target number (7:0)
[   11.304493] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   11.306467] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[   11.789798] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
[   11.789976] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.791050] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   11.804223] vboxdrv: Found 2 processor cores.
[   11.804537] vboxdrv: fAsync=0 offMin=0x1dc offMax=0xa74
[   11.804597] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   11.804599] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   11.821203] vboxpci: IOMMU not found (not registered)
[   12.148638] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15000000, was 12060000
[   12.262441] init: plymouth-stop pre-start process (1395) terminated with status 1
[   12.478718] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   13.830174] wlan0: authenticate with 7c:03:d8:b0:01:be (try 1)
[   13.832625] wlan0: authenticated
[   13.859701] wlan0: associate with 7c:03:d8:b0:01:be (try 1)
[   13.865575] wlan0: RX AssocResp from 7c:03:d8:b0:01:be (capab=0x431 status=0 aid=5)
[   13.865580] wlan0: associated
[   13.870721] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.871098] cfg80211: Calling CRDA for country: FR
[   13.875423] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   13.875429] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875431] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   13.875435] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875437] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   13.875440] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875442] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   13.875445] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875448] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   13.875451] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875453] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   13.875456] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875458] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   13.875461] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875463] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   13.875466] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875469] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   13.875472] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875474] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   13.875477] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875479] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   13.875482] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875484] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   13.875487] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875490] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   13.875493] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   13.875495] cfg80211: Disabling freq 2484 MHz
[   13.875500] cfg80211: Regulatory domain changed to country: FR
[   13.875502] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.875504] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.875507] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.875509] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.875512] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   23.930872] wlan0: no IPv6 routers present
[   32.755870] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[  224.486468] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 000d0000, was 15000000
[ 6956.970042] usb 3-2: new high-speed USB device number 3 using xhci_hcd
[ 6956.988601] scsi6 : usb-storage 3-2:1.0
[ 6957.986555] scsi 6:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 6957.992648] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 6961.000973] ready
[ 6961.001219] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.107633] sd 6:0:0:0: [sdd] Write Protect is off
[ 6961.107645] sd 6:0:0:0: [sdd] Mode Sense: 3b 00 00 00
[ 6961.217606] sd 6:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 6961.219241] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.440868]  sdd: sdd1
[ 6961.440881] sdd: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 6961.441609] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.657867]  sdd: sdd1
[ 6961.657877] sdd: p1 size 17179869180 extends beyond EOD, truncated
[ 6961.661115] sd 6:0:0:0: [sdd] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 6961.877373] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[ 6973.806420] usb 3-2: USB disconnect, device number 3
[ 6973.815205] sd 6:0:0:0: [sdd] Synchronizing SCSI cache
[ 6973.815280] sd 6:0:0:0: [sdd]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6974.036607] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 6974.308513] usb 3-2: new full-speed USB device number 5 using xhci_hcd
[ 6974.308676] usb 3-2: Device not responding to set address.
[ 6974.512592] usb 3-2: Device not responding to set address.
[ 6974.716390] usb 3-2: device not accepting address 5, error -71
[ 6974.828337] usb 3-2: new full-speed USB device number 6 using xhci_hcd
[ 6974.828500] usb 3-2: Device not responding to set address.
[ 6975.032426] usb 3-2: Device not responding to set address.
[ 6975.236217] usb 3-2: device not accepting address 6, error -71
[ 6975.348185] usb 3-2: new full-speed USB device number 7 using xhci_hcd
[ 6975.348314] usb 3-2: Device not responding to set address.
[ 6975.552260] usb 3-2: Device not responding to set address.
[ 6975.756049] usb 3-2: device not accepting address 7, error -71
[ 6975.868023] usb 3-2: new full-speed USB device number 8 using xhci_hcd
[ 6975.868179] usb 3-2: Device not responding to set address.
[ 6976.072104] usb 3-2: Device not responding to set address.
[ 6976.275867] usb 3-2: device not accepting address 8, error -71
[ 6976.275926] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 6987.908204] usb 3-2: new full-speed USB device number 9 using xhci_hcd
[ 6987.924839] usb 3-2: not running at top speed; connect to a high speed hub
[ 6987.927462] scsi7 : usb-storage 3-2:1.0
[ 6988.357998] usb 3-2: USB disconnect, device number 9
[ 6988.627966] usb 3-2: new full-speed USB device number 10 using xhci_hcd
[ 6988.644624] usb 3-2: not running at top speed; connect to a high speed hub
[ 6988.647718] scsi8 : usb-storage 3-2:1.0
[ 6988.701884] usb 3-2: USB disconnect, device number 10
[ 6989.099801] usb 3-2: new full-speed USB device number 11 using xhci_hcd
[ 6989.099838] usb 3-2: Device not responding to set address.
[ 6989.303795] usb 3-2: Device not responding to set address.
[ 6989.507683] usb 3-2: device not accepting address 11, error -71
[ 6989.563700] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 6990.995211] usb 3-2: new high-speed USB device number 13 using xhci_hcd
[ 6991.013606] scsi9 : usb-storage 3-2:1.0
[ 6991.526910] usb 3-2: USB disconnect, device number 13
[ 7171.695752] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
[ 7171.699242] WARNING! power/level is deprecated; use power/control instead
[ 7172.137658] usb 4-1: USB disconnect, device number 2
[ 7172.553683] usb 4-1: new SuperSpeed USB device number 3 using xhci_hcd
[ 7172.573528] scsi10 : usb-storage 4-1:1.0
[ 7173.697110] usb 4-1: USB disconnect, device number 3
[ 7216.959376] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 7217.259244] usb 3-2: new full-speed USB device number 15 using xhci_hcd
[ 7217.275942] usb 3-2: not running at top speed; connect to a high speed hub
[ 7217.278597] scsi11 : usb-storage 3-2:1.0
[ 7218.275899] scsi 11:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 7218.277499] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 7219.286834] ready
[ 7219.287077] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7219.393943] sd 11:0:0:0: [sdb] Write Protect is off
[ 7219.393954] sd 11:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 7219.503884] sd 11:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7219.506891] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7219.727647]  sdb: sdb1
[ 7219.727660] sdb: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 7219.728269] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7219.947441]  sdb: sdb1
[ 7219.947452] sdb: p1 size 17179869180 extends beyond EOD, truncated
[ 7219.949198] sd 11:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7220.163633] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 7280.655077] usb 3-2: USB disconnect, device number 15
[ 7280.661855] sd 11:0:0:0: [sdb] Synchronizing SCSI cache
[ 7280.661933] sd 11:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 7296.250146] usb 3-2: new high-speed USB device number 16 using xhci_hcd
[ 7296.268927] scsi12 : usb-storage 3-2:1.0
[ 7297.266700] scsi 12:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 7297.268222] sd 12:0:0:0: Attached scsi generic sg1 type 0
[ 7298.277709] ready
[ 7298.278028] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7298.385194] sd 12:0:0:0: [sdb] Write Protect is off
[ 7298.385205] sd 12:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 7298.495131] sd 12:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7298.496753] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7298.715520]  sdb: sdb1
[ 7298.715533] sdb: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 7298.716333] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7298.935392]  sdb: sdb1
[ 7298.935403] sdb: p1 size 17179869180 extends beyond EOD, truncated
[ 7298.937805] sd 12:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7299.154904] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 7693.599825] usb 3-2: USB disconnect, device number 16
[ 7693.608280] sd 12:0:0:0: [sdb] Synchronizing SCSI cache
[ 7693.608371] sd 12:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 7693.879700] usb 3-2: new full-speed USB device number 17 using xhci_hcd
[ 7693.879857] usb 3-2: Device not responding to set address.
[ 7694.083621] usb 3-2: Device not responding to set address.
[ 7694.287540] usb 3-2: device not accepting address 17, error -71
[ 7694.343544] hub 3-0:1.0: unable to enumerate USB device on port 2
[ 7757.415450] usb 3-2: new high-speed USB device number 19 using xhci_hcd
[ 7757.433717] scsi13 : usb-storage 3-2:1.0
[ 7758.431932] scsi 13:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 2
[ 7758.433539] sd 13:0:0:0: Attached scsi generic sg1 type 0
[ 7759.443076] ready
[ 7759.443302] sd 13:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7759.549045] sd 13:0:0:0: [sdb] Write Protect is off
[ 7759.549056] sd 13:0:0:0: [sdb] Mode Sense: 3b 00 00 00
[ 7759.659012] sd 13:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7759.660767] sd 13:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7759.879418]  sdb: sdb1
[ 7759.879431] sdb: p1 size 17179869180 extends beyond EOD, enabling native capacity
[ 7759.880186] sd 13:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7760.099264]  sdb: sdb1
[ 7760.099274] sdb: p1 size 17179869180 extends beyond EOD, truncated
[ 7760.100821] sd 13:0:0:0: [sdb] 7435968 2048-byte logical blocks: (15.2 GB/14.1 GiB)
[ 7760.318772] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 7764.781235] usb 3-2: reset high-speed USB device number 19 using xhci_hcd
[ 7764.781319] usb 3-2: Device not responding to set address.
[ 7764.985174] usb 3-2: Device not responding to set address.
[ 7765.188990] usb 3-2: device not accepting address 19, error -71
[ 7765.245038] usb 3-2: USB disconnect, device number 19
[ 7765.257004] sd 13:0:0:0: [sdb] Synchronizing SCSI cache
[ 7765.257069] sd 13:0:0:0: [sdb]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 7765.257846] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d112d900
[ 7765.257854] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d112d940
[ 7765.257861] xhci_hcd 0000:00:14.0: xHCI xhci_drop_endpoint called with disabled ep ffff8800d112d980
dovah@Asus-X501A:~$ 
```

Thank you for your help :/

---

### Post by kostkon on 2013-08-19
Tried a different USB port?

---

### Post by dovah on 2013-08-30
Yes, I did. However, I reinstalled the system, now it works, thank you for your tip.

---

