---
title: "Happauge  - Audio &amp; Video not captured."
date: 2009-08-02
forum: Multimedia Software
---

### Post by EmmGeeImage on 2009-08-02
I went out and had to get a quick PC for audio and video production, a few years ago. I got this HP Media Center PC, with a Haupauge PVR PCI II video in (1 front, 1 back panel intake) and has a Realtek HD audio card. Windows failed on several instances of using the "Media Center, which seems to have made things corrupt on many occasions. Needless to say, I have 1 Ubuntu PC, and thought I'd try it on this same PC that I am typing on now.

Problem: I cannot get the Realtek HD Audio card to work with JJ (9.04), along with my Happauge WinTV PVR PCI II (26xx), to accept video inputs, as Windows did. Seems that both audio and video inputs seem null. I cannot capture either audio or video, unless I use Windows.

I'm running the Jaunty Jackalope (JJ) or Ubuntu 9.04. I have WINE 1.26 in the system as well. 

If anyone has any ideas, let me know.

Alsa, HD intel, OSS mixer, Pulse Audio mixer, nothing gets audio through it. So, I cannot even record on this PC. 

The other one is older, and does not have the same sound card and PVR card. Of course it's also shorter on Memory and Hard Drive space. So that's not an option.

---

### Post by EmmGeeImage on 2009-08-03
One other note, since I cannot edit my posting above...

I was also told that Myth TV and this V4L DVB would make the thing work. It did not. I am totally out of options at this point... I need help to get my "Prod" machine back up.... or just ditch linux all together.

I have seen several peeps say the latter of those 2, and would hope the open source community has answers to this problem, SO that more peeps do not leave linux and the OS community.

---

### Post by xc3RnbFO8P on 2009-08-03
In Terminal, show the output of:
> dmesg
and 
> lspci -vvn

---

### Post by EmmGeeImage on 2009-08-03
Does this mean that it will work??? I tried both of the above.


