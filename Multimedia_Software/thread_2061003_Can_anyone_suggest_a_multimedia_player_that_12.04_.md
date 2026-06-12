---
title: "Can anyone suggest a multimedia player that 12.04 will recognize and mount?"
date: 2012-09-21
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2012-09-21
Can anyone suggest a multimedia player that 12.04 will recognize and mount?

It won't mount my coby.

Thanks Hannibal

---

### Post by jerrrys on 2012-09-21
The software center is full of them, whats your problem?

Oh, and thanks for the cigar :)

---

### Post by acefromspace on 2012-09-21
I think he means a portable device like mp3 player, connected thru USB. I have a cheap one (and it is a Coby) that works just fine (I'm using ubuntu 10.04) I just connect it to USB (it should be OFF) and it lights up screen saying USB connected, then shows up on desktop (mounted, but not open) Double click to open (or right click and open folder) I don't use most of the stuff that comes with the player (for windows) but leave it on there anyway (don't delete when you delete media files) I can do music (mp3), photos (jpeg), but not video (it would have to be converted first... this can be done, but I haven't tried it yet)
Is this what you wanted to know? I don't use the disc that came with it, and I didn't care about video anyway. Also, the USB charges the battery... blinks, then stays on when charged.

---

### Post by acefromspace on 2012-09-21
By the way, a software multimedia player is what it sounded like you meant.
In that case, I love VLC. I know you meant portable device because of the name Coby.

---

### Post by Cheesemill on 2012-09-21
If you mean a hardware MP3 player then anything that can be mounted as a USB mass storage device will let you drag and drop files or use your media player to transfer music.

Every MP3 player I've ever seen has this functionality (apart from iDevices).

---

### Post by coljohnhannibalsmith on 2012-09-21
acefromspace, 12.04 will not mount my Coby 827.  At least there's no visible indication that it's mounted.

Should I get another unit, or is there something else I can try.

Thanks Hannibal

BTW, I did mean MP3/Video Player.

Also GParted doesn't even see it even though the unit says USB connected.

---

### Post by Cheesemill on 2012-09-21
Your Coby should work without any problems, I've just had a look at the manuals.

Could you plug it in, wait a few seconds, and then post the output of:
```
dmesg
lsusb
mount
```

---

### Post by coljohnhannibalsmith on 2012-09-21
Here's the output:
```

: 0 ANSI: 5
[    1.963656] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.963666] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.963694] sd 0:0:0:0: [sda] Write Protect is off
[    1.963697] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.963710] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.968217] scsi 2:0:0:0: CD-ROM            PLDS     DVD+-RW DS-8A8SH KD11 PQ: 0 ANSI: 5
[    1.977945] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.977951] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.978137] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.978244] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.046424]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.047280] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.048413] Freeing unused kernel memory: 920k freed
[    2.048492] Write protecting the kernel read-only data: 12288k
[    2.052165] Freeing unused kernel memory: 1616k freed
[    2.054817] Freeing unused kernel memory: 1200k freed
[    2.067609] udevd[140]: starting version 175
[    2.075463] xor: automatically using best checksumming function: generic_sse
[    2.084296] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.084318] r8169 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.084352] r8169 0000:01:00.0: setting latency timer to 64
[    2.084422] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[    2.084815] r8169 0000:01:00.0: eth0: RTL8105e at 0xffffc90000c3c000, d4:be:d9:44:03:ce, XID 00c00000 IRQ 42
[    2.094132]    generic_sse:  9466.000 MB/sec
[    2.094135] xor: using function: generic_sse (9466.000 MB/sec)
[    2.094792] device-mapper: dm-raid45: initialized v0.2594b
[    2.094796] hub 1-1:1.0: USB hub found
[    2.094878] hub 1-1:1.0: 6 ports detected
[    2.205994] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.338419] hub 2-1:1.0: USB hub found
[    2.338516] hub 2-1:1.0: 8 ports detected
[    2.377735] Refined TSC clocksource calibration: 2095.243 MHz.
[    2.377744] Switching to clocksource tsc
[    2.409827] usb 1-1.3: new high-speed USB device number 3 using ehci_hcd
[    2.577569] usb 1-1.5: new high-speed USB device number 4 using ehci_hcd
[    2.821203] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
[    3.248451] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   17.361655] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.380200] udevd[427]: starting version 175
[   17.404827] lp: driver loaded but no devices found
[   17.472849] wmi: Mapper loaded
[   17.476330] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   17.476611] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.476616] [drm] Initialized drm 1.1.0 20060810
[   17.476618] mei 0000:00:16.0: setting latency timer to 64
[   17.476677] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   17.478226] Adding 8287228k swap on /dev/sda6.  Priority:-1 extents:1 across:8287228k 
[   17.480401] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.480406] i915 0000:00:02.0: setting latency timer to 64
[   17.484888] cfg80211: Calling CRDA to update world regulatory domain
[   17.491677] Bluetooth: Core ver 2.16
[   17.494121] NET: Registered protocol family 31
[   17.494124] Bluetooth: HCI device and connection manager initialized
[   17.494127] Bluetooth: HCI socket layer initialized
[   17.494128] Bluetooth: L2CAP socket layer initialized
[   17.494133] Bluetooth: SCO socket layer initialized
[   17.495280] Linux video capture interface: v2.00
[   17.495294] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   17.495296] Copyright(c) 2003-2011 Intel Corporation
[   17.495467] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.495501] iwlwifi 0000:02:00.0: setting latency timer to 64
[   17.495531] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   17.495534] iwlwifi 0000:02:00.0: pci_resource_base = ffffc900117b4000
[   17.495536] iwlwifi 0000:02:00.0: HW Revision ID = 0xC4
[   17.495669] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[   17.495751] iwlwifi 0000:02:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
[   17.495817] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   17.495865] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   17.495885] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_E4HD (0c45:644a)
[   17.496241] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   17.496459] usbcore: registered new interface driver btusb
[   17.496880] Initializing rts5139 USB card reader driver...
[   17.502342] scsi6 : SCSI emulation for RTS5139 USB card reader
[   17.502550] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   17.502855] usbcore: registered new interface driver rts5139
[   17.502858] Realtek rts5139 USB card reader support registered.
[   17.504311] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   17.507703] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   17.512332] iwlwifi 0000:02:00.0: device EEPROM VER=0x81c, CALIB=0x6
[   17.512335] iwlwifi 0000:02:00.0: Device SKU: 0X150
[   17.512337] iwlwifi 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   17.512354] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   17.516823] device-mapper: multipath: version 1.3.0 loaded
[   17.520435] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.529765] input: Laptop_Integrated_Webcam_E4HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
[   17.530217] usbcore: registered new interface driver uvcvideo
[   17.530219] USB Video Class driver (1.1.1)
[   17.551110] mtrr: type mismatch for b0000000,10000000 old: write-back new: write-combining
[   17.551113] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   17.551373] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   17.551376] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.551377] [drm] Driver supports precise vblank timestamp query.
[   17.551725] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.554668] input: Dell WMI hotkeys as /devices/virtual/input/input5
[   17.559050] cfg80211: World regulatory domain updated:
[   17.559052] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.559054] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.559056] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.559057] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.559058] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.559060] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.638058] type=1400 audit(1348245202.415:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=725 comm="apparmor_parser"
[   17.638119] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[   17.638173] type=1400 audit(1348245202.415:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=608 comm="apparmor_parser"
[   17.638275] Registered led device: phy0-led
[   17.638292] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   17.638367] type=1400 audit(1348245202.415:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=725 comm="apparmor_parser"
[   17.638502] type=1400 audit(1348245202.415:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=608 comm="apparmor_parser"
[   17.638525] type=1400 audit(1348245202.415:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=725 comm="apparmor_parser"
[   17.638663] type=1400 audit(1348245202.415:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=608 comm="apparmor_parser"
[   17.640176] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.015966] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f02)
[   18.101062] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x17, 0x0c.
[   18.130070] fbcon: inteldrmfb (fb0) is primary device
[   18.130128] Console: switching to colour frame buffer device 170x48
[   18.130152] fb0: inteldrmfb frame buffer device
[   18.130153] drm: registered panic notifier
[   18.195090] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   18.195187] acpi device:31: registered as cooling_device13
[   18.195348] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   18.195403] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.195444] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.195483] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.195544] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   18.195570] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   18.231300] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   18.314144] init: failsafe main process (917) killed by TERM signal
[   18.314447] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input7
[   18.421341] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.421344] Bluetooth: BNEP filters: protocol multicast
[   18.421659] Bluetooth: RFCOMM TTY layer initialized
[   18.421664] Bluetooth: RFCOMM socket layer initialized
[   18.421666] Bluetooth: RFCOMM ver 1.11
[   18.664447] ppdev: user-space parallel port driver
[   18.671939] type=1400 audit(1348245203.451:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1015 comm="apparmor_parser"
[   18.672267] type=1400 audit(1348245203.451:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1015 comm="apparmor_parser"
[   18.734702] hda_codec: CX20590: BIOS auto-probing.
[   18.738747] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[   18.738797] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   18.738876] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.738946] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.788193] r8169 0000:01:00.0: eth0: link down
[   18.788598] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.788838] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.790126] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   18.797714] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   19.044030] type=1400 audit(1348245203.823:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1053 comm="apparmor_parser"
[   19.044318] type=1400 audit(1348245203.823:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1060 comm="apparmor_parser"
[   19.060783] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   19.068350] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   19.154148] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.154331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.035076] init: plymouth-stop pre-start process (1807) terminated with status 1
[   21.363536] wlan0: authenticate with 84:1b:5e:01:5d:fe (try 1)
[   21.365349] wlan0: authenticated
[   21.375143] wlan0: associate with 84:1b:5e:01:5d:fe (try 1)
[   21.378791] wlan0: RX AssocResp from 84:1b:5e:01:5d:fe (capab=0x411 status=0 aid=1)
[   21.378794] wlan0: associated
[   21.381920] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.526495] wlan0: no IPv6 routers present
[  705.747105] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  705.748246] SGI XFS Quota Management subsystem
[  705.800114] JFS: nTxBlock = 8192, nTxLock = 65536
[  705.975363] NTFS driver 2.1.30 [Flags: R/O MODULE].
[  706.335889] QNX4 filesystem 0.2.3 registered.
[  706.509958] Btrfs loaded
[ 5458.554333] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 5458.569162] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 5458.584470] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 5458.600774] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 5458.614122] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 5458.614128] psmouse serio1: issuing reconnect request
[ 6141.705668] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[ 6142.021607] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.
[ 8868.517327] INFO: task java:1200 blocked for more than 120 seconds.
[ 8868.517329] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517331] java            D 0000000000000003     0  1200      1 0x00000000
[ 8868.517334]  ffff880226f25cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517338]  ffff880226f25fd8 ffff880226f25fd8 ffff880226f25fd8 00000000000137c0
[ 8868.517340]  ffff88017d870000 ffff8802283d1700 ffff8802283d1700 ffff88023da3fa80
[ 8868.517343] Call Trace:
[ 8868.517350]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517353]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517356]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517359]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517362]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517365]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517367]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517371]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517373]  [<ffffffff8106604b>] ? do_fork+0x15b/0x2e0
[ 8868.517384]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517386]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517388]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517390]  [<ffffffff8101c668>] ? sys_clone+0x28/0x30
[ 8868.517393]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517395] INFO: task java:1202 blocked for more than 120 seconds.
[ 8868.517396] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517397] java            D 0000000000000005     0  1202      1 0x00000000
[ 8868.517399]  ffff880225c2dcc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517401]  ffff880225c2dfd8 ffff880225c2dfd8 ffff880225c2dfd8 00000000000137c0
[ 8868.517404]  ffff88017d874500 ffff8802283d0000 ffff8802283d0000 ffff88023da3fa80
[ 8868.517406] Call Trace:
[ 8868.517408]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517410]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517412]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517414]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517417]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517419]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517421]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517423]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517426]  [<ffffffff811830f5>] ? putname+0x35/0x50
[ 8868.517428]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517429]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517431]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517433]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517435] INFO: task java:1203 blocked for more than 120 seconds.
[ 8868.517436] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517437] java            D ffffffff81806200     0  1203      1 0x00000000
[ 8868.517439]  ffff880225ccfcc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517441]  ffff880225ccffd8 ffff880225ccffd8 ffff880225ccffd8 00000000000137c0
[ 8868.517443]  ffff880241a99700 ffff880228f6ae00 ffff880228f6ae00 ffff88023da3fa80
[ 8868.517446] Call Trace:
[ 8868.517448]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517450]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517452]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517454]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517456]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517458]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517460]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517462]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517464]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517465]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517467]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517469]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517471] INFO: task java:1204 blocked for more than 120 seconds.
[ 8868.517472] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517473] java            D 0000000000000000     0  1204      1 0x00000000
[ 8868.517475]  ffff880226f21cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517477]  ffff880226f21fd8 ffff880226f21fd8 ffff880226f21fd8 00000000000137c0
[ 8868.517479]  ffff880212bf8000 ffff880228f6dc00 ffff880228f6dc00 ffff88023da3fa80
[ 8868.517482] Call Trace:
[ 8868.517484]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517486]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517488]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517489]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517492]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517494]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517495]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517498]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517499]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517501]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517503]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517505]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517506] INFO: task java:1205 blocked for more than 120 seconds.
[ 8868.517507] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517508] java            D 0000000000000001     0  1205      1 0x00000000
[ 8868.517510]  ffff880225cd5cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517512]  ffff880225cd5fd8 ffff880225cd5fd8 ffff880225cd5fd8 00000000000137c0
[ 8868.517515]  ffff88023f149700 ffff880228f6c500 ffff880228f6c500 ffff88023da3fa80
[ 8868.517517] Call Trace:
[ 8868.517519]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517521]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517523]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517525]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517527]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517529]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517531]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517533]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517535]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517537]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517538]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517540]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517542] INFO: task java:1206 blocked for more than 120 seconds.
[ 8868.517543] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517544] java            D 0000000000000003     0  1206      1 0x00000000
[ 8868.517546]  ffff880225c09cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517548]  ffff880225c09fd8 ffff880225c09fd8 ffff880225c09fd8 00000000000137c0
[ 8868.517550]  ffff8802418ec500 ffff880228cbc500 ffff880228cbc500 ffff88023da3fa80
[ 8868.517553] Call Trace:
[ 8868.517555]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517557]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517559]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517560]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517563]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517565]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517566]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517569]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517571]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517573]  [<ffffffff8101ae69>] ? sched_clock+0x9/0x10
[ 8868.517574]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517576]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517578]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517579] INFO: task java:1207 blocked for more than 120 seconds.
[ 8868.517580] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517582] java            D 0000000000000002     0  1207      1 0x00000000
[ 8868.517583]  ffff880226f29cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517586]  ffff880226f29fd8 ffff880226f29fd8 ffff880226f29fd8 00000000000137c0
[ 8868.517588]  ffff88021d465c00 ffff880228cbae00 ffff880228cbae00 ffff88023da3fa80
[ 8868.517590] Call Trace:
[ 8868.517592]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517594]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517596]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517598]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517600]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517602]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517604]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517606]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517608]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517610]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517612]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517613]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517615] INFO: task java:1208 blocked for more than 120 seconds.
[ 8868.517616] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517617] java            D 0000000000000004     0  1208      1 0x00000000
[ 8868.517619]  ffff880226dd1cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517621]  ffff880226dd1fd8 ffff880226dd1fd8 ffff880226dd1fd8 00000000000137c0
[ 8868.517623]  ffff8802293a4500 ffff88023d66dc00 ffff88023d66dc00 ffff88023da3fa80
[ 8868.517626] Call Trace:
[ 8868.517628]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517630]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517632]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517633]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517636]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517638]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517639]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517641]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517643]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517645]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517647]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517649]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517650] INFO: task java:1209 blocked for more than 120 seconds.
[ 8868.517651] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517652] java            D 0000000000000005     0  1209      1 0x00000000
[ 8868.517654]  ffff880225cc1cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517656]  ffff880225cc1fd8 ffff880225cc1fd8 ffff880225cc1fd8 00000000000137c0
[ 8868.517659]  ffff880225f58000 ffff88023d66c500 ffff88023d66c500 ffff88023da3fa80
[ 8868.517661] Call Trace:
[ 8868.517663]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517665]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517667]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517669]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517671]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517673]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517675]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517677]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517679]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517680]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517682]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517684]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[ 8868.517686] INFO: task java:1210 blocked for more than 120 seconds.
[ 8868.517686] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 8868.517688] java            D 0000000000000003     0  1210      1 0x00000000
[ 8868.517690]  ffff880225cc3cc8 0000000000000082 0000000000000000 ffffffffffffffe0
[ 8868.517692]  ffff880225cc3fd8 ffff880225cc3fd8 ffff880225cc3fd8 00000000000137c0
[ 8868.517694]  ffff880228cbc500 ffff88023cf24500 ffff88023cf24500 ffff88023da3fa80
[ 8868.517696] Call Trace:
[ 8868.517698]  [<ffffffff8165850f>] schedule+0x3f/0x60
[ 8868.517700]  [<ffffffff8106b3e5>] exit_mm+0x85/0x130
[ 8868.517702]  [<ffffffff8106b5fe>] do_exit+0x16e/0x420
[ 8868.517704]  [<ffffffff8109d42f>] ? __unqueue_futex+0x3f/0x80
[ 8868.517706]  [<ffffffff81079d9a>] ? __dequeue_signal+0x6a/0xb0
[ 8868.517708]  [<ffffffff8106ba54>] do_group_exit+0x44/0xa0
[ 8868.517710]  [<ffffffff8107c91c>] get_signal_to_deliver+0x21c/0x420
[ 8868.517712]  [<ffffffff81013865>] do_signal+0x45/0x130
[ 8868.517714]  [<ffffffff810a04dc>] ? do_futex+0x7c/0x1b0
[ 8868.517716]  [<ffffffff810a071a>] ? sys_futex+0x10a/0x1a0
[ 8868.517718]  [<ffffffff81013b15>] do_notify_resume+0x65/0x80
[ 8868.517719]  [<ffffffff81662cd0>] int_signal+0x12/0x17
[10102.624996] usb 3-2: new full-speed USB device number 2 using xhci_hcd
[10102.625032] usb 3-2: Device not responding to set address.
[10102.828736] usb 3-2: Device not responding to set address.
[10103.032402] usb 3-2: device not accepting address 2, error -71
[10103.088354] hub 3-0:1.0: unable to enumerate USB device on port 2
[10194.039100] RPC: Registered named UNIX socket transport module.
[10194.039103] RPC: Registered udp transport module.
[10194.039105] RPC: Registered tcp transport module.
[10194.039107] RPC: Registered tcp NFSv4.1 backchannel transport module.
[10194.174778] FS-Cache: Loaded
[10194.209995] FS-Cache: Netfs 'nfs' registered for caching
[10194.230275] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[19145.353009] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[19145.367299] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[19145.382153] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.
sophie@sophie-Inspiron-5520:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 0c45:644a Microdia 
Bus 002 Device 003: ID 8087:07da Intel Corp. 
sophie@sophie-Inspiron-5520:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sophie/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sophie)
rpc_pipefs on /run/rpc_pipefs type rpc_pipefs (rw)
sophie@sophie-Inspiron-5520:~$ 
```
 
I hope this is helpful

---

### Post by acefromspace on 2012-09-21
Cheesemill is more qualified to help you (I just jumped in to get some of the basic info... give you a head start) Just to be sure: player is off (and stays off), connected with USB cable to computer, and player shows connection, but nothing shows on desktop (or Computer folder)? My cheapo coby just shows as 4G drive... like a USB stick/flash. The player screen showing connection just means it's charging (just a guess actually) I'm sure we will figure this out. Do you also want video on the player? Like I said, I can tell you how to convert to proper size/format (I'll learn with you) Also, is this player new (virgin?) or has it been connected to another computer before?

---

### Post by coljohnhannibalsmith on 2012-09-22
[LIST=1]
[*]Absolutely, I want video.  There are several video transcoders in the Software Center that will do this job neatly.
[/LIST]
For the time being I'm waiting for cheesemill's response to the additional data.


BTW, to get this device to load music in Windows 7 I have to use the synchronize feature.  I can't just load the music I want to a specific folder.  What a nuisance!


Thanks Hannibal

---

