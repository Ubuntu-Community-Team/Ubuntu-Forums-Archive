---
title: "Sony Vaio SZ series, Intel Corporation PRO/Wireless 4965 AG or AGN"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by hhnaing on 2010-07-22
I am new to Ubuntu and I have problem with wireless connection. I could not find any wireless connection at all. I am now using wired connection.

Sony Vaio SZ series, Intel Corporation PRO/Wireless 4965 AG or AGN

My software details are:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


lsmod
Module                  Size  Used by
tpm_infineon            7937  0 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_idt      54489  1 
joydev                  8799  0 
usbhid                 36946  0 
nvidia               7088432  37 
pcmcia                 38277  0 
snd_hda_intel          22075  2 
snd_hda_codec          87488  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71539  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4620  0 
snd_rawmidi            17847  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19099  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55879  0 
videodev               43162  1 uvcvideo
tifm_7xx1               3766  0 
psmouse                58937  0 
v4l1_compat            13359  2 uvcvideo,videodev
hid                    67806  1 usbhid
option                 12973  0 
usb_wwan                9953  1 option
tifm_core               6089  1 tifm_7xx1
snd                    49038  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           21582  0 
pcmcia_rsrc            10566  1 yenta_socket
serio_raw               4022  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
usbserial              33068  2 option,usb_wwan
ndiswrapper           224642  1 
tpm_tis                 7498  0 
tpm                    13741  2 tpm_infineon,tpm_tis
intel_agp              25261  0 
soundcore                880  1 snd
sony_laptop            29088  0 
vga16fb                12287  0 
tpm_bios                5310  1 tpm
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
vgastate                8973  1 vga16fb
video                  18712  0 
output                  1883  1 video
agpgart                32107  2 nvidia,intel_agp
lp                      7374  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40236  0 
firewire_ohci          21170  0 
firewire_core          46675  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
sky2                   45127  0 


Kernel Boot message