n't support DPO or FUA
[    4.688517]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    4.743521] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.743602] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.743675] ata_piix 0000:00:1f.1: version 2.12
[    4.743697] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.743743] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.743828] scsi4 : ata_piix
[    4.743908] scsi5 : ata_piix
[    4.744550] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    4.744555] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    4.908461] ata5.00: ATAPI: HP      DVD Writer 840x, S632, max UDMA/33
[    4.924413] ata5.00: configured for UDMA/33
[    4.925800] ata6: port disabled. ignoring.
[    4.927564] scsi 4:0:0:0: CD-ROM            HP       DVD Writer 840x  S632 PQ: 0 ANSI: 5
[    4.932691] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.932696] Uniform CD-ROM driver Revision: 3.20
[    4.932832] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.932886] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    4.933751] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.933776] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.933797] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.933802] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.933879] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    4.937776] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    4.937794] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    4.952020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.952132] usb usb1: configuration #1 chosen from 1 choice
[    4.952171] hub 1-0:1.0: USB hub found
[    4.952181] hub 1-0:1.0: 8 ports detected
[    4.952343] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.952364] uhci_hcd: USB Universal Host Controller Interface driver
[    4.952391] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.952399] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.952402] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.952458] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.952484] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fe00
[    4.952581] usb usb2: configuration #1 chosen from 1 choice
[    4.952619] hub 2-0:1.0: USB hub found
[    4.952628] hub 2-0:1.0: 2 ports detected
[    4.952737] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.952744] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.952748] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.952803] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.952836] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fd00
[    4.952932] usb usb3: configuration #1 chosen from 1 choice
[    4.952967] hub 3-0:1.0: USB hub found
[    4.952976] hub 3-0:1.0: 2 ports detected
[    4.953082] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.953089] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.953093] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.953153] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.953186] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fc00
[    4.953278] usb usb4: configuration #1 chosen from 1 choice
[    4.953312] hub 4-0:1.0: USB hub found
[    4.953321] hub 4-0:1.0: 2 ports detected
[    4.953431] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    4.953439] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    4.953443] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.953498] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    4.953530] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fb00
[    4.953623] usb usb5: configuration #1 chosen from 1 choice
[    4.953664] hub 5-0:1.0: USB hub found
[    4.953674] hub 5-0:1.0: 2 ports detected
[    4.953860] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.956468] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.956478] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.960076] mice: PS/2 mouse device common for all mice
[    4.960276] rtc_cmos 00:03: RTC can wake from S4
[    4.960326] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.960352] rtc0: alarms up to one month, 242 bytes nvram
[    4.960445] device-mapper: uevent: version 1.0.3
[    4.960548] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    4.960638] device-mapper: multipath: version 1.0.5 loaded
[    4.960642] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.960736] EISA: Probing bus 0 at eisa.0
[    4.960769] EISA: Detected 0 cards.
[    4.960830] cpuidle: using governor ladder
[    4.960834] cpuidle: using governor menu
[    4.961537] TCP cubic registered
[    4.961634] NET: Registered protocol family 10
[    4.962235] lo: Disabled Privacy Extensions
[    4.962696] NET: Registered protocol family 17
[    4.962721] Bluetooth: L2CAP ver 2.11
[    4.962724] Bluetooth: L2CAP socket layer initialized
[    4.962727] Bluetooth: SCO (Voice Link) ver 0.6
[    4.962730] Bluetooth: SCO socket layer initialized
[    4.962758] Bluetooth: RFCOMM socket layer initialized
[    4.962767] Bluetooth: RFCOMM TTY layer initialized
[    4.962770] Bluetooth: RFCOMM ver 1.10
[    4.964967] Using IPI No-Shortcut mode
[    4.965078] registered taskstats version 1
[    4.965229]   Magic number: 5:145:217
[    4.965316] rtc_cmos 00:03: setting system clock to 2009-08-03 07:14:02 UTC (1249283642)
[    4.965320] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.965324] EDD information not available.
[    4.965667] Freeing unused kernel memory: 532k freed
[    4.965852] Write protecting the kernel text: 4116k
[    4.965925] Write protecting the kernel read-only data: 1524k
[    4.993875] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.232952] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    5.232957] e100: Copyright(c) 1999-2006 Intel Corporation
[    5.233016] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.253632] e100 0000:01:08.0: PME# disabled
[    5.255549] e100: eth0: e100_probe: addr 0xfdefe000, irq 20, MAC addr 00:17:31:b9:f0:03
[    5.264575] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    5.275724] ohci1394 0000:01:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.366570] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.404331] usb 1-1: configuration #1 chosen from 1 choice
[    5.520028] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    5.585224] Initializing USB Mass Storage driver...
[    5.585358] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.585467] usbcore: registered new interface driver usb-storage
[    5.585473] USB Mass Storage support registered.
[    5.585578] usb-storage: device found at 2
[    5.585580] usb-storage: waiting for device to settle before scanning
[    5.653093] usb 1-2: configuration #1 chosen from 1 choice
[    5.653349] scsi7 : SCSI emulation for USB Mass Storage devices
[    5.654377] usb-storage: device found at 3
[    5.654381] usb-storage: waiting for device to settle before scanning
[    6.068543] PM: Starting manual resume from disk
[    6.068548] PM: Resume from partition 8:6
[    6.068550] PM: Checking hibernation image.
[    6.068673] PM: Resume from disk failed.
[    6.096025] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    6.109038] kjournald starting.  Commit interval 5 seconds
[    6.109057] EXT3-fs: mounted filesystem with ordered data mode.
[    6.269730] usb 5-1: configuration #1 chosen from 1 choice
[    6.272795] scsi8 : SCSI emulation for USB Mass Storage devices
[    6.272904] usb-storage: device found at 2
[    6.272909] usb-storage: waiting for device to settle before scanning
[    6.652155] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000b46801]
[   10.588904] usb-storage: device scan complete
[   10.619744] scsi 6:0:0:0: Direct-Access     WD       2500JB External  0108 PQ: 0 ANSI: 0
[   10.621212] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   10.621958] sd 6:0:0:0: [sdb] Write Protect is off
[   10.621962] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.621966] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.622834] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   10.623582] sd 6:0:0:0: [sdb] Write Protect is off
[   10.623586] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.623589] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.623594]  sdb: sdb1
[   10.624362] sd 6:0:0:0: [sdb] Attached SCSI disk
[   10.624440] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   10.652241] usb-storage: device scan complete
[   10.652731] scsi 7:0:0:0: Direct-Access     WD       3200AAV External 1.65 PQ: 0 ANSI: 4
[   10.653960] sd 7:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   10.654708] sd 7:0:0:0: [sdc] Write Protect is off
[   10.654713] sd 7:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   10.654716] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   10.655336] sd 7:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[   10.656084] sd 7:0:0:0: [sdc] Write Protect is off
[   10.656089] sd 7:0:0:0: [sdc] Mode Sense: 21 00 00 00
[   10.656092] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   10.656097]  sdc: sdc1
[   10.656715] sd 7:0:0:0: [sdc] Attached SCSI disk
[   10.656775] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   10.904493] udev: starting version 141
[   11.040627] parport_pc 00:06: reported by Plug and Play ACPI
[   11.040686] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   11.048860] Linux agpgart interface v0.103
[   11.060582] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[   11.061559] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   11.065086] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   11.219131] iTCO_vendor_support: vendor-support=0
[   11.220941] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.221154] iTCO_wdt: Found a ICH7DH TCO device (Version=2, TCOBASE=0x0460)
[   11.221255] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.274345] usb-storage: device scan complete
[   11.276348] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   11.276870] scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   11.279865] scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   11.282864] scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   11.287873] scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   11.293718] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[   11.293818] sd 8:0:0:0: Attached scsi generic sg4 type 0
[   11.299093] sd 8:0:0:1: [sde] Attached SCSI removable disk
[   11.299238] sd 8:0:0:1: Attached scsi generic sg5 type 0
[   11.304027] sd 8:0:0:2: [sdf] Attached SCSI removable disk
[   11.304168] sd 8:0:0:2: Attached scsi generic sg6 type 0
[   11.309060] sd 8:0:0:3: [sdg] Attached SCSI removable disk
[   11.309226] sd 8:0:0:3: Attached scsi generic sg7 type 0
[   11.584532] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.791223] ppdev: user-space parallel port driver
[   11.905792] Linux video capture interface: v2.00
[   12.028576] ivtv:  Start initialization, version 1.4.0
[   12.028664] ivtv0: Initializing card #0
[   12.028668] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   12.029835] ivtv 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.029847] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   12.065713] psmouse serio1: ID: 10 00 64<6>tveeprom 0-0050: Hauppauge model 26552, rev F0A3, serial# 9814792
[   12.080270] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   12.080274] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   12.080277] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   12.080280] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   12.080282] tveeprom 0-0050: has radio
[   12.080285] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   12.195209] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.195284] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.204171] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   12.225934] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   12.256513] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   12.268000] tda9887 0-0043: creating new instance
[   12.268004] tda9887 0-0043: tda988[5/6/7] found
[   12.269255] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   12.269301] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   12.291324] tuner-simple 0-0061: creating new instance
[   12.291329] tuner-simple 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   12.307067] cx25840 0-0044: firmware: requesting v4l-cx25840.fw
[   12.657574] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   15.621228] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   15.686971] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   15.687116] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   15.687263] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   15.687404] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   15.687540] ivtv0: Registered device radio0 for encoder radio
[   15.687544] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   15.687776] ivtv:  End initialization
[   15.842985] lp0: using parport0 (interrupt-driven).
[   15.987577] Adding 6016300k swap on /dev/sda6.  Priority:-1 extents:1 across:6016300k
[   16.537273] EXT3 FS on sda5, internal journal
[   17.797903] type=1505 audit(1249298055.330:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2213
[   17.852157] type=1505 audit(1249298055.386:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2217
[   17.852271] type=1505 audit(1249298055.386:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2217
[   17.852324] type=1505 audit(1249298055.386:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2217
[   17.852374] type=1505 audit(1249298055.386:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2217
[   17.896758] type=1505 audit(1249298055.430:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2222
[   18.044992] type=1505 audit(1249298055.579:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2226
[   18.045167] type=1505 audit(1249298055.579:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2226
[   18.082423] type=1505 audit(1249298055.614:10): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2230
[   18.113804] type=1505 audit(1249298055.646:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2234
[   25.544018] ivtv 0000:01:04.0: firmware: requesting v4l-cx2341x-enc.fw
[   25.604740] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   25.804163] ivtv0: Encoder revision: 0x02060039
[   28.172206] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.172210] Bluetooth: BNEP filters: protocol multicast
[   28.191438] Bridge firewalling registered
[   29.596785] [drm] Initialized drm 1.1.0 20060810
[   29.603038] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.603045] pci 0000:00:02.0: setting latency timer to 64
[   29.603260] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   29.605682] [drm:i915_setparam] *ERROR* unknown parameter 4
[   29.605716] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.201352] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   33.481570] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.484629] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   33.484969] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   44.180508] eth0: no IPv6 routers present
mikel@MikelProd:~$ 
mikel@MikelProd:~$ 
mikel@MikelProd:~$ 
mikel@MikelProd:~$ lspci -vvn
00:00.0 0600: 8086:2770 (rev 02)
	Subsystem: 103c:2a3b
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 0300: 8086:2772 (rev 02)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ff00 [size=8]
	Region 2: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at fdf80000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:1b.0 0403: 8086:27d8 (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1d.0 0c03: 8086:27c8 (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at fe00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 0c03: 8086:27c9 (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at fd00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 0c03: 8086:27ca (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at fc00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 0c03: 8086:27cb (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at fb00 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 0c03: 8086:27cc (rev 01) (prog-if 20)
	Subsystem: 103c:2a3b
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at fdfff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 0604: 8086:244e (rev e1) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000fbffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 0601: 8086:27b0 (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 0101: 8086:27df (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: 103c:2a3b
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at fa00 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 0104: 8086:27c3 (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 2303
	Region 0: I/O ports at f900 [size=8]
	Region 1: I/O ports at f800 [size=4]
	Region 2: I/O ports at f700 [size=8]
	Region 3: I/O ports at f600 [size=4]
	Region 4: I/O ports at f500 [size=16]
	Region 5: Memory at fdffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 0c05: 8086:27da (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 255
	Region 4: I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:01.0 0c00: 1106:3044 (rev c0) (prog-if 10)
	Subsystem: 0003:000f
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at ef00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

01:04.0 0400: 4444:0016 (rev 01)
	Subsystem: 0070:8801
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (32000ns min, 2000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: ivtv
	Kernel modules: ivtv

01:05.0 0780: 14f1:2f20
	Subsystem: 14f1:200c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at fdee0000 (32-bit, non-prefetchable) [size=64K]
	Region 1: I/O ports at ee00 [size=8]
	Capabilities: <access denied>

01:08.0 0200: 8086:27dc (rev 01)
	Subsystem: 103c:2a3b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fdefe000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at ed00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100

---

### Post by xc3RnbFO8P on 2009-08-03
You could try this (post #16)
[http://ubuntuforums.org/showthread.php?t=859090&page=2]("http://ubuntuforums.org/showthread.php?t=859090&page=2")

---

### Post by EmmGeeImage on 2009-08-03
Ringi:

As for the other posting, it did not work :


Re: Conexant Falcon II TV tuner setup help?
Here is one thing you can try:
add in /etc/modprobe.d/ivtv:
Quote:
options ivtv tuner=43 cardtype=7 newi2c=1
Otherwise this card is not working.
But if someone have more information about this card,
please add it here.



Here's my try on it:

mikel@MikelProd:~$ add in /etc/modprobe.d/ivtv:
bash: add: command not found
mikel@MikelProd:~$ options ivtv tuner=43 cardtype=7 newi2c=1
bash: options: command not found

either this isn't a good set of commands to make Ubuntu recognize the cards, or I am missing something totally.

---

### Post by xc3RnbFO8P on 2009-08-03
Did you install IVTV?

---

### Post by EmmGeeImage on 2009-08-03
I can't figure out how to "install" anything, since I don't have the repos commans. "BZ2" and "TAR" files mean nothing to me... take me through this step by step, since there are not instructions to go on. Do i move the files to the root drive? can;t seem to get anywhere. I am literally on the verge of going back to less hassles on Windows.... even if it is corrupt. At least I know where to put things in.

Please take me step by step... it's all non copyable things, The makefile says nothing to me. tried to copy into terminal, but nothing... bad commands.

VERY frustrating!

---

### Post by xc3RnbFO8P on 2009-08-03
IVTV should be in Synaptic Package Manager
ivtv-source
ivtv-utils

and read this:
[http://ubuntuforums.org/showthread.php?t=763698]("http://ubuntuforums.org/showthread.php?t=763698")

---

### Post by EmmGeeImage on 2009-08-03
yes, source codes, utils, etc are in.

However, Nothing comes through from walkman to Computer output speakers. still cannot capture either. MythTv does not let me see tv stations either.

I have also ran MYTHTV backend, to see if the tuner is set up. I had gone through the tuner setup. Still nothing.

---

### Post by EmmGeeImage on 2009-08-04
I did use the e-mail forms to contact Hauppauge support on this issue. Trust me, I will NEVER get a PC with a Hauppauge card in it again. I keep reading on how many peeps have problems with the cards, outside of Windows. If I had extra cash, I would get rid of the 150 card, for something that would work on the free based open source programs, without issues. 

I still have no video in, cannot record audio. I still need help. 

Those of you not liking the "gates" company, Looks like I may have to migrate back. Not enough is done to solve TV/PVR issues and others, for people to get the same results as that same company. Yes, security is at issue on that platform, but it is more workable, when loaded back in. That's the "gates" company advantage.

However, I still need some help. I'm still giving this a chance. I am praying that someone will be able to solve this, if Hauppauge cannot support it in Ubuntu linux 9.04. I think that's a huge possibility.

So, to this time, my problem is not solved. I do thank the one fellow that tried. Maybe more have some options.

---

