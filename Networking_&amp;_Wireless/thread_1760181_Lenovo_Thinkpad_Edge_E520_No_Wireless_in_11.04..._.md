---
title: "Lenovo Thinkpad Edge E520 No Wireless in 11.04... (I am a newb)"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by awfullook on 2011-05-16
Hello all, just got my E520 today and am trying to scrap W7 asap, am running live 64 bit version from a USB stick as for some reason wubi won't install... but perhaps that is another thread. Or perhaps not.

Wireless hardware is an Intel Centrino wireless-N 1000. The wireless is enabled (checked) in the context menu accessed from the top right of the desktop but no networks are visible. The following is strange - if I tap the Lenovo wireless on/off button (F9) in conjunction with shift OR ctrl the wireless context menu on the top right will SOMETIMES show a list of available networks as if it was working correctly, but only for a fraction of a second. Very odd.

I have tried to follow the official Ubuntu 11.04 help tutorial 'Resolve problems with wireless connections' and have accessed the terminal and followed the commands it suggests. I will paste the output here. Not sure how useful this is though - I am a newb and really want to scrap W7 and install sweet, sweet Ubuntu:

                                 ubuntu@ubuntu:~$ **nm-tool  **
 

 NetworkManager Tool  
 

 State: disconnected  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             unavailable  
   Default:           no  
   HW Address:        F0:DE:F1:5B:FF:4A  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           10 Mb/s  
 

   Wired Properties  
     Carrier:         off  
 

 

 - Device: wlan0 ----------------------------------------------------------------  
   Type:              802.11 WiFi  
   Driver:            iwlagn  
   State:             unavailable  
   Default:           no  
   HW Address:        8C:A9:82:77:1A:34  
 

   Capabilities:  
 

   Wireless Properties  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Access Points  
 

 

 ubuntu@ubuntu:~$ 



