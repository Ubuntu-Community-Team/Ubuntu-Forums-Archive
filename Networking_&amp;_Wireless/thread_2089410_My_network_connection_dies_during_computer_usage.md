---
title: "My network connection dies during computer usage"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by KhaaL on 2012-11-29
If I try to re-connect to the same or another access point, nm-manager gives me signal that it has connected successfully but I cant access the net.
I tried to use modprobe to remove and load iwlwifi back in, but then my computer goes into a hard-freeze. 

The only solution is to reboot. I tried killing Xorg, but that didn't help.

relevant output of lshw:
         *-network
                description: Wireless interface
                product: Centrino Wireless-N 1000
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 00:1e:64:10:85:cc
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-18-generic firmware=39.31.5.1 build 35138 ip=130.241.14.98 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:43 memory:d2500000-d2501fff

----------------

output of ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:26:9e:64:b4:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:296348 (296.3 KB)  TX bytes:296348 (296.3 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:33106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28386 errors:0 dropped:10667 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:31107570 (31.1 MB)  TX bytes:6440331 (6.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:10:85:cc  
          inet addr:130.241.14.98  Bcast:130.241.15.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:64ff:fe10:85cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33652530 (33.6 MB)  TX bytes:9260010 (9.2 MB)

--------------
output of dmesg when the network becomes unresponsive...
```


[    1.629252] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
[    1.629299] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.629303] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.629307] usb usb5: Product: UHCI Host Controller
[    1.629311] usb usb5: Manufacturer: Linux 3.5.0-18-generic uhci_hcd
[    1.629315] usb usb5: SerialNumber: 0000:00:1d.1
[    1.629482] hub 5-0:1.0: USB hub found
[    1.629489] hub 5-0:1.0: 2 ports detected
[    1.629601] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.629606] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.629614] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    1.629649] uhci_hcd 0000:00:1d.2: irq 16, io base 0x00003020
[    1.629694] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.629698] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.629702] usb usb6: Product: UHCI Host Controller
[    1.629706] usb usb6: Manufacturer: Linux 3.5.0-18-generic uhci_hcd
[    1.629710] usb usb6: SerialNumber: 0000:00:1d.2
[    1.629873] hub 6-0:1.0: USB hub found
[    1.629879] hub 6-0:1.0: 2 ports detected
[    1.630065] usbcore: registered new interface driver libusual
[    1.630135] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    1.633794] isapnp: No Plug & Play device found
[    1.637762] i8042: Detected active multiplexing controller, rev 1.1
[    1.641174] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.641182] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.641225] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.641267] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.641305] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.641502] mousedev: PS/2 mouse device common for all mice
[    1.641816] rtc_cmos 00:03: RTC can wake from S4
[    1.641998] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.642037] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.642118] device-mapper: uevent: version 1.0.3
[    1.642226] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.642274] EISA: Probing bus 0 at eisa.0
[    1.642277] EISA: Cannot allocate resource for mainboard
[    1.642280] Cannot allocate resource for EISA slot 1
[    1.642282] Cannot allocate resource for EISA slot 2
[    1.642285] Cannot allocate resource for EISA slot 3
[    1.642287] Cannot allocate resource for EISA slot 4
[    1.642290] Cannot allocate resource for EISA slot 5
[    1.642293] Cannot allocate resource for EISA slot 6
[    1.642295] Cannot allocate resource for EISA slot 7
[    1.642298] Cannot allocate resource for EISA slot 8
[    1.642300] EISA: Detected 0 cards.
[    1.642362] cpuidle: using governor ladder
[    1.642437] cpuidle: using governor menu
[    1.642440] EFI Variables Facility v0.08 2004-May-17
[    1.642769] ashmem: initialized
[    1.642995] TCP: cubic registered
[    1.643181] NET: Registered protocol family 10
[    1.643488] NET: Registered protocol family 17
[    1.643504] Key type dns_resolver registered
[    1.643622] Using IPI No-Shortcut mode
[    1.643803] PM: Hibernation image not present or could not be loaded.
[    1.643821] registered taskstats version 1
[    1.647657] Key type trusted registered
[    1.650984] Key type encrypted registered
[    1.654760]   Magic number: 4:294:777
[    1.654808] misc rfkill: hash matches
[    1.654885] rtc_cmos 00:03: setting system clock to 2012-11-29 08:45:50 UTC (1354178750)
[    1.655388] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.655391] EDD information not available.
[    1.662363] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.771315] ata2: SATA link down (SStatus 4 SControl 300)
[    1.931262] ata3: SATA link down (SStatus 4 SControl 300)
[    1.931353] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.942532] ata1.00: ATA-8: Hitachi HTS545032B9A300, PB3OC60F, max UDMA/133
[    1.942537] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.942566] ata4: SATA link down (SStatus 0 SControl 300)
[    1.942600] usb 2-5: new high-speed USB device number 2 using ehci_hcd
[    1.956484] ata1.00: configured for UDMA/133
[    1.956705] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54503 PB3O PQ: 0 ANSI: 5
[    1.956900] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.956941] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.956978] sd 0:0:0:0: [sda] Write Protect is off
[    1.956984] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.957025] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.014349]  sda: sda1 sda3 < sda5 sda6 >
[    2.015074] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.015227] Freeing unused kernel memory: 756k freed
[    2.015640] Write protecting the kernel text: 5964k
[    2.015681] Write protecting the kernel read-only data: 2424k
[    2.015683] NX-protecting the kernel data: 4276k
[    2.045574] udevd[101]: starting version 175
[    2.106033] usb 2-5: New USB device found, idVendor=04f2, idProduct=b175
[    2.106039] usb 2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.106044] usb 2-5: Product: CNF9011
[    2.106048] usb 2-5: Manufacturer: Chicony Electronics Co., Ltd.
[    2.106052] usb 2-5: SerialNumber: SN0001
[    2.117073] wmi: Mapper loaded
[    2.118305] [drm] Initialized drm 1.1.0 20060810
[    2.164047] i915 0000:00:02.0: setting latency timer to 64
[    2.165121] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[    2.165139] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.165141] [drm] Driver supports precise vblank timestamp query.
[    2.165196] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.196721] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[    2.864128] fbcon: inteldrmfb (fb0) is primary device
[    2.864206] Console: switching to colour frame buffer device 170x48
[    2.864260] fb0: inteldrmfb frame buffer device
[    2.864262] drm: registered panic notifier
[    2.865961] acpi device:03: registered as cooling_device2
[    2.866089] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    2.866174] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    2.866286] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.130520] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   14.196108] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[   14.339255] usb 1-1: New USB device found, idVendor=0bb4, idProduct=0ff9
[   14.339261] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[   14.339266] usb 1-1: Product: HTC
[   14.339270] usb 1-1: Manufacturer: HTC
[   14.339274] usb 1-1: SerialNumber: HT23RW118685
[   17.585302] Initializing USB Mass Storage driver...
[   17.585479] scsi4 : usb-storage 1-1:1.0
[   17.585586] usbcore: registered new interface driver usb-storage
[   17.585589] USB Mass Storage support registered.
[   18.586794] scsi 4:0:0:0: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   18.588531] scsi 4:0:0:1: CD-ROM            HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   18.589691] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   18.606251] sr0: scsi-1 drive
[   18.606255] cdrom: Uniform CD-ROM driver Revision: 3.20
[   18.606436] sr 4:0:0:1: Attached scsi CD-ROM sr0
[   18.606556] sr 4:0:0:1: Attached scsi generic sg2 type 5
[   18.608262] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   24.609356] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.649533] udevd[378]: starting version 175
[   24.681858] lp: driver loaded but no devices found
[   24.831630] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   24.842070] cfg80211: Calling CRDA to update world regulatory domain
[   24.882447] type=1400 audit(1354175173.722:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=482 comm="apparmor_parser"
[   24.883957] type=1400 audit(1354175173.722:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=482 comm="apparmor_parser"
[   24.884403] type=1400 audit(1354175173.726:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=482 comm="apparmor_parser"
[   24.921184] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   24.921190] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   24.921295] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   24.921300] iwlwifi 0000:02:00.0: pci_resource_base = f846c000
[   24.921304] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   24.921405] iwlwifi 0000:02:00.0: irq 43 for MSI/MSI-X
[   25.126528] Bluetooth: Core ver 2.16
[   25.136699] ppdev: user-space parallel port driver
[   25.141898] NET: Registered protocol family 31
[   25.141905] Bluetooth: HCI device and connection manager initialized
[   25.142373] Bluetooth: HCI socket layer initialized
[   25.142377] Bluetooth: L2CAP socket layer initialized
[   25.142993] Bluetooth: SCO socket layer initialized
[   25.167980] type=1400 audit(1354175174.006:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=668 comm="apparmor_parser"
[   25.184533] type=1400 audit(1354175174.026:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=668 comm="apparmor_parser"
[   25.219541] Bluetooth: RFCOMM TTY layer initialized
[   25.219550] Bluetooth: RFCOMM socket layer initialized
[   25.219553] Bluetooth: RFCOMM ver 1.11
[   25.258438] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.258444] Bluetooth: BNEP filters: protocol multicast
[   25.416730] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMBA 1 (20120320/utaddress-251)
[   25.416743] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.416746] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   25.416752] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20120320/utaddress-251)
[   25.416759] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.416764] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   25.416771] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.LPC_.GPIO 2 (20120320/utaddress-251)
[   25.416778] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   25.416780] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   25.427712] Linux video capture interface: v2.00
[   25.451525] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   25.487464] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
[   25.514809] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input6
[   25.515906] usbcore: registered new interface driver uvcvideo
[   25.515910] USB Video Class driver (1.1.1)
[   25.545883] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[   25.576161] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   25.576298] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   25.576412] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   25.634969] acerhdf: Acer Aspire One Fan driver, v.0.5.26
[   25.635000] acerhdf: Fan control off, to enable do:
[   25.635002] acerhdf: echo -n "enabled" > /sys/class/thermal/thermal_zone0/mode
[   25.899631] init: failsafe main process (817) killed by TERM signal
[   26.097654] type=1400 audit(1354175174.938:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=930 comm="apparmor_parser"
[   26.116327] type=1400 audit(1354175174.958:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=931 comm="apparmor_parser"
[   26.116944] type=1400 audit(1354175174.958:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=931 comm="apparmor_parser"
[   26.124132] type=1400 audit(1354175174.966:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=930 comm="apparmor_parser"
[   26.134124] acer_wmi: Acer Laptop ACPI-WMI Extras
[   26.136468] type=1400 audit(1354175174.978:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=937 comm="apparmor_parser"
[   26.161708] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[   26.161986] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   26.161990] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   26.161993] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   26.161997] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   26.162001] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   26.162005] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   26.162078] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   26.182429] iwlwifi 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   26.182436] iwlwifi 0000:02:00.0: Device SKU: 0x50
[   26.182440] iwlwifi 0000:02:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[   26.182460] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   26.188067] Registered led device: phy0-led
[   26.188133] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   26.209383] acer_wmi: Function bitmap for Communication Device: 0x10
[   26.209397] acer_wmi: Brightness must be controlled by acpi video driver
[   26.221505] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   26.223450] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   26.229787] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   26.232694] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   26.232699] cfg80211: World regulatory domain updated:
[   26.232702] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.232706] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.232709] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.232713] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.232716] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.232719] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.245743] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.250105] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   26.252384] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.271403] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[   26.278661] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   26.317187] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input11
[   26.344314] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   26.346144] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   26.411554] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.413404] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.786144] init: gdm main process (1088) killed by TERM signal
[   27.324479] wlan0: authenticate with 00:23:5e:4a:0a:60
[   27.349392] wlan0: send auth to 00:23:5e:4a:0a:60 (try 1/3)
[   27.352072] wlan0: authenticated
[   27.356065] wlan0: associate with 00:23:5e:4a:0a:60 (try 1/3)
[   27.359623] wlan0: RX AssocResp from 00:23:5e:4a:0a:60 (capab=0x431 status=0 aid=32)
[   27.362652] wlan0: associated
[   27.362953] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.363044] cfg80211: Calling CRDA for country: SE
[   27.368110] init: anacron main process (1075) killed by TERM signal
[   27.384262] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   27.384269] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384272] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   27.384276] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384279] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   27.384282] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384285] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   27.384288] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384291] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   27.384295] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384298] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   27.384301] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384304] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   27.384307] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384310] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   27.384314] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384317] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   27.384320] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384323] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   27.384326] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384329] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   27.384333] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384336] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   27.384339] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384342] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   27.384345] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   27.384349] cfg80211: Regulatory domain changed to country: SE
[   27.384352] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   27.384355] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   27.384358] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   27.384361] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   27.384364] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   27.782474] init: plymouth-stop pre-start process (1465) terminated with status 1
[   28.389611] Adding 1945596k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:1945596k 
[   50.863761] usb 1-1: USB disconnect, device number 2
[   61.668045] usb 1-1: new high-speed USB device number 3 using ehci_hcd
[   61.813105] usb 1-1: New USB device found, idVendor=0bb4, idProduct=0ff9
[   61.813112] usb 1-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[   61.813117] usb 1-1: Product: HTC
[   61.813121] usb 1-1: Manufacturer: HTC
[   61.813124] usb 1-1: SerialNumber: HT23RW118685
[   61.819041] scsi5 : usb-storage 1-1:1.0
[   62.824513] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   62.825373] scsi 5:0:0:1: CD-ROM            HTC      Android Phone    0000 PQ: 0 ANSI: 2
[   62.826321] sd 5:0:0:0: Attached scsi generic sg1 type 0
[   62.842370] sr0: scsi-1 drive
[   62.842588] sr 5:0:0:1: Attached scsi CD-ROM sr0
[   62.842724] sr 5:0:0:1: Attached scsi generic sg2 type 5
[   62.848367] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  102.451579] audit_printk_skb: 48 callbacks suppressed
[  102.451586] type=1701 audit(1354175249.847:28): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2684 comm="chromium-browse" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb2ee6424 code=0x50000
[  115.088045] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[  115.222818] usb 2-1: New USB device found, idVendor=0951, idProduct=1603
[  115.222825] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  115.222830] usb 2-1: Product: DataTraveler 2.0
[  115.222834] usb 2-1: Manufacturer: Kingston
[  115.222838] usb 2-1: SerialNumber: 000AEBFFD75BA8B1C2CF003B
[  115.223534] scsi6 : usb-storage 2-1:1.0
[  116.224583] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[  116.226059] sd 6:0:0:0: [sdc] 31506432 512-byte logical blocks: (16.1 GB/15.0 GiB)
[  116.226678] sd 6:0:0:0: [sdc] Write Protect is off
[  116.226684] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  116.227305] sd 6:0:0:0: [sdc] No Caching mode page present
[  116.227311] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  116.229702] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  116.232812] sd 6:0:0:0: [sdc] No Caching mode page present
[  116.232818] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  116.447676]  sdc: sdc1
[  116.450184] sd 6:0:0:0: [sdc] No Caching mode page present
[  116.450191] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  116.450195] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 2557.597403] wlan0: authenticate with 00:0d:97:30:c0:9e
[ 2557.600856] wlan0: send auth to 00:0d:97:30:c0:9e (try 1/3)
[ 2557.604067] wlan0: authenticated
[ 2557.606590] wlan0: waiting for beacon from 00:0d:97:30:c0:9e
[ 2557.720037] wlan0: associate with 00:0d:97:30:c0:9e (try 1/3)
[ 2557.732231] wlan0: RX AssocResp from 00:0d:97:30:c0:9e (capab=0x431 status=0 aid=4)
[ 2557.737223] wlan0: associated
[ 2619.790723] wlan0: disassociating from 00:0d:97:30:c0:9e by local choice (reason=3)
[ 2619.822683] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2619.822691] cfg80211: Restoring regulatory settings
[ 2619.822701] cfg80211: Calling CRDA to update world regulatory domain
[ 2619.823576] wlan0: deauthenticating from 00:0d:97:30:c0:9e by local choice (reason=3)
[ 2619.832111] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 2619.832117] cfg80211: World regulatory domain updated:
[ 2619.832120] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2619.832124] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2619.832127] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2619.832131] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2619.832134] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2619.832137] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2621.206524] wlan0: authenticate with 00:23:5e:4a:0a:60
[ 2621.218323] wlan0: send auth to 00:23:5e:4a:0a:60 (try 1/3)
[ 2621.221116] wlan0: authenticated
[ 2621.224178] wlan0: associate with 00:23:5e:4a:0a:60 (try 1/3)
[ 2621.229301] wlan0: RX AssocResp from 00:23:5e:4a:0a:60 (capab=0x431 status=0 aid=32)
[ 2621.238702] wlan0: associated
[ 2621.239056] cfg80211: Calling CRDA for country: SE
[ 2621.247163] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247170] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247174] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247177] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247180] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247184] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247187] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247190] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247193] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247196] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247199] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247203] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247206] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247209] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247212] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247216] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247218] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247222] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247225] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247228] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247231] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247234] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247237] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247241] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247244] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 2621.247247] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 2621.247251] cfg80211: Regulatory domain changed to country: SE
[ 2621.247253] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2621.247257] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2621.247260] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2621.247263] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2621.247266] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 2652.046769] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
xaal@ACE:~$ 

```

--------------
output of dmesg when I've reconnected to another AP, after it has become unresponsive...
```

[ 5266.228042] [drm:intel_lvds_enable] *ERROR* timed out waiting for panel to power on
[ 5293.915650] type=1701 audit(1354180441.313:29): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=8203 comm="chromium-browse" reason="seccomp" sig=0 syscall=20 compat=0 ip=0xb2f2e424 code=0x50000
[ 5465.686446] wlan0: deauthenticating from 00:23:5e:4a:0a:60 by local choice (reason=3)
[ 5465.698187] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 5465.698195] cfg80211: Restoring regulatory settings
[ 5465.698206] cfg80211: Calling CRDA to update world regulatory domain
[ 5465.716422] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 5465.716428] cfg80211: World regulatory domain updated:
[ 5465.716432] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5465.716435] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5465.716439] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5465.716442] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5465.716446] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5465.716449] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5476.319821] wlan0: authenticate with 00:23:5e:96:29:51
[ 5476.347130] wlan0: send auth to 00:23:5e:96:29:51 (try 1/3)
[ 5476.349783] wlan0: authenticated
[ 5476.350247] wlan0: waiting for beacon from 00:23:5e:96:29:51
[ 5476.669966] wlan0: authenticate with 00:23:5e:4a:0a:61
[ 5476.679724] wlan0: send auth to 00:23:5e:4a:0a:61 (try 1/3)
[ 5476.682470] wlan0: authenticated
[ 5476.684126] wlan0: associate with 00:23:5e:4a:0a:61 (try 1/3)
[ 5476.888022] wlan0: associate with 00:23:5e:4a:0a:61 (try 2/3)
[ 5476.892884] wlan0: RX AssocResp from 00:23:5e:4a:0a:61 (capab=0x421 status=12 aid=0)
[ 5476.892889] wlan0: 00:23:5e:4a:0a:61 denied association (code=12)
[ 5476.901442] wlan0: deauthenticating from 00:23:5e:4a:0a:61 by local choice (reason=3)
[ 5477.128435] wlan0: authenticate with 00:23:5e:49:f2:11
[ 5477.140472] wlan0: send auth to 00:23:5e:49:f2:11 (try 1/3)
[ 5477.143146] wlan0: authenticated
[ 5477.144035] wlan0: associate with 00:23:5e:49:f2:11 (try 1/3)
[ 5477.152566] wlan0: RX AssocResp from 00:23:5e:49:f2:11 (capab=0x421 status=12 aid=0)
[ 5477.152573] wlan0: 00:23:5e:49:f2:11 denied association (code=12)
[ 5477.154078] wlan0: deauthenticating from 00:23:5e:49:f2:11 by local choice (reason=3)
[ 5477.386386] wlan0: authenticate with 00:23:5e:49:f2:01
[ 5477.391966] wlan0: send auth to 00:23:5e:49:f2:01 (try 1/3)
[ 5477.395678] wlan0: authenticated
[ 5477.396034] wlan0: associate with 00:23:5e:49:f2:01 (try 1/3)
[ 5477.399900] wlan0: RX AssocResp from 00:23:5e:49:f2:01 (capab=0x421 status=12 aid=0)
[ 5477.399906] wlan0: 00:23:5e:49:f2:01 denied association (code=12)
[ 5477.407269] wlan0: deauthenticating from 00:23:5e:49:f2:01 by local choice (reason=3)
[ 5477.649037] wlan0: authenticate with 00:23:5e:96:29:c1
[ 5477.654671] wlan0: send auth to 00:23:5e:96:29:c1 (try 1/3)
[ 5477.659269] wlan0: authenticated
[ 5477.660032] wlan0: associate with 00:23:5e:96:29:c1 (try 1/3)
[ 5477.665304] wlan0: RX AssocResp from 00:23:5e:96:29:c1 (capab=0x421 status=0 aid=34)
[ 5477.668160] wlan0: associated
[ 5477.669152] cfg80211: Calling CRDA for country: SE
[ 5477.684594] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684602] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684605] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684609] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684612] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684616] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684619] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684623] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684626] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684630] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684633] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684637] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684640] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684643] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684647] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684650] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684654] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684657] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684660] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684664] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684667] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684671] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684674] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684678] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684681] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 5477.684684] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 5477.684689] cfg80211: Regulatory domain changed to country: SE
[ 5477.684691] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5477.684695] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 5477.684698] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 5477.684702] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 5477.684705] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)

```

I hope for a solution without having to reinstall the OS.

---

