---
title: "Ubuntu 10.10 screws my Windows Wireless"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by Under Influence on 2012-03-19
Hi, I have a laptop with intel Wifi link 5100 AGN in dual boot mode with Windows 7 and Ubuntu 10.10. 

My problem is that Ubuntu screwed my wireless on Windows 7, it takes forever to connect to the network in Windows and pages takes lots of time to load but Ubuntu works fine. Sometimes is the opposite, the  Windows 7 wireless works fine and the ubuntu doesn't. 

How do I know? Windows wireless was working fine then installed ubuntu and the wireless on Windows got screwed, then I re installed the Windows and wireless started working fine until I booted the ubuntu.

Note: When Im shutting down the computer in ubuntu 10.10 it gives a FAIL on wireless adapters.

---

### Post by wyliecoyoteuk on 2012-03-19
Sounds like the old "warm boot" firmware error.
Some devices (mainly wifi cards or TV cards) load firmware at boot time, to handle localised settings for different countires.
Unfortunately, some of them only load it at startup from power down ("cold boot"), but not when rebooted ("warm boot").
This can mean that if one OS leaves the firmware in an incompatible state, then the other OS cannot use it.
This means that when you boot Ubuntu, it is OK, then you reboot  into Windows, the wifi doesn't work, and vice versa.
The solution is to shutdown to power off when restarting.

---

### Post by Under Influence on 2012-03-19
I thought of that too, but the problem isn't solved by just shutting down instead of reboot. Its complete random, like I boot the PC in the same Os only, some times wireless works, sometimes it doesn't. I have to boot the PC several times until I can make it work.

---

### Post by wyliecoyoteuk on 2012-03-19
It must be something to do with firmware, as that is the only thing that is shared between the OSes.
In a terminal type:

```

dmesg | grep intel 
```
this should give you some information on what is happening at boot time.

---

### Post by Under Influence on 2012-03-19
main@main-VG:~$ dmesg | grep intel
[    1.223282] intel_idle: MWAIT substates: 0x3122220
[    1.223284] intel_idle: does not run on family 6 model 23

---

### Post by wyliecoyoteuk on 2012-03-19
That sounds like a processor message, not wifi
try:
```

dmesg |grep 5100
```or
```
dmesg |grep wifi
```
or just 
```
dmesg
```
and scroll though manually
(we are searching the dmseg bootup log for info on the wifi card)

---