...




                                  ubuntu@ubuntu:~$ **sudo lshw -C network  **
   *-network                
        description: Ethernet interface  
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 06  
        serial: f0:de:f1:5b:ff:4a  
        size: 10Mbit/s  
        capacity: 1Gbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s  
        resources: irq:41 ioport:4000(size=256) memory:90404000-90404fff memory:90400000-90403fff  
   *-network DISABLED  
        description: Wireless interface  
        product: Centrino Wireless-N 1000  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:08:00.0  
        logical name: wlan0  
        version: 00  
        serial: 8c:a9:82:77:1a:34  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn  
        resources: irq:43 memory:91d00000-91d01fff  
 ubuntu@ubuntu:~$  
 


 I have also seen other peeps on here with wireless problems being asked for the output of **dmesg**:


                                  [    4.376980] system 00:0c: [mem 0x40000000-0x401fffff] could not be reserved  
 [    4.376982] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)  
 [    4.377002] pnp: PnP ACPI: found 13 devices  
 [    4.377004] ACPI: ACPI bus type pnp unregistered  
 [    4.382931] pci 0000:00:1c.0: PCI bridge to [bus 01-01]  
 [    4.382933] pci 0000:00:1c.0:   bridge window [io  disabled]  
 [    4.382938] pci 0000:00:1c.0:   bridge window [mem disabled]  
 [    4.382943] pci 0000:00:1c.0:   bridge window [mem pref disabled]  
 [    4.382950] pci 0000:00:1c.1: PCI bridge to [bus 02-02]  
 [    4.382953] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]  
 [    4.382959] pci 0000:00:1c.1:   bridge window [mem disabled]  
 [    4.382964] pci 0000:00:1c.1:   bridge window [mem 0x90400000-0x904fffff 64bit pref]  
 [    4.382971] pci 0000:00:1c.2: PCI bridge to [bus 03-07]  
 [    4.382974] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]  
 [    4.382980] pci 0000:00:1c.2:   bridge window [mem 0x91e00000-0x925fffff]  
 [    4.382985] pci 0000:00:1c.2:   bridge window [mem 0x90500000-0x90cfffff 64bit pref]  
 [    4.382992] pci 0000:00:1c.3: PCI bridge to [bus 08-08]  
 [    4.382993] pci 0000:00:1c.3:   bridge window [io  disabled]  
 [    4.382999] pci 0000:00:1c.3:   bridge window [mem 0x91d00000-0x91dfffff]  
 [    4.383003] pci 0000:00:1c.3:   bridge window [mem pref disabled]  
 [    4.383010] pci 0000:00:1c.7: PCI bridge to [bus 09-0d]  
 [    4.383014] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]  
 [    4.383021] pci 0000:00:1c.7:   bridge window [mem 0x91500000-0x91cfffff]  
 [    4.383027] pci 0000:00:1c.7:   bridge window [mem 0x90d00000-0x914fffff 64bit pref]  
 [    4.383048] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    4.383055] pci 0000:00:1c.0: setting latency timer to 64  
 [    4.383066] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    4.383070] pci 0000:00:1c.1: setting latency timer to 64  
 [    4.383080] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    4.383085] pci 0000:00:1c.2: setting latency timer to 64  
 [    4.383095] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19  
 [    4.383099] pci 0000:00:1c.3: setting latency timer to 64  
 [    4.383107] pci 0000:00:1c.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19  
 [    4.383112] pci 0000:00:1c.7: setting latency timer to 64  
 [    4.383116] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]  
 [    4.383118] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]  
 [    4.383120] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]  
 [    4.383122] pci_bus 0000:00: resource 7 [mem 0x7f200000-0xfeafffff]  
 [    4.383124] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]  
 [    4.383126] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]  
 [    4.383128] pci_bus 0000:02: resource 2 [mem 0x90400000-0x904fffff 64bit pref]  
 [    4.383130] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]  
 [    4.383132] pci_bus 0000:03: resource 1 [mem 0x91e00000-0x925fffff]  
 [    4.383134] pci_bus 0000:03: resource 2 [mem 0x90500000-0x90cfffff 64bit pref]  
 [    4.383136] pci_bus 0000:08: resource 1 [mem 0x91d00000-0x91dfffff]  
 [    4.383138] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]  
 [    4.383140] pci_bus 0000:09: resource 1 [mem 0x91500000-0x91cfffff]  
 [    4.383142] pci_bus 0000:09: resource 2 [mem 0x90d00000-0x914fffff 64bit pref]  
 [    4.383170] NET: Registered protocol family 2  
 [    4.383272] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)  
 [    4.384053] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)  
 [    4.385016] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)  
 [    4.385253] TCP: Hash tables configured (established 262144 bind 65536)  
 [    4.385255] TCP reno registered  
 [    4.385261] UDP hash table entries: 1024 (order: 3, 32768 bytes)  
 [    4.385275] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)  
 [    4.385377] NET: Registered protocol family 1  
 [    4.385392] pci 0000:00:02.0: Boot video device  
 [    4.385585] PCI: CLS 64 bytes, default 64  
 [    4.385587] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)  
 [    4.385589] Placing 64MB software IO TLB between ffff880072a00000 - ffff880076a00000  
 [    4.385591] software IO TLB at phys 0x72a00000 - 0x76a00000  
 [    4.386038] audit: initializing netlink socket (disabled)  
 [    4.386046] type=2000 audit(1305578424.230:1): initialized  
 [    4.399220] HugeTLB registered 2 MB page size, pre-allocated 0 pages  
 [    4.400766] VFS: Disk quotas dquot_6.5.2  
 [    4.400815] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)  
 [    4.401342] fuse init (API version 7.16)  
 [    4.401416] msgmni has been set to 3701  
 [    4.401627] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)  
 [    4.401652] io scheduler noop registered  
 [    4.401654] io scheduler deadline registered  
 [    4.401688] io scheduler cfq registered (default)  
 [    4.402028] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    4.402047] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    4.402085] intel_idle: MWAIT substates: 0x21120  
 [    4.402087] intel_idle: v0.4 model 0x2A  
 [    4.402088] intel_idle: lapic_timer_reliable_states 0xffffffff  
 [    4.469826] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    4.469878] ACPI: AC Adapter [ADP1] (off-line)  
 [    4.469992] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0  
 [    4.629491] ACPI: Lid Switch [LID0]  
 [    4.629585] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1  
 [    4.629588] ACPI: Power Button [PWRF]  
 [    4.629753] ACPI: acpi_idle yielding to intel_idle  
 [    4.631255] ACPI Error: No handler for Region [ECRM] (ffff88006f50e2d0) [EmbeddedControl] (20110112/evregion-369)  
 [    4.631261] ACPI Error: Region EmbeddedControl(0x3) has no handler (20110112/exfldio-292)  
 [    4.631265] ACPI Error: Method parse/execution failed [\_TZ_.RDEC] (Node ffff8801003cf4b0), AE_NOT_EXIST (20110112/psparse-536)  
 [    4.631273] ACPI Error: Method parse/execution failed [\_TZ_.TZS0._TMP] (Node ffff8801003cf528), AE_NOT_EXIST (20110112/psparse-536)  
 [    4.631441] thermal LNXTHERM:01: registered as thermal_zone0  
 [    4.631443] ACPI: Thermal Zone [TZS1] (36 C)  
 [    4.631458] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    4.631531] ERST: Table is not found!  
 [    4.631610] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled  
 [    4.632325] ACPI: Battery Slot [BAT0] (battery present)  
 [    4.641396] Linux agpgart interface v0.103  
 [    4.641471] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset  
 [    4.641582] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable  
 [    4.642743] agpgart-intel 0000:00:00.0: detected 65536K stolen memory  
 [    4.642843] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000  
 [    4.643748] brd: module loaded  
 [    4.644171] loop: module loaded  
 [    4.644244] i2c-core: driver [adp5520] using legacy suspend method  
 [    4.644246] i2c-core: driver [adp5520] using legacy resume method  
 [    4.644565] Fixed MDIO Bus: probed  
 [    4.644588] PPP generic driver version 2.4.2  
 [    4.644622] tun: Universal TUN/TAP device driver, 1.6  
 [    4.644623] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>  
 [    4.644689] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    4.644705] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    4.644722] ehci_hcd 0000:00:1a.0: setting latency timer to 64  
 [    4.644726] ehci_hcd 0000:00:1a.0: EHCI Host Controller  
 [    4.644756] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1  
 [    4.644816] ehci_hcd 0000:00:1a.0: debug port 2  
 [    4.648702] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported  
 [    4.648721] ehci_hcd 0000:00:1a.0: irq 16, io mem 0x9260a000  
 [    4.669438] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00  
 [    4.669585] hub 1-0:1.0: USB hub found  
 [    4.669589] hub 1-0:1.0: 2 ports detected  
 [    4.669651] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    4.669663] ehci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    4.669667] ehci_hcd 0000:00:1d.0: EHCI Host Controller  
 [    4.669701] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    4.669749] ehci_hcd 0000:00:1d.0: debug port 2  
 [    4.673627] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported  
 [    4.673640] ehci_hcd 0000:00:1d.0: irq 23, io mem 0x92609000  
 [    4.689415] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00  
 [    4.689545] hub 2-0:1.0: USB hub found  
 [    4.689548] hub 2-0:1.0: 2 ports detected  
 [    4.689601] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    4.689610] uhci_hcd: USB Universal Host Controller Interface driver  
 [    4.689702] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12  
 [    4.691869] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    4.691875] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    4.691970] mousedev: PS/2 mouse device common for all mice  
 [    4.692068] rtc_cmos 00:07: RTC can wake from S4  
 [    4.692123] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0  
 [    4.692151] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs  
 [    4.692235] device-mapper: uevent: version 1.0.3  
 [    4.692298] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  
 [    4.692358] device-mapper: multipath: version 1.2.0 loaded  
 [    4.692361] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    4.692561] cpuidle: using governor ladder  
 [    4.692733] cpuidle: using governor menu  
 [    4.692926] TCP cubic registered  
 [    4.693026] NET: Registered protocol family 10  
 [    4.693426] NET: Registered protocol family 17  
 [    4.693438] Registering the dns_resolver key type  
 [    4.694316] PM: Hibernation image not present or could not be loaded.  
 [    4.694327] registered taskstats version 1  
 [    4.694836]   Magic number: 11:450:700  
 [    4.694937] rtc_cmos 00:07: setting system clock to 2011-05-16 20:40:24 UTC (1305578424)  
 [    4.694939] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    4.694940] EDD information not available.  
 [    4.696595] Freeing unused kernel memory: 956k freed  
 [    4.696770] Write protecting the kernel read-only data: 10240k  
 [    4.697612] Freeing unused kernel memory: 184k freed  
 [    4.702333] Freeing unused kernel memory: 1444k freed  
 [    4.709810] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2  
 [    4.724918] <30>udev[75]: starting version 167  
 [    4.764276] sdhci: Secure Digital Host Controller Interface driver  
 [    4.764280] sdhci: Copyright(c) Pierre Ossman  
 [    4.773191] sdhci-pci 0000:03:00.0: SDHCI controller found [1180:e823] (rev 4)  
 [    4.773246] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    4.773504] sdhci-pci 0000:03:00.0: setting latency timer to 64  
 [    4.773532] mmc0: no vmmc regulator found  
 [    4.773620] Registered led device: mmc0::  
 [    4.775530] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA  
 [    4.778022] ahci 0000:00:1f.2: version 3.0  
 [    4.778039] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    4.778112] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X  
 [    4.778155] ahci: SSS flag set, parallel bus scan disabled  
 [    4.790858] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x31 impl SATA mode  
 [    4.790864] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst  
 [    4.790873] ahci 0000:00:1f.2: setting latency timer to 64  
 [    4.804284] [drm] Initialized drm 1.1.0 20060810  
 [    4.808237] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded  
 [    4.808274] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [    4.808392] r8169 0000:02:00.0: setting latency timer to 64  
 [    4.808410] r8169 0000:02:00.0: (unregistered net_device): unknown MAC, using family default  
 [    4.808632] r8169 0000:02:00.0: irq 41 for MSI/MSI-X  
 [    4.809327] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc90000926000, f0:de:f1:5b:ff:4a, XID 0c200000 IRQ 41  
 [    4.830000] scsi0 : ahci  
 [    4.830157] scsi1 : ahci  
 [    4.830271] scsi2 : ahci  
 [    4.830409] scsi3 : ahci  
 [    4.830650] scsi4 : ahci  
 [    4.830790] scsi5 : ahci  
 [    4.831170] ata1: SATA max UDMA/133 abar m2048@0x92608000 port 0x92608100 irq 40  
 [    4.831172] ata2: DUMMY  
 [    4.831173] ata3: DUMMY  
 [    4.831174] ata4: DUMMY  
 [    4.831177] ata5: SATA max UDMA/133 abar m2048@0x92608000 port 0x92608300 irq 40  
 [    4.831180] ata6: SATA max UDMA/133 abar m2048@0x92608000 port 0x92608380 irq 40  
 [    4.831239] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    4.831245] i915 0000:00:02.0: setting latency timer to 64  
 [    4.887950] mtrr: no more MTRRs available  
 [    4.887953] [drm] MTRR allocation failed.  Graphics performance may suffer.  
 [    4.888246] i915 0000:00:02.0: irq 42 for MSI/MSI-X  
 [    4.888251] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).  
 [    4.888252] [drm] Driver supports precise vblank timestamp query.  
 [    4.988964] usb 1-1: new high speed USB device using ehci_hcd and address 2  
 [    4.989371] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem  
 [    5.134601] Console: switching to colour frame buffer device 170x48  
 [    5.137299] fb0: inteldrmfb frame buffer device  
 [    5.137301] drm: registered panic notifier  
 [    5.139451] hub 1-1:1.0: USB hub found  
 [    5.139534] hub 1-1:1.0: 6 ports detected  
 [    5.178789] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  
 [    5.249465] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded  
 [    5.249470] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out  
 [    5.249473] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out  
 [    5.249787] acpi device:40: registered as cooling_device4  
 [    5.250050] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input3  
 [    5.250125] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)  
 [    5.250234] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0  
 [    5.258662] usb 2-1: new high speed USB device using ehci_hcd and address 2  
 [    5.378463] Refined TSC clocksource calibration: 2095.239 MHz.  
 [    5.378482] Switching to clocksource tsc  
 [    5.409038] hub 2-1:1.0: USB hub found  
 [    5.409129] hub 2-1:1.0: 6 ports detected  
 [    5.488464] usb 1-1.5: new high speed USB device using ehci_hcd and address 3  
 [    5.688167] usb 2-1.2: new high speed USB device using ehci_hcd and address 3  
 [    5.820926] ata1.00: ATA-8: TOSHIBA MK3261GSY, MC002E, max UDMA/100  
 [    5.820935] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA  
 [    5.822074] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded  
 [    5.822085] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out  
 [    5.822093] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out  
 [    5.823021] ata1.00: configured for UDMA/100  
 [    5.823176] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3261GS MC00 PQ: 0 ANSI: 5  
 [    5.823314] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)  
 [    5.823353] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    5.823374] sd 0:0:0:0: [sda] Write Protect is off  
 [    5.823378] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    5.823405] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    5.826972] usbcore: registered new interface driver uas  
 [    5.866722]  sda: sda1 sda2 sda3  
 [    5.867066] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    5.897853] usb 2-1.4: new full speed USB device using ehci_hcd and address 4  
 [    6.566710] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  
 [    6.570998] ata5.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)  
 [    6.571017] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out  
 [    6.571020] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out  
 [    6.571025] ata5.00: ATAPI: SlimtypeDVD A  DS8A5SH, XL63, max UDMA/100  
 [    6.573460] ata5.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)  
 [    6.573472] ata5.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out  
 [    6.573480] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out  
 [    6.573500] ata5.00: configured for UDMA/100  
 [    6.577924] scsi 4:0:0:0: CD-ROM            Slimtype DVD A  DS8A5SH   XL63 PQ: 0 ANSI: 5  
 [    6.583843] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    6.583847] cdrom: Uniform CD-ROM driver Revision: 3.20  
 [    6.584028] sr 4:0:0:0: Attached scsi CD-ROM sr0  
 [    6.584123] sr 4:0:0:0: Attached scsi generic sg1 type 5  
 [    6.926178] ata6: SATA link down (SStatus 0 SControl 300)  
 [    6.935015] Initializing USB Mass Storage driver...  
 [    6.935144] scsi6 : usb-storage 2-1.2:1.0  
 [    6.935287] usbcore: registered new interface driver usb-storage  
 [    6.935290] USB Mass Storage support registered.  
 [    7.522923] Btrfs loaded  
 [    7.527894] xor: automatically using best checksumming function: generic_sse  
 [    7.575091]    generic_sse:  9326.400 MB/sec  
 [    7.575094] xor: using function: generic_sse (9326.400 MB/sec)  
 [    7.577411] device-mapper: dm-raid45: initialized v0.2594b  
 [    7.925544] scsi 6:0:0:0: Direct-Access     A-DATA   USB Flash Drive  0.00 PQ: 0 ANSI: 2  
 [    7.926026] sd 6:0:0:0: Attached scsi generic sg2 type 0  
 [    7.926620] sd 6:0:0:0: [sdb] 7897088 512-byte logical blocks: (4.04 GB/3.76 GiB)  
 [    7.927425] sd 6:0:0:0: [sdb] Write Protect is off  
 [    7.927429] sd 6:0:0:0: [sdb] Mode Sense: 00 00 00 00  
 [    7.928054] sd 6:0:0:0: [sdb] Asking for cache data failed  
 [    7.928057] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
 [    7.931964] sd 6:0:0:0: [sdb] Asking for cache data failed  
 [    7.931967] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
 [    8.091953]  sdb: sdb1  
 [    8.094249] sd 6:0:0:0: [sdb] Asking for cache data failed  
 [    8.094253] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
 [    8.094255] sd 6:0:0:0: [sdb] Attached SCSI removable disk  
 [    9.969247] aufs 2.1-standalone.tree-38-rcN-20110207  
 [    9.982803] squashfs: version 4.0 (2009/01/31) Phillip Lougher  
 [   11.506812] EXT3-fs: barriers not enabled  
 [   11.508350] kjournald starting.  Commit interval 5 seconds  
 [   11.509050] EXT3-fs (loop1): using internal journal  
 [   11.509062] EXT3-fs (loop1): mounted filesystem with ordered data mode  
 [   11.517567] aufs test_add:261:exe[706]: uid/gid/perm //filesystem.squashfs 0/0/0755, 1000/1000/0755  
 [   21.480683] <30>udev[2464]: starting version 167  
 [   21.919653] Linux video capture interface: v2.00  
 [   21.954483] Bluetooth: Core ver 2.15 
 [   21.954517] NET: Registered protocol family 31  
 [   21.954519] Bluetooth: HCI device and connection manager initialized  
 [   21.954522] Bluetooth: HCI socket layer initialized  
 [   21.963261] acer-wmi: Acer Laptop ACPI-WMI Extras  
 [   21.994371] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b257)  
 [   21.996327] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4 
 [   21.996383] usbcore: registered new interface driver uvcvideo  
 [   21.996385] USB Video Class driver (v1.0.0)  
 [   22.023285] cfg80211: Calling CRDA to update world regulatory domain  
 [   22.031873] Bluetooth: Generic Bluetooth USB driver ver 0.6  
 [   22.034759] usbcore: registered new interface driver btusb  
 [   22.038194] Non-volatile memory driver v1.3  
 [   22.254286] r8169 0000:02:00.0: eth0: link down  
 [   22.254563] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   22.321722] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:  
 [   22.321726] iwlagn: Copyright(c) 2003-2010 Intel Corporation  
 [   22.321814] iwlagn 0000:08:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19  
 [   22.321845] iwlagn 0000:08:00.0: setting latency timer to 64  
 [   22.321909] iwlagn 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C  
 [   22.345543] iwlagn 0000:08:00.0: device EEPROM VER=0x15d, CALIB=0x6  
 [   22.345547] iwlagn 0000:08:00.0: Device SKU: 0X9  
 [   22.345549] iwlagn 0000:08:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3  
 [   22.345566] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels  
 [   22.345852] iwlagn 0000:08:00.0: irq 43 for MSI/MSI-X  
 [   22.498160] iwlagn 0000:08:00.0: loaded firmware version 128.50.3.1 build 13488  
 [   22.498376] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain  
 [   22.567710] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'  
 [   22.646665] Bluetooth: L2CAP ver 2.15  
 [   22.646670] Bluetooth: L2CAP socket layer initialized  
 [   22.649205] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd000b3/0x340000/0xa0400  
 [   22.649213] serio: Synaptics pass-through port at isa0060/serio1/input0  
 [   22.660557] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain  
 [   22.660565] cfg80211: World regulatory domain updated:  
 [   22.660568] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   22.660572] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   22.660576] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   22.660580] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   22.660583] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   22.660587] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   22.678542] thinkpad_acpi: ThinkPad ACPI Extras v0.24  
 [   22.678546] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)  
 [   22.678549] thinkpad_acpi: ThinkPad BIOS 8HET28WW(1.10), EC unknown  
 [   22.678552] thinkpad_acpi: Lenovo ThinkPad E520, model 1143CTO  
 [   22.681679] thinkpad_acpi: detected a 8-level brightness capable ThinkPad  
 [   22.681901] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5  
 [   22.695593] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked  
 [   22.696080] Registered led device: tpacpi::thinklight  
 [   22.696098] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.  
 [   22.696238] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)  
 [   22.698296] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6  
 [   22.714879] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   22.714883] Bluetooth: BNEP filters: protocol multicast  
 [   22.758548] Bluetooth: SCO (Voice Link) ver 0.6  
 [   22.758552] Bluetooth: SCO socket layer initialized  
 [   22.838309] Bluetooth: RFCOMM TTY layer initialized  
 [   22.838315] Bluetooth: RFCOMM socket layer initialized  
 [   22.838317] Bluetooth: RFCOMM ver 1.11  
 [   22.913228] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [   22.913297] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X  
 [   22.913328] HDA Intel 0000:00:1b.0: setting latency timer to 64  
 [   23.706623] lp: driver loaded but no devices found  
 [   23.733590] ppdev: user-space parallel port driver  
 [   27.235594] IBM TrackPoint firmware: 0x0e, buttons: 3/3  
 [   27.412016] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input7  
 [  691.116615] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  710.438939] usb 2-1.4: USB disconnect, address 4  
 [  712.744219] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  712.984036] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  715.530586] usb 2-1.4: new full speed USB device using ehci_hcd and address 5  
 [  716.857808] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  717.127570] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  719.385856] usb 2-1.4: USB disconnect, address 5  
 [  719.386005] btusb_intr_complete: hci0 urb ffff88006b815480 failed to resubmit (19)  
 [  719.386175] btusb_bulk_complete: hci0 urb ffff88006b815a80 failed to resubmit (19)  
 [  719.386189] btusb_bulk_complete: hci0 urb ffff88006b815f00 failed to resubmit (19)  
 [  720.564084] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  720.762127] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  722.809553] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 39989, at 39989], missed IRQ?  
 [  722.939646] usb 2-1.4: new full speed USB device using ehci_hcd and address 6  
 [  724.796099] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  727.309728] usb 2-1.4: USB disconnect, address 6  
 [  727.309869] btusb_intr_complete: hci0 urb ffff88006b52bd80 failed to resubmit (19)  
 [  727.309883] btusb_bulk_complete: hci0 urb ffff88006b52b840 failed to resubmit (19)  
 [  727.309997] btusb_bulk_complete: hci0 urb ffff88006b52b600 failed to resubmit (19)  
 [  728.081258] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  730.338339] [drm:i915_hangcheck_ring_idle] *ERROR* Hangcheck timer elapsed... blt ring idle [waiting on 41446, at 41446], missed IRQ?  
 [  732.843858] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  733.164283] usb 2-1.4: new full speed USB device using ehci_hcd and address 7  
 [  734.722451] usb 2-1.4: USB disconnect, address 7  
 [  734.722533] btusb_bulk_complete: hci0 urb ffff88006ddff540 failed to resubmit (19)  
 [  734.722610] btusb_intr_complete: hci0 urb ffff88006f816300 failed to resubmit (19)  
 [  734.722670] btusb_bulk_complete: hci0 urb ffff88006ddff180 failed to resubmit (19)  
 [  738.915351] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  740.733618] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  740.832810] usb 2-1.4: new full speed USB device using ehci_hcd and address 8  
 [  742.646571] usb 2-1.4: USB disconnect, address 8  
 [  742.646676] btusb_bulk_complete: hci0 urb ffff88006f6cf180 failed to resubmit (19)  
 [  742.646734] btusb_intr_complete: hci0 urb ffff88006b8dc9c0 failed to resubmit (19)  
 [  742.646800] btusb_bulk_complete: hci0 urb ffff88006dc899c0 failed to resubmit (19)  
 [  742.829072] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  745.265865] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [  745.695709] usb 2-1.4: new full speed USB device using ehci_hcd and address 9  
 [ 1459.372376] usb 1-1.3: new high speed USB device using ehci_hcd and address 4  
 [ 1459.488985] scsi7 : usb-storage 1-1.3:1.0  
 [ 1460.482606] scsi 7:0:0:0: Direct-Access     SanDisk  SDDR-113         9412 PQ: 0 ANSI: 0  
 [ 1460.484092] sd 7:0:0:0: Attached scsi generic sg3 type 0  
 [ 1460.608774] sd 7:0:0:0: [sdc] 7959552 512-byte logical blocks: (4.07 GB/3.79 GiB)  
 [ 1460.610120] sd 7:0:0:0: [sdc] Write Protect is off  
 [ 1460.610131] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00  
 [ 1460.611184] sd 7:0:0:0: [sdc] No Caching mode page present  
 [ 1460.611194] sd 7:0:0:0: [sdc] Assuming drive cache: write through  
 [ 1460.614707] sd 7:0:0:0: [sdc] No Caching mode page present  
 [ 1460.614714] sd 7:0:0:0: [sdc] Assuming drive cache: write through  
 [ 1460.615741]  sdc: sdc1  
 [ 1460.618847] sd 7:0:0:0: [sdc] No Caching mode page present  
 [ 1460.618854] sd 7:0:0:0: [sdc] Assuming drive cache: write through  
 [ 1460.618860] sd 7:0:0:0: [sdc] Attached SCSI removable disk  
 [ 1984.365057] usb 1-1.3: USB disconnect, address 4  
 [ 2192.999343] usb 1-1.3: new high speed USB device using ehci_hcd and address 5  
 [ 2193.115804] scsi8 : usb-storage 1-1.3:1.0  
 [ 2194.109754] scsi 8:0:0:0: Direct-Access     SanDisk  SDDR-113         9412 PQ: 0 ANSI: 0  
 [ 2194.111194] sd 8:0:0:0: Attached scsi generic sg3 type 0  
 [ 2194.236359] sd 8:0:0:0: [sdc] 7959552 512-byte logical blocks: (4.07 GB/3.79 GiB)  
 [ 2194.237613] sd 8:0:0:0: [sdc] Write Protect is off  
 [ 2194.237623] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00  
 [ 2194.238589] sd 8:0:0:0: [sdc] No Caching mode page present  
 [ 2194.238599] sd 8:0:0:0: [sdc] Assuming drive cache: write through  
 [ 2194.243046] sd 8:0:0:0: [sdc] No Caching mode page present  
 [ 2194.243056] sd 8:0:0:0: [sdc] Assuming drive cache: write through  
 [ 2194.244059]  sdc: sdc1  
 [ 2194.247152] sd 8:0:0:0: [sdc] No Caching mode page present  
 [ 2194.247162] sd 8:0:0:0: [sdc] Assuming drive cache: write through  
 [ 2194.247168] sd 8:0:0:0: [sdc] Attached SCSI removable disk  
 ubuntu@ubuntu:~$  
  
 
