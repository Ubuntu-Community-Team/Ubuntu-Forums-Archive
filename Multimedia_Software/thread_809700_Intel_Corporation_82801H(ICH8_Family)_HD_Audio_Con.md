---
title: "Intel Corporation 82801H(ICH8 Family) HD Audio Controler"
date: 2008-05-27
forum: Multimedia Software
---

### Post by viteriker on 2008-05-27
Hola a todos, soy nuevo en esto del linux, y por ahora me he topado con el problema de que la tarjeta de sonido parece que está bien configurada pero no consigo que suene ningun sonido.

cuando la configuro con alsaconf, me la detecta bien, pero al hacer la prueba de sonido, no se oye nada.

He estado unos días intentando buscar soluciones por los foros, dandole vueltas a la instalación de ALSA, y no consigo hacerlo sonar.

Es obligatorio usar el ALSA, no hay otra manera???

Lo he hecho 10 veces aproximadamente de distintas maneras y no consigo nada.

Un saludo a todos, y gracias de antemano.

---

### Post by LaRoza on 2008-05-27
Hola. ¿Podría usted hablar en inglés?

Si no, puedo mover esto a otro foro.

(Perdone mi español)

---

### Post by Sef on 2008-05-27
1) Please post only in English.

2) If you do want to post in your native tongue, then post in the correct [Ubuntu LoCo Team Forum]("http://ubuntuforums.org/forumdisplay.php?f=183").

---

### Post by viteriker on 2008-05-28
Sorry I couldn't see forums in spanish and i saw that page was about multimedia, sound cards...

My problem is that i've that sound card in my laptop.

 Intel Corporation 82801H(ICH8 Family) HD Audio Controler

And Ubuntu 8.04 installed.

I tried with ALSA many times, but there is not sound in my speakers.

I think that my alsaconf works correctly, because my sound card is detected fine, but when the configuration puts the example, no sound apears. The speakers doesn't work with any sound reproduction program, and the start "drums" doesn't sound when the session starts.

I think the alsamixer is good (with the sound levels al 100%), and i think the soundcar works (the bios "bell" sound).

Thank you if you like to help me, and sorry because i wrote in spanish.

(Your spanish is good, sorry about my english)

---

### Post by zatara on 2008-12-05
viterider i have the same problem if you find the solution post me

---

### Post by &gt;:3 on 2008-12-28
Hi, I've got the same problem. No sound from headphones or speakers.

Running Ibex on a [COLOR="Blue"]_["Hi-Grade Notino D7000SRA"]("http://www.higrade.com/nqcontent.cfm?a_id=3674")_[/COLOR] Laptop

Speakers on Maximum, Nothing muted, I can't get any sound with or without headphones. 
Speakers work fine in windoze

Any help would be much appreciated. 
Also: Would I be wiser posting this in bugs.launchpad? 

So: Here's what I tried: 


-------------------------------------------------------------------

**System > Prefs > Sound > Devices > Test**

^ No option anywhere gives out any noise

Following errors:

"HDA Intel HDA Generic (ALSA)" gives:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.*

"HDA Intel HDA Generic (OSS)" gives: 
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application. *

"OSS &#8211; Open Sound System" gives:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.*

**Checked alsamixer**, Both channels (capture and Master) are on full volume, and are not muted. 

Went though: _[COLOR="Blue"][https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems")[/COLOR]_
The following are outputs from various commands

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****

card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]

  Subdevices: 0/1

  Subdevice #0: subdevice #0

card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]

  Subdevices: 1/1

  Subdevice #0: subdevice #0
```


**find /lib/modules/`uname -r` | grep snd**

Output: Really big list, I've not included it, I can if requested. 

**lspci -v **

```
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]

	Subsystem: Rioworks Device 2073

	Flags: bus master, fast devsel, latency 0, IRQ 17

	Memory at fb010000 (32-bit, non-prefetchable) [size=16K]

	Capabilities: [50] Power Management version 3

	Capabilities: [58] Express Legacy Endpoint, MSI 00

	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

	Capabilities: [100] Vendor Specific Information <?>

	Kernel driver in use: HDA Intel

	Kernel modules: snd-hda-intel


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

	Subsystem: Rioworks Device 2073

	Flags: bus master, fast devsel, latency 0, IRQ 22

	Memory at fb300000 (64-bit, non-prefetchable) [size=16K]

	Capabilities: [50] Power Management version 2

	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00

	Capabilities: [100] Virtual Channel <?>

	Capabilities: [130] Root Complex Link <?>

	Kernel driver in use: HDA Intel

	Kernel modules: snd-hda-intel