### Post by Under Influence on 2012-03-19
```
[    0.717745] PCI: max bus depth: 1 pci_try_num: 2
[    0.717812] pci 0000:00:1c.4: BAR 15: assigned [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.717823] pci 0000:00:1c.3: BAR 15: assigned [mem 0xd5500000-0xd56fffff 64bit pref]
[    0.717833] pci 0000:00:1c.1: BAR 15: assigned [mem 0xd5700000-0xd58fffff 64bit pref]
[    0.717844] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd5900000-0xd5afffff 64bit pref]
[    0.717854] pci 0000:00:01.0: BAR 15: assigned [mem 0xd5b00000-0xd5cfffff 64bit pref]
[    0.717859] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.717863] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.717868] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd00fffff]
[    0.717873] pci 0000:00:01.0:   bridge window [mem 0xd5b00000-0xd5cfffff 64bit pref]
[    0.717879] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.717883] pci 0000:00:1c.0:   bridge window [io  0xc000-0xcfff]
[    0.717890] pci 0000:00:1c.0:   bridge window [mem 0xd3d00000-0xd50fffff]
[    0.717896] pci 0000:00:1c.0:   bridge window [mem 0xd5900000-0xd5afffff 64bit pref]
[    0.717905] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.717909] pci 0000:00:1c.1:   bridge window [io  0xb000-0xbfff]
[    0.717916] pci 0000:00:1c.1:   bridge window [mem 0xd2900000-0xd3cfffff]
[    0.717922] pci 0000:00:1c.1:   bridge window [mem 0xd5700000-0xd58fffff 64bit pref]
[    0.717930] pci 0000:00:1c.3: PCI bridge to [bus 06-07]
[    0.717935] pci 0000:00:1c.3:   bridge window [io  0xa000-0xafff]
[    0.717942] pci 0000:00:1c.3:   bridge window [mem 0xd1500000-0xd28fffff]
[    0.717948] pci 0000:00:1c.3:   bridge window [mem 0xd5500000-0xd56fffff 64bit pref]
[    0.717956] pci 0000:00:1c.4: PCI bridge to [bus 08-09]
[    0.717961] pci 0000:00:1c.4:   bridge window [io  0x9000-0x9fff]
[    0.717968] pci 0000:00:1c.4:   bridge window [mem 0xd0100000-0xd14fffff]
[    0.717974] pci 0000:00:1c.4:   bridge window [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.717983] pci 0000:00:1e.0: PCI bridge to [bus 0a-0a]
[    0.717985] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.717992] pci 0000:00:1e.0:   bridge window [mem 0xd5100000-0xd51fffff]
[    0.717998] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.718019] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.718024] pci 0000:00:01.0: setting latency timer to 64
[    0.718037] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.718043] pci 0000:00:1c.0: setting latency timer to 64
[    0.718052] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.718058] pci 0000:00:1c.1: setting latency timer to 64
[    0.718070] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.718076] pci 0000:00:1c.3: setting latency timer to 64
[    0.718084] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.718090] pci 0000:00:1c.4: setting latency timer to 64
[    0.718099] pci 0000:00:1e.0: setting latency timer to 64
[    0.718105] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.718108] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.718112] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.718115] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.718119] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.718122] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.718125] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.718129] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.718132] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.718135] pci_bus 0000:00: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.718139] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.718142] pci_bus 0000:01: resource 1 [mem 0xc0000000-0xd00fffff]
[    0.718146] pci_bus 0000:01: resource 2 [mem 0xd5b00000-0xd5cfffff 64bit pref]
[    0.718149] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.718153] pci_bus 0000:02: resource 1 [mem 0xd3d00000-0xd50fffff]
[    0.718156] pci_bus 0000:02: resource 2 [mem 0xd5900000-0xd5afffff 64bit pref]
[    0.718160] pci_bus 0000:04: resource 0 [io  0xb000-0xbfff]
[    0.718163] pci_bus 0000:04: resource 1 [mem 0xd2900000-0xd3cfffff]
[    0.718166] pci_bus 0000:04: resource 2 [mem 0xd5700000-0xd58fffff 64bit pref]
[    0.718170] pci_bus 0000:06: resource 0 [io  0xa000-0xafff]
[    0.718173] pci_bus 0000:06: resource 1 [mem 0xd1500000-0xd28fffff]
[    0.718177] pci_bus 0000:06: resource 2 [mem 0xd5500000-0xd56fffff 64bit pref]
[    0.718180] pci_bus 0000:08: resource 0 [io  0x9000-0x9fff]
[    0.718183] pci_bus 0000:08: resource 1 [mem 0xd0100000-0xd14fffff]
[    0.718187] pci_bus 0000:08: resource 2 [mem 0xd5300000-0xd54fffff 64bit pref]
[    0.718190] pci_bus 0000:0a: resource 1 [mem 0xd5100000-0xd51fffff]
[    0.718194] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    0.718197] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
[    0.718200] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
[    0.718204] pci_bus 0000:0a: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.718207] pci_bus 0000:0a: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.718210] pci_bus 0000:0a: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.718213] pci_bus 0000:0a: resource 10 [mem 0x000dc000-0x000dffff]
[    0.718217] pci_bus 0000:0a: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.718220] pci_bus 0000:0a: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.718223] pci_bus 0000:0a: resource 13 [mem 0xc0000000-0xfebfffff]
[    0.718269] NET: Registered protocol family 2
[    0.718362] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.718666] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.719133] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.719351] TCP: Hash tables configured (established 131072 bind 65536)
[    0.719354] TCP reno registered
[    0.719357] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.719367] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.719478] NET: Registered protocol family 1
[    0.719870] pci 0000:01:00.0: Boot video device
[    0.719892] PCI: CLS 64 bytes, default 64
[    0.720293] audit: initializing netlink socket (disabled)
[    0.720303] type=2000 audit(1332172538.716:1): initialized
[    0.756490] highmem bounce pool size: 64 pages
[    0.756497] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.771662] VFS: Disk quotas dquot_6.5.2
[    0.771760] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.772740] fuse init (API version 7.16)
[    0.772879] msgmni has been set to 1641
[    0.773355] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.773392] io scheduler noop registered
[    0.773395] io scheduler deadline registered
[    0.773415] io scheduler cfq registered (default)
[    0.773586] pcieport 0000:00:01.0: setting latency timer to 64
[    0.773629] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.773692] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.773745] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.773824] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.773877] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.773957] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.774010] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.774090] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.774143] pcieport 0000:00:1c.4: irq 44 for MSI/MSI-X
[    0.774259] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.774293] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.774391] intel_idle: MWAIT substates: 0x3122220
[    0.774393] intel_idle: does not run on family 6 model 23
[    0.775008] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.775976] ACPI: AC Adapter [ADP1] (off-line)
[    0.776136] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.777709] ACPI: Lid Switch [LID0]
[    0.777767] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.777773] ACPI: Power Button [PWRB]
[    0.777808] ACPI: acpi_idle registered with cpuidle
[    0.779715] Monitor-Mwait will be used to enter C-1 state
[    0.779751] Monitor-Mwait will be used to enter C-2 state
[    0.779784] Monitor-Mwait will be used to enter C-3 state
[    0.779793] Marking TSC unstable due to TSC halts in idle
[    0.798843] thermal LNXTHERM:00: registered as thermal_zone0
[    0.798846] ACPI: Thermal Zone [TZ00] (50 C)
[    0.799480] ACPI: Invalid active0 threshold
[    0.800155] thermal LNXTHERM:01: registered as thermal_zone1
[    0.800159] ACPI: Thermal Zone [TZ01] (50 C)
[    0.800194] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.800218] ERST: Table is not found!
[    0.800289] isapnp: Scanning for PnP cards...
[    0.800307] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.842386] ACPI: Battery Slot [BAT0] (battery present)
[    1.153875] isapnp: No Plug & Play device found
[    1.157984] Linux agpgart interface v0.103
[    1.159934] brd: module loaded
[    1.160764] loop: module loaded
[    1.161434] Fixed MDIO Bus: probed
[    1.161468] PPP generic driver version 2.4.2
[    1.161513] tun: Universal TUN/TAP device driver, 1.6
[    1.161516] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.161632] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.161653] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.161669] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.161674] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.161724] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.161757] ehci_hcd 0000:00:1a.7: debug port 1
[    1.165638] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    1.165662] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xd5204c00
[    1.180018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.180168] hub 1-0:1.0: USB hub found
[    1.180174] hub 1-0:1.0: 6 ports detected
[    1.180282] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.180297] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.180302] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.180346] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.180375] ehci_hcd 0000:00:1d.7: debug port 1
[    1.184254] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.184272] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd5204800
[    1.200017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.200168] hub 2-0:1.0: USB hub found
[    1.200173] hub 2-0:1.0: 6 ports detected
[    1.200275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.200294] uhci_hcd: USB Universal Host Controller Interface driver
[    1.200319] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.200328] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.200333] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.200387] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.200427] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e0e0
[    1.200584] hub 3-0:1.0: USB hub found
[    1.200589] hub 3-0:1.0: 2 ports detected
[    1.200690] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.200698] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.200703] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.200747] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.200786] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e0c0
[    1.200937] hub 4-0:1.0: USB hub found
[    1.200942] hub 4-0:1.0: 2 ports detected
[    1.201029] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.201037] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.201041] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.201085] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.201115] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e0a0
[    1.201273] hub 5-0:1.0: USB hub found
[    1.201278] hub 5-0:1.0: 2 ports detected
[    1.201364] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.201372] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.201376] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.201427] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.201454] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    1.201605] hub 6-0:1.0: USB hub found
[    1.201610] hub 6-0:1.0: 2 ports detected
[    1.201700] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.201708] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.201712] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.201756] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.201784] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    1.201943] hub 7-0:1.0: USB hub found
[    1.201948] hub 7-0:1.0: 2 ports detected
[    1.202043] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.202051] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.202055] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.202101] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.202143] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    1.202298] hub 8-0:1.0: USB hub found
[    1.202303] hub 8-0:1.0: 2 ports detected
[    1.202455] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.207840] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.207848] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.207989] mousedev: PS/2 mouse device common for all mice
[    1.208160] rtc_cmos 00:06: RTC can wake from S4
[    1.208282] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.208311] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.208411] device-mapper: uevent: version 1.0.3
[    1.208526] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.208569] EISA: Probing bus 0 at eisa.0
[    1.208572] EISA: Cannot allocate resource for mainboard
[    1.208575] Cannot allocate resource for EISA slot 1
[    1.208578] Cannot allocate resource for EISA slot 2
[    1.208580] Cannot allocate resource for EISA slot 3
[    1.208583] Cannot allocate resource for EISA slot 4
[    1.208585] Cannot allocate resource for EISA slot 5
[    1.208588] Cannot allocate resource for EISA slot 6
[    1.208590] Cannot allocate resource for EISA slot 7
[    1.208593] Cannot allocate resource for EISA slot 8
[    1.208595] EISA: Detected 0 cards.
[    1.208607] cpufreq-nforce2: No nForce2 chipset.
[    1.208688] cpuidle: using governor ladder
[    1.208822] cpuidle: using governor menu
[    1.208825] EFI Variables Facility v0.08 2004-May-17
[    1.209226] TCP cubic registered
[    1.209415] NET: Registered protocol family 10
[    1.210234] NET: Registered protocol family 17
[    1.210253] Registering the dns_resolver key type
[    1.210283] Using IPI No-Shortcut mode
[    1.210383] PM: Hibernation image not present or could not be loaded.
[    1.210403] registered taskstats version 1
[    1.225836]   Magic number: 4:889:942
[    1.225929] rtc_cmos 00:06: setting system clock to 2012-03-19 15:55:39 UTC (1332172539)
[    1.227592] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.227595] EDD information not available.
[    1.227865] Freeing unused kernel memory: 720k freed
[    1.228178] Write protecting the kernel text: 5528k
[    1.228314] Write protecting the kernel read-only data: 2240k
[    1.228317] NX-protecting the kernel data: 4712k
[    1.229955] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.251074] udevd[86]: starting version 173
[    1.319379] sky2: driver version 1.28
[    1.319425] sky2 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.319440] sky2 0000:08:00.0: setting latency timer to 64
[    1.319478] sky2 0000:08:00.0: Yukon-2 EC Ultra chip revision 3
[    1.319756] sky2 0000:08:00.0: irq 45 for MSI/MSI-X
[    1.321356] sky2 0000:08:00.0: eth0: addr 00:1d:ba:ef:ae:b3
[    1.350528] ahci 0000:00:1f.2: version 3.0
[    1.350547] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.350613] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.350688] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.350693] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.350699] ahci 0000:00:1f.2: setting latency timer to 64
[    1.364089] scsi0 : ahci
[    1.364109] firewire_ohci 0000:0a:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.367111] scsi1 : ahci
[    1.368840] sdhci: Secure Digital Host Controller Interface driver
[    1.368843] sdhci: Copyright(c) Pierre Ossman
[    1.369149] scsi2 : ahci
[    1.369474] scsi3 : ahci
[    1.369617] ata1: SATA max UDMA/133 abar m2048@0xd5204000 port 0xd5204100 irq 46
[    1.369622] ata2: SATA max UDMA/133 abar m2048@0xd5204000 port 0xd5204180 irq 46
[    1.369625] ata3: DUMMY
[    1.369627] ata4: DUMMY
[    1.428127] firewire_ohci: Added fw-ohci device 0000:0a:03.0, OHCI v1.0, 4 IR + 4 IT contexts, quirks 0x1
[    1.428216] sdhci-pci 0000:0a:03.1: SDHCI controller found [1180:0822] (rev 22)
[    1.428233] sdhci-pci 0000:0a:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.428267] sdhci-pci 0000:0a:03.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.428294] mmc0: no vmmc regulator found
[    1.428332] Registered led device: mmc0::
[    1.428374] mmc0: SDHCI controller on PCI [0000:0a:03.1] using DMA
[    1.492076] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.692084] ata2: SATA link down (SStatus 0 SControl 300)
[    1.692117] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.703234] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.703966] ata1.00: ATA-8: Corsair Force 3 SSD, 1.3.3, max UDMA/133
[    1.703970] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.713191] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.713196] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.713834] ata1.00: configured for UDMA/133
[    1.714034] scsi 0:0:0:0: Direct-Access     ATA      Corsair Force 3  1.3. PQ: 0 ANSI: 5
[    1.714236] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.714256] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.714418] sd 0:0:0:0: [sda] Write Protect is off
[    1.714423] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.714450] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.715357]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.715832] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.766414] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.928143] firewire_core: created device fw0: GUID 0800460302f9fa15, S400
[    2.009986] udevd[307]: starting version 173
[    2.036073] usb 6-2: new low speed USB device number 2 using uhci_hcd
[    2.042533] lp: driver loaded but no devices found
[    2.444046] usb 8-1: new full speed USB device number 2 using uhci_hcd
[    3.450188] Adding 3905532k swap on /dev/sda5.  Priority:-1 extents:1 across:3905532k SS
[    3.463904] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
[    3.483835] type=1400 audit(1332172541.753:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=468 comm="apparmor_parser"
[    3.484501] type=1400 audit(1332172541.757:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=468 comm="apparmor_parser"
[    3.484869] type=1400 audit(1332172541.757:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=468 comm="apparmor_parser"
[    3.546379] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    3.605282] Bluetooth: Core ver 2.16
[    3.606524] NET: Registered protocol family 31
[    3.606526] Bluetooth: HCI device and connection manager initialized
[    3.606529] Bluetooth: HCI socket layer initialized
[    3.606531] Bluetooth: L2CAP socket layer initialized
[    3.607793] sony_laptop: Sony Notebook Control Driver v0.6
[    3.613223] r592 0000:0a:03.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.613782] Linux video capture interface: v2.00
[    3.617416] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183d)
[    3.623761] Bluetooth: SCO socket layer initialized
[    3.627259] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    3.636285] r592: driver successfully loaded
[    3.655353] usbcore: registered new interface driver btusb
[    3.712028] cfg80211: Calling CRDA to update world regulatory domain
[    3.718524] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    3.718530] Disabling lock debugging due to kernel taint
[    3.756613] type=1400 audit(1332172542.029:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=683 comm="apparmor_parser"
[    3.766733] type=1400 audit(1332172542.037:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=684 comm="apparmor_parser"
[    3.769804] input: UVC Camera (05ca:183d) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input3
[    3.770014] usbcore: registered new interface driver uvcvideo
[    3.770017] USB Video Class driver (v1.1.0)
[    3.772568] type=1400 audit(1332172542.045:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=684 comm="apparmor_parser"
[    3.772941] type=1400 audit(1332172542.045:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=684 comm="apparmor_parser"
[    3.787095] type=1400 audit(1332172542.057:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=700 comm="apparmor_parser"
[    3.806384] type=1400 audit(1332172542.077:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=700 comm="apparmor_parser"
[    3.818665] acpi device:14: registered as cooling_device2
[    3.919645] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input4
[    3.963469] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.963473] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    3.963554] iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.963563] iwlagn 0000:06:00.0: setting latency timer to 64
[    3.963597] iwlagn 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    3.985571] iwlagn 0000:06:00.0: device EEPROM VER=0x11f, CALIB=0x4
[    3.985575] iwlagn 0000:06:00.0: Device SKU: 0Xb
[    4.004638] generic-usb 0003:04F3:0212.0001: input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1d.0-2/input0
[    4.007454] usbcore: registered new interface driver usbhid
[    4.007458] usbhid: USB HID core driver
[    4.017511] cfg80211: World regulatory domain updated:
[    4.017515] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.017520] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.017523] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.017527] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    4.017530] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.017534] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    4.039877] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    4.039970] iwlagn 0000:06:00.0: irq 47 for MSI/MSI-X
[    4.041060] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/LNXVIDEO:00/input/input5
[    4.041245] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    4.185246] iwlagn 0000:06:00.0: loaded firmware version 8.83.5.1 build 33692
[    4.185500] Registered led device: phy0-led
[    4.185537] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    4.213360] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.227269] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
[    4.249299] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
[    4.256626] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/SNY5001:00/input/input8
[    4.257401] input: Sony Vaio Jogdial as /devices/virtual/input/input9
[    4.257567] sony_laptop: brightness ignored, must be controlled by ACPI video driver
[    4.351401] init: failsafe main process (620) killed by TERM signal
[    4.355246] init: apport pre-start process (827) terminated with status 1
[    4.355847] init: alsa-restore main process (836) terminated with status 19
[    4.396021] init: apport post-stop process (860) terminated with status 1
[    4.519950] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.520177] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    4.520211] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    4.520898] [fglrx] Maximum main memory to use for locked dma buffers: 3829 MBytes.
[    4.521652] [fglrx]   vendor: 1002 device: 9480 count: 1
[    4.522740] [fglrx] ioport: bar 1, base 0xd000, size: 0x100
[    4.522755] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.522761] pci 0000:01:00.0: setting latency timer to 64
[    4.523170] [fglrx] Kernel PAT support is enabled
[    4.523195] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[    4.592529] hda_codec: ALC262: SKU not ready 0x411111f0
[    4.627536] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.627761] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.628415] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.628511] HDA Intel 0000:01:00.1: irq 49 for MSI/MSI-X
[    4.628545] HDA Intel 0000:01:00.1: setting latency timer to 64
[    4.632890] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.644165] sky2 0000:08:00.0: eth0: enabling interface
[    4.644532] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.652492] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[    4.653034] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    4.704034] Bluetooth: RFCOMM TTY layer initialized
[    4.704041] Bluetooth: RFCOMM socket layer initialized
[    4.704043] Bluetooth: RFCOMM ver 1.11
[    4.716446] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.716450] Bluetooth: BNEP filters: protocol multicast
[    4.869087] init: udev-fallback-graphics main process (1025) terminated with status 1
[    4.878122] ppdev: user-space parallel port driver
[    4.946843] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[    5.457753] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[    5.458750] [fglrx] Firegl kernel thread PID: 1143
[    5.458856] [fglrx] Firegl kernel thread PID: 1144
[    5.458967] [fglrx] Firegl kernel thread PID: 1145
[    5.459190] [fglrx] IRQ 50 Enabled
[    5.676669] [fglrx] Gart USWC size:1248 M.
[    5.676674] [fglrx] Gart cacheable size:495 M.
[    5.676681] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[    5.676685] [fglrx] Reserved FB block: Unshared offset:fc17000, size:3e9000 
[    5.676688] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[    7.539596] init: plymouth-upstart-bridge main process (662) killed by TERM signal
[    8.324702] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=600
[   12.279915] wlan0: authenticate with 00:0e:84:b8:a2:90 (try 1)
[   12.281897] wlan0: authenticated
[   12.285991] wlan0: associate with 00:0e:84:b8:a2:90 (try 1)
[   12.287751] wlan0: RX AssocResp from 00:0e:84:b8:a2:90 (capab=0x431 status=0 aid=198)
[   12.287756] wlan0: associated
[   12.291138] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   22.560036] wlan0: no IPv6 routers present
```

