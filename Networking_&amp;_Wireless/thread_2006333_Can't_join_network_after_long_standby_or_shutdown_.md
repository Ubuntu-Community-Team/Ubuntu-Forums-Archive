---
title: "Can't join network after long standby or shutdown (DWA-552 AR5416, 12.04)"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by coffeecaet on 2012-06-19
My wireless card works perfectly until I go into sleep mode for longer than roughly 30 minutes or I shut down my computer for longer than 30 minutes.
To get it working after that, I have to boot into windows. Restarting, restarting networkmanager, unloading and reloading ath9k, nothing works except booting into windows. I guess the windows driver properly wakes up the card or initializes it right or something, because even the light won't work right on the card until booting into windows after a suspend.

$ uname -mr
```
3.2.0-25-generic x86_64
```$ lspci
```
04:01.0 Network controller: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] (rev 01)
```sudo lshw -C network
```
 *-network               
       description: Wireless interface
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 01
       serial: 00:22:b0:ce:5e:4b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-25-generic firmware=N/A ip=192.168.1.3 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fe500000-fe50ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:f8:bb:25
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:51 ioport:d000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff

```$ lsmod | grep ath
```
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath

```NetworkManager logs say this after waking up/powering on and wireless doesn't work:
```
Jun 18 16:31:26 teal NetworkManager[1109]: <info> wake requested (sleeping: yes  enabled: yes)
Jun 18 16:31:26 teal NetworkManager[1109]: <info> waking up and re-enabling...
Jun 18 16:31:26 teal NetworkManager[1109]: <info> WWAN now enabled by management service
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (wlan0): now managed
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (wlan0): bringing up device.
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (wlan0): preparing device.
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 18 16:31:26 teal NetworkManager[1109]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 18 16:31:26 teal NetworkManager[1109]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (eth0): now managed
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 18 16:31:26 teal NetworkManager[1109]: <info> (eth0): bringing up device.
Jun 18 16:31:26 teal kernel: [65510.625217] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 18 16:31:27 teal NetworkManager[1109]: <info> (eth0): preparing device.
Jun 18 16:31:27 teal NetworkManager[1109]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 18 16:31:27 teal kernel: [65510.732980] r8169 0000:05:00.0: eth0: link down
Jun 18 16:31:27 teal kernel: [65510.733297] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 18 16:31:27 teal NetworkManager[1109]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 18 16:31:27 teal NetworkManager[1109]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 18 16:31:27 teal NetworkManager[1109]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 18 16:31:27 teal NetworkManager[1109]: <warn> Trying to remove a non-existant call id.
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Auto-activating connection 'GOULD'.
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) starting connection 'GOULD'
Jun 18 16:31:28 teal NetworkManager[1109]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0/wireless): access point 'GOULD' has security, but secrets are required.
Jun 18 16:31:28 teal NetworkManager[1109]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 18 16:31:28 teal NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 18 16:31:28 teal NetworkManager[1109]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
``````
Jun 18 16:34:37 teal kernel: [65701.319328] wlan0: direct probe to XX:XX:XX:XX:XX (try 1/3)
Jun 18 16:34:37 teal kernel: [65701.516065] wlan0: direct probe to XX:XX:XX:XX:XX (try 2/3)
Jun 18 16:34:38 teal kernel: [65701.716035] wlan0: direct probe to XX:XX:XX:XX:XX (try 3/3)
Jun 18 16:34:38 teal kernel: [65701.916068] wlan0: direct probe to XX:XX:XX:XX:XX timed out
Jun 18 16:35:31 teal NetworkManager[1109]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 18 16:35:31 teal NetworkManager[1109]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
```I'll try posting more relevant logs after putting it to sleep tonight

---

### Post by coffeecaet on 2012-06-19
Should I my dmesg as well?
Happened again after automatically going to sleep, restarting  networkmanager/reloading ath9k/restarting computer did not help. Only  way I can seem to get this to work is to boot Windows.

