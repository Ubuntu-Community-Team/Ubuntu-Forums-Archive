---
title: "Nvidia drivers not working after 11.10 (64 bits) clean install, getting desperate"
date: 2011-10-27
forum: Multimedia Software
---

### Post by Panna-cakkhu on 2011-10-27
After a clean install of Ubuntu 11.10 (64 bits) i kept ended up in a black screen (no X, no lightdm, no nothing).

I fixed that part by removing the Nvidia drivers. (For those who have the same problem, here is what i did: boot in recovery mode and entered the following command from the root prompt: apt-get --purge remove nvidia-current)

Then when rebooting i could login. The feeling was great but that didn't last. I couldn't install any version of the nvidia drivers to get them to work:
- additional proprietary drivers proposed by ubuntu: freeze at booting
- new purge and drivers from ubuntu-x-swat/x-updates repository: freeze at booting
- new purge and vidia-173 drivers: doesn't work
- new purge and nvidia drivers from nvidia website (64-bits version): no success either

Any help would be GREATLY appreciated

System: Ubuntu 11.10 64 bits fresh install, Nvidia GTX 560

---

### Post by wolfen69 on 2011-10-27
Have you tried *nvidia-current-updates* ?

---

### Post by Panna-cakkhu on 2011-10-27
Thanks Wolfen69 but that didn't work either. After choosing text mode and deleting the options "quiet slash" in GRUB i still get a black screen after a couple of seconds.

---

### Post by wolfen69 on 2011-10-27
[Here]("http://www.nvidia.com/object/linux-display-amd64-285.05.09-driver.html") is the nvidia 285 driver for your card from the nvidia website. Perhaps you could try that.

---

### Post by Panna-cakkhu on 2011-10-27
I already tried that but it didn't work. I tried again and it was axactly the same error: black screen without any possibility to even go to any terminal console (CTRL+ALT+F1/2/3/4/...).

The only thing i can do is press the switch off button. Then some messages appear, including 2 failing warnings:

```
...
Starting load fallback graphics devices       [COLOR="Red"][fail][/COLOR] 
...
Starting automatic crash report generation    [COLOR="Red"][fail][/COLOR]
...
```

And then, as expected, my computer shutdown.

---