---

### Post by wyliecoyoteuk on 2012-03-19
```
dmesg |grep iwlagn
```
should give you all the info on the wifi card

iwlagn 0000:06:00.0: loaded firmware version 8.83.5.1 build 33692

tells you what firmware is being loaded.
Maybe this conflicts with the Windows version somehow, there may be a newer or older version loaded by windows.
the firmware in windows is usually part of the driver installation package.
If you find that and copy it, so that both OSes have the same firmware, it might fix things.

---

### Post by Under Influence on 2012-03-19
```
dmesg |grep iwlagn

main@main-VG:~$ dmesg |grep iwlagn
[    3.627299] 
iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.627303]
iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    3.627360] 
iwlagn 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.627368] 
iwlagn 0000:06:00.0: setting latency timer to 64
[    3.627393] 
iwlagn 0000:06:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    3.649284] 
iwlagn 0000:06:00.0: device EEPROM VER=0x11f, CALIB=0x4
[    3.649286] 
iwlagn 0000:06:00.0: Device SKU: 0Xb
[    3.660164] 
iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    3.660236] 
iwlagn 0000:06:00.0: irq 47 for MSI/MSI-X
[    4.042303] iwlagn 0000:06:00.0: loaded firmware version 8.83.5.1 build 33692
main@main-VG:~$ 




```

how do i know the firmware version of windows and how do i match both versions ?

---

### Post by wyliecoyoteuk on 2012-03-19
I would download the latest driver and extract it, then look at the filenames, the firmware is often a .fw file.
A look at the Intel website shows that there is a Linux driver, which includes the firmware.
Sorry, but I don't have access to Windows at home (or your hardware), I can't really help with that.

---

### Post by wyliecoyoteuk on 2012-03-19
In Ubuntu, firmware is kept in  /lib/firmware
Firmware files are the usually same for Windows and Linux, so they can be copied across

---

