---
title: "Very Slow Internet (New Ubuntu User)"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by Philosogamer on 2012-05-19
My internet is horridly slow. On speedtest.net, I'm getting 0.11 MBPS download speed; dial up speeds on 1.5 MBPS internet is unacceptable. Any help would be greatly appreciated. The internet speeds are both slow wireless and wired.

Also, I'm a 100% new Linux user. I'm pretty good with Windows but going from Windows to Linux is just a totally new experience. I would like to continue and learn to use Linux if only my internet would not be so sluggish.

1 ) Machine Brand and Model (PC/Laptop):

**Lenovo ThinkPad T410 (2518-F5U)**

2 ) Wireless Brand, Model and Wireless Chipset:
$ lspci
```
[    2.800200] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.815250] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7930H  1.D1 PQ: 0 ANSI: 5
[    2.832254] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.832260] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.832425] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.832558] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.845020]  sda: sda1 sda2 < sda5 >
[    2.846089] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.847373] Freeing unused kernel memory: 920k freed
[    2.847504] Write protecting the kernel read-only data: 12288k
[    2.851465] Freeing unused kernel memory: 1608k freed
[    2.854617] Freeing unused kernel memory: 1196k freed
[    2.871733] udevd[103]: starting version 175
[    2.895116] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.895119] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.895160] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.895175] e1000e 0000:00:19.0: setting latency timer to 64
[    2.895325] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    2.913213] sdhci: Secure Digital Host Controller Interface driver
[    2.913216] sdhci: Copyright(c) Pierre Ossman
[    2.913519] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e822] (rev 1)
[    2.913587] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.913666] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.913676] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    2.913706] mmc0: no vmmc regulator found
[    2.913790] Registered led device: mmc0::
[    2.916720] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    2.917580] firewire_ohci 0000:0d:00.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.917629] firewire_ohci 0000:0d:00.3: setting latency timer to 64
[    2.978333] firewire_ohci: Added fw-ohci device 0000:0d:00.3, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    3.075256] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:1c:b6:07
[    3.075259] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.075327] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 10, PBA No: A002FF-0FF
[    3.116150] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.116154] EXT4-fs (sda1): write access will be enabled during recovery
[    3.478139] firewire_core: created device fw0: GUID f0def1ff1cb607ff, S400
[    5.080550] EXT4-fs (sda1): recovery complete
[    5.081461] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.829721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.034646] udevd[469]: starting version 175
[    8.255774] Adding 4048892k swap on /dev/sda5.  Priority:-1 extents:1 across:4048892k 
[    8.824102] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.999031] Bluetooth: Core ver 2.16
[    9.999051] NET: Registered protocol family 31
[    9.999053] Bluetooth: HCI device and connection manager initialized
[    9.999056] Bluetooth: HCI socket layer initialized
[    9.999057] Bluetooth: L2CAP socket layer initialized
[    9.999063] Bluetooth: SCO socket layer initialized
[   10.111912] Non-volatile memory driver v1.3
[   10.117331] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   10.117530] usbcore: registered new interface driver btusb
[   10.126370] tpm_tis 00:0b: 1.2 TPM (device-id 0x0, rev-id 78)
[   10.410278] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.410667] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.410674] mei 0000:00:16.0: setting latency timer to 64
[   10.410774] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[   10.423951] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   10.423961] intel ips 0000:00:1f.6: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   10.423991] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   10.424061] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   10.437811] acpi device:0c: registered as cooling_device4
[   10.437948] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b/LNXVIDEO:01/input/input4
[   10.438000] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[   10.591269] i2400m_usb 2-1.3:1.0: WiMAX interface wmx0 (00:1d:e1:39:de:7c) ready
[   10.861645] wmi: Mapper loaded
[   11.191881] cfg80211: Calling CRDA to update world regulatory domain
[   11.453756] lp: driver loaded but no devices found
[   11.808795] type=1400 audit(1337413576.975:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=657 comm="apparmor_parser"
[   11.808831] type=1400 audit(1337413576.975:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
[   11.809095] type=1400 audit(1337413576.975:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=657 comm="apparmor_parser"
[   11.809266] type=1400 audit(1337413576.975:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=657 comm="apparmor_parser"
[   11.809330] type=1400 audit(1337413576.975:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   11.809630] type=1400 audit(1337413576.975:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
[   11.815818] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.815884] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   11.815912] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   11.945568] Linux video capture interface: v2.00
[   11.960722] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480f)
[   11.962639] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input5
[   11.962742] usbcore: registered new interface driver uvcvideo
[   11.962744] USB Video Class driver (1.1.1)
[   12.166306] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.166309] Copyright(c) 2003-2011 Intel Corporation
[   12.166401] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.166431] iwlwifi 0000:03:00.0: setting latency timer to 64
[   12.166477] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   12.166479] iwlwifi 0000:03:00.0: pci_resource_base = ffffc9000066c000
[   12.166481] iwlwifi 0000:03:00.0: HW Revision ID = 0x35
[   12.166598] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   12.166686] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   12.166788] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   12.176655] iwlwifi 0000:03:00.0: device EEPROM VER=0x536, CALIB=0x6
[   12.176657] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   12.176671] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.182515] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   12.182517] thinkpad_acpi: http://ibm-acpi.sf.net/
[   12.182519] thinkpad_acpi: ThinkPad BIOS 6IET72WW (1.32 ), EC 6IHT37WW-1.12
[   12.182520] thinkpad_acpi: Lenovo ThinkPad T410, model 2518F5U
[   12.183228] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   12.183390] thinkpad_acpi: radio switch found; radios are enabled
[   12.185998] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   12.186464] Registered led device: tpacpi::thinklight
[   12.186506] Registered led device: tpacpi::power
[   12.186526] Registered led device: tpacpi::standby
[   12.186553] Registered led device: tpacpi::thinkvantage
[   12.188462] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   12.188553] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   12.189689] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   12.283431] iwlwifi 0000:03:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.283675] Registered led device: phy0-led
[   12.283710] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.362140] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.362144] hda_intel: Disabling MSI
[   12.362205] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   12.366075] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.734968] nvidia: module license 'NVIDIA' taints kernel.
[   12.734971] Disabling lock debugging due to kernel taint
[   12.909556] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   12.909568] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   12.944739] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.944742] cfg80211: World regulatory domain updated:
[   12.944743] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.944745] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.944747] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.944749] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.944751] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.944753] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.958879] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   13.544439] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.568418] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.592401] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.616393] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.616600] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   13.616700] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   13.617058] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   13.617729] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   13.619365] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.619375] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.619386] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.619400] nvidia 0000:01:00.0: setting latency timer to 64
[   13.619406] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.619557] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   14.041147] init: failsafe main process (841) killed by TERM signal
[   14.127658] ppdev: user-space parallel port driver
[   14.585246] i2400m_usb 2-1.3:1.0: firmware interface version 9.3.2
[   14.593078] usbcore: registered new interface driver i2400m_usb
[   14.782429] Bluetooth: RFCOMM TTY layer initialized
[   14.782435] Bluetooth: RFCOMM socket layer initialized
[   14.782437] Bluetooth: RFCOMM ver 1.11
[   14.862565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.862568] Bluetooth: BNEP filters: protocol multicast
[   15.086278] type=1400 audit(1337413580.251:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=972 comm="apparmor_parser"
[   15.086667] type=1400 audit(1337413580.251:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=972 comm="apparmor_parser"
[   15.521231] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   15.521234] vesafb: scrolling: redraw
[   15.521236] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.522827] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90011280000, using 1216k, total 1216k
[   15.522999] Console: switching to colour frame buffer device 80x30
[   15.523013] fb0: VESA VGA frame buffer device
[   16.075651] type=1400 audit(1337413581.243:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1040 comm="apparmor_parser"
[   16.075934] type=1400 audit(1337413581.243:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1040 comm="apparmor_parser"
[   16.990131] audit_printk_skb: 21 callbacks suppressed
[   16.990134] type=1400 audit(1337413582.155:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1041 comm="apparmor_parser"
[   16.993370] type=1400 audit(1337413582.159:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1041 comm="apparmor_parser"
[   16.993989] type=1400 audit(1337413582.159:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1041 comm="apparmor_parser"
[   16.994842] type=1400 audit(1337413582.163:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1041 comm="apparmor_parser"
[   16.996725] type=1400 audit(1337413582.163:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=1041 comm="apparmor_parser"
[   16.997289] type=1400 audit(1337413582.163:24): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//sanitized_helper" pid=1041 comm="apparmor_parser"
[   16.997814] type=1400 audit(1337413582.163:25): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1041 comm="apparmor_parser"
[   16.999235] type=1400 audit(1337413582.167:26): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=1041 comm="apparmor_parser"
[   17.447635] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   17.502331] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   17.502756] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.503084] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.504467] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   17.504649] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   17.744853] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   17.745038] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   17.864002] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.864699] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.867914] ADDRCONF(NETDEV_UP): wmx0: link is not ready
[   17.868139] ADDRCONF(NETDEV_UP): wmx0: link is not ready
[   19.079859] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[   19.079865] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   19.080230] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.452944] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.708730] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12
[   29.828665] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[   29.834688] wlan0: authenticated
[   29.841450] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[   29.844153] wlan0: RX AssocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=3)
[   29.844158] wlan0: associated
[   29.850557] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.927371] eth0: no IPv6 routers present
[   39.881871] wlan0: no IPv6 routers present
[   47.123500] type=1400 audit(1337413612.314:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1980 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  208.139485] wlan0: deauthenticated from 00:1d:6a:e1:1b:61 (Reason: 3)
[  208.198366] cfg80211: All devices are disconnected, going to restore regulatory settings
[  208.198377] cfg80211: Restoring regulatory settings
[  208.198385] cfg80211: Calling CRDA to update world regulatory domain
[  208.204463] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  208.204470] cfg80211: World regulatory domain updated:
[  208.204473] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  208.204478] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  208.204482] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  208.204486] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  208.204490] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  208.204495] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  223.260132] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  262.784196] eth0: no IPv6 routers present
[  856.648477] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[  856.651054] wlan0: authenticated
[  856.651372] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[  856.654125] wlan0: RX ReassocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=1)
[  856.654130] wlan0: associated
[  856.661271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  859.324713] e1000e: eth0 NIC Link is Down
[  863.609473] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  866.980096] wlan0: no IPv6 routers present
[ 1219.064758] wlan0: deauthenticated from 00:1d:6a:e1:1b:61 (Reason: 3)
[ 1219.075631] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1219.075641] cfg80211: Restoring regulatory settings
[ 1219.075676] cfg80211: Calling CRDA to update world regulatory domain
[ 1219.081764] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1219.081771] cfg80211: World regulatory domain updated:
[ 1219.081774] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1219.081779] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1219.081784] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1219.081788] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1219.081792] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1219.081796] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1230.404240] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[ 1230.406771] wlan0: authenticated
[ 1230.407077] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[ 1230.409871] wlan0: RX ReassocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=2)
[ 1230.409877] wlan0: associated
[ 1290.770152] wlan0: deauthenticated from 00:1d:6a:e1:1b:61 (Reason: 3)
[ 1290.803983] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1290.803994] cfg80211: Restoring regulatory settings
[ 1290.804001] cfg80211: Calling CRDA to update world regulatory domain
[ 1290.810183] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1290.810190] cfg80211: World regulatory domain updated:
[ 1290.810193] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1290.810198] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.810202] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1290.810206] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1290.810211] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.810215] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1302.252236] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[ 1302.255078] wlan0: authenticated
[ 1302.255426] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[ 1302.258215] wlan0: RX ReassocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=2)
[ 1302.258222] wlan0: associated
philosogamer@Nabu:~$ sudo lshw -C network
[sudo] password for philosogamer: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:1c:b6:07
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:15:6c:82:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=41.28.5.1 build 33926 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f2000000-f2001fff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:1.3
       logical name: wmx0
       serial: 00:1d:e1:39:de:7c
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ iwlist scan
lo        Interface doesn't support scanning.

wmx0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:6A:E1:1B:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000a0f181
                    Extra: Last beacon: 1248888ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD730050F204104A000110103B00010310470010AA4DE2BCD5F89FF6ABB6001D6AE11B611044000101102100074169726C696E6B10230006415234333057102400064152343330571042000830303030303030301054000800060050F20400011011000641523433305710080002008E1041000100

eth0      Interface doesn't support scanning.

philosogamer@Nabu:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS
philosogamer@Nabu:~$ uname -mr
3.2.0-23-generic x86_64
philosogamer@Nabu:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ 
philosogamer@Nabu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [NVS 3100M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 35)
0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 PCIe IEEE 1394 Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

$ lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 005: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 002 Device 003: ID 8086:0187 Intel Corp. 

```

