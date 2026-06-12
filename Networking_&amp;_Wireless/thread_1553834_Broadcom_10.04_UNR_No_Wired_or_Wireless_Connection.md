---
title: "Broadcom/ 10.04 UNR/ No Wired or Wireless Connection"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by V13 Noob on 2010-08-15
Hello, I've been having major problems with my wired and wireless connection in Ubuntu 10.04 Netbook remix. When I plug an ethernet cable, nothing is recognized in the network manager, nor when unplugged does the wireless detect anything. The router and signal work though, as I am using my desktop to post this and have another laptop running Windows that uses the WiFi signal. I have tried several methods with no success and the only reason I want to keep trying is because I've had Ubuntu on my desktop for about 2 weeks now so Im new to linux but can tell its far better than Windows, but I'm afraid if I can't use the WiFi, or ethernet at least, I would be forced to use Windows. I've also tried Crashbang on it because I read it had better broadcom support out of the box but the best it would do is turn the WiFi light on but with the exact symptoms as Ubuntu and I'd rather struggle to get Ubuntu up and running, no offense to #!

I looked at the how to post guide and here are the terminal results I got

I have an Acer Aspire One 721 - doesn't have an optical drive  so any install would have to be via usb

It says broadcom 4357 but as far as I've found browsing the net and these forums, its the same as BCM43225

Any aid you can lend would be life saving. Thanks for looking.

[COLOR=Red]lspci -nn:[/COLOR]
                                 
aaron@aaron-laptop:~$ lspci -nn  
 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]  
 00:01.0 PCI bridge [0604]: Acer Incorporated [ALI] Device [1025:9602]  
 00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604] 
 00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605] 
 00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]  
 00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]  
 00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]  
 00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]  
 00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]  
 00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)  
 00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (rev 40)  
 00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)  
 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40) 
 00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)  
 00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]  
 00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]  
 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]  
 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]  
 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]  
 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]  
 00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]  
 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]  
 01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]  
 03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)  
 06:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01) 

[COLOR=Red]ifconfig:[/COLOR]
                                  
aaron@aaron-laptop:~$ ifconfig  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:68 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:68 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:5360 (5.3 KB)  TX bytes:5360 (5.3 KB)  
 
[COLOR=Red]iwconfig:[/COLOR]

aaron@aaron-laptop:~$ iwconfig  
 lo        no wireless extensions. 

[COLOR=Red]lsmod:[/COLOR]
                                  
aaron@aaron-laptop:~$ lsmod  
 Module                  Size  Used by  
 binfmt_misc             6587  1  
 ppdev                   5259  0  
 snd_hda_codec_atihdmi     2367  1  
 snd_hda_codec_realtek   203168  1  
 fbcon                  35102  71  
 tileblit                2031  1 fbcon  
 font                    7557  1 fbcon  
 bitblit                 4707  1 fbcon  
 snd_hda_intel          21877  2  
 softcursor              1189  1 bitblit 
 snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel  
 vga16fb                11385  0  
 vgastate                8961  1 vga16fb 
 snd_hwdep               5412  1 snd_hda_codec  
 snd_pcm_oss            35308  0  
 joydev                  8708  0  
 snd_mixer_oss          13746  1 snd_pcm_oss  
 radeon                674135  4  
 snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           1338  0  
 ttm                    49943  1 radeon  
 snd_seq_oss            26726  0  
 snd_seq_midi            4557  0  
 drm_kms_helper         29297  1 radeon  
 snd_rawmidi            19056  1 snd_seq_midi  
 drm                   162471  6 radeon,ttm,drm_kms_helper  
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  
 agpgart                31724  2 ttm,drm 
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              19098  2 snd_pcm,snd_seq  
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 psmouse                63245  0  
 i2c_algo_bit            5028  1 radeon  
 video                  17375  0  
 snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i2c_piix4               8335  0  
 uvcvideo               56990  0  
 shpchp                 28820  0  
 soundcore               6620  1 snd  
 acer_wmi               13861  0  
 snd_page_alloc          7076  2 snd_hda_intel,snd_pcm  
 lp                      7028  0  
 videodev               34361  1 uvcvideo  
 output                  1871  1 video  
 serio_raw               3978  0  
 parport                32635  2 ppdev,lp  
 v4l1_compat            13251  2 uvcvideo,videodev  
 led_class               2864  1 acer_wmi  
 usb_storage            39425  0  
 pata_atiixp             3148  0  
 ahci                   32008  2 

[COLOR=Red]dmsg:[/COLOR]
                                  
