---
title: "WiFi often disconnects"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by Shishimaru on 2013-07-04
Hello,
I use Ubuntu 13.04 Raring Ringtail on my Acer TravelMate 5730. Since I left hometown and moved I use a wifi hotspot with my uncle and I found out that I have strange problems. Wifi suddenly disconnects for no reasons and SSID disappears from Network Manager's list. Sometimes disabling wifi from NM and re-enabling it would solve the problem, sometimes it would not. I have the same problem with my Nexus 4 with Android 4.2.2 Jelly Bean but NOT with my old LG Optimus One with unofficial CyanogenMod 9 (Android 4.0.x ICS). With the latter, it happens that connection doesn't work (at the same time, on my laptop, wifi has totally disconnected) but wifi is still connected so I can go to router's page and reset it. I tried almost everything: changing kernel (3.8, 3.9 and 3.10), changing security (WEP and WPA), disabling wifi 'n', changing wifi channel, reducing beaconing interval and disabling firewall in the router. Nothing worked.  It's getting very frustrating and don't know what to do. Do you people have idea of what's happening? Here's my dmesg, by the way:

```
[   11.449638] input: Acer BMA150 accelerometer as /devices/virtual/input/input5
[   11.683920] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input6
[   11.706696] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input7
[   12.000225] Console: switching to colour frame buffer device 160x50
[   12.003365] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.003367] i915 0000:00:02.0: registered panic notifier
[   12.099589] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.104700] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa1
[   12.109532] cfg80211: World regulatory domain updated:
[   12.109538] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.109541] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.109543] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.109546] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.109548] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.109551] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.118194] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   12.125055] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   12.142774] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   12.142785]  excluding 0xc0000-0xd3fff 0xe4000-0xfffff
[   12.142816] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   12.142827]  excluding 0xa0000000-0xa0ffffff
[   12.142849] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   12.142860]  excluding 0x60000000-0x60ffffff
[   12.176444] acpi device:03: registered as cooling_device2
[   12.176543] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.176610] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   12.180160] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.183564] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   12.183875] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   12.220340] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   12.220346]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.220348]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   12.220350]    mono: mono_out=0x0
[   12.220351]    inputs:
[   12.220354]      Mic=0x18
[   12.220356]      Internal Mic=0x12
[   12.220358]      Line=0x1a
[   12.220360] realtek: No valid SSID, checking pincfg 0x4016852d for NID 0x1d
[   12.220362] realtek: Enabling init ASM_ID=0x852d CODEC_ID=10ec0268
[   12.272654] autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   12.272660]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.272662]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.272664]    mono: mono_out=0x0
[   12.272666]    inputs:
[   12.294269] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.294536] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.294873] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.295097] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   12.311147] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   12.314332] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   12.391841] init: Failed to spawn atd main process: unable to execute: No such file or directory
[   12.432650] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.662566] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   12.681026] zram: Created 2 device(s) ...
[   12.700044] usb 8-2: new full-speed USB device number 2 using uhci_hcd
[   12.744946] Adding 752520k swap on /dev/zram0.  Priority:5 extents:1 across:752520k SSFS
[   12.771585] Adding 752520k swap on /dev/zram1.  Priority:5 extents:1 across:752520k SSFS
[   12.872068] usb 8-2: New USB device found, idVendor=0a5c, idProduct=2101
[   12.872075] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   12.872078] usb 8-2: Product: Acer Module
[   12.872081] usb 8-2: Manufacturer: Broadcom Corp
[   12.926499] usbcore: registered new interface driver btusb
[   18.810108] wlan0: authenticate with 38:22:9d:03:a7:d2
[   18.811746] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[   18.819125] wlan0: authenticated
[   18.819287] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   18.820076] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[   18.841530] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[   18.844400] wlan0: associated
[   18.844435] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.148194] init: plymouth-stop pre-start process (2429) terminated with status 1
[   89.924139] usb 8-2: USB disconnect, device number 2
[  909.820362] cfg80211: Calling CRDA to update world regulatory domain
[  909.835534] cfg80211: World regulatory domain updated:
[  909.835546] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  909.835554] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  909.835560] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  909.835566] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  909.835573] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  909.835579] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  921.177717] wlan0: authenticate with 38:22:9d:03:a7:d2
[  921.179416] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[  921.181785] wlan0: authenticated
[  921.182106] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  921.184153] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[  921.215210] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[  921.217492] wlan0: associated
[  921.217561] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  924.192364] cfg80211: Calling CRDA to update world regulatory domain
[  924.201939] cfg80211: World regulatory domain updated:
[  924.201944] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  924.201947] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  924.201950] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  924.201953] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  924.201955] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  924.201958] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  927.357509] wlan0: authenticate with 38:22:9d:03:a7:d2
[  927.359459] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[  927.361872] wlan0: authenticated
[  927.362257] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  927.364084] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[  927.395258] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[  927.397765] wlan0: associated
[ 1365.400427] cfg80211: Calling CRDA to update world regulatory domain
[ 1365.412885] cfg80211: World regulatory domain updated:
[ 1365.412891] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1365.412894] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1365.412897] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1365.412899] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1365.412902] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1365.412904] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1387.613748] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 1387.615578] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 1387.617966] wlan0: authenticated
[ 1387.618848] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1387.620947] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 1387.652039] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 1387.654680] wlan0: associated
[ 1706.528833] tg3 0000:02:00.0: System wakeup enabled by ACPI
[ 1706.750737] wlan0: deauthenticating from 38:22:9d:03:a7:d2 by local choice (reason=3)
[ 1706.758088] cfg80211: Calling CRDA to update world regulatory domain
[ 1706.763931] cfg80211: World regulatory domain updated:
[ 1706.763938] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1706.763941] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1706.763944] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1706.763946] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1706.763949] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1706.763951] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1706.743715] PM: Syncing filesystems ... done.
[ 1706.810694] Freezing user space processes ... (elapsed 0.10 seconds) done.
[ 1706.920273] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 1706.936283] Suspending console(s) (use no_console_suspend to debug)
[ 1706.936821] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1706.938096] sd 0:0:0:0: [sda] Stopping disk
[ 1707.488130] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D3hot
[ 1707.488182] PM: suspend of devices complete after 551.492 msecs
[ 1707.488472] PM: late suspend of devices complete after 0.287 msecs
[ 1707.504358] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
[ 1707.520065] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
[ 1707.520107] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
[ 1707.520148] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
[ 1707.520279] ehci-pci 0000:00:1a.7: System wakeup enabled by ACPI
[ 1707.536060] uhci_hcd 0000:00:1a.2: System wakeup enabled by ACPI
[ 1707.536101] uhci_hcd 0000:00:1a.1: System wakeup enabled by ACPI
[ 1707.536143] uhci_hcd 0000:00:1a.0: System wakeup enabled by ACPI
[ 1707.536195] PM: noirq suspend of devices complete after 47.720 msecs
[ 1707.536425] ACPI: Preparing to enter system sleep state S3
[ 1707.563891] PM: Saving platform NVS memory
[ 1707.564253] Disabling non-boot CPUs ...
[ 1707.668036] smpboot: CPU 1 is now offline
[ 1707.668409] ACPI: Low-level resume complete
[ 1707.668409] PM: Restoring platform NVS memory
[ 1707.668409] Enabling non-boot CPUs ...
[ 1707.668409] smpboot: Booting Node 0 Processor 1 APIC 0x1
[ 1707.680100] CPU1 is up
[ 1707.682600] ACPI: Waking up from system sleep state S3
[ 1707.780215] uhci_hcd 0000:00:1a.0: System wakeup disabled by ACPI
[ 1707.780286] uhci_hcd 0000:00:1a.1: System wakeup disabled by ACPI
[ 1707.780360] uhci_hcd 0000:00:1a.2: System wakeup disabled by ACPI
[ 1707.796084] ehci-pci 0000:00:1a.7: System wakeup disabled by ACPI
[ 1707.796620] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[ 1707.812504] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[ 1707.812576] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[ 1707.812645] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
[ 1707.828078] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[ 1707.876242] yenta_cardbus 0000:0d:06.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[ 1707.892853] PM: noirq resume of devices complete after 127.224 msecs
[ 1707.893179] PM: early resume of devices complete after 0.282 msecs
[ 1707.893227] i915 0000:00:02.0: setting latency timer to 64
[ 1707.893678] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1707.893710] usb usb3: root hub lost power or was reset
[ 1707.893856] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 1707.893884] usb usb4: root hub lost power or was reset
[ 1707.894085] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 1707.894113] usb usb5: root hub lost power or was reset
[ 1707.894258] ehci-pci 0000:00:1a.7: setting latency timer to 64
[ 1707.894522] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[ 1707.894751] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1707.894780] usb usb6: root hub lost power or was reset
[ 1707.894922] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 1707.894950] usb usb7: root hub lost power or was reset
[ 1707.895091] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 1707.895120] usb usb8: root hub lost power or was reset
[ 1707.895262] ehci-pci 0000:00:1d.7: setting latency timer to 64
[ 1707.895293] pci 0000:00:1e.0: setting latency timer to 64
[ 1707.895313] ahci 0000:00:1f.2: setting latency timer to 64
[ 1707.895359] tg3 0000:02:00.0: System wakeup disabled by ACPI
[ 1707.895408] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 1708.216179] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1708.224186] ata5: SATA link down (SStatus 0 SControl 300)
[ 1708.228192] usb 3-1: reset full-speed USB device number 2 using uhci_hcd
[ 1708.232074] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1708.240191] ata6: SATA link down (SStatus 0 SControl 300)
[ 1708.286676] ata1.00: configured for UDMA/133
[ 1708.299111] ata2.00: configured for UDMA/133
[ 1708.300124] sd 0:0:0:0: [sda] Starting disk
[ 1708.476093] usb 1-3: reset high-speed USB device number 3 using ehci-pci
[ 1709.150457] PM: resume of devices complete after 1257.268 msecs
[ 1709.336191] Restarting tasks ... done.
[ 1709.367032] video LNXVIDEO:00: Restoring backlight state
[ 1710.096879] tg3 0000:02:00.0: irq 47 for MSI/MSI-X
[ 1710.880386] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1710.884913] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1710.887928] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 1710.972052] [drm] HPD interrupt storm detected on connector DP-2: switching from hotplug detection to polling
[ 1711.016702] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1717.393522] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 1717.395452] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 1717.402855] wlan0: authenticated
[ 1717.403206] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1717.404778] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 1717.426319] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=2)
[ 1717.429799] wlan0: associated
[ 1717.429873] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2599.784789] tg3 0000:02:00.0: System wakeup enabled by ACPI
[ 2599.970594] PM: Syncing filesystems ... done.
[ 2600.003652] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 2600.020263] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 2600.036277] Suspending console(s) (use no_console_suspend to debug)
[ 2600.036743] wlan0: deauthenticating from 38:22:9d:03:a7:d2 by local choice (reason=3)
[ 2600.046507] cfg80211: Calling CRDA to update world regulatory domain
[ 2600.081326] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2600.082381] sd 0:0:0:0: [sda] Stopping disk
[ 2600.632125] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D3hot
[ 2600.632178] PM: suspend of devices complete after 595.499 msecs
[ 2600.632476] PM: late suspend of devices complete after 0.294 msecs
[ 2600.648358] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
[ 2600.664066] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
[ 2600.664109] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
[ 2600.664150] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
[ 2600.664281] ehci-pci 0000:00:1a.7: System wakeup enabled by ACPI
[ 2600.680061] uhci_hcd 0000:00:1a.2: System wakeup enabled by ACPI
[ 2600.680102] uhci_hcd 0000:00:1a.1: System wakeup enabled by ACPI
[ 2600.680143] uhci_hcd 0000:00:1a.0: System wakeup enabled by ACPI
[ 2600.680196] PM: noirq suspend of devices complete after 47.717 msecs
[ 2600.680424] ACPI: Preparing to enter system sleep state S3
[ 2600.704451] PM: Saving platform NVS memory
[ 2600.704805] Disabling non-boot CPUs ...
[ 2600.808021] smpboot: CPU 1 is now offline
[ 2600.808344] ACPI: Low-level resume complete
[ 2600.808344] PM: Restoring platform NVS memory
[ 2600.808344] Enabling non-boot CPUs ...
[ 2600.808344] smpboot: Booting Node 0 Processor 1 APIC 0x1
[ 2600.820163] CPU1 is up
[ 2600.824253] ACPI: Waking up from system sleep state S3
[ 2600.928209] uhci_hcd 0000:00:1a.0: System wakeup disabled by ACPI
[ 2600.928280] uhci_hcd 0000:00:1a.1: System wakeup disabled by ACPI
[ 2600.928354] uhci_hcd 0000:00:1a.2: System wakeup disabled by ACPI
[ 2600.944082] ehci-pci 0000:00:1a.7: System wakeup disabled by ACPI
[ 2600.944621] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
[ 2600.960431] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[ 2600.960500] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[ 2600.960568] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
[ 2600.976081] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[ 2601.024238] yenta_cardbus 0000:0d:06.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[ 2601.040847] PM: noirq resume of devices complete after 125.666 msecs
[ 2601.041168] PM: early resume of devices complete after 0.277 msecs
[ 2601.041220] i915 0000:00:02.0: setting latency timer to 64
[ 2601.041599] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 2601.041630] usb usb3: root hub lost power or was reset
[ 2601.041775] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 2601.041804] usb usb4: root hub lost power or was reset
[ 2601.041945] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 2601.041974] usb usb5: root hub lost power or was reset
[ 2601.042117] ehci-pci 0000:00:1a.7: setting latency timer to 64
[ 2601.042312] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[ 2601.042571] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2601.042611] usb usb6: root hub lost power or was reset
[ 2601.042757] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2601.042785] usb usb7: root hub lost power or was reset
[ 2601.042926] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2601.042955] usb usb8: root hub lost power or was reset
[ 2601.043100] ehci-pci 0000:00:1d.7: setting latency timer to 64
[ 2601.043130] pci 0000:00:1e.0: setting latency timer to 64
[ 2601.043151] ahci 0000:00:1f.2: setting latency timer to 64
[ 2601.043196] tg3 0000:02:00.0: System wakeup disabled by ACPI
[ 2601.166515] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 2601.364167] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2601.368163] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2601.372176] ata5: SATA link down (SStatus 0 SControl 300)
[ 2601.384184] ata6: SATA link down (SStatus 0 SControl 300)
[ 2601.388182] usb 1-3: reset high-speed USB device number 3 using ehci-pci
[ 2601.423024] ata1.00: configured for UDMA/133
[ 2601.440006] ata2.00: configured for UDMA/133
[ 2601.440165] sd 0:0:0:0: [sda] Starting disk
[ 2601.640194] usb 3-1: reset full-speed USB device number 2 using uhci_hcd
[ 2601.901404] ACPI Error: [CB04] Namespace lookup failure, AE_ALREADY_EXISTS (20130328/dsfield-211)
[ 2601.901416] ACPI Error: Method parse/execution failed [\_SB_.AMW0.WMCA] (Node ffff8800b6a37960), AE_ALREADY_EXISTS (20130328/psparse-537)
[ 2601.901428] ACPI: Marking method WMCA as Serialized because of AE_ALREADY_EXISTS error
[ 2601.974705] PM: resume of devices complete after 933.527 msecs
[ 2601.978989] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 2601.987000] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 2601.975690] Restarting tasks ... done.
[ 2602.020301] video LNXVIDEO:00: Restoring backlight state
[ 2602.055568] cfg80211: World regulatory domain updated:
[ 2602.055579] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2602.055584] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2602.055589] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2602.055594] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2602.055598] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2602.055603] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2602.119178] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2603.261029] tg3 0000:02:00.0: irq 47 for MSI/MSI-X
[ 2604.031899] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2604.033170] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 2604.036214] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 2604.156486] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2610.537669] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 2610.539337] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 2610.546728] wlan0: authenticated
[ 2610.547100] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2610.548135] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 2610.569678] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=2)
[ 2610.572771] wlan0: associated
[ 2610.572855] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2874.228665] cfg80211: Calling CRDA to update world regulatory domain
[ 2874.242406] cfg80211: World regulatory domain updated:
[ 2874.242417] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2874.242425] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2874.242432] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2874.242438] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2874.242444] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2874.242450] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2922.349184] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 2922.350370] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 2922.357755] wlan0: authenticated
[ 2922.357967] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2922.360204] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 2922.381760] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 2922.383628] wlan0: associated
[ 2922.383675] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3919.876334] cfg80211: Calling CRDA to update world regulatory domain
[ 3919.890771] cfg80211: World regulatory domain updated:
[ 3919.890786] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3919.890793] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3919.890801] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3919.890807] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3919.890813] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3919.890819] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3931.258137] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 3931.259578] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 3931.364059] wlan0: send auth to 38:22:9d:03:a7:d2 (try 2/3)
[ 3931.366374] wlan0: authenticated
[ 3931.366612] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3931.368070] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 3931.399085] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 3931.401124] wlan0: associated
[ 3931.401158] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6115.221284] cfg80211: Calling CRDA to update world regulatory domain
[ 6115.234082] cfg80211: World regulatory domain updated:
[ 6115.234087] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6115.234089] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6115.234092] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6115.234094] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6115.234096] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6115.234099] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6126.586105] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 6126.587691] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 6126.590124] wlan0: authenticated
[ 6126.590602] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 6126.592566] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 6126.623700] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 6126.626016] wlan0: associated
[ 6133.196395] cfg80211: Calling CRDA to update world regulatory domain
[ 6133.206728] cfg80211: World regulatory domain updated:
[ 6133.206749] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6133.206752] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6133.206755] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6133.206757] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6133.206760] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6133.206762] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6136.372481] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 6136.374040] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 6136.396166] wlan0: send auth to 38:22:9d:03:a7:d2 (try 2/3)
[ 6136.417797] wlan0: send auth to 38:22:9d:03:a7:d2 (try 3/3)
[ 6136.437974] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 6152.104905] show_signal_msg: 51 callbacks suppressed
[ 6152.104911] plugin-containe[4977]: segfault at 0 ip 00007f0d29bd3d72 sp 00007fffe83a9720 error 4 in plugin-container[7f0d29bc9000+10000]
[ 6156.009601] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 6156.010834] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 6156.013146] wlan0: authenticated
[ 6156.013354] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 6156.013359] wlan0: waiting for beacon from 38:22:9d:03:a7:d2
[ 6156.020036] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 6156.051092] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 6156.052938] wlan0: associated
[ 9816.900205] cfg80211: Calling CRDA to update world regulatory domain
[ 9816.907535] cfg80211: World regulatory domain updated:
[ 9816.907539] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 9816.907542] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9816.907545] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9816.907547] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 9816.907549] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9816.907551] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 9852.800830] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 9854.815147] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 9854.816523] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 9854.819562] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 9854.942367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9861.373331] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 9861.375442] wlan0: send auth to 38:22:9d:03:a7:d2 (try 1/3)
[ 9861.383021] wlan0: authenticated
[ 9861.383451] iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 9861.384140] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 9861.405677] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 9861.409165] wlan0: associated
[ 9861.409256] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


```