```

Unable to find any mention under
_[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")_

**uname -a**
Linux Device-Name 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux


**amixer**

```
Simple mixer control 'Master',0

  Capabilities: pvolume pswitch pswitch-joined

  Playback channels: Front Left - Front Right

  Limits: Playback 0 - 65536

  Mono:

  Front Left: Playback 65536 [100%] [on]

  Front Right: Playback 65536 [100%] [on]

Simple mixer control 'Capture',0

  Capabilities: cvolume cswitch cswitch-joined

  Capture channels: Front Left - Front Right

  Limits: Capture 0 - 65536

  Front Left: Capture 65536 [100%] [on]

  Front Right: Capture 65536 [100%] [on]
```

**dmesg**
```
[    1.978850] usb usb1: configuration #1 chosen from 1 choice

[    1.978871] hub 1-0:1.0: USB hub found

[    1.978876] hub 1-0:1.0: 2 ports detected

[    2.037078] No dock devices found.

[    2.048788] SCSI subsystem initialized

[    2.069080] libata version 3.00 loaded.

[    2.185329] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21

[    2.185339] uhci_hcd 0000:00:1a.1: setting latency timer to 64

[    2.185343] uhci_hcd 0000:00:1a.1: UHCI Host Controller

[    2.185364] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2

[    2.185399] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820

[    2.185480] usb usb2: configuration #1 chosen from 1 choice

[    2.185502] hub 2-0:1.0: USB hub found

[    2.185508] hub 2-0:1.0: 2 ports detected

[    2.289388] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    2.289405] ehci_hcd 0000:00:1a.7: setting latency timer to 64

[    2.289409] ehci_hcd 0000:00:1a.7: EHCI Host Controller

[    2.289435] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3

[    2.293357] ehci_hcd 0000:00:1a.7: debug port 1

[    2.293363] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported

[    2.293376] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfb304800

[    2.309030] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[    2.309148] usb usb3: configuration #1 chosen from 1 choice

[    2.309171] hub 3-0:1.0: USB hub found

[    2.309178] hub 3-0:1.0: 4 ports detected

[    2.500102] Clocksource tsc unstable (delta = -177422742 ns)

[    2.517433] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23

[    2.517442] uhci_hcd 0000:00:1d.0: setting latency timer to 64

[    2.517446] uhci_hcd 0000:00:1d.0: UHCI Host Controller

[    2.517465] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4

[    2.517500] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840

[    2.517578] usb usb4: configuration #1 chosen from 1 choice

[    2.517599] hub 4-0:1.0: USB hub found

[    2.517605] hub 4-0:1.0: 2 ports detected

[    2.724508] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[    2.724514] uhci_hcd 0000:00:1d.1: setting latency timer to 64

[    2.724517] uhci_hcd 0000:00:1d.1: UHCI Host Controller

[    2.724540] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5

[    2.724570] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860

[    2.724636] usb usb5: configuration #1 chosen from 1 choice

[    2.724655] hub 5-0:1.0: USB hub found

[    2.724661] hub 5-0:1.0: 2 ports detected

[    2.829540] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18

[    2.829546] uhci_hcd 0000:00:1d.2: setting latency timer to 64

[    2.829550] uhci_hcd 0000:00:1d.2: UHCI Host Controller

[    2.829570] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6

[    2.829596] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880

[    2.829662] usb usb6: configuration #1 chosen from 1 choice

[    2.829681] hub 6-0:1.0: USB hub found

[    2.829686] hub 6-0:1.0: 2 ports detected

[    2.992059] usb 3-3: new high speed USB device using ehci_hcd and address 3

[    3.036943] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23

[    3.036956] ehci_hcd 0000:00:1d.7: setting latency timer to 64

[    3.036959] ehci_hcd 0000:00:1d.7: EHCI Host Controller

[    3.036981] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7

[    3.040894] ehci_hcd 0000:00:1d.7: debug port 1

[    3.040900] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported

[    3.040904] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfb304c00

[    3.116067] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

[    3.116347] usb usb7: configuration #1 chosen from 1 choice

[    3.116529] hub 7-0:1.0: USB hub found

[    3.116536] hub 7-0:1.0: 6 ports detected

[    3.131717] usb 3-3: configuration #1 chosen from 1 choice

[    3.244117] usb 3-4: new high speed USB device using ehci_hcd and address 4