[    0.004171] Initializing cgroup subsys cpuacct  
 [    0.004175] Initializing cgroup subsys memory  
 [    0.004183] Initializing cgroup subsys devices  
 [    0.004186] Initializing cgroup subsys freezer  
 [    0.004189] Initializing cgroup subsys net_cls  
 [    0.004207] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)  
 [    0.004210] CPU: L2 Cache: 1024K (64 bytes/line)  
 [    0.004215] mce: CPU supports 6 MCE banks  
 [    0.004228] using C1E aware idle routine  
 [    0.004235] Performance Events: AMD PMU driver.  
 [    0.004241] ... version:                0  
 [    0.004243] ... bit width:              48  
 [    0.004245] ... generic registers:      4  
 [    0.004247] ... value mask:             0000ffffffffffff  
 [    0.004250] ... max period:             00007fffffffffff  
 [    0.004252] ... fixed-purpose events:   0  
 [    0.004254] ... event mask:             000000000000000f  
 [    0.004259] Checking 'hlt' instruction... OK.  
 [    0.020682] SMP alternatives: switching to UP code  
 [    0.027237] Freeing SMP alternatives: 19k freed  
 [    0.027248] ACPI: Core revision 20090903  
 [    0.052010] ftrace: converting mcount calls to 0f 1f 44 00 00  
 [    0.052014] ftrace: allocating 21771 entries in 43 pages  
 [    0.056095] Enabling APIC mode:  Flat.  Using 1 I/O APICs  
 [    0.056407] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1  
 [    0.097114] CPU0: AMD Athlon(tm) II Neo K125 Processor stepping 03  
 [    0.100001] Brought up 1 CPUs  
 [    0.100001] Total of 1 processors activated (3390.65 BogoMIPS).  
 [    0.100001] CPU0 attaching NULL sched-domain.  
 [    0.100001] devtmpfs: initialized  
 [    0.100001] regulator: core version 0.5  
 [    0.100001] Time:  8:02:08  Date: 08/15/10  
 [    0.100001] NET: Registered protocol family 16  
 [    0.100001] EISA bus registered  
 [    0.100001] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it  
 [    0.100001] ACPI: bus type pci registered  
 [    0.100001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6  
 [    0.100001] PCI: Not using MMCONFIG. 
 [    0.100001] PCI: PCI BIOS revision 2.10 entry at 0xfd9ba, last bus=7  
 [    0.100001] PCI: Using configuration type 1 for base access  
 [    0.100001] PCI: Using configuration type 1 for extended access  
 [    0.100001] bio: create slab <bio-0> at 0  
 [    0.100001] ACPI: EC: Look up EC in DSDT  
 [    0.100772] ACPI Warning for \_SB_._OSC: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)  
 [    0.100781] \_SB_:_OSC evaluation returned wrong type  
 [    0.100783] _OSC request data:1 7  
 [    0.107502] ACPI: BIOS _OSI(Linux) query ignored  
 [    0.108292] ACPI: OEMN 6feadd60 00024 (v01 AMD    NAHP     00000001 MSFT 03000001)  
 [    0.109075] System has AMD C1E enabled  
 [    0.109086] Switch to broadcast mode on CPU0  
 [    0.124211] ACPI: Interpreter enabled  
 [    0.124211] ACPI: (supports S0 S3 S4 S5)  
 [    0.124211] ACPI: Using IOAPIC for interrupt routing  
 [    0.124568] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 6  
 [    0.133164] PCI: BIOS Bug: MCFG area at e0000000 is not reserved in ACPI motherboard resources  
 [    0.133169] PCI: Not using MMCONFIG. 
 [    0.140440] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62  
 [    0.144133] ACPI: No dock devices found.  
 [    0.145991] ACPI: PCI Root Bridge [PCI0] (0000:00)  
 [    0.146154] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold  
 [    0.146159] pci 0000:00:04.0: PME# disabled  
 [    0.146204] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold  
 [    0.146208] pci 0000:00:05.0: PME# disabled  
 [    0.146280] pci 0000:00:11.0: reg 10 io port: [0x8440-0x8447]  
 [    0.146288] pci 0000:00:11.0: reg 14 io port: [0x8430-0x8433]  
 [    0.146296] pci 0000:00:11.0: reg 18 io port: [0x8420-0x8427]  
 [    0.146304] pci 0000:00:11.0: reg 1c io port: [0x8410-0x8413]  
 [    0.146311] pci 0000:00:11.0: reg 20 io port: [0x8400-0x840f]  
 [    0.146319] pci 0000:00:11.0: reg 24 32bit mmio: [0xd0607c00-0xd0607fff]  
 [    0.146386] pci 0000:00:12.0: reg 10 32bit mmio: [0xd0404000-0xd0404fff]  
 [    0.146463] pci 0000:00:12.2: reg 10 32bit mmio: [0xd0607000-0xd06070ff]  
 [    0.146517] pci 0000:00:12.2: supports D1 D2  
 [    0.146519] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot  
 [    0.146524] pci 0000:00:12.2: PME# disabled  
 [    0.146557] pci 0000:00:13.0: reg 10 32bit mmio: [0xd0405000-0xd0405fff]  
 [    0.146633] pci 0000:00:13.2: reg 10 32bit mmio: [0xd0607400-0xd06074ff]  
 [    0.146687] pci 0000:00:13.2: supports D1 D2  
 [    0.146690] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot  
 [    0.146694] pci 0000:00:13.2: PME# disabled  
 [    0.146779] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]  
 [    0.146787] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]  
 [    0.146795] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]  
 [    0.146802] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]  
 [    0.146809] pci 0000:00:14.1: reg 20 io port: [0x8450-0x845f]  
 [    0.146864] pci 0000:00:14.2: reg 10 64bit mmio: [0xd0400000-0xd0403fff]  
 [    0.146909] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold  
 [    0.146914] pci 0000:00:14.2: PME# disabled  
 [    0.147028] pci 0000:00:16.0: reg 10 32bit mmio: [0xd0406000-0xd0406fff]  
 [    0.147104] pci 0000:00:16.2: reg 10 32bit mmio: [0xd0607800-0xd06078ff]  
 [    0.147158] pci 0000:00:16.2: supports D1 D2  
 [    0.147160] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot  
 [    0.147165] pci 0000:00:16.2: PME# disabled  
 [    0.147302] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc0000000-0xcfffffff]  
 [    0.147307] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]  
 [    0.147313] pci 0000:01:05.0: reg 18 32bit mmio: [0xd0100000-0xd010ffff]  
 [    0.147322] pci 0000:01:05.0: reg 24 32bit mmio: [0xd0000000-0xd00fffff]  
 [    0.147338] pci 0000:01:05.0: supports D1 D2  
 [    0.147361] pci 0000:01:05.1: reg 10 32bit mmio: [0xd0110000-0xd0113fff]  
 [    0.147387] pci 0000:01:05.1: supports D1 D2  
 [    0.147435] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]  
 [    0.147438] pci 0000:00:01.0: bridge 32bit mmio: [0xd0000000-0xd01fffff]  
 [    0.147444] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]  
 [    0.147494] pci 0000:03:00.0: reg 10 64bit mmio: [0xd0200000-0xd023ffff]  
 [    0.147503] pci 0000:03:00.0: reg 18 io port: [0xa000-0xa07f]  
 [    0.147563] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold  
 [    0.147568] pci 0000:03:00.0: PME# disabled  
 [    0.147633] pci 0000:00:04.0: bridge io port: [0xa000-0xafff]  
 [    0.147637] pci 0000:00:04.0: bridge 32bit mmio: [0xd0200000-0xd02fffff]  
 [    0.147721] pci 0000:06:00.0: reg 10 64bit mmio: [0xd0300000-0xd0303fff]  
 [    0.147782] pci 0000:06:00.0: supports D1 D2  
 [    0.147784] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold  
 [    0.147789] pci 0000:06:00.0: PME# disabled  
 [    0.147860] pci 0000:00:05.0: bridge 32bit mmio: [0xd0300000-0xd03fffff]  
 [    0.147921] pci 0000:00:14.4: transparent bridge  
 [    0.147944] pci_bus 0000:00: on NUMA node 0  
 [    0.147948] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]  
 [    0.148225] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]  
 [    0.148315] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]  
 [    0.148458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]  
 [    0.148582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]  
 [    0.154358] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0  
 [    0.154577] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0  
 [    0.154803] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0  
 [    0.155031] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0  
 [    0.155239] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0  
 [    0.155392] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0  
 [    0.155549] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0  
 [    0.155702] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0  
 [    0.155829] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none  
 [    0.155833] vgaarb: loaded  
 [    0.155948] SCSI subsystem initialized  
 [    0.156007] libata version 3.00 loaded.  
 [    0.156069] usbcore: registered new interface driver usbfs  
 [    0.156081] usbcore: registered new interface driver hub  
 [    0.156101] usbcore: registered new device driver usb  
 [    0.156252] ACPI: WMI: Mapper loaded 
 [    0.156254] PCI: Using ACPI for IRQ routing  
 [    0.156580] NetLabel: Initializing  
 [    0.156582] NetLabel:  domain hash size = 128  
 [    0.156584] NetLabel:  protocols = UNLABELED CIPSOv4  
 [    0.156597] NetLabel:  unlabeled traffic allowed by default  
 [    0.156626] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0  
 [    0.156631] hpet0: 3 comparators, 32-bit 14.318180 MHz counter  
 [    0.158643] Switching to clocksource tsc  
 [    0.160001] AppArmor: AppArmor Filesystem Enabled  
 [    0.160001] pnp: PnP ACPI init  
 [    0.160001] ACPI: bus type pnp registered  
 [    0.161123] pnp: PnP ACPI: found 10 devices  
 [    0.161125] ACPI: ACPI bus type pnp unregistered  
 [    0.161129] PnPBIOS: Disabled by ACPI PNP  
 [    0.161139] system 00:01: ioport range 0xf50-0xf51 has been reserved  
 [    0.161144] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved  
 [    0.161147] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved  
 [    0.161155] system 00:06: ioport range 0x220-0x22f has been reserved  
 [    0.161159] system 00:06: ioport range 0x40b-0x40b has been reserved  
 [    0.161162] system 00:06: ioport range 0x4d0-0x4d1 has been reserved  
 [    0.161165] system 00:06: ioport range 0x4d6-0x4d6 has been reserved  
 [    0.161168] system 00:06: ioport range 0x530-0x537 has been reserved  
 [    0.161171] system 00:06: ioport range 0xc00-0xc01 has been reserved  
 [    0.161174] system 00:06: ioport range 0xc14-0xc14 has been reserved  
 [    0.161177] system 00:06: ioport range 0xc50-0xc52 has been reserved  
 [    0.161181] system 00:06: ioport range 0xc6c-0xc6c has been reserved  
 [    0.161184] system 00:06: ioport range 0xc6f-0xc6f has been reserved  
 [    0.161187] system 00:06: ioport range 0xcd0-0xcd1 has been reserved  
 [    0.161190] system 00:06: ioport range 0xcd2-0xcd3 has been reserved  
 [    0.161193] system 00:06: ioport range 0xcd4-0xcd5 has been reserved  
 [    0.161196] system 00:06: ioport range 0xcd6-0xcd7 has been reserved  
 [    0.161200] system 00:06: ioport range 0xcd8-0xcdf has been reserved  
 [    0.161203] system 00:06: ioport range 0x8000-0x805f has been reserved  
 [    0.161206] system 00:06: ioport range 0xf40-0xf47 has been reserved  
 [    0.161210] system 00:06: ioport range 0x87f-0x87f has been reserved  
 [    0.161213] system 00:06: iomem range 0xff800000-0xff800fff has been reserved  
 [    0.161220] system 00:07: iomem range 0xe0000-0xfffff could not be reserved  
 [    0.161223] system 00:07: iomem range 0xffe00000-0xffffffff could not be reserved  
 [    0.161227] system 00:07: iomem range 0xfec10000-0xfec1001f has been reserved  
 [    0.161230] system 00:07: iomem range 0xfed00000-0xfed003ff has been reserved  
 [    0.161234] system 00:07: iomem range 0xfed61000-0xfed613ff has been reserved  
 [    0.161237] system 00:07: iomem range 0xfed80000-0xfed80fff has been reserved  
 [    0.196022] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01  
 [    0.196026] pci 0000:00:01.0:   IO window: 0x9000-0x9fff  
 [    0.196030] pci 0000:00:01.0:   MEM window: 0xd0000000-0xd01fffff  
 [    0.196035] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff  
 [    0.196040] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03  
 [    0.196043] pci 0000:00:04.0:   IO window: 0xa000-0xafff  
 [    0.196047] pci 0000:00:04.0:   MEM window: 0xd0200000-0xd02fffff  
 [    0.196050] pci 0000:00:04.0:   PREFETCH window: disabled  
 [    0.196055] pci 0000:00:05.0: PCI bridge, secondary bus 0000:06  
 [    0.196057] pci 0000:00:05.0:   IO window: disabled  
 [    0.196061] pci 0000:00:05.0:   MEM window: 0xd0300000-0xd03fffff  
 [    0.196064] pci 0000:00:05.0:   PREFETCH window: disabled  
 [    0.196069] pci 0000:00:14.4: PCI bridge, secondary bus 0000:07  
 [    0.196071] pci 0000:00:14.4:   IO window: disabled  
 [    0.196077] pci 0000:00:14.4:   MEM window: disabled  
 [    0.196081] pci 0000:00:14.4:   PREFETCH window: disabled  
 [    0.196098]   alloc irq_desc for 16 on node -1  
 [    0.196100]   alloc kstat_irqs on node -1  
 [    0.196106] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.196110] pci 0000:00:04.0: setting latency timer to 64  
 [    0.196116]   alloc irq_desc for 17 on node -1  
 [    0.196118]   alloc kstat_irqs on node -1  
 [    0.196121] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [    0.196125] pci 0000:00:05.0: setting latency timer to 64  
 [    0.196134] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]  
 [    0.196137] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]  
 [    0.196140] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]  
 [    0.196143] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd01fffff]  
 [    0.196146] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]  
 [    0.196149] pci_bus 0000:03: resource 0 io:  [0xa000-0xafff]  
 [    0.196152] pci_bus 0000:03: resource 1 mem: [0xd0200000-0xd02fffff]  
 [    0.196155] pci_bus 0000:06: resource 1 mem: [0xd0300000-0xd03fffff]  
 [    0.196158] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]  
 [    0.196161] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffff]  
 [    0.196198] NET: Registered protocol family 2  
 [    0.196296] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)  
 [    0.196639] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)  
 [    0.197316] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)  
 [    0.197698] TCP: Hash tables configured (established 131072 bind 65536)  
 [    0.197701] TCP reno registered  
 [    0.197794] NET: Registered protocol family 1  
 [    0.261464] pci 0000:01:05.0: Boot video device  
 [    0.261664] cpufreq-nforce2: No nForce2 chipset.  
 [    0.261690] Scanning for low memory corruption every 60 seconds  
 [    0.261789] audit: initializing netlink socket (disabled)  
 [    0.261803] type=2000 audit(1281859326.261:1): initialized  
 [    0.272226] Trying to unpack rootfs image as initramfs...  
 [    0.285563] highmem bounce pool size: 64 pages  
 [    0.285569] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    0.287073] VFS: Disk quotas dquot_6.5.2  
 [    0.287132] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    0.293684] fuse init (API version 7.13)  
 [    0.293785] msgmni has been set to 1696  
 [    0.293993] alg: No test for stdrng (krng)  
 [    0.294049] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)  
 [    0.294053] io scheduler noop registered  
 [    0.294055] io scheduler anticipatory registered  
 [    0.294057] io scheduler deadline registered  
 [    0.294100] io scheduler cfq registered (default)  
 [    0.294241]   alloc irq_desc for 24 on node -1  
 [    0.294243]   alloc kstat_irqs on node -1  
 [    0.294253] pcieport 0000:00:04.0: irq 24 for MSI/MSI-X  
 [    0.294260] pcieport 0000:00:04.0: setting latency timer to 64  
 [    0.294349]   alloc irq_desc for 25 on node -1  
 [    0.294351]   alloc kstat_irqs on node -1  
 [    0.294356] pcieport 0000:00:05.0: irq 25 for MSI/MSI-X  
 [    0.294362] pcieport 0000:00:05.0: setting latency timer to 64  
 [    0.294426] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.294448] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.296362] ACPI: AC Adapter [ADP1] (off-line)  
 [    0.296424] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0  
 [    0.296428] ACPI: Power Button [PWRB]  
 [    0.296485] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1  
 [    0.298534] ACPI: Lid Switch [LID0]  
 [    0.298579] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2  
 [    0.298588] ACPI: Sleep Button [SLPB]  
 [    0.298628] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3  
 [    0.298631] ACPI: Power Button [PWRF]  
 [    0.298888] ACPI: processor limited to max C-state 1  
 [    0.298911] processor LNXCPU:00: registered as cooling_device0  
 [    0.322356] thermal LNXTHERM:01: registered as thermal_zone0  
 [    0.322368] ACPI: Thermal Zone [TZS0] (59 C)  
 [    0.329281] thermal LNXTHERM:02: registered as thermal_zone1  
 [    0.329291] ACPI: Thermal Zone [TZS1] (59 C)  
 [    0.330684] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled  
 [    0.331893] brd: module loaded  
 [    0.332326] loop: module loaded  
 [    0.332404] input: Macintosh mouse button emulation as /devices/virtual/input/input4  
 [    0.332567] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.332888] Fixed MDIO Bus: probed  
 [    0.332920] PPP generic driver version 2.4.2  
 [    0.332952] tun: Universal TUN/TAP device driver, 1.6  
 [    0.332954] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>  
 [    0.333022] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    0.333074] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.333094] ehci_hcd 0000:00:12.2: EHCI Host Controller  
 [    0.333122] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1  
 [    0.333155] ehci_hcd 0000:00:12.2: debug port 1  
 [    0.333181] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd0607000  
 [    0.338047] isapnp: Scanning for PnP cards...  
 [    0.343728] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00  
 [    0.343826] usb usb1: configuration #1 chosen from 1 choice  
 [    0.343854] hub 1-0:1.0: USB hub found  
 [    0.343863] hub 1-0:1.0: 5 ports detected  
 [    0.343924] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.343941] ehci_hcd 0000:00:13.2: EHCI Host Controller  
 [    0.343976] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2  
 [    0.344006] ehci_hcd 0000:00:13.2: debug port 1  
 [    0.344023] ehci_hcd 0000:00:13.2: irq 17, io mem 0xd0607400  
 [    0.396452] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00  
 [    0.396530] usb usb2: configuration #1 chosen from 1 choice  
 [    0.396555] hub 2-0:1.0: USB hub found  
 [    0.396561] hub 2-0:1.0: 5 ports detected  
 [    0.396617] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    0.396629] ehci_hcd 0000:00:16.2: EHCI Host Controller  
 [    0.396657] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3  
 [    0.396684] ehci_hcd 0000:00:16.2: debug port 1  
 [    0.396699] ehci_hcd 0000:00:16.2: irq 17, io mem 0xd0607800  
 [    0.405447] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00  
 [    0.405557] usb usb3: configuration #1 chosen from 1 choice  
 [    0.405586] hub 3-0:1.0: USB hub found  
 [    0.405596] hub 3-0:1.0: 4 ports detected  
 [    0.405685] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    0.405708]   alloc irq_desc for 18 on node -1  
 [    0.405710]   alloc kstat_irqs on node -1  
 [    0.405717] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    0.405739] ohci_hcd 0000:00:12.0: OHCI Host Controller  
 [    0.405778] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4  
 [    0.405812] ohci_hcd 0000:00:12.0: irq 18, io mem 0xd0404000  
 [    0.503381] usb usb4: configuration #1 chosen from 1 choice  
 [    0.503416] hub 4-0:1.0: USB hub found  
 [    0.503463] hub 4-0:1.0: 5 ports detected  
 [    0.503523] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    0.503546] ohci_hcd 0000:00:13.0: OHCI Host Controller  
 [    0.503586] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5  
 [    0.503613] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd0405000  
 [    0.603447] usb usb5: configuration #1 chosen from 1 choice  
 [    0.603482] hub 5-0:1.0: USB hub found  
 [    0.603498] hub 5-0:1.0: 5 ports detected  
 [    0.603561] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    0.603584] ohci_hcd 0000:00:16.0: OHCI Host Controller  
 [    0.603623] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6  
 [    0.603649] ohci_hcd 0000:00:16.0: irq 18, io mem 0xd0406000  
 [    0.630828] ACPI: Battery Slot [BAT0] (battery present)  
 [    0.698111] usb 1-1: new high speed USB device using ehci_hcd and address 2  
 [    0.705935] usb usb6: configuration #1 chosen from 1 choice  
 [    0.705966] hub 6-0:1.0: USB hub found  
 [    0.706013] hub 6-0:1.0: 4 ports detected  
 [    0.706075] uhci_hcd: USB Universal Host Controller Interface driver  
 [    0.706162] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12  
 [    0.730382] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    0.730395] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    0.730549] mice: PS/2 mouse device common for all mice  
 [    0.731148] rtc_cmos 00:04: RTC can wake from S4  
 [    0.731190] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0  
 [    0.731220] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs  
 [    0.731350] device-mapper: uevent: version 1.0.3  
 [    0.733611] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  
 [    0.734721] device-mapper: multipath: version 1.1.0 loaded  
 [    0.734725] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    0.737115] EISA: Probing bus 0 at eisa.0  
 [    0.737184] Cannot allocate resource for EISA slot 8  
 [    0.737187] EISA: Detected 0 cards.  
 [    0.739926] cpuidle: using governor ladder  
 [    0.739928] cpuidle: using governor menu  
 [    0.740371] TCP cubic registered  
 [    0.740524] NET: Registered protocol family 10  
 [    0.740982] lo: Disabled Privacy Extensions  
 [    0.741312] NET: Registered protocol family 17  
 [    0.741340] powernow-k8: Found 1 AMD Athlon(tm) II Neo K125 Processor processors (1 cpu cores) (version 2.20.00)  
 [    0.741381] powernow-k8:    0 : pstate 0 (1700 MHz)  
 [    0.741383] powernow-k8:    1 : pstate 1 (1300 MHz)  
 [    0.741386] powernow-k8:    2 : pstate 2 (800 MHz)  
 [    0.741426] Using IPI No-Shortcut mode  
 [    0.741521] PM: Resume from disk failed.  
 [    0.741535] registered taskstats version 1  
 [    0.741910]   Magic number: 6:945:17 
 [    0.742054] rtc_cmos 00:04: setting system clock to 2010-08-15 08:02:08 UTC (1281859328)  
 [    0.742058] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    0.742060] EDD information not available.  
 [    0.757334] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5  
 [    0.760850] Freeing initrd memory: 7767k freed  
 [    0.947722] isapnp: No Plug & Play device found  
 [    0.947751] Freeing unused kernel memory: 656k freed  
 [    0.948198] Write protecting the kernel text: 4676k  
 [    0.948231] Write protecting the kernel read-only data: 1840k  
 [    0.952725] usb 1-1: configuration #1 chosen from 1 choice  
 [    0.964532] udev: starting version 151  
 [    1.060069] usb 1-5: new high speed USB device using ehci_hcd and address 3  
 [    1.203735] scsi0 : pata_atiixp  
 [    1.203873] scsi1 : pata_atiixp  
 [    1.203912] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8450 irq 14  
 [    1.203916] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8458 irq 15  
 [    1.204060] ahci 0000:00:11.0: version 3.0  
 [    1.204073]   alloc irq_desc for 19 on node -1  
 [    1.204075]   alloc kstat_irqs on node -1  
 [    1.204082] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19  
 [    1.204121]   alloc irq_desc for 26 on node -1  
 [    1.204123]   alloc kstat_irqs on node -1  
 [    1.204133] ahci 0000:00:11.0: irq 26 for MSI/MSI-X  
 [    1.204187] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 1 ports 6 Gbps 0x1 impl SATA mode  
 [    1.204191] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part  
 [    1.204555] Initializing USB Mass Storage driver...  
 [    1.204614] scsi2 : ahci  
 [    1.204736] ata3: SATA max UDMA/133 abar m1024@0xd0607c00 port 0xd0607d00 irq 26  
 [    1.204877] scsi3 : SCSI emulation for USB Mass Storage devices  
 [    1.204974] usbcore: registered new interface driver usb-storage  
 [    1.204977] USB Mass Storage support registered.  
 [    1.205043] usb-storage: device found at 2  
 [    1.205045] usb-storage: waiting for device to settle before scanning  
 [    1.450941] usb 1-5: configuration #1 chosen from 1 choice  
 [    1.456876] scsi4 : SCSI emulation for USB Mass Storage devices  
 [    1.457157] usb-storage: device found at 3  
 [    1.457159] usb-storage: waiting for device to settle before scanning  
 [    1.568100] usb 2-5: new high speed USB device using ehci_hcd and address 2  
 [    1.696100] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  
 [    1.697317] ata3.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133  
 [    1.697322] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA  
 [    1.698677] ata3.00: configured for UDMA/133  
 [    1.712171] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5  
 [    1.712338] sd 2:0:0:0: Attached scsi generic sg0 type 0  
 [    1.712562] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)  
 [    1.712602] sd 2:0:0:0: [sda] Write Protect is off  
 [    1.712605] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    1.712626] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.712753]  sda:  
 [    1.732707] usb 2-5: configuration #1 chosen from 1 choice  
 [    1.745475]  sda1 sda2 < sda5 > 
 [    1.770589] sd 2:0:0:0: [sda] Attached SCSI disk  
 [    2.125393] EXT4-fs (sda1): mounted filesystem with ordered data mode  
 [    3.820946] Adding 5275640k swap on /dev/sda5.  Priority:-1 extents:1 across:5275640k  
 [    4.303867] udev: starting version 151  
 [    5.830192] Linux video capture interface: v2.00  
 [    5.957343] lp: driver loaded but no devices found  
 [    6.009141] acer-wmi: Acer Laptop ACPI-WMI Extras  
 [    6.010088] acer-wmi: Brightness must be controlled by generic video driver  
 [    6.018648] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4  
 [    6.037287] uvcvideo: Found UVC 1.00 device 1.3M WebCam (04f2:b1d8)  
 [    6.047252] input: 1.3M WebCam as /devices/pci0000:00/0000:00:13.2/usb2/2-5/2-5:1.0/input/input6  
 [    6.047404] usbcore: registered new interface driver uvcvideo  
 [    6.048037] USB Video Class driver (v0.1.0)  
 [    6.049339] ACPI: resource piix4_smbus [0x8040-0x8047] conflicts with ACPI region SMB0 [0x8040-0x804f]  
 [    6.049342] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver  
 [    6.148136] acpi device:40: registered as cooling_device1  
 [    6.151087] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:3e/LNXVIDEO:02/input/input7 
 [    6.151237] ACPI: Video Device [VGA2] (multi-head: yes  rom: no  post: no)  
 [    6.207025] usb-storage: device scan complete  
 [    6.207990] scsi 3:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ: 0 ANSI: 0 CCS  
 [    6.210552] sd 3:0:0:0: Attached scsi generic sg1 type 0  
 [    6.217822] sd 3:0:0:0: [sdb] Attached SCSI removable disk  
 [    6.225898] Linux agpgart interface v0.103  
 [    6.349442] [drm] Initialized drm 1.1.0 20060810  
 [    6.456393] usb-storage: device scan complete  
 [    6.458889] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS  
 [    6.460798] sd 4:0:0:0: Attached scsi generic sg2 type 0  
 [    6.471699] sd 4:0:0:0: [sdc] Attached SCSI removable disk  
 [    6.908741] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1c0b1, caps: 0xd04771/0xa40000  
 [    6.976799] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8  
 [    7.050380] type=1505 audit(1281859334.806:2):  operation="profile_load" pid=516 name="/sbin/dhclient3"  
 [    7.050705] type=1505 audit(1281859334.806:3):  operation="profile_load" pid=516 name="/usr/lib/NetworkManager/nm-dhcp-client.action"  
 [    7.050886] type=1505 audit(1281859334.806:4):  operation="profile_load" pid=516 name="/usr/lib/connman/scripts/dhclient-script"  
 [    7.441043] [drm] radeon defaulting to kernel modesetting.  
 [    7.441048] [drm] radeon kernel modesetting enabled.  
 [    7.441131] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    7.441137] radeon 0000:01:05.0: setting latency timer to 64  
 [    7.449504] [drm] radeon: Initializing kernel modesetting.  
 [    7.452213] [drm] register mmio base: 0xD0100000  
 [    7.452216] [drm] register mmio size: 65536  
 [    7.452312] ATOM BIOS: Acer_SJV10NL  
 [    7.452330] [drm] Clocks initialized !  
 [    7.452510] [drm] Detected VRAM RAM=256M, BAR=256M  
 [    7.452515] [drm] RAM width 32bits DDR  
 [    7.454500] [TTM] Zone  kernel: Available graphics memory: 438634 kiB.  
 [    7.454504] [TTM] Zone highmem: Available graphics memory: 900750 kiB.  
 [    7.454519] [drm] radeon: 256M of VRAM memory ready  
 [    7.454521] [drm] radeon: 512M of GTT memory ready.  
 [    7.454555] [drm] radeon: irq initialized.  
 [    7.454559] [drm] GART: num cpu pages 131072, num gpu pages 131072  
 [    7.455026] [drm] Loading RS780 Microcode  
 [    7.455376] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin  
 [    7.560125] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin  
 [    7.605464] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin  
 [    7.699726] [drm] ring test succeeded in 1 usecs  
 [    7.699918] [drm] radeon: ib pool ready.  
 [    7.699983] [drm] ib test succeeded in 0 usecs  
 [    7.699986] [drm] Enabling audio support  
 [    7.702153] [drm] Radeon Display Connectors  
 [    7.702156] [drm] Connector 0:  
 [    7.702158] [drm]   VGA  
 [    7.702161] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c  
 [    7.702163] [drm]   Encoders:  
 [    7.702165] [drm]     CRT1: INTERNAL_KLDSCP_DAC1  
 [    7.702167] [drm] Connector 1:  
 [    7.702168] [drm]   LVDS  
 [    7.702171] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c  
 [    7.702173] [drm]   Encoders:  
 [    7.702175] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA  
 [    7.702177] [drm] Connector 2:  
 [    7.702178] [drm]   HDMI-A  
 [    7.702180] [drm]   HPD1  
 [    7.702182] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c  
 [    7.702184] [drm]   Encoders:  
 [    7.702186] [drm]     DFP1: INTERNAL_UNIPHY  
 [    7.840027] [drm] fb mappable at 0xC0141000  
 [    7.840031] [drm] vram apper at 0xC0000000  
 [    7.840033] [drm] size 4325376  
 [    7.840035] [drm] fb depth is 24  
 [    7.840037] [drm]    pitch is 5632  
 [    7.840241] fb0: radeondrmfb frame buffer device  
 [    7.840243] registered panic notifier  
 [    7.840248] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0  
 [    8.141421] vga16fb: initializing  
 [    8.141426] vga16fb: mapped to 0xc00a0000  
 [    8.141433] vga16fb: not registering due to another framebuffer present  
 [    8.451036] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    8.783728] hda_codec: ALC269: BIOS auto-probing.  
 [    8.783932] hda_codec: connection list not available for 0x24  
 [    8.784224] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9  
 [    8.794287] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    8.794330] HDA Intel 0000:01:05.1: setting latency timer to 64  
 [    9.415046] Console: switching to colour frame buffer device 170x48  
 [   12.265042] type=1505 audit(1281859340.021:5):  operation="profile_replace" pid=1155 name="/sbin/dhclient3"  
 [   12.265379] type=1505 audit(1281859340.021:6):  operation="profile_replace" pid=1155 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
 [   12.265565] type=1505 audit(1281859340.021:7):  operation="profile_replace" pid=1155 name="/usr/lib/connman/scripts/dhclient-script"  
 [   12.577680] type=1505 audit(1281859340.334:8):  operation="profile_load" pid=1156 name="/usr/bin/evince"  
 [   12.582052] type=1505 audit(1281859340.337:9):  operation="profile_load" pid=1156 name="/usr/bin/evince-previewer"  
 [   12.587892] type=1505 audit(1281859340.341:10):  operation="profile_load" pid=1156 name="/usr/bin/evince-thumbnailer"  
 [   12.685685] type=1505 audit(1281859340.441:11):  operation="profile_load" pid=1227 name="/usr/lib/cups/backend/cups-pdf"  
 [   12.686100] type=1505 audit(1281859340.441:12):  operation="profile_load" pid=1227 name="/usr/sbin/cupsd"  
 [   12.718562] type=1505 audit(1281859340.474:13):  operation="profile_load" pid=1228 name="/usr/sbin/tcpdump"  
 [   14.895152] ppdev: user-space parallel port driver  
 [   24.894813] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.  
 [   35.007823] usb 1-1: USB disconnect, address 2  
 [COLOR=Red]
