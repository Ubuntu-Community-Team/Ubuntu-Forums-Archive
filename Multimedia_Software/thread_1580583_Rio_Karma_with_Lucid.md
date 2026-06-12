---
title: "Rio Karma with Lucid"
date: 2010-09-23
forum: Multimedia Software
---

### Post by whitemagicwoman on 2010-09-23
Hi folks, 

I am hoping to get USB access set up to my Rio Karma.  I am running Lucid Lynx 10.04 dual-booted with Windows Vista on my main computer.

I found a page here: 
[http://ubuntuforums.org/showthread.php?t=87225&page=2](http://ubuntuforums.org/showthread.php?t=87225&page=2)

which then took me here:

[http://linux-karma.sourceforge.net/Karma-HOWTO.html](http://linux-karma.sourceforge.net/Karma-HOWTO.html)

Currently when I plug in the device, it says "communicating" but I don't see it anywhere obvious, like in the Places list.

When I run "dmesg" I get:

```
0x2a00002, writing 0x2a00013)
[ 6438.556116] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[ 6438.556386] fglrx_pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100403)
[ 6438.556414] HDA Intel 0000:01:05.1: restoring config space at offset 0xf (was 0x2ff, writing 0x207)
[ 6438.556426] HDA Intel 0000:01:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xd2410000)
[ 6438.556432] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[ 6438.556485] sdhci-pci 0000:08:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
[ 6438.556665] jmb38x_ms 0000:08:00.3: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
[ 6438.556850] wl 0000:09:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 6438.556957] r8169 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 6438.557427] PM: early resume of devices complete after 33.205 msecs
[ 6439.011679] PM: resume of drv:battery dev:PNP0C0A:00 complete after 443.448 msecs
[ 6439.047529] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 6439.047681] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6439.068071] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6439.092071] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 6439.092087] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6439.116071] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6439.140071] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 6439.141099] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 6439.141181] fglrx_pci 0000:01:05.0: power state changed by ACPI to D0
[ 6439.141190] fglrx_pci 0000:01:05.0: power state changed by ACPI to D0
[ 6439.141196] fglrx_pci 0000:01:05.0: setting latency timer to 64
[ 6439.144630] [fglrx] Power up the ASIC
[ 6439.144660] [fglrx] Preparing resume fglrx in kernel.
[ 6439.178828] [fglrx] Resuming fglrx in kernel completed.
[ 6439.179064] [fglrx] IRQ 30 Enabled
[ 6439.179146] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 6439.179153] HDA Intel 0000:01:05.1: setting latency timer to 64
[ 6439.179184] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 6439.179195] sdhci-pci 0000:08:00.0: setting latency timer to 64
[ 6439.179220] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 6439.179226] jmb38x_ms 0000:08:00.3: setting latency timer to 64
[ 6439.179251] wl 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 6439.179257] wl 0000:09:00.0: setting latency timer to 64
[ 6439.194961] r8169 0000:0a:00.0: PME# disabled
[ 6439.364085] ata5: SATA link down (SStatus 0 SControl 300)
[ 6439.440070] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[ 6439.528067] ata4: softreset failed (device not ready)
[ 6439.528070] ata4: applying SB600 PMP SRST workaround and retrying
[ 6439.597213] PM: resume of drv:usb dev:1-6 complete after 340.018 msecs
[ 6439.597275] sd 2:0:0:0: [sda] Starting disk
[ 6439.692076] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6439.765103] ata4.00: configured for UDMA/100
[ 6439.920066] ata3: softreset failed (device not ready)
[ 6439.920069] ata3: applying SB600 PMP SRST workaround and retrying
[ 6440.084075] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 6440.085380] ata3.00: configured for UDMA/100
[ 6440.116347] PM: resume of drv:sd dev:2:0:0:0 complete after 519.072 msecs
[ 6440.116773] PM: resume of devices complete after 1559.312 msecs
[ 6440.116974] PM: resume devices took 1.560 seconds
[ 6440.117004] PM: Finishing wakeup.
[ 6440.117006] Restarting tasks ... done.
[ 6441.032108] r8169: eth0: link down
[ 6441.034069] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6441.583141] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input13
[ 6441.630731] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input14
[ 6441.770331] CPU0 attaching NULL sched-domain.
[ 6441.770339] CPU1 attaching NULL sched-domain.
[ 6441.824371] CPU0 attaching sched-domain:
[ 6441.824385]  domain 0: span 0-1 level MC
[ 6441.824397]   groups: 0 1
[ 6441.824417] CPU1 attaching sched-domain:
[ 6441.824426]  domain 0: span 0-1 level MC
[ 6441.824436]   groups: 1 0
[ 6451.400595] eth1: no IPv6 routers present
[14470.638833] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[14470.638837] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[14470.650687] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[14470.650692] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[14470.842449] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[14470.842454] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[14470.854444] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[14470.854448] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[14470.928365] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[14470.928370] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[14470.940591] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[14470.940596] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[15580.277224] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[15580.277232] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[15580.289987] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[15580.289992] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19062.499329] CPU0 attaching NULL sched-domain.
[19062.499336] CPU1 attaching NULL sched-domain.
[19062.520189] CPU0 attaching sched-domain:
[19062.520198]  domain 0: span 0-1 level MC
[19062.520206]   groups: 0 1
[19062.520220] CPU1 attaching sched-domain:
[19062.520225]  domain 0: span 0-1 level MC
[19062.520230]   groups: 1 0
[19064.820835] PM: Syncing filesystems ... done.
[19064.864544] PM: Preparing system for mem sleep
[19064.864550] Freezing user space processes ... (elapsed 0.00 seconds) done.
[19064.865968] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[19064.866078] PM: Entering mem sleep
[19064.866098] Suspending console(s) (use no_console_suspend to debug)
[19064.866671] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[19064.866922] sd 2:0:0:0: [sda] Stopping disk
[19065.850543] PM: suspend of drv:sd dev:2:0:0:0 complete after 983.866 msecs
[19066.290083] PM: suspend of drv:psmouse dev:serio1 complete after 425.939 msecs
[19066.392049] PM: suspend of drv:atkbd dev:serio0 complete after 101.959 msecs
[19066.398391] wl 0000:09:00.0: PCI INT A disabled
[19066.412132] jmb38x_ms 0000:08:00.3: PCI INT A disabled
[19066.428135] sdhci-pci 0000:08:00.0: PCI INT A disabled
[19066.444068] HDA Intel 0000:01:05.1: PCI INT B disabled
[19066.444091] ACPI handle has no context!
[19066.460185] [fglrx] IRQ 30 Disabled
[19066.460224] [fglrx] Preparing suspend fglrx in kernel.
[19066.491429] [fglrx] Suspending fglrx in kernel completed.
[19066.491434] [fglrx] Power down the ASIC .
[19066.596257] HDA Intel 0000:00:14.2: PCI INT A disabled
[19066.596300] ACPI handle has no context!
[19066.612057] PM: suspend of drv:HDA Intel dev:0000:00:14.2 complete after 120.509 msecs
[19066.612173] ehci_hcd 0000:00:13.2: PCI INT B disabled
[19066.612184] ohci_hcd 0000:00:13.1: PCI INT A disabled
[19066.612194] ohci_hcd 0000:00:13.0: PCI INT A disabled
[19066.612204] ehci_hcd 0000:00:12.2: PCI INT B disabled
[19066.612214] ohci_hcd 0000:00:12.1: PCI INT A disabled
[19066.612224] ohci_hcd 0000:00:12.0: PCI INT A disabled
[19066.660192] ahci 0000:00:11.0: PCI INT A disabled
[19066.676997] PM: suspend of devices complete after 1810.553 msecs
[19066.677000] PM: suspend devices took 1.812 seconds
[19066.677481] r8169 0000:0a:00.0: PME# enabled
[19066.724394] PM: late suspend of devices complete after 47.386 msecs
[19066.724473] ACPI: Preparing to enter system sleep state S3
[19066.740050] Disabling non-boot CPUs ...
[19066.740078] CPU0 attaching NULL sched-domain.
[19066.740082] CPU1 attaching NULL sched-domain.
[19066.804053] CPU0 attaching NULL sched-domain.
[19066.805305] Breaking affinity for irq 9
[19066.805313] Breaking affinity for irq 12
[19066.908052] CPU 1 is now offline
[19066.908055] SMP alternatives: switching to UP code
[19066.912984] Back to C!
[19066.912984] Enabling non-boot CPUs ...
[19066.912984] SMP alternatives: switching to SMP code
[19066.917748] Booting processor 1 APIC 0x1 ip 0x6000
[19066.912460] Initializing CPU#1
[19066.932798] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[19066.932798] CPU: L2 Cache: 512K (64 bytes/line)
[19066.932798] CPU: Physical Processor ID: 0
[19066.932798] CPU: Processor Core ID: 1
[19067.008141] CPU1: AMD Turion(tm) X2 Dual-Core Mobile RM-72 stepping 01
[19067.008288] CPU0 attaching NULL sched-domain.
[19067.036077] CPU0 attaching sched-domain:
[19067.036080]  domain 0: span 0-1 level MC
[19067.036083]   groups: 0 1
[19067.036087] CPU1 attaching sched-domain:
[19067.036089]  domain 0: span 0-1 level MC
[19067.036092]   groups: 1 0
[19067.037067] CPU1 is up
[19067.037268] ACPI: Waking up from system sleep state S3
[19067.056437] pcieport 0000:00:04.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[19067.056523] pcieport 0000:00:05.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[19067.056566] pcieport 0000:00:06.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[19067.056650] pcieport 0000:00:07.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[19067.056703] ahci 0000:00:11.0: restoring config space at offset 0x1 (was 0x2300003, writing 0x2300007)
[19067.056743] ohci_hcd 0000:00:12.0: restoring config space at offset 0x1 (was 0x2a00002, writing 0x2a00013)
[19067.072105] ehci_hcd 0000:00:12.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[19067.072146] ohci_hcd 0000:00:13.0: restoring config space at offset 0x1 (was 0x2a00002, writing 0x2a00013)
[19067.088101] ehci_hcd 0000:00:13.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00013)
[19067.088370] fglrx_pci 0000:01:05.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100403)
[19067.088398] HDA Intel 0000:01:05.1: restoring config space at offset 0xf (was 0x2ff, writing 0x207)
[19067.088410] HDA Intel 0000:01:05.1: restoring config space at offset 0x4 (was 0x0, writing 0xd2410000)
[19067.088416] HDA Intel 0000:01:05.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[19067.088468] sdhci-pci 0000:08:00.0: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
[19067.088648] jmb38x_ms 0000:08:00.3: restoring config space at offset 0x1 (was 0x100003, writing 0x100007)
[19067.088834] wl 0000:09:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[19067.088936] r8169 0000:0a:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[19067.089412] PM: early resume of devices complete after 33.185 msecs
[19067.539534] PM: resume of drv:battery dev:PNP0C0A:00 complete after 439.303 msecs
[19067.571293] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[19067.571450] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[19067.592072] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[19067.616072] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[19067.616089] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[19067.640068] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[19067.664072] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19067.665110] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[19067.665192] fglrx_pci 0000:01:05.0: power state changed by ACPI to D0
[19067.665201] fglrx_pci 0000:01:05.0: power state changed by ACPI to D0
[19067.665207] fglrx_pci 0000:01:05.0: setting latency timer to 64
[19067.668630] [fglrx] Power up the ASIC
[19067.668660] [fglrx] Preparing resume fglrx in kernel.
[19067.702741] [fglrx] Resuming fglrx in kernel completed.
[19067.702970] [fglrx] IRQ 30 Enabled
[19067.703026] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[19067.703033] HDA Intel 0000:01:05.1: setting latency timer to 64
[19067.703066] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[19067.703078] sdhci-pci 0000:08:00.0: setting latency timer to 64
[19067.703103] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[19067.703109] jmb38x_ms 0000:08:00.3: setting latency timer to 64
[19067.703135] wl 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[19067.703142] wl 0000:09:00.0: setting latency timer to 64
[19067.718760] r8169 0000:0a:00.0: PME# disabled
[19067.888110] ata5: SATA link down (SStatus 0 SControl 300)
[19067.960072] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[19068.052069] ata4: softreset failed (device not ready)
[19068.052072] ata4: applying SB600 PMP SRST workaround and retrying
[19068.116872] PM: resume of drv:usb dev:1-6 complete after 334.921 msecs
[19068.116934] sd 2:0:0:0: [sda] Starting disk
[19068.216077] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[19068.273127] ata4.00: configured for UDMA/100
[19068.444065] ata3: softreset failed (device not ready)
[19068.444068] ata3: applying SB600 PMP SRST workaround and retrying
[19068.608075] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[19068.609380] ata3.00: configured for UDMA/100
[19068.641248] PM: resume of drv:sd dev:2:0:0:0 complete after 524.314 msecs
[19068.641675] PM: resume of devices complete after 1552.228 msecs
[19068.641880] PM: resume devices took 1.552 seconds
[19068.641908] PM: Finishing wakeup.
[19068.641910] Restarting tasks ... done.
[19068.954389] r8169: eth0: link down
[19068.954624] ADDRCONF(NETDEV_UP): eth0: link is not ready
[19069.642400] CPU0 attaching NULL sched-domain.
[19069.642407] CPU1 attaching NULL sched-domain.
[19069.673565] CPU0 attaching sched-domain:
[19069.673570]  domain 0: span 0-1 level MC
[19069.673574]   groups: 0 1
[19069.673580] CPU1 attaching sched-domain:
[19069.673583]  domain 0: span 0-1 level MC
[19069.673623]   groups: 1 0
[19070.128557] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input15
[19070.176622] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input16
[19079.720065] eth1: no IPv6 routers present
[19426.972858] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19426.972862] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19426.982180] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19426.982184] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19440.818743] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19440.818752] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19440.830579] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19440.830584] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19441.079448] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19441.079453] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19441.088848] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19441.088853] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19441.565097] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19441.565101] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19441.577270] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19441.577275] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19700.032664] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19700.032668] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19700.041910] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19700.041915] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19700.329665] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19700.329674] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19700.341300] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19700.341308] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19722.681313] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19722.681317] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19722.691590] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19722.691594] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19723.035445] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19723.035449] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19723.047330] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19723.047335] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19723.123992] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[19723.123997] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[19723.131622] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[19723.131627] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[26810.338263] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[26810.338268] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[26810.347769] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[26810.347774] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[26810.414961] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[26810.414965] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[26810.426792] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[26810.426797] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[26810.531468] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[26810.531473] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[26810.539187] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[26810.539191] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[27486.655068] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[27486.655073] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[27486.667097] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[27486.667101] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[27486.865402] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[27486.865406] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[27486.877370] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[27486.877375] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[27487.018535] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[27487.018540] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[27487.030209] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[27487.030214] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29078.474626] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29078.474631] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29078.486867] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29078.486872] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29078.675745] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29078.675750] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29078.687599] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29078.687604] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.170963] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29247.170968] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.183036] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29247.183041] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.312045] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29247.312050] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.324252] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29247.324257] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.400337] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29247.400342] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.412960] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29247.412964] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.512964] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29247.512973] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29247.525280] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29247.525288] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29897.312540] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29897.312544] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29897.324419] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29897.324424] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29897.446215] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29897.446220] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29897.455389] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29897.455393] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29897.599542] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29897.599550] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29897.608860] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29897.608864] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29954.329696] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29954.329700] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29954.337357] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29954.337361] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29954.457370] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29954.457374] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29954.469255] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29954.469259] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29954.538538] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[29954.538543] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[29954.550202] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[29954.550207] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32033.784106] TCP: Peer 212.54.220.125:16428/33121 unexpectedly shrunk window 1592622660:1592629860 (repaired)
[32215.179039] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[32215.179043] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32215.191076] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[32215.191080] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32215.267503] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[32215.267508] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32215.279780] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[32215.279785] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32215.389741] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[32215.389745] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32215.401569] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[32215.401574] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32220.852920] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[32220.852925] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[32220.864680] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[32220.864684] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[33110.223231] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
[33110.223236] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[33110.234876] atkbd.c: Unknown key released (translated set 2, code 0x94 on isa0060/serio0).
[33110.234880] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
[38903.352206] usb 1-1: new high speed USB device using ehci_hcd and address 3
[38903.572375] usb 1-1: configuration #1 chosen from 1 choice
[38903.749272] Initializing USB Mass Storage driver...
[38903.749493] scsi8 : SCSI emulation for USB Mass Storage devices
[38903.749686] usbcore: registered new interface driver usb-storage
[38903.749689] USB Mass Storage support registered.
[38903.756684] usb-storage: device found at 3
[38903.756688] usb-storage: waiting for device to settle before scanning
[38908.756702] usb-storage: device scan complete
[38908.758315] scsi 8:0:0:0: Direct-Access     Generic  Flash Disk       8.07 PQ: 0 ANSI: 2
[38908.765889] sd 8:0:0:0: Attached scsi generic sg2 type 0
[38908.768790] sd 8:0:0:0: [sdb] 7780352 512-byte logical blocks: (3.98 GB/3.70 GiB)
[38908.769341] sd 8:0:0:0: [sdb] Write Protect is off
[38908.769355] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[38908.769366] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[38908.772698] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[38908.772712]  sdb:
[38909.054722] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[38909.054736] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[38920.297575] usb 1-1: USB disconnect, address 3
[39505.484154] hub 3-0:1.0: unable to enumerate USB device on port 1
[39512.384129] usb 1-1: new high speed USB device using ehci_hcd and address 5
[39512.520783] usb 1-1: configuration #1 chosen from 1 choice
[39514.161668] scsi9 : SCSI emulation for USB Mass Storage devices
[39514.162048] usb-storage: device found at 5
[39514.162052] usb-storage: waiting for device to settle before scanning
[39514.162122] usbcore: registered new interface driver ums-karma
[39519.164173] usb-storage: device scan complete
[39519.167190] scsi 9:0:0:0: Direct-Access     HITACHI_ DK14FA-20             PQ: 0 ANSI: 0
[39519.172846] sd 9:0:0:0: Attached scsi generic sg2 type 0
[39519.182578] sd 9:0:0:0: [sdb] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[39519.183421] sd 9:0:0:0: [sdb] Write Protect is off
[39519.183425] sd 9:0:0:0: [sdb] Mode Sense: 33 00 00 00
[39519.183428] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[39519.185297] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[39519.185302]  sdb: sdb1 sdb2
[39519.294842] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[39519.294866] sd 9:0:0:0: [sdb] Attached SCSI disk
```I checked the kernel, I have a current enough version.  I ran make modules and depmod and mounted the device.  I installed the libkarma packages.  I downloaded Banshee.  I'm just not sure what to do next.  I'd appreciate any help you can give me.

---

### Post by ajgreeny on 2010-09-23
I assume from your dmesg output that sdb1 and sdb2 are the partitions on the karma.  You say you have mounted it but don't say if it can be navigated to in nautilus, just that it does not show in Places, which I agree is where you would expect to see it.

Does it mount in /media, or /mnt or somewhere else, and do you have to mount it manually or is it automounted?  If the letter it would be in /media, I think, so this is a bit strange.

Finally are you trying to play music which is on the player on your computer with rhythmbox or banshee, or do you just want to copy files to it or from  it?

---

### Post by whitemagicwoman on 2010-09-23
> I assume from your dmesg output that sdb1 and sdb2 are the partitions on  the karma.  You say you have mounted it but don't say if it can be  navigated to in nautilus, just that it does not show in Places, which I  agree is where you would expect to see it.

Does it mount in /media, or /mnt or somewhere else, and do you have to  mount it manually or is it automounted?  If the letter it would be in  /media, I think, so this is a bit strange.

Finally are you trying to play music which is on the player on your  computer with rhythmbox or banshee, or do you just want to copy files to  it or from  it?     Really good questions, aj.  I do not see the drive in Nautilus.    

As for mounting it, I used this command, which I got from the website linked above:
```
# mount -t omfs /dev/sda2 /mnt/karma
```So I guess it mounts in /mnt.

And finally, I just want to copy files to and from the device.  I can do it
using Windows XP on my other computer but that feels sort of like a long 
process, I normally don't even boot on that side unless I'm having trouble.

---

### Post by ajgreeny on 2010-09-24
Change your command's mountpoint to /media/karma and it should appear in Places.  However, you should be able to navigate to it in /mnt/karma as well.

As it is formatted as omfs, I suspect that may be why it does not automount, but without a search I know nothing more about omfs, I'm afraid.

EDIT:
It looks as if the supported versions of ubuntu should be able to deal with the omfs file system, using the mount command you used, but I suggest you use /media, not /mnt.

Have a look at [http://bobcopeland.com/karma/](http://bobcopeland.com/karma/) for info on the USB mass storage activation that may be needed.

---

