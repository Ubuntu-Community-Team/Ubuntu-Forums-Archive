---
title: "Wireless Device Not Detected"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by jquill on 2009-08-28
I've been through many posts before getting to this point.  I've researched drivers, unmanaged issues, wireless issues, network management problems, run many recommended commands and I'M TROUGH!!!

I have Ubuntu 9.04 released April 2009 running on an Acer Aspire 3680 with Atheros AR242x wireless device with NetworkManager Applet 0.7.0.100.  Everything was running smooth for weeks until last evening I had to get froggy and install madwifi-tools through Synaptic and followed the Linux command lines provided on the HP website to install an HP Wireless Printer.  (The moral of that is do one thing at a time)  Once I rebooted the Network Manager Applet no longer recognized my wireless device.
 

 I have another Acer Aspire (9410) and although it has the Intel PRO/Wireless 3945ABG network  device, I thought I would match the packages loaded loaded on both machines through Synaptic Package Manager but that didn't work either.  I've tried to follow GNUSCI's advice in the “**HOWTO post a Wireless issue (ticket)”**but the device appears to have DIS-appeared.   
 

 The Network Manager Applet (NMA) works differently on the non functioning 3640 then it does on the 9410.  When you right click on the NMA on the 9410 it displays the “Enable Networking” and “Enable Wireless” selections but the NMA on the 3680 only displays the “Enable Networking” selection.  The “Edit Connections” parameters are identical on both machines.   
 
 **Detailed results from ****[B]gnusci's 10 Steps **[/B]**are as follows:**
 
 **[B]Step 1: Machine Brand and Model (Provided above.)**[/B]
 
 **[B]Step 2: Wireless Brand, Model and Wireless Chipset (LSPCI) Results;**[/B]
 
 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)  
 00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)  
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)  
 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)  
 0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller  
 0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)  
 
 **[B]Step 2: Wireless Brand, Model and Wireless Chipset (LSUSB) Results;**[/B]
 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 
 **[B]Step 2: Wireless Brand, Model and Wireless Chipset (LSPCI) Results;**[/B]
 

 lspci -nn | grep 'Wireless Brand' 

 No result however, provided above.
 
 **[B]Step 3: Check Interface (IFCONFIG) Results;**[/B]
 
 eth0      Link encap:Ethernet  HWaddr 00:1b:24:3b:b7:f4   
           inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::21b:24ff:fe3b:b7f4/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:12256 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:11998 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:10895435 (10.8 MB)  TX bytes:2226409 (2.2 MB)  
           Interrupt:16  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:32 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:32 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:2376 (2.3 KB)  TX bytes:2376 (2.3 KB)  
 
 **[B]Step 3: Check Interface (IWCONFIG) Result;**[/B]
 
 eth0      no wireless extensions.  
 

 pan0      no wireless extensions.  
 

 **Then the ****[B]Step 3: IWCONFIG WLAN0**[/B]command obviously resulted in “wlan0     No such device ”
 

 **[B]Step 4: Check for Module (LSMOD) Results;**[/B]
 

 Module                  Size  Used by  
 xt_limit               10116  8  
 xt_tcpudp              11008  7  
 ipt_LOG                13700  8  
 ipt_MASQUERADE         10752  0  
 xt_DSCP                11264  0  
 ipt_REJECT             11136  1  
 nf_conntrack_irc       13220  0  
 nf_conntrack_ftp       15652  0  
 xt_state               10112  6  
 i915                   67844  2  
 drm                    96424  3 i915  
 binfmt_misc            16776  1  
 ppdev                  15620  0  
 bridge                 56212  0  
 stp                    10500  1 bridge  
 bnep                   20224  2  
 input_polldev          11912  0  
 joydev                 18496  0  
 lp                     17156  0  
 parport                42220  2 ppdev,lp  
 snd_hda_intel         434100  3  
 snd_pcm_oss            46336  0  
 snd_mixer_oss          22656  1 snd_pcm_oss  
 iptable_nat            13700  0  
 nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat  
 snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss  
 nf_conntrack_ipv4      21388  9 iptable_nat,nf_nat  
 nf_conntrack           72008  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4  
 snd_seq_dummy          10756  0  
 nf_defrag_ipv4          9984  1 nf_conntrack_ipv4  
 snd_seq_oss            37760  0  
 iptable_mangle         10880  0  
 snd_seq_midi           14336  0  
 snd_rawmidi            29696  1 snd_seq_midi  
 snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi  
 snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              29704  2 snd_pcm,snd_seq  
 snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 iptable_filter         10752  1  
 pcmcia                 44748  0  
 ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter  
 iTCO_wdt               19108  0  
 iTCO_vendor_support    11652  1 iTCO_wdt  
 x_tables               23044  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables  
 acer_wmi               24260  0  
 psmouse                61972  0  
 tifm_7xx1              13824  0  
 ath_pci                99224  0  
 snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device  
 soundcore              15200  1 snd  
 intel_agp              34108  1  
 yenta_socket           32396  1  
 rsrc_nonstatic         19328  1 yenta_socket  
 pcspkr                 10496  0  
 led_class              12036  1 acer_wmi  
 serio_raw              13444  0  
 tifm_core              15900  1 tifm_7xx1  
 wlan                  210544  1 ath_pci  
 ath_hal               198864  1 ath_pci  
 snd_page_alloc         16904  2 snd_hda_intel,snd_pcm  
 agpgart                42696  3 drm,intel_agp  
 pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic  
 video                  25360  0  
 output                 11008  1 video  
 usbhid                 42336  0  
 sky2                   54916  0  
 fbcon                  46112  0  
 tileblit               10752  1 fbcon  
 font                   16384  1 fbcon  
 bitblit                13824  1 fbcon  
 softcursor              9984  1 bitblit  
 
 **[B]Step 5: Kernel Boot Messaes (DMESG) Result;**[/B]
 
 [    1.144269] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0200000-0xd02fffff]  
 [    1.144324] bus 00 -> node 0  
 [    1.144331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]  
 [    1.144722] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]  
 [    1.144875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]  
 [    1.145025] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]  
 [    1.145189] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]  
 [    1.149868] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11  
 [    1.149995] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)  
 [    1.150120] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)  
 [    1.150247] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10  
 [    1.150372] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)  
 [    1.150495] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)  
 [    1.150619] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)  
 [    1.150744] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)  
 [    1.151161] ACPI: WMI: Mapper loaded  
 [    1.151331] SCSI subsystem initialized  
 [    1.151371] libata version 3.00 loaded.  
 [    1.151415] usbcore: registered new interface driver usbfs  
 [    1.151432] usbcore: registered new interface driver hub  
 [    1.151462] usbcore: registered new device driver usb  
 [    1.151580] PCI: Using ACPI for IRQ routing  
 [    1.151584] pci 0000:00:1c.0: BAR 7: can't allocate resource  
 [    1.151586] pci 0000:00:1c.0: BAR 8: can't allocate resource  
 [    1.151588] pci 0000:00:1c.0: BAR 9: can't allocate resource  
 [    1.151591] pci 0000:00:1c.1: BAR 7: can't allocate resource  
 [    1.151593] pci 0000:00:1c.1: BAR 8: can't allocate resource  
 [    1.151595] pci 0000:00:1c.1: BAR 9: can't allocate resource  
 [    1.151597] pci 0000:00:1c.2: BAR 7: can't allocate resource  
 [    1.151599] pci 0000:00:1c.2: BAR 8: can't allocate resource  
 [    1.151601] pci 0000:00:1c.2: BAR 9: can't allocate resource  
 [    1.151717] Bluetooth: Core ver 2.13  
 [    1.151717] NET: Registered protocol family 31  
 [    1.151717] Bluetooth: HCI device and connection manager initialized  
 [    1.151717] Bluetooth: HCI socket layer initialized  
 [    1.151717] NET: Registered protocol family 8  
 [    1.151717] NET: Registered protocol family 20  
 [    1.151717] NetLabel: Initializing  
 [    1.151717] NetLabel:  domain hash size = 128  
 [    1.151717] NetLabel:  protocols = UNLABELED CIPSOv4  
 [    1.151717] NetLabel:  unlabeled traffic allowed by default  
 [    1.151717] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0  
 [    1.151717] hpet0: 3 comparators, 64-bit 14.318180 MHz counter  
 [    1.156072] AppArmor: AppArmor Filesystem Enabled  
 [    1.156080] pnp: PnP ACPI init  
 [    1.156080] ACPI: bus type pnp registered  
 [    1.157520] pnp 00:05: io resource (0x2e-0x2f) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157524] pnp 00:05: io resource (0x61-0x61) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157527] pnp 00:05: io resource (0x63-0x63) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157530] pnp 00:05: io resource (0x65-0x65) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157533] pnp 00:05: io resource (0x67-0x67) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157536] pnp 00:05: io resource (0x68-0x6f) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157539] pnp 00:05: io resource (0x80-0x80) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157543] pnp 00:05: io resource (0x92-0x92) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.157546] pnp 00:05: io resource (0xb2-0xb3) overlaps 0000:02:00.0 BAR 2 (0x0-0xff), disabling  
 [    1.159078] pnp: PnP ACPI: found 9 devices  
 [    1.159081] ACPI: ACPI bus type pnp unregistered  
 [    1.159084] PnPBIOS: Disabled by ACPI PNP  
 [    1.159094] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved  
 [    1.159098] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved  
 [    1.159100] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved  
 [    1.159103] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved  
 [    1.159106] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved  
 [    1.159109] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved  
 [    1.159112] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved  
 [    1.159115] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved  
 [    1.159121] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved  
 [    1.159128] system 00:05: ioport range 0x800-0x80f has been reserved  
 [    1.159130] system 00:05: ioport range 0x1000-0x107f has been reserved  
 [    1.159133] system 00:05: ioport range 0x1180-0x11bf has been reserved  
 [    1.159136] system 00:05: ioport range 0x1600-0x166f has been reserved  
 [    1.159139] system 00:05: ioport range 0xfe10-0xfe11 has been reserved  
 [    1.159142] system 00:05: ioport range 0xfe00-0xfe00 has been reserved  
 [    1.160017] Switched to high resolution mode on CPU 0  
 [    1.193990] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02  
 [    1.193994] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff  
 [    1.194000] pci 0000:00:1c.0:   MEM window: 0x34000000-0x340fffff  
 [    1.194005] pci 0000:00:1c.0:   PREFETCH window: disabled  
 [    1.194022] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03  
 [    1.194024] pci 0000:00:1c.1:   IO window: disabled  
 [    1.194030] pci 0000:00:1c.1:   MEM window: 0x34100000-0x341fffff  
 [    1.194035] pci 0000:00:1c.1:   PREFETCH window: disabled  
 [    1.194043] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04  
 [    1.194045] pci 0000:00:1c.2:   IO window: disabled  
 [    1.194051] pci 0000:00:1c.2:   MEM window: disabled  
 [    1.194055] pci 0000:00:1c.2:   PREFETCH window: disabled  
 [    1.194065] pci 0000:0a:09.0: CardBus bridge, secondary bus 0000:0b  
 [    1.194068] pci 0000:0a:09.0:   IO window: 0x003000-0x0030ff  
 [    1.194073] pci 0000:0a:09.0:   IO window: 0x003400-0x0034ff  
 [    1.194079] pci 0000:0a:09.0:   PREFETCH window: 0x30000000-0x33ffffff  
 [    1.194085] pci 0000:0a:09.0:   MEM window: 0x38000000-0x3bffffff  
 [    1.194091] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0a  
 [    1.194095] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff  
 [    1.194101] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xd02fffff  
 [    1.194106] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff  
 [    1.194122] pci 0000:00:1c.0: enabling device (0000 -> 0003)  
 [    1.194130] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    1.194137] pci 0000:00:1c.0: setting latency timer to 64  
 [    1.194146] pci 0000:00:1c.1: enabling device (0000 -> 0002)  
 [    1.194151] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17  
 [    1.194157] pci 0000:00:1c.1: setting latency timer to 64  
 [    1.194167] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    1.194173] pci 0000:00:1c.2: setting latency timer to 64  
 [    1.194179] pci 0000:00:1e.0: enabling device (0004 -> 0007)  
 [    1.194185] pci 0000:00:1e.0: setting latency timer to 64  
 [    1.194194] pci 0000:0a:09.0: enabling device (0000 -> 0003)  
 [    1.194200] pci 0000:0a:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [    1.194208] bus: 00 index 0 io port: [0x00-0xffff]  
 [    1.194211] bus: 00 index 1 mmio: [0x000000-0xffffffff]  
 [    1.194213] bus: 02 index 0 io port: [0x2000-0x2fff]  
 [    1.194215] bus: 02 index 1 mmio: [0x34000000-0x340fffff]  
 [    1.194218] bus: 02 index 2 mmio: [0x0-0xfffff]  
 [    1.194219] bus: 02 index 3 mmio: [0x0-0x0]  
 [    1.194222] bus: 03 index 0 mmio: [0x0-0xfff]  
 [    1.194224] bus: 03 index 1 mmio: [0x34100000-0x341fffff]  
 [    1.194226] bus: 03 index 2 mmio: [0x0-0xfffff]  
 [    1.194228] bus: 03 index 3 mmio: [0x0-0x0]  
 [    1.194230] bus: 04 index 0 mmio: [0x0-0xfff]  
 [    1.194232] bus: 04 index 1 mmio: [0x0-0xfffff]  
 [    1.194234] bus: 04 index 2 mmio: [0x0-0xfffff]  
 [    1.194236] bus: 04 index 3 mmio: [0x0-0x0]  
 [    1.194238] bus: 0a index 0 io port: [0x3000-0x3fff]  
 [    1.194240] bus: 0a index 1 mmio: [0xd0200000-0xd02fffff]  
 [    1.194243] bus: 0a index 2 mmio: [0x30000000-0x33ffffff]  
 [    1.194245] bus: 0a index 3 io port: [0x00-0xffff]  
 [    1.194247] bus: 0a index 4 mmio: [0x000000-0xffffffff]  
 [    1.194249] bus: 0b index 0 io port: [0x3000-0x30ff]  
 [    1.194251] bus: 0b index 1 io port: [0x3400-0x34ff]  
 [    1.194254] bus: 0b index 2 mmio: [0x30000000-0x33ffffff]  
 [    1.194256] bus: 0b index 3 mmio: [0x38000000-0x3bffffff]  
 [    1.194266] NET: Registered protocol family 2  
 [    1.194384] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)  
 [    1.194598] TCP established hash table entries: 16384 (order: 5, 131072 bytes)  
 [    1.194676] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)  
 [    1.194757] TCP: Hash tables configured (established 16384 bind 16384)  
 [    1.194759] TCP reno registered  
 [    1.194834] NET: Registered protocol family 1  
 [    1.194953] checking if image is initramfs... it is  
 [    1.853125] Freeing initrd memory: 7376k freed  
 [    1.853172] Simple Boot Flag at 0x36 set to 0x1  
 [    1.853254] cpufreq: No nForce2 chipset.  
 [    1.853421] audit: initializing netlink socket (disabled)  
 [    1.853441] type=2000 audit(1251483674.852:1): initialized  
 [    1.861101] HugeTLB registered 4 MB page size, pre-allocated 0 pages  
 [    1.862386] VFS: Disk quotas dquot_6.5.1  
 [    1.862442] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)  
 [    1.863047] fuse init (API version 7.10)  
 [    1.863129] msgmni has been set to 975  
 [    1.863308] alg: No test for stdrng (krng)  
 [    1.863319] io scheduler noop registered  
 [    1.863322] io scheduler anticipatory registered  
 [    1.863323] io scheduler deadline registered  
 [    1.863339] io scheduler cfq registered (default)  
 [    1.863356] pci 0000:00:02.0: Boot video device  
 [    1.867487] pcieport-driver 0000:00:1c.0: setting latency timer to 64  
 [    1.867539] pcieport-driver 0000:00:1c.0: found MSI capability  
 [    1.867577] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X  
 [    1.867593] pci_express 0000:00:1c.0:pcie00: allocate port service  
 [    1.867608] pci_express 0000:00:1c.0:pcie02: allocate port service  
 [    1.867620] pci_express 0000:00:1c.0:pcie03: allocate port service  
 [    1.867692] pcieport-driver 0000:00:1c.1: setting latency timer to 64  
 [    1.867740] pcieport-driver 0000:00:1c.1: found MSI capability  
 [    1.867773] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X  
 [    1.867789] pci_express 0000:00:1c.1:pcie00: allocate port service  
 [    1.867803] pci_express 0000:00:1c.1:pcie02: allocate port service  
 [    1.867818] pci_express 0000:00:1c.1:pcie03: allocate port service  
 [    1.867890] pcieport-driver 0000:00:1c.2: setting latency timer to 64  
 [    1.867938] pcieport-driver 0000:00:1c.2: found MSI capability  
 [    1.867971] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X  
 [    1.867987] pci_express 0000:00:1c.2:pcie00: allocate port service  
 [    1.868011] pci_express 0000:00:1c.2:pcie02: allocate port service  
 [    1.868023] pci_express 0000:00:1c.2:pcie03: allocate port service  
 [    1.868102] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    1.868190] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    1.871664] ACPI: AC Adapter [ACAD] (on-line)  
 [    1.871734] ACPI: Battery Slot [BAT1] (battery absent)  
 [    1.871810] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0  
 [    1.871813] ACPI: Power Button (FF) [PWRF]  
 [    1.871863] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1  
 [    1.871931] ACPI: Lid Switch [LID]  
 [    1.871974] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2  
 [    1.871977] ACPI: Power Button (CM) [PWRB]  
 [    1.872033] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3  
 [    1.872035] ACPI: Sleep Button (CM) [SLPB]  
 [    1.872936] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])  
 [    1.872961] processor ACPI_CPU:00: registered as cooling_device0  
 [    1.872965] ACPI: Processor [CPU0] (supports 8 throttling states)  
 [    1.878426] thermal LNXTHERM:01: registered as thermal_zone0  
 [    1.884350] ACPI: Thermal Zone [THRM] (55 C)  
 [    1.884391] isapnp: Scanning for PnP cards...  
 [    2.238278] isapnp: No Plug & Play device found  
 [    2.240304] Serial: 8250/16550 driver4 ports, IRQ sharing enabled  
 [    2.241272] brd: module loaded  
 [    2.241567] loop: module loaded  
 [    2.241639] Fixed MDIO Bus: probed  
 [    2.241645] PPP generic driver version 2.4.2  
 [    2.241705] input: Macintosh mouse button emulation as /devices/virtual/input/input4  
 [    2.241736] Driver 'sd' needs updating - please use bus_type methods  
 [    2.241745] Driver 'sr' needs updating - please use bus_type methods  
 [    2.241812] ata_piix 0000:00:1f.2: version 2.12  
 [    2.241834] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    2.241838] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]  
 [    2.396020] ata_piix 0000:00:1f.2: setting latency timer to 64  
 [    2.396112] scsi0 : ata_piix  
 [    2.396203] scsi1 : ata_piix  
 [    2.396334] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14  
 [    2.396337] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15  
 [    2.560466] ata1.00: ATA-7: TOSHIBA MK8034GSX, AH301J, max UDMA/100  
 [    2.560469] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)  
 [    2.568481] ata1.00: configured for UDMA/100  
 [    2.732491] ata2.00: ATAPI: Optiarc CD-RW CRX880A, KX07, max UDMA/33  
 [    2.748442] ata2.00: configured for UDMA/33  
 [    2.748932] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK8034GS AH30 PQ: 0 ANSI: 5  
 [    2.749032] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)  
 [    2.749050] sd 0:0:0:0: [sda] Write Protect is off  
 [    2.749053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    2.749079] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    2.749145] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)  
 [    2.749160] sd 0:0:0:0: [sda] Write Protect is off  
 [    2.749162] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    2.749186] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    2.749190]  sda: sda1 sda2 < sda5 >  
 [    2.808311] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    2.808355] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    2.809272] scsi 1:0:0:0: CD-ROM            Optiarc  CD-RW CRX880A    KX07 PQ: 0 ANSI: 5  
 [    2.813620] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray  
 [    2.813624] Uniform CD-ROM driver Revision: 3.20  
 [    2.813713] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    2.813750] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    2.814315] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    2.814339] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    2.814363] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    2.814367] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    2.814428] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1  
 [    2.818351] ehci_hcd 0000:00:1d.7: debug port 1  
 [    2.818358] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported  
 [    2.818374] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0644000  
 [    2.832008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    2.832091] usb usb1: configuration #1 chosen from 1 choice  
 [    2.832117] hub 1-0:1.0: USB hub found  
 [    2.832125] hub 1-0:1.0: 8 ports detected  
 [    2.832239] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    2.832253] uhci_hcd: USB Universal Host Controller Interface driver  
 [    2.832282] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    2.832289] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    2.832292] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    2.832331] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2  
 [    2.832358] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820  
 [    2.832430] usb usb2: configuration #1 chosen from 1 choice  
 [    2.832457] hub 2-0:1.0: USB hub found  
 [    2.832464] hub 2-0:1.0: 2 ports detected  
 [    2.832543] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    2.832549] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    2.832553] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    2.832592] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3  
 [    2.832626] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840  
 [    2.832697] usb usb3: configuration #1 chosen from 1 choice  
 [    2.832720] hub 3-0:1.0: USB hub found  
 [    2.832727] hub 3-0:1.0: 2 ports detected  
 [    2.832807] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    2.832814] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    2.832817] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    2.832855] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4  
 [    2.832891] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860  
 [    2.832969] usb usb4: configuration #1 chosen from 1 choice  
 [    2.832992] hub 4-0:1.0: USB hub found  
 [    2.832999] hub 4-0:1.0: 2 ports detected  
 [    2.833078] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16  
 [    2.833084] uhci_hcd 0000:00:1d.3: setting latency timer to 64  
 [    2.833088] uhci_hcd 0000:00:1d.3: UHCI Host Controller  
 [    2.833134] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5  
 [    2.833166] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880  
 [    2.833239] usb usb5: configuration #1 chosen from 1 choice  
 [    2.833265] hub 5-0:1.0: USB hub found  
 [    2.833271] hub 5-0:1.0: 2 ports detected  
 [    2.833399] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12  
 [    2.846870] i8042.c: Detected active multiplexing controller, rev 1.1.  
 [    2.853105] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    2.853111] serio: i8042 AUX0 port at 0x60,0x64 irq 12  
 [    2.853113] serio: i8042 AUX1 port at 0x60,0x64 irq 12  
 [    2.853116] serio: i8042 AUX2 port at 0x60,0x64 irq 12  
 [    2.853118] serio: i8042 AUX3 port at 0x60,0x64 irq 12  
 [    2.853279] mice: PS/2 mouse device common for all mice  
 [    2.853460] rtc_cmos 00:06: RTC can wake from S4  
 [    2.853501] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0  
 [    2.853533] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs  
 [    2.853598] device-mapper: uevent: version 1.0.3  
 [    2.853705] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]  
 [    2.853752] device-mapper: multipath: version 1.0.5 loaded  
 [    2.853755] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    2.853833] EISA: Probing bus 0 at eisa.0  
 [    2.853840] Cannot allocate resource for EISA slot 1  
 [    2.853843] Cannot allocate resource for EISA slot 2  
 [    2.853845] Cannot allocate resource for EISA slot 3  
 [    2.853866] EISA: Detected 0 cards.  
 [    2.853926] cpuidle: using governor ladder  
 [    2.853984] cpuidle: using governor menu  
 [    2.854461] TCP cubic registered  
 [    2.854558] NET: Registered protocol family 10  
 [    2.854946] lo: Disabled Privacy Extensions  
 [    2.855241] NET: Registered protocol family 17  
 [    2.855260] Bluetooth: L2CAP ver 2.11  
 [    2.855262] Bluetooth: L2CAP socket layer initialized  
 [    2.855265] Bluetooth: SCO (Voice Link) ver 0.6  
 [    2.855266] Bluetooth: SCO socket layer initialized  
 [    2.855294] Bluetooth: RFCOMM socket layer initialized  
 [    2.855301] Bluetooth: RFCOMM TTY layer initialized  
 [    2.855303] Bluetooth: RFCOMM ver 1.10  
 [    2.855343] Using IPI No-Shortcut mode  
 [    2.855418] registered taskstats version 1  
 [    2.855523]   Magic number: 5:848:393  
 [    2.855605] rtc_cmos 00:06: setting system clock to 2009-08-28 18:21:16 UTC (1251483676)  
 [    2.855608] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    2.855610] EDD information not available.  
 [    2.855897] Freeing unused kernel memory: 532k freed  
 [    2.856033] Write protecting the kernel text: 4116k  
 [    2.856071] Write protecting the kernel read-only data: 1528k  
 [    2.899527] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5  
 [    3.328022] usb 3-2: new low speed USB device using uhci_hcd and address 2  
 [    3.448754] sky2 driver version 1.22  
 [    3.448802] sky2 0000:02:00.0: enabling device (0000 -> 0003)  
 [    3.448809] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    3.448824] sky2 0000:02:00.0: setting latency timer to 64  
 [    3.448870] sky2 0000:02:00.0: Yukon-2 FE chip revision 1  
 [    3.512635] sky2 0000:02:00.0: Marvell Yukon 88E8038 Fast Ethernet Controller  
 [    3.512637]  Part Number: Yukon 88E8038  
 [    3.512639]  Engineering Level: Rev. 1.4  
 [    3.512641]  Manufacturer: Marvell  
 [    3.512714] sky2 0000:02:00.0: irq 2300 for MSI/MSI-X  
 [    3.517891] sky2 eth0: addr 00:1b:24:3b:b7:f4  
 [    3.574761] usb 3-2: configuration #1 chosen from 1 choice  
 [    3.798484] usbcore: registered new interface driver hiddev  
 [    3.801656] Marking TSC unstable due to TSC halts in idle  
 [    3.806468] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input6  
 [    3.806721] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.1-2/input0  
 [    3.806741] usbcore: registered new interface driver usbhid  
 [    3.806745] usbhid: v2.6:USB HID core driver  
 [    3.837194] PM: Starting manual resume from disk  
 [    3.837197] PM: Resume from partition 8:5  
 [    3.837199] PM: Checking hibernation image.  
 [    3.837483] PM: Resume from disk failed.  
 [    3.880885] kjournald starting.  Commit interval 5 seconds  
 [    3.880896] EXT3-fs: mounted filesystem with ordered data mode.  
 [   10.928809] udev: starting version 141  
 [   11.221750] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input7  
 [   11.248237] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)  
 [   11.723687] Linux agpgart interface v0.103  
 [   11.759826] intel_rng: FWH not detected  
 [   11.831773] ath_hal: module license 'Proprietary' taints kernel.  
 [   11.833331] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)  
 [   11.847213] wlan: 0.9.4  
 [   12.283807] input: PC Speaker as /devices/platform/pcspkr/input/input8  
 [   12.300254] yenta_cardbus 0000:0a:09.0: CardBus bridge found [1025:0110]  
 [   12.300279] yenta_cardbus 0000:0a:09.0: Using CSCINT to route CSC interrupts to PCI  
 [   12.300282] yenta_cardbus 0000:0a:09.0: Routing CardBus interrupts to PCI  
 [   12.300288] yenta_cardbus 0000:0a:09.0: TI: mfunc 0x01321b22, devctl 0x66  
 [   12.317987] agpgart-intel 0000:00:00.0: Intel 945GM Chipset  
 [   12.318221] agpgart-intel 0000:00:00.0: detected 7932K stolen memory  
 [   12.321176] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000  
 [   12.470404] ath_pci: 0.9.4  
 [   12.470659] ath_pci 0000:03:00.0: enabling device (0000 -> 0002)  
 [   12.470669] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   12.470684] ath_pci 0000:03:00.0: setting latency timer to 64  
 [   12.519111] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)  
 [   12.519127] ath_pci 0000:03:00.0: PCI INT A disabled  
 [   12.533139] yenta_cardbus 0000:0a:09.0: ISA IRQ mask 0x0cf8, PCI irq 20  
 [   12.533145] yenta_cardbus 0000:0a:09.0: Socket status: 30000006  
 [   12.533149] pci_bus 0000:0a: Raising subordinate bus# of parent bus (#0a) from #0b to #0e  
 [   12.533158] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff  
 [   12.533162] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.  
 [   12.533368] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff  
 [   12.533371] yenta_cardbus 0000:0a:09.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff  
 [   12.538244] tifm_7xx1 0000:0a:09.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20  
 [   12.551981] acer-wmi: Acer Laptop ACPI-WMI Extras  
 [   12.575375] acer-wmi: software RFKILL enabled  
 [   12.628760] iTCO_vendor_support: vendor-support=0  
 [   12.630882] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05  
 [   12.631028] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)  
 [   12.631123] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)  
 [   12.648071] ip_tables: (C) 2000-2006 Netfilter Core Team  
 [   12.842956] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume  
 [   12.885927] nf_conntrack version 0.5.0 (8041 buckets, 32164 max)  
 [   12.886162] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use  
 [   12.886165] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or  
 [   12.886168] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.  
 [   13.095363] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [   13.095504] HDA Intel 0000:00:1b.0: setting latency timer to 64  
 [   13.132964] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.  
 [   13.134977] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7  
 [   13.135822] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.  
 [   13.136534] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.  
 [   13.137457] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.  
 [   13.405517] lp: driver loaded but no devices found  
 [   13.467112] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k  
 [   13.801577] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1280b1, caps: 0xa04713/0x204000  
 [   13.867242] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9  
 [   14.000465] EXT3 FS on sda1, internal journal  
 [   14.500074] Clocksource tsc unstable (delta = -300263435 ns)  
 [   15.130959] type=1505 audit(1251483688.772:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2067  
 [   15.183921] type=1505 audit(1251483688.824:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2071  
 [   15.184106] type=1505 audit(1251483688.828:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2071  
 [   15.184160] type=1505 audit(1251483688.828:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2071  
 [   15.184208] type=1505 audit(1251483688.828:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2071  
 [   15.338848] type=1505 audit(1251483688.980:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2076  
 [   15.339069] type=1505 audit(1251483688.980:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2076  
 [   15.369357] type=1505 audit(1251483689.012:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2080  
 [   18.445578] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   18.445582] Bluetooth: BNEP filters: protocol multicast  
 [   18.488930] Bridge firewalling registered  
 [   20.188385] ppdev: user-space parallel port driver  
 [   21.880112] [drm] Initialized drm 1.1.0 20060810  
 [   21.896432] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   21.896440] pci 0000:00:02.0: setting latency timer to 64  
 [   21.896608] [drm] Initialized i915 1.6.0 20080730 on minor 0  
 [   21.898983] [drm:i915_setparam] *ERROR* unknown parameter 4  
 [   21.899008] [drm:i915_getparam] *ERROR* Unknown parameter 6  
 [   23.515200] [drm:i915_getparam] *ERROR* Unknown parameter 6  
 [   24.358823] sky2 eth0: enabling interface  
 [   24.358884] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   35.078600] [drm:i915_getparam] *ERROR* Unknown parameter 6  
 [   44.133007] CPU0 attaching NULL sched-domain.  
 [   44.144065] CPU0 attaching NULL sched-domain.  
 [   47.833657] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.  
 [   72.618270] sky2 eth0: disabling interface  
 [  116.436912] sky2 eth0: enabling interface  
 [  116.436978] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [  118.285308] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both  
 [  118.285362] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  
 [  128.456039] eth0: no IPv6 routers present  
 [  462.892542] sky2 eth0: disabling interface  
 [  467.131958] sky2 eth0: enabling interface  
 [  467.132049] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [  539.901608] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both  
 [  539.901671] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  
 [  550.016092] eth0: no IPv6 routers present  
 [  600.067181] sky2 eth0: disabling interface  
 [  603.901527] sky2 eth0: enabling interface  
 [  603.901593] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [  675.295683] device lo entered promiscuous mode  
 [  772.377420] device lo left promiscuous mode  
 [  824.129028] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both  
 [  824.129082] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready  
 [  834.676101] eth0: no IPv6 routers present  
 
 **[B]STEP 6: Network Configuration (sudo lshw -C network) Result;**[/B]
 
  *-network                
        description: Ethernet interface  
        product: 88E8038 PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 14  
        serial: 00:1b:24:3b:b7:f4  
        size: 100MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.6 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s  
   *-network UNCLAIMED  
        description: Ethernet controller  
        product: AR242x 802.11abg Wireless PCI Express Adapter  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix cap_list  
        configuration: latency=0  
   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: e6:fa:b3:91:9e:dd  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes  
 
 **[B]STEP 7: Scan for Networks (IWLIST) Result;**[/B]
 
 Usage: iwlist [interface] scanning [essid NNN] [last]  
               [interface] frequency  
               [interface] channel  
               [interface] bitrate  
               [interface] rate  
               [interface] encryption  
               [interface] keys  
               [interface] power  
               [interface] txpower  
               [interface] retry  
               [interface] ap  
               [interface] accesspoints  
               [interface] peers  
               [interface] event  
               [interface] auth  
               [interface] wpakeys  
               [interface] genie  
               [interface] modulation  
 
 **[B]STEP 7: Scan for Networks (IWLIST SCAN) Result;**[/B]
 
 Again, an expected “iwlist: unknown command `wlan0' (check 'iwlist –help'). ” result.
 
 **[B]STEP 8: Ubuntu Version (LSB_RELEASE -D) Result;**[/B]
 
 Description:    Ubuntu 9.04  
 
**[B]STEP 9: Kernel/architecture (including 32 vs. 64 bit) (UNAMR -MR) Result;**[/B]
 
 2.6.28-15-generic i686  
 
**[B]STEP 10: **[/B]**[B]Restarting the network (SUDO /ETC/INIT.D/NETORKING RESTART) Result;**[/B]
 
Reconfiguring network interfaces...
 Ignoring unknown interface eth0=eth0.  
 

 **[B]Man I hope this helps...**[/B]

---

### Post by Asopiram on 2009-08-30
I too am having the same issue...I don't even see any drivers in jockey at all..Compaq CQ60-211DX

$ uname -a
Linux LT2 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:53:e2:87
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.6.102 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:53:e2:87  
          inet addr:192.168.6.102  Bcast:192.168.6.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe53:e287/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1181132 (1.1 MB)  TX bytes:138290 (138.2 KB)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0  
          RX bytes:2468 (2.4 KB)  TX bytes:2468 (2.4 KB)

Maybe posting here will help us both out... I have searched around extensively I think finding the answer to this mystery will be a huge donation to the Ubuntu community.

---

### Post by jquill on 2009-08-31
I sure hope so, I provided ALL of the data requested but it's been posted for days and the lack of a response worries me.  I've been researching all of the posted wireless issues and I'm finding that my inability to detect my wireless device my be linked to the HP Printer install forcing proxy issues.

---

### Post by Asopiram on 2009-08-31
Don't Fret to much.. With the 2 of us checking in and following up on this then we may have a chance... here is what I have found out...Make sure that ath_pci and ath_hal are blacklisted in blacklist.conf.. that ath5k is commented out in madwifi.conf and that ath5k is commented out in blacklist-ath_pci.conf all these files can be reached by 

sudo gedit /etc/modprobe.d/blacklist.conf madwifi.conf blacklist-ath_pci.conf

check iwconfig for your wireless to pop up.. check ifconfig also, lshw -C network should list it also... lsmod will tell you if ath5k is up and running also... 

These are just a bit of tidbits to keep the hope up...

Also try and unsecure your wireless network just to make sure that it can be reached...

---

### Post by Asopiram on 2009-09-05
I have now successfully made wireless to work.. I didn't realize that you had a HP printer also.. I too have a HP 6300 Photosmart printer on my wireless network and Ubuntu and it work well together.

I was goofing around with the wireless button on the laptop next to the power button and noticed that my network kept popping up. Reverting from WICD back to Network Manager I have set up my wireless and am connecting to my secure network. WPA2 .... 

Make sure that ath5k is installed and that the entries are blacklisted. madwifi should not be running.. I hope this helps. I am excited to report this....I too have been working on this for about 15 to 20 days now....

---

### Post by amateur-scientist on 2009-09-15
I clobbered my wireless (it disappeared completely) by installing camorama and or gqcam while trying to fix the webcam. Beats me why that happened. Lo and behold, the blacklist advice (#4) by asopiram fixed the wireless for me. Thanks!

---

