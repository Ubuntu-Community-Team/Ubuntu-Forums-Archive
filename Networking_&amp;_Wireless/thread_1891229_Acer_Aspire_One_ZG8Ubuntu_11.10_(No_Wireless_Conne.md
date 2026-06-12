---
title: "Acer Aspire One ZG8/Ubuntu 11.10 (No Wireless Connection)"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by cozski on 2011-12-05
Hello, after a clean install on my Netbook I am not able to connect to my home wireless; checking the option to enable wireless from the panel has no effect. Below is the information as advised to post. I appreciate any help. Thanks.


	  **sunonthecross@sunonthecross:~$  lspci ** 
 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)  
 00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)  
 00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)  
 00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)  
 01:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0) 
 02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
 

 **sunonthecross@sunonthecross:~$  lsusb ** 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 007: ID 04f2:b175 Chicony Electronics Co., Ltd
 

 **sunonthecross@sunonthecross:~$ ifconfig ** 
 eth0      Link encap:Ethernet  HWaddr 00:23:8b:a2:26:b0   
           inet addr:10.110.182.176  Bcast:10.110.182.255  Mask:255.255.255.0  
           inet6 addr: fe80::223:8bff:fea2:26b0/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:55393 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:36833 errors:0 dropped:0 overruns:0 carrier:1  
           collisions:0 txqueuelen:1000  
           RX bytes:79435928 (79.4 MB)  TX bytes:2832518 (2.8 MB)  
           Interrupt:45  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 

 **sunonthecross@sunonthecross:~$ iwconfig**  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off
 

 sunonthecross@sunonthecross:~$ lsmod  
 Module                  Size  Used by  
 parport_pc             32114  0  
 ppdev                  12849  0  
 joydev                 17393  0  
 bnep                   17923  2  
 rfcomm                 38408  0  
 bluetooth             148839  10 bnep,rfcomm  
 acer_wmi               23302  0  
 sparse_keymap          13658  1 acer_wmi  
 arc4                   12473  2  
 ath5k                 145100  0  
 snd_hda_codec_realtek   254125  1  
 ath                    19387  1 ath5k  
 mac80211              272785  1 ath5k  
 uvcvideo               67271  0  
 videodev               85626  1 uvcvideo  
 snd_hda_intel          24262  2  
 snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep              13276  1 snd_hda_codec  
 snd_pcm                80468  2 snd_hda_intel,snd_hda_codec  
 psmouse                73673  0  
 cfg80211              172392  3 ath5k,ath,mac80211  
 serio_raw              12990  0  
 snd_seq_midi           13132  0  
 snd_rawmidi            25241  1 snd_seq_midi  
 snd_seq_midi_event     14475  1 snd_seq_midi  
 snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event  
 binfmt_misc            17292  1  
 snd_timer              28932  2 snd_pcm,snd_seq  
 snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq  
 wmi                    18744  1 acer_wmi  
 snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i915                  505108  3  
 soundcore              12600  1 snd  
 drm_kms_helper         32889  1 i915  
 snd_page_alloc         14115  2 snd_hda_intel,snd_pcm  
 drm                   192226  4 i915,drm_kms_helper  
 i2c_algo_bit           13199  1 i915  
 video                  18908  1 i915  
 lp                     17455  0  
 parport                40930  3 parport_pc,ppdev,lp  
 ahci                   21634  2  
 libahci                25727  1 ahci  
 atl1e                  32809  0
 

 [    0.416196] pnp 00:01: [io  0x0400-0x047f]  
 [    0.416203] pnp 00:01: [io  0x0500-0x053f]  
 [    0.416212] pnp 00:01: [mem 0xe0000000-0xefffffff]  
 [    0.416220] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]  
 [    0.416228] pnp 00:01: [mem 0xfed14000-0xfed17fff]  
 [    0.416236] pnp 00:01: [mem 0xfed18000-0xfed18fff]  
 [    0.416244] pnp 00:01: [mem 0xfed19000-0xfed19fff]  
 [    0.416253] pnp 00:01: [mem 0xfec00000-0xfec00fff]  
 [    0.416260] pnp 00:01: [mem 0xfee00000-0xfee00fff]  
 [    0.416493] system 00:01: [io  0x0200-0x020f] has been reserved  
 [    0.416505] system 00:01: [io  0x0600-0x060f] has been reserved  
 [    0.416515] system 00:01: [io  0x0610] has been reserved  
 [    0.416525] system 00:01: [io  0x0800-0x080f] has been reserved  
 [    0.416536] system 00:01: [io  0x0400-0x047f] has been reserved  
 [    0.416547] system 00:01: [io  0x0500-0x053f] has been reserved  
 [    0.416560] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved  
 [    0.416572] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved  
 [    0.416582] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved  
 [    0.416593] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved  
 [    0.416603] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved  
 [    0.416623] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved  
 [    0.416634] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved  
 [    0.416647] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)  
 [    0.416691] pnp 00:02: [io  0x0000-0x001f]  
 [    0.416699] pnp 00:02: [io  0x0081-0x0091]  
 [    0.416707] pnp 00:02: [io  0x0093-0x009f]  
 [    0.416715] pnp 00:02: [io  0x00c0-0x00df]  
 [    0.416728] pnp 00:02: [dma 4]  
 [    0.416832] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)  
 [    0.416931] pnp 00:03: [io  0x0070-0x0077]  
 [    0.417032] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)  
 [    0.417265] pnp 00:04: [irq 0 disabled]  
 [    0.417290] pnp 00:04: [irq 8]  
 [    0.417298] pnp 00:04: [mem 0xfed00000-0xfed003ff]  
 [    0.417415] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)  
 [    0.417461] pnp 00:05: [io  0x00f0]  
 [    0.417479] pnp 00:05: [irq 13]  
 [    0.417594] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)  
 [    0.417642] pnp 00:06: [mem 0xff800000-0xffffffff]  
 [    0.417749] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)  
 [    0.417835] pnp 00:07: [io  0x0060]  
 [    0.417843] pnp 00:07: [io  0x0064]  
 [    0.417861] pnp 00:07: [irq 1]  
 [    0.417964] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)  
 [    0.418032] pnp 00:08: [irq 12]  
 [    0.418142] pnp 00:08: Plug and Play ACPI device, IDs SYN1b20 SYN1b00 SYN0002 PNP0f13 (active)  
 [    0.418418] pnp: PnP ACPI: found 9 devices  
 [    0.418425] ACPI: ACPI bus type pnp unregistered  
 [    0.418434] PnPBIOS: Disabled by ACPI PNP  
 [    0.459587] PCI: max bus depth: 1 pci_try_num: 2  
 [    0.459660] pci 0000:00:1c.0: PCI bridge to [bus 01-01]  
 [    0.459672] pci 0000:00:1c.0:   bridge window [io  0x3000-0x4fff]  
 [    0.459687] pci 0000:00:1c.0:   bridge window [mem 0x55200000-0x562fffff]  
 [    0.459700] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]  
 [    0.459717] pci 0000:00:1c.2: PCI bridge to [bus 02-02]  
 [    0.459727] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]  
 [    0.459741] pci 0000:00:1c.2:   bridge window [mem 0x54100000-0x551fffff]  
 [    0.459754] pci 0000:00:1c.2:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]  
 [    0.459770] pci 0000:00:1c.3: PCI bridge to [bus 03-03]  
 [    0.459780] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]  
 [    0.459794] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x540fffff]  
 [    0.459808] pci 0000:00:1c.3:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]  
 [    0.459824] pci 0000:00:1e.0: PCI bridge to [bus 04-04]  
 [    0.459831] pci 0000:00:1e.0:   bridge window [io  disabled]  
 [    0.459843] pci 0000:00:1e.0:   bridge window [mem disabled]  
 [    0.459854] pci 0000:00:1e.0:   bridge window [mem pref disabled]  
 [    0.459912] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.459927] pci 0000:00:1c.0: setting latency timer to 64  
 [    0.459958] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    0.459971] pci 0000:00:1c.2: setting latency timer to 64  
 [    0.460040] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19  
 [    0.460053] pci 0000:00:1c.3: setting latency timer to 64  
 [    0.460073] pci 0000:00:1e.0: setting latency timer to 64  
 [    0.460086] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]  
 [    0.460094] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]  
 [    0.460104] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]  
 [    0.460114] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]  
 [    0.460124] pci_bus 0000:01: resource 0 [io  0x3000-0x4fff]  
 [    0.460134] pci_bus 0000:01: resource 1 [mem 0x55200000-0x562fffff]  
 [    0.460145] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]  
 [    0.460156] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]  
 [    0.460165] pci_bus 0000:02: resource 1 [mem 0x54100000-0x551fffff]  
 [    0.460175] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]  
 [    0.460185] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]  
 [    0.460194] pci_bus 0000:03: resource 1 [mem 0x53000000-0x540fffff]  
 [    0.460203] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]  
 [    0.460213] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]  
 [    0.460222] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]  
 [    0.460231] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]  
 [    0.460241] pci_bus 0000:04: resource 7 [mem 0x40000000-0xfebfffff]  
 [    0.460365] NET: Registered protocol family 2  
 [    0.460563] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  
 [    0.461451] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  
 [    0.462583] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  
 [    0.463178] TCP: Hash tables configured (established 131072 bind 65536)  
 [    0.463192] TCP reno registered  
 [    0.463213] UDP hash table entries: 512 (order: 2, 16384 bytes)  
 [    0.463241] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)  
 [    0.463553] NET: Registered protocol family 1  
 [    0.463603] pci 0000:00:02.0: Boot video device  
 [    0.463913] PCI: CLS 0 bytes, default 64  
 [    0.463927] Simple Boot Flag value 0x5 read from CMOS RAM was invalid  
 [    0.463934] Simple Boot Flag at 0x44 set to 0x1  
 [    0.465030] audit: initializing netlink socket (disabled)  
 [    0.465060] type=2000 audit(1323084190.460:1): initialized  
 [    0.525347] highmem bounce pool size: 64 pages  
 [    0.525366] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    0.538180] VFS: Disk quotas dquot_6.5.2  
 [    0.538409] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    0.541040] fuse init (API version 7.16)  
 [    0.541409] msgmni has been set to 1704  
 [    0.542703] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)  
 [    0.542849] io scheduler noop registered  
 [    0.542857] io scheduler deadline registered  
 [    0.542924] io scheduler cfq registered (default)  
 [    0.543302] pcieport 0000:00:1c.0: setting latency timer to 64  
 [    0.543400] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X  
 [    0.543576] pcieport 0000:00:1c.2: setting latency timer to 64  
 [    0.543667] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X  
 [    0.543828] pcieport 0000:00:1c.3: setting latency timer to 64  
 [    0.543913] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X  
 [    0.544225] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.544327] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.544508] intel_idle: MWAIT substates: 0x20220  
 [    0.544525] intel_idle: v0.4 model 0x1C  
 [    0.544531] intel_idle: lapic_timer_reliable_states 0x2  
 [    0.544551] Marking TSC unstable due to TSC halts in idle states deeper than C2  
 [    0.545036] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    0.545820] ACPI: AC Adapter [ACAD] (off-line)  
 [    0.546367] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0  
 [    0.546385] ACPI: Power Button [PWRB]  
 [    0.546583] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1  
 [    0.546936] ACPI: Lid Switch [LID0]  
 [    0.547096] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2  
 [    0.547113] ACPI: Sleep Button [SLPB]  
 [    0.547316] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3  
 [    0.547330] ACPI: Power Button [PWRF]  
 [    0.547426] ACPI: acpi_idle yielding to intel_idle  
 [    0.551492] thermal LNXTHERM:00: registered as thermal_zone0  
 [    0.551502] ACPI: Thermal Zone [THRM] (25 C)  
 [    0.551577] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared  
 [    0.551662] ERST: Table is not found!  
 [    0.551884] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled  
 [    0.552842] ACPI: Battery Slot [BAT1] (battery absent)  
 [    0.552871] isapnp: Scanning for PnP cards...  
 [    0.908225] isapnp: No Plug & Play device found  
 [    0.926168] Freeing initrd memory: 13296k freed  
 [    0.951591] Linux agpgart interface v0.103  
 [    0.951749] agpgart-intel 0000:00:00.0: Intel 945GME Chipset  
 [    0.952081] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable  
 [    0.952317] agpgart-intel 0000:00:00.0: detected 8192K stolen memory  
 [    0.952575] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000  
 [    0.955730] brd: module loaded  
 [    0.957333] loop: module loaded  
 [    0.957694] ata_piix 0000:00:1f.1: version 2.13  
 [    0.957724] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.957796] ata_piix 0000:00:1f.1: setting latency timer to 64  
 [    0.958534] scsi0 : ata_piix  
 [    0.958769] scsi1 : ata_piix  
 [    0.959607] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x50c0 irq 14  
 [    0.959615] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x50c8 irq 15  
 [    0.959725] ata2: port disabled. ignoring.  
 [    0.960771] Fixed MDIO Bus: probed  
 [    0.960843] PPP generic driver version 2.4.2  
 [    0.960988] tun: Universal TUN/TAP device driver, 1.6  
 [    0.960994] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>  
 [    0.961204] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    0.961248] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.961287] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    0.961295] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    0.961386] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1  
 [    0.961430] ehci_hcd 0000:00:1d.7: using broken periodic workaround  
 [    0.961449] ehci_hcd 0000:00:1d.7: debug port 1  
 [    0.965344] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported  
 [    0.965386] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x56444400  
 [    0.980034] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    0.980330] hub 1-0:1.0: USB hub found  
 [    0.980343] hub 1-0:1.0: 8 ports detected  
 [    0.980521] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    0.980557] uhci_hcd: USB Universal Host Controller Interface driver  
 [    0.980634] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.980649] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    0.980657] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    0.980767] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    0.980813] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000050a0  
 [    0.981118] hub 2-0:1.0: USB hub found  
 [    0.981130] hub 2-0:1.0: 2 ports detected  
 [    0.981282] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.981297] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    0.981305] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    0.981400] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3  
 [    0.981459] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00005080  
 [    0.981758] hub 3-0:1.0: USB hub found  
 [    0.981770] hub 3-0:1.0: 2 ports detected  
 [    0.981898] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    0.981917] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    0.981925] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    0.982023] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4  
 [    0.982088] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005060  
 [    0.982396] hub 4-0:1.0: USB hub found  
 [    0.982408] hub 4-0:1.0: 2 ports detected  
 [    0.982546] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19  
 [    0.982560] uhci_hcd 0000:00:1d.3: setting latency timer to 64  
 [    0.982568] uhci_hcd 0000:00:1d.3: UHCI Host Controller  
 [    0.982658] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5  
 [    0.982717] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00005040  
 [    0.983032] hub 5-0:1.0: USB hub found  
 [    0.983043] hub 5-0:1.0: 2 ports detected  
 [    0.983289] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12  
 [    0.990574] i8042: Detected active multiplexing controller, rev 1.1  
 [    0.993753] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    0.993771] serio: i8042 AUX0 port at 0x60,0x64 irq 12  
 [    0.993855] serio: i8042 AUX1 port at 0x60,0x64 irq 12  
 [    0.993923] serio: i8042 AUX2 port at 0x60,0x64 irq 12  
 [    0.993990] serio: i8042 AUX3 port at 0x60,0x64 irq 12  
 [    0.994305] mousedev: PS/2 mouse device common for all mice  
 [    0.994739] rtc_cmos 00:03: RTC can wake from S4  
 [    0.994933] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0  
 [    0.994979] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs  
 [    0.995238] device-mapper: uevent: version 1.0.3  
 [    0.995446] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]  
 [    0.995529] EISA: Probing bus 0 at eisa.0  
 [    0.995536] EISA: Cannot allocate resource for mainboard  
 [    0.995542] Cannot allocate resource for EISA slot 1  
 [    0.995548] Cannot allocate resource for EISA slot 2  
 [    0.995553] Cannot allocate resource for EISA slot 3  
 [    0.995559] Cannot allocate resource for EISA slot 4  
 [    0.995564] Cannot allocate resource for EISA slot 5  
 [    0.995570] Cannot allocate resource for EISA slot 6  
 [    0.995575] Cannot allocate resource for EISA slot 7  
 [    0.995581] Cannot allocate resource for EISA slot 8  
 [    0.995585] EISA: Detected 0 cards.  
 [    0.995604] cpufreq-nforce2: No nForce2 chipset.  
 [    0.995780] cpuidle: using governor ladder  
 [    0.996092] cpuidle: using governor menu  
 [    0.996098] EFI Variables Facility v0.08 2004-May-17  
 [    0.996774] TCP cubic registered  
 [    0.997176] NET: Registered protocol family 10  
 [    0.998597] NET: Registered protocol family 17  
 [    0.998647] Registering the dns_resolver key type  
 [    0.998690] Using IPI No-Shortcut mode  
 [    0.998946] PM: Hibernation image not present or could not be loaded.  
 [    0.998971] registered taskstats version 1  
 [    1.016572] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4  
 [    1.019238]   Magic number: 7:400:377  
 [    1.019395] rtc_cmos 00:03: setting system clock to 2011-12-05 11:23:11 UTC (1323084191)  
 [    1.020916] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    1.020922] EDD information not available.  
 [    1.112484] Freeing unused kernel memory: 696k freed  
 [    1.112980] Write protecting the kernel text: 5332k  
 [    1.113075] Write protecting the kernel read-only data: 2188k  
 [    1.155578] udevd[83]: starting version 173  
 [    1.292168] usb 1-1: new high speed USB device number 2 using ehci_hcd  
 [    1.395972] ATL1E 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    1.395999] ATL1E 0000:01:00.0: setting latency timer to 64  
 [    1.433074] ahci 0000:00:1f.2: version 3.0  
 [    1.433112] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    1.433228] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X  
 [    1.433324] ahci: SSS flag set, parallel bus scan disabled  
 [    1.433385] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode  
 [    1.433398] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part  
 [    1.433413] ahci 0000:00:1f.2: setting latency timer to 64  
 [    1.449902] scsi2 : ahci  
 [    1.454143] scsi3 : ahci  
 [    1.459474] scsi4 : ahci  
 [    1.464202] scsi5 : ahci  
 [    1.464959] ata3: SATA max UDMA/133 abar m1024@0x56444000 port 0x56444100 irq 43  
 [    1.464970] ata4: DUMMY  
 [    1.464980] ata5: SATA max UDMA/133 abar m1024@0x56444000 port 0x56444200 irq 43  
 [    1.464988] ata6: DUMMY  
 [    1.784154] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  
 [    1.785411] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out  
 [    1.786283] ata3.00: ATA-8: Hitachi HTS543216L9SA00, FB2OC40C, max UDMA/133  
 [    1.786300] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA  
 [    1.787924] ata3.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)  
 [    1.788372] ata3.00: configured for UDMA/133  
 [    1.788718] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5  
 [    1.789265] sd 2:0:0:0: Attached scsi generic sg0 type 0  
 [    1.789727] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)  
 [    1.789992] sd 2:0:0:0: [sda] Write Protect is off  
 [    1.790001] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    1.790105] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.841066]  sda: sda1 sda2 < sda5 >  
 [    1.842133] sd 2:0:0:0: [sda] Attached SCSI disk  
 [    2.108154] ata5: SATA link down (SStatus 0 SControl 300)  
 [    2.541167] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)  
 [    5.427301] usb 1-1: USB disconnect, device number 2  
 [    5.696116] usb 1-1: new high speed USB device number 3 using ehci_hcd  
 [    8.253820] usb 1-1: USB disconnect, device number 3  
 [    8.524114] usb 1-1: new high speed USB device number 4 using ehci_hcd  
 [   11.999061] usb 1-1: USB disconnect, device number 4  
 [   12.268094] usb 1-1: new high speed USB device number 5 using ehci_hcd  
 [   12.955388] udevd[297]: starting version 173  
 [   13.034025] lp: driver loaded but no devices found  
 [   13.037508] Adding 1035260k swap on /dev/sda5.  Priority:-1 extents:1 across:1035260k  
 [   13.225685] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5  
 [   13.226034] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)  
 [   13.267585] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro  
 [   13.268117] [drm] Initialized drm 1.1.0 20060810  
 [   13.326730] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   13.326747] i915 0000:00:02.0: setting latency timer to 64  
 [   13.425923] mtrr: no more MTRRs available  
 [   13.425933] [drm] MTRR allocation failed.  Graphics performance may suffer.  
 [   13.427435] wmi: Mapper loaded  
 [   13.430266] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).  
 [   13.430277] [drm] Driver supports precise vblank timestamp query.  
 [   13.462080] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem  
 [   13.554355] type=1400 audit(1323084204.029:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=422 comm="apparmor_parser"  
 [   13.555914] type=1400 audit(1323084204.029:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=422 comm="apparmor_parser"  
 [   13.556972] type=1400 audit(1323084204.033:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=422 comm="apparmor_parser"  
 [   13.583579] fixme: max PWM is zero.  
 [   13.766361] intel_rng: FWH not detected  
 [   13.825130] leds_ss4200: no LED devices found  
 [   13.853363] [drm] initialized overlay support  
 [   13.936461] fbcon: inteldrmfb (fb0) is primary device  
 [   13.936745] Console: switching to colour frame buffer device 128x37  
 [   13.936827] fb0: inteldrmfb frame buffer device  
 [   13.936834] drm: registered panic notifier  
 [   13.936892] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0  
 [   14.114114] cfg80211: Calling CRDA to update world regulatory domain  
 [   14.492287] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   14.492422] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X  
 [   14.492504] HDA Intel 0000:00:1b.0: setting latency timer to 64  
 [   14.528235] Linux video capture interface: v2.00  
 [   14.556168] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)  
 [   14.577993] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input6  
 [   14.578264] usbcore: registered new interface driver uvcvideo  
 [   14.578273] USB Video Class driver (v1.1.0)  
 [   14.667464] hda_codec: ALC272X: BIOS auto-probing.  
 [   14.679980] ath5k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [   14.680103] ath5k 0000:02:00.0: setting latency timer to 64  
 [   14.684462] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7  
 [   14.684733] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8  
 [   14.704935] ath5k 0000:02:00.0: registered as 'phy0'  
 [   14.870232] ATL1E 0000:01:00.0: irq 45 for MSI/MSI-X  
 [   14.874302] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   15.216700] ath: EEPROM regdomain: 0x65  
 [   15.216710] ath: EEPROM indicates we should expect a direct regpair map  
 [   15.216722] ath: Country alpha2 being used: 00  
 [   15.216728] ath: Regpair used: 0x65  
 [   15.217346] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217359] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217369] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217380] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217389] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217399] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217407] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217418] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217426] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217436] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217445] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217455] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217463] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217474] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217483] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217493] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217501] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217512] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217521] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217532] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217540] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217551] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217560] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217571] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217579] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:  
 [   15.217589] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)  
 [   15.217597] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel  
 [   15.217754] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain  
 [   15.224613] ATL1E 0000:01:00.0: eth0: NIC Link is Up <100 Mbps Full Duplex>  
 [   15.225245] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  
 [   15.230995] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'  
 [   15.242434] Registered led device: ath5k-phy0::rx  
 [   15.247874] Registered led device: ath5k-phy0::tx  
 [   15.247920] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)  
 [   15.331036] type=1400 audit(1323084205.805:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=632 comm="apparmor_parser"  
 [   15.338420] type=1400 audit(1323084205.813:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=633 comm="apparmor_parser"  
 [   15.345567] type=1400 audit(1323084205.821:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=633 comm="apparmor_parser"  
 [   15.346577] type=1400 audit(1323084205.821:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=633 comm="apparmor_parser"  
 [   15.381395] type=1400 audit(1323084205.857:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=634 comm="apparmor_parser"  
 [   15.381711] acerhdf: Acer Aspire One Fan driver, v.0.5.24  
 [   15.381741] acerhdf: unknown (unsupported) BIOS version Acer/AO531h/v0.3110, please report, aborting!  
 [   15.392483] type=1400 audit(1323084205.869:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=637 comm="apparmor_parser"  
 [   15.403134] type=1400 audit(1323084205.877:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=637 comm="apparmor_parser"  
 [   15.534530] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000  
 [   15.579352] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input9  
 [   15.764283] usb 1-1: USB disconnect, device number 5  
 [   16.036161] usb 1-1: new high speed USB device number 6 using ehci_hcd  
 [   16.041136] init: failsafe main process (654) killed by TERM signal  
 [   16.046990] init: apport pre-start process (708) terminated with status 1  
 [   16.143258] init: apport post-stop process (750) terminated with status 1  
 [   16.204365] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)  
 [   16.220848] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input10  
 [   16.508774] acer_wmi: Acer Laptop ACPI-WMI Extras  
 [   16.878968] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain  
 [   16.878982] cfg80211: World regulatory domain updated:  
 [   16.878990] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   16.879001] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   16.879012] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   16.879022] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   16.879032] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   16.879042] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   16.957880] Bluetooth: Core ver 2.16 
 [   16.958110] NET: Registered protocol family 31  
 [   16.958117] Bluetooth: HCI device and connection manager initialized  
 [   16.958127] Bluetooth: HCI socket layer initialized  
 [   16.958133] Bluetooth: L2CAP socket layer initialized  
 [   16.959112] Bluetooth: SCO socket layer initialized  
 [   16.986258] Bluetooth: RFCOMM TTY layer initialized  
 [   16.986362] Bluetooth: RFCOMM socket layer initialized  
 [   16.986370] Bluetooth: RFCOMM ver 1.11  
 [   17.012953] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   17.012963] Bluetooth: BNEP filters: protocol multicast  
 [   17.163877] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [   17.706765] ppdev: user-space parallel port driver  
 [   17.721058] init: anacron main process (742) killed by TERM signal  
 [   18.756165] usb 1-1: USB disconnect, device number 6  
 [   19.036134] usb 1-1: new high speed USB device number 7 using ehci_hcd  
 [   19.209652] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)  
 [   19.225878] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0/input/input11  
 [   19.414170] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600  
 [   19.778330] init: plymouth-stop pre-start process (1192) terminated with status 1  
 [   21.215401] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600  
 [   25.616065] eth0: no IPv6 routers present
 

 **sunonthecross@sunonthecross:~$ sudo lshw -C network ** 
 [sudo] password for sunonthecross:  
   *-network                
        description: Ethernet interface  
        product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:01:00.0  
        logical name: eth0  
        version: b0  
        serial: 00:23:8b:a2:26:b0  
        size: 100Mbit/s  
        capacity: 100Mbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=10.110.182.176 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s  
        resources: irq:45 memory:55200000-5523ffff ioport:3000(size=128)  
   *-network DISABLED  
        description: Wireless interface  
        product: AR242x / AR542x Wireless Network Adapter (PCI-Express)  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 01  
        serial: 00:25:56:7b:98:ea  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=ath5k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg  
        resources: irq:18 memory:54100000-5410ffff  
 

 **sunonthecross@sunonthecross:~$ lsb_release -d ** Description:	Ubuntu 11.10  **sunonthecross@sunonthecross:~$ uname -mr ** 3.0.0-12-generic i686   **sunonthecross@sunonthecross:~$ sudo /etc/init.d/networking restart **  * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces   * Reconfiguring network interfaces...