3 ) check interface:

$ ifconfig

```
eth0      Link encap:Ethernet  HWaddr f0:de:f1:1c:b6:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:13694 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16219655 (16.2 MB)  TX bytes:1445747 (1.4 MB)
          Interrupt:20 Memory:f2400000-f2420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2575 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:250187 (250.1 KB)  TX bytes:250187 (250.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:15:6c:82:2c  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:15ff:fe6c:822c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13519893 (13.5 MB)  TX bytes:3095485 (3.0 MB)

wmx0      Link encap:Ethernet  HWaddr 00:1d:e1:39:de:7c  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

$ iwconfig

```
lo        no wireless extensions.

wmx0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"default"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:6A:E1:1B:61   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:485   Missed beacon:0

eth0      no wireless extensions.

```

4 ) Check for modules:

$ lsmod

```
Module                  Size  Used by
ath9k                 132390  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
vesafb                 13844  1 
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  4 
nvidia              12319264  43 
arc4                   12529  2 
snd_hda_codec_conexant    62128  1 
thinkpad_acpi          81819  0 
iwlwifi               328352  0 
psmouse                87603  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  4 
mac80211              506816  2 ath9k,iwlwifi
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
lp                     17799  0 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13211  0 
cfg80211              205544  4 ath9k,ath,iwlwifi,mac80211
snd_seq_midi           13324  0 
parport                46562  3 parport_pc,ppdev,lp
snd_rawmidi            30748  1 snd_seq_midi
mxm_wmi                12979  0 
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i2400m_usb             36569  0 
i2400m                107980  1 i2400m_usb
snd_timer              29990  2 snd_pcm,snd_seq
binfmt_misc            17540  1 
video                  19596  0 
intel_ips              18089  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mei                    41616  0 
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18804  0 
btusb                  18288  2 
nvram                  14413  1 thinkpad_acpi
bluetooth             180104  23 bnep,rfcomm,btusb
wimax                  34762  1 i2400m
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 

