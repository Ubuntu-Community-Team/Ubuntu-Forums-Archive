---
title: "lubuntu 12.10; Linksys V3 Ralink RT2070L 1737:0077 no access to internet; HOWTO?"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by floppy_stuttgart on 2013-04-20
hello,
 I installed Lubuntu on a dell optiplex, with an USB Wlan.
 The networks are recognized with WICD.
Network is WPA2 + psk encryption.
  But the internet access is not possible via wlan (LAN is fine when I connect the cable).
 It says in dmesg: "wlan0: link is not ready"; see below.
 What happens? How to solve this?
I would like to give that PC to a Windooze user.. so it must work..;-)


UPDATE: I realized there was a networkmanager on the right side bottom of the screen. I clicked on it and gave the passwort for my local wpa2 and IT WORKS.
So, I deleted WICD, booted again and it worked again with the networkmanager. I disconnected the WLAN usb, booted and pluged later the USB and IT WORKS.
So, obviously this is a WICD issue (when the Networkmanager is present?).
I dont know how to mark this thread SOLVED...
**Conclusion: that USB modem works out of the box with lubuntu 12.10**. VERY GOOD. I am happy.

 dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-27-generic (buildd@akateko) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #46-Ubuntu SMP Mon Mar 25 20:00:05 UTC 2013 (Ubuntu 3.5.0-27.46-generic 3.5.7.7)