---

### Post by cozski on 2011-12-09
Anyone?

---

### Post by cozski on 2011-12-11
Is this query likely to get a response? Is there something else I should be doing to help?

---

### Post by praseodym on 2011-12-11
Hi,

disable the hardware encryption of the driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

> [ 15.216722] ath: Country alpha2 being used: [COLOR="Red"]00[/COLOR] 
Which country do you live? There is a bug with the country code settings:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE [COLOR="Red"]# DE for Germany, change it to yours[/COLOR]
```
Check:
```
iwconfig
iwlist chan
sudo iwlist scan
rfkill list
```

---

### Post by cozski on 2011-12-11
I live in Ireland. I don't have a connection to the Internet here at home so I will have to do thisat work tomorrow and let you know. Thanks for the reply.

---

### Post by praseodym on 2011-12-11
Here is the link:

[http://de.archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.19-1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/i/iw/iw_0.9.19-1_i386.deb)

---

### Post by cozski on 2011-12-11
I've tethered my Galaxy to get internet access. I followed your instructions and re-installed iw but this doesn't seem to have fixed it yet.

---

### Post by cozski on 2012-01-02
> **praseodym said:**
> Hi,

disable the hardware encryption of the driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```Which country do you live? There is a bug with the country code settings:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE [COLOR=Red]# DE for Germany, change it to yours[/COLOR]
```Check:
```
iwconfig
iwlist chan
sudo iwlist scan
rfkill list
```

I'm still not able to get the wireless working. I have posted the output from running the checks that you outlined. I installed iw from the link you provided but I'm not sure if I'm supposed to do anything after that... either way, still no wireless options to pick from.

iwconfig

lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 

sunonthecross@sunonthecross:~$ iwlist chan 
lo        no frequency information. 
 
eth0      no frequency information. 
 
wlan0     13 channels in total; available frequencies : 
          Channel 01 : 2.412 GHz 
          Channel 02 : 2.417 GHz 
          Channel 03 : 2.422 GHz 
          Channel 04 : 2.427 GHz 
          Channel 05 : 2.432 GHz 
          Channel 06 : 2.437 GHz 
          Channel 07 : 2.442 GHz 
          Channel 08 : 2.447 GHz 
          Channel 09 : 2.452 GHz 
          Channel 10 : 2.457 GHz 
          Channel 11 : 2.462 GHz 
          Channel 12 : 2.467 GHz 
          Channel 13 : 2.472 GHz 

sunonthecross@sunonthecross:~$ sudo iwlist scan 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wlan0     Interface doesn't support scanning : Network is down 

sunonthecross@sunonthecross:~$ rfkill list 
0: acer-wireless: Wireless LAN 
    Soft blocked: yes 
    Hard blocked: no 
2: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no

---

### Post by wildmanne39 on 2012-01-02
Hi, it shows it is soft blocked you can try this.
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Thanks

---

### Post by cozski on 2012-01-08
> **wildmanne39 said:**
> Hi, it shows it is soft blocked you can try this.
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```Thanks