[    3.326061] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[    3.326090] pata_acpi 0000:00:1f.1: setting latency timer to 64

[    3.326102] pata_acpi 0000:00:1f.1: PCI INT A disabled


[    3.326147] ahci 0000:00:1f.2: version 3.0

[    3.326155] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19

[    3.326237] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode

[    3.326240] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 

[    3.326245] ahci 0000:00:1f.2: setting latency timer to 64

[    3.326729] scsi0 : ahci

[    3.326824] scsi1 : ahci

[    3.326888] scsi2 : ahci

[    3.326975] ata1: SATA max UDMA/133 abar m2048@0xfb304000 port 0xfb304100 irq 219

[    3.326978] ata2: SATA max UDMA/133 abar m2048@0xfb304000 port 0xfb304180 irq 219

[    3.326981] ata3: SATA max UDMA/133 abar m2048@0xfb304000 port 0xfb304200 irq 219

[    3.389103] usb 3-4: configuration #1 chosen from 1 choice

[    3.644127] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

[    3.648085] ata1.00: _GTF unexpected object type 0x1

[    3.649893] ata1.00: ATA-8: SAMSUNG HM250JI, HS100-08, max UDMA7

[    3.649897] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)

[    3.655570] ata1.00: _GTF unexpected object type 0x1

[    3.657381] ata1.00: configured for UDMA/133

[    3.888119] usb 1-2: new full speed USB device using uhci_hcd and address 2

[    3.992122] ata2: SATA link down (SStatus 0 SControl 300)

[    4.054889] usb 1-2: configuration #1 chosen from 1 choice

[    4.328127] ata3: SATA link down (SStatus 0 SControl 300)

[    4.344288] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM250JI  HS10 PQ: 0 ANSI: 5

[    4.344402] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

[    4.344423] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[    4.344443] r8169 0000:02:00.0: setting latency timer to 64

[    4.344776] eth0: RTL8101e at 0xf884e000, 00:03:25:5b:3b:6a, XID 34200000 IRQ 218

[    4.351854] ata_piix 0000:00:1f.1: version 2.12

[    4.351864] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19

[    4.351898] ata_piix 0000:00:1f.1: setting latency timer to 64

[    4.353204] usb 7-4: new high speed USB device using ehci_hcd and address 3

[    4.353222] scsi3 : ata_piix

[    4.353289] scsi4 : ata_piix

[    4.353874] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14

[    4.353876] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15

[    4.376627] scsi 0:0:0:0: Attached scsi generic sg0 type 0

[    4.388025] Driver 'sd' needs updating - please use bus_type methods

[    4.388121] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)

[    4.388143] sd 0:0:0:0: [sda] Write Protect is off

[    4.388145] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.388187] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.388263] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)

[    4.388281] sd 0:0:0:0: [sda] Write Protect is off

[    4.388283] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00

[    4.388320] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

[    4.388322]  sda:<6>usb 7-4: configuration #1 chosen from 1 choice

[    4.532502] ata4.00: ATAPI: TSSTcorp CDDVDW SN-S082H, SB01, max UDMA/33

[    4.564449] ata4.00: configured for UDMA/33

[    4.616366] usbcore: registered new interface driver libusual

[    4.621646] Initializing USB Mass Storage driver...

[    4.732436] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082H  SB01 PQ: 0 ANSI: 5

[    4.732606] scsi 3:0:0:0: Attached scsi generic sg1 type 5

[    4.744373] Driver 'sr' needs updating - please use bus_type methods

[    4.856067] usb 4-1: new low speed USB device using uhci_hcd and address 2

[    5.044723] usb 4-1: configuration #1 chosen from 1 choice

[    5.288062] usb 6-2: new full speed USB device using uhci_hcd and address 2

[    5.330280]  sda1 sda2 sda3 < sda5 sda6 >

[    5.368991] sd 0:0:0:0: [sda] Attached SCSI disk

[    5.373866] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

[    5.373872] Uniform CD-ROM driver Revision: 3.20

[    5.373978] sr 3:0:0:0: Attached scsi CD-ROM sr0

[    5.462352] usb 6-2: configuration #1 chosen from 1 choice

[    5.465869] scsi5 : SCSI emulation for USB Mass Storage devices

[    5.469057] scsi6 : SCSI emulation for USB Mass Storage devices

[    5.469058] usb-storage: device found at 4

[    5.469060] usb-storage: waiting for device to settle before scanning

[    5.469494] usbcore: registered new interface driver usb-storage