...
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127528
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-27-generic root=/dev/mapper/lubuntu-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
...
[    1.600039] Switching to clocksource tsc
[    1.788016] usb 1-7: new high-speed USB device number 4 using ehci_hcd
[    1.937237] usb 1-7: New USB device found, idVendor=1737, idProduct=0077
[    1.937242] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.937246] usb 1-7: Product: 802.11 g WLAN
[    1.937249] usb 1-7: Manufacturer: Ralink
[    1.937252] usb 1-7: SerialNumber: 1.0
[    2.176022] usb 3-1: new low-speed USB device number 2 using uhci_hcd
[    2.344269] usb 3-1: New USB device found, idVendor=15ca, idProduct=00c3
[    2.344275] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.344279] usb 3-1: Product: USB Optical Mouse
[    2.584015] usb 3-2: new low-speed USB device number 3 using uhci_hcd
[    2.758269] usb 3-2: New USB device found, idVendor=413c, idProduct=2003
[    2.758274] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.758278] usb 3-2: Product: Dell USB Keyboard
[    2.758281] usb 3-2: Manufacturer: Dell
[    5.412131] Freeing unused kernel memory: 756k freed
[    5.412703] Write protecting the kernel text: 5960k
[    5.412725] Write protecting the kernel read-only data: 2412k
[    5.412728] NX-protecting the kernel data: 4280k
[    5.449232] udevd[91]: starting version 175
[    5.653271] tg3.c:v3.123 (March 21, 2012)
[    5.667286] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:14:22:2f:a2:33
[    5.667295] tg3 0000:02:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    5.667299] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    5.667303] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    5.730036] Floppy drive(s): fd0 is 1.44M
[    5.731568] usbcore: registered new interface driver usbhid
[    5.731574] usbhid: USB HID core driver
[    5.746201] FDC 0 is a post-1991 82077
[    5.951734] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input2
[    5.966098] hid-generic 0003:15CA:00C3.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1/input0
[    5.967953] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[    5.968426] hid-generic 0003:413C:2003.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2/input0
[    6.524084] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   16.300457] Adding 511996k swap on /dev/mapper/lubuntu-swap_1.  Priority:-1 extents:1 across:511996k 
[   16.321342] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.387669] udevd[311]: starting version 175
[   16.480093] lp: driver loaded but no devices found
[   16.600359] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   16.885500] [drm] Initialized drm 1.1.0 20060810
[   17.133467] ppdev: user-space parallel port driver
[   17.148969] Bluetooth: Core ver 2.16
[   17.155733] NET: Registered protocol family 31
[   17.155741] Bluetooth: HCI device and connection manager initialized
[   17.155745] Bluetooth: HCI socket layer initialized
[   17.155747] Bluetooth: L2CAP socket layer initialized
[   17.155759] Bluetooth: SCO socket layer initialized
[   17.163947] type=1400 audit(1366401868.059:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=506 comm="apparmor_parser"
[   17.178371] type=1400 audit(1366401868.075:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
[   17.178722] type=1400 audit(1366401868.075:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=506 comm="apparmor_parser"
[   17.192422] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.192429] Bluetooth: BNEP filters: protocol multicast
[   17.202481] type=1400 audit(1366401868.099:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=515 comm="apparmor_parser"
[   17.203239] Bluetooth: RFCOMM TTY layer initialized
[   17.203247] Bluetooth: RFCOMM socket layer initialized
[   17.203250] Bluetooth: RFCOMM ver 1.11
[   17.344429] i915 0000:00:02.0: setting latency timer to 64
[   17.358974] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.358981] [drm] Driver supports precise vblank timestamp query.
[   17.359147] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   17.439713] parport_pc 00:07: reported by Plug and Play ACPI
[   17.439779] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   17.441865] intel_rng: Firmware space is locked read-only. If you can't or
[   17.441865] intel_rng: don't want to disable this in firmware setup, and if
[   17.441865] intel_rng: you are certain that your system has a functional
[   17.441865] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.536442] lp0: using parport0 (interrupt-driven).
[   17.576718] type=1400 audit(1366401868.475:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=587 comm="apparmor_parser"
[   17.581089] type=1400 audit(1366401868.479:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=587 comm="apparmor_parser"
[   17.686312] cfg80211: Calling CRDA to update world regulatory domain
[   17.832316] microcode: CPU0 sig=0xf41, pf=0x10, revision=0xd
[   17.920366] usb 1-7: reset high-speed USB device number 4 using ehci_hcd
[   17.967110] [drm] initialized overlay support
[   18.051210] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.154134] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.154141] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154145] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.154148] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154150] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.154153] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154156] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.154159] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154162] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.154164] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154167] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.154170] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154173] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.154175] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154178] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.154181] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154184] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.154186] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154189] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.154192] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154195] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.154197] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154200] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.154203] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154206] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.154208] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.154211] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.154214] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   18.198883] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.200075] Registered led device: rt2800usb-phy0::radio
[   18.200189] Registered led device: rt2800usb-phy0::assoc
[   18.200298] Registered led device: rt2800usb-phy0::quality
[   18.200418] usbcore: registered new interface driver rt2800usb
[   18.347002] init: failsafe main process (684) killed by TERM signal
[   18.399861] i2c i2c-1: sendbytes: NAK bailout.
[   18.400395] i2c i2c-1: sendbytes: NAK bailout.
[   18.451495] i2c i2c-1: sendbytes: NAK bailout.
[   18.451974] i2c i2c-1: sendbytes: NAK bailout.
[   18.585792] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 126
[   18.585799] Raw EDID:
[   18.585803]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   18.585806]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.585808]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.585811]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.585813]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.585815]      ff ff fb ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.585818]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.585820]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.683676] type=1400 audit(1366401869.579:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=781 comm="apparmor_parser"
[   18.711878] type=1400 audit(1366401869.607:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=781 comm="apparmor_parser"
[   18.743083] type=1400 audit(1366401869.639:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=783 comm="apparmor_parser"
[   18.744874] type=1400 audit(1366401869.643:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=783 comm="apparmor_parser"
[   18.953051] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.957545] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.166806] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   19.166812] Raw EDID:
[   19.166816]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   19.166819]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.166821]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.166824]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.166826]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.166829]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.166831]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.166834]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.194967] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.194974] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.194978] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.194981] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.194984] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.194987] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.194989] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.194992] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.194995] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.194998] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195001] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.195004] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195007] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.195010] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195012] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.195015] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195018] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.195021] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195024] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.195027] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195029] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.195032] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195035] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.195038] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.195041] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.195044] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.195046] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.195049] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.195053] cfg80211: World regulatory domain updated:
[   19.195055] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.195058] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195061] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.195064] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.195067] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.195070] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.239425] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 98
[   19.239432] Raw EDID:
[   19.239436]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   19.239438]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.239441]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.239443]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.239446]      ff ff ff ff ff ff ff df ff ff ff ff ff ff ff ff
[   19.239448]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.239451]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.239453]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.263975] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   19.496404] init: alsa-restore main process (852) terminated with status 19
[   19.567922] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[   19.567930] Raw EDID:
[   19.567933]      00 ff ff ff ff ff ff 00 ff ff ff ff ff ff ff ff
[   19.567936]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567939]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567941]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567943]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567946]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567948]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567951]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.567958] i915 0000:00:02.0: VGA-1: EDID block 0 invalid.
[   19.707248] fbcon: inteldrmfb (fb0) is primary device
[   19.721841] Console: switching to colour frame buffer device 128x48
[   19.721882] fb0: inteldrmfb frame buffer device
[   19.721886] drm: registered panic notifier
[   19.721905] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.723990] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \GLBC 1 (20120320/utaddress-251)
[   19.724724] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \SACT 2 (20120320/utaddress-251)
[   19.724737] ACPI Warning: 0x00000828-0x0000082f SystemIO conflicts with Region \SSTS 3 (20120320/utaddress-251)
[   19.724744] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.725252] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   19.726018] snd_intel8x0 0000:00:1e.2: setting latency timer to 64
[   20.002232] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.002772] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.046961] gpio_ich: ACPI BAR is unavailable, GPI 0 - 15 unavailable
[   20.049633] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   20.180508] i2c i2c-1: sendbytes: NAK bailout.
[   20.180988] i2c i2c-1: sendbytes: NAK bailout.
[   20.181463] i2c i2c-1: sendbytes: NAK bailout.
[   20.181937] i2c i2c-1: sendbytes: NAK bailout.
[   20.182412] i2c i2c-1: sendbytes: NAK bailout.
[   20.216085] intel8x0_measure_ac97_clock: measured 53037 usecs (2556 samples)
[   20.216093] intel8x0: clocking to 48000
[   20.848531] i2c i2c-1: sendbytes: NAK bailout.
[   20.849014] i2c i2c-1: sendbytes: NAK bailout.
[   20.849490] i2c i2c-1: sendbytes: NAK bailout.
[   20.849966] i2c i2c-1: sendbytes: NAK bailout.
[   20.850441] i2c i2c-1: sendbytes: NAK bailout.
[   20.880532] i2c i2c-1: sendbytes: NAK bailout.
[   20.881013] i2c i2c-1: sendbytes: NAK bailout.
[   20.881488] i2c i2c-1: sendbytes: NAK bailout.
[   20.881964] i2c i2c-1: sendbytes: NAK bailout.
[   20.882439] i2c i2c-1: sendbytes: NAK bailout.
[   21.234653] init: plymouth-stop pre-start process (1082) terminated with status 1
[   23.292517] i2c i2c-1: sendbytes: NAK bailout.
[   23.292999] i2c i2c-1: sendbytes: NAK bailout.
[   23.293474] i2c i2c-1: sendbytes: NAK bailout.
[   23.294021] i2c i2c-1: sendbytes: NAK bailout.
[   23.294499] i2c i2c-1: sendbytes: NAK bailout.
[   23.340702] i2c i2c-1: sendbytes: NAK bailout.
[   23.341182] i2c i2c-1: sendbytes: NAK bailout.
[   23.341657] i2c i2c-1: sendbytes: NAK bailout.
[   23.342132] i2c i2c-1: sendbytes: NAK bailout.
[   23.342606] i2c i2c-1: sendbytes: NAK bailout.
[   26.924078] end_request: I/O error, dev fd0, sector 0
[   26.948078] end_request: I/O error, dev fd0, sector 0
[   29.569269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.908490] pcieport 0000:00:1c.0: wake-up capability enabled by ACPI
[   30.195866] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.272360] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.803855] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.196356] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   70.236346] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   70.604479] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   71.116133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   71.163276] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  129.664518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  130.180159] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  130.227089] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  130.856367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  131.300100] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  169.244376] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  169.617818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  170.148135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  170.195081] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  194.512430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  195.028191] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  195.075079] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  195.724407] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  196.184182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  234.108412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  234.464413] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  234.964179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  235.010993] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