Hey, thanks for the suggestion but this has not solved the problem either. I've had so many problems with my Acer Aspire Netbook on Ubuntu I think I'm goint to go back to Mint... that seemed to work no problem (although there always appears to be display configuration problems on my netbook, but maybe they've resolved that by now) for my wireless. Disappointed though :(

---

### Post by praseodym on 2012-01-08
Did you try

> sudo rfkill unblock all

?

---

### Post by wildmanne39 on 2012-01-08
Hi, > I'm goint to go back to Mint...if you change your mind we have a few other idea's like turning off power management for one.
Thanks

---

### Post by bdr117 on 2012-01-08
I have acer travelmate2420 had problems detecting wireless card and no connection, 1st i went to: [http://www.linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://www.linuxwireless.org/en/users/Drivers/b43#Supported_devices)  (to check if it was a supported device)
Then type this command in the terminal( lspci -vnn | grep 14e4)  and follow the next set of instructions to interpret your terminal readout   I then downloaded the b43-fwcutter file on my wired internet connection)   [http://packages.ubuntu.com/hardy/i386/b43-fwcutter/download](http://packages.ubuntu.com/hardy/i386/b43-fwcutter/download)
Then Download the file , don't save ...... set to open with g deb package manager,installer etc.
a separate window will open check the box next to find and install firmware as well ( It doesn't say that exactly but you get my drift) then click the appropriate button at the bottom of the box that basiclly means yes and your set let it do its job and when it is done restart your computer.....
botta bing ...
If it is working you don't need to do much, the bar at the top of your computer has a network symbal click on it and it should show you all of the avalable wireless networks. ( ps i unpluged my wired internet connection when i restarted my computer)  my wireless now works better than it ever did with winxp
b43-fwcutter can also be obtained by going to synaptic package manager.  Hope this helps yawl out just a little.   :popcorn::popcorn:

---

### Post by cozski on 2012-01-09
> **wildmanne39 said:**
> Hi, if you change your mind we have a few other idea's like turning off power management for one.
Thanks

I'm trying the suggestion above first but if that doesn't work should I just turn my netbook off? What do I do then? Is there something I can do when I'm rebooting? Thanks.

---

### Post by wildmanne39 on 2012-01-09
Hi, which one are you trying? bdr117 suggestion is not for your wireless card please do not do it.
Thanks

---

### Post by wildmanne39 on 2012-01-09
Hi, please try this:
```
gksudo gedit /etc/pm/power.d/wireless
```
```
#!/bin/sh

/sbin/iwconfig wlan0 power off

```
save, exit gedit and reboot.
Thanks

---

### Post by cozski on 2012-01-09
> **wildmanne39 said:**
> Hi, which one are you trying? bdr117 suggestion is not for your wireless card please do not do it.
Thanks

Ah, didn't do it... couldn't get the command to output whether or not my card was on the list. Ditched Ubuntu on my netbook and installed Jolicloud... thanks for the suggestions though.

---

### Post by wildmanne39 on 2012-01-09
Hi, ok your welcome!

---

### Post by cozski on 2012-01-09
[QUOTE=wildmanne39;11599463]Hi, ok your welcome![/QUOT

... so it wasn't working with Jolicloud either but i thought i'd try your last suggestion and it worked great! So definite thanks for that... Appreciated!

---

### Post by wildmanne39 on 2012-01-09
Hi, your welcome! I am glad it worked, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