[    5.469497] USB Mass Storage support registered.

[    5.469604] usbcore: registered new interface driver hiddev

[    5.472633] usb-storage: device found at 3

[    5.472635] usb-storage: waiting for device to settle before scanning

[    5.502848] input: HID 04d9:1133 as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input2

[    5.504199] input,hidraw0: USB HID v1.10 Mouse [HID 04d9:1133] on usb-0000:00:1d.0-1

[    5.504217] usbcore: registered new interface driver usbhid

[    5.504225] usbhid: v2.6:USB HID core driver

[    5.779175] PM: Starting manual resume from disk

[    5.779178] PM: Resume from partition 8:6

[    5.779179] PM: Checking hibernation image.

[    5.779405] PM: Resume from disk failed.

[    5.815817] kjournald starting.  Commit interval 5 seconds

[    5.815856] EXT3-fs: mounted filesystem with ordered data mode.

[   10.468360] usb-storage: device scan complete

[   10.469746] usb-storage: device scan complete

[   10.471115] scsi 5:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4

[   10.474670] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS

[   10.475929] sd 6:0:0:0: [sdb] Attached SCSI removable disk

[   10.476024] sd 6:0:0:0: Attached scsi generic sg2 type 0

[   10.478217] sd 5:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)

[   10.479750] sd 5:0:0:0: [sdc] Write Protect is off

[   10.479753] sd 5:0:0:0: [sdc] Mode Sense: 1c 00 00 00

[   10.479755] sd 5:0:0:0: [sdc] Assuming drive cache: write through

[   10.481844] sd 5:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)

[   10.483343] sd 5:0:0:0: [sdc] Write Protect is off

[   10.483345] sd 5:0:0:0: [sdc] Mode Sense: 1c 00 00 00

[   10.483347] sd 5:0:0:0: [sdc] Assuming drive cache: write through

[   10.483350]  sdc: sdc1

[   10.496070] sd 5:0:0:0: [sdc] Attached SCSI disk

[   10.496113] sd 5:0:0:0: Attached scsi generic sg3 type 0

[   11.818997] udevd version 124 started

[   12.163764] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[   12.190425] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

[   12.228577] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3

[   12.247909] Linux agpgart interface v0.103

[   12.253029] ACPI: Power Button (FF) [PWRF]

[   12.253217] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4

[   12.253493] ACPI: Lid Switch [LID0]

[   12.253558] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5

[   12.285588] ACPI: Power Button (CM) [PWRB]

[   12.285669] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6

[   12.317028] ACPI: Sleep Button (CM) [SLPB]

[   12.321426] ACPI: Battery Slot [BAT0] (battery absent)

[   12.321863] ACPI: AC Adapter [AC] (on-line)

[   12.488186] acpi device:06: registered as cooling_device2

[   12.488363] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input7

[   12.504678] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)

[   12.505254] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input8

[   12.537059] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)

[   12.706721] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.

[   12.759127] [fglrx] Maximum main memory to use for locked dma buffers: 2892 MBytes.

[   12.759639] [fglrx]   vendor: 1002 device: 94c8 count: 1

[   12.766275] [fglrx] ioport: bar 1, base 0x2000, size: 0x100

[   12.766291] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[   12.766296] pci 0000:01:00.0: setting latency timer to 64

[   12.767902] [fglrx] PAT is enabled successfully!

[   12.767929] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors

[   12.851608] Bluetooth: Core ver 2.13

[   12.854836] NET: Registered protocol family 31

[   12.854839] Bluetooth: HCI device and connection manager initialized

[   12.854841] Bluetooth: HCI socket layer initialized

[   12.982008] Bluetooth: Generic Bluetooth USB driver ver 0.3

[   12.982102] usbcore: registered new interface driver btusb

[   13.026939] Linux video capture interface: v2.00

[   13.061307] input: PC Speaker as /devices/platform/pcspkr/input/input9

[   13.068726] iTCO_vendor_support: vendor-support=0

[   13.092910] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)

[   13.093411] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)

[   13.093524] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

[   13.125624] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22

[   13.125651] HDA Intel 0000:00:1b.0: setting latency timer to 64

[   13.183455] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)

[   13.190477] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.7/usb3/3-3/3-3:1.0/input/input10

[   13.241490] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17

[   13.241520] HDA Intel 0000:01:00.1: setting latency timer to 64

[   13.273677] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks

[   13.273680] iwl3945: Copyright(c) 2003-2008 Intel Corporation