```

5 ) Kernel boot messages

```
[    0.883957] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.884374] fuse init (API version 7.17)
[    0.884452] msgmni has been set to 7626
[    0.884819] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.884849] io scheduler noop registered
[    0.884851] io scheduler deadline registered
[    0.884876] io scheduler cfq registered (default)
[    0.884986] pcieport 0000:00:01.0: setting latency timer to 64
[    0.885014] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.885267] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.885284] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.885323] intel_idle: MWAIT substates: 0x1120
[    0.885325] intel_idle: v0.4 model 0x25
[    0.885326] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.885681] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.885980] ACPI: AC Adapter [AC] (on-line)
[    0.886062] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.886380] ACPI: Lid Switch [LID]
[    0.886417] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.886421] ACPI: Sleep Button [SLPB]
[    0.886462] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.886464] ACPI: Power Button [PWRF]
[    0.893402] thermal LNXTHERM:00: registered as thermal_zone0
[    0.893404] ACPI: Thermal Zone [THM0] (47 C)
[    0.893420] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.893426] ACPI: Battery Slot [BAT0] (battery present)
[    0.893445] ERST: Table is not found!
[    0.893446] GHES: HEST is not enabled!
[    0.893524] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.908955] ACPI: Battery Slot [BAT0] (battery present)
[    1.059561] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.079952] 0000:00:16.3: ttyS4 at I/O 0x1800 (irq = 17) is a 16550A
[    1.115466] Linux agpgart interface v0.103
[    1.116664] brd: module loaded
[    1.117269] loop: module loaded
[    1.117391] ata_piix 0000:00:1f.2: version 2.13
[    1.117402] ata_piix 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.117407] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.271211] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.271461] scsi0 : ata_piix
[    1.271531] scsi1 : ata_piix
[    1.271874] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1840 irq 14
[    1.271881] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1848 irq 15
[    1.271901] ata_piix 0000:00:1f.5: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    1.271908] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.271973] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.272161] scsi2 : ata_piix
[    1.272230] scsi3 : ata_piix
[    1.272491] ata3: SATA max UDMA/133 cmd 0x1898 ctl 0x180c bmdma 0x1880 irq 17
[    1.272496] ata4: SATA max UDMA/133 cmd 0x1890 ctl 0x1808 bmdma 0x1888 irq 17
[    1.272755] Fixed MDIO Bus: probed
[    1.272767] tun: Universal TUN/TAP device driver, 1.6
[    1.272769] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.272815] PPP generic driver version 2.4.2
[    1.272893] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.272905] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.272909] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.272915] ehci_hcd 0000:00:1a.0: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.272939] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.272942] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.272979] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.273006] ehci_hcd 0000:00:1a.0: debug port 2
[    1.276913] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.276927] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xf2427800
[    1.291168] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.291316] hub 1-0:1.0: USB hub found
[    1.291320] hub 1-0:1.0: 3 ports detected
[    1.291374] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.291377] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    1.291383] ehci_hcd 0000:00:1d.0: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.291396] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.291400] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.291440] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.291464] ehci_hcd 0000:00:1d.0: debug port 2
[    1.295368] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.295382] ehci_hcd 0000:00:1d.0: irq 19, io mem 0xf2427c00
[    1.311158] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.311283] hub 2-0:1.0: USB hub found
[    1.311285] hub 2-0:1.0: 3 ports detected
[    1.311336] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.311346] uhci_hcd: USB Universal Host Controller Interface driver
[    1.311381] usbcore: registered new interface driver libusual
[    1.311409] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.314582] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.314587] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.314686] mousedev: PS/2 mouse device common for all mice
[    1.314850] rtc_cmos 00:08: RTC can wake from S4
[    1.314959] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.314996] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.315055] device-mapper: uevent: version 1.0.3
[    1.315119] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.315210] cpuidle: using governor ladder
[    1.315326] cpuidle: using governor menu
[    1.315327] EFI Variables Facility v0.08 2004-May-17
[    1.315510] TCP cubic registered
[    1.315582] NET: Registered protocol family 10
[    1.315949] NET: Registered protocol family 17
[    1.315961] Registering the dns_resolver key type
[    1.316213] PM: Hibernation image not present or could not be loaded.
[    1.316238] registered taskstats version 1
[    1.325630] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.335607]   Magic number: 12:397:774
[    1.335674] mem zero: hash matches
[    1.335823] rtc_cmos 00:08: setting system clock to 2012-05-19 07:46:06 UTC (1337413566)
[    1.344099] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.344103] EDD information not available.
[    1.602656] ata4: SATA link down (SStatus 0 SControl 300)
[    1.614297] ata3: SATA link down (SStatus 0 SControl 300)
[    1.615094] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.747848] hub 1-1:1.0: USB hub found
[    1.748052] hub 1-1:1.0: 6 ports detected
[    1.834935] Refined TSC clocksource calibration: 2526.999 MHz.
[    1.834941] Switching to clocksource tsc
[    1.858960] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.991702] hub 2-1:1.0: USB hub found
[    1.991907] hub 2-1:1.0: 8 ports detected
[    2.062997] usb 1-1.3: new full-speed USB device number 3 using ehci_hcd
[    2.226938] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[    2.394833] usb 1-1.6: new high-speed USB device number 5 using ehci_hcd
[    2.562739] usb 2-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.618490] ata1.01: failed to resume link (SControl 0)
[    2.618581] ata2.01: failed to resume link (SControl 0)
[    2.774491] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.774513] ata1.01: SATA link down (SStatus 4 SControl 0)
[    2.774690] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.774712] ata2.01: SATA link down (SStatus 4 SControl 0)
[    2.774728] ata2.01: link offline, clearing class 3 to NONE
[    2.782939] ata2.00: ATAPI: Optiarc DVD RW AD-7930H, 1.D1, max UDMA/100
[    2.783156] ata1.00: ATA-8: HITACHI HTS725050A9A364, PC4ZC70F, max UDMA/100
[    2.783158] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.798790] ata2.00: configured for UDMA/100
[    2.799144] ata1.00: configured for UDMA/100
[    2.799519] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72505 PC4Z PQ: 0 ANSI: 5
[    2.799811] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.799823] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.800068] sd 0:0:0:0: [sda] Write Protect is off
[    2.800074] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.800200] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.815250] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7930H  1.D1 PQ: 0 ANSI: 5
[    2.832254] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.832260] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.832425] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.832558] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.845020]  sda: sda1 sda2 < sda5 >
[    2.846089] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.847373] Freeing unused kernel memory: 920k freed
[    2.847504] Write protecting the kernel read-only data: 12288k
[    2.851465] Freeing unused kernel memory: 1608k freed
[    2.854617] Freeing unused kernel memory: 1196k freed
[    2.871733] udevd[103]: starting version 175
[    2.895116] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
[    2.895119] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.895160] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.895175] e1000e 0000:00:19.0: setting latency timer to 64
[    2.895325] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[    2.913213] sdhci: Secure Digital Host Controller Interface driver
[    2.913216] sdhci: Copyright(c) Pierre Ossman
[    2.913519] sdhci-pci 0000:0d:00.0: SDHCI controller found [1180:e822] (rev 1)
[    2.913587] sdhci-pci 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.913666] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.913676] sdhci-pci 0000:0d:00.0: setting latency timer to 64
[    2.913706] mmc0: no vmmc regulator found
[    2.913790] Registered led device: mmc0::
[    2.916720] mmc0: SDHCI controller on PCI [0000:0d:00.0] using DMA
[    2.917580] firewire_ohci 0000:0d:00.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.917629] firewire_ohci 0000:0d:00.3: setting latency timer to 64
[    2.978333] firewire_ohci: Added fw-ohci device 0000:0d:00.3, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    3.075256] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:1c:b6:07
[    3.075259] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.075327] e1000e 0000:00:19.0: eth0: MAC: 9, PHY: 10, PBA No: A002FF-0FF
[    3.116150] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.116154] EXT4-fs (sda1): write access will be enabled during recovery
[    3.478139] firewire_core: created device fw0: GUID f0def1ff1cb607ff, S400
[    5.080550] EXT4-fs (sda1): recovery complete
[    5.081461] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.829721] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.034646] udevd[469]: starting version 175
[    8.255774] Adding 4048892k swap on /dev/sda5.  Priority:-1 extents:1 across:4048892k 
[    8.824102] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    9.999031] Bluetooth: Core ver 2.16
[    9.999051] NET: Registered protocol family 31
[    9.999053] Bluetooth: HCI device and connection manager initialized
[    9.999056] Bluetooth: HCI socket layer initialized
[    9.999057] Bluetooth: L2CAP socket layer initialized
[    9.999063] Bluetooth: SCO socket layer initialized
[   10.111912] Non-volatile memory driver v1.3
[   10.117331] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   10.117530] usbcore: registered new interface driver btusb
[   10.126370] tpm_tis 00:0b: 1.2 TPM (device-id 0x0, rev-id 78)
[   10.410278] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   10.410667] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.410674] mei 0000:00:16.0: setting latency timer to 64
[   10.410774] mei 0000:00:16.0: irq 42 for MSI/MSI-X
[   10.423951] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   10.423961] intel ips 0000:00:1f.6: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   10.423991] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   10.424061] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   10.437811] acpi device:0c: registered as cooling_device4
[   10.437948] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b/LNXVIDEO:01/input/input4
[   10.438000] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[   10.591269] i2400m_usb 2-1.3:1.0: WiMAX interface wmx0 (00:1d:e1:39:de:7c) ready
[   10.861645] wmi: Mapper loaded
[   11.191881] cfg80211: Calling CRDA to update world regulatory domain
[   11.453756] lp: driver loaded but no devices found
[   11.808795] type=1400 audit(1337413576.975:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=657 comm="apparmor_parser"
[   11.808831] type=1400 audit(1337413576.975:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
[   11.809095] type=1400 audit(1337413576.975:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=657 comm="apparmor_parser"
[   11.809266] type=1400 audit(1337413576.975:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=657 comm="apparmor_parser"
[   11.809330] type=1400 audit(1337413576.975:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   11.809630] type=1400 audit(1337413576.975:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
[   11.815818] snd_hda_intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.815884] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   11.815912] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   11.945568] Linux video capture interface: v2.00
[   11.960722] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480f)
[   11.962639] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input5
[   11.962742] usbcore: registered new interface driver uvcvideo
[   11.962744] USB Video Class driver (1.1.1)
[   12.166306] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.166309] Copyright(c) 2003-2011 Intel Corporation
[   12.166401] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.166431] iwlwifi 0000:03:00.0: setting latency timer to 64
[   12.166477] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   12.166479] iwlwifi 0000:03:00.0: pci_resource_base = ffffc9000066c000
[   12.166481] iwlwifi 0000:03:00.0: HW Revision ID = 0x35
[   12.166598] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   12.166686] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N + WiMAX 6250 AGN, REV=0x84
[   12.166788] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   12.176655] iwlwifi 0000:03:00.0: device EEPROM VER=0x536, CALIB=0x6
[   12.176657] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   12.176671] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.182515] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   12.182517] thinkpad_acpi: http://ibm-acpi.sf.net/
[   12.182519] thinkpad_acpi: ThinkPad BIOS 6IET72WW (1.32 ), EC 6IHT37WW-1.12
[   12.182520] thinkpad_acpi: Lenovo ThinkPad T410, model 2518F5U
[   12.183228] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   12.183390] thinkpad_acpi: radio switch found; radios are enabled
[   12.185998] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   12.186464] Registered led device: tpacpi::thinklight
[   12.186506] Registered led device: tpacpi::power
[   12.186526] Registered led device: tpacpi::standby
[   12.186553] Registered led device: tpacpi::thinkvantage
[   12.188462] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   12.188553] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   12.189689] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   12.283431] iwlwifi 0000:03:00.0: loaded firmware version 41.28.5.1 build 33926
[   12.283675] Registered led device: phy0-led
[   12.283710] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.362140] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   12.362144] hda_intel: Disabling MSI
[   12.362205] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   12.366075] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.734968] nvidia: module license 'NVIDIA' taints kernel.
[   12.734971] Disabling lock debugging due to kernel taint
[   12.909556] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   12.909568] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   12.944739] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.944742] cfg80211: World regulatory domain updated:
[   12.944743] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.944745] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.944747] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.944749] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.944751] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.944753] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.958879] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   13.544439] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.568418] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.592401] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.616393] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   13.616600] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   13.616700] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   13.617058] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   13.617729] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   13.619365] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.619375] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.619386] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.619400] nvidia 0000:01:00.0: setting latency timer to 64
[   13.619406] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.619557] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  295.40  Thu Apr  5 21:37:00 PDT 2012
[   14.041147] init: failsafe main process (841) killed by TERM signal
[   14.127658] ppdev: user-space parallel port driver
[   14.585246] i2400m_usb 2-1.3:1.0: firmware interface version 9.3.2
[   14.593078] usbcore: registered new interface driver i2400m_usb
[   14.782429] Bluetooth: RFCOMM TTY layer initialized
[   14.782435] Bluetooth: RFCOMM socket layer initialized
[   14.782437] Bluetooth: RFCOMM ver 1.11
[   14.862565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.862568] Bluetooth: BNEP filters: protocol multicast
[   15.086278] type=1400 audit(1337413580.251:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=972 comm="apparmor_parser"
[   15.086667] type=1400 audit(1337413580.251:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=972 comm="apparmor_parser"
[   15.521231] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   15.521234] vesafb: scrolling: redraw
[   15.521236] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   15.522827] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90011280000, using 1216k, total 1216k
[   15.522999] Console: switching to colour frame buffer device 80x30
[   15.523013] fb0: VESA VGA frame buffer device
[   16.075651] type=1400 audit(1337413581.243:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1040 comm="apparmor_parser"
[   16.075934] type=1400 audit(1337413581.243:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1040 comm="apparmor_parser"
[   16.990131] audit_printk_skb: 21 callbacks suppressed
[   16.990134] type=1400 audit(1337413582.155:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1041 comm="apparmor_parser"
[   16.993370] type=1400 audit(1337413582.159:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=1041 comm="apparmor_parser"
[   16.993989] type=1400 audit(1337413582.159:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=1041 comm="apparmor_parser"
[   16.994842] type=1400 audit(1337413582.163:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1041 comm="apparmor_parser"
[   16.996725] type=1400 audit(1337413582.163:23): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=1041 comm="apparmor_parser"
[   16.997289] type=1400 audit(1337413582.163:24): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//sanitized_helper" pid=1041 comm="apparmor_parser"
[   16.997814] type=1400 audit(1337413582.163:25): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1041 comm="apparmor_parser"
[   16.999235] type=1400 audit(1337413582.167:26): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer//sanitized_helper" pid=1041 comm="apparmor_parser"
[   17.447635] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   17.502331] e1000e 0000:00:19.0: irq 41 for MSI/MSI-X
[   17.502756] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.503084] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.504467] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   17.504649] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   17.744853] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   17.745038] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   17.864002] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.864699] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.867914] ADDRCONF(NETDEV_UP): wmx0: link is not ready
[   17.868139] ADDRCONF(NETDEV_UP): wmx0: link is not ready
[   19.079859] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx
[   19.079865] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   19.080230] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.452944] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   19.708730] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input12
[   29.828665] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[   29.834688] wlan0: authenticated
[   29.841450] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[   29.844153] wlan0: RX AssocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=3)
[   29.844158] wlan0: associated
[   29.850557] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.927371] eth0: no IPv6 routers present
[   39.881871] wlan0: no IPv6 routers present
[   47.123500] type=1400 audit(1337413612.314:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1980 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  208.139485] wlan0: deauthenticated from 00:1d:6a:e1:1b:61 (Reason: 3)
[  208.198366] cfg80211: All devices are disconnected, going to restore regulatory settings
[  208.198377] cfg80211: Restoring regulatory settings
[  208.198385] cfg80211: Calling CRDA to update world regulatory domain
[  208.204463] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  208.204470] cfg80211: World regulatory domain updated:
[  208.204473] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  208.204478] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  208.204482] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  208.204486] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  208.204490] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  208.204495] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  223.260132] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  262.784196] eth0: no IPv6 routers present
[  856.648477] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[  856.651054] wlan0: authenticated
[  856.651372] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[  856.654125] wlan0: RX ReassocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=1)
[  856.654130] wlan0: associated
[  856.661271] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  859.324713] e1000e: eth0 NIC Link is Down
[  863.609473] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  866.980096] wlan0: no IPv6 routers present
[ 1219.064758] wlan0: deauthenticated from 00:1d:6a:e1:1b:61 (Reason: 3)
[ 1219.075631] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1219.075641] cfg80211: Restoring regulatory settings
[ 1219.075676] cfg80211: Calling CRDA to update world regulatory domain
[ 1219.081764] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1219.081771] cfg80211: World regulatory domain updated:
[ 1219.081774] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1219.081779] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1219.081784] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1219.081788] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1219.081792] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1219.081796] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1230.404240] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[ 1230.406771] wlan0: authenticated
[ 1230.407077] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[ 1230.409871] wlan0: RX ReassocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=2)
[ 1230.409877] wlan0: associated
[ 1290.770152] wlan0: deauthenticated from 00:1d:6a:e1:1b:61 (Reason: 3)
[ 1290.803983] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1290.803994] cfg80211: Restoring regulatory settings
[ 1290.804001] cfg80211: Calling CRDA to update world regulatory domain
[ 1290.810183] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1290.810190] cfg80211: World regulatory domain updated:
[ 1290.810193] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1290.810198] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.810202] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1290.810206] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1290.810211] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.810215] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1302.252236] wlan0: authenticate with 00:1d:6a:e1:1b:61 (try 1)
[ 1302.255078] wlan0: authenticated
[ 1302.255426] wlan0: associate with 00:1d:6a:e1:1b:61 (try 1)
[ 1302.258215] wlan0: RX ReassocResp from 00:1d:6a:e1:1b:61 (capab=0x421 status=0 aid=2)
[ 1302.258222] wlan0: associated

