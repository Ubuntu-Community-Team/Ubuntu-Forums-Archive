---
title: "Unable to connect to wireless after upgrade."
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by spiked4life on 2008-12-27
I very recently installed Ubuntu 8.10. After the install everything seemed to be working and I could easily connect to the wireless network. After connecting the Update Manager asked me to install a whole bunch of updates, which I did. Then it asked me to reboot. Now however, I am unable to connect to the wireless network anymore. I can see other wireless networks but i cant connect to my WPA protected wlan. The dialog box for the security passphrase always pops up and even tho i enter the right pass it wont connect. I have tried googling for a solution and there seems to be plenty of people with similar problems but all of the forum posts I have seen has either been way too technical for me or the problem has not been resolved. I'd appreciate some help in resolving this matter.

---

### Post by spiked4life on 2008-12-28
I'm guessing that you guys might need some logs posted or some hardware specs listed?

I have no idea what logs might be useful or how to access them so I'll need some help there. 

As for the hardware, this is a desktop with a PCI Wifi card. Other then that I don't know.

---

### Post by ieee488 on 2008-12-28
Read the Sticky at the top of the 1st page of this forum for info about what info people need to see.

---

### Post by spiked4life on 2008-12-28
> **ieee488 said:**
> Read the Sticky at the top of the 1st page of this forum for info about what info people need to see.

Thanks. Should have noticed that. Anyway, here are the outputs from those commands.


Lspci =
```
02:09.0 Network controller: RaLink RT2600 802.11 MIMO 
```

ifconfig=
```
wlan0     Link encap:Ethernet  HWaddr 00:13:f7:1e:c0:38   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-13-F7-1E-C0-38-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

iwconfig=
```
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11bg  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=10 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

lsmod= I didn't quite get this one right I think

