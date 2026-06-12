---
title: "Wireless Help Please..."
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by Fletch71011 on 2010-02-14
I am completely new to Linux, so excuse anything stupid I might be missing.  Anyways, I just installed Linux on 3 of my laptops, and I'm having trouble enabling wireless on my oldest one.  I tried to go through the tutorials, but it looks like my adapter should be supported, yet I can't get it enabled.  Here is my information.  Anything that I didn't understand I just pasted everything that the instructed command gave me.

**1 ) Machine Brand and Model (PC/Laptop)**:
     Code:
     HP Pavilion zd8000 
**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     Realtek Semiconductor Co. Ltd. RTL-8139/8139C/8139C+ (rev 10) 
**3 ) check interface:**
                            
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:6e:71:d8   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:20 Base address:0x5000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  

lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:""   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=0 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

**4 ) Check for modules:**
                                 Module                  Size  Used by  
 usbhid                 38208  0  
 nls_iso8859_1           3740  1  
 nls_cp437               5372  1  
 vfat                   10716  1  
 fat                    51452  1 vfat  
 binfmt_misc             8356  1  
 snd_intel8x0           30168  2  
 snd_ac97_codec        101216  1 snd_intel8x0  
 arc4                    1660  2  
 ecb                     2524  2  
 b43                   122136  0  
 ac97_bus                1532  1 snd_ac97_codec  
 snd_pcm_oss            37920  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 snd_seq_midi            6432  0  
 snd_rawmidi            22208  1 snd_seq_midi  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 joydev                 10272  0  
 mac80211              181236  1 b43  
 sdhci_pci               7100  0  
 sdhci                  17472  1 sdhci_pci  
 snd_timer              22276  2 snd_pcm,snd_seq  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 pcmcia                 36808  0  
 iptable_filter          3100  0  
 ip_tables              11692  1 iptable_filter  
 ppdev                   6688  0  
 cfg80211               93052  2 b43,mac80211  
 psmouse                56180  0  
 yenta_socket           24200  1  
 rsrc_nonstatic         11644  1 yenta_socket  
 pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic  
 tifm_7xx1               5372  0  
 tifm_core               7832  1 tifm_7xx1  
 lp                      8964  0  
 parport                35340  2 ppdev,lp  
 serio_raw               5280  0  
 led_class               4096  2 b43,sdhci  
 x_tables               16544  1 ip_tables  
 snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 soundcore               7264  1 snd  
 snd_page_alloc          9156  2 snd_intel8x0,snd_pcm  
 8139too                22620  0  
 video                  19380  0  
 usb_storage            52544  1  
 8139cp                 19260  0  
 mii                     5212  2 8139too,8139cp  
 ssb                    35300  1 b43  
 ohci1394               29900  0  
 ieee1394               86596  1 ohci1394  
 radeon                636000  2  
 output                  2780  1 video  
 ttm                    36212  1 radeon  
 drm                   159584  4 radeon,ttm  
 i2c_algo_bit            5760  1 radeon  
 intel_agp              27484  0  
 agpgart                34988  3 ttm,drm,intel_agp  
 
[B]