sudo lshw -C network:[/COLOR]

 aaron@aaron-laptop:~$ sudo lshw -C network  
   *-network UNCLAIMED      
        description: Ethernet controller 
        product: AR8151 v1.0 Gigabit Ethernet  
        vendor: Atheros Communications  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        version: c0  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress vpd bus_master cap_list  
        configuration: latency=0  
        resources: memory:d0200000-d023ffff ioport:a000(size=128)  
   *-network UNCLAIMED  
        description: Network controller  
        product: Broadcom Corporation  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: memory:d0300000-d0303fff  
 
[COLOR=Red]lsb_release-d:[/COLOR]

 aaron@aaron-laptop:~$ lsb_release -d  
 Description:    Ubuntu 10.04 LTS  
 aaron@aaron-laptop:~$ uname -mr  
 2.6.32-21-generic i686  
 
[COLOR=Red]sudo /etc/init.d/networking restart:[/COLOR]

aaron@aaron-laptop:~$ sudo /etc/init.d/networking restart  
  * Reconfiguring network interfaces...                                                                                                                           [ OK ]

---

### Post by V13 Noob on 2010-08-16
Does anybody have any light shedding info? Im really stuck...

---

### Post by dineshs on 2010-08-16
Network unclaimed is not a good sign.Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1476231")