[   13.289512] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[   13.289527] iwl3945 0000:04:00.0: setting latency timer to 64

[   13.289550] iwl3945: Detected Intel Wireless WiFi Link 3945ABG

[   13.411376] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

[   13.411761] phy0: Selected rate control algorithm 'iwl-3945-rs'

[   13.484747] usbcore: registered new interface driver uvcvideo

[   13.484751] USB Video Class driver (v0.1.0)

[   13.637487] iwl3945 0000:04:00.0: PCI INT A disabled

[   13.944430] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input11

[   15.870848] lp: driver loaded but no devices found

[   15.991153] Adding 3156732k swap on /dev/sda6.  Priority:-1 extents:1 across:3156732k

[   16.522881] EXT3 FS on sda5, internal journal

[   17.382744] type=1505 audit(1230490712.678:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4403

[   17.504170] type=1505 audit(1230490712.802:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4408

[   17.504370] type=1505 audit(1230490712.802:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4408

[   17.636271] ip_tables: (C) 2000-2006 Netfilter Core Team

[   18.143128] ACPI: WMI: Mapper loaded

[   19.041426] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)

[   19.093158] apm: BIOS not found.

[   19.338397] ppdev: user-space parallel port driver

[   22.128291] Bluetooth: L2CAP ver 2.11

[   22.128305] Bluetooth: L2CAP socket layer initialized

[   22.165827] Bluetooth: RFCOMM socket layer initialized

[   22.165856] Bluetooth: RFCOMM TTY layer initialized

[   22.165862] Bluetooth: RFCOMM ver 1.10

[   22.175433] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

[   22.175447] Bluetooth: BNEP filters: protocol multicast

[   22.243105] Bridge firewalling registered

[   22.243959] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.

[   22.257648] Bluetooth: SCO (Voice Link) ver 0.6

[   22.257658] Bluetooth: SCO socket layer initialized

[   26.392338] r8169: eth0: link down

[   26.408234] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[   26.408394] iwl3945 0000:04:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)

[   26.408674] firmware: requesting iwlwifi-3945-1.ucode

[   26.629025] Registered led device: iwl-phy0:radio

[   26.629045] Registered led device: iwl-phy0:assoc

[   26.629098] Registered led device: iwl-phy0:RX

[   26.629112] Registered led device: iwl-phy0:TX

[   26.732062] NET: Registered protocol family 17

[   26.904661] [fglrx] Reserved FB block: Shared offset:0, size:1000000 

[   26.904667] [fglrx] Reserved FB block: Unshared offset:7f73000, size:88000 

[   26.904669] [fglrx] Reserved FB block: Unshared offset:7ffc000, size:4000 

[   65.312624] UDF-fs: No VRS found

[   65.378260] ISO 9660 Extensions: Microsoft Joliet Level 3

[   65.894435] ISO 9660 Extensions: RRIP_1991A

[   67.928451] canberra-gtk-pl[5977]: segfault at 496665d8 ip b70e384d sp b6e89f10 error 6 in libpulse.so.0.4.1[b70a4000+4e000]

[   72.232519] CPU0 attaching NULL sched-domain.

[   72.232540] CPU1 attaching NULL sched-domain.

[   72.240704] CPU0 attaching sched-domain:

[   72.240718]  domain 0: span 0-1 level MC

[   72.240725]   groups: 0 1

[   72.240737] CPU1 attaching sched-domain:

[   72.240742]  domain 0: span 0-1 level MC

[   72.240748]   groups: 1 0

[   73.283385] wlan0: authenticate with AP 00:16:e3:c2:2b:76

[   73.285141] wlan0: authenticated

[   73.285155] wlan0: associate with AP 00:16:e3:c2:2b:76

[   73.287241] wlan0: RX AssocResp from 00:16:e3:c2:2b:76 (capab=0x11 status=0 aid=5)

[   73.287248] wlan0: associated

[   93.869167] NET: Registered protocol family 10

[   93.869641] lo: Disabled Privacy Extensions

[   93.870121] ADDRCONF(NETDEV_UP): eth0: link is not ready

[  104.212022] wlan0: no IPv6 routers present

[  160.120059] usb 7-2: new high speed USB device using ehci_hcd and address 5

[  160.261895] usb 7-2: configuration #1 chosen from 1 choice

[  160.262995] scsi7 : SCSI emulation for USB Mass Storage devices

[  160.264900] usb-storage: device found at 5

[  160.264914] usb-storage: waiting for device to settle before scanning

[  165.260171] usb-storage: device scan complete

[  165.262653] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS

[  165.263371] scsi 7:0:0:1: CD-ROM            SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0

[  165.264987] sd 7:0:0:0: [sdd] 31306239 512-byte hardware sectors (16029 MB)

[  165.265723] sd 7:0:0:0: [sdd] Write Protect is off

[  165.265729] sd 7:0:0:0: [sdd] Mode Sense: 45 00 00 08

[  165.265731] sd 7:0:0:0: [sdd] Assuming drive cache: write through

[  165.267347] sd 7:0:0:0: [sdd] 31306239 512-byte hardware sectors (16029 MB)

[  165.268098] sd 7:0:0:0: [sdd] Write Protect is off

[  165.268104] sd 7:0:0:0: [sdd] Mode Sense: 45 00 00 08

[  165.268106] sd 7:0:0:0: [sdd] Assuming drive cache: write through

[  165.268441]  sdd: sdd1

[  165.269544] sd 7:0:0:0: [sdd] Attached SCSI removable disk

[  165.269811] sd 7:0:0:0: Attached scsi generic sg4 type 0

[  165.274730] sr1: scsi3-mmc drive: 48x/48x tray

[  165.274972] sr 7:0:0:1: Attached scsi CD-ROM sr1

[  165.275220] sr 7:0:0:1: Attached scsi generic sg5 type 5

[  165.416294] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.416302] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.416306] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.416311] end_request: I/O error, dev sr1, sector 196352