dmesg=
```
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K 
[    0.004000] CPU: L2 cache: 512K 
[    0.004000] CPU: Physical Processor ID: 0 
[    0.148223] CPU1: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09 
[    0.148250] checking TSC synchronization [CPU#0 -> CPU#1]: passed. 
[    0.152046] Brought up 2 CPUs 
[    0.152052] Total of 2 processors activated (10395.29 BogoMIPS). 
[    0.152087] CPU0 attaching sched-domain: 
[    0.152091]  domain 0: span 0-1 level SIBLING 
[    0.152095]   groups: 0 1 
[    0.152102]   domain 1: span 0-1 level CPU 
[    0.152106]    groups: 0-1 
[    0.152114] CPU1 attaching sched-domain: 
[    0.152117]  domain 0: span 0-1 level SIBLING 
[    0.152120]   groups: 1 0 
[    0.152126]   domain 1: span 0-1 level CPU 
[    0.152130]    groups: 0-1 
[    0.152262] net_namespace: 840 bytes 
[    0.152262] Booting paravirtualized kernel on bare hardware 
[    0.152447] Time: 18:16:31  Date: 12/28/08 
[    0.152493] NET: Registered protocol family 16 
[    0.152531] EISA bus registered 
[    0.152531] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2 
[    0.152531] PCI: Using configuration type 1 for base access 
[    0.156074] ACPI: Interpreter disabled. 
[    0.156074] Linux Plug and Play Support v0.97 (c) Adam Belay 
[    0.156074] pnp: PnP ACPI: disabled 
[    0.156074] ASUS P4P800 detected. Disabling PnPBIOS 
[    0.156074] PnPBIOS: Disabled 
[    0.156074] PCI: Probing PCI hardware 
[    0.156074] PCI: Probing PCI hardware (bus 00) 
[    0.156077] PCI: 0000:00:00.0 reg 10 32bit mmio: [f8000000, fbffffff] 
[    0.156205] PCI: 0000:00:1d.0 reg 20 io port: [ef00, ef1f] 
[    0.156262] PCI: 0000:00:1d.1 reg 20 io port: [ef20, ef3f] 
[    0.156319] PCI: 0000:00:1d.2 reg 20 io port: [ef40, ef5f] 
[    0.156376] PCI: 0000:00:1d.3 reg 20 io port: [ef80, ef9f] 
[    0.156440] PCI: 0000:00:1d.7 reg 10 32bit mmio: [febffc00, febfffff] 
[    0.156499] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold 
[    0.156505] pci 0000:00:1d.7: PME# disabled 
[    0.156592] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000 
[    0.156601] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO 
[    0.156606] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO 
[    0.156628] PCI: 0000:00:1f.1 reg 10 io port: [0, 7] 
[    0.156637] PCI: 0000:00:1f.1 reg 14 io port: [0, 3] 
[    0.156645] PCI: 0000:00:1f.1 reg 18 io port: [0, 7] 
[    0.156654] PCI: 0000:00:1f.1 reg 1c io port: [0, 3] 
[    0.156662] PCI: 0000:00:1f.1 reg 20 io port: [fc00, fc0f] 
[    0.156671] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff] 
[    0.156702] PCI: 0000:00:1f.2 reg 10 io port: [efe0, efe7] 
[    0.156710] PCI: 0000:00:1f.2 reg 14 io port: [efac, efaf] 
[    0.156718] PCI: 0000:00:1f.2 reg 18 io port: [efa0, efa7] 
[    0.156725] PCI: 0000:00:1f.2 reg 1c io port: [efa8, efab] 
[    0.156733] PCI: 0000:00:1f.2 reg 20 io port: [ef60, ef6f] 
[    0.156789] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f] 
[    0.156836] PCI: 0000:00:1f.5 reg 10 io port: [e800, e8ff] 
[    0.156844] PCI: 0000:00:1f.5 reg 14 io port: [ee80, eebf] 
[    0.156852] PCI: 0000:00:1f.5 reg 18 32bit mmio: [febff800, febff9ff] 
[    0.156861] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [febff400, febff4ff] 
[    0.156891] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold 
[    0.156897] pci 0000:00:1f.5: PME# disabled 
[    0.156937] PCI: 0000:01:00.0 reg 10 32bit mmio: [e0000000, efffffff] 
[    0.156944] PCI: 0000:01:00.0 reg 14 io port: [c000, c0ff] 
[    0.156952] PCI: 0000:01:00.0 reg 18 32bit mmio: [fe9f0000, fe9fffff] 
[    0.156972] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe9c0000, fe9dffff] 
[    0.156990] pci 0000:01:00.0: supports D1 
[    0.156993] pci 0000:01:00.0: supports D2 
[    0.157018] PCI: 0000:01:00.1 reg 10 32bit mmio: [d0000000, dfffffff] 
[    0.157026] PCI: 0000:01:00.1 reg 14 32bit mmio: [fe9e0000, fe9effff] 
[    0.157060] pci 0000:01:00.1: supports D1 
[    0.157063] pci 0000:01:00.1: supports D2 
[    0.157106] PCI: bridge 0000:00:01.0 io port: [c000, cfff] 
[    0.157112] PCI: bridge 0000:00:01.0 32bit mmio: [fe900000, fe9fffff] 
[    0.157117] PCI: bridge 0000:00:01.0 32bit mmio pref: [b7f00000, f7efffff] 
[    0.157169] PCI: 0000:02:05.0 reg 10 32bit mmio: [feafc000, feafffff] 
[    0.157177] PCI: 0000:02:05.0 reg 14 io port: [d800, d8ff] 
[    0.157219] pci 0000:02:05.0: supports D1 
[    0.157222] pci 0000:02:05.0: supports D2 
[    0.157225] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.157231] pci 0000:02:05.0: PME# disabled 
[    0.157269] PCI: 0000:02:09.0 reg 10 32bit mmio: [feaf0000, feaf7fff] 
[    0.157343] PCI: 0000:02:0b.0 reg 10 32bit mmio: [feafb800, feafbfff] 
[    0.157388] pci 0000:02:0b.0: supports D1 
[    0.157390] pci 0000:02:0b.0: supports D2 
[    0.157418] pci 0000:00:1e.0: transparent bridge 
[    0.157424] PCI: bridge 0000:00:1e.0 io port: [d000, dfff] 
[    0.157429] PCI: bridge 0000:00:1e.0 32bit mmio: [fea00000, feafffff] 
[    0.160075] pci 0000:00:1f.0: PIIX/ICH IRQ router [8086/24d0] 
[    0.160108] pci 0000:00:1d.0: PCI->APIC IRQ transform: INT A -> IRQ 16 
[    0.160115] pci 0000:00:1d.1: PCI->APIC IRQ transform: INT B -> IRQ 19 
[    0.160122] pci 0000:00:1d.2: PCI->APIC IRQ transform: INT C -> IRQ 18 
[    0.160128] pci 0000:00:1d.3: PCI->APIC IRQ transform: INT A -> IRQ 16 
[    0.160135] pci 0000:00:1d.7: PCI->APIC IRQ transform: INT D -> IRQ 23 
[    0.160146] pci 0000:00:1f.1: PCI->APIC IRQ transform: INT A -> IRQ 18 
[    0.160152] pci 0000:00:1f.2: PCI->APIC IRQ transform: INT A -> IRQ 18 
[    0.160159] pci 0000:00:1f.3: PCI->APIC IRQ transform: INT B -> IRQ 17 
[    0.160165] pci 0000:00:1f.5: PCI->APIC IRQ transform: INT B -> IRQ 17 
[    0.160171] pci 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16 
[    0.160179] pci 0000:02:05.0: PCI->APIC IRQ transform: INT A -> IRQ 22 
[    0.160186] pci 0000:02:09.0: PCI->APIC IRQ transform: INT A -> IRQ 21 
[    0.160192] pci 0000:02:0b.0: PCI->APIC IRQ transform: INT A -> IRQ 23 
[    0.164031] NET: Registered protocol family 8 
[    0.164035] NET: Registered protocol family 20 
[    0.164065] NetLabel: Initializing 
[    0.164065] NetLabel:  domain hash size = 128 
[    0.164065] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.164070] NetLabel:  unlabeled traffic allowed by default 
[    0.164177] hpet clockevent registered 
[    0.164183] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0 
[    0.164192] hpet0: 3 64-bit timers, 14318180 Hz 
[    0.166042] tracer: 772 pages allocated for 65536 entries of 48 bytes 
[    0.166046]    actual entries 65620 
[    0.166253] AppArmor: AppArmor Filesystem Enabled 
[    0.202310] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 
[    0.202316] pci 0000:00:01.0:   IO window: 0xc000-0xcfff 
[    0.202322] pci 0000:00:01.0:   MEM window: 0xfe900000-0xfe9fffff 
[    0.202328] pci 0000:00:01.0:   PREFETCH window: 0x000000b7f00000-0x000000f7efffff 
[    0.202337] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02 
[    0.202341] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff 
[    0.202349] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff 
[    0.202354] pci 0000:00:1e.0:   PREFETCH window: disabled 
[    0.202376] pci 0000:00:1e.0: setting latency timer to 64 
[    0.202383] bus: 00 index 0 io port: [0, ffff] 
[    0.202386] bus: 00 index 1 mmio: [0, ffffffff] 
[    0.202390] bus: 01 index 0 io port: [c000, cfff] 
[    0.202393] bus: 01 index 1 mmio: [fe900000, fe9fffff] 
[    0.202396] bus: 01 index 2 mmio: [b7f00000, f7efffff] 
[    0.202399] bus: 01 index 3 mmio: [0, 0] 
[    0.202402] bus: 02 index 0 io port: [d000, dfff] 
[    0.202405] bus: 02 index 1 mmio: [fea00000, feafffff] 
[    0.202408] bus: 02 index 2 mmio: [0, 0] 
[    0.202411] bus: 02 index 3 io port: [0, ffff] 
[    0.202414] bus: 02 index 4 mmio: [0, ffffffff] 
[    0.202428] NET: Registered protocol family 2 
[    0.212366] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.212812] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.213509] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.214101] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.214107] TCP reno registered 
[    0.216424] NET: Registered protocol family 1 
[    0.216599] checking if image is initramfs... it is 
[    0.664309] Switched to high resolution mode on CPU 1 
[    0.668043] Switched to high resolution mode on CPU 0 
[    0.981491] Freeing initrd memory: 8004k freed 
[    0.982241] platform rtc_cmos: registered platform RTC device (no PNP device found) 
[    0.983185] audit: initializing netlink socket (disabled) 
[    0.983207] type=2000 audit(1230488190.981:1): initialized 
[    0.988282] highmem bounce pool size: 64 pages 
[    0.988293] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    0.992958] VFS: Disk quotas dquot_6.5.1 
[    0.993126] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    0.993310] msgmni has been set to 1761 
[    0.993548] io scheduler noop registered 
[    0.993552] io scheduler anticipatory registered 
[    0.993556] io scheduler deadline registered 
[    0.993579] io scheduler cfq registered (default) 
[    8.992015] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001 
[    8.992152] pci 0000:01:00.0: Boot video device 
[    8.992844] isapnp: Scanning for PnP cards... 
[    9.346498] isapnp: No Plug & Play device found 
[    9.423845] Serial: 8250/16550 driver4 ports, IRQ sharing enabled 
[    9.424035] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
[    9.424276] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
[    9.428535] brd: module loaded 
[    9.428659] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[    9.429047] PNP: No PS/2 controller found. Probing ports directly. 
[    9.431642] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    9.431653] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    9.436266] mice: PS/2 mouse device common for all mice 
[    9.436556] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0 
[    9.436586] rtc0: alarms up to one day, hpet irqs 
[    9.684140] EISA: Probing bus 0 at eisa.0 
[    9.684187] EISA: Detected 0 cards. 
[    9.684192] cpuidle: using governor ladder 
[    9.684196] cpuidle: using governor menu 
[    9.685070] TCP cubic registered 
[    9.685116] Using IPI No-Shortcut mode 
[    9.685565] registered taskstats version 1 
[    9.685740]   Magic number: 4:770:292 
[    9.685768] tty ttyz6: hash matches 
[    9.685855] tty tty25: hash matches 
[    9.685899] rtc_cmos rtc_cmos: setting system clock to 2008-12-28 18:16:40 UTC (1230488200) 
[    9.685904] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    9.685907] EDD information not available. 
[    9.686332] Freeing unused kernel memory: 424k freed 
[    9.686400] Write protecting the kernel text: 2576k 
[    9.686441] Write protecting the kernel read-only data: 936k 
[    9.931478] fuse init (API version 7.9) 
[   10.363415] thermal: Unknown symbol acpi_processor_set_thermal_limit 
[   10.654824] usbcore: registered new interface driver usbfs 
[   10.654877] usbcore: registered new interface driver hub 
[   10.667999] usbcore: registered new device driver usb 
[   10.674468] USB Universal Host Controller Interface driver v3.0 
[   10.674562] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
[   10.674572] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[   10.674675] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[   10.674724] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ef00 
[   10.675091] usb usb1: configuration #1 chosen from 1 choice 
[   10.675170] hub 1-0:1.0: USB hub found 
[   10.675197] hub 1-0:1.0: 2 ports detected 
[   10.864987] SCSI subsystem initialized 
[   10.909474] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
[   10.909483] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[   10.909539] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[   10.909575] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ef20 
[   10.909787] usb usb2: configuration #1 chosen from 1 choice 
[   10.909847] hub 2-0:1.0: USB hub found 
[   10.909864] hub 2-0:1.0: 2 ports detected 
[   10.939919] libata version 3.00 loaded. 
[   11.020155] usb 1-1: new full speed USB device using uhci_hcd and address 2 
[   11.020390] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
[   11.020400] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[   11.020509] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[   11.020555] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef40 
[   11.020909] usb usb3: configuration #1 chosen from 1 choice 
[   11.020985] hub 3-0:1.0: USB hub found 
[   11.021038] hub 3-0:1.0: 2 ports detected 
[   11.186199] usb 1-1: configuration #1 chosen from 1 choice 
[   11.191845] hub 1-1:1.0: USB hub found 
[   11.192737] hub 1-1:1.0: 2 ports detected 
[   11.229709] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
[   11.229721] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[   11.229804] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[   11.229845] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef80 
[   11.230166] usb usb4: configuration #1 chosen from 1 choice 
[   11.230253] hub 4-0:1.0: USB hub found 
[   11.230274] hub 4-0:1.0: 2 ports detected 
[   11.333843] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
[   11.333855] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[   11.333934] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[   11.337876] ehci_hcd 0000:00:1d.7: debug port 1 
[   11.337890] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported 
[   11.337917] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfebffc00 
[   11.353051] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   11.353423] usb usb5: configuration #1 chosen from 1 choice 
[   11.353501] hub 5-0:1.0: USB hub found 
[   11.353524] hub 5-0:1.0: 8 ports detected 
[   11.537088] usb 1-1: USB disconnect, address 2 
[   11.563818] skge 1.13 addr 0xfeafc000 irq 22 chip Yukon rev 1 
[   11.564608] skge eth0: addr 00:0c:6e:4e:e2:07 
[   11.572777] ata_piix 0000:00:1f.1: version 2.12 
[   11.572797] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007) 
[   11.572886] ata_piix 0000:00:1f.1: setting latency timer to 64 
[   11.573554] scsi0 : ata_piix 
[   11.578131] scsi1 : ata_piix 
[   11.578274] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14 
[   11.578283] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15 
[   11.740670] ata1.01: ATA-5: QUANTUM FIREBALLP AS30.0, A1Y.1500, max UDMA/100 
[   11.740680] ata1.01: 58633344 sectors, multi 16: LBA  
[   11.756512] ata1.01: configured for UDMA/100 
[   11.920316] ata2.00: ATAPI: PLEXTOR DVDR   PX-708A, 1.11, max UDMA/33 
[   11.928256] ata2.00: configured for UDMA/33 
[   11.928438] scsi 0:0:1:0: Direct-Access     ATA      QUANTUM FIREBALL A1Y. PQ: 0 ANSI: 5 
[   11.929189] scsi 1:0:0:0: CD-ROM            PLEXTOR  DVDR   PX-708A   1.11 PQ: 0 ANSI: 5 
[   11.929381] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ] 
[   11.929465] ata_piix 0000:00:1f.2: setting latency timer to 64 
[   11.929636] scsi2 : ata_piix 
[   11.929814] scsi3 : ata_piix 
[   11.929921] ata3: SATA max UDMA/133 cmd 0xefe0 ctl 0xefac bmdma 0xef60 irq 18 
[   11.929929] ata4: SATA max UDMA/133 cmd 0xefa0 ctl 0xefa8 bmdma 0xef68 irq 18 
[   12.092349] ata3.00: ATA-7: ST3250823AS, 3.03, max UDMA/133 
[   12.092355] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32) 
[   12.101365] ata3.00: configured for UDMA/133 
[   12.128027] usb 5-5: new high speed USB device using ehci_hcd and address 4 
[   12.267092] scsi 2:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5 
[   12.271384] usb 5-5: configuration #1 chosen from 1 choice 
[   12.310553] scsi 0:0:1:0: Attached scsi generic sg0 type 0 
[   12.310656] scsi 1:0:0:0: Attached scsi generic sg1 type 5 
[   12.310780] scsi 2:0:0:0: Attached scsi generic sg2 type 0 
[   12.357287] Driver 'sd' needs updating - please use bus_type methods 
[   12.357546] sd 0:0:1:0: [sda] 58633344 512-byte hardware sectors (30020 MB) 
[   12.357609] sd 0:0:1:0: [sda] Write Protect is off 
[   12.357622] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
[   12.357714] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   12.357933] sd 0:0:1:0: [sda] 58633344 512-byte hardware sectors (30020 MB) 
[   12.358006] sd 0:0:1:0: [sda] Write Protect is off 
[   12.358013] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00 
[   12.358118] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   12.358131]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
[   12.362216]  sda1 
[   12.362393] sd 0:0:1:0: [sda] Attached SCSI disk 
[   12.362815] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB) 
[   12.362853] sd 2:0:0:0: [sdb] Write Protect is off 
[   12.362857] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[   12.362967] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   12.363227] sd 2:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB) 
[   12.363262] sd 2:0:0:0: [sdb] Write Protect is off 
[   12.363266] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00 
[   12.363343] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[   12.363350]  sdb:sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray 
[   12.364433] Uniform CD-ROM driver Revision: 3.20 
[   12.364906] sr 1:0:0:0: Attached scsi CD-ROM sr0 
[   12.382064]  sdb1 sdb2 < sdb5 sdb6 > 
[   12.422166] sd 2:0:0:0: [sdb] Attached SCSI disk 
[   12.512032] usb 1-1: new full speed USB device using uhci_hcd and address 3 
[   12.677673] usb 1-1: configuration #1 chosen from 1 choice 
[   12.683528] hub 1-1:1.0: USB hub found 
[   12.684495] hub 1-1:1.0: 2 ports detected 
[   13.140021] usb 1-2: new full speed USB device using uhci_hcd and address 4 
[   13.325563] usb 1-2: configuration #1 chosen from 1 choice 
[   13.405346] usb 1-1.2: new low speed USB device using uhci_hcd and address 5 
[   13.545236] usb 1-1.2: configuration #1 chosen from 1 choice 
[   13.549512] usbcore: registered new interface driver libusual 
[   13.580252] Initializing USB Mass Storage driver... 
[   13.587422] scsi4 : SCSI emulation for USB Mass Storage devices 
[   13.596475] usbcore: registered new interface driver usb-storage 
[   13.596494] USB Mass Storage support registered. 
[   13.596516] usb-storage: device found at 4 
[   13.596521] usb-storage: waiting for device to settle before scanning 
[   13.597423] usbcore: registered new interface driver hiddev 
[   13.611743] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input1 
[   13.612277] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1.2 
[   13.641316] Fixing up Logitech keyboard report descriptor 
[   13.642415] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input2 
[   13.645292] input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2 
[   13.645327] usbcore: registered new interface driver usbhid 
[   13.645333] usbhid: v2.6:USB HID core driver 
[   14.013246] usb 1-1.1: new low speed USB device using uhci_hcd and address 6 
[   14.150917] usb 1-1.1: configuration #1 chosen from 1 choice 
[   14.177386] input: Logitech Desktop USB stand as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3 
[   14.178941] input,hiddev97,hidraw2: USB HID v1.10 Keyboard [Logitech Desktop USB stand] on usb-0000:00:1d.0-1.1 
[   18.592224] usb-storage: device scan complete 
[   18.592813] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0 
[   18.593434] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0 
[   18.594058] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0 
[   18.594683] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0 
[   18.598873] sd 4:0:0:0: [sdc] Attached SCSI removable disk 
[   18.599904] sd 4:0:0:0: Attached scsi generic sg3 type 0 
[   18.602696] sd 4:0:0:1: [sdd] Attached SCSI removable disk 
[   18.605095] sd 4:0:0:1: Attached scsi generic sg4 type 0 
[   18.612898] sd 4:0:0:2: [sde] Attached SCSI removable disk 
[   18.613657] sd 4:0:0:2: Attached scsi generic sg5 type 0 
[   18.616374] sd 4:0:0:3: [sdf] Attached SCSI removable disk 
[   18.616698] sd 4:0:0:3: Attached scsi generic sg6 type 0 
[   18.829040] kjournald starting.  Commit interval 5 seconds 
[   18.829069] EXT3-fs: mounted filesystem with ordered data mode. 
[   23.966042] udevd version 124 started 
[   24.642064] Linux agpgart interface v0.103 
[   24.747067] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   24.796511] agpgart-intel 0000:00:00.0: Intel 865 Chipset 
[   24.799657] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000 
[   24.819970] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   24.909416] intel_rng: FWH not detected 
[   25.028048] iTCO_vendor_support: vendor-support=0 
[   25.100521] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008) 
[   25.100657] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860) 
[   25.100829] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   25.104650] input: PC Speaker as /devices/platform/pcspkr/input/input4 
[   25.395360] Linux video capture interface: v2.00 
[   25.499840] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel. 
[   25.700438] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes. 
[   25.701104] [fglrx]   vendor: 1002 device: 4150 count: 1 
[   25.703205] [fglrx] ioport: bar 1, base 0xc000, size: 0x100 
[   25.705184] [fglrx] PAT is enabled successfully! 
[   25.725611] saa7130/34: v4l2 driver version 0.2.14 loaded 
[   25.739967] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors 
[   25.747546] saa7133[0]: found at 0000:02:0b.0, rev: 240, irq: 23, latency: 64, mmio: 0xfeafb800 
[   25.747562] saa7133[0]: subsystem: 1043:4845, board: ASUS TV-FM 7135 [card=53,autodetected] 
[   25.747593] saa7133[0]: board init: gpio is 0 
[   25.917366] saa7133[0]: i2c eeprom 00: 43 10 45 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92 
[   25.917396] saa7133[0]: i2c eeprom 10: 00 ff e2 0f ff 20 ff ff ff ff ff ff ff ff ff ff 
[   25.917425] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 04 08 ff 00 89 ff ff ff ff 
[   25.917452] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917480] saa7133[0]: i2c eeprom 40: ff 14 00 c2 96 ff 01 30 ff ff ff ff ff ff ff ff 
[   25.917508] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917536] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917564] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917591] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917619] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917649] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917678] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917708] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917738] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917769] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff 
[   25.917802] saa7133[0]: i2c eeprom f0: 71 35 aa c0 02 dd 20 04 05 05 ff ff ff ff ff ff 
[   26.109540] gspca: main v2.2.0 registered 
[   26.134913] gspca: probing 041e:405f 
[   26.333808] ov519: I2C synced in 1 attempt(s) 
[   26.333815] ov519: starting OV7xx0 configuration 
[   26.349258] ov519: Sensor is an OV7670 
[   26.528253] tuner' 0-004b: chip found @ 0x96 (saa7133[0]) 
[   26.620063] tda829x 0-004b: setting tuner address to 61 
[   26.896075] tda829x 0-004b: type set to tda8290+75 
[   28.310256] gspca: probe ok 
[   28.310312] usbcore: registered new interface driver ov519 
[   28.310322] ov519: registered 
[   31.580483] saa7133[0]: registered device video1 [v4l2] 
[   31.580571] saa7133[0]: registered device vbi0 
[   31.580669] saa7133[0]: registered device radio0 
[   31.652771] phy0: Selected rate control algorithm 'pid' 
[   31.699955] saa7134 ALSA driver for DMA sound loaded 
[   31.700046] saa7133[0]/alsa: saa7133[0] at 0xfeafb800 irq 23 registered as card -2 
[   31.877337] Registered led device: rt61pci-phy0:radio 
[   31.877390] Registered led device: rt61pci-phy0:assoc 
[   31.877518] Intel ICH 0000:00:1f.5: setting latency timer to 64 
[   32.304017] intel8x0_measure_ac97_clock: measured 55988 usecs 
[   32.304021] intel8x0: clocking to 48000 
[   32.948026] loop: module loaded 
[   33.013366] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP] 
[   33.013950] parport0: irq 7 detected 
[   33.112781] lp0: using parport0 (polling). 
[   33.419672] Adding 9815672k swap on /dev/sdb6.  Priority:-1 extents:1 across:9815672k 
[   33.734135] EXT3 FS on sdb1, internal journal 
[   34.403469] kjournald starting.  Commit interval 5 seconds 
[   34.403794] EXT3 FS on sdb5, internal journal 
[   34.403803] EXT3-fs: mounted filesystem with ordered data mode. 
[   34.691906] type=1505 audit(1230484625.858:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4183 
[   34.907317] type=1505 audit(1230484626.074:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4188 
[   34.907625] type=1505 audit(1230484626.074:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4188 
[   35.049685] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   35.798023] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm 
[   35.798174] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance 
[   35.798764] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance 
[   35.798996] acpi_cpufreq: Unknown symbol acpi_processor_register_performance 
[   36.538230] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use) 
[   36.625437] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
[   36.625446] apm: disabled - APM is not SMP safe. 
[   36.868285] ppdev: user-space parallel port driver 
[   43.801708] Bluetooth: Core ver 2.13 
[   43.802707] NET: Registered protocol family 31 
[   43.802713] Bluetooth: HCI device and connection manager initialized 
[   43.802720] Bluetooth: HCI socket layer initialized 
[   43.832619] Bluetooth: L2CAP ver 2.11 
[   43.832628] Bluetooth: L2CAP socket layer initialized 
[   43.858444] Bluetooth: SCO (Voice Link) ver 0.6 
[   43.858453] Bluetooth: SCO socket layer initialized 
[   43.888301] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   43.888314] Bluetooth: BNEP filters: protocol multicast 
[   43.927482] Bluetooth: RFCOMM socket layer initialized 
[   43.927515] Bluetooth: RFCOMM TTY layer initialized 
[   43.927521] Bluetooth: RFCOMM ver 1.10 
[   43.961426] Bridge firewalling registered 
[   43.961819] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature. 
[   45.951603] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset) 
[   48.065931] skge eth0: enabling interface 
[   48.075086] firmware: requesting rt2661.bin 
[   48.323337] NET: Registered protocol family 17 
[   49.096633] agpgart-intel 0000:00:00.0: AGP 3.0 bridge 
[   49.096680] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode 
[   49.096749] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode 
[   49.096800] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps) 
[   49.096952] [fglrx] Setup AGP aperture 
[   49.097382] [fglrx] GART Table is not in FRAME_BUFFER range  
[   49.106286] [fglrx] CMM init INV FB MC:0xe8000000, length:0x8000000 
[   49.106304] [fglrx] Reserved FB block: Shared offset:0, size:40000  
[  147.860837] ppdev0: registered pardevice 
[  147.908275] ppdev0: unregistered pardevice 
[  148.078572] ppdev0: registered pardevice 
[  148.124405] ppdev0: unregistered pardevice 
[  149.144519] ppdev0: registered pardevice 
[  149.192034] ppdev0: unregistered pardevice 
```