### Post by Panna-cakkhu on 2011-10-27
For more info here is part of the sys.log:
```
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.349127] **[COLOR="Red"]nvidia: module license 'NVIDIA' taints kernel.[/COLOR]**
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.349131] Disabling lock debugging due to kernel taint
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.431552] **[COLOR="Red"]nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/COLOR]**
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.431558] **[COLOR="Red"]nvidia 0000:01:00.0: setting latency timer to 64[/COLOR]**
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.431561] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.431609] [COLOR="Red"]**NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011**[/COLOR]
Oct 27 23:21:41 michael-cooler-UB kernel: [  277.437413] **nvidia 0000:01:00.0: PCI INT A disabled**
Oct 27 23:21:41 michael-cooler-UB kernel: [  305.094830] init: plymouth-upstart-bridge main process (2096) terminated with status 1
Oct 27 23:21:41 michael-cooler-UB kernel: [  305.135807] init: alsa-store main process (2094) terminated with status 19
Oct 27 23:21:41 michael-cooler-UB kernel: [  308.287646] usb 2-1.6: USB disconnect, device number 11
Oct 27 23:21:41 michael-cooler-UB kernel: [  309.765369] usb 2-1.6: new low speed USB device number 12 using ehci_hcd
Oct 27 23:21:41 michael-cooler-UB kernel: [  309.863715] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input10
Oct 27 23:21:41 michael-cooler-UB kernel: [  309.863808] generic-usb 0003:093A:2510.0009: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.6/input0
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.720982] lp: driver loaded but no devices found
Oct 27 23:21:41 michael-cooler-UB udev-configure-printer: add /module/lp
Oct 27 23:21:41 michael-cooler-UB udev-configure-printer: Failed to get parent
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.732266] wmi: Mapper loaded
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.733721] [drm] Initialized drm 1.1.0 20060810
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.739083] cfg80211: Calling CRDA to update world regulatory domain
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> NetworkManager (version 0.9.1.90) is starting...
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.743643] rtl8192se 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.743649] rtl8192se 0000:03:00.0: setting latency timer to 64
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.744922] type=1400 audit(1319750501.394:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=2538 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.745129] type=1400 audit(1319750501.394:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2538 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.745261] type=1400 audit(1319750501.394:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=2538 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.745306] mei: module is from the staging directory, the quality is unknown, you have been warned.
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.750488] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.750492] mei 0000:00:16.0: setting latency timer to 64
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.752328] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.752329]            Loading firmware rtlwifi/rtl8192sefw.bin
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.758646] Adding 8368124k swap on /dev/sda5.  Priority:-1 extents:1 across:8368124k 
Oct 27 23:21:41 michael-cooler-UB dbus[2525]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Oct 27 23:21:41 michael-cooler-UB mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
Oct 27 23:21:41 michael-cooler-UB mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.781449] AV200 0000:06:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.783152] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.783190] HDA Intel 0000:00:1b.0: irq 54 for MSI/MSI-X
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.783209] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 27 23:21:41 michael-cooler-UB failsafe: Failsafe of 120 seconds reached.
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.819452] asus_wmi: ASUS WMI generic driver loaded
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.819659] asus_wmi: Initialization: 0x0
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.819674] asus_wmi: BIOS WMI version: 0.9
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.819696] asus_wmi: SFUN value: 0x0
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.820022] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input11
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829707] cfg80211: World regulatory domain updated:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829709] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829710] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829711] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829712] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829713] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.829715] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.833428] hda_codec: ALC892: BIOS auto-probing.
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.838947] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.839032] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.839034] hda_intel: Disabling MSI
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.839089] HDA Intel 0000:01:00.1: setting latency timer to 64
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.875086] Adding 8366076k swap on /dev/sda7.  Priority:-2 extents:1 across:8366076k 
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.881516] type=1400 audit(1319750501.530:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=2942 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.882692] type=1400 audit(1319750501.530:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=2946 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.882818] type=1400 audit(1319750501.530:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=2943 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.882908] type=1400 audit(1319750501.530:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=2946 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.883028] type=1400 audit(1319750501.530:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2943 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.883162] type=1400 audit(1319750501.530:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=2943 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.883287] type=1400 audit(1319750501.530:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=2944 comm="apparmor_parser"
Oct 27 23:21:41 michael-cooler-UB mtp-probe: bus: 2, device: 3 was not an MTP device
Oct 27 23:21:41 michael-cooler-UB mtp-probe: bus: 2, device: 12 was not an MTP device
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893120] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893123] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893124] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893125] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893126] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893128] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893129] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893130] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893131] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893132] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893133] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893135] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893136] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893137] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893138] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893139] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893140] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893142] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893143] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893144] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893145] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893146] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893148] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893149] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893150] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893151] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893152] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.893245] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.895581] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Oct 27 23:21:41 michael-cooler-UB anacron[3031]: Anacron 2.3 started on 2011-10-27
Oct 27 23:21:41 michael-cooler-UB cron[3020]: (CRON) INFO (pidfile fd = 3)
Oct 27 23:21:41 michael-cooler-UB acpid: starting up with proc fs
Oct 27 23:21:41 michael-cooler-UB acpid: 32 rules loaded
Oct 27 23:21:41 michael-cooler-UB acpid: waiting for events: event logging is off
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.912203] init: rc main process (2092) killed by TERM signal
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.912359] init: failsafe main process (2840) killed by TERM signal
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.913058] init: apport pre-start process (3015) terminated with status 1
Oct 27 23:21:41 michael-cooler-UB kernel: [  319.917048] init: apport post-stop process (3040) terminated with status 1
Oct 27 23:21:41 michael-cooler-UB polkitd[2722]: started daemon version 0.102 using authority implementation `local' version `0.102'
Oct 27 23:21:41 michael-cooler-UB dbus[2525]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: init!
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: update_system_hostname
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPluginIfupdown: management mode: unmanaged
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlan0, iface: wlan0)
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:07:00.0/net/eth0, iface: eth0)
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:07:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: end _init.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    Ifupdown: get unmanaged devices count: 0
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: (23474992) ... get_connections.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    SCPlugin-Ifupdown: (23474992) ... get_connections (managed=false): return empty list.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    keyfile: parsing FASTWEB-1-9qKizSz833fE ... 
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    keyfile:     read connection 'FASTWEB-1-9qKizSz833fE'
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]:    Ifupdown: get unmanaged devices count: 0
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> modem-manager is now available
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> WiFi enabled by radio killswitch; enabled by state file
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> WWAN enabled by radio killswitch; enabled by state file
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> WiMAX enabled by radio killswitch; enabled by state file
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> Networking is enabled by state file
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192se' ifindex: 3)
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): now managed
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): bringing up device.
Oct 27 23:21:41 michael-cooler-UB cron[3051]: (CRON) STARTUP (fork ok)
Oct 27 23:21:41 michael-cooler-UB cron[3051]: (CRON) INFO (Running @reboot jobs)
Oct 27 23:21:41 michael-cooler-UB bluetoothd[3061]: Bluetooth daemon 4.96
Oct 27 23:21:41 michael-cooler-UB bluetoothd[3061]: Starting SDP server
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.024681] Bluetooth: Core ver 2.16
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.024695] NET: Registered protocol family 31
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.024696] Bluetooth: HCI device and connection manager initialized
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.024697] Bluetooth: HCI socket layer initialized
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.024698] Bluetooth: L2CAP socket layer initialized
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.024966] Bluetooth: SCO socket layer initialized
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.025786] Bluetooth: RFCOMM TTY layer initialized
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.025788] Bluetooth: RFCOMM socket layer initialized
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.025789] Bluetooth: RFCOMM ver 1.11
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.079809] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): preparing device.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): deactivating device (reason 'managed') [2]
Oct 27 23:21:41 michael-cooler-UB dbus[2525]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): carrier is OFF
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): now managed
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): bringing up device.
Oct 27 23:21:41 michael-cooler-UB dbus[2525]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Oct 27 23:21:41 michael-cooler-UB anacron[3031]: Normal exit (0 jobs run)
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.276712] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.276714] Bluetooth: BNEP filters: protocol multicast
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.282967] r8169 0000:07:00.0: eth0: link down
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.282991] r8169 0000:07:00.0: eth0: link down
Oct 27 23:21:41 michael-cooler-UB kernel: [  320.283306] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): preparing device.
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:07:00.0/net/eth0
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> wpa_supplicant started
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <warn> bluez error getting default adapter: No such adapter
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: starting -> ready
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Oct 27 23:21:41 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: ready -> inactive
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.786886] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.818816] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 27 23:21:42 michael-cooler-UB anacron[3181]: Anacron 2.3 started on 2011-10-27
Oct 27 23:21:42 michael-cooler-UB anacron[3181]: Normal exit (0 jobs run)
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.850787] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.886791] HDMI status: Pin=5 Presence_Detect=0 ELD_Valid=0
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.902871] i**[COLOR="Red"]nput: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input13[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.902922] **[COLOR="Red"]input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input14[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.902951] **[COLOR="Red"]input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input15[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.902978] **[COLOR="Red"]input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2/input16[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.903192] **[COLOR="Red"]nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.903199] **[COLOR="Red"]nvidia 0000:01:00.0: setting latency timer to 64[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  320.903202] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=none,decodes=none:owns=io+mem
Oct 27 23:21:42 michael-cooler-UB **[COLOR="Red"]kernel: [  320.903320] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011[/COLOR]**
Oct 27 23:21:42 michael-cooler-UB kernel: [  321.286574] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
Oct 27 23:21:42 michael-cooler-UB kernel: [  321.292509] ppdev: user-space parallel port driver
Oct 27 23:21:42 michael-cooler-UB kernel: [  321.306942] init: udev-fallback-graphics main process (3224) terminated with status 1
Oct 27 23:21:42 michael-cooler-UB kernel: [  321.308872] init: friendly-recovery post-stop process (2322) terminated with status 1
Oct 27 23:21:43 michael-cooler-UB acpid: client connected from 3259[0:0]
Oct 27 23:21:43 michael-cooler-UB acpid: 1 client rule loaded
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.465410] init: plymouth-upstart-bridge main process (2531) killed by TERM signal
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.511871] BUG: unable to handle kernel paging request at ffffc900057e3000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.512109] **[COLOR="Red"]IP: [<ffffffffa04cf468>] _nv027819rm+0xd4/0x20a [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.512355] PGD 21e819067 PUD 21e81a067 PMD 20fdda067 PTE 0
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.512699] Oops: 0000 [#1] SMP 
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.512920] CPU 1 
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.512986] **[COLOR="Red"]Modules linked in: parport_pc ppdev snd_hda_codec_hdmi bnep nvidia(P) nouveau rfcomm bluetooth arc4 joydev snd_hda_codec_realtek eeepc_wmi asus_wmi sparse_keymap psmouse serio_raw snd_hda_intel snd_hda_codec snd_hwdep snd_virtuoso snd_oxygen_lib snd_pcm snd_mpu401_uart snd_seq_midi snd_seq_midi_event snd_seq snd_rawmidi snd_timer snd_seq_device snd mei(C) rtl8192se rtlwifi mac80211 soundcore snd_page_alloc cfg80211 ttm drm_kms_helper drm i2c_algo_bit mxm_wmi wmi video lp parport binfmt_misc usbhid hid ahci libahci firewire_ohci firewire_core crc_itu_t r8169 pata_marvell xhci_hcd [last unloaded: nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.517047] 
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.517144] Pid: 3259, comm: Xorg Tainted: P         C  3.0.0-12-generic #20-Ubuntu System manufacturer System Product Name/P8P67 LE
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.517491] **[COLOR="Red"]RIP: 0010:[<ffffffffa04cf468>]  [<ffffffffa04cf468>] _nv027819rm+0xd4/0x20a [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.517759] RSP: 0018:ffff8801f22d98c8  EFLAGS: 00010202
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.517872] RAX: 000000000000003c RBX: 0000000000000000 RCX: 000000000000003c
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.517992] RDX: 0000000000000008 RSI: 0000000000000000 RDI: 0000000000000000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518113] RBP: ffff8801f8e25f30 R08: 00000000df475fff R09: ffff880000000000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518234] R10: 0000000000000081 R11: 0000000000000000 R12: 0000000000000059
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518354] R13: ffffc900057e2ff8 R14: ffff88021262e800 R15: ffff88021262e000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518475] FS:  00007f9d7226e8a0(0000) GS:ffff88021f480000(0000) knlGS:0000000000000000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518633] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518747] CR2: ffffc900057e3000 CR3: 00000002113a9000 CR4: 00000000000406e0
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518868] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.518988] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.519109] Process Xorg (pid: 3259, threadinfo ffff8801f22d8000, task ffff88020ea8ae40)
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.519266] Stack:
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.519364]  ffff88021262e800 ffff88021262e000 ffff88021262e800 ffff8801f9aca000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.519745]  000000000000001e ffffffffa04cf62c ffff88020edc3000 ffff88020edc3000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.520126]  ffff8801f9aca000 ffffffffa04ca838 ffff88020edc3000 ffff8801f9aca000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.520508] Call Trace:
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.520657]  **[COLOR="Red"][<ffffffffa04cf62c>] ? _nv023077rm+0x8e/0x9e [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.520821]  **[COLOR="Red"][<ffffffffa04ca838>] ? _nv023034rm+0xcf/0x301 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.520986]  **[COLOR="Red"][<ffffffffa04cab15>] ? _nv023084rm+0xab/0x174 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.521150]  **[COLOR="Red"][<ffffffffa04cac2e>] ? _nv023033rm+0x50/0x5d [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.521314]  **[COLOR="Red"][<ffffffffa04d189d>] ? _nv023025rm+0x6e/0x78 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.521514]  **[COLOR="Red"][<ffffffffa0b169e8>] ? _nv019727rm+0x69/0x121 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.521711]  **[COLOR="Red"][<ffffffffa0b16966>] ? _nv019741rm+0xe8/0x101 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.521885]  **[COLOR="Red"][<ffffffffa0510d61>] ? _nv004809rm+0x68/0x233 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.522108]  [COLOR="Red"]**[<ffffffffa08b965b>] ? _nv015370rm+0x19a/0x4e7 [nvidia]**[/COLOR]
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.522330]  **[COLOR="Red"][<ffffffffa08b8196>] ? _nv015669rm+0xe9/0x165 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.522491]  **[COLOR="Red"][<ffffffffa0495200>] ? _nv015862rm+0xd/0x12 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.522687]  **[COLOR="Red"][<ffffffffa0b16711>] ? _nv002340rm+0x19d/0x2a6 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.522882]  **[COLOR="Red"][<ffffffffa0b177f8>] ? _nv002334rm+0x4df/0x6e4 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523077]  **[COLOR="Red"][<ffffffffa0b0e294>] ? rm_init_adapter+0x9e/0x1b6 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523271]  **[COLOR="Red"][<ffffffffa0b31234>] ? nv_kern_open+0x414/0x7a0 [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523391]  [<ffffffff8116ae30>] ? mount_fs+0x1b0/0x1b0
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523504]  [<ffffffff8116b87a>] ? chrdev_open+0xda/0x230
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523619]  [<ffffffff811653d4>] ? __dentry_open+0x144/0x320
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523733]  [<ffffffff8116b7a0>] ? cdev_put+0x30/0x30
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523846]  [<ffffffff81166b1d>] ? nameidata_to_filp+0xad/0xb0
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.523962]  [<ffffffff81175550>] ? do_last+0x3a0/0x700
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524075]  [<ffffffff81176ada>] ? path_openat+0xca/0x3f0
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524191]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524306]  [<ffffffff81176e42>] ? do_filp_open+0x42/0xa0
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524421]  [<ffffffff812f4761>] ? strncpy_from_user+0x31/0x40
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524537]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524651]  [<ffffffff811841f7>] ? alloc_fd+0xf7/0x150
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524764]  [<ffffffff81166c0d>] ? do_sys_open+0xed/0x220
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524878]  [<ffffffff811867ef>] ? mntput+0x1f/0x30
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.524990]  [<ffffffff81166d60>] ? sys_open+0x20/0x30
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.525103]  [<ffffffff815f22c2>] ? system_call_fastpath+0x16/0x1b
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.525219] Code: ff 97 88 02 00 00 49 89 c5 48 85 c0 75 0c c7 45 08 32 00 00 00 e9 24 01 00 00 ba 00 00 00 00 8b 45 0c 48 89 c1 48 83 f8 00 76 0d 
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.529237] **[COLOR="Red"]RIP  [<ffffffffa04cf468>] _nv027819rm+0xd4/0x20a [nvidia][/COLOR]**
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.529460]  RSP <ffff8801f22d98c8>
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.529564] CR2: ffffc900057e3000
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.529669] ---[ end trace f64d3efffba104f4 ]---
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.773809] init: plymouth-stop pre-start process (3294) terminated with status 1
Oct 27 23:21:43 michael-cooler-UB udev-configure-printer: add /module/lp
Oct 27 23:21:43 michael-cooler-UB udev-configure-printer: Failed to get parent
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.929224] r8169 0000:07:00.0: eth0: link up
Oct 27 23:21:43 michael-cooler-UB kernel: [  321.929659] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (eth0): carrier now ON (device state 20)
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Auto-activating connection 'Wired connection 1'.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) starting connection 'Wired connection 1'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> dhclient started with pid 3301
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Oct 27 23:21:43 michael-cooler-UB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 27 23:21:43 michael-cooler-UB dhclient: Copyright 2004-2010 Internet Systems Consortium.
Oct 27 23:21:43 michael-cooler-UB dhclient: All rights reserved.
Oct 27 23:21:43 michael-cooler-UB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 27 23:21:43 michael-cooler-UB dhclient: 
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Oct 27 23:21:43 michael-cooler-UB dhclient: Listening on LPF/eth0/f4:6d:04:65:72:83
Oct 27 23:21:43 michael-cooler-UB dhclient: Sending on   LPF/eth0/f4:6d:04:65:72:83
Oct 27 23:21:43 michael-cooler-UB dhclient: Sending on   Socket/fallback
Oct 27 23:21:43 michael-cooler-UB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Auto-activating connection 'FASTWEB-1-9qKizSz833fE'.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) starting connection 'FASTWEB-1-9qKizSz833fE'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0/wireless): connection 'FASTWEB-1-9qKizSz833fE' has security, and secrets exist.  No new secrets needed.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Config: added 'ssid' value 'FASTWEB-1-9qKizSz833fE'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Config: added 'scan_ssid' value '1'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Config: added 'auth_alg' value 'OPEN'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Config: added 'psk' value '<omitted>'
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> Config: set interface ap_scan to 1
Oct 27 23:21:43 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: inactive -> scanning
Oct 27 23:21:44 michael-cooler-UB wpa_supplicant[3098]: Trying to authenticate with e0:91:53:5a:ae:54 (SSID='FASTWEB-1-9qKizSz833fE' freq=2462 MHz)
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.068680] wlan0: authenticate with e0:91:53:5a:ae:54 (try 1)
Oct 27 23:21:44 michael-cooler-UB wpa_supplicant[3098]: Trying to associate with e0:91:53:5a:ae:54 (SSID='FASTWEB-1-9qKizSz833fE' freq=2462 MHz)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.072952] wlan0: authenticated
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.093005] wlan0: associate with e0:91:53:5a:ae:54 (try 1)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.099600] wlan0: RX AssocResp from e0:91:53:5a:ae:54 (capab=0x431 status=0 aid=3)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.099761] wlan0: associated
Oct 27 23:21:44 michael-cooler-UB wpa_supplicant[3098]: Associated with e0:91:53:5a:ae:54
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.101207] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.101358] cfg80211: Calling CRDA for country: IT
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103099] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103267] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103388] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103555] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103675] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103842] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.103962] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104129] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104249] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104416] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104536] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104711] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: associating -> associated
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104832] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.104999] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.105119] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.105286] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107077] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107244] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107365] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107538] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107658] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107825] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.107946] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108113] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108233] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108400] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108520] cfg80211: Disabling freq 2484 MHz
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108630] cfg80211: Regulatory domain changed to country: IT
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108747] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.108906] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.109062] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.109217] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 27 23:21:44 michael-cooler-UB kernel: [  323.109372] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Oct 27 23:21:44 michael-cooler-UB wpa_supplicant[3098]: WPA: Key negotiation completed with e0:91:53:5a:ae:54 [PTK=TKIP GTK=TKIP]
Oct 27 23:21:44 michael-cooler-UB wpa_supplicant[3098]: CTRL-EVENT-CONNECTED - Connection to e0:91:53:5a:ae:54 completed (auth) [id=0 id_str=]
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): supplicant interface state: group handshake -> completed
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'FASTWEB-1-9qKizSz833fE'.
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> dhclient started with pid 3307
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Beginning IP6 addrconf.
Oct 27 23:21:44 michael-cooler-UB dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 27 23:21:44 michael-cooler-UB dhclient: Copyright 2004-2010 Internet Systems Consortium.
Oct 27 23:21:44 michael-cooler-UB dhclient: All rights reserved.
Oct 27 23:21:44 michael-cooler-UB dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 27 23:21:44 michael-cooler-UB dhclient: 
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 27 23:21:44 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 27 23:21:44 michael-cooler-UB dhclient: Listening on LPF/wlan0/00:1f:1f:fa:81:43
Oct 27 23:21:44 michael-cooler-UB dhclient: Sending on   LPF/wlan0/00:1f:1f:fa:81:43
Oct 27 23:21:44 michael-cooler-UB dhclient: Sending on   Socket/fallback
Oct 27 23:21:44 michael-cooler-UB dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 27 23:21:46 michael-cooler-UB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 27 23:21:46 michael-cooler-UB dhclient: DHCPOFFER of 192.168.1.128 from 192.168.1.254
Oct 27 23:21:46 michael-cooler-UB dhclient: DHCPREQUEST of 192.168.1.128 on wlan0 to 255.255.255.255 port 67
Oct 27 23:21:46 michael-cooler-UB dhclient: DHCPACK of 192.168.1.128 from 192.168.1.254
Oct 27 23:21:46 michael-cooler-UB dhclient: bound to 192.168.1.128 -- renewal in 757 seconds.
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   address 192.168.1.128
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   prefix 24 (255.255.255.0)
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   gateway 192.168.1.254
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   hostname 'michael-cooler-UB'
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   nameserver '62.101.93.101'
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   nameserver '83.103.25.250'
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   domain name 'fastwebnet.it'
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info>   wins '192.168.1.254'
Oct 27 23:21:46 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 27 23:21:47 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Oct 27 23:21:47 michael-cooler-UB NetworkManager[2676]: <info> Policy set 'FASTWEB-1-9qKizSz833fE' (wlan0) as default for IPv4 routing and DNS.
Oct 27 23:21:47 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) successful, device activated.
Oct 27 23:21:47 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 27 23:21:47 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Oct 27 23:21:47 michael-cooler-UB dbus[2525]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct 27 23:21:47 michael-cooler-UB dbus[2525]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct 27 23:21:50 michael-cooler-UB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct 27 23:21:54 michael-cooler-UB kernel: [  332.751611] eth0: no IPv6 routers present
Oct 27 23:21:55 michael-cooler-UB kernel: [  333.390987] wlan0: no IPv6 routers present
Oct 27 23:21:55 michael-cooler-UB ntpdate[3355]: adjust time server 91.189.94.4 offset -0.087682 sec
Oct 27 23:22:00 michael-cooler-UB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Oct 27 23:22:05 michael-cooler-UB NetworkManager[2676]: <info> (wlan0): IP6 addrconf timed out or failed.
Oct 27 23:22:05 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Oct 27 23:22:05 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Oct 27 23:22:05 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Oct 27 23:22:05 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Oct 27 23:22:05 michael-cooler-UB NetworkManager[2676]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Oct 27 23:22:19 michael-cooler-UB kernel: [  357.904610] usb 2-1.6: USB disconnect, device number 12
Oct 27 23:22:20 michael-cooler-UB dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Oct 27 23:22:21 michael-cooler-UB kernel: [  359.383225] usb 2-1.6: new low speed USB device number 13 using ehci_hcd
Oct 27 23:22:21 michael-cooler-UB mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
Oct 27 23:22:21 michael-cooler-UB kernel: [  359.482025] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input17
Oct 27 23:22:21 michael-cooler-UB kernel: [  359.482241] generic-usb 0003:093A:2510.000A: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.6/input0
Oct 27 23:22:21 michael-cooler-UB mtp-probe: bus: 2, device: 13 was not an MTP device
Oct 27 23:22:25 michael-cooler-UB acpid: client 3259[0:0] has disconnected
Oct 27 23:22:25 michael-cooler-UB kernel: Kernel logging (proc) stopped.
Oct 27 23:22:25 michael-cooler-UB rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="2527" x-info="http://www.rsyslog.com"] exiting on signal 15.
Oct 27 23:24:00 michael-cooler-UB kernel: imklog 5.8.1, log source = /proc/kmsg started.
Oct 27 23:24:00 michael-cooler-UB rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="906" x-info="http://www.rsyslog.com"] start
Oct 27 23:24:00 michael-cooler-UB rsyslogd: rsyslogd's groupid changed to 103
Oct 27 23:24:00 michael-cooler-UB rsyslogd: rsyslogd's userid changed to 101
Oct 27 23:24:00 michael-cooler-UB rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Linux version 3.0.0-12-generic (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 (Ubuntu 3.0.0-12.20-generic 3.0.4)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c2821ccf-ec76-4150-b7ff-d0f5571fa545 ro nomodeset vt.handoff=7
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] KERNEL supported cpus:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   Intel GenuineIntel
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   AMD AuthenticAMD
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   Centaur CentaurHauls
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000df422000 (usable)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df422000 - 00000000df476000 (ACPI NVS)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df476000 - 00000000df5a9000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5a9000 - 00000000df5ba000 (ACPI NVS)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5ba000 - 00000000df5d1000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5d1000 - 00000000df5d3000 (usable)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5d3000 - 00000000df5d4000 (ACPI NVS)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5d4000 - 00000000df5dc000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5dc000 - 00000000df5e6000 (ACPI NVS)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df5e6000 - 00000000df642000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df642000 - 00000000df685000 (ACPI NVS)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000df685000 - 00000000df800000 (usable)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000021f800000 (usable)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] DMI 2.6 present.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] DMI: System manufacturer System Product Name/P8P67 LE, BIOS 1017 06/13/2011
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] No AGP bridge found
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] last_pfn = 0x21f800 max_arch_pfn = 0x400000000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] MTRR default type: uncachable
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   00000-9FFFF write-back
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   C0000-CFFFF write-protect
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   D0000-E7FFF uncachable
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   E8000-FFFFF write-protect
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] MTRR variable ranges enabled:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   0 base 000000000 mask E00000000 write-back
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   1 base 200000000 mask FE0000000 write-back
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   3 base 21F800000 mask FFF800000 uncachable
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   4 disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   5 disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   6 disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   7 disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   8 disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   9 disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] original variable MTRRs
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 0, base: 0GB, range: 8GB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 1, base: 8GB, range: 512MB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 3, base: 8696MB, range: 8MB, type UC
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] total RAM covered: 8184M
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Found optimal setting for mtrr clean up
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 6  	lose cover RAM: 0G
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] New variable MTRRs
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 2, base: 3GB, range: 512MB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 4, base: 8GB, range: 512MB, type WB
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] reg 5, base: 8696MB, range: 8MB, type UC
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] last_pfn = 0xdf800 max_arch_pfn = 0x400000000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] found SMP MP-table at [ffff8800000fceb0] fceb0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] initial memory mapped : 0 - 20000000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000df800000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  0000000000 - 00df800000 page 2M
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] kernel direct mapping tables up to df800000 @ df7fb000-df800000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000021f800000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  0100000000 - 021f800000 page 2M
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] kernel direct mapping tables up to 21f800000 @ 21f7f6000-21f800000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] RAMDISK: 365b8000 - 372d4000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: RSDP 00000000000f0420 00024 (v02 ALASKA)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: XSDT 00000000df46d068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: FACP 00000000df474d80 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: DSDT 00000000df46d140 07C3B (v02 ALASKA    A M I 00000000 INTL 20051117)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: FACS 00000000df5ddf80 00040
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: APIC 00000000df474e78 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: SSDT 00000000df474ef0 00102 (v01 AMICPU     PROC 00000001 MSFT 03000001)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: MCFG 00000000df474ff8 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: HPET 00000000df475038 00038 (v01 ALASKA    A M I 01072009 AMI. 00000004)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] No NUMA configuration found
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Faking a node at 0000000000000000-000000021f800000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000021f800000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   NODE_DATA [000000021f7fb000 - 000000021f7fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880216e00000-ffff88021dffffff] on node 0