[  165.416315] Buffer I/O error on device sr1, logical block 49088

[  165.417167] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.417171] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.417174] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.417177] end_request: I/O error, dev sr1, sector 196356

[  165.417179] Buffer I/O error on device sr1, logical block 49089

[  165.418043] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.418046] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.418049] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.418053] end_request: I/O error, dev sr1, sector 196352

[  165.418055] Buffer I/O error on device sr1, logical block 49088

[  165.418919] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.418922] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.418925] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.418929] end_request: I/O error, dev sr1, sector 196356

[  165.418931] Buffer I/O error on device sr1, logical block 49089

[  165.419792] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.419795] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.419798] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.419802] end_request: I/O error, dev sr1, sector 196584

[  165.419804] Buffer I/O error on device sr1, logical block 49146

[  165.421172] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.421176] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.421180] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.421183] end_request: I/O error, dev sr1, sector 196588

[  165.421186] Buffer I/O error on device sr1, logical block 49147

[  165.422046] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.422049] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.422052] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.422055] end_request: I/O error, dev sr1, sector 196584

[  165.422057] Buffer I/O error on device sr1, logical block 49146

[  165.422919] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.422922] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.422925] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.422929] end_request: I/O error, dev sr1, sector 196588

[  165.422931] Buffer I/O error on device sr1, logical block 49147

[  165.425047] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.425051] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.425054] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.425058] end_request: I/O error, dev sr1, sector 196600

[  165.425060] Buffer I/O error on device sr1, logical block 49150

[  165.425924] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.425927] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.425930] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.425934] end_request: I/O error, dev sr1, sector 196600

[  165.426796] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.426799] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.426802] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.426806] end_request: I/O error, dev sr1, sector 196600

[  165.427672] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.427675] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.427678] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.427681] end_request: I/O error, dev sr1, sector 196600

[  165.428548] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.428550] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.428553] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.428557] end_request: I/O error, dev sr1, sector 196600

[  165.429425] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.429427] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.429430] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.429434] end_request: I/O error, dev sr1, sector 196600

[  165.430299] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.430302] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.430305] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.430308] end_request: I/O error, dev sr1, sector 196600

[  165.431172] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.431175] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.431178] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.431181] end_request: I/O error, dev sr1, sector 196536

[  165.432050] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK


[  165.432053] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.432056] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.432059] end_request: I/O error, dev sr1, sector 196540

[  165.432928] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.432931] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.432934] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.432938] end_request: I/O error, dev sr1, sector 196592

[  165.433801] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.433804] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.433807] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.433810] end_request: I/O error, dev sr1, sector 196596

[  165.434676] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.434679] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.434682] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.434686] end_request: I/O error, dev sr1, sector 196600

[  165.435550] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.435553] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.435556] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.435560] end_request: I/O error, dev sr1, sector 196600

[  165.483952] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.483959] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.483963] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.483967] end_request: I/O error, dev sr1, sector 196352

[  165.485325] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.485330] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.485333] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.485337] end_request: I/O error, dev sr1, sector 196356