```

6 ) Network configuration

```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:1c:b6:07
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:15:6c:82:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic firmware=41.28.5.1 build 33926 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:f2000000-f2001fff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:1.3
       logical name: wmx0
       serial: 00:1d:e1:39:de:7c
       capabilities: ethernet physical
       configuration: driver=i2400m firmware=i6050-fw-usb-1.5.sbcf link=no

```

7 ) Scan for networks:

```
The program 'scan' can be found in the following packages:
 * dvb-apps
 * mailutils-mh
 * nmh
Try: sudo apt-get install <selected package>
philosogamer@Nabu:~$ iwlist scan
lo        Interface doesn't support scanning.

wmx0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:6A:E1:1B:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000a0f181
                    Extra: Last beacon: 2018312ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD730050F204104A000110103B00010310470010AA4DE2BCD5F89FF6ABB6001D6AE11B611044000101102100074169726C696E6B10230006415234333057102400064152343330571042000830303030303030301054000800060050F20400011011000641523433305710080002008E1041000100

eth0      Interface doesn't support scanning.

```

8 ) Ubuntu Version: 

```
Description:	Ubuntu 12.04 LTS

```

9 ) Kernel/architecture (including 32 vs. 64 bit): 
Code:

```
3.2.0-23-generic x86_64

```

10 ) Restarting the network:

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  
```