sudo lshw -C network=
  ```
*-network:0              
       description: Ethernet interface 
       product: 3c940 10/100/1000Base-T [Marvell] 
       vendor: 3Com Corporation 
       physical id: 5 
       bus info: pci@0000:02:05.0 
       logical name: eth0 
       version: 12 
       serial: 00:0c:6e:4e:e2:07 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair 
  *-network:1 
       description: Wireless interface 
       product: RT2600 802.11 MIMO 
       vendor: RaLink 
       physical id: 9 
       bus info: pci@0000:02:09.0 
       logical name: wmaster0 
       version: 00 
       serial: 00:13:f7:1e:c0:38 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 5e:5e:7f:96:07:de 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
```

iwlist scan=
```
wmaster0  Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:15:E9:69:0F:73 
                    ESSID:"lsg10" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=28/100  Signal level:-72 dBm   
                    Encryption key:on 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000014790d6180 
                    Extra: Last beacon: 308ms ago 
```

 lsb_release -d =
```
Description:	Ubuntu 8.10 

```

Hopefully someone can make some use of this.

---

### Post by spiked4life on 2008-12-29
Guess linux is not yet ready for primetime. Back to windows then.

---

### Post by locketine on 2009-01-02
I had this exact problem with my Atheros 242X. I updated my laptop and mysteriously I could no longer connect to my WPA routers. I could see them and have good singal with them but could not connect. I just now fixed it by right clicking on the network manager, selecting edit wireless networks and removing my APs from the list. Once I did that I just clicked on my AP in the network manager, entered my security info and now it's working fine. 

I was not getting a dialog to reenter the security information though so my problem may have been different than yours. It would just sit there at step one of connecting to the AP and never move forward.

I'm guessing one of the updates changed how the network manager uses saved networks and caused it to hang on my saved network information.

---