---

### Post by V13 Noob on 2010-08-16
I hadnt seen it but I did as directed by "chili555" whosae solution worked for others, but when he instructs that in order to install the driver, build-essential must be installed, so I downloaded on my desktop and transferrred over to my home on the netbook w/o conection and when trying to install it it says Depedecy not satisfiable:libc6-dev|libc-dev
Should I try to get those packages? Or am I doing something wrong?
I've tried getting packages for dkms i think after a dependency wasnt satisfiable but I just kept running around in circles, any thoughts anyone?

---

### Post by dineshs on 2010-08-17
> Should I try to get those packages? 
Open synaptic package manager (system-administration-syn...)and mark build-essential for installation.(do not apply)
Go to file-generate package download script 
Name the script (anything) and save it in  a pen drive preferably in a folder.
You can download all packages using this script via any other ubuntu machine(rightclick the script and click run in terminal which will download all the required packages to the same folder)
Now go back to your ubuntu installation,copy and paste all these files - except the script - from the pendrive into /var/cache/apt/archives by opening the folder using
```
gksudo nautilus /var/cache/apt/archives
```
Now open synaptic package manager , mark build-essential for installation again and apply
Note:You can download the different packages seperately via WINDOWS.The script contains the name of the required packages.In my case I get
libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb
g++-4.4_4.4.3-4ubuntu5_i386.deb
g++_4.4.3-1ubuntu1_i386.deb
xz-utils_4.999.9beta+20091116-1_i386.deb
patch_2.6-2ubuntu1_i386.deb
dpkg-dev_1.15.5.6ubuntu4.1_all.deb
build-essential_11.4build1_i386.deb
fakeroot_1.14.4-1ubuntu1_i386.deb