---

### Post by chili555 on 2012-05-19
Please see: [http://ubuntuforums.org/showpost.php?p=11949650&postcount=2](http://ubuntuforums.org/showpost.php?p=11949650&postcount=2)

I believe you have a variant of the same issue.

---

### Post by Philosogamer on 2012-05-19
I haven't solved my problem 100%, but it appears the stupidly slow speeds came from my router. For the time being, I'm not going to troubleshoot that. I'll keep this post updated for the status of my router connections.

However, when I try to download something from the terminal, the download speeds are awfully slow, peaking at 18 KB/s, when Speedtest.net gives me 1.5 MBPS.

::EDIT::
Also, forgot to mention, the solution you provided me did not help at all. But I believe that's primarily to do with the fact that my terrible connection had to do with my router. My modem was hard to connect with as well; had to completely reset it while it was connected to my Linux computer. However, I'm able to browse the web and test my internet speed and such just fine.

::UPDATE::
Changed my download sources under Ubuntu Software Center; I live in Washington state, so I chose the Washington.edu/ubuntu FTP mirror. Apparently my mirror was set somewhere in Europe. The mirror change barely helped; internet speeds are more stable, and I've seen a peak of 22 KB/s, but still fluxuate between 9 KB/s and 14 KB/s 90% of the time.

---