5 ) Kernel boot messages[/B]

            [    0.254006] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 *10 11 14 15)  
 [    0.254132] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 10 11 14 15) *5  
 [    0.254256] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 10 *11 14 15)  
 [    0.254378] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 10 11 14 15) *7  
 [    0.254509] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 10 11 14 15) *7  
 [    0.254641] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 10 11 14 15) *0, disabled.  
 [    0.254773] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 10 *11 14 15)  
 [    0.254904] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 10 11 14 15) *7  
 [    0.255168] SCSI subsystem initialized  
 [    0.255213] libata version 3.00 loaded.  
 [    0.255213] usbcore: registered new interface driver usbfs  
 [    0.255213] usbcore: registered new interface driver hub  
 [    0.255213] usbcore: registered new device driver usb  
 [    0.255213] ACPI: WMI: Mapper loaded 
 [    0.255213] PCI: Using ACPI for IRQ routing  
 [    0.255213] pci 0000:00:1c.0: BAR 13: can't allocate resource  
 [    0.255213] pci 0000:00:1c.0: BAR 14: can't allocate resource  
 [    0.255213] pci 0000:00:1c.0: BAR 15: can't allocate resource  
 [    0.268013] Bluetooth: Core ver 2.15 
 [    0.268040] NET: Registered protocol family 31  
 [    0.268040] Bluetooth: HCI device and connection manager initialized  
 [    0.268040] Bluetooth: HCI socket layer initialized  
 [    0.268040] NetLabel: Initializing  
 [    0.268040] NetLabel:  domain hash size = 128  
 [    0.268040] NetLabel:  protocols = UNLABELED CIPSOv4  
 [    0.268055] NetLabel:  unlabeled traffic allowed by default  
 [    0.268183] hpet clockevent registered  
 [    0.268188] HPET: 3 timers in total, 0 timers will be used for per-cpu timer  
 [    0.268194] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0  
 [    0.268202] hpet0: 3 comparators, 64-bit 14.318180 MHz counter  
 [    0.284017] pnp: PnP ACPI init  
 [    0.284041] ACPI: bus type pnp registered  
 [    0.286965] pnp: PnP ACPI: found 9 devices  
 [    0.286969] ACPI: ACPI bus type pnp unregistered  
 [    0.286974] PnPBIOS: Disabled by ACPI PNP  
 [    0.286990] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved  
 [    0.287002] system 00:02: ioport range 0x800-0x83f has been reserved  
 [    0.287007] system 00:02: ioport range 0x1000-0x107f has been reserved  
 [    0.287011] system 00:02: ioport range 0x1180-0x11bf has been reserved  
 [    0.287015] system 00:02: ioport range 0x4d0-0x4d1 has been reserved  
 [    0.287019] system 00:02: ioport range 0xfe00-0xfe00 has been reserved  
 [    0.287024] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved  
 [    0.287028] system 00:02: iomem range 0xfed13000-0xfed13fff has been reserved  
 [    0.287032] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved  
 [    0.287037] system 00:02: iomem range 0xfed20000-0xfed8ffff has been reserved  
 [    0.287041] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved  
 [    0.287045] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved  
 [    0.287049] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved  
 [    0.321779] AppArmor: AppArmor Filesystem Enabled  
 [    0.321839] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01  
 [    0.321844] pci 0000:00:01.0:   IO window: 0x4000-0x4fff  
 [    0.321850] pci 0000:00:01.0:   MEM window: 0xc8100000-0xc81fffff  
 [    0.321855] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff  
 [    0.321860] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02  
 [    0.321863] pci 0000:00:1c.0:   IO window: disabled  
 [    0.321869] pci 0000:00:1c.0:   MEM window: disabled  
 [    0.321873] pci 0000:00:1c.0:   PREFETCH window: disabled  
 [    0.321887] pci 0000:0b:00.0: CardBus bridge, secondary bus 0000:0c  
 [    0.321890] pci 0000:0b:00.0:   IO window: 0x005400-0x0054ff  
 [    0.321896] pci 0000:0b:00.0:   IO window: 0x005800-0x0058ff  
 [    0.321902] pci 0000:0b:00.0:   PREFETCH window: 0x20000000-0x23ffffff  
 [    0.321908] pci 0000:0b:00.0:   MEM window: 0x24000000-0x27ffffff  
 [    0.321914] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0b  
 [    0.321918] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff  
 [    0.321925] pci 0000:00:1e.0:   MEM window: 0xc8200000-0xc82fffff  
 [    0.321930] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff  
 [    0.321945]   alloc irq_desc for 16 on node -1  
 [    0.321948]   alloc kstat_irqs on node -1  
 [    0.321955] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.321961] pci 0000:00:01.0: setting latency timer to 64  
 [    0.321970]   alloc irq_desc for 17 on node -1  
 [    0.321973]   alloc kstat_irqs on node -1  
 [    0.321978] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [    0.321985] pci 0000:00:1c.0: setting latency timer to 64  
 [    0.321994] pci 0000:00:1e.0: setting latency timer to 64  
 [    0.322005] pci 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    0.322014] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]  
 [    0.322017] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]  
 [    0.322021] pci_bus 0000:01: resource 0 io:  [0x4000-0x4fff]  
 [    0.322024] pci_bus 0000:01: resource 1 mem: [0xc8100000-0xc81fffff]  
 [    0.322028] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]  
 [    0.322032] pci_bus 0000:02: resource 0 mem: [0x0-0xfff]  
 [    0.322035] pci_bus 0000:02: resource 1 mem: [0x0-0xfffff]  
 [    0.322038] pci_bus 0000:02: resource 2 mem: [0x0-0xfffff]  
 [    0.322042] pci_bus 0000:0b: resource 0 io:  [0x5000-0x5fff]  
 [    0.322045] pci_bus 0000:0b: resource 1 mem: [0xc8200000-0xc82fffff]  
 [    0.322048] pci_bus 0000:0b: resource 2 pref mem [0x20000000-0x23ffffff]  
 [    0.322052] pci_bus 0000:0b: resource 3 io:  [0x00-0xffff]  
 [    0.322055] pci_bus 0000:0b: resource 4 mem: [0x000000-0xffffffff]  
 [    0.322059] pci_bus 0000:0c: resource 0 io:  [0x5400-0x54ff]  
 [    0.322062] pci_bus 0000:0c: resource 1 io:  [0x5800-0x58ff]  
 [    0.322065] pci_bus 0000:0c: resource 2 pref mem [0x20000000-0x23ffffff]  
 [    0.322069] pci_bus 0000:0c: resource 3 mem: [0x24000000-0x27ffffff]  
 [    0.322126] NET: Registered protocol family 2  
 [    0.322265] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)  
 [    0.322684] TCP established hash table entries: 16384 (order: 5, 131072 bytes)  
 [    0.322757] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)  
 [    0.322825] TCP: Hash tables configured (established 16384 bind 16384)  
 [    0.322829] TCP reno registered  
 [    0.322916] NET: Registered protocol family 1  
 [    0.323001] Trying to unpack rootfs image as initramfs...  
 [    0.570752] Freeing initrd memory: 7460k freed  
 [    0.575260] Simple Boot Flag at 0x36 set to 0x1  
 [    0.575476] cpufreq-nforce2: No nForce2 chipset.  
 [    0.575520] Scanning for low memory corruption every 60 seconds  
 [    0.575653] audit: initializing netlink socket (disabled)  
 [    0.575673] type=2000 audit(1266145582.572:1): initialized  
 [    0.585223] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    0.587271] VFS: Disk quotas dquot_6.5.2  
 [    0.587364] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    0.588152] fuse init (API version 7.12)  
 [    0.588271] msgmni has been set to 991  
 [    0.588582] alg: No test for stdrng (krng)  
 [    0.588606] io scheduler noop registered  
 [    0.588609] io scheduler anticipatory registered  
 [    0.588612] io scheduler deadline registered  
 [    0.588675] io scheduler cfq registered (default)  
 [    0.589176] pci 0000:01:00.0: Boot video device  
 [    0.589345]   alloc irq_desc for 24 on node -1  
 [    0.589348]   alloc kstat_irqs on node -1  
 [    0.589361] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X  
 [    0.589370] pcieport-driver 0000:00:01.0: setting latency timer to 64  
 [    0.589503]   alloc irq_desc for 25 on node -1  
 [    0.589507]   alloc kstat_irqs on node -1  
 [    0.589517] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X  
 [    0.589527] pcieport-driver 0000:00:1c.0: setting latency timer to 64  
 [    0.589652] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    0.589816] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS  
 [    0.589827] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node df80ed38), AE_ALREADY_EXISTS  
 [    0.590017] ACPI Error (dsfield-0140): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS  
 [    0.590027] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node df80ed38), AE_ALREADY_EXISTS  
 [    0.590074] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    0.590354] ACPI: AC Adapter [ACAD] (on-line)  
 [    0.590437] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0  
 [    0.590443] ACPI: Power Button [PWRF]  
 [    0.590525] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1  
 [    0.741724] ACPI: Lid Switch [LID0]  
 [    0.741796] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2  
 [    0.741801] ACPI: Power Button [PWRB]  
 [    0.741860] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3  
 [    0.741864] ACPI: Sleep Button [SLPB]  
 [    0.742151] processor LNXCPU:00: registered as cooling_device0  
 [    0.742157] ACPI: Processor [CPU0] (supports 8 throttling states)  
 [    0.742240] processor LNXCPU:01: registered as cooling_device1  
 [    0.742246] ACPI: Processor [CPU1] (supports 8 throttling states)  
 [    0.745647] thermal LNXTHERM:01: registered as thermal_zone0  
 [    0.745660] ACPI: Thermal Zone [THRM] (37 C)  
 [    0.745750] isapnp: Scanning for PnP cards...  
 [    0.753332] ACPI: Battery Slot [BAT1] (battery absent)  
 [    0.769149] Switched to high resolution mode on CPU 1  
 [    0.772015] Switched to high resolution mode on CPU 0  
 [    1.098985] isapnp: No Plug & Play device found  
 [    1.100581] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled  
 [    1.101025]   alloc irq_desc for 22 on node -1  
 [    1.101029]   alloc kstat_irqs on node -1  
 [    1.101038] serial 0000:00:1e.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [    1.101046] serial 0000:00:1e.3: PCI INT A disabled  
 [    1.102377] brd: module loaded  
 [    1.103025] loop: module loaded  
 [    1.103132] input: Macintosh mouse button emulation as /devices/virtual/input/input4  
 [    1.103283] ata_piix 0000:00:1f.1: version 2.13  
 [    1.103297]   alloc irq_desc for 18 on node -1  
 [    1.103300]   alloc kstat_irqs on node -1  
 [    1.103307] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18  
 [    1.103356] ata_piix 0000:00:1f.1: setting latency timer to 64  
 [    1.103472] scsi0 : ata_piix  
 [    1.103593] scsi1 : ata_piix  
 [    1.103644] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3c40 irq 14  
 [    1.103649] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3c48 irq 15  
 [    1.105048] ata2: port disabled. ignoring.  
 [    1.105054] Fixed MDIO Bus: probed  
 [    1.105114] PPP generic driver version 2.4.2  
 [    1.105240] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    1.105267]   alloc irq_desc for 23 on node -1  
 [    1.105270]   alloc kstat_irqs on node -1  
 [    1.105277] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    1.105297] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    1.105303] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    1.105368] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1  
 [    1.109273] ehci_hcd 0000:00:1d.7: debug port 1  
 [    1.109281] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported  
 [    1.109300] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xc8000000  
 [    1.124015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    1.124128] usb usb1: configuration #1 chosen from 1 choice  
 [    1.124174] hub 1-0:1.0: USB hub found  
 [    1.124185] hub 1-0:1.0: 8 ports detected  
 [    1.124279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    1.124304] uhci_hcd: USB Universal Host Controller Interface driver  
 [    1.124338] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    1.124346] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    1.124351] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    1.124399] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    1.124427] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800  
 [    1.124536] usb usb2: configuration #1 chosen from 1 choice  
 [    1.124574] hub 2-0:1.0: USB hub found  
 [    1.124584] hub 2-0:1.0: 2 ports detected  
 [    1.124649]   alloc irq_desc for 19 on node -1  
 [    1.124652]   alloc kstat_irqs on node -1  
 [    1.124659] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    1.124667] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    1.124672] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    1.124723] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3  
 [    1.124759] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000038c0  
 [    1.124860] usb usb3: configuration #1 chosen from 1 choice  
 [    1.124900] hub 3-0:1.0: USB hub found  
 [    1.124910] hub 3-0:1.0: 2 ports detected  
 [    1.124979] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    1.124987] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    1.124991] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    1.125052] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4  
 [    1.125086] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000038e0  
 [    1.125188] usb usb4: configuration #1 chosen from 1 choice  
 [    1.125226] hub 4-0:1.0: USB hub found  
 [    1.125236] hub 4-0:1.0: 2 ports detected  
 [    1.125301] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16  
 [    1.125308] uhci_hcd 0000:00:1d.3: setting latency timer to 64  
 [    1.125313] uhci_hcd 0000:00:1d.3: UHCI Host Controller  
 [    1.125358] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5  
 [    1.125392] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003c00  
 [    1.125494] usb usb5: configuration #1 chosen from 1 choice  
 [    1.125532] hub 5-0:1.0: USB hub found  
 [    1.125542] hub 5-0:1.0: 2 ports detected  
 [    1.125676] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12  
 [    1.128119] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    1.128131] serio: i8042 AUX port at 0x60,0x64 irq 12  
 [    1.128249] mice: PS/2 mouse device common for all mice  
 [    1.128436] rtc_cmos 00:05: RTC can wake from S4  
 [    1.128483] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0  
 [    1.128511] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs  
 [    1.128657] device-mapper: uevent: version 1.0.3  
 [    1.128784] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  
 [    1.128897] device-mapper: multipath: version 1.1.0 loaded  
 [    1.128902] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    1.129075] EISA: Probing bus 0 at eisa.0  
 [    1.129083] Cannot allocate resource for EISA slot 1  
 [    1.129090] Cannot allocate resource for EISA slot 3  
 [    1.129094] Cannot allocate resource for EISA slot 4  
 [    1.129096] Cannot allocate resource for EISA slot 5  
 [    1.129109] EISA: Detected 0 cards.  
 [    1.129242] cpuidle: using governor ladder  
 [    1.129248] cpuidle: using governor menu  
 [    1.129980] TCP cubic registered  
 [    1.130160] NET: Registered protocol family 10  
 [    1.130824] lo: Disabled Privacy Extensions  
 [    1.131356] NET: Registered protocol family 17  
 [    1.131385] Bluetooth: L2CAP ver 2.13  
 [    1.131388] Bluetooth: L2CAP socket layer initialized  
 [    1.131391] Bluetooth: SCO (Voice Link) ver 0.6  
 [    1.131394] Bluetooth: SCO socket layer initialized  
 [    1.131437] Bluetooth: RFCOMM TTY layer initialized  
 [    1.131443] Bluetooth: RFCOMM socket layer initialized  
 [    1.131445] Bluetooth: RFCOMM ver 1.11  
 [    1.131489] Using IPI No-Shortcut mode  
 [    1.131575] PM: Resume from disk failed.  
 [    1.131593] registered taskstats version 1  
 [    1.131743]   Magic number: 14:256:125  
 [    1.131787] acpi device:00: hash matches  
 [    1.131822] rtc_cmos 00:05: setting system clock to 2010-02-14 11:06:23 UTC (1266145583)  
 [    1.131827] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    1.131829] EDD information not available.  
 [    1.157940] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5  
 [    1.273563] ata1.00: ATA-6: TOSHIBA MK8026GAX, PA002G, max UDMA/100  
 [    1.273567] ata1.00: 156301488 sectors, multi 16: LBA  
 [    1.273617] ata1.01: ATAPI: HL-DT-ST DVD-RW GCA-4080N, 0C35, max MWDMA2  
 [    1.280324] ata1.00: configured for UDMA/100  
 [    1.296225] ata1.01: configured for MWDMA2  
 [    1.298717] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8026GA PA00 PQ: 0 ANSI: 5  
 [    1.298892] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    1.300554] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)  
 [    1.300631] sd 0:0:0:0: [sda] Write Protect is off  
 [    1.300635] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    1.300673] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    1.300870]  sda: sda1 sda2 <  
 [    1.357502] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GCA-4080N 0C35 PQ: 0 ANSI: 5  
 [    1.381516]  sda5 >  
 [    1.385022] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    1.393473] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray  
 [    1.393478] Uniform CD-ROM driver Revision: 3.20  
 [    1.393577] sr 0:0:1:0: Attached scsi CD-ROM sr0  
 [    1.393643] sr 0:0:1:0: Attached scsi generic sg1 type 5  
 [    1.393689] Freeing unused kernel memory: 540k freed  
 [    1.394136] Write protecting the kernel text: 4568k  
 [    1.394198] Write protecting the kernel read-only data: 1836k  
 [    1.437044] usb 1-5: new high speed USB device using ehci_hcd and address 2  
 [    1.575206] Linux agpgart interface v0.103  
 [    1.583807] usb 1-5: configuration #1 chosen from 1 choice  
 [    1.729209] [drm] Initialized drm 1.1.0 20060810  
 [    1.759370] [drm] radeon default to kernel modesetting DISABLED.  
 [    1.759412] pci 0000:01:00.0: power state changed by ACPI to D0  
 [    1.759426] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    1.759433] pci 0000:01:00.0: setting latency timer to 64  
 [    1.759608] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0  
 [    1.783634] ohci1394 0000:0b:00.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22  
 [    1.793300] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)  
 [    1.799528] Initializing USB Mass Storage driver...  
 [    1.802964] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input6 
 [    1.803042] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)  
 [    1.803405] scsi2 : SCSI emulation for USB Mass Storage devices  
 [    1.803579] usbcore: registered new interface driver usb-storage  
 [    1.803587] USB Mass Storage support registered.  
 [    1.803789] usb-storage: device found at 2  
 [    1.803794] usb-storage: waiting for device to settle before scanning  
 [    1.836060] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[c8208000-c82087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]  
 [    1.836178] b43-pci-bridge 0000:0b:03.0: enabling device (0000 -> 0002)  
 [    1.836194] b43-pci-bridge 0000:0b:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [    1.901075] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:03.0  
 [    1.901455] 8139cp 0000:0b:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too  
 [    1.905306] 8139too Fast Ethernet driver 0.9.28  
 [    1.905378]   alloc irq_desc for 20 on node -1  
 [    1.905384]   alloc kstat_irqs on node -1  
 [    1.905398] 8139too 0000:0b:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    1.906861] eth0: RealTek RTL8139 at 0x5000, 00:c0:9f:6e:71:d8, IRQ 20  
 [    3.018160] PM: Starting manual resume from disk  
 [    3.018166] PM: Resume from partition 8:5  
 [    3.018168] PM: Checking hibernation image.  
 [    3.018395] PM: Resume from disk failed.  
 [    3.023103] EXT4-fs (sda1): INFO: recovery required on readonly filesystem  
 [    3.023111] EXT4-fs (sda1): write access will be enabled during recovery  
 [    3.050737] EXT4-fs (sda1): barriers enabled  
 [    3.112270] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800285600061dc9]  
 [    4.416258] kjournald2 starting: pid 370, dev sda1:8, commit interval 5 seconds  
 [    4.416282] EXT4-fs (sda1): delayed allocation enabled  
 [    4.416288] EXT4-fs: file extents enabled  
 [    4.427637] EXT4-fs: mballoc enabled 
 [    4.427661] EXT4-fs (sda1): orphan cleanup on readonly fs  
 [    4.427672] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 107  
 [    4.427716] EXT4-fs (sda1): 1 orphan inode deleted  
 [    4.427722] EXT4-fs (sda1): recovery complete  
 [    4.774384] EXT4-fs (sda1): mounted filesystem with ordered data mode  
 [    5.553326] type=1505 audit(1266145587.921:2): operation="profile_load" pid=393 name=/usr/share/gdm/guest-session/Xsession  
 [    5.556631] type=1505 audit(1266145587.924:3): operation="profile_load" pid=394 name=/sbin/dhclient3  
 [    5.557424] type=1505 audit(1266145587.924:4): operation="profile_load" pid=394 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [    5.557856] type=1505 audit(1266145587.924:5): operation="profile_load" pid=394 name=/usr/lib/connman/scripts/dhclient-script  
 [    5.626933] type=1505 audit(1266145587.993:6): operation="profile_load" pid=395 name=/usr/bin/evince  
 [    5.639207] type=1505 audit(1266145588.004:7): operation="profile_load" pid=395 name=/usr/bin/evince-previewer  
 [    5.646483] type=1505 audit(1266145588.012:8): operation="profile_load" pid=395 name=/usr/bin/evince-thumbnailer  
 [    5.667054] type=1505 audit(1266145588.032:9): operation="profile_load" pid=397 name=/usr/lib/cups/backend/cups-pdf  
 [    5.667974] type=1505 audit(1266145588.032:10): operation="profile_load" pid=397 name=/usr/sbin/cupsd  
 [    5.682439] type=1505 audit(1266145588.048:11): operation="profile_load" pid=398 name=/usr/sbin/tcpdump  
 [    6.505060] Adding 1485972k swap on /dev/sda5.  Priority:-1 extents:1 across:1485972k  
 [    6.797033] EXT4-fs (sda1): internal journal on sda1:8  
 [    6.803964] usb-storage: device scan complete  
 [    6.815014] udev: starting version 147  
 [    6.835636] scsi 2:0:0:0: Direct-Access     ST350082 0AS                   PQ: 0 ANSI: 2 CCS  
 [    6.836354] sd 2:0:0:0: Attached scsi generic sg2 type 0  
 [    6.837740] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)  
 [    6.838303] sd 2:0:0:0: [sdb] Write Protect is off  
 [    6.838312] sd 2:0:0:0: [sdb] Mode Sense: 00 38 00 00  
 [    6.838318] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [    6.840728] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [    6.840736]  sdb: sdb2  
 [    8.635050] sd 2:0:0:0: [sdb] Assuming drive cache: write through  
 [    8.635058] sd 2:0:0:0: [sdb] Attached SCSI disk  
 [   10.568709] eth0: link down  
 [   10.568811] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   12.255373] intel_rng: FWH not detected  
 [   13.099875] lp: driver loaded but no devices found  
 [   13.117406] tifm_7xx1 0000:0b:00.3: enabling device (0000 -> 0002)  
 [   13.117421] tifm_7xx1 0000:0b:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   13.192504] yenta_cardbus 0000:0b:00.0: CardBus bridge found [103c:3082]  
 [   13.192530] yenta_cardbus 0000:0b:00.0: Enabling burst memory read transactions  
 [   13.192539] yenta_cardbus 0000:0b:00.0: Using CSCINT to route CSC interrupts to PCI  
 [   13.192544] yenta_cardbus 0000:0b:00.0: Routing CardBus interrupts to PCI  
 [   13.192553] yenta_cardbus 0000:0b:00.0: TI: mfunc 0x01a01b22, devctl 0x64  
 [   13.432735] yenta_cardbus 0000:0b:00.0: ISA IRQ mask 0x0cf8, PCI irq 16  
 [   13.432743] yenta_cardbus 0000:0b:00.0: Socket status: 30000006  
 [   13.432755] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff  
 [   13.432762] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.  
 [   13.433188] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge Memory window: 0xc8200000 - 0xc82fffff  
 [   13.433195] yenta_cardbus 0000:0b:00.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff  
 [   13.463230] ppdev: user-space parallel port driver  
 [   13.497126] cfg80211: Calling CRDA to update world regulatory domain  
 [   13.637061] ip_tables: (C) 2000-2006 Netfilter Core Team  
 [   14.016899] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x80b1, caps: 0xa04713/0x20040a  
 [   14.053124] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7  
 [   14.295817] sdhci: Secure Digital Host Controller Interface driver  
 [   14.295823] sdhci: Copyright(c) Pierre Ossman  
 [   14.299681] sdhci-pci 0000:0b:00.4: SDHCI controller found [104c:8034] (rev 0)  
 [   14.299701] sdhci-pci 0000:0b:00.4: enabling device (0000 -> 0002)  
 [   14.299715] sdhci-pci 0000:0b:00.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   14.299823] Registered led device: mmc0::  
 [   14.299890] mmc0: SDHCI controller on PCI [0000:0b:00.4] using PIO  
 [   14.299956] Registered led device: mmc1::  
 [   14.300031] mmc1: SDHCI controller on PCI [0000:0b:00.4] using PIO  
 [   14.301778] Registered led device: mmc2::  
 [   14.301863] mmc2: SDHCI controller on PCI [0000:0b:00.4] using PIO  
 [   14.729007] cfg80211: World regulatory domain updated:  
 [   14.729014]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   14.729019]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   14.729023]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   14.729027]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   14.729031]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   14.729034]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   14.948760] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.  
 [   14.950131] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.  
 [   14.950803] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.  
 [   14.951236] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.  
 [   14.951947] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.  
 [   16.120933] b43-phy0: Broadcom 4318 WLAN found (core revision 9)  
 [   16.199764] phy0: Selected rate control algorithm 'minstrel'  
 [   16.201474] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]  
 [   16.384038] b43 ssb0:0: firmware: requesting b43/ucode5.fw  
 [   16.456446] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [   16.456494] Intel ICH 0000:00:1e.2: setting latency timer to 64  
 [   16.492836] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 [   16.497710] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found  
 [   16.497720] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found  
 [   16.497726] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.  
 [   16.776018] intel8x0_measure_ac97_clock: measured 51612 usecs (2487 samples)  
 [   16.776023] intel8x0: clocking to 48000  
 [   16.860037] b43 ssb0:0: firmware: requesting b43/ucode5.fw  
 [   16.864310] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw  
 [   16.874126] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found  
 [   16.874136] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found  
 [   16.874143] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.  
 [   18.789558] CPU0 attaching NULL sched-domain.  
 [   18.789567] CPU1 attaching NULL sched-domain.  
 [   18.808078] CPU0 attaching sched-domain:  
 [   18.808084]  domain 0: span 0-1 level SIBLING  
 [   18.808089]   groups: 0 1  
 [   18.808097] CPU1 attaching sched-domain:  
 [   18.808101]  domain 0: span 0-1 level SIBLING  
 [   18.808104]   groups: 1 0  
 [   20.121169] [drm] Setting GART location based on new memory map  
 [   20.122342] [drm] Loading R300 Microcode  
 [   20.122376] [drm] Num pipes: 1  
 [   20.122384] [drm] writeback test succeeded in 1 usecs  
 [   26.478928] CPU0 attaching NULL sched-domain.  
 [   26.478937] CPU1 attaching NULL sched-domain.  
 [   26.493100] CPU0 attaching sched-domain:  
 [   26.493106]  domain 0: span 0-1 level SIBLING  
 [   26.493111]   groups: 0 1  
 [   26.493119] CPU1 attaching sched-domain:  
 [   26.493123]  domain 0: span 0-1 level SIBLING  
 [   26.493127]   groups: 1 0  
 [  106.896018] usb 3-1: new low speed USB device using uhci_hcd and address 2  
 [  107.080143] usb 3-1: configuration #1 chosen from 1 choice  
 [  107.153457] usbcore: registered new interface driver hiddev  
 [  107.187335] input: Microsoft Microsoft Wireless Optical Mouse® 1.0A as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input8  
 [  107.187520] generic-usb 0003:045E:008C.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.0A] on usb-0000:00:1d.1-1/input0 
 [  107.187560] usbcore: registered new interface driver usbhid  
 [  107.187569] usbhid: v2.6:USB HID core driver
 
 