[    0.280500] Firmware did not grant requested _OSC control
[    0.280506] Firmware did not grant requested _OSC control
[    0.280511] Firmware did not grant requested _OSC control
[    0.280518] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.282417] ACPI: AC Adapter [ACAD] (on-line)
[    0.282502] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.282513] ACPI: Power Button [PWRB]
[    0.282551] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.284294] ACPI: Lid Switch [LID0]
[    0.284655] ACPI: acpi_idle registered with cpuidle
[    0.303717] Monitor-Mwait will be used to enter C-1 state
[    0.303749] Monitor-Mwait will be used to enter C-2 state
[    0.303775] Monitor-Mwait will be used to enter C-3 state
[    0.303781] Marking TSC unstable due to TSC halts in idle
[    0.306138] Switching to clocksource hpet
[    0.329058] thermal LNXTHERM:01: registered as thermal_zone0
[    0.329066] ACPI: Thermal Zone [ATF0] (59 C)
[    0.329777] thermal LNXTHERM:02: registered as thermal_zone1
[    0.329786] ACPI: Thermal Zone [DTS0] (61 C)
[    0.330515] thermal LNXTHERM:03: registered as thermal_zone2
[    0.330523] ACPI: Thermal Zone [DTS1] (62 C)
[    0.330620] ERST: Table is not found!
[    0.332112] vesafb: framebuffer at 0xc9000000, mapped to 0xf8100000, using 1216k, total 1216k
[    0.332115] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    0.332116] vesafb: scrolling: redraw
[    0.332119] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.351211] Console: switching to colour frame buffer device 80x30
[    0.370257] fb0: VESA VGA frame buffer device
[    0.370334] isapnp: Scanning for PnP cards...
[    0.392047] ACPI: Battery Slot [BAT1] (battery present)
[    0.431622] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.433024] brd: module loaded
[    0.433493] loop: module loaded
[    0.433675] ata_piix 0000:00:1f.1: version 2.13
[    0.433691]   alloc irq_desc for 22 on node -1
[    0.433693]   alloc kstat_irqs on node -1
[    0.433701] ata_piix 0000:00:1f.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.433743] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.442206] Freeing initrd memory: 10508k freed
[    0.447543] scsi0 : ata_piix
[    0.447700] scsi1 : ata_piix
[    0.448347] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.448350] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.448389] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.448396] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.601039] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.613138] ata1.00: ATAPI: MATSHITADVD-RAM UJ-852S, 1.01, max UDMA/33
[    0.613292] scsi2 : ata_piix
[    0.613347] scsi3 : ata_piix
[    0.614423] ata3: SATA max UDMA/133 cmd 0x18f8 ctl 0x18cc bmdma 0x18e0 irq 22
[    0.614431] ata4: SATA max UDMA/133 cmd 0x18f0 ctl 0x18c8 bmdma 0x18e8 irq 22
[    0.614740] Fixed MDIO Bus: probed
[    0.614777] PPP generic driver version 2.4.2
[    0.614843] tun: Universal TUN/TAP device driver, 1.6
[    0.614844] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.614925] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.614944] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.614965] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.614969] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.614998] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.615031] ehci_hcd 0000:00:1a.7: debug port 1
[    0.618929] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.618943] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfc304000
[    0.632433] ata1.00: configured for UDMA/33
[    0.636014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.636127] hub 1-0:1.0: USB hub found
[    0.636132] hub 1-0:1.0: 4 ports detected
[    0.636200]   alloc irq_desc for 23 on node -1
[    0.636202]   alloc kstat_irqs on node -1
[    0.636208] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.636219] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.636222] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.636250] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.636279] ehci_hcd 0000:00:1d.7: debug port 1
[    0.640174] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.640188] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc304400
[    0.656013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.656102] hub 2-0:1.0: USB hub found
[    0.656106] hub 2-0:1.0: 6 ports detected
[    0.656174] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.656188] uhci_hcd: USB Universal Host Controller Interface driver
[    0.656209] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.656215] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.656219] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.656255] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.656283] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001800
[    0.656391] hub 3-0:1.0: USB hub found
[    0.656395] hub 3-0:1.0: 2 ports detected
[    0.656453] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.656459] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.656463] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.656490] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.656516] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001820
[    0.656620] hub 4-0:1.0: USB hub found
[    0.656623] hub 4-0:1.0: 2 ports detected
[    0.656679] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.656686] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.656689] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.656717] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.656742] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.656848] hub 5-0:1.0: USB hub found
[    0.656852] hub 5-0:1.0: 2 ports detected
[    0.656906] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.656913] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.656916] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.656943] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.656969] uhci_hcd 0000:00:1d.1: irq 23, io base 0x00001860
[    0.657071] hub 6-0:1.0: USB hub found
[    0.657074] hub 6-0:1.0: 2 ports detected
[    0.657131] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.657138] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.657141] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.657173] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.657198] uhci_hcd 0000:00:1d.2: irq 23, io base 0x00001880
[    0.657297] hub 7-0:1.0: USB hub found
[    0.657301] hub 7-0:1.0: 2 ports detected
[    0.657423] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.659607] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.659613] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.659662] mice: PS/2 mouse device common for all mice
[    0.659751] rtc_cmos 00:08: RTC can wake from S4
[    0.659785] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.659817] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.659913] device-mapper: uevent: version 1.0.3
[    0.660016] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.660076] device-mapper: multipath: version 1.1.1 loaded
[    0.660079] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.660175] EISA: Probing bus 0 at eisa.0
[    0.660181] Cannot allocate resource for EISA slot 1
[    0.660183] Cannot allocate resource for EISA slot 2
[    0.660185] Cannot allocate resource for EISA slot 3
[    0.660186] Cannot allocate resource for EISA slot 4
[    0.660188] Cannot allocate resource for EISA slot 5
[    0.660190] Cannot allocate resource for EISA slot 6
[    0.660192] Cannot allocate resource for EISA slot 7
[    0.660197] EISA: Detected 0 cards.
[    0.660325] cpuidle: using governor ladder
[    0.660417] cpuidle: using governor menu
[    0.660698] TCP cubic registered
[    0.660815] NET: Registered protocol family 10
[    0.661141] lo: Disabled Privacy Extensions
[    0.661349] NET: Registered protocol family 17
[    0.661911] Using IPI No-Shortcut mode
[    0.661975] PM: Resume from disk failed.
[    0.661986] registered taskstats version 1
[    0.662386]   Magic number: 2:60:149
[    0.662401] bdi 1:1: hash matches
[    0.662481] rtc_cmos 00:08: setting system clock to 2010-07-22 22:07:55 UTC (1279836475)
[    0.662484] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.662485] EDD information not available.
[    0.685246] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.695555] isapnp: No Plug & Play device found
[    0.697458] scsi 0:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-852S  1.01 PQ: 0 ANSI: 5
[    0.701908] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.701910] Uniform CD-ROM driver Revision: 3.20
[    0.702002] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.702041] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.056056] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.416158] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.416182] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.424410] ata3.00: ATA-7: ST91608220AS, 3.ALE, max UDMA/133
[    1.424413] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.441450] ata3.00: configured for UDMA/133
[    1.441588] scsi 2:0:0:0: Direct-Access     ATA      ST91608220AS     3.AL PQ: 0 ANSI: 5
[    1.441688] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.441693] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.441768] sd 2:0:0:0: [sda] Write Protect is off
[    1.441770] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.441840] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.442148]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    1.452522] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.468040] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    1.904074] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.968060] ata4.01: failed to resume link (SControl 0)
[    1.979402] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.979428] ata4.01: SATA link down (SStatus 0 SControl 0)
[    1.979497] Freeing unused kernel memory: 684k freed
[    1.979890] Write protecting the kernel text: 4944k
[    1.979943] Write protecting the kernel read-only data: 2012k
[    1.994687] udev: starting version 151
[    2.043127] sky2: driver version 1.28
[    2.043167] sky2 0000:07:00.0: power state changed by ACPI to D0
[    2.043178] sky2 0000:07:00.0: power state changed by ACPI to D0
[    2.043189] sky2 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.043206] sky2 0000:07:00.0: setting latency timer to 64
[    2.043240] sky2 0000:07:00.0: Yukon-2 EC Ultra chip revision 3
[    2.043650]   alloc irq_desc for 45 on node -1
[    2.043652]   alloc kstat_irqs on node -1
[    2.043723] sky2 0000:07:00.0: irq 45 for MSI/MSI-X
[    2.069685] sky2 0000:07:00.0: eth0: addr 00:1a:80:56:e2:f0
[    2.079436]   alloc irq_desc for 21 on node -1
[    2.079439]   alloc kstat_irqs on node -1
[    2.079447] firewire_ohci 0000:09:04.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.110628] Initializing USB Mass Storage driver...
[    2.132114] firewire_ohci: Added fw-ohci device 0000:09:04.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.160134] scsi4 : usb-storage 2-4:1.0
[    2.168541] usbcore: registered new interface driver usb-storage
[    2.168544] USB Mass Storage support registered.
[    2.320066] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.632110] firewire_core: created device fw0: GUID 08004603029371df, S400
[    2.728055] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    2.902281] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    3.178544] scsi 4:0:0:0: Direct-Access     Sony     USB   HS-CARD    4.82 PQ: 0 ANSI: 0
[    3.179154] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    3.186530] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.778233] udev: starting version 151
[    7.846237] Adding 875516k swap on /dev/sda8.  Priority:-1 extents:1 across:875516k 
[    7.855256] lp: driver loaded but no devices found
[    7.909664] [Firmware Bug]: ACPI(NGFX) defines _DOD but not _DOS
[    7.909982] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input3
[    7.910037] ACPI: Video Device [NGFX] (multi-head: yes  rom: no  post: no)
[    7.991396] Disabling lock debugging due to kernel taint
[    8.011854] Linux agpgart interface v0.103
[    8.031572] tpm_tis 00:09: 1.2 TPM (device-id 0xB, rev-id 16)
[    8.032224] vga16fb: initializing
[    8.032227] vga16fb: mapped to 0xc00a0000
[    8.032233] checking generic (c9000000 130000) vs hw (a0000 10000)
[    8.032269] fb1: VGA16 VGA frame buffer device
[    8.064780] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[    8.125366] sony-laptop: Sony Programmable IO Control Driver v0.6.
[    8.125384] sony-laptop: detected Type3 model
[    8.127204] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:38/SNY6001:00/input/input4
[    8.127273] input: Sony Vaio Jogdial as /devices/virtual/input/input5
[    8.127348] sony-laptop: device allocated minor is 55
[    8.132902] yenta_cardbus 0000:09:04.0: CardBus bridge found [104d:9008]
[    8.132925] yenta_cardbus 0000:09:04.0: Using CSCINT to route CSC interrupts to PCI
[    8.132926] yenta_cardbus 0000:09:04.0: Routing CardBus interrupts to PCI
[    8.132932] yenta_cardbus 0000:09:04.0: TI: mfunc 0x01a21b22, devctl 0x64
[    8.167931] usbcore: registered new interface driver usbserial
[    8.167943] USB Serial support registered for generic
[    8.167997] usbcore: registered new interface driver usbserial_generic
[    8.167999] usbserial: USB Serial Driver core
[    8.174495] sony-laptop: Sony Notebook Control Driver v0.6.
[    8.196416] USB Serial support registered for GSM modem (1-port)
[    8.196655] option 4-1:1.0: GSM modem (1-port) converter detected
[    8.217847] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB0
[    8.217866] option 4-1:1.1: GSM modem (1-port) converter detected
[    8.218012] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB1
[    8.218025] option 4-1:1.2: GSM modem (1-port) converter detected
[    8.218172] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB2
[    8.218185] option 4-1:1.3: GSM modem (1-port) converter detected
[    8.218330] usb 4-1: GSM modem (1-port) converter now attached to ttyUSB3
[    8.218534] usbcore: registered new interface driver option
[    8.218537] option: v0.7.2:USB Driver for GSM modems
[    8.224906] Linux video capture interface: v2.00
[    8.229770] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[    8.321247] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:183a)
[    8.322565] input: UVC Camera (05ca:183a) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input6
[    8.323100] usbcore: registered new interface driver uvcvideo
[    8.323102] USB Video Class driver (v0.1.0)
[    8.412594] yenta_cardbus 0000:09:04.0: ISA IRQ mask 0x0cb0, PCI irq 20
[    8.412598] yenta_cardbus 0000:09:04.0: Socket status: 30000006
[    8.412602] pci_bus 0000:09: Raising subordinate bus# of parent bus (#09) from #0a to #0d
[    8.412611] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[    8.412614] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x70ff 0x7400-0x74ff
[    8.418479] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge window: [mem 0xfc000000-0xfc0fffff]
[    8.418482] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfc000000-0xfc0fffff: excluding 0xfc000000-0xfc00ffff
[    8.418496] yenta_cardbus 0000:09:04.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[    8.418498] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[    8.439613] tifm_7xx1 0000:09:04.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    8.525641] type=1400 audit(1279800483.362:2):  operation="profile_load" pid=836 name="/sbin/dhclient3" pid=836 comm="apparmor_parser"
[    8.526374] type=1400 audit(1279800483.362:3):  operation="profile_load" pid=836 name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=836 comm="apparmor_parser"
[    8.526684] type=1400 audit(1279800483.362:4):  operation="profile_load" pid=836 name="/usr/lib/connman/scripts/dhclient-script" pid=836 comm="apparmor_parser"
[    8.549318] usbcore: registered new interface driver hiddev
[    8.563195] input: Microsoft  Compact Optical Mouse 500 as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input7
[    8.563288] generic-usb 0003:045E:0737.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Compact Optical Mouse 500] on usb-0000:00:1d.0-1/input0
[    8.563304] usbcore: registered new interface driver usbhid
[    8.563306] usbhid: USB HID core driver
[    8.610328] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[    8.625873] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[    8.709435] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.709448] nvidia 0000:01:00.0: setting latency timer to 64
[    8.709455] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.709592] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.27  Tue Jul 13 20:39:52 PDT 2010
[    8.826135] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[    8.827795] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[    8.828518] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    8.829087] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    8.829714] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[    8.829768] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[    8.829821] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[    8.829875] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    8.866312] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[    8.868034] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[    8.868044] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.868107]   alloc irq_desc for 46 on node -1
[    8.868109]   alloc kstat_irqs on node -1
[    8.868123] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[    8.868159] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.937765] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    8.937962] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.298862] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'_aulldvrm'
[   11.299532] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoWMIOpenBlock'
[   11.300233] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoWMIQueryAllData'
[   11.300969] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'KeRegisterBugCheckReasonCallback'
[   11.301819] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'KeDeregisterBugCheckReasonCallback'
[   11.302890] ndiswrapper: driver netw5x32 (Intel,05/31/2010,13.2.1.5) loaded
[   11.303360] ndiswrapper 0000:06:00.0: power state changed by ACPI to D0
[   11.303371] ndiswrapper 0000:06:00.0: power state changed by ACPI to D0
[   11.303383] ndiswrapper 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.303393] ndiswrapper 0000:06:00.0: power state changed by ACPI to D0
[   11.303402] ndiswrapper 0000:06:00.0: power state changed by ACPI to D0
[   11.303411] ndiswrapper (NdisWriteErrorLogEntry:190): log: 40001B7C, count: 2, return_address: f96fe435
[   11.304265] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x56524457
[   11.304855] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x9e
[   11.305405] ndiswrapper 0000:06:00.0: setting latency timer to 64
[   11.321167] ndiswrapper: using IRQ 17
[   11.321951] BUG: unable to handle kernel paging request at 00628c0e
[   11.322553] IP: [<00628c0e>] 0x628c0e
[   11.322901] *pde = 7f8a0067 
[   11.323202] Oops: 0000 [#1] SMP 
[   11.323542] last sysfs file: /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0:0/block/sda/sda2/alignment_offset
[   11.324021] Modules linked in: snd_hda_codec_idt joydev usbhid nvidia(P) pcmcia snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device uvcvideo videodev tifm_7xx1 psmouse v4l1_compat hid option usb_wwan tifm_core snd yenta_socket pcmcia_rsrc serio_raw pcmcia_core usbserial ndiswrapper(+) tpm_tis(+) tpm intel_agp soundcore sony_laptop vga16fb tpm_bios snd_page_alloc vgastate video output agpgart lp parport usb_storage firewire_ohci firewire_core crc_itu_t sky2
[   11.324021] 
[   11.324021] Pid: 589, comm: modprobe Tainted: P            2.6.35-9-generic #14-Ubuntu VAIO                            /VGN-SZ670N
[   11.324021] EIP: 0060:[<00628c0e>] EFLAGS: 00010282 CPU: 0
[   11.324021] EIP is at 0x628c0e
[   11.324021] EAX: f5abb84c EBX: f51ea800 ECX: f5abb854 EDX: 000011d1
[   11.324021] ESI: f51ea800 EDI: f69f6950 EBP: f5abb868 ESP: f5abb82c
[   11.324021]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   11.324021] Process modprobe (pid: 589, ti=f5aba000 task=f506f230 task.ti=f5aba000)
[   11.324021] Stack:
[   11.324021]  f94b83ec f5abb854 00000001 f5abb84c f69f6950 f51ea800 f51ea800 f59b9200
[   11.324021] <0> 00000000 f5abb880 8f680850 11d1a584 a00038bf 102906c9 f326dc6d f5abb984
[   11.324021] <0> f94bc726 f51ea800 00000000 f69f6950 f51ea800 42298086 00100006 02800061
[   11.324021] Call Trace:
[   11.324021]  [<f835cf40>] ? NdisWriteErrorLogEntry+0x0/0x90 [ndiswrapper]
[   11.324021]  [<f835cf40>] ? NdisWriteErrorLogEntry+0x0/0x90 [ndiswrapper]
[   11.324021]  [<f835cf40>] ? NdisWriteErrorLogEntry+0x0/0x90 [ndiswrapper]
[   11.324021]  [<f836b8a6>] ? mp_init+0x66/0x220 [ndiswrapper]
[   11.324021]  [<f836cfe5>] ? ndis_start_device+0x15/0x920 [ndiswrapper]
[   11.324021]  [<f8366189>] ? pdoDispatchPnp+0x49/0xf0 [ndiswrapper]
[   11.324021]  [<f83637e6>] ? IofCallDriver+0x56/0xc0 [ndiswrapper]
[   11.324021]  [<f8363d7f>] ? IoSyncForwardIrp+0x7f/0xd0 [ndiswrapper]
[   11.324021]  [<f8364605>] ? IoAllocateIrp+0x65/0x80 [ndiswrapper]
[   11.324021]  [<f836d983>] ? NdisDispatchPnp+0x93/0x140 [ndiswrapper]
[   11.324021]  [<f83637e6>] ? IofCallDriver+0x56/0xc0 [ndiswrapper]
[   11.324021]  [<f83653a8>] ? IoSendIrpTopDev+0xe8/0x140 [ndiswrapper]
[   11.324021]  [<f836578f>] ? pnp_start_device+0x3f/0x90 [ndiswrapper]
[   11.324021]  [<f8365a40>] ? wrap_pnp_start_device+0xe0/0x170 [ndiswrapper]
[   11.324021]  [<f8365c15>] ? wrap_pnp_start_pci_device+0x55/0x70 [ndiswrapper]
[   11.324021]  [<c0271117>] ? sysfs_new_dirent+0x67/0x100
[   11.324021]  [<c027154a>] ? sysfs_addrm_finish+0x1a/0xb0
[   11.324021]  [<c05cb0a9>] ? mutex_lock+0x19/0x40
[   11.324021]  [<c03703fe>] ? pci_match_device+0xbe/0xd0
[   11.324021]  [<c0370293>] ? local_pci_probe+0x13/0x20
[   11.324021]  [<c0371248>] ? pci_device_probe+0x68/0x90
[   11.324021]  [<c0404a6d>] ? really_probe+0x4d/0x150
[   11.324021]  [<c040bcb7>] ? pm_runtime_barrier+0x57/0xb0
[   11.324021]  [<c0404bac>] ? driver_probe_device+0x3c/0x60
[   11.324021]  [<c0404c51>] ? __driver_attach+0x81/0x90
[   11.324021]  [<c0404073>] ? bus_for_each_dev+0x53/0x80
[   11.324021]  [<c040493e>] ? driver_attach+0x1e/0x20
[   11.324021]  [<c0404bd0>] ? __driver_attach+0x0/0x90
[   11.324021]  [<c0404305>] ? bus_add_driver+0xd5/0x280
[   11.324021]  [<c0371180>] ? pci_device_remove+0x0/0x40
[   11.324021]  [<c0404f4a>] ? driver_register+0x6a/0x130
[   11.324021]  [<c03d16ec>] ? misc_register+0xcc/0x140
[   11.324021]  [<c0371485>] ? __pci_register_driver+0x45/0xb0
[   11.324021]  [<f83582ed>] ? loader_init+0x9d/0x150 [ndiswrapper]
[   11.324021]  [<f8366317>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
[   11.324021]  [<f838407f>] ? wrapper_init+0x7f/0xb7 [ndiswrapper]
[   11.324021]  [<c0101131>] ? do_one_initcall+0x31/0x190
[   11.324021]  [<f8384000>] ? wrapper_init+0x0/0xb7 [ndiswrapper]
[   11.324021]  [<c0180bab>] ? sys_init_module+0x9b/0x1e0
[   11.324021]  [<c0216bf5>] ? sys_close+0x75/0xc0
[   11.324021]  [<c05cc7fc>] ? syscall_call+0x7/0xb
[   11.324021] Code:  Bad EIP value.
[   11.324021] EIP: [<00628c0e>] 0x628c0e SS:ESP 0068:f5abb82c
[   11.324021] CR2: 0000000000628c0e
[   12.022825] ---[ end trace 4727e05b909df021 ]---
[   12.096898] type=1400 audit(1279800486.930:5):  operation="profile_load" pid=1019 name="/usr/share/gdm/guest-session/Xsession" pid=1019 comm="apparmor_parser"
[   12.126070] type=1400 audit(1279800486.958:6):  operation="profile_replace" pid=1027 name="/sbin/dhclient3" pid=1027 comm="apparmor_parser"
[   12.147028] type=1400 audit(1279800486.982:7):  operation="profile_replace" pid=1027 name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1027 comm="apparmor_parser"
[   12.180316] type=1400 audit(1279800487.014:8):  operation="profile_replace" pid=1027 name="/usr/lib/connman/scripts/dhclient-script" pid=1027 comm="apparmor_parser"
[   12.504407] type=1400 audit(1279800487.338:9):  operation="profile_load" pid=1028 name="/usr/bin/evince" pid=1028 comm="apparmor_parser"
[   12.537478] type=1400 audit(1279800487.370:10):  operation="profile_load" pid=1028 name="/usr/bin/evince-previewer" pid=1028 comm="apparmor_parser"
[   12.569535] type=1400 audit(1279800487.402:11):  operation="profile_load" pid=1028 name="/usr/bin/evince-thumbnailer" pid=1028 comm="apparmor_parser"
[   13.628727] audit_printk_skb: 6 callbacks suppressed
[   13.643676] type=1400 audit(1279800488.462:14):  operation="profile_load" pid=1038 name="/usr/sbin/mysqld-akonadi" pid=1038 comm="apparmor_parser"
[   13.721829] sky2 0000:07:00.0: eth0: enabling interface
[   13.737595] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.096736] type=1400 audit(1279800488.930:15):  operation="profile_load" pid=1041 name="/usr/sbin/tcpdump" pid=1041 comm="apparmor_parser"
[   15.678615] sky2 0000:07:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   15.678764] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.649274] ppdev: user-space parallel port driver
[   21.317914] type=1400 audit(1279800496.154:16):  operation="getattr" pid=1246 parent=1244 profile="/usr/sbin/cupsd" name="/lib/" pid=1246 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   21.317990] type=1400 audit(1279800496.154:17):  operation="getattr" pid=1246 parent=1244 profile="/usr/sbin/cupsd" name="/usr/lib/" pid=1246 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   22.665427] ata3.00: configured for UDMA/133
[   22.665431] ata3: EH complete
[   23.384533] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   25.944025] eth0: no IPv6 routers present
[   32.684598] ata3.00: configured for UDMA/133
[   32.684606] ata3: EH complete
[   34.438171] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   48.306854] type=1400 audit(1279800523.138:18):  operation="getattr" pid=1689 parent=1033 profile="/sbin/dhclient3" name="/lib/" pid=1689 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   48.306952] type=1400 audit(1279800523.138:19):  operation="getattr" pid=1689 parent=1033 profile="/sbin/dhclient3" name="/usr/lib/" pid=1689 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  130.284132] tpm_tis 00:09: tpm_transmit: tpm_send: error 4294967234
[  252.540137] tpm_tis 00:09: tpm_transmit: tpm_send: error 4294967234
[  373.293059] tpm_tis 00:09: tpm_transmit: tpm_send: error 4294967234
[ 1154.853008] type=1400 audit(1279801629.685:20):  operation="open" pid=4737 parent=4727 profile="/usr/sbin/cupsd" name="/dev/ttyUSB0" pid=4737 comm="serial" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
[ 1154.853031] type=1400 audit(1279801629.689:21):  operation="open" pid=4737 parent=4727 profile="/usr/sbin/cupsd" name="/dev/ttyUSB1" pid=4737 comm="serial" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
[ 1154.853047] type=1400 audit(1279801629.689:22):  operation="open" pid=4737 parent=4727 profile="/usr/sbin/cupsd" name="/dev/ttyUSB2" pid=4737 comm="serial" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
[ 1154.853063] type=1400 audit(1279801629.689:23):  operation="open" pid=4737 parent=4727 profile="/usr/sbin/cupsd" name="/dev/ttyUSB3" pid=4737 comm="serial" requested_mask="w" denied_mask="w" fsuid=0 ouid=0
[ 1950.691267] usb 3-1: USB disconnect, address 2
[ 1951.676088] usb 3-1: new full speed USB device using uhci_hcd and address 3


Network configuration

 *-network               
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ndiswrapper latency=0
       resources: irq:17 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:1a:80:56:e2:f0
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=10.1.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:45 memory:fa000000-fa003fff ioport:5000(size=256) memory:f4000000-f401ffff


Scan for network
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



Ubuntu version
Description:    Ubuntu maverick (development branch)


Kernel/Architecture
2.6.35-9-generic i686


Restarting the network
* Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]


Sorry for so much information. I just do it as advised on your forum.

Thanks for your help.

---

### Post by uriela on 2010-09-24
Have a Sony VAIO with the same wirelesss adapter you have and Maverick also has not set up the wireless, whereas, it has under Lucid on the same machine.

---