[  165.488591] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.488594] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.488597] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.488601] end_request: I/O error, dev sr1, sector 196352

[  165.489957] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.489963] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.489967] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.489970] end_request: I/O error, dev sr1, sector 196356

[  165.491204] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.491210] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.491214] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.491218] end_request: I/O error, dev sr1, sector 196584

[  165.492080] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.492086] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.492090] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.492094] end_request: I/O error, dev sr1, sector 196588

[  165.492955] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.492961] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.492965] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.492968] end_request: I/O error, dev sr1, sector 196584

[  165.494454] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.494460] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.494463] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.494467] end_request: I/O error, dev sr1, sector 196588

[  165.499213] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.499221] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.499225] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.499229] end_request: I/O error, dev sr1, sector 196600

[  165.500651] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.500657] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.500661] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.500664] end_request: I/O error, dev sr1, sector 196600

[  165.501835] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.501840] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.501843] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.501847] end_request: I/O error, dev sr1, sector 196600

[  165.502960] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.502966] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.502969] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.502973] end_request: I/O error, dev sr1, sector 196600

[  165.504115] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.504120] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.504124] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.504127] end_request: I/O error, dev sr1, sector 196600

[  165.505340] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.505346] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.505349] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.505352] end_request: I/O error, dev sr1, sector 196600

[  165.507215] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.507221] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.507224] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.507228] end_request: I/O error, dev sr1, sector 196600

[  165.508359] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.508370] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.508375] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.508383] end_request: I/O error, dev sr1, sector 196536

[  165.509857] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.509867] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.509873] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.509880] end_request: I/O error, dev sr1, sector 196540

[  165.511349] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.511358] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.511364] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.511371] end_request: I/O error, dev sr1, sector 196592

[  165.513226] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.513235] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.513241] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.513248] end_request: I/O error, dev sr1, sector 196596

[  165.514841] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.514846] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.514849] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.514853] end_request: I/O error, dev sr1, sector 196600

[  165.516481] sr 7:0:0:1: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

[  165.516490] sr 7:0:0:1: [sr1] Sense Key : No Sense [current] 

[  165.516497] sr 7:0:0:1: [sr1] Add. Sense: No additional sense information

[  165.516505] end_request: I/O error, dev sr1, sector 196600

[ 4896.291399] VFS: busy inodes on changed media.

[ 4896.992422] VFS: busy inodes on changed media.

[ 4897.162310] VFS: busy inodes on changed media.

[ 4897.651304] VFS: busy inodes on changed media.

[ 4897.842452] VFS: busy inodes on changed media.

[ 4898.033652] VFS: busy inodes on changed media.

[ 4898.421963] VFS: busy inodes on changed media.

[ 4898.974797] VFS: busy inodes on changed media.

[ 4899.187080] VFS: busy inodes on changed media.

[ 4899.378377] VFS: busy inodes on changed media.

[ 4899.569516] VFS: busy inodes on changed media.

[ 4899.888424] VFS: busy inodes on changed media.

[ 4900.064571] VFS: busy inodes on changed media.

[ 4901.822148] VFS: busy inodes on changed media.

[ 4901.949635] VFS: busy inodes on changed media.

[ 4903.819766] VFS: busy inodes on changed media.

[ 4903.947342] VFS: busy inodes on changed media.

[ 4905.817487] VFS: busy inodes on changed media.

[ 4905.944973] VFS: busy inodes on changed media.

[ 4907.717896] VFS: busy inodes on changed media.

[ 4914.392499] wlan0: deauthenticated

[ 4915.392118] wlan0: authenticate with AP 00:16:e3:c2:2b:76

[ 4915.393946] wlan0: authenticated

[ 4915.393959] wlan0: associate with AP 00:16:e3:c2:2b:76

[ 4915.430728] wlan0: RX ReassocResp from 00:16:e3:c2:2b:76 (capab=0x11 status=0 aid=5)

[ 4915.430742] wlan0: associated

[ 5719.132281] CE: hpet increasing min_delta_ns to 15000 nsec

[ 7747.447091] wlan0: deauthenticated

[ 7748.448270] wlan0: authenticate with AP 00:16:e3:c2:2b:76

[ 7748.450646] wlan0: authenticated

[ 7748.450660] wlan0: associate with AP 00:16:e3:c2:2b:76

[ 7748.452870] wlan0: RX ReassocResp from 00:16:e3:c2:2b:76 (capab=0x11 status=0 aid=3)