Hope someone can help. This is driving me mental.

Cheers and that.

---

### Post by josephmills on 2011-05-16
could we all see a ```
rfkill list all 
``` thanks

---

### Post by awfullook on 2011-05-16
You all may indeed:

ubuntu@ubuntu:~$ rfkill list all  
 0: acer-wireless: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: no  
 1: tpacpi_bluetooth_sw: Bluetooth  
 	Soft blocked: yes  
 	Hard blocked: no  
 2: phy0: Wireless LAN  
 	Soft blocked: yes  
 	Hard blocked: no  
 ubuntu@ubuntu:~$

---

### Post by awfullook on 2011-05-16
OK, I found this thread: [http://ubuntuforums.org/showthread.php?t=1744402&highlight=edge+e520](http://ubuntuforums.org/showthread.php?t=1744402&highlight=edge+e520)

and on it, this load of mad terminal stuff:

$ rfkill list all
$ sudo rmmod -f acer_wmi
$ sudo rfkill unblock all
$ sudo su
# echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
# exit

Which, for the time being, appears to have totally worked. I can now see all the wireless networks within range, and I can connect to mine and surf directly to the Warp Records website. Which means the internet is up and running!

Thanks for your help, the fact that there had been a reply on here at all motivated me to dig deeper and try and answer this myself. No idea what 'acer_wmi' is, but I hate it. And have condemned it for all time.

Many Thanks

---

### Post by BigSnake.NET on 2011-06-24
hello awfullook. I'm a linux user and i plan to buy a thinkpad edge e520. I wounder whether the AMD graphic card can work under linux(with the newest drivers). Do you have any idea?

thx.

---

### Post by wgarciamachmar on 2011-08-11
Thanks! I had the exact same problem in my Sony Vaio PCG

---

### Post by danger89 on 2011-09-12
Somebody know also if the AMD gfx works under Linux with the edge 520?

---

### Post by kastelix on 2011-11-09
it works for me im in ubuntu 10.10 
$ rfkill list all
$ sudo rmmod -f acer_wmi
$ sudo rfkill unblock all
$ sudo su
# echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
# exit
great thnx guys

---

### Post by mandaofpune on 2012-05-31
Hey thanks a lot..

I have a Sony Vaio with Intel Centrino -N 1000 wireless adaptor and I recently upgraded by Ubuntu 10.04 to 11.04 and suddenly no wireless networks were detected.. 

Read quite a few posts on this forum.. and finally bumped here.. I tried the $rfkill list all
and it showed "Soft blocked: yes" for acer-wireless 
so I did $sudo rmmod -f acer_wmi
and my wirelss was detected instantaneously !!!

I am really happy :) This is my first instance of successfully solving something by reading forum posts.. (as you would guess I am a newbie to Ubuntu)

Forum rocks!! Thanks guys :)

---