lsmod

Module                  Size  Used by
gpio_ich               13160  0 
snd_intel8x0           33107  1 
snd_ac97_codec        105652  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
arc4                   12474  2 
snd_pcm                80235  2 snd_intel8x0,snd_ac97_codec
dcdbas                 14055  0 
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
rt2800usb              22286  0 
microcode              18210  0 
rt2800lib              57182  1 rt2800usb
crc_ccitt              12628  1 rt2800lib
psmouse                84878  0 
rt2x00usb              19980  1 rt2800usb
snd_seq_midi_event     14476  1 snd_seq_midi
rt2x00lib              48602  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
mac80211              461261  3 rt2800lib,rt2x00usb,rt2x00lib
snd_timer              24412  2 snd_pcm,snd_seq
cfg80211              175574  2 rt2x00lib,mac80211
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13032  0 
snd                    62146  9 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                16926  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_intel8x0,snd_pcm
bnep                   17708  2 
rfcomm                 37277  0 
parport_pc             31969  1 
bluetooth             183270  10 bnep,rfcomm
ppdev                  12818  0 
i915                  457241  2 
drm_kms_helper         47304  1 i915
ext2                   67205  1 
drm                   238811  3 i915,drm_kms_helper
mac_hid                13038  0 
i2c_algo_bit           13198  1 i915
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
floppy                 55445  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
tg3                   130493  0

---