```

---

### Post by Panna-cakkhu on 2011-10-27
PART 2
```

Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Zone PFN ranges:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   Normal   0x00100000 -> 0x0021f800
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Movable zone start PFN for each node
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] early_node_map[5] active PFN ranges
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]     0: 0x00000100 -> 0x000df422
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]     0: 0x000df5d1 -> 0x000df5d3
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]     0: 0x000df685 -> 0x000df800
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]     0: 0x00100000 -> 0x0021f800
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] On node 0 totalpages: 2092332
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA zone: 5 pages reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA zone: 3920 pages, LIFO batch:0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   DMA32 zone: 896471 pages, LIFO batch:31
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   Normal zone: 16100 pages used for memmap
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000]   Normal zone: 1161500 pages, LIFO batch:31
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] nr_irqs_gsi: 40
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df422000 - 00000000df476000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df476000 - 00000000df5a9000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df5a9000 - 00000000df5ba000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df5ba000 - 00000000df5d1000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df5d3000 - 00000000df5d4000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df5d4000 - 00000000df5dc000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df5dc000 - 00000000df5e6000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df5e6000 - 00000000df642000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df642000 - 00000000df685000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000df800000 - 00000000fed1c000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Allocating PCI resources starting at df800000 (gap: df800000:1f51c000)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021f400000 s79616 r8192 d22784 u524288
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] pcpu-alloc: s79616 r8192 d22784 u524288 alloc=1*2097152
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2061891
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Policy zone: Normal
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c2821ccf-ec76-4150-b7ff-d0f5571fa545 ro nomodeset vt.handoff=7
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Checking aperture...
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] No AGP bridge found
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Memory: 8159092k/8904704k available (6104k kernel code, 535376k absent, 210236k reserved, 4880k data, 984k init)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Hierarchical RCU implementation.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Extended CMOS year: 2000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] vt handoff: transparent VT on vt#7
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Console: colour VGA+ 80x25
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] console [tty0] enabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] hpet clockevent registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000000] Fast TSC calibration using PIT
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.004000] Detected 3310.679 MHz processor.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6621.35 BogoMIPS (lpj=13242716)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000004] pid_max: default: 32768 minimum: 301
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000019] Security Framework initialized
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000028] AppArmor: AppArmor initialized
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000029] Yama: becoming mindful.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.000568] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.001818] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002314] Mount-cache hash table entries: 256
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002379] Initializing cgroup subsys cpuacct
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002382] Initializing cgroup subsys memory
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002386] Initializing cgroup subsys devices
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002388] Initializing cgroup subsys freezer
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002389] Initializing cgroup subsys net_cls
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002390] Initializing cgroup subsys blkio
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002393] Initializing cgroup subsys perf_event
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002411] CPU: Physical Processor ID: 0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002412] CPU: Processor Core ID: 0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002415] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002416] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002418] mce: CPU supports 9 MCE banks
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002427] CPU0: Thermal monitoring enabled (TM1)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.002434] using mwait in idle threads.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.004093] ACPI: Core revision 20110413
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.012024] ftrace: allocating 25651 entries in 101 pages
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.019017] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.058662] CPU0: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz stepping 07
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164016] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164021] ... version:                3
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164022] ... bit width:              48
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164023] ... generic registers:      8
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164023] ... value mask:             0000ffffffffffff
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164024] ... max period:             000000007fffffff
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164025] ... fixed-purpose events:   3
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164026] ... event mask:             00000007000000ff
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164275] Booting Node   0, Processors  #1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.164277] smpboot cpu 1: start_ip = 98000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.272040]  #2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.272042] smpboot cpu 2: start_ip = 98000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.379901]  #3 Ok.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.379902] smpboot cpu 3: start_ip = 98000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.487815] Brought up 4 CPUs
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.487817] Total of 4 processors activated (26485.64 BogoMIPS).
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.489620] devtmpfs: initialized
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.489698] PM: Registering ACPI NVS region at df422000 (344064 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.489703] PM: Registering ACPI NVS region at df5a9000 (69632 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.489705] PM: Registering ACPI NVS region at df5d3000 (4096 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.489706] PM: Registering ACPI NVS region at df5dc000 (40960 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.489708] PM: Registering ACPI NVS region at df642000 (274432 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490586] print_constraints: dummy: 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490610] Time: 23:23:44  Date: 10/27/11
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490629] NET: Registered protocol family 16
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490689] ACPI: bus type pci registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490692] Trying to unpack rootfs image as initramfs...
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490733] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490735] PCI: not using MMCONFIG
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.490736] PCI: Using configuration type 1 for base access
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.491123] bio: create slab <bio-0> at 0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.491819] ACPI: EC: Look up EC in DSDT
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.492429] ACPI: Executed 1 blocks of module-level executable AML code
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.493772] ACPI Error: [RAMB] Namespace lookup failure, AE_NOT_FOUND (20110413/psargs-359)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.493776] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20110413/nsinit-349)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.493928] ACPI: SSDT 00000000df5dcc18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494118] ACPI: Dynamic OEM Table Load:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494120] ACPI: SSDT           (null) 0038C (v01    AMI      IST 00000001 MSFT 03000001)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494134] ACPI: SSDT 00000000df5dde18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494291] ACPI: Dynamic OEM Table Load:
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494292] ACPI: SSDT           (null) 00084 (v01    AMI      CST 00000001 MSFT 03000001)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494562] ACPI: Interpreter enabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494564] ACPI: (supports S0 S1 S3 S4 S5)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494576] ACPI: Using IOAPIC for interrupt routing
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494591] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.494635] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.504521] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507108] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507192] ACPI: No dock devices found.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507193] HEST: Table not found.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507195] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507307] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507433] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507434] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507436] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507437] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000dffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507438] pci_root PNP0A08:00: host bridge window [mem 0xe4000000-0xffffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507446] pci 0000:00:00.0: [8086:0100] type 0 class 0x000600
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507470] pci 0000:00:01.0: [8086:0101] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507488] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507490] pci 0000:00:01.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507526] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507548] pci 0000:00:16.0: reg 10: [mem 0xfb508000-0xfb50800f 64bit]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507603] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507606] pci 0000:00:16.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507634] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507653] pci 0000:00:1a.0: reg 10: [mem 0xfb507000-0xfb5073ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507725] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507728] pci 0000:00:1a.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507748] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507761] pci 0000:00:1b.0: reg 10: [mem 0xfb500000-0xfb503fff 64bit]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507810] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507813] pci 0000:00:1b.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507830] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507887] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507890] pci 0000:00:1c.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507911] pci 0000:00:1c.2: [8086:1c14] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507968] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507971] pci 0000:00:1c.2: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.507990] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508047] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508050] pci 0000:00:1c.3: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508069] pci 0000:00:1c.4: [8086:244e] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508126] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508129] pci 0000:00:1c.4: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508148] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508205] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508207] pci 0000:00:1c.5: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508226] pci 0000:00:1c.6: [8086:1c1c] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508283] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508286] pci 0000:00:1c.6: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508305] pci 0000:00:1c.7: [8086:1c1e] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508362] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508365] pci 0000:00:1c.7: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508389] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508408] pci 0000:00:1d.0: reg 10: [mem 0xfb506000-0xfb5063ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508475] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508479] pci 0000:00:1d.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508499] pci 0000:00:1f.0: [8086:1c46] type 0 class 0x000601
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508605] pci 0000:00:1f.2: [8086:1c02] type 0 class 0x000106
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508621] pci 0000:00:1f.2: reg 10: [io  0xf070-0xf077]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508627] pci 0000:00:1f.2: reg 14: [io  0xf060-0xf063]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508634] pci 0000:00:1f.2: reg 18: [io  0xf050-0xf057]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508641] pci 0000:00:1f.2: reg 1c: [io  0xf040-0xf043]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508647] pci 0000:00:1f.2: reg 20: [io  0xf020-0xf03f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508654] pci 0000:00:1f.2: reg 24: [mem 0xfb505000-0xfb5057ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508683] pci 0000:00:1f.2: PME# supported from D3hot
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508685] pci 0000:00:1f.2: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508699] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508712] pci 0000:00:1f.3: reg 10: [mem 0xfb504000-0xfb5040ff 64bit]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508731] pci 0000:00:1f.3: reg 20: [io  0xf000-0xf01f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508774] pci 0000:01:00.0: [10de:1080] type 0 class 0x000300
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508781] pci 0000:01:00.0: reg 10: [mem 0xfa000000-0xfaffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508789] pci 0000:01:00.0: reg 14: [mem 0xe8000000-0xefffffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508797] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508803] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508809] pci 0000:01:00.0: reg 30: [mem 0xfb000000-0xfb07ffff pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508841] pci 0000:01:00.1: [10de:0e09] type 0 class 0x000403
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.508849] pci 0000:01:00.1: reg 10: [mem 0xfb080000-0xfb083fff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515687] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515689] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515691] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfb0fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515693] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515734] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515737] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515741] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515746] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515805] pci 0000:03:00.0: [10ec:8172] type 0 class 0x000280
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515824] pci 0000:03:00.0: reg 10: [io  0xd000-0xd0ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515838] pci 0000:03:00.0: reg 14: [mem 0xfb400000-0xfb403fff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515937] pci 0000:03:00.0: supports D1 D2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515938] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.515942] pci 0000:03:00.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523682] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523686] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523689] pci 0000:00:1c.2:   bridge window [mem 0xfb400000-0xfb4fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523694] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523736] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523739] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523742] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523747] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523801] pci 0000:05:00.0: [1b21:1080] type 1 class 0x000604
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523903] pci 0000:00:1c.4: PCI bridge to [bus 05-06] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523906] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523909] pci 0000:00:1c.4:   bridge window [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523914] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523916] pci 0000:00:1c.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523918] pci 0000:00:1c.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523919] pci 0000:00:1c.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523921] pci 0000:00:1c.4:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523922] pci 0000:00:1c.4:   bridge window [mem 0xe4000000-0xffffffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.523981] pci 0000:06:02.0: [13f6:8788] type 0 class 0x000401
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524011] pci 0000:06:02.0: reg 10: [io  0xc000-0xc0ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524136] pci 0000:06:02.0: supports D1 D2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524162] pci 0000:06:03.0: [1106:3044] type 0 class 0x000c00
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524192] pci 0000:06:03.0: reg 10: [mem 0xfb300000-0xfb3007ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524209] pci 0000:06:03.0: reg 14: [io  0xc100-0xc17f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524320] pci 0000:06:03.0: supports D2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524321] pci 0000:06:03.0: PME# supported from D2 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524327] pci 0000:06:03.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524400] pci 0000:05:00.0: PCI bridge to [bus 06-06] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524409] pci 0000:05:00.0:   bridge window [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524414] pci 0000:05:00.0:   bridge window [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524423] pci 0000:05:00.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524424] pci 0000:05:00.0:   bridge window [io  0xc000-0xcfff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524426] pci 0000:05:00.0:   bridge window [mem 0xfb300000-0xfb3fffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524427] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524429] pci 0000:05:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524430] pci 0000:05:00.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524432] pci 0000:05:00.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524433] pci 0000:05:00.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524434] pci 0000:05:00.0:   bridge window [mem 0x000c8000-0x000dffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524436] pci 0000:05:00.0:   bridge window [mem 0xe4000000-0xffffffff] (subtractive decode)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524507] pci 0000:07:00.0: [10ec:8168] type 0 class 0x000200
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524526] pci 0000:07:00.0: reg 10: [io  0xb000-0xb0ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524559] pci 0000:07:00.0: reg 18: [mem 0xf2104000-0xf2104fff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524579] pci 0000:07:00.0: reg 20: [mem 0xf2100000-0xf2103fff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524637] pci 0000:07:00.0: supports D1 D2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524638] pci 0000:07:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.524643] pci 0000:07:00.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531675] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531678] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531681] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531687] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531744] pci 0000:08:00.0: [1b4b:91a0] type 0 class 0x000101
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531761] pci 0000:08:00.0: reg 10: [io  0xa090-0xa097]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531773] pci 0000:08:00.0: reg 14: [io  0xa080-0xa083]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531784] pci 0000:08:00.0: reg 18: [io  0xa070-0xa077]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531796] pci 0000:08:00.0: reg 1c: [io  0xa060-0xa063]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531807] pci 0000:08:00.0: reg 20: [io  0xa050-0xa05f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531819] pci 0000:08:00.0: reg 24: [mem 0xfb215000-0xfb2157ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531831] pci 0000:08:00.0: reg 30: [mem 0xfb200000-0xfb20ffff pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531866] pci 0000:08:00.0: PME# supported from D3hot
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531870] pci 0000:08:00.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531904] pci 0000:08:00.1: [1b4b:91a4] type 0 class 0x000101
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531920] pci 0000:08:00.1: reg 10: [io  0xa040-0xa047]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531931] pci 0000:08:00.1: reg 14: [io  0xa030-0xa033]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531943] pci 0000:08:00.1: reg 18: [io  0xa020-0xa027]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531955] pci 0000:08:00.1: reg 1c: [io  0xa010-0xa013]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531967] pci 0000:08:00.1: reg 20: [io  0xa000-0xa00f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531978] pci 0000:08:00.1: reg 24: [mem 0xfb214000-0xfb21400f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.531990] pci 0000:08:00.1: reg 30: [mem 0xfb210000-0xfb213fff pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.532025] pci 0000:08:00.1: PME# supported from D3hot
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.532029] pci 0000:08:00.1: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539665] pci 0000:00:1c.6: PCI bridge to [bus 08-08]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539669] pci 0000:00:1c.6:   bridge window [io  0xa000-0xafff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539672] pci 0000:00:1c.6:   bridge window [mem 0xfb200000-0xfb2fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539677] pci 0000:00:1c.6:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539743] pci 0000:09:00.0: [1b21:1042] type 0 class 0x000c03
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539771] pci 0000:09:00.0: reg 10: [mem 0xfb100000-0xfb107fff 64bit]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539892] pci 0000:09:00.0: PME# supported from D3hot D3cold
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.539897] pci 0000:09:00.0: PME# disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547658] pci 0000:00:1c.7: PCI bridge to [bus 09-09]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547662] pci 0000:00:1c.7:   bridge window [io  0xf000-0x0000] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547666] pci 0000:00:1c.7:   bridge window [mem 0xfb100000-0xfb1fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547671] pci 0000:00:1c.7:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547705] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547818] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4.BR16._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547880] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX6._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547910] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX7._PRT]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.547979]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.548099]  pci0000:00: ACPI _OSC control (0x1c) granted
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550352] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550381] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550407] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550433] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550461] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550487] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550512] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550538] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550597] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550600] vgaarb: loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550600] vgaarb: bridge control possible 0000:01:00.0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550696] SCSI subsystem initialized
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550728] libata version 3.00 loaded.
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550749] usbcore: registered new interface driver usbfs
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550754] usbcore: registered new interface driver hub
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550767] usbcore: registered new device driver usb
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.550807] PCI: Using ACPI for IRQ routing
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552123] PCI: pci_cache_line_size set to 64 bytes
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552205] reserve RAM buffer: 000000000009d400 - 000000000009ffff 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552206] reserve RAM buffer: 00000000df422000 - 00000000dfffffff 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552208] reserve RAM buffer: 00000000df5d3000 - 00000000dfffffff 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552210] reserve RAM buffer: 00000000df800000 - 00000000dfffffff 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552211] reserve RAM buffer: 000000021f800000 - 000000021fffffff 
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552260] NetLabel: Initializing
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552261] NetLabel:  domain hash size = 128
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552262] NetLabel:  protocols = UNLABELED CIPSOv4
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552269] NetLabel:  unlabeled traffic allowed by default
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552295] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.552299] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.554310] Switching to clocksource hpet
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.555641] Switched to NOHz mode on CPU #0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.555688] Switched to NOHz mode on CPU #2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.555718] Switched to NOHz mode on CPU #1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.555754] Switched to NOHz mode on CPU #3
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557569] AppArmor: AppArmor Filesystem Enabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557583] pnp: PnP ACPI init
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557590] ACPI: bus type pnp registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557679] pnp 00:00: [bus 00-ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557681] pnp 00:00: [io  0x0cf8-0x0cff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557682] pnp 00:00: [io  0x0000-0x0cf7 window]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557683] pnp 00:00: [io  0x0d00-0xffff window]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557685] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557686] pnp 00:00: [mem 0x000c8000-0x000dffff window]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557687] pnp 00:00: [mem 0xe4000000-0xffffffff window]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557688] pnp 00:00: [mem 0x00000000 window]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557723] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557757] pnp 00:01: [mem 0xfed10000-0xfed19fff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557759] pnp 00:01: [mem 0xe0000000-0xe3ffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557760] pnp 00:01: [mem 0xfed90000-0xfed93fff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557761] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557762] pnp 00:01: [mem 0xfee00000-0xfee0ffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557789] system 00:01: [mem 0xfed10000-0xfed19fff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557790] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557792] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557793] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557796] system 00:01: [mem 0xfee00000-0xfee0ffff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557798] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557836] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557838] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557839] pnp 00:02: [io  0x0290-0x029f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557840] pnp 00:02: [io  0x0000-0xffffffffffffffff disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557861] system 00:02: [io  0x0290-0x029f] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557863] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557870] pnp 00:03: [dma 4]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557871] pnp 00:03: [io  0x0000-0x000f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557873] pnp 00:03: [io  0x0081-0x0083]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557874] pnp 00:03: [io  0x0087]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557874] pnp 00:03: [io  0x0089-0x008b]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557875] pnp 00:03: [io  0x008f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557876] pnp 00:03: [io  0x00c0-0x00df]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557889] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557894] pnp 00:04: [io  0x0070-0x0071]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557901] pnp 00:04: [irq 8]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557912] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557916] pnp 00:05: [io  0x0061]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557926] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557935] pnp 00:06: [io  0x0010-0x001f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557936] pnp 00:06: [io  0x0022-0x003f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557937] pnp 00:06: [io  0x0044-0x005f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557938] pnp 00:06: [io  0x0063]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557939] pnp 00:06: [io  0x0065]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557940] pnp 00:06: [io  0x0067-0x006f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557941] pnp 00:06: [io  0x0072-0x007f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557942] pnp 00:06: [io  0x0080]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557943] pnp 00:06: [io  0x0084-0x0086]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557944] pnp 00:06: [io  0x0088]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557945] pnp 00:06: [io  0x008c-0x008e]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557946] pnp 00:06: [io  0x0090-0x009f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557947] pnp 00:06: [io  0x00a2-0x00bf]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557948] pnp 00:06: [io  0x00e0-0x00ef]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557951] pnp 00:06: [io  0x04d0-0x04d1]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557977] system 00:06: [io  0x04d0-0x04d1] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557979] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557984] pnp 00:07: [io  0x00f0-0x00ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557987] pnp 00:07: [irq 13]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.557998] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558150] pnp 00:08: [io  0x03f8-0x03ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558154] pnp 00:08: [irq 4]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558155] pnp 00:08: [dma 0 disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558184] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
Oct 27 23:24:00 michael-cooler-UB modem-manager[928]: <info>  ModemManager (version 0.5) starting...
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558260] pnp 00:09: [io  0x0400-0x0453]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558261] pnp 00:09: [io  0x0458-0x047f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558263] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558264] pnp 00:09: [io  0x0500-0x057f]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558265] pnp 00:09: [mem 0xfed1c000-0xfed1ffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558266] pnp 00:09: [mem 0xfec00000-0xfecfffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558267] pnp 00:09: [mem 0xfed08000-0xfed08fff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558268] pnp 00:09: [mem 0xff000000-0xffffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558291] system 00:09: [io  0x0400-0x0453] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558292] system 00:09: [io  0x0458-0x047f] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558294] system 00:09: [io  0x0500-0x057f] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558295] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558297] system 00:09: [mem 0xfec00000-0xfecfffff] could not be reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558298] system 00:09: [mem 0xfed08000-0xfed08fff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558300] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558302] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558322] pnp 00:0a: [io  0x0454-0x0457]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558343] system 00:0a: [io  0x0454-0x0457] has been reserved
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558345] system 00:0a: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558417] pnp 00:0b: [mem 0xfed00000-0xfed003ff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558436] pnp 00:0b: Plug and Play ACPI device, IDs PNP0103 (active)
Oct 27 23:24:00 michael-cooler-UB modem-manager[928]: <info>  Loaded plugin Option High-Speed
Oct 27 23:24:00 michael-cooler-UB modem-manager[928]: <info>  Loaded plugin X22X
Oct 27 23:24:00 michael-cooler-UB modem-manager[928]: <info>  Loaded plugin Huawei
Oct 27 23:24:00 michael-cooler-UB modem-manager[928]: <info>  Loaded plugin AnyData
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558516] pnp: PnP ACPI: found 12 devices
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.558517] ACPI: ACPI bus type pnp unregistered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563702] PCI: max bus depth: 2 pci_try_num: 3
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563763] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563765] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563767] pci 0000:00:01.0:   bridge window [mem 0xfa000000-0xfb0fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563770] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xf1ffffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563772] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563773] pci 0000:00:1c.0:   bridge window [io  disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563777] pci 0000:00:1c.0:   bridge window [mem disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563780] pci 0000:00:1c.0:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563785] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563787] pci 0000:00:1c.2:   bridge window [io  0xd000-0xdfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563791] pci 0000:00:1c.2:   bridge window [mem 0xfb400000-0xfb4fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563794] pci 0000:00:1c.2:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563799] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563800] pci 0000:00:1c.3:   bridge window [io  disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563804] pci 0000:00:1c.3:   bridge window [mem disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563807] pci 0000:00:1c.3:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563812] pci 0000:05:00.0: PCI bridge to [bus 06-06]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563815] pci 0000:05:00.0:   bridge window [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563822] pci 0000:05:00.0:   bridge window [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563827] pci 0000:05:00.0:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563836] pci 0000:00:1c.4: PCI bridge to [bus 05-06]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563838] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563842] pci 0000:00:1c.4:   bridge window [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563845] pci 0000:00:1c.4:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563850] pci 0000:00:1c.5: PCI bridge to [bus 07-07]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563852] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563856] pci 0000:00:1c.5:   bridge window [mem disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563859] pci 0000:00:1c.5:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563865] pci 0000:00:1c.6: PCI bridge to [bus 08-08]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563867] pci 0000:00:1c.6:   bridge window [io  0xa000-0xafff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563871] pci 0000:00:1c.6:   bridge window [mem 0xfb200000-0xfb2fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563874] pci 0000:00:1c.6:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563879] pci 0000:00:1c.7: PCI bridge to [bus 09-09]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563880] pci 0000:00:1c.7:   bridge window [io  disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563884] pci 0000:00:1c.7:   bridge window [mem 0xfb100000-0xfb1fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563887] pci 0000:00:1c.7:   bridge window [mem pref disabled]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563899] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563901] pci 0000:00:01.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563907] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563910] pci 0000:00:1c.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563918] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563921] pci 0000:00:1c.2: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563928] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563931] pci 0000:00:1c.3: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563936] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563939] pci 0000:00:1c.4: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563944] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563949] pci 0000:05:00.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563954] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563957] pci 0000:00:1c.5: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563962] pci 0000:00:1c.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563965] pci 0000:00:1c.6: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563970] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563973] pci 0000:00:1c.7: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563975] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563977] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563978] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563979] pci_bus 0000:00: resource 7 [mem 0x000c8000-0x000dffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563981] pci_bus 0000:00: resource 8 [mem 0xe4000000-0xffffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563982] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563983] pci_bus 0000:01: resource 1 [mem 0xfa000000-0xfb0fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563984] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xf1ffffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563986] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563987] pci_bus 0000:03: resource 1 [mem 0xfb400000-0xfb4fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563988] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563990] pci_bus 0000:05: resource 1 [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563991] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563992] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563993] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563994] pci_bus 0000:05: resource 7 [mem 0x000c8000-0x000dffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563996] pci_bus 0000:05: resource 8 [mem 0xe4000000-0xffffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563997] pci_bus 0000:06: resource 0 [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563998] pci_bus 0000:06: resource 1 [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.563999] pci_bus 0000:06: resource 4 [io  0xc000-0xcfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564001] pci_bus 0000:06: resource 5 [mem 0xfb300000-0xfb3fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564002] pci_bus 0000:06: resource 8 [io  0x0000-0x0cf7]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564003] pci_bus 0000:06: resource 9 [io  0x0d00-0xffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564004] pci_bus 0000:06: resource 10 [mem 0x000a0000-0x000bffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564006] pci_bus 0000:06: resource 11 [mem 0x000c8000-0x000dffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564007] pci_bus 0000:06: resource 12 [mem 0xe4000000-0xffffffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564008] pci_bus 0000:07: resource 0 [io  0xb000-0xbfff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564009] pci_bus 0000:07: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564011] pci_bus 0000:08: resource 0 [io  0xa000-0xafff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564012] pci_bus 0000:08: resource 1 [mem 0xfb200000-0xfb2fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564013] pci_bus 0000:09: resource 1 [mem 0xfb100000-0xfb1fffff]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564031] NET: Registered protocol family 2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564184] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.564830] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.565740] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.565842] TCP: Hash tables configured (established 524288 bind 65536)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.565844] TCP reno registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.565853] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.565877] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.565943] NET: Registered protocol family 1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822182] pci 0000:01:00.0: Boot video device
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822242] PCI: CLS 64 bytes, default 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822243] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822245] Placing 64MB software IO TLB between ffff8800db422000 - ffff8800df422000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822246] software IO TLB at phys 0xdb422000 - 0xdf422000
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822504] audit: initializing netlink socket (disabled)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.822510] type=2000 audit(1319757823.668:1): initialized
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.842491] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856118] VFS: Disk quotas dquot_6.5.2
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856148] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856458] fuse init (API version 7.16)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856503] msgmni has been set to 15935
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856689] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856703] io scheduler noop registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856704] io scheduler deadline registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856724] io scheduler cfq registered (default)
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856787] pcieport 0000:00:01.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856805] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856841] pcieport 0000:00:1c.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856876] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856929] pcieport 0000:00:1c.2: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB modem-manager[928]: <info>  Loaded plugin Option
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.856965] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857019] pcieport 0000:00:1c.3: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857055] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857108] pcieport 0000:00:1c.5: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857144] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857197] pcieport 0000:00:1c.6: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857232] pcieport 0000:00:1c.6: irq 45 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857286] pcieport 0000:00:1c.7: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857322] pcieport 0000:00:1c.7: irq 46 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857381] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857383] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857384] pci 0000:01:00.1: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857386] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857399] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857402] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857415] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857416] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857419] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857431] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857434] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857447] pcieport 0000:00:1c.5: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857449] pci 0000:07:00.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857452] pcie_pme 0000:00:1c.5:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857464] pcieport 0000:00:1c.6: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857465] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857466] pci 0000:08:00.1: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857469] pcie_pme 0000:00:1c.6:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857482] pcieport 0000:00:1c.7: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857483] pci 0000:09:00.0: Signaling PME through PCIe PME interrupt
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857486] pcie_pme 0000:00:1c.7:pcie01: service driver pcie_pme loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857495] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857509] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857531] intel_idle: MWAIT substates: 0x1120
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857532] intel_idle: v0.4 model 0x2A
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857532] intel_idle: lapic_timer_reliable_states 0xffffffff
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857591] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857595] ACPI: Power Button [PWRB]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857616] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857618] ACPI: Power Button [PWRF]
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.857632] ACPI: acpi_idle yielding to intel_idle
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.858883] ERST: Table is not found!
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.858917] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.879289] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 27 23:24:00 michael-cooler-UB kernel: [    0.885434] Freeing initrd memory: 13424k freed
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.062389] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.062551] Linux agpgart interface v0.103
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063133] brd: module loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063372] loop: module loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063464] pata_acpi 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063481] pata_acpi 0000:08:00.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063492] pata_acpi 0000:08:00.0: PCI INT A disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063500] pata_acpi 0000:08:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063512] pata_acpi 0000:08:00.1: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063519] pata_acpi 0000:08:00.1: PCI INT B disabled
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063655] Fixed MDIO Bus: probed
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063666] PPP generic driver version 2.4.2
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063684] tun: Universal TUN/TAP device driver, 1.6
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063685] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063721] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063734] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063748] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063750] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063768] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.063788] ehci_hcd 0000:00:1a.0: debug port 2
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.067678] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.067692] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xfb507000
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.081910] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.081968] hub 1-0:1.0: USB hub found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.081971] hub 1-0:1.0: 2 ports detected
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.082007] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.082015] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.082017] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.082037] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.082054] ehci_hcd 0000:00:1d.0: debug port 2
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.085942] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.085945] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfb506000
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.097895] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.097944] hub 2-0:1.0: USB hub found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.097946] hub 2-0:1.0: 2 ports detected
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.097977] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.097983] uhci_hcd: USB Universal Host Controller Interface driver
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.098012] i8042: PNP: No PS/2 controller found. Probing ports directly.
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100527] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100531] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100586] mousedev: PS/2 mouse device common for all mice
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100646] rtc_cmos 00:04: RTC can wake from S4
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100719] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100742] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100796] device-mapper: uevent: version 1.0.3
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100832] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100887] cpuidle: using governor ladder
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100964] cpuidle: using governor menu
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.100965] EFI Variables Facility v0.08 2004-May-17
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.101078] TCP cubic registered
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.101142] NET: Registered protocol family 10
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.101364] NET: Registered protocol family 17
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.101371] Registering the dns_resolver key type
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.101420] PM: Hibernation image not present or could not be loaded.
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.101426] registered taskstats version 1
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.112477]   Magic number: 15:318:404
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.112579] rtc_cmos 00:04: setting system clock to 2011-10-27 23:23:44 UTC (1319757824)
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.113199] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.113200] EDD information not available.
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.114209] Freeing unused kernel memory: 984k freed
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.114280] Write protecting the kernel read-only data: 10240k
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.114543] Freeing unused kernel memory: 20k freed
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.116906] Freeing unused kernel memory: 1400k freed
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.137382] xhci_hcd 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.137403] xhci_hcd 0000:09:00.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.137407] xhci_hcd 0000:09:00.0: xHCI Host Controller
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.137440] xhci_hcd 0000:09:00.0: new USB bus registered, assigned bus number 3
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.140444] ahci 0000:00:1f.2: version 3.0
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.140461] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.140506] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.140569] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x6 impl SATA mode
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.140571] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.140574] ahci 0000:00:1f.2: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.141502] pata_marvell 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.141527] pata_marvell 0000:08:00.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.142292] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.142308] r8169 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.142360] r8169 0000:07:00.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.142462] r8169 0000:07:00.0: irq 48 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.142673] r8169 0000:07:00.0: eth0: RTL8168e/8111e at 0xffffc90000c7a000, f4:6d:04:65:72:83, XID 0c200000 IRQ 48
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.144030] scsi0 : pata_marvell
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.144669] scsi1 : pata_marvell
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.144691] ata1: PATA max UDMA/100 cmd 0xa090 ctl 0xa080 bmdma 0xa050 irq 18
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.144692] ata2: PATA max UDMA/133 cmd 0xa070 ctl 0xa060 bmdma 0xa058 irq 18
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.144709] pata_marvell 0000:08:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.144731] pata_marvell 0000:08:00.1: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.146700] scsi2 : pata_marvell
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147090] xhci_hcd 0000:09:00.0: irq 19, io mem 0xfb100000
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147151] xhci_hcd 0000:09:00.0: irq 49 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147154] xhci_hcd 0000:09:00.0: irq 50 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147157] xhci_hcd 0000:09:00.0: irq 51 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147160] xhci_hcd 0000:09:00.0: irq 52 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147162] xhci_hcd 0000:09:00.0: irq 53 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147283] xHCI xhci_add_endpoint called for root hub
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147284] xHCI xhci_check_bandwidth called for root hub
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147298] hub 3-0:1.0: USB hub found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147305] hub 3-0:1.0: 2 ports detected
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147344] xhci_hcd 0000:09:00.0: xHCI Host Controller
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147362] xhci_hcd 0000:09:00.0: new USB bus registered, assigned bus number 4
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147406] xHCI xhci_add_endpoint called for root hub
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147406] xHCI xhci_check_bandwidth called for root hub
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147418] hub 4-0:1.0: USB hub found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147423] hub 4-0:1.0: 2 ports detected
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147471] scsi4 : pata_marvell
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147493] ata3: PATA max UDMA/100 cmd 0xa040 ctl 0xa030 bmdma 0xa000 irq 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147494] ata4: PATA max UDMA/133 cmd 0xa020 ctl 0xa010 bmdma 0xa008 irq 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.147783] scsi3 : ahci
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.148499] scsi5 : ahci
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.149098] scsi6 : ahci
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.149830] scsi7 : ahci
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.149989] scsi8 : ahci
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150048] scsi9 : ahci
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150120] ata5: DUMMY
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150122] ata6: SATA max UDMA/133 abar m2048@0xfb505000 port 0xfb505180 irq 47
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150124] ata7: SATA max UDMA/133 abar m2048@0xfb505000 port 0xfb505200 irq 47
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150125] ata8: DUMMY
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150126] ata9: DUMMY
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.150126] ata10: DUMMY
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.393660] usb 1-1: new high speed USB device number 2 using ehci_hcd
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.469566] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.469585] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.471290] ata6.00: ATA-8: WDC WD1002FAEX-00Z3A0, 05.01D05, max UDMA/133
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.471292] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.474012] ata6.00: configured for UDMA/133
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.484408] ata7.00: ATAPI: PIONEER DVD-RW  DVR-219L, 1.01, max UDMA/100
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.497209] ata7.00: configured for UDMA/100
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.526232] hub 1-1:1.0: USB hub found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.526348] hub 1-1:1.0: 6 ports detected
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.636953] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 05.0 PQ: 0 ANSI: 5
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.637027] sd 5:0:0:0: Attached scsi generic sg0 type 0
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.637047] sd 5:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.637096] sd 5:0:0:0: [sda] Write Protect is off
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.637097] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.637114] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.637402] usb 2-1: new high speed USB device number 2 using ehci_hcd
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.641906] scsi 6:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-219L 1.01 PQ: 0 ANSI: 5
Oct 27 23:24:00 michael-cooler-UB avahi-daemon[931]: Found user 'avahi' (UID 106) and group 'avahi' (GID 113).
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.656917] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.656922] cdrom: Uniform CD-ROM driver Revision: 3.20
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.657018] sr 6:0:0:0: Attached scsi CD-ROM sr0
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.657044] sr 6:0:0:0: Attached scsi generic sg1 type 5
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.684570]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.684896] sd 5:0:0:0: [sda] Attached SCSI disk
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.685651] firewire_ohci 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.749368] firewire_ohci: Added fw-ohci device 0000:06:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.773713] hub 2-1:1.0: USB hub found
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.773822] hub 2-1:1.0: 8 ports detected
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.821216] Refined TSC clocksource calibration: 3310.798 MHz.
Oct 27 23:24:00 michael-cooler-UB kernel: [    1.821219] Switching to clocksource tsc
Oct 27 23:24:00 michael-cooler-UB kernel: [    2.045239] usb 2-1.5: new low speed USB device number 3 using ehci_hcd
Oct 27 23:24:00 michael-cooler-UB kernel: [    2.151289] input: SIGMACH1P USB Keykoard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input2
Oct 27 23:24:00 michael-cooler-UB kernel: [    2.151330] generic-usb 0003:1C4F:000E.0001: input,hidraw0: USB HID v1.10 Keyboard [SIGMACH1P USB Keykoard] on usb-0000:00:1d.0-1.5/input0
Oct 27 23:24:00 michael-cooler-UB kernel: [    2.182727] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
Oct 27 23:24:00 michael-cooler-UB kernel: [    2.217123] usb 2-1.6: new low speed USB device number 4 using ehci_hcd
Oct 27 23:24:00 michael-cooler-UB kernel: [    2.248948] firewire_core: created device fw0: GUID 001e8c00004d29f9, S400
Oct 27 23:24:00 michael-cooler-UB kernel: [    5.439755] usb 2-1.6: USB disconnect, device number 4
Oct 27 23:24:00 michael-cooler-UB kernel: [    6.916623] usb 2-1.6: new low speed USB device number 5 using ehci_hcd
Oct 27 23:24:00 michael-cooler-UB kernel: [   10.043534] usb 2-1.6: USB disconnect, device number 5
Oct 27 23:24:00 michael-cooler-UB kernel: [   11.520261] usb 2-1.6: new low speed USB device number 6 using ehci_hcd
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.143662] generic-usb 0003:1C4F:000E.0002: usb_submit_urb(ctrl) failed
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.143770] generic-usb 0003:1C4F:000E.0002: timeout initializing reports
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.143819] input: SIGMACH1P USB Keykoard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/input/input3
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.143859] generic-usb 0003:1C4F:000E.0002: input,hidraw1: USB HID v1.10 Device [SIGMACH1P USB Keykoard] on usb-0000:00:1d.0-1.5/input1
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.145813] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input4
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.145853] generic-usb 0003:093A:2510.0003: input,hidraw2: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.6/input0
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.145861] usbcore: registered new interface driver usbhid
Oct 27 23:24:00 michael-cooler-UB kernel: [   12.145862] usbhid: USB HID core driver
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.742799] mei: module is from the staging directory, the quality is unknown, you have been warned.
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.742966] mei 0000:00:16.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.742971] mei 0000:00:16.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.745386] cfg80211: Calling CRDA to update world regulatory domain
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.748317] lp: driver loaded but no devices found
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.751001] rtl8192se 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.751008] rtl8192se 0000:03:00.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.752306] wmi: Mapper loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.764112] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.764113]            Loading firmware rtlwifi/rtl8192sefw.bin
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.779626] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.779671] HDA Intel 0000:00:1b.0: irq 54 for MSI/MSI-X
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.779692] HDA Intel 0000:00:1b.0: setting latency timer to 64
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.781723] AV200 0000:06:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791474] cfg80211: World regulatory domain updated:
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791475] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791477] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791478] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791479] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791481] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791482] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.791927] asus_wmi: ASUS WMI generic driver loaded
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.792272] asus_wmi: Initialization: 0x0
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.792285] asus_wmi: BIOS WMI version: 0.9
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.792308] asus_wmi: SFUN value: 0x0
Oct 27 23:24:00 michael-cooler-UB kernel: [   15.792445] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input5
Oct 27 23:24:00 michael-cooler-UB avahi-daemon[931]: Successfully dropped root privileges.
```

---

### Post by shchur on 2011-10-30
Hi 

I have exactly the same problem with my Acer laptop...did you figure it out eventually? I'm really getting frustrated.....

best regards

Shchur

---

### Post by shanta on 2011-10-31
I to have this problem.

---

### Post by shanta on 2011-10-31
> **shanta said:**
> I to have this problem.

tried this and had to uninstall at the command line Nvida updated the drivers but not the kernel.

I know have new choices in the driver list and have made the upgrade but have not tested this. yet.

Just tested it and I now see my exteral monitor in the nvidia control list.

Not working for display as I did not have the monitor on when I booted.

---

### Post by kc6ymp on 2011-10-31
Bro this is an easy fix ? when it boot's to black screen hit ctrl + alt + f1 and look in the nvidia directory their is a file called reset.sh run that script and reboot ? your problem will be solved ?

---

### Post by Panna-cakkhu on 2011-11-02
@Shchur: Unfortunately no, i still didn't have find any solution to this problem. At least i'm glad not to be alone on this and hopefully we'll find the solution with this thread. I'll definitely let you know if i resolve this issue.

@kc6ymp: I don't have access to any text terminal. Ctrl + Alt + F1/F2/... doesn't work. What Nvidia directory are you talkinga about, could you please give me its path? I assume you are referencing to the situation when Nvidia drivers are installed from Nvidia website and not from additional proprietary drivers proposed by Ubuntu then?

---

### Post by shchur on 2011-11-05
Yeah...the same situation here...I've just installed "fresh" x86_64 11.04. It's working now. But it doesn't recognize Nvidia drivers. According to "xorg.conf log" it automatically uses "nouveau" drivers. Still....at least lets me run ubuntu in normal way....but no chance for Unity....and generally it is not stable solution......ehhhhhh....If I will find how to fix it, I will let you know....

---

### Post by bcschmerker on 2011-12-16
I suspect that [nVIDIA Corporation](http://www.nvidia.com/) has yet to catch up with the [LinUX Kernel Project](http://www.kernel.org/) on GeForce® drivers for Kernels 3.0-up; I ran into the same situation with the Advance Micro Devices® Catalyst drivers and control-center application on 10.04.4-LTS with Kernel 3.0.0.14 (Catalyst was fully functional on Kernel 2.6.35) with my hybrid Everex'® Gigabyte® MA78GM-S2HP's planar ATi® Radeon HD 3200.

---

### Post by papu40000 on 2012-01-22
Hi!

I see that nvidia binary driver need some "buildings" on kernel module, bla bla. My lazy way I use is recycle the script to install a nvidia driver, uninstall it, and put a version choiced specifically for my video card.

This worked for me -> nvidia binary driver in ubuntu 64bit 10.10.

First, you need a console and Internet (or the packages I use).
Ctrl+Alt+F1
doesn't work?
GRUB, rescue mode, if doesn't appear, press shift to enter it. and after that, "normal mode"
should have Ctrl+Alt+F1 console.

now:
```
sudo apt-get install nvidia-current-updates
```

reboot computer

Ctrl+Alt+F1 and:
```
sudo apt-get remove nvidia-current
```
next, go to the nvidia download:
```

chmod +x NVIDIA*
sudo ./NVIDIA*

```
reboot!

regards,
Pedro

---