---

### Post by V13 Noob on 2010-08-17
Thanks. I did as you said, opened the folder as you instructed and copied the packages but they didn't show up on synaptic package manager. I rebooted just in case they would show up after but they still didn't and I did confirm and they are there. also did a quick Google search as to why they wouldn't show up but couldn't come up with anything.
Thanks for helping me out dineshs, sorry to stretch your patience..

---

### Post by dineshs on 2010-08-18
> but they didn't show up on synaptic package manager.They will not
When you try to install something ,the packages  are first downloaded to /var/cache/apt/archives then installed.You have done the first step.The second step is
Open synaptic package manager , mark build-essential for installation again and apply

---

### Post by V13 Noob on 2010-08-18
I understand the next step except that build essentials doesn't appear in the synaptic package manager list so i cant mark it for installation..

---

### Post by dineshs on 2010-08-18
Did you try typing [COLOR="Green"]build-essential[/COLOR] on quick search option in syn pack mangr?

---

### Post by V13 Noob on 2010-08-19
Yea its the first thing i tried. Do you know if broadcom just isnt supported at all by ubuntu? Ive tried a few methods and maybe im doing something wrong on my part and searched but it just seems like broadcom doesnt get along with ubuntu for the wireless and the wired, I just dont know..

---

### Post by dineshs on 2010-08-19
Please try post#7 here
[http://ubuntuforums.org/showthread.php?t=1555540](http://ubuntuforums.org/showthread.php?t=1555540)

---

### Post by V13 Noob on 2010-08-19
Thanks, it seems like this guide should do it. but i didnt work for me my guess though is that I'm using a liveUSB since my netbook dosnt have an optical drive, and i dont have an external one, would you know if these codes from the link would work with the USB? also does it make a differance if its Netbook Remix? Thanks
 	Code:
 	sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential 
 	Code:
 	sudo umount /dev/sr0
sudo mount /dev/sr0 /media/apt/
sudo apt-cdrom add

---

### Post by dineshs on 2010-08-19
I am not sure (You may try google.)
> **V13 Noob said:**
> 
 	sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential 
 	
This may help
[http://ubuntuforums.org/showthread.php?p=9035543#post9035543](http://ubuntuforums.org/showthread.php?p=9035543#post9035543)

---