[ 7748.452876] wlan0: associated

[11299.772644] __ratelimit: 33 callbacks suppressed

[11299.772653] pidgin[6214]: segfault at 0 ip 080b0a3e sp bff1ffa0 error 4 in pidgin[8048000+d5000]

[14312.544414] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

lsmod | grep snd


```
snd_hda_intel         381488  4 

snd_pcm_oss            46848  0 

snd_mixer_oss          22784  1 snd_pcm_oss

snd_seq_dummy          10884  0 

snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss

snd_seq_oss            38528  0 

snd_seq_midi           14336  0 

snd_rawmidi            29824  1 snd_seq_midi

snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi

snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              29960  2 snd_pcm,snd_seq

snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    63268  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              15328  1 snd

snd_page_alloc         16136  2 snd_hda_intel,snd_pcm

```

---

### Post by &gt;:3 on 2008-12-29
Also: I forgot to mention that I have windoze Drivers, on my windoze partition, if that's any help.

---

### Post by &gt;:3 on 2009-02-07
Bump, still no sound!

---

### Post by markbuntu on 2009-02-07
You most likely just need to fix your sound configuration. Just follow this guide here


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not help, there is troubleshooting and setup help here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by ohgodnotanother1 on 2009-02-08
Here is another guide that you might want to try:
[http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20081230-asus-onboard-soundcard-configuration-on-xubuntu.html](http://members.chello.hu/balla.gyorgy/balla-it/html/articles/20081230-asus-onboard-soundcard-configuration-on-xubuntu.html)

It's for 8.10 though, but I think it is the same configuration procedure.
Good luck!

---

### Post by wolfie on 2009-03-30
Try upgrading to Intrepid (Ubuntu 8.10)

wolfie

---

### Post by &gt;:3 on 2009-03-30
I'm already on 8.10, and I've been meaning to go through the rest of the instructions from markbuntu and ohgodnotanother1 (I've not had much time lately)

I'm hoping a fresh install of 9.04 will magically fix all problems, but I'm not holding my breath :\

---

### Post by markbuntu on 2009-03-30
What does aplay -l tell you?

---

### Post by &gt;:3 on 2009-03-30
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

^ That's my output from aplay -l

---

### Post by markbuntu on 2009-03-31
In here there is a Drivers section with a HDA part that you should check out first before taking any of the more drastic steps

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by &gt;:3 on 2009-03-31
Righty, just tried the HDA section of that awesome post, but I got stuck identifying my chip. 

aplay -l lists it as HDA Generic or ATI HDMI (I think...) So then I open /user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz to search for the chipset, then find: ```
The model name "genric" is treated as a special case. When this model 
is given, the driver uses the generic codec parser without "codec-patch".  
It's sometimes good for testing and debugging.
``` So I'm not sure what to do there...

I then followed [http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620) which gave me: 
head -n 1 /proc/asound/card0/codec#0
Codec: SigmaTel ID 7698
head -n 1 /proc/asound/card0/codec#1
Codec: LSI ID 1040
neither of these are listed under /user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz either. 

I tried killing pulse audio and sudo alsa force-reload, which didn't work either.

Someone else with the same hardware as myself has posted [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960)

P.S: Thanks for the help, it's *much* appreciated

---

### Post by markbuntu on 2009-03-31
Ahhh, well at least someone is paying attention.

---

### Post by &gt;:3 on 2009-06-12
In the [aforementioned bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960/comments/13") someone has linked to a patch: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960/comments/13](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960/comments/13)

And more information
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960/comments/13](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272960/comments/13)

The forum thread appears to be most useful (because it links to .deb(s), and I know what to do twith them :D), saying to > Please test the appropriate kernel at [http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/)

However, I'm not sure which is the appropriate one. As the Laptop has an intel Core 2 Duo Processor, I'm lead to believe it's 64 bit, so I'm currently on Jaunty, 64bit installation, but I'm not sure whether to use the Headers, Image, Restricted Modules, or Restricted-Modules Common .debs

Help?

---

### Post by &gt;:3 on 2009-06-20
> **>:3 said:**
> 
Help?

*Bump*

---

### Post by &gt;:3 on 2009-07-21
*re-bump*

---

### Post by qwerty800 on 2009-09-13
Errr...

I wouldn't recommend you to use those drivers, since they looks like hi-grade notino drivers, while you have an snd-hda-intel.

There's a bug in Launchpad about this. You should join us!
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/411574")

---

