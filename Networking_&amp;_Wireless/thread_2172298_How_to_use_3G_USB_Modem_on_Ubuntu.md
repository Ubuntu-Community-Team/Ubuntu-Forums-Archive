---
title: "How to use 3G USB Modem on Ubuntu?"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by emptycoder on 2013-09-04
I have 3G USB Modem, how I can use it on Ubuntu? thanks!

---

### Post by CatKiller on 2013-09-04
A search for the model number and Ubuntu should tell you of any quirks, but I found it quite straightforward when I did it in the past: it did claim to be a surprising type of network device (dial-up modem, maybe? Can't remember) but was otherwise configured using the normal network manager tool on the panel.

Some dongles helpfully include Windows drivers with the device, which means that they get mounted as a removable storage device rather than being used as a network device. You need a package called usb-modeswitch or similar to make them not do this. I can't remember if that's installed by default or not.

---

### Post by emptycoder on 2013-09-04
Thanks CatKiller for your reply, if you're talking about usb-modeswitch and usb-modeswitch-data, they are installed by default on Ubuntu 12.04, but how do I know the USB is flipped to network device not to storage device?

---

### Post by CatKiller on 2013-09-04
If it works as a network device, it's the right way ;)

As I say, I don't know many details because it was painless when I did it, and I've only done it the once.

---

### Post by emptycoder on 2013-09-04
I mean, how to know it works? because I see nothing when I plug my USB, the only new thing appears on Network Manager is a new Wired Connection with status Unplugged?!

---

### Post by CatKiller on 2013-09-04
Ah, yeah, that was it: it showed up as a wired network card. So the device is in the correct mode and it's been detected by the system OK. All that's left is configuring the connection.

I don't think I had to do anything counter-intuitive, since I'd remember otherwise. It's possible that once I'd set things up there was a landing page in the browser similar to if you're using public wi-fi.

EDIT: Make sure the SIM card's in properly, too.

---

### Post by Bucky Ball on 2013-09-04
*Thread moved to **Networking & Wireless***

Try giving more information. This is scant. What version of Ubuntu are you using? What is the make/model of the USB dongle? Please read the link in my thread regarding the fastest way to get support. 

Plug in the dongle and issue this in a terminal:

```
dmesg
```

The last part should show the dongle being acknowledged when plugged in. Now issue this:

```
lsusb
```

Post the output here, please.

---

### Post by emptycoder on 2013-09-04
I have no idea how to configure it on Wired Connection, I tried it on Windows and the USB modem launches CD autoplay with exe file that installs an adapter with GUI app where you enter the username and password to active it.

Hey Bucky Ball, thanks for your reply, here's the output, the dmesg is very long but here are the results.

dmesg

```

[    0.939935] ACPI: Battery Slot [BAT0] (battery present)
[    0.939970] ERST: Table is not found!
[    0.939972] GHES: HEST is not enabled!
[    0.940277] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.952200] ACPI: Battery Slot [BAT0] (battery present)
[    1.013507] Freeing initrd memory: 14228k freed
[    1.179887] Linux agpgart interface v0.103
[    1.181447] brd: module loaded
[    1.182233] loop: module loaded
[    1.182353] ahci 0000:00:1f.2: version 3.0
[    1.182378] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.182434] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.182519] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x13 impl SATA mode
[    1.182523] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.182529] ahci 0000:00:1f.2: setting latency timer to 64
[    1.195956] scsi0 : ahci
[    1.196044] scsi1 : ahci
[    1.196118] scsi2 : ahci
[    1.196195] scsi3 : ahci
[    1.196272] scsi4 : ahci
[    1.196348] scsi5 : ahci
[    1.196471] ata1: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06100 irq 45
[    1.196475] ata2: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06180 irq 45
[    1.196477] ata3: DUMMY
[    1.196478] ata4: DUMMY
[    1.196481] ata5: SATA max UDMA/133 abar m2048@0xfbf06000 port 0xfbf06300 irq 45
[    1.196482] ata6: DUMMY
[    1.196866] Fixed MDIO Bus: probed
[    1.196881] tun: Universal TUN/TAP device driver, 1.6
[    1.196883] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.196948] PPP generic driver version 2.4.2
[    1.197060] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.197079] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.197096] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.197100] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.197156] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.197190] ehci_hcd 0000:00:1a.0: debug port 2
[    1.201159] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.201176] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfbf08000
[    1.215449] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.215608] hub 1-0:1.0: USB hub found
[    1.215612] hub 1-0:1.0: 2 ports detected
[    1.215674] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.215688] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.215692] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.215742] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.215767] ehci_hcd 0000:00:1d.0: debug port 2
[    1.219731] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.219745] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfbf07000
[    1.235418] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.235568] hub 2-0:1.0: USB hub found
[    1.235572] hub 2-0:1.0: 2 ports detected
[    1.235628] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.235639] uhci_hcd: USB Universal Host Controller Interface driver
[    1.235679] usbcore: registered new interface driver libusual
[    1.235713] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2] at 0x60,0x64 irq 1,12
[    1.259120] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.259126] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.259256] mousedev: PS/2 mouse device common for all mice
[    1.260070] rtc_cmos 00:03: RTC can wake from S4
[    1.260192] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.260225] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.260292] device-mapper: uevent: version 1.0.3
[    1.260371] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.260458] cpuidle: using governor ladder
[    1.260586] cpuidle: using governor menu
[    1.260588] EFI Variables Facility v0.08 2004-May-17
[    1.260792] TCP cubic registered
[    1.260878] NET: Registered protocol family 10
[    1.261297] NET: Registered protocol family 17
[    1.261300] Registering the dns_resolver key type
[    1.261463] PM: Hibernation image not present or could not be loaded.
[    1.261475] registered taskstats version 1
[    1.268674]   Magic number: 13:836:387
[    1.268716] thermal cooling_device2: hash matches
[    1.268848] rtc_cmos 00:03: setting system clock to 2013-09-04 16:22:29 UTC (1378311749)
[    1.269983] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.269984] EDD information not available.
[    1.289855] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.515082] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.515121] ata5: SATA link down (SStatus 0 SControl 300)
[    1.515159] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.519346] ata2.00: ATAPI: HL-DT-ST DVDRW/BDROM CT10N, A105, max UDMA/133
[    1.521385] ata1.00: ATA-8: SAMSUNG HM641JI, 2AJ10001, max UDMA/133
[    1.521390] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.524393] ata2.00: configured for UDMA/133
[    1.527014] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.527622] ata1.00: configured for UDMA/133
[    1.527976] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM641JI  2AJ1 PQ: 0 ANSI: 5
[    1.528218] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.528271] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.528534] sd 0:0:0:0: [sda] Write Protect is off
[    1.528539] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.528685] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.531651] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRWBD CT10N    A105 PQ: 0 ANSI: 5
[    1.537191] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.537196] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.537457] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.537592] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.563133]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.564519] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.565937] Freeing unused kernel memory: 924k freed
[    1.566090] Write protecting the kernel read-only data: 12288k
[    1.570294] Freeing unused kernel memory: 1592k freed
[    1.573647] Freeing unused kernel memory: 1188k freed
[    1.591890] udevd[106]: starting version 175
[    1.616139] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.616187] r8169 0000:13:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.616229] r8169 0000:13:00.0: setting latency timer to 64
[    1.616293] r8169 0000:13:00.0: irq 46 for MSI/MSI-X
[    1.621039] r8169 0000:13:00.0: eth0: RTL8102e at 0xffffc90000c72000, a4:ba:db:c8:3f:e5, XID 04e00000 IRQ 46
[    1.659801] hub 1-1:1.0: USB hub found
[    1.659881] hub 1-1:1.0: 6 ports detected
[    1.774618] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.898479] Refined TSC clocksource calibration: 2399.998 MHz.
[    1.898486] Switching to clocksource tsc
[    1.911414] hub 2-1:1.0: USB hub found
[    1.911494] hub 2-1:1.0: 8 ports detected
[    1.982432] usb 1-1.6: new high-speed USB device number 3 using ehci_hcd
[    2.190110] usb 2-1.6: new full-speed USB device number 3 using ehci_hcd
[    2.284755] hub 2-1.6:1.0: USB hub found
[    2.284933] hub 2-1.6:1.0: 3 ports detected
[    2.522390] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[    2.557661] usb 2-1.6.1: new full-speed USB device number 4 using ehci_hcd
[    2.725429] usb 2-1.6.2: new full-speed USB device number 5 using ehci_hcd
[   20.691429] Adding 262140k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262140k 
[   20.694963] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.713674] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   20.714092] udevd[484]: starting version 175
[   20.792571] lp: driver loaded but no devices found
[   20.815459] mei: module is from the staging directory, the quality is unknown, you have been warned.
[   20.818698] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.818706] mei 0000:00:16.0: setting latency timer to 64
[   20.818786] mei 0000:00:16.0: irq 47 for MSI/MSI-X
[   20.839725] ACPI Warning: _BQC returned an invalid level (20110623/video-526)
[   20.847307] acpi device:02: registered as cooling_device4
[   20.847908] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
[   20.848214] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   20.850867] wmi: Mapper loaded
[   20.868742] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   20.868747] Disabling lock debugging due to kernel taint
[   20.890010] cfg80211: Calling CRDA to update world regulatory domain
[   20.918389] brcmsmac 0000:12:00.0: bus 18 slot 0 func 0 irq 10
[   20.918413] brcmsmac 0000:12:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.918423] brcmsmac 0000:12:00.0: setting latency timer to 64
[   20.919132] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   20.919145] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   20.919181] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   20.923590] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   20.923628] [fglrx] Maximum main memory to use for locked dma buffers: 5638 MBytes.
[   20.923899] [fglrx]   vendor: 1002 device: 68e0 count: 1
[   20.924271] [fglrx] ioport: bar 4, base 0xe000, size: 0x100
[   20.924289] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.924294] pci 0000:01:00.0: setting latency timer to 64
[   20.924445] [fglrx] Kernel PAT support is enabled
[   20.924468] [fglrx] module loaded - fglrx 12.10.5 [Mar 28 2013] with 1 minors
[   20.937020] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.937089] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   20.937124] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.945171] Linux video capture interface: v2.00
[   20.946036] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (0c45:641d)
[   20.968067] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input6
[   20.968154] usbcore: registered new interface driver uvcvideo
[   20.968156] USB Video Class driver (1.1.1)
[   20.991434] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.991538] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.991834] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.991917] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   20.991942] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   20.997958] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.032882] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   21.032978] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   21.051644] input: Dell WMI hotkeys as /devices/virtual/input/input10
[   21.060167] cfg80211: World regulatory domain updated:
[   21.060171] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.060173] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.060176] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.060178] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.060180] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.060182] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.160833] type=1400 audit(1378304569.421:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=717 comm="apparmor_parser"
[   21.160855] type=1400 audit(1378304569.421:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=645 comm="apparmor_parser"
[   21.161199] type=1400 audit(1378304569.421:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=717 comm="apparmor_parser"
[   21.161266] type=1400 audit(1378304569.421:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=645 comm="apparmor_parser"
[   21.161396] type=1400 audit(1378304569.421:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=717 comm="apparmor_parser"
[   21.161498] type=1400 audit(1378304569.421:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=645 comm="apparmor_parser"
[   21.173631] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   21.173635] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173637] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   21.173639] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173641] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   21.173643] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173645] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   21.173648] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173650] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   21.173653] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173655] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   21.173657] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173659] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   21.173662] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173664] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   21.173667] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173669] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   21.173671] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173673] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   21.173676] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173678] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   21.173681] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.173683] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   21.173685] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.173688] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   21.173690] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.173693] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   21.173695] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.177407] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   21.178735] cfg80211: Calling CRDA for country: US
[   21.187804] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   21.187809] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187812] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   21.187815] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187818] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   21.187821] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187823] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   21.187826] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187828] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   21.187831] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187834] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   21.187837] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187839] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   21.187842] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187845] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   21.187848] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187851] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   21.187854] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187857] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   21.187860] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187863] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   21.187866] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187869] cfg80211: Disabling freq 2467 MHz
[   21.187871] cfg80211: Disabling freq 2472 MHz
[   21.187873] cfg80211: Disabling freq 2484 MHz
[   21.187876] cfg80211: Regulatory domain changed to country: US
[   21.187878] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.187881] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   21.187884] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   21.187887] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.187890] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.187893] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.187896] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   21.297164] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.1/2-1.6.1:1.0/input/input11
[   21.297390] generic-usb 0003:413C:8161.0001: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1d.0-1.6.1/input0
[   21.299971] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6.2/2-1.6.2:1.0/input/input12
[   21.300101] generic-usb 0003:413C:8162.0002: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1d.0-1.6.2/input0
[   21.300118] usbcore: registered new interface driver usbhid
[   21.300120] usbhid: USB HID core driver
[   21.364937] init: failsafe main process (881) killed by TERM signal
[   21.393240] Bluetooth: Core ver 2.16
[   21.393268] NET: Registered protocol family 31
[   21.393270] Bluetooth: HCI device and connection manager initialized
[   21.393273] Bluetooth: HCI socket layer initialized
[   21.393275] Bluetooth: L2CAP socket layer initialized
[   21.393461] Bluetooth: SCO socket layer initialized
[   21.401160] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.401164] Bluetooth: BNEP filters: protocol multicast
[   21.421652] Bluetooth: RFCOMM TTY layer initialized
[   21.421660] Bluetooth: RFCOMM socket layer initialized
[   21.421662] Bluetooth: RFCOMM ver 1.11
[   21.799596] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.806127] r8169 0000:13:00.0: eth0: link down
[   21.807964] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.808262] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.842715] ppdev: user-space parallel port driver
[   21.853962] type=1400 audit(1378304570.113:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=986 comm="apparmor_parser"
[   21.854479] type=1400 audit(1378304570.113:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=986 comm="apparmor_parser"
[   21.855825] type=1400 audit(1378304570.117:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=994 comm="apparmor_parser"
[   21.856704] type=1400 audit(1378304570.117:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=994 comm="apparmor_parser"
[   22.021804] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   22.062929] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.099000] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   22.457114] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   22.503619] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   22.503623] vesafb: scrolling: redraw
[   22.503625] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   22.505589] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90011980000, using 3072k, total 3072k
[   22.505765] Console: switching to colour frame buffer device 128x48
[   22.505794] fb0: VESA VGA frame buffer device
[   22.528216] init: gdm main process (1100) killed by TERM signal
[   22.710434] vboxdrv: Found 4 processor cores.
[   22.710878] vboxdrv: fAsync=0 offMin=0x23a offMax=0x1956
[   22.710954] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.710957] vboxdrv: Successfully loaded version 4.2.16 (interface 0x001a0005).
[   22.768510] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   22.904811] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   22.905295] [fglrx] Firegl kernel thread PID: 1161
[   22.905346] [fglrx] Firegl kernel thread PID: 1162
[   22.905395] [fglrx] Firegl kernel thread PID: 1163
[   22.905483] [fglrx] IRQ 50 Enabled
[   22.917772] vboxpci: IOMMU not found (not registered)
[   22.920764] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.920768] [fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   22.920771] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   25.619530] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[   25.621148] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  100.425986] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  100.427596] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  100.817323] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  100.828965] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  115.775090] r8169 0000:13:00.0: eth0: link up
[  115.776186] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  118.611939] usb 1-1.2: new low-speed USB device number 4 using ehci_hcd
[  118.709858] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input14
[  118.710136] generic-usb 0003:2188:0AE1.0003: input,hidraw1: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1a.0-1.2/input0
[  126.511278] eth0: no IPv6 routers present
[  131.375432] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  131.377138] [fglrx:firegl_apl_loadDatabase] *ERROR* APL: apl initialize fail.
[  145.545548] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:60:4c:42:12:9a:08:00 SRC=192.168.2.1 DST=224.0.0.251 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5287 PROTO=2 
[  145.545751] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:5c:59:48:db:de:74:08:00 SRC=192.168.2.15 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=14714 PROTO=2 
[  146.123411] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:98:fe:94:61:46:87:08:00 SRC=192.168.2.11 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=55662 PROTO=2 
[  192.890143] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:60:4c:42:12:9a:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5291 PROTO=2 
[  194.629118] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:98:fe:94:61:46:87:08:00 SRC=192.168.2.11 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=12931 PROTO=2 
[  257.297789] r8169 0000:13:00.0: eth0: link down
[  258.931400] r8169 0000:13:00.0: eth0: link up
[  259.915097] r8169 0000:13:00.0: eth0: link down
[  261.559177] r8169 0000:13:00.0: eth0: link up
[  268.526202] usb 2-1.1: new high-speed USB device number 6 using ehci_hcd
[  268.852756] Initializing USB Mass Storage driver...
[  268.852941] scsi6 : usb-storage 2-1.1:1.0
[  268.853052] usbcore: registered new interface driver usb-storage
[  268.853055] USB Mass Storage support registered.
[  269.848324] scsi 6:0:0:0: CD-ROM            BCM-CD V 01.02 01.01 1.13      PQ: 0 ANSI: 2
[  269.850498] sr1: scsi3-mmc drive: 0x/0x xa/form2 tray
[  269.850811] sr 6:0:0:0: Attached scsi CD-ROM sr1
[  269.851024] sr 6:0:0:0: Attached scsi generic sg2 type 5
[  269.931133] usb 2-1.1: reset high-speed USB device number 6 using ehci_hcd
[  270.234526] usb 2-1.1: reset high-speed USB device number 6 using ehci_hcd
[  270.453881] scsi 6:0:0:0: rejecting I/O to offline device
[  270.453891] scsi 6:0:0:0: killing request
[  270.628149] usb 2-1.1: USB disconnect, device number 6
[  270.825361] usb 2-1.1: new high-speed USB device number 7 using ehci_hcd
[  271.108359] bcm_wimax: module is from the staging directory, the quality is unknown, you have been warned.
[  271.109340] beceem: Beceem Communications Inc. WiMAX driver, 5.2.45
[  271.109347] Copyright 2010. Beceem Communications Inc
[  271.109449] usbbcm_device_probe:subtype[1] = 0x000000ff
[  271.109452] usbbcm_device_probe:subtype[2] = 0x00000000
[  271.109455] usbbcm_device_probe:subtype[4] = 0x00000000
[  271.109457] usbbcm_device_probe:subtype[8] = 0x00000000
[  271.109461] InitAdapter:Initialising Adapter = ffff8801012c0780
[  271.109492] InitAdapter:Adapter initialised
[  271.109496] usbbcm_device_probe:psIntfAdapter 0xffff88010d64a000
[  271.109596] usb 2-1.1: RDM Chip ID 0xbece3301
[  271.128230] beceem: AutoSyncup is Disabled
[  271.128235] beceem: Disabling autolink up
[  271.128238] beceem: DDR Setting: 3
[  271.128240] beceem: Power Save Mode: 0
[  271.128242] beceem: Enabling Auto Firmware Download
[  271.128245] beceem: MIPSConfig   : 0x0
[  271.128247] beceem: PMU MODE: 0
[  271.128249] beceem: uiEEPROMFlag  : 0x2
[  271.128845] reset_card_proc:Reseting UMA-B
[  271.204648] usb 2-1.1: reset high-speed USB device number 7 using ehci_hcd
[  271.428250] ddr_init:Register Count is =48
[  271.443815] usbbcm 2-1.1:1.0: beceem eth1: register usb-0000:00:1d.0-1.1 f8:3d:ff:89:c4:28
[  271.713471] BcmFileDownload:Opened file is = /lib/firmware/macxvi200.bin and length =0x1efe40 to be downloaded at =0xbfc00000
[  271.713477] BcmFileDownload:download start 140e95e84d8
[  272.095622] InterfaceFileDownload:Got end of file!
[  272.343201] InterfaceFileReadbackFromChip:Got end of file!
[  272.360316] usbcore: registered new interface driver usbbcm
[  272.393488] beceem eth1: enabling interface
[  272.394472] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  272.394926] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  299.250770] r8169 0000:13:00.0: eth0: link down
[  303.957780] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

lsusb

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 004: ID 2188:0ae1  
Bus 002 Device 007: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter

```

---

### Post by Bucky Ball on 2013-09-04
Well, dmesg seems to pick up you're plugging it in and this is what you have from the readout of lsusb:

Beceem Communications Inc. BCSM250 WiMAX Adapter

Does that sound right? Currently doing a bit of sniffing but not sure I can help much beyond helping you confirm the device is being recognised. Could you also give the result, with it plugged in, of these two commands, issued separately:

```
iwconfig
sudo lshw -C network
```

---

### Post by emptycoder on 2013-09-04
Yup, it's Beceem Communications Inc. BCSM250 WiMAX Adapter, no doubt about it.

iwconfig

```

lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```

sudo lshw -C network

```

  *-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 01
       serial: 70:f1:a1:92:0d:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.0-52-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbd00000-fbd03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:13:00.0
       logical name: eth0
       version: 02
       serial: a4:ba:db:c8:3f:e5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:d000(size=256) memory:d0c10000-d0c10fff memory:d0c00000-d0c0ffff memory:fb300000-fb31ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: f8:3d:ff:89:c4:28
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=beceem driverversion=5.2.45 duplex=full firmware=1.2 link=no multicast=yes port=twisted pair

```

Many people said that used Mobile Broadband to connect, but mine only shows as Wired Connection which drives me crazy, don't really know what to do.

---

### Post by Bucky Ball on 2013-09-04
Well, your internal card is using wlan0, which is where your USB wireless probably needs to be. That or wlan1, rather than eth1 which is what it seems to be getting assigned to now.

Unsure why this is happening also. :-k

---

### Post by CatKiller on 2013-09-04
It doesn't matter that it's showing up as a wired connection; it'll work anyway. My other half's laptop (that I configured for her) works in exactly this fashion with some generic dongle that she got from the phone company.

---

### Post by emptycoder on 2013-09-04
Can you tell me what configuration did you use to make it work as Wire Connection?
I really don't know that much about networking, like MAC address, Cloned MAC address, 802.1x Security, IPv4 or v6 settings... etc
Guys please, any help will be appreciated, I'm having this problem for more than 3 months and I don't want to use Windows!:(

---

### Post by CatKiller on 2013-09-04
I think it was just Auto all the way. As I said, if it was something really complicated I'd have remembered the process. Once the network connection came up I'm fairly sure that opening a browser window gave me a landing page so that I could sign away our firstborn and then it was good to go.

If you've been fiddling with it for three months, though, then anything could have happened.

EDIT: Just checked the connection settings and it's set to "connect automatically," "available to all users," and "Automatic (DHCP)" on the IPv4 tab.

EDIT 2: The SIM card was definitely separate, though, and needed to be put in.

---

### Post by emptycoder on 2013-09-04
CatKiller, all the settings you mentioned were exact the same.
"Sigh" I guess there's no use. I'm so disappointed but thanks for help, I really appreciate it.
I remember a trick that I found on one of those forums where you use Virtual Machine as an Internet source, where you can use Windows inside Ubuntu, maybe that will help me to connect to Internet, although I don't know that much about Virtualization.
I have made a thread in the past about this matter and got no responds, I think I will repost it again.

---