I think you can find more recent events in the last lines of course.

---

### Post by Shishimaru on 2013-07-05
Anyone with an idea in mind? :(

---

### Post by wildmanne39 on 2013-07-05
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Shishimaru on 2013-07-06
I've attached the gzip file to this message.

---

### Post by wildmanne39 on 2013-07-06
Hi, please do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Then add this one line to the bottom of the file:
```
options iwlwifi 11n_disable=1 swcrypto=1 bt_coex_active=N
```
Also it would be best to set your encryption in your router to just wpa2 if you have that option wep does not work well with linux.
Then reboot
Thanks

---

### Post by Shishimaru on 2013-07-06
I tried WEP only once, but I always use WPA. Is it OK? Actually I don't know why I see "WEP" in dmesg.

---

### Post by Shishimaru on 2013-07-06
I added that line in iwlwifi.conf, but wifi just disconnected again :(
Seems that this time disabling wifi with network manager and enabling it again won't work. Doesn't even connect on my Nexus 4.

```
[ 2933.298446] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 2933.500070] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 2933.704088] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 2933.908085] wlan0: authentication with 38:22:9d:03:a7:d2 timed out


```

Anyway, it's totally random: sometimes it just connects again, sometimes not (just like now, for example).

---

### Post by wildmanne39 on 2013-07-06
Please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
and set your wireless settings in network manger to match the screenshots.
The dmesg about the wep is strange and it looks like you have a bug in the kernel but I am not sure that is your issue.
Thanks

---

### Post by chili555 on 2013-07-06
> iwlwifi 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP useJust peeking over your shoulders. This means that HT and VHT, or high throughput and very high throughput; also known as N speeds, are disabled because the router is set to either WEP or TKIP. You have already said you are using WPA, so the router must be set to WPA-TKIP. The encryption algorithm AES is more secure so I suggest you reset the router to WPA2-AES. [http://www.dd-wrt.com/phpBB2/files/wpa2aes_174.jpg](http://www.dd-wrt.com/phpBB2/files/wpa2aes_174.jpg)

I am not sure that will help you connect any better, but it will eliminate a troubling message and one possibility.

---

### Post by Shishimaru on 2013-07-06
@Wild Man: my NM settings are already like that (just using OpenDNS and not Google's).
This is the file content:
```
~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1 swcrypto=1 bt_coex_active=N


```

@chili555: OK, I'm going to try AES algorithm and I'll let you know if it'll make a difference or not.

Thanks to both: some little help definitely helps me feeling less abandoned about this issue. Anyway, do you people think that advanced settings like DTIM or beaconing interval have something to do?

---

### Post by chili555 on 2013-07-06
> Anyway, do you people think that advanced settings like DTIM or beaconing interval have something to do? Perhaps. Let us both see:```
dmesg | grep 80211
```

---

### Post by Shishimaru on 2013-07-06
Here it is:

```
~$ dmesg | grep 80211
[   10.324458] cfg80211: Calling CRDA to update world regulatory domain
[   10.550703] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.091693] cfg80211: World regulatory domain updated:
[   11.091695] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.091698] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.091700] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.091701] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.091703] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.091704] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.980280] cfg80211: Calling CRDA to update world regulatory domain
[  117.991261] cfg80211: World regulatory domain updated:
[  117.991266] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  117.991268] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.991271] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  117.991273] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  117.991275] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  117.991278] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1063.884340] cfg80211: Calling CRDA to update world regulatory domain
[ 1063.892545] cfg80211: World regulatory domain updated:
[ 1063.892552] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1063.892555] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1063.892558] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1063.892560] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1063.892563] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1063.892565] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7799.864372] cfg80211: Calling CRDA to update world regulatory domain
[ 7799.879297] cfg80211: World regulatory domain updated:
[ 7799.879309] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7799.879317] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7799.879324] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7799.879330] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7799.879336] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7799.879342] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7857.904507] cfg80211: Calling CRDA to update world regulatory domain
[ 7857.910489] cfg80211: World regulatory domain updated:
[ 7857.910495] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7857.910498] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7857.910501] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7857.910504] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7857.910506] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7857.910509] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7968.892168] cfg80211: Calling CRDA to update world regulatory domain
[ 7968.899641] cfg80211: World regulatory domain updated:
[ 7968.899648] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7968.899651] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7968.899654] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7968.899656] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7968.899659] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7968.899661] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

---

### Post by wildmanne39 on 2013-07-06
After you change your router settings please reboot and show us:
```
sudo iwlist scan
cat /etc/resolv.conf
```
Thanks

---

### Post by Shishimaru on 2013-07-06
Changed to WPA2 with AES, saved and rebooted the router. Then, rebooted Ubuntu too. I gave those commands. Here's the first:
```
~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable


```

And then:

```
~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1


```

---

### Post by wildmanne39 on 2013-07-06
I am researching to see why we have this error:
> wlan0     Failed to read scan data : Resource temporarily unavailable

---

### Post by wildmanne39 on 2013-07-06
Let's try one more thing with the router before moving on.
Change 802.11abgn to just 802.11bg then reboot your computer.
Thanks

---

### Post by Shishimaru on 2013-07-06
Already tried that solution unfortunately. Anyway, I stayed (and still staying) with bg only.

---

### Post by wildmanne39 on 2013-07-06
Please boot into the kernel that comes with 13.04 originally should be 3.08, then check this file:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
and see if the parameters we added to that file are in this kernel as well if they are not please add them then reboot back into the original kernel 3.08 and see if it connects properly if not post the wireless script again from this kernel because I believe the 3.10 is causing issues with your connection.
Thanks

---

### Post by Shishimaru on 2013-07-07
I booted with Linux 3.8 (with parameters still in iwlwifi.conf) and it connected properly just as 3.10. I have this issue since Precise (with Linux 3.2). Probably it's going to disconnect sometime soon.

I'm starting to think about some problem in the router or in Linux kernel. This morning I only used my Nexus 4. Connected, then disconnected.

Ubuntu (Linux 3.2+): disconnects
Nexus 4 (Linux 3.4): disconnects
Optimus One (Linux 3.0): when disconnects on other systems, here doesn't disconnects but only can't use connection; so, I can go into my router page (192.168.1.1) and reboot. Unfortunately this Optimus One "died" weeks ago.

Anyway, still don't know why I can't scan data:
```
~$ sudo iwlist scan
[sudo] password for shishimaru: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable


```


I'm going to post wireless script as soon as disconnects, so we can see more errors maybe.


EDIT:
iwlist couldn't scan data because I was connected of course. If disconnected, this is the result:
```
~$ sudo iwlist scan
[sudo] password for shishimaru: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 38:22:9D:03:A7:D2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"stefano"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a2a50821
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000773746566616E6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000


```

---

### Post by Shishimaru on 2013-07-07
And here I am, wifi disconnected and I can't reconnect anymore until I will be able to restart router again.
I've attached wireless-info.txt to this post.

---

### Post by wildmanne39 on 2013-07-07
When you are connected is the internet speed good?
Thanks

---

### Post by Shishimaru on 2013-07-07
Yes, the speed is good (or, at least, it's normal as it should be).

---

### Post by wildmanne39 on 2013-07-07
Does your router have the option to change  802.11bg to  802.11ag? If so please try that setting, it is best to reboot the computer after changing that setting.
Thanks

---

### Post by Shishimaru on 2013-07-07
No :(
I can only set bgn or bg. I have bg at the moment.

---

### Post by wildmanne39 on 2013-07-07
I am compiling a new driver on my computer right now but I am pretty sure there is an easier way for you to do it using 13.04 so I am looking for the instructions while the driver is compiling.
Thanks

---

### Post by Shishimaru on 2013-07-07
Alright, I'm waiting, thank you very much for your efforts!

---

### Post by wildmanne39 on 2013-07-07
Please do:
```
sudo apt-get install --reinstall linux-headers-$(uname sudo-r) build-essential
```
then go to this link [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10-rc1/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.10-rc1/) and download backports-3.10-rc1-2.tar.xz then drag the file to your desktop and click extract here.
```
cd Desktop
sudo su
make defconfig-iwlwifi
make
make install
```
watch for errors, after it is done reboot computer.
Thanks

---

### Post by Shishimaru on 2013-07-07
I think I've got a couple of errors:

```
# make
Generating local configuration database from kernel ... done.
/--------------
| Your backport package isn't configured, please configure it
| using one of the following options:
| To configure manually:
|     make oldconfig
|     make menuconfig
|
| To get defaults for certain drivers:
|     make defconfig-drm
|     make defconfig-iwlwifi
|     make defconfig-media
|     make defconfig-nfc
|     make defconfig-regulator
|     make defconfig-rtlwifi
\--
make[2]: *** [.config] Errore 1
make[1]: *** [modules] Errore 2
make: *** [default] Errore 2


```

---

### Post by wildmanne39 on 2013-07-07
Do ```
make defconfig-iwlwifi
``` then make.

---

### Post by Shishimaru on 2013-07-09
I made it. Stayed a couple of days and seems that wifi disconnected only once and reconnected. It only happens that I'm connected but I lose all the packets, but it's still a great step forward since I can reboot the router from my web browser.
Just a question: isn't that 3.10-rc1 backport already in Linux 3.10? I should have it in mine I installed as well, I think. I'm using Raring's default version (3.8) now with 3.10 backport now.

---

### Post by wildmanne39 on 2013-07-09
Hi, no the backport was removed in 13.04.

---

### Post by Shishimaru on 2013-07-09
But it should be in this one, right? &#8594;&#8594;&#8594; [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10-saucy/)
I installed that but, as you noticed, I still had disconnection issues from 3.2 to 3.10. Now everything seems to work better with 3.8 + 3.10 backport.

---

### Post by wildmanne39 on 2013-07-09
The backport drivers are not installed when you install ubuntu they are not part of the kernel but you use to be able to install them with software center, since 13.04 it was removed from the repository.

So the driver you installed is not the same that comes with ubuntu.

---

### Post by Shishimaru on 2013-07-09
So, a backport is a backport, I won't find it in 3.10 as well.
Thank you very much. I'll keep you updated if something new is going to occur. Thank you again.

---

### Post by wildmanne39 on 2013-07-09
Your welcome! 
Thanks to chili555 for your invaluable input.

---

### Post by Shishimaru on 2013-07-12
I definitely spoke too soon :'(
I had the usual disconnection and can't connect again.

Didn't change anything from last time.

```
[ 8424.612444] wlan0: authenticated
[ 8424.616066] wlan0: associate with 38:22:9d:03:a7:d2 (try 1/3)
[ 8424.643055] wlan0: RX AssocResp from 38:22:9d:03:a7:d2 (capab=0x431 status=0 aid=1)
[ 8424.645078] wlan0: associated
[ 8589.837180] cfg80211: Calling CRDA to update world regulatory domain
[ 8589.841743] cfg80211: World regulatory domain updated:
[ 8589.841746] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8589.841748] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8589.841751] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8589.841753] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 8589.841755] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8589.841757] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8601.192588] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8601.193734] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8601.300050] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8601.404051] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8601.508030] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 8604.742173] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8604.743289] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8604.848065] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8604.952049] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8605.057773] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 8627.243779] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[ 8630.769536] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 8630.772126] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 8630.775156] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 8630.896786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8637.200694] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8637.204253] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8637.308065] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8637.412050] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8637.516054] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 8648.878007] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8648.879005] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8648.984063] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8649.088053] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8649.192161] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 8652.424996] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8652.426420] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8652.532056] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8652.636053] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8652.740050] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 8667.645412] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8667.646898] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8667.752187] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8667.856072] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8667.960070] wlan0: authentication with 38:22:9d:03:a7:d2 timed out
[ 8671.199489] wlan0: authenticate with 38:22:9d:03:a7:d2
[ 8671.201122] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 1/3)
[ 8671.308054] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 2/3)
[ 8671.412042] wlan0: direct probe to 38:22:9d:03:a7:d2 (try 3/3)
[ 8671.516046] wlan0: authentication with 38:22:9d:03:a7:d2 timed out