kern.log
```
Jun 19 17:00:15 teal kernel: [33983.277935] wlan0: deauthenticating from XX:XX:XX:XX:XX:XX by local choice (reason=3)
Jun 19 17:00:15 teal kernel: [33983.838388] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 19 17:00:15 teal kernel: [33983.838391] cfg80211: Restoring regulatory settings
Jun 19 17:00:15 teal kernel: [33983.838393] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 17:00:15 teal kernel: [33983.840491] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840494] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840495] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840496] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840497] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840498] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840499] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840500] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840501] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840502] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840503] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840504] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840505] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840506] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840507] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840509] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840509] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840511] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840512] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840513] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840514] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840515] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840516] cfg80211: Disabling freq 2467 MHz
Jun 19 17:00:15 teal kernel: [33983.840516] cfg80211: Disabling freq 2472 MHz
Jun 19 17:00:15 teal kernel: [33983.840517] cfg80211: Disabling freq 2484 MHz
Jun 19 17:00:15 teal kernel: [33983.840519] cfg80211: World regulatory domain updated:
Jun 19 17:00:15 teal kernel: [33983.840520] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 19 17:00:15 teal kernel: [33983.840521] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840522] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840523] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840524] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840525] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:17 teal kernel: [33985.549012] PM: Syncing filesystems ... done.
Jun 19 17:00:17 teal kernel: [33985.552219] PM: Preparing system for mem sleep
Jun 19 19:21:04 teal kernel: [33986.450409] Freezing user space processes ... (elapsed 0.01 seconds) done.
Jun 19 19:21:04 teal kernel: [33986.465786] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Jun 19 19:21:04 teal kernel: [33986.481786] PM: Entering mem sleep
Jun 19 19:21:04 teal kernel: [33986.481852] Suspending console(s) (use no_console_suspend to debug)
Jun 19 19:21:04 teal kernel: [33986.482564] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482693] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482763] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482839] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482880] sd 3:0:0:0: [sdd] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.482882] sd 2:0:0:0: [sdc] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.483026] sd 1:0:0:0: [sdb] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.483028] sd 0:0:0:0: [sda] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.483907] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 4 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.484907] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 2 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.485987] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.486142] serial 00:0a: disabled
Jun 19 19:21:04 teal kernel: [33986.486145] serial 00:0a: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33986.486151] i8042 kbd 00:09: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33986.486471] [fglrx] IRQ 56 Disabled
Jun 19 19:21:04 teal kernel: [33986.486555] [fglrx] Preparing suspend fglrx in kernel.
Jun 19 19:21:04 teal kernel: [33986.555432] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 2 ep 2 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.555674] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 2 ep 0 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.577758] ehci_hcd 0000:00:1d.0: PCI INT A disabled
Jun 19 19:21:04 teal kernel: [33986.589787] ehci_hcd 0000:00:1a.0: PCI INT A disabled
Jun 19 19:21:04 teal kernel: [33986.589788] PM: suspend of drv:ehci_hcd dev:0000:00:1a.0 complete after 103.035 msecs
Jun 19 19:21:04 teal kernel: [33986.589803] snd_hda_intel 0000:01:00.1: PCI INT B disabled
Jun 19 19:21:04 teal kernel: [33986.589843] ACPI handle has no context!
Jun 19 19:21:04 teal kernel: [33986.605739] PM: suspend of drv:snd_hda_intel dev:0000:01:00.1 complete after 119.329 msecs
Jun 19 19:21:04 teal kernel: [33986.794700] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
Jun 19 19:21:04 teal kernel: [33986.794753] ACPI handle has no context!
Jun 19 19:21:04 teal kernel: [33986.809745] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 323.001 msecs
Jun 19 19:21:04 teal kernel: [33986.844212] [fglrx] Suspending fglrx in kernel completed.
Jun 19 19:21:04 teal kernel: [33986.844213] [fglrx] Power down the ASIC .
Jun 19 19:21:04 teal kernel: [33986.844244] PM: suspend of drv:fglrx_pci dev:0000:01:00.0 complete after 357.801 msecs
Jun 19 19:21:04 teal kernel: [33986.844252] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 357.437 msecs
Jun 19 19:21:04 teal kernel: [33986.857750] PM: suspend of drv:i915 dev:0000:00:02.0 complete after 370.941 msecs
Jun 19 19:21:04 teal kernel: [33987.005445] PM: suspend of drv:sd dev:0:0:0:0 complete after 522.617 msecs
Jun 19 19:21:04 teal kernel: [33987.005579] PM: suspend of drv:scsi dev:target0:0:0 complete after 522.745 msecs
Jun 19 19:21:04 teal kernel: [33987.005584] PM: suspend of drv:sd dev:2:0:0:0 complete after 522.905 msecs
Jun 19 19:21:04 teal kernel: [33987.005589] PM: suspend of drv:scsi dev:target2:0:0 complete after 522.868 msecs
Jun 19 19:21:04 teal kernel: [33987.005594] PM: suspend of drv:scsi dev:host2 complete after 519.476 msecs
Jun 19 19:21:04 teal kernel: [33987.005597] PM: suspend of drv:scsi dev:host0 complete after 519.387 msecs
Jun 19 19:21:04 teal kernel: [33987.021738] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 535.236 msecs
Jun 19 19:21:04 teal kernel: [33987.021866] PM: suspend of drv: dev:pci0000:00 complete after 535.046 msecs
Jun 19 19:21:04 teal kernel: [33987.021871] PM: suspend of devices complete after 539.955 msecs
Jun 19 19:21:04 teal kernel: [33987.021872] PM: suspend devices took 0.540 seconds
Jun 19 19:21:04 teal kernel: [33987.022021] xhci_hcd 0000:06:00.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.022026] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.037869] r8169 0000:05:00.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.037873] pcieport 0000:00:1c.4: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.054009] ehci_hcd 0000:00:1d.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.054012] ehci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.069796] ehci_hcd 0000:00:1a.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.069806] ehci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.101874] PM: late suspend of devices complete after 80.001 msecs
Jun 19 19:21:04 teal kernel: [33987.102075] ACPI: Preparing to enter system sleep state S3
Jun 19 19:21:04 teal kernel: [33987.501962] PM: Saving platform NVS memory
Jun 19 19:21:04 teal kernel: [33987.503048] Disabling non-boot CPUs ...
Jun 19 19:21:04 teal kernel: [33987.605730] CPU 1 is now offline
Jun 19 19:21:04 teal kernel: [33987.709726] CPU 2 is now offline
Jun 19 19:21:04 teal kernel: [33987.813718] CPU 3 is now offline
Jun 19 19:21:04 teal kernel: [33987.814017] Extended CMOS year: 2000
Jun 19 19:21:04 teal kernel: [33987.814233] ACPI: Low-level resume complete
Jun 19 19:21:04 teal kernel: [33987.814266] PM: Restoring platform NVS memory
Jun 19 19:21:04 teal kernel: [33987.814599] Extended CMOS year: 2000
Jun 19 19:21:04 teal kernel: [33987.814614] Enabling non-boot CPUs ...
Jun 19 19:21:04 teal kernel: [33987.814689] Booting Node 0 Processor 1 APIC 0x2
Jun 19 19:21:04 teal kernel: [33987.814689] smpboot cpu 1: start_ip = 98000
Jun 19 19:21:04 teal kernel: [33988.883566] Calibrating delay loop (skipped) already calibrated this CPU
Jun 19 19:21:04 teal kernel: [33987.845817] TSC synchronization [CPU#0 -> CPU#1]:
Jun 19 19:21:04 teal kernel: [33987.845818] Measured 3483092704 cycles TSC warp between CPUs, turning off TSC clock.
Jun 19 19:21:04 teal kernel: [    0.008000] Marking TSC unstable due to check_tsc_sync_source failed
Jun 19 19:21:04 teal kernel: [33989.609551] Switching to clocksource hpet
Jun 19 19:21:04 teal kernel: [33989.609642] NMI watchdog enabled, takes one hw-pmu counter.
Jun 19 19:21:04 teal kernel: [33989.609930] CPU1 is up
Jun 19 19:21:04 teal kernel: [33989.610109] Booting Node 0 Processor 2 APIC 0x4
Jun 19 19:21:04 teal kernel: [33989.610111] smpboot cpu 2: start_ip = 98000
Jun 19 19:21:04 teal kernel: [    0.008000] Calibrating delay loop (skipped) already calibrated this CPU
Jun 19 19:21:04 teal kernel: [33989.621489] NMI watchdog enabled, takes one hw-pmu counter.
Jun 19 19:21:04 teal kernel: [33989.621675] CPU2 is up
Jun 19 19:21:04 teal kernel: [33989.621939] Booting Node 0 Processor 3 APIC 0x6
Jun 19 19:21:04 teal kernel: [33989.621940] smpboot cpu 3: start_ip = 98000
Jun 19 19:21:04 teal kernel: [    0.008000] Calibrating delay loop (skipped) already calibrated this CPU
Jun 19 19:21:04 teal kernel: [33989.633728] NMI watchdog enabled, takes one hw-pmu counter.
Jun 19 19:21:04 teal kernel: [33989.634036] CPU3 is up
Jun 19 19:21:04 teal kernel: [33989.635947] ACPI: Waking up from system sleep state S3
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x18010b)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xcff1c001)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x8 (was 0x0, writing 0xfe60fe60)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0xe0e0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900006, writing 0x900407)
Jun 19 19:21:04 teal kernel: [33989.635947] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfed0e004, writing 0xfe708004)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe707000)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10010a)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x100403)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xfe50fe50)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x10010a)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xd001d001)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0xd0d0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x10020b)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xfe40fe40)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe706000)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.635947] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x203)
Jun 19 19:21:04 teal kernel: [33989.635947] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x300, writing 0x30b)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfe600000)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x8 (was 0x1, writing 0xe001)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfe620004)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x4 (was 0xc, writing 0xc000000c)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100403)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0xf (was 0x2ff, writing 0x20a)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0x4 (was 0x4, writing 0xfe640004)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x100103)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x8 (was 0x0, writing 0xfe50fe50)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x7 (was 0x20200101, writing 0x202001f1)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe500000)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0x3 (was 0x0, writing 0xa810)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00006)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xd000000c)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xd000400c)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfe400004)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100402)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.635947] PM: early resume of devices complete after 2.038 msecs
Jun 19 19:21:04 teal kernel: [33989.635964] i915 0000:00:02.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 19 19:21:04 teal kernel: [33989.635964] mei 0000:00:16.0: irq 52 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:00:1b.0: irq 54 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] ahci 0000:00:1f.2: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] fglrx_pci 0000:01:00.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] pci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 19 19:21:04 teal kernel: [33989.635964] pci 0000:03:00.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:01:00.1: irq 55 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.635964] pcieport 0000:00:1c.4: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635964] r8169 0000:05:00.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.639473] xhci_hcd 0000:06:00.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.639494] usb usb3: root hub lost power or was reset
Jun 19 19:21:04 teal kernel: [33989.639495] usb usb4: root hub lost power or was reset
Jun 19 19:21:04 teal kernel: [33989.649197] i8042 kbd 00:09: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.649474] serial 00:0a: activated
Jun 19 19:21:04 teal kernel: [33989.650136] xhci_hcd 0000:06:00.0: irq 46 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650138] xhci_hcd 0000:06:00.0: irq 47 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650140] xhci_hcd 0000:06:00.0: irq 48 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650142] xhci_hcd 0000:06:00.0: irq 49 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650143] xhci_hcd 0000:06:00.0: irq 50 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.653416] [fglrx] Power up the ASIC
Jun 19 19:21:04 teal kernel: [33989.653423] [fglrx] Preparing resume fglrx in kernel.
Jun 19 19:21:04 teal kernel: [33989.657146] sd 0:0:0:0: [sda] Starting disk
Jun 19 19:21:04 teal kernel: [33989.657158] sd 1:0:0:0: [sdb] Starting disk
Jun 19 19:21:04 teal kernel: [33989.657169] sd 2:0:0:0: [sdc] Starting disk
Jun 19 19:21:04 teal kernel: [33989.657176] sd 3:0:0:0: [sdd] Starting disk
Jun 19 19:21:04 teal kernel: [33989.671000] [fglrx] Resuming fglrx in kernel completed.
Jun 19 19:21:04 teal kernel: [33989.671035] [fglrx] IRQ 56 Enabled
Jun 19 19:21:04 teal kernel: [33989.709087] No ACPI video bus found
Jun 19 19:21:04 teal kernel: [33989.776073] PM: resume of drv: dev:ep_00 complete after 118.937 msecs
Jun 19 19:21:04 teal kernel: [33989.776151] PM: resume of drv:hub dev:4-0:1.0 complete after 119.020 msecs
Jun 19 19:21:04 teal kernel: [33989.776186] PM: resume of drv: dev:ep_81 complete after 119.054 msecs
Jun 19 19:21:04 teal kernel: [33989.776781] PM: resume of drv: dev:ep_00 complete after 118.811 msecs
Jun 19 19:21:04 teal kernel: [33989.776806] PM: resume of drv:btusb dev:2-1.1:1.0 complete after 118.992 msecs
Jun 19 19:21:04 teal kernel: [33989.776810] PM: resume of drv:btusb dev:2-1.1:1.1 complete after 118.903 msecs
Jun 19 19:21:04 teal kernel: [33989.776817] PM: resume of drv: dev:ep_83 complete after 118.889 msecs
Jun 19 19:21:04 teal kernel: [33989.776846] PM: resume of drv: dev:ep_03 complete after 118.897 msecs
Jun 19 19:21:04 teal kernel: [33989.776848] PM: resume of drv: dev:ep_82 complete after 118.980 msecs
Jun 19 19:21:04 teal kernel: [33989.776850] PM: resume of drv: dev:ep_02 complete after 118.966 msecs
Jun 19 19:21:04 teal kernel: [33989.776854] PM: resume of drv: dev:ep_81 complete after 119.010 msecs
Jun 19 19:21:04 teal kernel: [33989.777172] PM: resume of drv:hub dev:2-1.4:1.0 complete after 119.161 msecs
Jun 19 19:21:04 teal kernel: [33989.777176] PM: resume of drv: dev:ep_00 complete after 119.119 msecs
Jun 19 19:21:04 teal kernel: [33989.777198] PM: resume of drv: dev:ep_81 complete after 119.166 msecs
Jun 19 19:21:04 teal kernel: [33989.880170] PM: resume of drv: dev:ep_00 complete after 223.063 msecs
Jun 19 19:21:04 teal kernel: [33989.880173] PM: resume of drv:hub dev:3-0:1.0 complete after 223.078 msecs
Jun 19 19:21:04 teal kernel: [33989.880200] PM: resume of drv: dev:ep_81 complete after 223.097 msecs
Jun 19 19:21:04 teal kernel: [33989.976045] ata6: SATA link down (SStatus 0 SControl 300)
Jun 19 19:21:04 teal kernel: [33989.984046] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 19:21:04 teal kernel: [33989.991487] ata5.00: configured for UDMA/100
Jun 19 19:21:04 teal kernel: [33990.048192] usb 3-2: reset high-speed USB device number 3 using xhci_hcd
Jun 19 19:21:04 teal kernel: [33990.068712] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88026dec9400
Jun 19 19:21:04 teal kernel: [33990.173186] PM: resume of drv:hub dev:3-2:1.0 complete after 515.500 msecs
Jun 19 19:21:04 teal kernel: [33990.173189] PM: resume of drv: dev:ep_00 complete after 515.439 msecs
Jun 19 19:21:04 teal kernel: [33990.173216] PM: resume of drv: dev:ep_81 complete after 515.499 msecs
Jun 19 19:21:04 teal kernel: [33990.236200] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
Jun 19 19:21:04 teal kernel: [33990.258222] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88026dec9b80
Jun 19 19:21:04 teal kernel: [33990.258226] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88026dec9bc0
Jun 19 19:21:04 teal kernel: [33990.260037] PM: resume of drv:usbhid dev:3-1:1.0 complete after 602.518 msecs
Jun 19 19:21:04 teal kernel: [33990.260043] PM: resume of drv:usbhid dev:3-1:1.1 complete after 602.477 msecs
Jun 19 19:21:04 teal kernel: [33990.260049] PM: resume of drv: dev:ep_00 complete after 602.424 msecs
Jun 19 19:21:04 teal kernel: [33990.260058] PM: resume of drv: dev:ep_82 complete after 602.465 msecs
Jun 19 19:21:04 teal kernel: [33990.260078] PM: resume of drv: dev:ep_81 complete after 602.541 msecs
Jun 19 19:21:04 teal kernel: [33995.032032] ata4: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.040034] ata1: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.048034] ata2: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.056034] ata3: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.320045] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jun 19 19:21:04 teal kernel: [33995.331985] ata1.00: configured for UDMA/133
Jun 19 19:21:04 teal kernel: [33995.377575] PM: resume of drv:sd dev:0:0:0:0 complete after 5720.430 msecs
Jun 19 19:21:04 teal kernel: [33995.377687] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 5720.618 msecs
Jun 19 19:21:04 teal kernel: [33995.377690] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 5720.535 msecs
Jun 19 19:21:04 teal kernel: [33995.384042] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 19:21:04 teal kernel: [33995.402326] ata2.00: configured for UDMA/133
Jun 19 19:21:04 teal kernel: [33995.451568] PM: resume of drv:sd dev:1:0:0:0 complete after 5794.408 msecs
Jun 19 19:21:04 teal kernel: [33995.451682] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 5794.522 msecs
Jun 19 19:21:04 teal kernel: [33995.504039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 19 19:21:04 teal kernel: [33995.506720] ata3.00: configured for UDMA/133
Jun 19 19:21:04 teal kernel: [33995.549126] PM: resume of drv:sd dev:2:0:0:0 complete after 5891.956 msecs
Jun 19 19:21:04 teal kernel: [33995.549236] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 5892.066 msecs
Jun 19 19:21:04 teal kernel: [33996.656042] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 19:21:04 teal kernel: [33996.663152] ata4.00: configured for UDMA/100
Jun 19 19:21:04 teal kernel: [33996.695605] PM: resume of drv:sd dev:3:0:0:0 complete after 7038.426 msecs
Jun 19 19:21:04 teal kernel: [33996.695730] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 7038.550 msecs
Jun 19 19:21:04 teal kernel: [33996.695731] PM: resume of drv:scsi_disk dev:3:0:0:0 complete after 1146.471 msecs
Jun 19 19:21:04 teal kernel: [33996.696119] PM: resume of devices complete after 7061.121 msecs
Jun 19 19:21:04 teal kernel: [33996.696165] PM: resume devices took 7.064 seconds
Jun 19 19:21:04 teal kernel: [33996.696186] PM: Finishing wakeup.
Jun 19 19:21:04 teal kernel: [33996.696187] Restarting tasks ... done.
Jun 19 19:21:04 teal kernel: [33997.470642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 19:21:04 teal kernel: [33997.572969] r8169 0000:05:00.0: eth0: link down
Jun 19 19:21:04 teal kernel: [33997.573278] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 19:21:06 teal kernel: [33998.800625] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 2 with no TDs queued?
Jun 19 19:21:06 teal kernel: [33998.800875] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
Jun 19 19:21:06 teal kernel: [33999.638357] wlan0: authenticate with XX:XX:XX:XX:XX:XX (try 1)
Jun 19 19:21:07 teal kernel: [33999.836023] wlan0: authenticate with XX:XX:XX:XX:XX:XX (try 2)
Jun 19 19:21:07 teal kernel: [34000.036028] wlan0: authenticate with XX:XX:XX:XX:XX:XX (try 3)
Jun 19 19:21:07 teal kernel: [34000.236051] wlan0: authentication with XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:13 teal kernel: [34006.294393] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:13 teal kernel: [34006.492037] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:14 teal kernel: [34006.692038] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:14 teal kernel: [34006.892050] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:20 teal kernel: [34012.986329] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:20 teal kernel: [34013.184068] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:20 teal kernel: [34013.384036] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:20 teal kernel: [34013.584067] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
```syslog
```
Jun 19 17:00:15 teal NetworkManager[1014]: <info> sleep requested (sleeping: no  enabled: yes)
Jun 19 17:00:15 teal NetworkManager[1014]: <info> sleeping or disabling...
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): now unmanaged
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'sleeping') [37]
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1788
Jun 19 17:00:15 teal kernel: [33983.277935] wlan0: deauthenticating from XX:XX:XX:XX:XX:XX by local choice (reason=3)
Jun 19 17:00:15 teal NetworkManager[1014]: <info> DNS: starting dnsmasq...
Jun 19 17:00:15 teal dnsmasq[1792]: exiting on receipt of SIGTERM
Jun 19 17:00:15 teal wpa_supplicant[1085]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 19 17:00:15 teal dnsmasq[15181]: started, version 2.59 cache disabled
Jun 19 17:00:15 teal dnsmasq[15181]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 19 17:00:15 teal dnsmasq[15181]: warning: no upstream servers configured
Jun 19 17:00:15 teal kernel: [33983.838388] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 19 17:00:15 teal kernel: [33983.838391] cfg80211: Restoring regulatory settings
Jun 19 17:00:15 teal kernel: [33983.838393] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 17:00:15 teal kernel: [33983.840491] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840494] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840495] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840496] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840497] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840498] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840499] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840500] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840501] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840502] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840503] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840504] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840505] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840506] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840507] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840509] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840509] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840511] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840512] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840513] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840514] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Jun 19 17:00:15 teal kernel: [33983.840515] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jun 19 17:00:15 teal kernel: [33983.840516] cfg80211: Disabling freq 2467 MHz
Jun 19 17:00:15 teal kernel: [33983.840516] cfg80211: Disabling freq 2472 MHz
Jun 19 17:00:15 teal kernel: [33983.840517] cfg80211: Disabling freq 2484 MHz
Jun 19 17:00:15 teal kernel: [33983.840519] cfg80211: World regulatory domain updated:
Jun 19 17:00:15 teal kernel: [33983.840520] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 19 17:00:15 teal kernel: [33983.840521] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840522] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840523] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840524] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal kernel: [33983.840525] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): cleaning up...
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (wlan0): taking down device.
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (eth0): now unmanaged
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (eth0): cleaning up...
Jun 19 17:00:15 teal NetworkManager[1014]: <info> (eth0): taking down device.
Jun 19 17:00:15 teal dbus[982]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 19 17:00:15 teal dbus[982]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 19 17:00:16 teal anacron[15305]: Anacron 2.3 started on 2012-06-19
Jun 19 17:00:16 teal anacron[15305]: Normal exit (0 jobs run)
Jun 19 17:00:17 teal kernel: [33985.549012] PM: Syncing filesystems ... done.
Jun 19 17:00:17 teal kernel: [33985.552219] PM: Preparing system for mem sleep
Jun 19 19:21:04 teal kernel: [33986.450409] Freezing user space processes ... (elapsed 0.01 seconds) done.
Jun 19 19:21:04 teal kernel: [33986.465786] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
Jun 19 19:21:04 teal kernel: [33986.481786] PM: Entering mem sleep
Jun 19 19:21:04 teal kernel: [33986.481852] Suspending console(s) (use no_console_suspend to debug)
Jun 19 19:21:04 teal kernel: [33986.482564] sd 3:0:0:0: [sdd] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482693] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482763] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482839] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jun 19 19:21:04 teal kernel: [33986.482880] sd 3:0:0:0: [sdd] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.482882] sd 2:0:0:0: [sdc] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.483026] sd 1:0:0:0: [sdb] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.483028] sd 0:0:0:0: [sda] Stopping disk
Jun 19 19:21:04 teal kernel: [33986.483907] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 4 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.484907] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 2 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.485987] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.486142] serial 00:0a: disabled
Jun 19 19:21:04 teal kernel: [33986.486145] serial 00:0a: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33986.486151] i8042 kbd 00:09: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33986.486471] [fglrx] IRQ 56 Disabled
Jun 19 19:21:04 teal kernel: [33986.486555] [fglrx] Preparing suspend fglrx in kernel.
Jun 19 19:21:04 teal kernel: [33986.555432] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 2 ep 2 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.555674] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 2 ep 0 with no TDs queued?
Jun 19 19:21:04 teal kernel: [33986.577758] ehci_hcd 0000:00:1d.0: PCI INT A disabled
Jun 19 19:21:04 teal kernel: [33986.589787] ehci_hcd 0000:00:1a.0: PCI INT A disabled
Jun 19 19:21:04 teal kernel: [33986.589788] PM: suspend of drv:ehci_hcd dev:0000:00:1a.0 complete after 103.035 msecs
Jun 19 19:21:04 teal kernel: [33986.589803] snd_hda_intel 0000:01:00.1: PCI INT B disabled
Jun 19 19:21:04 teal kernel: [33986.589843] ACPI handle has no context!
Jun 19 19:21:04 teal kernel: [33986.605739] PM: suspend of drv:snd_hda_intel dev:0000:01:00.1 complete after 119.329 msecs
Jun 19 19:21:04 teal kernel: [33986.794700] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
Jun 19 19:21:04 teal kernel: [33986.794753] ACPI handle has no context!
Jun 19 19:21:04 teal kernel: [33986.809745] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 323.001 msecs
Jun 19 19:21:04 teal kernel: [33986.844212] [fglrx] Suspending fglrx in kernel completed.
Jun 19 19:21:04 teal kernel: [33986.844213] [fglrx] Power down the ASIC .
Jun 19 19:21:04 teal kernel: [33986.844244] PM: suspend of drv:fglrx_pci dev:0000:01:00.0 complete after 357.801 msecs
Jun 19 19:21:04 teal kernel: [33986.844252] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 357.437 msecs
Jun 19 19:21:04 teal kernel: [33986.857750] PM: suspend of drv:i915 dev:0000:00:02.0 complete after 370.941 msecs
Jun 19 19:21:04 teal kernel: [33987.005445] PM: suspend of drv:sd dev:0:0:0:0 complete after 522.617 msecs
Jun 19 19:21:04 teal kernel: [33987.005579] PM: suspend of drv:scsi dev:target0:0:0 complete after 522.745 msecs
Jun 19 19:21:04 teal kernel: [33987.005584] PM: suspend of drv:sd dev:2:0:0:0 complete after 522.905 msecs
Jun 19 19:21:04 teal kernel: [33987.005589] PM: suspend of drv:scsi dev:target2:0:0 complete after 522.868 msecs
Jun 19 19:21:04 teal kernel: [33987.005594] PM: suspend of drv:scsi dev:host2 complete after 519.476 msecs
Jun 19 19:21:04 teal kernel: [33987.005597] PM: suspend of drv:scsi dev:host0 complete after 519.387 msecs
Jun 19 19:21:04 teal kernel: [33987.021738] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 535.236 msecs
Jun 19 19:21:04 teal kernel: [33987.021866] PM: suspend of drv: dev:pci0000:00 complete after 535.046 msecs
Jun 19 19:21:04 teal kernel: [33987.021871] PM: suspend of devices complete after 539.955 msecs
Jun 19 19:21:04 teal kernel: [33987.021872] PM: suspend devices took 0.540 seconds
Jun 19 19:21:04 teal kernel: [33987.022021] xhci_hcd 0000:06:00.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.022026] pcieport 0000:00:1c.5: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.037869] r8169 0000:05:00.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.037873] pcieport 0000:00:1c.4: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.054009] ehci_hcd 0000:00:1d.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.054012] ehci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.069796] ehci_hcd 0000:00:1a.0: PME# enabled
Jun 19 19:21:04 teal kernel: [33987.069806] ehci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
Jun 19 19:21:04 teal kernel: [33987.101874] PM: late suspend of devices complete after 80.001 msecs
Jun 19 19:21:04 teal kernel: [33987.102075] ACPI: Preparing to enter system sleep state S3
Jun 19 19:21:04 teal kernel: [33987.501962] PM: Saving platform NVS memory
Jun 19 19:21:04 teal kernel: [33987.503048] Disabling non-boot CPUs ...
Jun 19 19:21:04 teal kernel: [33987.605730] CPU 1 is now offline
Jun 19 19:21:04 teal kernel: [33987.709726] CPU 2 is now offline
Jun 19 19:21:04 teal kernel: [33987.813718] CPU 3 is now offline
Jun 19 19:21:04 teal kernel: [33987.814017] Extended CMOS year: 2000
Jun 19 19:21:04 teal kernel: [33987.814233] ACPI: Low-level resume complete
Jun 19 19:21:04 teal kernel: [33987.814266] PM: Restoring platform NVS memory
Jun 19 19:21:04 teal kernel: [33987.814599] Extended CMOS year: 2000
Jun 19 19:21:04 teal kernel: [33987.814614] Enabling non-boot CPUs ...
Jun 19 19:21:04 teal kernel: [33987.814689] Booting Node 0 Processor 1 APIC 0x2
Jun 19 19:21:04 teal kernel: [33987.814689] smpboot cpu 1: start_ip = 98000
Jun 19 19:21:04 teal kernel: [33988.883566] Calibrating delay loop (skipped) already calibrated this CPU
Jun 19 19:21:04 teal kernel: [33987.845817] TSC synchronization [CPU#0 -> CPU#1]:
Jun 19 19:21:04 teal kernel: [33987.845818] Measured 3483092704 cycles TSC warp between CPUs, turning off TSC clock.
Jun 19 19:21:04 teal kernel: [    0.008000] Marking TSC unstable due to check_tsc_sync_source failed
Jun 19 19:21:04 teal kernel: [33989.609551] Switching to clocksource hpet
Jun 19 19:21:04 teal kernel: [33989.609642] NMI watchdog enabled, takes one hw-pmu counter.
Jun 19 19:21:04 teal kernel: [33989.609930] CPU1 is up
Jun 19 19:21:04 teal kernel: [33989.610109] Booting Node 0 Processor 2 APIC 0x4
Jun 19 19:21:04 teal kernel: [33989.610111] smpboot cpu 2: start_ip = 98000
Jun 19 19:21:04 teal kernel: [    0.008000] Calibrating delay loop (skipped) already calibrated this CPU
Jun 19 19:21:04 teal kernel: [33989.621489] NMI watchdog enabled, takes one hw-pmu counter.
Jun 19 19:21:04 teal kernel: [33989.621675] CPU2 is up
Jun 19 19:21:04 teal kernel: [33989.621939] Booting Node 0 Processor 3 APIC 0x6
Jun 19 19:21:04 teal kernel: [33989.621940] smpboot cpu 3: start_ip = 98000
Jun 19 19:21:04 teal kernel: [    0.008000] Calibrating delay loop (skipped) already calibrated this CPU
Jun 19 19:21:04 teal kernel: [33989.633728] NMI watchdog enabled, takes one hw-pmu counter.
Jun 19 19:21:04 teal kernel: [33989.634036] CPU3 is up
Jun 19 19:21:04 teal kernel: [33989.635947] ACPI: Waking up from system sleep state S3
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0xf (was 0x100, writing 0x18010b)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xcff1c001)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x8 (was 0x0, writing 0xfe60fe60)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x7 (was 0x200000f0, writing 0xe0e0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900006, writing 0x900407)
Jun 19 19:21:04 teal kernel: [33989.635947] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfed0e004, writing 0xfe708004)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe707000)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1a.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10010a)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x100403)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xfe50fe50)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x10010a)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xd001d001)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0xd0d0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x10020b)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x8 (was 0x0, writing 0xfe40fe40)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe706000)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635947] ehci_hcd 0000:00:1d.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.635947] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x203)
Jun 19 19:21:04 teal kernel: [33989.635947] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x300, writing 0x30b)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0xc (was 0x0, writing 0xfe600000)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x8 (was 0x1, writing 0xe001)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x6 (was 0x4, writing 0xfe620004)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x4 (was 0xc, writing 0xc000000c)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Jun 19 19:21:04 teal kernel: [33989.635947] fglrx_pci 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100403)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0xf (was 0x2ff, writing 0x20a)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0x4 (was 0x4, writing 0xfe640004)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Jun 19 19:21:04 teal kernel: [33989.635947] snd_hda_intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x100103)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x8 (was 0x0, writing 0xfe50fe50)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x7 (was 0x20200101, writing 0x202001f1)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
Jun 19 19:21:04 teal kernel: [33989.635947] pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe500000)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0x3 (was 0x0, writing 0xa810)
Jun 19 19:21:04 teal kernel: [33989.635947] ath9k 0000:04:01.0: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00006)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xd000000c)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xd000400c)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x4 (was 0x1, writing 0xd001)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 19 19:21:04 teal kernel: [33989.635947] r8169 0000:05:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfe400004)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100402)
Jun 19 19:21:04 teal kernel: [33989.635947] pcieport 0000:00:1c.5: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635947] xhci_hcd 0000:06:00.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.635947] PM: early resume of devices complete after 2.038 msecs
Jun 19 19:21:04 teal kernel: [33989.635964] i915 0000:00:02.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 19 19:21:04 teal kernel: [33989.635964] mei 0000:00:16.0: irq 52 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:00:1b.0: irq 54 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 19 19:21:04 teal kernel: [33989.635964] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] ahci 0000:00:1f.2: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] fglrx_pci 0000:01:00.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:01:00.1: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] pci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun 19 19:21:04 teal kernel: [33989.635964] pci 0000:03:00.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.635964] snd_hda_intel 0000:01:00.1: irq 55 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.635964] pcieport 0000:00:1c.4: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.635964] r8169 0000:05:00.0: PME# disabled
Jun 19 19:21:04 teal kernel: [33989.639473] xhci_hcd 0000:06:00.0: setting latency timer to 64
Jun 19 19:21:04 teal kernel: [33989.639494] usb usb3: root hub lost power or was reset
Jun 19 19:21:04 teal kernel: [33989.639495] usb usb4: root hub lost power or was reset
Jun 19 19:21:04 teal kernel: [33989.649197] i8042 kbd 00:09: wake-up capability disabled by ACPI
Jun 19 19:21:04 teal kernel: [33989.649474] serial 00:0a: activated
Jun 19 19:21:04 teal kernel: [33989.650136] xhci_hcd 0000:06:00.0: irq 46 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650138] xhci_hcd 0000:06:00.0: irq 47 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650140] xhci_hcd 0000:06:00.0: irq 48 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650142] xhci_hcd 0000:06:00.0: irq 49 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.650143] xhci_hcd 0000:06:00.0: irq 50 for MSI/MSI-X
Jun 19 19:21:04 teal kernel: [33989.653416] [fglrx] Power up the ASIC
Jun 19 19:21:04 teal kernel: [33989.653423] [fglrx] Preparing resume fglrx in kernel.
Jun 19 19:21:04 teal kernel: [33989.657146] sd 0:0:0:0: [sda] Starting disk
Jun 19 19:21:04 teal kernel: [33989.657158] sd 1:0:0:0: [sdb] Starting disk
Jun 19 19:21:04 teal kernel: [33989.657169] sd 2:0:0:0: [sdc] Starting disk
Jun 19 19:21:04 teal kernel: [33989.657176] sd 3:0:0:0: [sdd] Starting disk
Jun 19 19:21:04 teal kernel: [33989.671000] [fglrx] Resuming fglrx in kernel completed.
Jun 19 19:21:04 teal kernel: [33989.671035] [fglrx] IRQ 56 Enabled
Jun 19 19:21:04 teal kernel: [33989.709087] No ACPI video bus found
Jun 19 19:21:04 teal kernel: [33989.776073] PM: resume of drv: dev:ep_00 complete after 118.937 msecs
Jun 19 19:21:04 teal kernel: [33989.776151] PM: resume of drv:hub dev:4-0:1.0 complete after 119.020 msecs
Jun 19 19:21:04 teal kernel: [33989.776186] PM: resume of drv: dev:ep_81 complete after 119.054 msecs
Jun 19 19:21:04 teal kernel: [33989.776781] PM: resume of drv: dev:ep_00 complete after 118.811 msecs
Jun 19 19:21:04 teal kernel: [33989.776806] PM: resume of drv:btusb dev:2-1.1:1.0 complete after 118.992 msecs
Jun 19 19:21:04 teal kernel: [33989.776810] PM: resume of drv:btusb dev:2-1.1:1.1 complete after 118.903 msecs
Jun 19 19:21:04 teal kernel: [33989.776817] PM: resume of drv: dev:ep_83 complete after 118.889 msecs
Jun 19 19:21:04 teal kernel: [33989.776846] PM: resume of drv: dev:ep_03 complete after 118.897 msecs
Jun 19 19:21:04 teal kernel: [33989.776848] PM: resume of drv: dev:ep_82 complete after 118.980 msecs
Jun 19 19:21:04 teal kernel: [33989.776850] PM: resume of drv: dev:ep_02 complete after 118.966 msecs
Jun 19 19:21:04 teal kernel: [33989.776854] PM: resume of drv: dev:ep_81 complete after 119.010 msecs
Jun 19 19:21:04 teal kernel: [33989.777172] PM: resume of drv:hub dev:2-1.4:1.0 complete after 119.161 msecs
Jun 19 19:21:04 teal kernel: [33989.777176] PM: resume of drv: dev:ep_00 complete after 119.119 msecs
Jun 19 19:21:04 teal kernel: [33989.777198] PM: resume of drv: dev:ep_81 complete after 119.166 msecs
Jun 19 19:21:04 teal kernel: [33989.880170] PM: resume of drv: dev:ep_00 complete after 223.063 msecs
Jun 19 19:21:04 teal kernel: [33989.880173] PM: resume of drv:hub dev:3-0:1.0 complete after 223.078 msecs
Jun 19 19:21:04 teal kernel: [33989.880200] PM: resume of drv: dev:ep_81 complete after 223.097 msecs
Jun 19 19:21:04 teal kernel: [33989.976045] ata6: SATA link down (SStatus 0 SControl 300)
Jun 19 19:21:04 teal kernel: [33989.984046] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 19:21:04 teal kernel: [33989.991487] ata5.00: configured for UDMA/100
Jun 19 19:21:04 teal kernel: [33990.048192] usb 3-2: reset high-speed USB device number 3 using xhci_hcd
Jun 19 19:21:04 teal kernel: [33990.068712] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88026dec9400
Jun 19 19:21:04 teal kernel: [33990.173186] PM: resume of drv:hub dev:3-2:1.0 complete after 515.500 msecs
Jun 19 19:21:04 teal kernel: [33990.173189] PM: resume of drv: dev:ep_00 complete after 515.439 msecs
Jun 19 19:21:04 teal kernel: [33990.173216] PM: resume of drv: dev:ep_81 complete after 515.499 msecs
Jun 19 19:21:04 teal kernel: [33990.236200] usb 3-1: reset full-speed USB device number 2 using xhci_hcd
Jun 19 19:21:04 teal kernel: [33990.258222] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88026dec9b80
Jun 19 19:21:04 teal kernel: [33990.258226] xhci_hcd 0000:06:00.0: xHCI xhci_drop_endpoint called with disabled ep ffff88026dec9bc0
Jun 19 19:21:04 teal kernel: [33990.260037] PM: resume of drv:usbhid dev:3-1:1.0 complete after 602.518 msecs
Jun 19 19:21:04 teal kernel: [33990.260043] PM: resume of drv:usbhid dev:3-1:1.1 complete after 602.477 msecs
Jun 19 19:21:04 teal kernel: [33990.260049] PM: resume of drv: dev:ep_00 complete after 602.424 msecs
Jun 19 19:21:04 teal kernel: [33990.260058] PM: resume of drv: dev:ep_82 complete after 602.465 msecs
Jun 19 19:21:04 teal kernel: [33990.260078] PM: resume of drv: dev:ep_81 complete after 602.541 msecs
Jun 19 19:21:04 teal kernel: [33995.032032] ata4: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.040034] ata1: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.048034] ata2: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.056034] ata3: link is slow to respond, please be patient (ready=0)
Jun 19 19:21:04 teal kernel: [33995.320045] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jun 19 19:21:04 teal kernel: [33995.331985] ata1.00: configured for UDMA/133
Jun 19 19:21:04 teal kernel: [33995.377575] PM: resume of drv:sd dev:0:0:0:0 complete after 5720.430 msecs
Jun 19 19:21:04 teal kernel: [33995.377687] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 5720.618 msecs
Jun 19 19:21:04 teal kernel: [33995.377690] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 5720.535 msecs
Jun 19 19:21:04 teal kernel: [33995.384042] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 19:21:04 teal kernel: [33995.402326] ata2.00: configured for UDMA/133
Jun 19 19:21:04 teal kernel: [33995.451568] PM: resume of drv:sd dev:1:0:0:0 complete after 5794.408 msecs
Jun 19 19:21:04 teal kernel: [33995.451682] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 5794.522 msecs
Jun 19 19:21:04 teal kernel: [33995.504039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 19 19:21:04 teal kernel: [33995.506720] ata3.00: configured for UDMA/133
Jun 19 19:21:04 teal kernel: [33995.549126] PM: resume of drv:sd dev:2:0:0:0 complete after 5891.956 msecs
Jun 19 19:21:04 teal kernel: [33995.549236] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 5892.066 msecs
Jun 19 19:21:04 teal kernel: [33996.656042] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 19 19:21:04 teal kernel: [33996.663152] ata4.00: configured for UDMA/100
Jun 19 19:21:04 teal kernel: [33996.695605] PM: resume of drv:sd dev:3:0:0:0 complete after 7038.426 msecs
Jun 19 19:21:04 teal kernel: [33996.695730] PM: resume of drv:scsi_device dev:3:0:0:0 complete after 7038.550 msecs
Jun 19 19:21:04 teal kernel: [33996.695731] PM: resume of drv:scsi_disk dev:3:0:0:0 complete after 1146.471 msecs
Jun 19 19:21:04 teal kernel: [33996.696119] PM: resume of devices complete after 7061.121 msecs
Jun 19 19:21:04 teal kernel: [33996.696165] PM: resume devices took 7.064 seconds
Jun 19 19:21:04 teal kernel: [33996.696186] PM: Finishing wakeup.
Jun 19 19:21:04 teal kernel: [33996.696187] Restarting tasks ... done.
Jun 19 19:21:04 teal rtkit-daemon[1768]: The canary thread is apparently starving. Taking action.
Jun 19 19:21:04 teal rtkit-daemon[1768]: Demoting known real-time threads.
Jun 19 19:21:04 teal rtkit-daemon[1768]: Successfully demoted thread 2056 of process 2028 (n/a).
Jun 19 19:21:04 teal rtkit-daemon[1768]: Successfully demoted thread 2055 of process 2028 (n/a).
Jun 19 19:21:04 teal rtkit-daemon[1768]: Successfully demoted thread 2042 of process 2028 (n/a).
Jun 19 19:21:04 teal rtkit-daemon[1768]: Successfully demoted thread 2028 of process 2028 (n/a).
Jun 19 19:21:04 teal rtkit-daemon[1768]: Demoted 4 threads.
Jun 19 19:21:04 teal anacron[15854]: Anacron 2.3 started on 2012-06-19
Jun 19 19:21:04 teal anacron[15854]: Normal exit (0 jobs run)
Jun 19 19:21:04 teal anacron[16044]: Anacron 2.3 started on 2012-06-19
Jun 19 19:21:04 teal anacron[16044]: Normal exit (0 jobs run)
Jun 19 19:21:04 teal NetworkManager[1014]: <info> wake requested (sleeping: yes  enabled: yes)
Jun 19 19:21:04 teal NetworkManager[1014]: <info> waking up and re-enabling...
Jun 19 19:21:04 teal NetworkManager[1014]: <info> WWAN now enabled by management service
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): now managed
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): bringing up device.
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): preparing device.
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 19 19:21:04 teal NetworkManager[1014]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 19:21:04 teal NetworkManager[1014]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (eth0): now managed
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (eth0): bringing up device.
Jun 19 19:21:04 teal kernel: [33997.470642] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (eth0): preparing device.
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 19 19:21:04 teal kernel: [33997.572969] r8169 0000:05:00.0: eth0: link down
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 19 19:21:04 teal kernel: [33997.573278] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 19 19:21:04 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 19 19:21:04 teal NetworkManager[1014]: <warn> Trying to remove a non-existant call id.
Jun 19 19:21:06 teal kernel: [33998.800625] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 2 with no TDs queued?
Jun 19 19:21:06 teal kernel: [33998.800875] xhci_hcd 0000:06:00.0: WARN Event TRB for slot 1 ep 0 with no TDs queued?
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Auto-activating connection 'ACCESSPOINT'.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'ACCESSPOINT'
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): access point 'ACCESSPOINT' has security, but secrets are required.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): connection 'ACCESSPOINT' has security, and secrets exist.  No new secrets needed.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Config: added 'ssid' value 'ACCESSPOINT'
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Config: added 'scan_ssid' value '1'
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Config: added 'psk' value '<omitted>'
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:21:06 teal NetworkManager[1014]: <info> Config: set interface ap_scan to 1
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 19 19:21:06 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:06 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 19:21:06 teal kernel: [33999.638357] wlan0: authenticate with XX:XX:XX:XX:XX:XX (try 1)
Jun 19 19:21:07 teal kernel: [33999.836023] wlan0: authenticate with XX:XX:XX:XX:XX:XX (try 2)
Jun 19 19:21:07 teal kernel: [34000.036028] wlan0: authenticate with XX:XX:XX:XX:XX:XX (try 3)
Jun 19 19:21:07 teal kernel: [34000.236051] wlan0: authentication with XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:13 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:13 teal kernel: [34006.294393] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:13 teal kernel: [34006.492037] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:14 teal kernel: [34006.692038] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:14 teal kernel: [34006.892050] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:20 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:20 teal kernel: [34012.986329] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:20 teal kernel: [34013.184068] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:20 teal kernel: [34013.384036] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:20 teal kernel: [34013.584067] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:26 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:26 teal kernel: [34019.634396] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:27 teal kernel: [34019.832064] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:27 teal kernel: [34020.032043] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:27 teal kernel: [34020.232066] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:33 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:33 teal kernel: [34026.278473] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:33 teal kernel: [34026.476037] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:34 teal kernel: [34026.676069] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:34 teal kernel: [34026.876034] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:40 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:40 teal kernel: [34032.966335] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:40 teal kernel: [34033.164077] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:40 teal kernel: [34033.364092] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:40 teal kernel: [34033.564030] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:46 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:46 teal kernel: [34039.618421] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:47 teal kernel: [34039.816068] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:47 teal kernel: [34040.016069] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:47 teal kernel: [34040.216069] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:21:53 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:21:53 teal kernel: [34046.270297] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:21:53 teal kernel: [34046.468071] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:21:54 teal kernel: [34046.668067] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:21:54 teal kernel: [34046.868067] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:22:00 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:22:00 teal kernel: [34052.922264] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:22:00 teal kernel: [34053.120035] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:22:00 teal kernel: [34053.320040] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:22:00 teal kernel: [34053.520035] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
Jun 19 19:22:06 teal NetworkManager[1014]: <warn> Activation (wlan0/wireless): association took too long.
Jun 19 19:22:06 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 19 19:22:06 teal NetworkManager[1014]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun 19 19:22:06 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 19 19:22:06 teal NetworkManager[1014]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 19 19:24:06 teal NetworkManager[1014]: <warn> No agents were available for this request.
Jun 19 19:24:06 teal NetworkManager[1014]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jun 19 19:24:06 teal NetworkManager[1014]: <warn> Activation (wlan0) failed for access point (ACCESSPOINT)
Jun 19 19:24:06 teal NetworkManager[1014]: <info> Marking connection 'ACCESSPOINT' invalid.
Jun 19 19:24:06 teal NetworkManager[1014]: <warn> Activation (wlan0) failed.
Jun 19 19:24:06 teal NetworkManager[1014]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 19 19:24:06 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Auto-activating connection 'linksys'.
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'linksys'
Jun 19 19:24:09 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:24:09 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Config: added 'ssid' value 'linksys'
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Config: added 'scan_ssid' value '1'
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Config: added 'bssid' value '00:18:f8:f0:a1:94'
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:24:09 teal NetworkManager[1014]: <info> Config: set interface ap_scan to 1
Jun 19 19:24:09 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 19 19:24:10 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:24:10 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 19:24:10 teal kernel: [34182.663315] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:24:10 teal kernel: [34182.860072] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:24:10 teal kernel: [34183.060064] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:24:10 teal kernel: [34183.260063] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:24:16 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:24:16 teal kernel: [34188.923253] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:24:16 teal kernel: [34189.120037] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:24:16 teal kernel: [34189.320042] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:24:16 teal kernel: [34189.520035] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:24:56 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:24:56 teal kernel: [34229.115049] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:24:56 teal kernel: [34229.312046] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:24:56 teal kernel: [34229.512033] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:24:57 teal kernel: [34229.712237] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:25:09 teal NetworkManager[1014]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 19 19:25:09 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jun 19 19:25:09 teal NetworkManager[1014]: <warn> Activation (wlan0) failed for access point (linksys)
Jun 19 19:25:09 teal NetworkManager[1014]: <warn> Activation (wlan0) failed.
Jun 19 19:25:09 teal NetworkManager[1014]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 19 19:25:09 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 19 19:25:09 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 19 19:25:09 teal NetworkManager[1014]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Auto-activating connection 'linksys'.
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'linksys'
Jun 19 19:25:12 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:25:12 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Config: added 'ssid' value 'linksys'
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Config: added 'scan_ssid' value '1'
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Config: added 'bssid' value '00:18:f8:f0:a1:94'
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:25:12 teal NetworkManager[1014]: <info> Config: set interface ap_scan to 1
Jun 19 19:25:13 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 19 19:25:25 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:25:25 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 19:25:25 teal kernel: [34258.031130] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:25:25 teal kernel: [34258.228051] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:25:25 teal kernel: [34258.428030] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:25:25 teal kernel: [34258.628041] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:25:54 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:25:54 teal kernel: [34286.915332] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:25:54 teal kernel: [34287.112044] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:25:54 teal kernel: [34287.312039] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:25:54 teal kernel: [34287.512038] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:26:12 teal NetworkManager[1014]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 19 19:26:12 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jun 19 19:26:12 teal NetworkManager[1014]: <warn> Activation (wlan0) failed for access point (linksys)
Jun 19 19:26:12 teal NetworkManager[1014]: <warn> Activation (wlan0) failed.
Jun 19 19:26:12 teal NetworkManager[1014]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 19 19:26:12 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 19 19:26:12 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 19 19:26:12 teal NetworkManager[1014]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Auto-activating connection 'linksys'.
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'linksys'
Jun 19 19:26:15 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:26:15 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Config: added 'ssid' value 'linksys'
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Config: added 'scan_ssid' value '1'
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Config: added 'bssid' value '00:18:f8:f0:a1:94'
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:26:15 teal NetworkManager[1014]: <info> Config: set interface ap_scan to 1
Jun 19 19:26:16 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 19 19:26:23 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:26:23 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 19:26:23 teal kernel: [34315.787094] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:26:23 teal kernel: [34315.984055] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:26:23 teal kernel: [34316.184038] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:26:23 teal kernel: [34316.384053] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:26:46 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:26:46 teal kernel: [34339.019158] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:26:46 teal kernel: [34339.216040] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:26:46 teal kernel: [34339.416042] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:26:46 teal kernel: [34339.616044] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:27:15 teal NetworkManager[1014]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 19 19:27:15 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jun 19 19:27:15 teal NetworkManager[1014]: <warn> Activation (wlan0) failed for access point (linksys)
Jun 19 19:27:15 teal NetworkManager[1014]: <warn> Activation (wlan0) failed.
Jun 19 19:27:15 teal NetworkManager[1014]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 19 19:27:15 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 19 19:27:15 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 19 19:27:15 teal NetworkManager[1014]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Auto-activating connection 'linksys'.
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'linksys'
Jun 19 19:27:18 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:27:18 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): connection 'linksys' requires no security.  No secrets needed.
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Config: added 'ssid' value 'linksys'
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Config: added 'scan_ssid' value '1'
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Config: added 'bssid' value '00:18:f8:f0:a1:94'
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Config: added 'key_mgmt' value 'NONE'
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:27:18 teal NetworkManager[1014]: <info> Config: set interface ap_scan to 1
Jun 19 19:27:20 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 19 19:27:20 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:27:20 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 19:27:20 teal kernel: [34373.523200] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:27:21 teal kernel: [34373.720044] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:27:21 teal kernel: [34373.920040] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:27:21 teal kernel: [34374.124038] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:28:17 teal wpa_supplicant[1085]: Trying to authenticate with 00:18:f8:f0:a1:94 (SSID='linksys' freq=2437 MHz)
Jun 19 19:28:17 teal kernel: [34430.643239] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 1/3)
Jun 19 19:28:18 teal kernel: [34430.840038] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 2/3)
Jun 19 19:28:18 teal NetworkManager[1014]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 19 19:28:18 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jun 19 19:28:18 teal NetworkManager[1014]: <warn> Activation (wlan0) failed for access point (linksys)
Jun 19 19:28:18 teal NetworkManager[1014]: <info> Marking connection 'linksys' invalid.
Jun 19 19:28:18 teal NetworkManager[1014]: <warn> Activation (wlan0) failed.
Jun 19 19:28:18 teal NetworkManager[1014]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 19 19:28:18 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 19 19:28:18 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 19 19:28:18 teal NetworkManager[1014]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 19 19:28:18 teal kernel: [34431.040046] wlan0: direct probe to 00:18:f8:f0:a1:94 (try 3/3)
Jun 19 19:28:18 teal kernel: [34431.240040] wlan0: direct probe to 00:18:f8:f0:a1:94 timed out
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Auto-activating connection 'Marett2GHz'.
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'Marett2GHz'
Jun 19 19:28:21 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:28:21 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): access point 'Marett2GHz' has security, but secrets are required.
Jun 19 19:28:21 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 19 19:28:21 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:30:21 teal NetworkManager[1014]: <warn> No agents were available for this request.
Jun 19 19:30:21 teal NetworkManager[1014]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jun 19 19:30:21 teal NetworkManager[1014]: <warn> Activation (wlan0) failed for access point (Marett2GHz)
Jun 19 19:30:21 teal NetworkManager[1014]: <info> Marking connection 'Marett2GHz' invalid.
Jun 19 19:30:21 teal NetworkManager[1014]: <warn> Activation (wlan0) failed.
Jun 19 19:30:21 teal NetworkManager[1014]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun 19 19:30:21 teal NetworkManager[1014]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Auto-activating connection 'ACCESSPOINT'.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) starting connection 'ACCESSPOINT'
Jun 19 19:30:24 teal NetworkManager[1014]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): access point 'ACCESSPOINT' has security, but secrets are required.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 19:30:24 teal NetworkManager[1014]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0/wireless): connection 'ACCESSPOINT' has security, and secrets exist.  No new secrets needed.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Config: added 'ssid' value 'ACCESSPOINT'
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Config: added 'scan_ssid' value '1'
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Config: added 'psk' value '<omitted>'
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 19:30:24 teal NetworkManager[1014]: <info> Config: set interface ap_scan to 1
Jun 19 19:30:24 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 19 19:30:25 teal wpa_supplicant[1085]: Trying to authenticate with XX:XX:XX:XX:XX:XX (SSID='ACCESSPOINT' freq=2462 MHz)
Jun 19 19:30:25 teal NetworkManager[1014]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 19 19:30:25 teal kernel: [34557.686354] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 1/3)
Jun 19 19:30:25 teal kernel: [34557.884065] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 2/3)
Jun 19 19:30:25 teal kernel: [34558.084070] wlan0: direct probe to XX:XX:XX:XX:XX:XX (try 3/3)
Jun 19 19:30:25 teal kernel: [34558.284068] wlan0: direct probe to XX:XX:XX:XX:XX:XX timed out
```

---

### Post by pihbar on 2012-07-05
My situation is similar, but sometimes just restarting the computer fixes things, and I usually only get problems after suspending. I added the line

SUSPEND_MODULES="ath9k ath9k_hw ath9k_common"

into /etc/pm/config.d/modules, but it didn't help much.

---

