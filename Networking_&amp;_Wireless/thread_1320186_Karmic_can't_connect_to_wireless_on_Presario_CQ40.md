---
title: "Karmic can't connect to wireless on Presario CQ40"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by ysNoi on 2009-11-09
Hi..!

I have installed a fresh Karmic on my COMPAQ Presario CQ40. I have no problem connecting on wireless with the Jaunty before. Please help me..
As of now, I'm using a wired connection to access the net..

Details:

[COLOR="Blue"]Machine Brand and Model:[/COLOR]
COMPAQ Presario CQ40

[COLOR="Blue"]Wireless Brand, Model and Wireless Chipset:[/COLOR]
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 192f:0116 Avago Technologies, Pte. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b098 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[COLOR="Blue"]Interface:[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:b1:8f:31  
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:feb1:8f31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3857666 (3.8 MB)  TX bytes:278224 (278.2 KB)
          Interrupt:32 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6349 (6.3 KB)  TX bytes:6349 (6.3 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

[COLOR="Blue"]Modules:[/COLOR]
Module                  Size  Used by
binfmt_misc             8356  1 
b43                   122136  0 
ppdev                   6688  0 
sdhci_pci               7100  0 
lp                      8964  0 
joydev                 10272  0 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
mac80211              181236  1 b43
jmb38x_ms               9600  0 
sdhci                  17472  1 sdhci_pci
cfg80211               93052  2 b43,mac80211
memstick               10072  1 jmb38x_ms
parport                35340  2 ppdev,lp
btusb                  11856  2 
led_class               4096  2 b43,sdhci
uvcvideo               59080  0 
psmouse                56180  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3100  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lirc_ene0100            8096  0 
lirc_dev               10804  1 lirc_ene0100
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ssb                    35300  1 b43
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

[COLOR="Blue"]Kernel Boot Messages:[/COLOR]
[    4.153249] pcieport-driver 0000:00:1c.5: irq 29 for MSI/MSI-X
[    4.153261] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    4.153376] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.153672] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.284084] ACPI: AC Adapter [AC] (on-line)
[    4.284161] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    4.284164] ACPI: Power Button [PWRF]
[    4.284214] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    4.284216] ACPI: Power Button [PWRB]
[    4.284264] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    4.284337] ACPI: Lid Switch [LID0]
[    4.284381] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    4.284388] ACPI: Sleep Button [SLPB]
[    4.319579] fan PNP0C0B:00: registered as cooling_device0
[    4.319586] ACPI: Fan [FAN] (on)
[    4.320616] ACPI: SSDT 3da77c18 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    4.321290] ACPI: SSDT 3da75618 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    4.321868] Monitor-Mwait will be used to enter C-1 state
[    4.321895] Monitor-Mwait will be used to enter C-2 state
[    4.321903] Marking TSC unstable due to TSC halts in idle
[    4.321918] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.321938] processor LNXCPU:00: registered as cooling_device1
[    4.321943] ACPI: Processor [CPU0] (supports 8 throttling states)
[    4.322456] ACPI: SSDT 3da76e18 001CF (v01  PmRef    ApIst 00003000 INTL 20060912)
[    4.323006] ACPI: SSDT 3da77f18 0008D (v01  PmRef    ApCst 00003000 INTL 20060912)
[    4.323680] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    4.323701] processor LNXCPU:01: registered as cooling_device2
[    4.323705] ACPI: Processor [CPU1] (supports 8 throttling states)
[    4.470449] thermal LNXTHERM:01: registered as thermal_zone0
[    4.470458] ACPI: Thermal Zone [THRM] (48 C)
[    4.470522] isapnp: Scanning for PnP cards...
[    4.715148] ACPI: Battery Slot [BAT0] (battery present)
[    4.824860] isapnp: No Plug & Play device found
[    4.826145] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    4.827560] brd: module loaded
[    4.828026] loop: module loaded
[    4.828106] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    4.828187] ahci 0000:00:1f.2: version 3.0
[    4.828203]   alloc irq_desc for 21 on node -1
[    4.828205]   alloc kstat_irqs on node -1
[    4.828213] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.828251]   alloc irq_desc for 30 on node -1
[    4.828253]   alloc kstat_irqs on node -1
[    4.828264] ahci 0000:00:1f.2: irq 30 for MSI/MSI-X
[    4.828363] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    4.828366] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ems 
[    4.828372] ahci 0000:00:1f.2: setting latency timer to 64
[    4.848095] scsi0 : ahci
[    4.848212] scsi1 : ahci
[    4.848279] scsi2 : ahci
[    4.848336] scsi3 : ahci
[    4.848394] scsi4 : ahci
[    4.848453] scsi5 : ahci
[    4.848723] ata1: SATA max UDMA/133 abar m2048@0x5c804000 port 0x5c804100 irq 30
[    4.848727] ata2: SATA max UDMA/133 abar m2048@0x5c804000 port 0x5c804180 irq 30
[    4.848729] ata3: DUMMY
[    4.848731] ata4: DUMMY
[    4.848734] ata5: SATA max UDMA/133 abar m2048@0x5c804000 port 0x5c804300 irq 30
[    4.848738] ata6: SATA max UDMA/133 abar m2048@0x5c804000 port 0x5c804380 irq 30
[    4.849746] Fixed MDIO Bus: probed
[    4.849780] PPP generic driver version 2.4.2
[    4.849895] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.849919] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.849939] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.849943] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.849995] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.853918] ehci_hcd 0000:00:1a.7: debug port 1
[    4.853925] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.853998] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x5c804c00
[    4.868018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.868094] usb usb1: configuration #1 chosen from 1 choice
[    4.868123] hub 1-0:1.0: USB hub found
[    4.868132] hub 1-0:1.0: 4 ports detected
[    4.868195]   alloc irq_desc for 20 on node -1
[    4.868198]   alloc kstat_irqs on node -1
[    4.868204] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.868214] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.868218] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.868250] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.872168] ehci_hcd 0000:00:1d.7: debug port 1
[    4.872175] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.872189] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x5c804800
[    4.884019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.884092] usb usb2: configuration #1 chosen from 1 choice
[    4.884119] hub 2-0:1.0: USB hub found
[    4.884126] hub 2-0:1.0: 8 ports detected
[    4.884199] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.884219] uhci_hcd: USB Universal Host Controller Interface driver
[    4.884248] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.884256] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.884260] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.884292] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.884331] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080e0
[    4.884415] usb usb3: configuration #1 chosen from 1 choice
[    4.884442] hub 3-0:1.0: USB hub found
[    4.884449] hub 3-0:1.0: 2 ports detected
[    4.884498] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.884517] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.884521] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.884556] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.884593] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000080c0
[    4.884672] usb usb4: configuration #1 chosen from 1 choice
[    4.884701] hub 4-0:1.0: USB hub found
[    4.884708] hub 4-0:1.0: 2 ports detected
[    4.884764] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.884771] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.884775] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.884809] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    4.884837] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000080a0
[    4.884920] usb usb5: configuration #1 chosen from 1 choice
[    4.884945] hub 5-0:1.0: USB hub found
[    4.884952] hub 5-0:1.0: 2 ports detected
[    4.884998]   alloc irq_desc for 22 on node -1
[    4.885000]   alloc kstat_irqs on node -1
[    4.885006] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.885013] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.885016] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.885046] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.885082] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00008080
[    4.885161] usb usb6: configuration #1 chosen from 1 choice
[    4.885187] hub 6-0:1.0: USB hub found
[    4.885194] hub 6-0:1.0: 2 ports detected
[    4.885243] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.885250] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.885253] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.885283] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.885312] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008060
[    4.885392] usb usb7: configuration #1 chosen from 1 choice
[    4.885419] hub 7-0:1.0: USB hub found
[    4.885425] hub 7-0:1.0: 2 ports detected
[    4.885472] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.885478] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.885482] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.885521] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    4.885559] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00008040
[    4.885636] usb usb8: configuration #1 chosen from 1 choice
[    4.885663] hub 8-0:1.0: USB hub found
[    4.885669] hub 8-0:1.0: 2 ports detected
[    4.885771] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[    4.930749] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.930755] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.930821] mice: PS/2 mouse device common for all mice
[    4.930952] rtc_cmos 00:03: RTC can wake from S4
[    4.930985] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.931017] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.931127] device-mapper: uevent: version 1.0.3
[    4.933238] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    4.933337] device-mapper: multipath: version 1.1.0 loaded
[    4.933340] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.933467] EISA: Probing bus 0 at eisa.0
[    4.933474] Cannot allocate resource for EISA slot 1
[    4.933476] Cannot allocate resource for EISA slot 2
[    4.933478] Cannot allocate resource for EISA slot 3
[    4.933480] Cannot allocate resource for EISA slot 4
[    4.933482] Cannot allocate resource for EISA slot 5
[    4.933484] Cannot allocate resource for EISA slot 6
[    4.933486] Cannot allocate resource for EISA slot 7
[    4.933487] Cannot allocate resource for EISA slot 8
[    4.933489] EISA: Detected 0 cards.
[    4.933658] cpuidle: using governor ladder
[    4.933755] cpuidle: using governor menu
[    4.934265] TCP cubic registered
[    4.934421] NET: Registered protocol family 10
[    4.934886] lo: Disabled Privacy Extensions
[    4.935232] NET: Registered protocol family 17
[    4.935251] Bluetooth: L2CAP ver 2.13
[    4.935252] Bluetooth: L2CAP socket layer initialized
[    4.935255] Bluetooth: SCO (Voice Link) ver 0.6
[    4.935257] Bluetooth: SCO socket layer initialized
[    4.935302] Bluetooth: RFCOMM TTY layer initialized
[    4.935305] Bluetooth: RFCOMM socket layer initialized
[    4.935307] Bluetooth: RFCOMM ver 1.11
[    4.935813] Using IPI No-Shortcut mode
[    4.935882] PM: Resume from disk failed.
[    4.935898] registered taskstats version 1
[    4.936069]   Magic number: 1:264:567
[    4.936073] misc network_latency: hash matches
[    4.936175] rtc_cmos 00:03: setting system clock to 2009-11-09 05:35:55 UTC (1257744955)
[    4.936178] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.936180] EDD information not available.
[    4.966405] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    5.172095] ata2: SATA link down (SStatus 0 SControl 300)
[    5.172132] ata6: SATA link down (SStatus 0 SControl 300)
[    5.336072] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.336091] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.337374] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.337514] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.337635] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.337638] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    5.337776] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.337897] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.337902] ata1.00: ATA-8: WDC WD1600BEVT-60ZCT0, 12.01A12, max UDMA/100
[    5.337905] ata1.00: 312581808 sectors, multi 0: LBA48 
[    5.339302] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.339441] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.339578] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.339581] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    5.339717] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.339839] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.339866] ata1.00: configured for UDMA/100
[    5.348060] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    5.349644] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 succeeded
[    5.349949] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.350295] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.350299] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    5.350649] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.351002] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.352688] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-6 12.0 PQ: 0 ANSI: 5
[    5.352818] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.352857] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    5.352902] sd 0:0:0:0: [sda] Write Protect is off
[    5.352904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.352928] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.353049]  sda:
[    5.363972] ata5.00: ATAPI: Optiarc DVD RW AD-7560S, SH03, max UDMA/100
[    5.377935] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 succeeded
[    5.378238] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.378580] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.378583] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    5.378927] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.379278] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[    5.392257] ata5.00: configured for UDMA/100
[    5.397723]  sda1 sda2 sda4 <
[    5.409580] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560S  SH03 PQ: 0 ANSI: 5
[    5.414810] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.414813] Uniform CD-ROM driver Revision: 3.20
[    5.414903] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.414949] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    5.415154]  sda5 sda6 >
[    5.415458] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.415488] Freeing unused kernel memory: 540k freed
[    5.415834] Write protecting the kernel text: 4568k
[    5.415891] Write protecting the kernel read-only data: 1836k
[    5.498152] usb 2-5: configuration #1 chosen from 1 choice
[    5.500031] Clocksource tsc unstable (delta = -344421800 ns)
[    5.534542] Linux agpgart interface v0.103
[    5.537542] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    5.537935] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    5.542060] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    5.610054] [drm] Initialized drm 1.1.0 20060810
[    5.656604] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.656610] i915 0000:00:02.0: setting latency timer to 64
[    5.659059]   alloc irq_desc for 31 on node -1
[    5.659063]   alloc kstat_irqs on node -1
[    5.659074] i915 0000:00:02.0: irq 31 for MSI/MSI-X
[    5.752533] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    5.764465] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.764487] r8169 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.764539] r8169 0000:04:00.0: setting latency timer to 64
[    5.764602]   alloc irq_desc for 32 on node -1
[    5.764605]   alloc kstat_irqs on node -1
[    5.764622] r8169 0000:04:00.0: irq 32 for MSI/MSI-X
[    5.765276] eth0: RTL8102e at 0xf867e000, 00:1e:ec:b1:8f:31, XID 24a00000 IRQ 32
[    5.771085] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.771101] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    5.790025] [drm] i2c_init DPDDC-B
[    5.799832] [drm] i2c_init DPDDC-D
[    5.923988] i2c-adapter i2c-2: unable to read EDID block.
[    5.923993] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    5.932966] [drm] fb0: inteldrmfb frame buffer device
[    5.934154] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    5.935007] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    5.957474] usb 3-1: configuration #1 chosen from 1 choice
[    5.959239] acpi device:04: registered as cooling_device3
[    5.959527] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
[    5.959567] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    5.959631] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    6.200535] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    6.251022] [drm] LVDS-8: set mode 1280x800 14
[    6.548985] usb 5-1: configuration #1 chosen from 1 choice
[    6.557212] usbcore: registered new interface driver hiddev
[    6.570126] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input7
[    6.570207] generic-usb 0003:192F:0116.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    6.570223] usbcore: registered new interface driver usbhid
[    6.570226] usbhid: v2.6:USB HID core driver
[    6.581436] Console: switching to colour frame buffer device 160x50
[    6.872413] PM: Starting manual resume from disk
[    6.872417] PM: Resume from partition 8:6
[    6.872419] PM: Checking hibernation image.
[    6.872626] PM: Resume from disk failed.
[    6.898965] EXT4-fs (sda1): barriers enabled
[    6.913593] kjournald2 starting: pid 426, dev sda1:8, commit interval 5 seconds
[    6.913617] EXT4-fs (sda1): delayed allocation enabled
[    6.913622] EXT4-fs: file extents enabled
[    6.919917] EXT4-fs: mballoc enabled
[    6.919934] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.578382] type=1505 audit(1257744958.139:2): operation="profile_load" pid=449 name=/usr/share/gdm/guest-session/Xsession
[    7.581302] type=1505 audit(1257744958.143:3): operation="profile_load" pid=450 name=/sbin/dhclient3
[    7.582038] type=1505 audit(1257744958.143:4): operation="profile_load" pid=450 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.582440] type=1505 audit(1257744958.143:5): operation="profile_load" pid=450 name=/usr/lib/connman/scripts/dhclient-script
[    7.623950] type=1505 audit(1257744958.183:6): operation="profile_load" pid=451 name=/usr/bin/evince
[    7.635465] type=1505 audit(1257744958.196:7): operation="profile_load" pid=451 name=/usr/bin/evince-previewer
[    7.642302] type=1505 audit(1257744958.204:8): operation="profile_load" pid=451 name=/usr/bin/evince-thumbnailer
[    7.662975] type=1505 audit(1257744958.224:9): operation="profile_load" pid=453 name=/usr/lib/cups/backend/cups-pdf
[    7.663832] type=1505 audit(1257744958.224:10): operation="profile_load" pid=453 name=/usr/sbin/cupsd
[    7.673860] type=1505 audit(1257744958.236:11): operation="profile_load" pid=454 name=/usr/sbin/tcpdump
[    8.831263] Adding 2449840k swap on /dev/sda6.  Priority:-1 extents:1 across:2449840k 
[    9.140140] udev: starting version 147
[    9.417917] EXT4-fs (sda1): internal journal on sda1:8
[    9.765585] EXT4-fs (sda2): barriers enabled
[    9.781205] kjournald2 starting: pid 675, dev sda2:8, commit interval 5 seconds
[    9.781479] EXT4-fs (sda2): internal journal on sda2:8
[    9.781483] EXT4-fs (sda2): delayed allocation enabled
[    9.781486] EXT4-fs: file extents enabled
[    9.782475] EXT4-fs: mballoc enabled
[    9.782490] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   12.875120] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.979730] lirc_dev: IR Remote Control driver registered, major 61 
[   12.981104] lirc_dev: lirc_register_driver: sample_rate: 0
[   12.981233] enecir: KB3926C detected, driver support is not complete!
[   12.981237] enecir: chip is 0x3926 - 0x00, 0xc0
[   12.981245] enecir: hardware features:
[   12.981247] enecir: learning and tx off, gpio40_learn off, fan_in off
[   12.981249] enecir: driver has been succesfully loaded
[   14.148187] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   14.148201] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   14.148206] hda_intel: msi for device 103c:3607 set to 1
[   14.148278]   alloc irq_desc for 33 on node -1
[   14.148280]   alloc kstat_irqs on node -1
[   14.148294] HDA Intel 0000:00:1b.0: irq 33 for MSI/MSI-X
[   14.148336] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.293535] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   14.501898] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.501974] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.822140] r8169: eth0: link down
[   15.822343] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.118586] Linux video capture interface: v2.00
[   16.607633] uvcvideo: Found UVC 1.00 device CNF7062 (04f2:b098)
[   16.616616] input: CNF7062 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input11
[   16.616675] usbcore: registered new interface driver uvcvideo
[   16.616679] USB Video Class driver (v0.1.0)
[   16.712918] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   16.713056] usbcore: registered new interface driver btusb
[   17.225755] cfg80211: Calling CRDA to update world regulatory domain
[   17.322554] sdhci: Secure Digital Host Controller Interface driver
[   17.322557] sdhci: Copyright(c) Pierre Ossman
[   17.324269] jmb38x_ms 0000:05:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.324280] jmb38x_ms 0000:05:00.3: setting latency timer to 64
[   17.344454] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input12
[   17.385408] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input13
[   17.443157] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.443160] Bluetooth: BNEP filters: protocol multicast
[   17.962841] Bridge firewalling registered
[   17.967749] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2382] (rev 0)
[   17.967774] sdhci-pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.967822] sdhci-pci 0000:05:00.0: setting latency timer to 64
[   17.967865] Registered led device: mmc0::
[   17.967906] mmc0: SDHCI controller on PCI [0000:05:00.0] using ADMA
[   17.967918] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 0)
[   17.967937] sdhci-pci 0000:05:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.967944] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[   17.967952] sdhci-pci 0000:05:00.2: PCI INT A disabled
[   17.970799] lp: driver loaded but no devices found
[   18.014032] ppdev: user-space parallel port driver
[   18.943604] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   18.984139] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[   18.984207] b43: probe of ssb0:0 failed with error -95
[   18.984247] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   19.293422] cfg80211: World regulatory domain updated:
[   19.293425] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.293428] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.293431] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.293434] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.293436] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.293439] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.394421] CPU0 attaching NULL sched-domain.
[   21.394427] CPU1 attaching NULL sched-domain.
[   21.509911] CPU0 attaching sched-domain:
[   21.509915]  domain 0: span 0-1 level MC
[   21.509918]   groups: 0 1
[   21.509924] CPU1 attaching sched-domain:
[   21.509926]  domain 0: span 0-1 level MC
[   21.509928]   groups: 1 0
[   21.517163] i2c-adapter i2c-2: unable to read EDID block.
[   21.517168] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.521844] i2c-adapter i2c-2: unable to read EDID block.
[   21.521847] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.681256] i2c-adapter i2c-2: unable to read EDID block.
[   21.681260] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   21.685988] i2c-adapter i2c-2: unable to read EDID block.
[   21.685991] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.194853] CPU0 attaching NULL sched-domain.
[   24.194859] CPU1 attaching NULL sched-domain.
[   24.212593] CPU0 attaching sched-domain:
[   24.212597]  domain 0: span 0-1 level MC
[   24.212600]   groups: 0 1
[   24.212605] CPU1 attaching sched-domain:
[   24.212608]  domain 0: span 0-1 level MC
[   24.212610]   groups: 1 0
[   24.523341] i2c-adapter i2c-2: unable to read EDID block.
[   24.523346] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.527884] i2c-adapter i2c-2: unable to read EDID block.
[   24.527887] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.662879] i2c-adapter i2c-2: unable to read EDID block.
[   24.662883] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.667412] i2c-adapter i2c-2: unable to read EDID block.
[   24.667415] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.811879] i2c-adapter i2c-2: unable to read EDID block.
[   24.811883] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   24.816603] i2c-adapter i2c-2: unable to read EDID block.
[   24.816606] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   36.767126] i2c-adapter i2c-2: unable to read EDID block.
[   36.767132] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   36.771723] i2c-adapter i2c-2: unable to read EDID block.
[   36.771729] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   36.907673] i2c-adapter i2c-2: unable to read EDID block.
[   36.907678] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   36.912277] i2c-adapter i2c-2: unable to read EDID block.
[   36.912284] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.042857] i2c-adapter i2c-2: unable to read EDID block.
[   37.042861] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   37.047403] i2c-adapter i2c-2: unable to read EDID block.
[   37.047406] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.842852] i2c-adapter i2c-2: unable to read EDID block.
[   38.842858] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.847590] i2c-adapter i2c-2: unable to read EDID block.
[   38.847594] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   56.944105] usb 3-1: USB disconnect, address 2
[   56.944383] btusb_intr_complete: hci0 urb ede16c00 failed to resubmit (19)
[   56.944391] btusb_bulk_complete: hci0 urb ede16c80 failed to resubmit (19)
[   56.945383] btusb_bulk_complete: hci0 urb edf26c00 failed to resubmit (19)
[   56.945505] btusb_send_frame: hci0 urb ef6f3080 submission failed
[   62.544045] usb 3-1: new full speed USB device using uhci_hcd and address 3
[   62.775203] usb 3-1: configuration #1 chosen from 1 choice
[  259.620614] r8169: eth0: link up
[  259.620997] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  270.564061] eth0: no IPv6 routers present

[COLOR="Blue"]Network configuration:[/COLOR]
*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:59700000-59703fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:b1:8f:31
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.119 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:3000(size=256) memory:53410000-53410fff(prefetchable) memory:53400000-5340ffff(prefetchable) memory:53420000-5343ffff(prefetchable)

[COLOR="Blue"]Network Scan:[/COLOR]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

[COLOR="Blue"]Ubuntu Version:[/COLOR]
Description:	Ubuntu 9.10

[COLOR="Blue"]Kernel/architecture:[/COLOR]
2.6.31-14-generic i686
[COLOR="Blue"]
Restarting the network:[/COLOR]
* Reconfiguring network interfaces...

Thanks in advanced...!

---

### Post by joao_da_costa on 2009-11-27
I have the same wireless card as you. I own a CQ40-313

Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Go to System -> Administration -> Hardware Drivers
then enable 'Broadcom STA wireless driver' and remove the other one. You must restart your machine before it works. After reboot, click the button to turn wireless on.

Take a look at the picture attached to see the right driver.

---