```



I was thinking that it would be fantastic to have the router to reboot itself every x minutes automatically, but I think this is impossible. It's easier to have it if I was always connected, but I'm not.

---

### Post by wildmanne39 on 2013-07-12
Hi, I doubt it is the same issue because it worked for five days.

Did you install any updates? 
Did you look at the updates to see what was being updated?
Did your computer lose its power supply?
Copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Shishimaru on 2013-07-13
In these days disconnected and reconnected immediately, so I thought it was solved. Maybe I've only been lucky?
Yeah, in these day I installed Raring latest updates: compiz. I didn't upgrade the kernel though.

The result of the script is attached to this post.

---

### Post by wildmanne39 on 2013-07-13
Please post the output of:
```
modinfo iwlwifi | grep version
ls -al /lib/firmware
```
Thanks

---

### Post by Shishimaru on 2013-07-13
Here:

```
~$ modinfo iwlwifi | grep version
version:        backported from Linux (v3.10-rc1-0-gf722406) using backports v3.10-rc1-2-0-gc918a4f
version:        in-tree:d
srcversion:     6F7438EAFC6C63ADEA69991
vermagic:       3.8.0-25-generic SMP mod_unload modversions 


```

```
~$ ls -al /lib/firmware
totale 19912
drwxr-xr-x 59 root root   20480 lug 10 22:15 .
drwxr-xr-x 23 root root    4096 giu 19 23:53 ..
drwxr-xr-x 31 root root    4096 lug  2 17:58 3.10.0-031000-generic
drwxr-xr-x  8 root root    4096 giu 16 11:57 3.8.0-25-generic
drwxr-xr-x  2 root root    4096 giu 19 23:34 3com
drwxr-xr-x  2 root root    4096 giu 19 23:34 acenic
drwxr-xr-x  2 root root    4096 giu 19 23:34 adaptec
drwxr-xr-x  2 root root    4096 giu 19 23:34 advansys
-rw-r--r--  1 root root   50698 nov  8  2012 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 nov  8  2012 agere_sta_fw.bin
-rw-r--r--  1 root root   22622 nov  8  2012 aic94xx-seq.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 amd-ucode
drwxr-xr-x  2 root root    4096 giu 19 23:34 ar3k
-rwxr-xr-x  1 root root  153416 dic  3  2012 ar5523.bin
drwxr-xr-x  2 root root    4096 giu 19 23:34 asihpi
-rw-r--r--  1 root root  246804 nov  8  2012 ath3k-1.fw
drwxr-xr-x  4 root root    4096 apr  5 22:01 ath6k
-rw-r--r--  1 root root   35180 nov  8  2012 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 nov  8  2012 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root    9726 nov  8  2012 atmsar11.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 av7110
drwxr-xr-x  2 root root    4096 giu 19 23:34 bnx2x
drwxr-xr-x  2 root root    4096 giu 19 23:34 brcm
-rw-r--r--  1 root root   13388 gen 29 20:05 carl9170-1.fw
drwxr-xr-x  9 root root    4096 giu 19 23:34 carl9170fw
drwxr-xr-x  3 root root    4096 giu 19 23:34 cis
-rw-r--r--  1 root root     107 nov  8  2012 configure
drwxr-xr-x  2 root root    4096 giu 19 23:34 cpia2
drwxr-xr-x  2 root root    4096 giu 19 23:34 cxgb3
drwxr-xr-x  2 root root    4096 giu 19 23:34 cxgb4
drwxr-xr-x  2 root root    4096 giu 19 23:34 dsp56k
-rw-r--r--  1 root root   12401 nov  8  2012 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   33768 nov  8  2012 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root   50222 nov  8  2012 dvb-usb-terratec-h5-drxk.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 ea
drwxr-xr-x  2 root root    4096 giu 19 23:34 edgeport
drwxr-xr-x  2 root root    4096 giu 19 23:34 emi26
drwxr-xr-x  2 root root    4096 giu 19 23:34 emi62
drwxr-xr-x  2 root root    4096 giu 19 23:34 ene-ub6250
drwxr-xr-x  2 root root    4096 giu 19 23:34 ess
-rw-r--r--  1 root root  180776 nov  8  2012 f2255usb.bin
-rw-r--r--  1 root root   35068 nov  8  2012 GPL-3
drwxr-xr-x  2 root root    4096 feb 14  2012 hp
-rw-r--r--  1 root root   72992 nov  8  2012 htc_7010.fw
-rw-r--r--  1 root root   51272 nov  8  2012 htc_9271.fw
-rw-r--r--  1 root root 1251036 nov  8  2012 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root 1334532 nov  8  2012 i2400m-fw-usb-1.5.sbcf
-rw-r--r--  1 root root 1531932 nov  8  2012 i6050-fw-usb-1.5.sbcf
-rw-r--r--  1 root root  209190 nov  8  2012 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 nov  8  2012 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 nov  8  2012 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 nov  8  2012 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 nov  8  2012 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 nov  8  2012 ipw2200-sniffer.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 isci
-rw-r--r--  1 root root  337520 nov  8  2012 iwlwifi-1000-5.ucode
-rw-r--r--  1 root root  337572 nov  8  2012 iwlwifi-100-5.ucode
-rw-r--r--  1 root root  689680 nov  8  2012 iwlwifi-105-6.ucode
-rw-r--r--  1 root root  701228 nov  8  2012 iwlwifi-135-6.ucode
-rw-r--r--  1 root root  695876 nov  8  2012 iwlwifi-2000-6.ucode
-rw-r--r--  1 root root  707392 nov  8  2012 iwlwifi-2030-6.ucode
-rw-r--r--  1 root root  150100 nov  8  2012 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 nov  8  2012 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  340696 nov  8  2012 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  337400 nov  8  2012 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 nov  8  2012 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 nov  8  2012 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  677296 nov  8  2012 iwlwifi-6000g2a-6.ucode
-rw-r--r--  1 root root  679436 nov  8  2012 iwlwifi-6000g2b-6.ucode
-rw-r--r--  1 root root  469780 nov  8  2012 iwlwifi-6050-5.ucode
drwxr-xr-x  2 root root    4096 giu 19 23:34 kaweth
drwxr-xr-x  2 root root    4096 giu 19 23:34 keyspan
drwxr-xr-x  2 root root    4096 giu 19 23:34 keyspan_pda
drwxr-xr-x  2 root root    4096 giu 19 23:34 korg
-rw-r--r--  1 root root  118888 nov  8  2012 lbtf_usb.bin
-rw-r--r--  1 root root     262 nov  8  2012 lgs8g75.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 libertas
-rw-r--r--  1 root root     319 nov  8  2012 Makefile
drwxr-xr-x  2 root root    4096 giu 19 23:34 matrox
drwxr-xr-x  2 root root    4096 giu 19 23:34 mrvl
-rw-r--r--  1 root root   13847 nov  8  2012 mts_cdma.fw
-rw-r--r--  1 root root   14067 nov  8  2012 mts_edge.fw
-rw-r--r--  1 root root   13847 nov  8  2012 mts_gsm.fw
-rw-r--r--  1 root root   13769 nov  8  2012 mts_mt9234mu.fw
-rw-r--r--  1 root root   13769 nov  8  2012 mts_mt9234zba.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 mwl8k
-rw-r--r--  1 root root  377784 nov  8  2012 myri10ge_ethp_z8e.dat
-rw-r--r--  1 root root  367464 nov  8  2012 myri10ge_eth_z8e.dat
-rw-r--r--  1 root root  563592 nov  8  2012 myri10ge_rss_ethp_z8e.dat
-rw-r--r--  1 root root  553192 nov  8  2012 myri10ge_rss_eth_z8e.dat
-rw-r--r--  1 root root   15664 nov  8  2012 NPE-B
-rw-r--r--  1 root root   15664 nov  8  2012 NPE-C
drwxr-xr-x  2 root root    4096 giu 19 23:34 ositech
-rw-r--r--  1 root root 1845305 apr 10 15:33 phanfw.bin
-rw-r--r--  1 root root   76802 nov  8  2012 ql2100_fw.bin
-rw-r--r--  1 root root   84566 nov  8  2012 ql2200_fw.bin
-rw-r--r--  1 root root  125252 nov  8  2012 ql2300_fw.bin
-rw-r--r--  1 root root  136038 nov  8  2012 ql2322_fw.bin
-rw-r--r--  1 root root  257108 gen  4  2013 ql2400_fw.bin
-rw-r--r--  1 root root  260064 gen  4  2013 ql2500_fw.bin
drwxr-xr-x  2 root root    4096 giu 19 23:34 r128
drwxr-xr-x  2 root root   12288 giu 19 23:34 radeon
-rw-r--r--  1 root root    1419 nov  8  2012 README
-rw-r--r--  1 root root    8192 nov  8  2012 rt2561.bin
-rw-r--r--  1 root root    8192 nov  8  2012 rt2561s.bin
-rw-r--r--  1 root root    8192 nov  8  2012 rt2661.bin
-rw-r--r--  1 root root    8192 nov  8  2012 rt2860.bin
-rw-r--r--  1 root root    8192 nov  8  2012 rt2870.bin
lrwxrwxrwx  1 root root      10 nov  8  2012 rt3070.bin -> rt2870.bin
lrwxrwxrwx  1 root root      10 nov  8  2012 rt3090.bin -> rt2860.bin
-rw-r--r--  1 root root    4096 apr 18 14:35 rt3290.bin
-rw-r--r--  1 root root    2048 nov  8  2012 rt73.bin
drwxr-xr-x  2 root root    4096 giu 19 23:34 RTL8192E
drwxr-xr-x  2 root root    4096 giu 19 23:34 rtl_nic
drwxr-xr-x  2 root root    4096 giu 19 23:34 rtlwifi
-rw-r--r--  1 root root    9508 nov  8  2012 s2250.fw
-rw-r--r--  1 root root    1092 nov  8  2012 s2250_loader.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 s5p-mfc
drwxr-xr-x  2 root root    4096 giu 19 23:34 sb16
drwxr-xr-x  2 root root    4096 giu 19 23:34 scripts
drwxr-xr-x  2 root root    4096 giu 19 23:34 slicoss
drwxr-xr-x  2 root root    4096 giu 19 23:34 sun
drwxr-xr-x  2 root root    4096 giu 19 23:34 tehuti
-rw-r--r--  1 root root   13765 nov  8  2012 ti_3410.fw
-rw-r--r--  1 root root   13764 nov  8  2012 ti_5052.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 ti-connectivity
drwxr-xr-x  2 root root    4096 giu 19 23:34 tigon
-rw-r--r--  1 root root   51972 nov  8  2012 tlg2300_firmware.bin
drwxr-xr-x  2 root root    4096 giu 19 23:34 ttusb-budget
drwxr-xr-x  2 root root    4096 giu 19 23:34 ueagle-atm
drwxr-xr-x  2 root root    4096 giu 19 23:34 usbdux
-rw-r--r--  1 root root     999 nov  8  2012 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 nov  8  2012 usbdux_firmware.bin
-rw-r--r--  1 root root    8192 nov  8  2012 usbduxsigma_firmware.bin
-rw-r--r--  1 root root   16382 nov  8  2012 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 nov  8  2012 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 nov  8  2012 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 nov  8  2012 v4l-cx23418-dig.fw
-rw-r--r--  1 root root  262144 nov  8  2012 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 nov  8  2012 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 nov  8  2012 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root   16382 nov  8  2012 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 nov  8  2012 v4l-cx25840.fw
-rw-r--r--  1 root root    8192 nov  8  2012 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 nov  8  2012 v4l-pvrusb2-29xxx-01.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 vicam
-rw-r--r--  1 root root   11341 nov  8  2012 vntwusb.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 vxge
-rw-r--r--  1 root root    5186 gen 29 20:05 WHENCE.ubuntu
-rw-r--r--  1 root root   23554 nov  8  2012 whiteheat.fw
-rw-r--r--  1 root root    5626 nov  8  2012 whiteheat_loader.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 yam
drwxr-xr-x  2 root root    4096 giu 19 23:34 yamaha
-rw-r--r--  1 root root   62484 nov  8  2012 zd1201-ap.fw
-rw-r--r--  1 root root   70612 nov  8  2012 zd1201.fw
drwxr-xr-x  2 root root    4096 giu 19 23:34 zd1211