**6 ) Network configuration**
                                   *-network:0              
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 2  
        bus info: pci@0000:0b:02.0  
        logical name: eth0  
        version: 10  
        serial: 00:c0:9f:6e:71:d8  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s  
        resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff  
   *-network:1  
        description: Network controller  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 3  
        bus info: pci@0000:0b:03.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=64  
        resources: irq:17 memory:c8206000-c8207fff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:90:4b:f5:57:2f  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
 
**7 ) Scan for networks:**
                                 wlan0     Failed to read scan data : Network is down

**8 ) Ubuntu Version: **
     Code:
     Ubuntu 9.10 
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     2.6.31-14-generic i686

---

### Post by gordintoronto on 2010-02-14
This might be relevant:
[http://ubuntuforums.org/showthread.php?p=3278523&highlight=8139#post3278523](http://ubuntuforums.org/showthread.php?p=3278523&highlight=8139#post3278523)

Most people post less info, lspci is useful.

Do the other laptops use a wireless connection?

---

### Post by Fletch71011 on 2010-02-14
Thanks for the link, I'll try that out.

Yes I have both of my other laptops running the same version of Ubuntu and have them on wireless.

---

### Post by bkratz on 2010-02-14
When searching this is actually your wireless card

description: Network controller 
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
vendor: Broadcom Corporation 

The other device mentioned is your ethernet controller. Will search for other information also.


This really "sticks out" in your listing

[ 16.874143] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 

You might try that


Especially this section of the above

Ubuntu/Debian..................

---

### Post by Fletch71011 on 2010-02-14
> **gordintoronto said:**
> This might be relevant:
[http://ubuntuforums.org/showthread.php?p=3278523&highlight=8139#post3278523](http://ubuntuforums.org/showthread.php?p=3278523&highlight=8139#post3278523)

Most people post less info, lspci is useful.

Do the other laptops use a wireless connection?

I believe that is more of a problem with dual-booting; I am not dual-booting, but I tried the steps on that link... no dice.

> **bkratz said:**
> When searching this is actually your wireless card

description: Network controller 
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
vendor: Broadcom Corporation 

The other device mentioned is your ethernet controller. Will search for other information also.


This really "sticks out" in your listing

[ 16.874143] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/...devicefirmware](http://wireless.kernel.org/en/users/...devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 

You might try that


Especially this section of the above

Ubuntu/Debian..................

[LEFT] [FONT=Arial]I saw that too... I tried to run the command "[/FONT][FONT=Arial]sudo apt-get install b43-fwcutter" in the terminal, but it is saying that it can't find the package.[/FONT][/LEFT]

---

### Post by northd_tech on 2010-02-14
You might take a look at the links on this thread where someone else is having trouble with the Broadcom 4318:

[http://ubuntuforums.org/showthread.php?t=1406813&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=1406813&highlight=broadcom+4318)

---

### Post by Fletch71011 on 2010-02-15
> **northd_tech said:**
> You might take a look at the links on this thread where someone else is having trouble with the Broadcom 4318:

[http://ubuntuforums.org/showthread.php?t=1406813&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=1406813&highlight=broadcom+4318)

Ya, I saw that thread and tried all of that stuff, but it doesn't seem to help.  Maybe because those are all for older versions of Ubuntu?  Not sure.

---

### Post by northd_tech on 2010-02-15
> **Fletch71011 said:**
> 
                                 Module                  Size  Used by  
 [COLOR=Blue]**b43**                   122136  0  
 mac80211              181236  1 **b43**
 cfg80211               93052  2 **b43**,mac80211  
 led_class               4096  2 **b43**,sdhci  [/COLOR]  
 
 8139too                22620  0  
 8139cp                 19260  0  
 mii                     5212  2 8139too,8139cp  

 [COLOR=Blue]ssb                    35300  1 **b43**[/COLOR]  
 
**6 ) Network configuration**
                                   *-network:0              
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 2  
        bus info: pci@0000:0b:02.0  
        logical name: eth0  
        version: 10  
        serial: 00:c0:9f:6e:71:d8  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s  
        resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff  
   *-network:1  
        description: Network controller  
        product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  
        vendor: Broadcom Corporation  
        physical id: 3  
        bus info: pci@0000:0b:03.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master  
        configuration: driver=b43-pci-bridge latency=64  
        resources: irq:17 memory:c8206000-c8207fff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:90:4b:f5:57:2f  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
 
**7 ) Scan for networks:**
                                 wlan0     Failed to read scan data : Network is down

**8 ) Ubuntu Version: **
     Code:
     Ubuntu 9.10 
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     2.6.31-14-generic i686

It looks like you've got most of the Broadcom b43 modules loaded (the stuff in [COLOR=Blue]blue [/COLOR]above).

That one thread I linked to was for ubuntu 9.04 (Jaunty Jackalope), and I've actually had much better luck with that than 9.10 on 3 or more laptops now.

You've got a Realtek 8139C ethernet interface (that 8139 too, 8139c stuff below the [COLOR=Blue]blue[/COLOR] wireless modules above)- do you have a working cable connection?

I vaguely remember something about needing to blacklist one of the modules ("ssb" I seem to recall, when I was trying to set up wireless under a non-ubuntu version of Linux on my Broadcom 4321AG WiFi).  I ended up just using ndiswrapper for a while, since the 802.11(n) support isn't/wasn't very good for my 4321AG.  Then Broadcom released their proprietary "STA" driver, and that has worked extremely well for me (but is slower now than it used to be- this IPv6 problem it sounds like).

This was the original website I found the information about that b43 driver at- you probably want to read through some of that- it mentions the 4318 and that it is better supported there than my 4321AG is:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Here is their download page:

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

If you end up re-compiling the b43 driver from those sources, you might need to install the kernel header files first for the version of kernel that you usually run.  I can elaborate on that if you need me to, but you should be able to install those or check their status from the Synaptic Package Manager under the Administration menu.

One thing that I've heard works for some is to go into the Hardware Drivers (also under the Administration menu) and disable the proprietary b43 driver.  Wait a while (or else restart the ubuntu) and then re-Activate the b43 driver.  This has worked for some people with both the b43 and the STA driver (that my 4321AG seems to like).  You might need a 2nd reboot to see the wireless interface after Activation.

If you want to try the STA driver, you can download that directly from Broadcom at:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Post #9 at this thread is for a 4318 that someone got to work with the proprietary b43 driver under 9.10:

[http://ubuntuforums.org/showpost.php?p=8631764&postcount=9](http://ubuntuforums.org/showpost.php?p=8631764&postcount=9)

---