```

---

### Post by wildmanne39 on 2013-07-13
Have you tried connecting with your wireless without the ethernet plugged in?

Can you look and see if network manager was updated?
Thanks

---

### Post by Shishimaru on 2013-07-13
I can only use this connection via wifi since it comes from the 1st floor where my uncle lives (it's very close, so the signal is very strong).

---

### Post by wildmanne39 on 2013-07-13
What is this then? ```
Device: usb0  [Connessione via cavo 2] ---------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

```
Thanks

---

### Post by wildmanne39 on 2013-07-13
Nevermind you are tethering, you have to disconnect that before wireless will work.
Thanks

---

### Post by Shishimaru on 2013-07-13
I was using 3G tethering because wifi didn't work. Otherwise, I can't look for support here.

---

### Post by wildmanne39 on 2013-07-13
I understand but I need to see the wireless script information without the tethering connect.

Disconnect the tethering then go into your home folder and click on the wireless script and choose run then post the results here.
Thanks

---

### Post by Shishimaru on 2013-07-13
Ok, I'm attaching the wireless-info again. In this very moment wifi is working since my uncle rebooted the router; I'm start thinking that he has problems too.

---

### Post by wildmanne39 on 2013-07-13
I suspect you may be having trouble with your router it may be going out, but I do not know that for sure.

I have done all I know to do.

---

### Post by Shishimaru on 2013-07-13
Okay, thank you again anyway for all your efforts. I'll try to invent something to reboot the router every x minutes or just buy another access point to add, when I can.

---

### Post by chili555 on 2013-07-15
I suggest the following:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the file to:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/rc.local
```Just above exit 0, add this line:```
iw reg set IT
```I am assuming your country code is IT corresponding to Italy as shown in your location. Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/mac80211.conf
```A new, empty file will open. Add this single line:```
options mac80211 probe_wait_ms=5000
```Proofread carefully, save and close gedit.

Reboot and let us have a report.

---

### Post by gregory_ on 2013-08-07
Thanks a lot i had the same problem, the post above seems to have fixed it (did not disconnected for a long time already).
I have ubuntu 13.04 with 3.8.0-27-generic kernel
Pc specs:
HP 655 laptop, AMD E1-1200 1.4ghz, AMD Radeon HD 7310
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 07)
Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe

Hm, it just disconnected again, i disable-reenable networking and it connects, after the 1st disconnect i have a similar ssid with number 1 aside untill next reboot, btw it might be my problem, i only tried the above post i ll investigate my problem further.

It looks like it was my routers problem, when i closed my torrents it didn't disconnected again. Sorry if wasted someones time.

---

