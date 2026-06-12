---
title: "Help with wireless usb dongle"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by MM7 on 2011-12-19
Hi

I'm very new to Ubuntu and stuck with something that should be simple.

I'm trying to follow these instructions: [http://ubuntuforums.org/showpost.php?p=9304551&postcount=4](http://ubuntuforums.org/showpost.php?p=9304551&postcount=4)

So far I've downloaded a file, renamed it, copied it to my usb stick and placed the file in a folder called 123 on my Ubuntu desktop.

I've tried to copy and paste the file into /lib/firmware/2.6.32-33-generic but it says I don't have access rights so I've tried the command sudo mv /home/mike/desktop/123/isl3887usb /lib/firmware/2.6.32-33-generic

I press enter and I get mv:cannot stat ' /home/mike/desktop/123/isl3887usb': No such file or directory 

Can someone please tell me where I'm going wrong and please tell me like a 2 year old as very, very newbie to all this.

Thanks

Mike

---

### Post by azmyth on 2011-12-19
```
sudo mv /home/mike/[COLOR="Red"]D[/COLOR]esktop/123/isl3887usb /lib/firmware/2.6.32-33-generic

```

Linux is case sensitive you need a capital D

---

### Post by seawolf167 on 2011-12-19
This is where tab completion is nice, if you enter part of the filename/folder then hit the [TAB] key, if there is a single unique completion, it will auto-complete, else it will fill in until the string branches. You can hit tab twice [TAB][TAB] to see a list of all possible completions. This saves you from having to laboriously type in each character of a file/folder's name.

If there is no completion available, then you know you've made a mistake somewhere (like the case-sensitive one here)

---

### Post by MM7 on 2011-12-19
Good answer azmyth.  That worked.  Thank you. :D

BUT

The next stage didn't work. :confused:

This is what I was greeted with.  Sorry for the photo as my legs are getting tired running between my XP machine and my Ubuntu machine taking too long to type out.

[IMG]http://i211.photobucket.com/albums/bb37/ManicMic/2011-12-19190450-1.jpg[/IMG]

---

### Post by MM7 on 2011-12-19
Any ideas why "Operation not permitted"?

---

### Post by seawolf167 on 2011-12-19
Add a *sudo* infront of the command[s] you used.

---

### Post by MM7 on 2011-12-19
Ah!  Makes sense.  Will try that soon.  Just installing Ubuntu 10.04.

Thanks for the reply. :D

---

### Post by MM7 on 2011-12-19
Ok.  Tried everything suggested and all I'm getting is "FATAL: Error inserting p54common. FATAL: Error inserting p54usb. FATAL: Error inserting mac80211.ko etc. etc.
Operation not permitted.

I've even tried installing linux-firmware-nonfree_1.8_all.deb I found from another thread.

All I'm trying to do is get my Dell 1450 usb wireless thingy to work on any version of Ubuntu.  How hard can that be? ](*,)

Anybody else got any ideas before I launch my pc out of the window?

---

### Post by MM7 on 2011-12-19
BTW...my usb wireless unit can see other networks but won't connect.
The light on the usb wireless unit comes on for 8 seconds and then goes out when plugged in.
The pc looks like it's going to connect but doesn't.

---

### Post by Wayne_V on 2011-12-19
run dmesg and check the last few lines for error messages.

---

### Post by MM7 on 2011-12-19
[IMG]http://i211.photobucket.com/albums/bb37/ManicMic/2011-12-19205208.jpg[/IMG]

---

### Post by Wayne_V on 2011-12-19
do you have a wired connection as well so you can ssh in and not have to take photos of the screen?

---

### Post by MM7 on 2011-12-19
I have no internet on the Ubuntu machine, yet.  I have just copied the results to my usb dongle and transferred it to my xp machine.  Eventually got the info in a readable format.

Try this:
```
[    0.153247] pci 0000:02:0a.0: reg 10 io port: [0xa000-0xa01f]
[    0.153309] pci 0000:02:0a.0: supports D1 D2
[    0.153357] pci 0000:02:0a.1: reg 10 io port: [0xa400-0xa407]
[    0.153418] pci 0000:02:0a.1: supports D1 D2
[    0.153477] pci 0000:00:1e.0: transparent bridge
[    0.153485] pci 0000:00:1e.0: bridge io port: [0xa000-0xafff]
[    0.153494] pci 0000:00:1e.0: bridge 32bit mmio: [0xe6000000-0xe67fffff]
[    0.153516] pci_bus 0000:00: on NUMA node 0
[    0.153531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.153795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.179503] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.179737] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.179955] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.180207] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.180427] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.180647] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.180867] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.181090] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.181401] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.181415] vgaarb: loaded
[    0.181728] SCSI subsystem initialized
[    0.181938] libata version 3.00 loaded.
[    0.182162] usbcore: registered new interface driver usbfs
[    0.182193] usbcore: registered new interface driver hub
[    0.182279] usbcore: registered new device driver usb
[    0.182669] ACPI: WMI: Mapper loaded
[    0.182675] PCI: Using ACPI for IRQ routing
[    0.183008] NetLabel: Initializing
[    0.183014] NetLabel:  domain hash size = 128
[    0.183017] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.183052] NetLabel:  unlabeled traffic allowed by default
[    0.183188] Switching to clocksource tsc
[    0.184356] AppArmor: AppArmor Filesystem Enabled
[    0.184418] pnp: PnP ACPI init
[    0.184472] ACPI: bus type pnp registered
[    0.191042] pnp: PnP ACPI: found 13 devices
[    0.191051] ACPI: ACPI bus type pnp unregistered
[    0.191061] PnPBIOS: Disabled by ACPI PNP
[    0.191093] system 00:00: iomem range 0xcd000-0xcffff has been reserved
[    0.191101] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.191108] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.191114] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.191122] system 00:00: iomem range 0x3fff0000-0x3fffffff could not be reserved
[    0.191129] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.191135] system 00:00: iomem range 0x100000-0x3ffeffff could not be reserved
[    0.191143] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.191150] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.191157] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.191165] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.191171] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.191189] system 00:02: ioport range 0x4000-0x40bf could not be reserved
[    0.191206] system 00:03: ioport range 0xb78-0xb7b has been reserved
[    0.191213] system 00:03: ioport range 0xf78-0xf7b has been reserved
[    0.191220] system 00:03: ioport range 0xa78-0xa7b has been reserved
[    0.191226] system 00:03: ioport range 0xe78-0xe7b has been reserved
[    0.191233] system 00:03: ioport range 0xbbc-0xbbf has been reserved
[    0.191240] system 00:03: ioport range 0xfbc-0xfbf has been reserved
[    0.191246] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.191253] system 00:03: ioport range 0x294-0x297 has been reserved
[    0.226273] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.226281] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.226290] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.226298] pci 0000:00:01.0:   PREFETCH window: 0xc0000000-0xdfffffff
[    0.226309] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.226316] pci 0000:00:1e.0:   IO window: 0xa000-0xafff
[    0.226326] pci 0000:00:1e.0:   MEM window: 0xe6000000-0xe67fffff
[    0.226333] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.226365] pci 0000:00:1e.0: setting latency timer to 64
[    0.226376] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.226381] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.226388] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.226394] pci_bus 0000:01: resource 1 mem: [0xe4000000-0xe5ffffff]
[    0.226400] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xdfffffff]
[    0.226406] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.226412] pci_bus 0000:02: resource 1 mem: [0xe6000000-0xe67fffff]
[    0.226417] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.226423] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.226512] NET: Registered protocol family 2
[    0.226758] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.227703] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.230306] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.231651] TCP: Hash tables configured (established 131072 bind 65536)
[    0.231661] TCP reno registered
[    0.232022] NET: Registered protocol family 1
[    0.232140] pci 0000:01:00.0: Boot video device
[    0.232679] cpufreq-nforce2: No nForce2 chipset.
[    0.232750] Scanning for low memory corruption every 60 seconds
[    0.233070] audit: initializing netlink socket (disabled)
[    0.233101] type=2000 audit(1324325782.232:1): initialized
[    0.247746] Trying to unpack rootfs image as initramfs...
[    0.265001] highmem bounce pool size: 64 pages
[    0.265018] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.273087] VFS: Disk quotas dquot_6.5.2
[    0.273327] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.275074] fuse init (API version 7.13)
[    0.275352] msgmni has been set to 1716
[    0.281404] alg: No test for stdrng (krng)
[    0.281661] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.281669] io scheduler noop registered
[    0.281676] io scheduler anticipatory registered
[    0.281682] io scheduler deadline registered
[    0.281797] io scheduler cfq registered (default)
[    0.282071] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.282131] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.282356] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.282367] ACPI: Power Button [PWRB]
[    0.282500] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.282507] ACPI: Power Button [PWRF]
[    0.282617] fan PNP0C0B:00: registered as cooling_device0
[    0.282631] ACPI: Fan [FAN] (on)
[    0.283137] Marking TSC unstable due to TSC halts in idle
[    0.283374] processor LNXCPU:00: registered as cooling_device1
[    0.287336] Switching to clocksource acpi_pm
[    0.288835] thermal LNXTHERM:01: registered as thermal_zone0
[    0.288858] ACPI: Thermal Zone [THRM] (70 C)
[    0.295157] isapnp: Scanning for PnP cards...
[    0.305488] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.305669] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.305834] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.306506] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.306761] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.357529] brd: module loaded
[    0.358690] loop: module loaded
[    0.358978] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.359254] ata_piix 0000:00:1f.1: version 2.13
[    0.359402] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.364794] scsi0 : ata_piix
[    0.365206] scsi1 : ata_piix
[    0.366986] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.366995] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.367967] Fixed MDIO Bus: probed
[    0.368120] PPP generic driver version 2.4.2
[    0.368316] tun: Universal TUN/TAP device driver, 1.6
[    0.368321] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.368559] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.368615] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.368664]   alloc irq_desc for 21 on node -1
[    0.368670]   alloc kstat_irqs on node -1
[    0.368686] ohci_hcd 0000:02:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.368726] ohci_hcd 0000:02:07.0: OHCI Host Controller
[    0.368822] ohci_hcd 0000:02:07.0: new USB bus registered, assigned bus number 1
[    0.368880] ohci_hcd 0000:02:07.0: irq 21, io mem 0xe6400000
[    0.960858] ata2.00: ATAPI: LITE-ON COMBO LTC-48161H, KH0F, max UDMA/33
[    0.969227] ata1.00: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
[    0.969237] ata1.00: 240121728 sectors, multi 16: LBA 
[    0.969518] ata1.01: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
[    0.969526] ata1.01: 240121728 sectors, multi 16: LBA 
[    0.977191] ata2.00: configured for UDMA/33
[    0.985331] ata1.00: configured for UDMA/100
[    1.044474] ata1.01: configured for UDMA/100
[    1.484412] isapnp: No Plug & Play device found
[    1.484778] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
[    1.485187] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.485514] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
[    1.485963] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.486356] sd 0:0:0:0: [sda] 240121728 512-byte logical blocks: (122 GB/114 GiB)
[    1.486476] sd 0:0:0:0: [sda] Write Protect is off
[    1.486483] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.486543] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.487178]  sda:
[    1.487300] scsi 1:0:0:0: CD-ROM            LITE-ON  COMBO LTC-48161H KH0F PQ: 0 ANSI: 5
[    1.495112] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[    1.495125] Uniform CD-ROM driver Revision: 3.20
[    1.495462] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.495640] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.503631]  sda1 sda2 < sda5 >
[    1.527688] sd 0:0:1:0: [sdb] 240121728 512-byte logical blocks: (122 GB/114 GiB)
[    1.527863] sd 0:0:1:0: [sdb] Write Protect is off
[    1.527870] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.527937] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.528476]  sdb: sdb1 < sdb5 >
[    1.554142] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.554368] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.645755] Freeing initrd memory: 7815k freed
[    1.665266] usb usb1: configuration #1 chosen from 1 choice
[    1.665350] hub 1-0:1.0: USB hub found
[    1.665394] hub 1-0:1.0: 2 ports detected
[    1.665541] uhci_hcd: USB Universal Host Controller Interface driver
[    1.665686]   alloc irq_desc for 19 on node -1
[    1.665692]   alloc kstat_irqs on node -1
[    1.665709] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.665731] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    1.665739] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    1.665894] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 2
[    1.665954] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000b000
[    1.666212] usb usb2: configuration #1 chosen from 1 choice
[    1.666284] hub 2-0:1.0: USB hub found
[    1.666314] hub 2-0:1.0: 2 ports detected
[    1.666436]   alloc irq_desc for 23 on node -1
[    1.666442]   alloc kstat_irqs on node -1
[    1.666457] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    1.666476] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    1.666483] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    1.666615] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 3
[    1.666674] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000b800
[    1.666930] usb usb3: configuration #1 chosen from 1 choice
[    1.667004] hub 3-0:1.0: USB hub found
[    1.667028] hub 3-0:1.0: 2 ports detected
[    1.667254] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.667261] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.668098] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.668436] mice: PS/2 mouse device common for all mice
[    1.668749] rtc_cmos 00:05: RTC can wake from S4
[    1.668877] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.668920] rtc0: alarms up to one month, 242 bytes nvram
[    1.669247] device-mapper: uevent: version 1.0.3
[    1.669628] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.669825] device-mapper: multipath: version 1.1.0 loaded
[    1.669833] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.670191] EISA: Probing bus 0 at eisa.0
[    1.670221] Cannot allocate resource for EISA slot 4
[    1.670227] Cannot allocate resource for EISA slot 5
[    1.670246] EISA: Detected 0 cards.
[    1.670483] cpuidle: using governor ladder
[    1.670587] cpuidle: using governor menu
[    1.671590] TCP cubic registered
[    1.672080] NET: Registered protocol family 10
[    1.674026] NET: Registered protocol family 17
[    1.674218] Using IPI No-Shortcut mode
[    1.674481] PM: Resume from disk failed.
[    1.674514] registered taskstats version 1
[    1.674860]   Magic number: 7:307:296
[    1.674927] tty tty29: hash matches
[    1.675030] rtc_cmos 00:05: setting system clock to 2011-12-19 20:16:24 UTC (1324325784)
[    1.675039] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.675043] EDD information not available.
[    1.675176] Freeing unused kernel memory: 668k freed
[    1.677221] Write protecting the kernel text: 4676k
[    1.677303] Write protecting the kernel read-only data: 1848k
[    1.690235] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.744152] udev: starting version 151
[    1.976199] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    2.155291] usb 2-2: configuration #1 chosen from 1 choice
[    2.316675] Floppy drive(s): fd0 is 1.44M
[    2.336336] FDC 0 is a post-1991 82077
[    2.452937] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    2.454686] usbcore: registered new interface driver hiddev
[    2.474130] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1f.2/usb2/2-2/2-2:1.0/input/input4
[    2.475045] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1f.2-2/input0
[    2.475143] usbcore: registered new interface driver usbhid
[    2.475543] usbhid: v2.6:USB HID core driver
[    2.599841] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.679436] usb 1-2: configuration #1 chosen from 1 choice
[   11.591731] Adding 3004408k swap on /dev/sda5.  Priority:-1 extents:1 across:3004408k 
[   11.703648] udev: starting version 151
[   11.891658] lp: driver loaded but no devices found
[   12.161169] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.388676] Linux agpgart interface v0.103
[   12.505515] parport_pc 00:0b: reported by Plug and Play ACPI
[   12.505576] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.533996] intel_rng: FWH not detected
[   12.590824] lp0: using parport0 (interrupt-driven).
[   12.752532] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   12.908408] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   13.084691] Initializing USB Mass Storage driver...
[   13.115466] scsi2 : SCSI emulation for USB Mass Storage devices
[   13.136251] usbcore: registered new interface driver usb-storage
[   13.136260] USB Mass Storage support registered.
[   13.136281] usb-storage: device found at 2
[   13.136285] usb-storage: waiting for device to settle before scanning
[   13.339730] gameport: EMU10K1 is pci0000:02:0a.1/gameport0, io 0xa400, speed 903kHz
[   13.542507] [drm] Initialized drm 1.1.0 20060810
[   13.660139] ppdev: user-space parallel port driver
[   13.800753] type=1505 audit(1324325796.624:2):  operation="profile_load" pid=541 name="/sbin/dhclient3"
[   13.801818] type=1505 audit(1324325796.624:3):  operation="profile_load" pid=541 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.802432] type=1505 audit(1324325796.624:4):  operation="profile_load" pid=541 name="/usr/lib/connman/scripts/dhclient-script"
[   14.054781] [drm] radeon defaulting to kernel modesetting.
[   14.054794] [drm] radeon kernel modesetting enabled.
[   14.054944]   alloc irq_desc for 16 on node -1
[   14.054950]   alloc kstat_irqs on node -1
[   14.054970] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.094674] [drm] radeon: Initializing kernel modesetting.
[   14.112233] [drm] register mmio base: 0xE5000000
[   14.112241] [drm] register mmio size: 65536
[   14.112618] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   14.112686] [drm] Generation 2 PCI interface, using max accessible memory
[   14.112712] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   14.112746] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   14.112777] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   14.112816] [drm] radeon: VRAM 128M
[   14.112820] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   14.112824] [drm] radeon: GTT 64M
[   14.112829] [drm] radeon: GTT from 0xE0000000 to 0xE3FFFFFF
[   14.112899] [drm] radeon: irq initialized.
[   14.113052] [drm] Detected VRAM RAM=128M, BAR=256M
[   14.113061] [drm] RAM width 128bits DDR
[   14.118072] [TTM] Zone  kernel: Available graphics memory: 443642 kiB.
[   14.118080] [TTM] Zone highmem: Available graphics memory: 513246 kiB.
[   14.118132] [drm] radeon: 128M of VRAM memory ready
[   14.118137] [drm] radeon: 64M of GTT memory ready.
[   14.118404] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   14.118433] [drm] radeon: cp idle (0x10000C03)
[   14.118744] [drm] Loading R300 Microcode
[   14.119629] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   14.159654] [drm] radeon: ring at 0x00000000E0000000
[   14.159689] [drm] ring test succeeded in 1 usecs
[   14.208132] [drm] radeon: ib pool ready.
[   14.208333] [drm] ib test succeeded in 0 usecs
[   14.210649] [drm] Default TV standard: NTSC
[   14.210658] [drm] 27.000000000 MHz TV ref clk
[   14.210663] [drm] No TV DAC info found in BIOS
[   14.210672] [drm] DFP table revision: 3
[   14.212932] [drm] Default TV standard: NTSC
[   14.212941] [drm] 27.000000000 MHz TV ref clk
[   14.213426] [drm] Radeon Display Connectors
[   14.213433] [drm] Connector 0:
[   14.213437] [drm]   VGA
[   14.213444] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   14.213448] [drm]   Encoders:
[   14.213452] [drm]     CRT1: INTERNAL_DAC1
[   14.213456] [drm] Connector 1:
[   14.213459] [drm]   DVI-I
[   14.213462] [drm]   HPD1
[   14.213468] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   14.213472] [drm]   Encoders:
[   14.213475] [drm]     CRT2: INTERNAL_DAC2
[   14.213479] [drm]     DFP1: INTERNAL_TMDS1
[   14.213482] [drm] Connector 2:
[   14.213486] [drm]   S-video
[   14.213489] [drm]   Encoders:
[   14.213492] [drm]     TV1: INTERNAL_DAC2
[   14.739280] type=1505 audit(1324325797.560:5):  operation="profile_load" pid=645 name="/usr/share/gdm/guest-session/Xsession"
[   14.808666] type=1505 audit(1324325797.632:6):  operation="profile_replace" pid=647 name="/sbin/dhclient3"
[   14.809805] type=1505 audit(1324325797.632:7):  operation="profile_replace" pid=647 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.810434] type=1505 audit(1324325797.632:8):  operation="profile_replace" pid=647 name="/usr/lib/connman/scripts/dhclient-script"
[   14.998268] [drm] fb mappable at 0xC0040000
[   14.998275] [drm] vram apper at 0xC0000000
[   14.998279] [drm] size 5242880
[   14.998283] [drm] fb depth is 24
[   14.998287] [drm]    pitch is 5120
[   15.067020] type=1505 audit(1324325797.888:9):  operation="profile_load" pid=648 name="/usr/bin/evince"
[   15.143193] fb0: radeondrmfb frame buffer device
[   15.143201] registered panic notifier
[   15.143221] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   15.153633] type=1505 audit(1324325797.976:10):  operation="profile_load" pid=648 name="/usr/bin/evince-previewer"
[   15.168131]   alloc irq_desc for 20 on node -1
[   15.168139]   alloc kstat_irqs on node -1
[   15.168156] EMU10K1_Audigy 0000:02:0a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.178478] vga16fb: initializing
[   15.178496] vga16fb: mapped to 0xc00a0000
[   15.178508] vga16fb: not registering due to another framebuffer present
[   15.243167] type=1505 audit(1324325798.065:11):  operation="profile_load" pid=648 name="/usr/bin/evince-thumbnailer"
[   15.691063] Console: switching to colour frame buffer device 160x64
[   18.144104] usb-storage: device scan complete
[   18.151776] scsi 2:0:0:0: Direct-Access     USB2.0   Flash Disk       2.10 PQ: 0 ANSI: 2
[   18.158668] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   18.175125] sd 2:0:0:0: [sdc] 129024 512-byte logical blocks: (66.0 MB/63.0 MiB)
[   18.183737] sd 2:0:0:0: [sdc] Write Protect is off
[   18.183747] sd 2:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[   18.183753] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   18.230739] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   18.230757]  sdc: sdc1
[   18.271730] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   18.271747] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  114.352063] usb 1-2: reset full speed USB device using ohci_hcd and address 2
[  114.532391] usb 1-2: device descriptor read/64, error -62
[  114.696146] usb 1-2: USB disconnect, address 2
[  152.856065] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  153.073651] usb 1-2: configuration #1 chosen from 1 choice
[  153.097254] scsi3 : SCSI emulation for USB Mass Storage devices
[  153.104417] usb-storage: device found at 3
[  153.104424] usb-storage: waiting for device to settle before scanning
[  158.106015] usb-storage: device scan complete
[  158.114977] scsi 3:0:0:0: Direct-Access     USB2.0   Flash Disk       2.10 PQ: 0 ANSI: 2
[  158.122439] sd 3:0:0:0: Attached scsi generic sg3 type 0
[  158.154050] sd 3:0:0:0: [sdc] 129024 512-byte logical blocks: (66.0 MB/63.0 MiB)
[  158.162971] sd 3:0:0:0: [sdc] Write Protect is off
[  158.162984] sd 3:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[  158.162990] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  158.209915] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  158.209932]  sdc: sdc1
[  158.255944] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[  158.255960] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[  880.312056] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  880.473135] usb 2-1: configuration #1 chosen from 1 choice
[  880.557593] cfg80211: Calling CRDA to update world regulatory domain
[  880.658120] cfg80211: World regulatory domain updated:
[  880.658131]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  880.658139]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  880.658146]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  880.658152]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  880.658159]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  880.658166]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  880.804055] usb 2-1: reset full speed USB device using uhci_hcd and address 3
[  880.945468] usb 2-1: firmware: requesting isl3887usb
[  880.951663] phy0: p54 detected a LM87 firmware
[  880.951671] p54: rx_mtu reduced from 3240 to 2384
[  880.951677] phy0: FW rev 2.13.24.0 - Softmac protocol 5.9
[  880.951682] phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[  881.974378] phy0: unknown rssi calibration data packing  type:(1908) len:14.
[  881.974396] rssical:00 00 8f 09 85 00 73 fe 78 14 83 00 76 fe        ......s.x...v.
[  881.974402] phy0: please report this issue.
[  881.974490] phy0: hwaddr 00:14:a5:9f:aa:c1, MAC:isl3892 RF:Xbow
[  882.049655] phy0: Selected rate control algorithm 'minstrel'
[  882.053117] Registered led device: p54-phy0::assoc
[  882.053311] Registered led device: p54-phy0::tx
[  882.053479] Registered led device: p54-phy0::rx
[  882.053655] Registered led device: p54-phy0::radio
[  882.053686] usb 2-1: is registered as 'phy0'
[  882.053767] usbcore: registered new interface driver p54usb
[  882.155941] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  902.237030] wlan0: deauthenticating from 30:46:9a:83:4a:10 by local choice (reason=3)
[  902.239112] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 1)
[  902.436084] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 2)
[  902.636080] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 3)
[  902.836067] wlan0: direct probe to AP 30:46:9a:83:4a:10 timed out
[  914.850949] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 1)
[  915.048078] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 2)
[  915.248078] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 3)
[  915.448074] wlan0: direct probe to AP 30:46:9a:83:4a:10 timed out
[  927.463010] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 1)
[  927.660075] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 2)
[  927.860070] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 3)
[  928.060064] wlan0: direct probe to AP 30:46:9a:83:4a:10 timed out
[  940.074917] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 1)
[  940.272115] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 2)
[  940.472088] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 3)
[  940.672104] wlan0: direct probe to AP 30:46:9a:83:4a:10 timed out
[  942.320120] usb 2-1: USB disconnect, address 3
[  984.539710] usbcore: deregistering interface driver p54usb
[ 1011.210078] cfg80211: Calling CRDA to update world regulatory domain
[ 1011.264453] cfg80211: World regulatory domain updated:
[ 1011.264464]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1011.264472]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1011.264478]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1011.264485]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1011.264491]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1011.264498]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1011.307382] usbcore: registered new interface driver p54usb
[ 1029.069555] usb 1-2: USB disconnect, address 3
[ 2777.420054] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 2777.637469] usb 1-2: configuration #1 chosen from 1 choice
[ 2777.816089] usb 1-2: reset full speed USB device using ohci_hcd and address 4
[ 2778.019752] usb 1-2: firmware: requesting isl3887usb
[ 2778.026076] phy0: p54 detected a LM87 firmware
[ 2778.026085] p54: rx_mtu reduced from 3240 to 2384
[ 2778.026091] phy0: FW rev 2.13.24.0 - Softmac protocol 5.9
[ 2778.026097] phy0: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[ 2779.065735] phy0: unknown rssi calibration data packing  type:(1908) len:14.
[ 2779.065750] rssical:00 00 8f 09 85 00 73 fe 78 14 83 00 76 fe        ......s.x...v.
[ 2779.065756] phy0: please report this issue.
[ 2779.065837] phy0: hwaddr 00:14:a5:9f:aa:c1, MAC:isl3892 RF:Xbow
[ 2779.117345] phy0: Selected rate control algorithm 'minstrel'
[ 2779.125441] Registered led device: p54-phy0::assoc
[ 2779.130027] Registered led device: p54-phy0::tx
[ 2779.131915] Registered led device: p54-phy0::rx
[ 2779.137329] Registered led device: p54-phy0::radio
[ 2779.137373] usb 1-2: is registered as 'phy0'
[ 2779.210632] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2902.521055] wlan0: deauthenticating from 30:46:9a:83:4a:10 by local choice (reason=3)
[ 2902.523086] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 1)
[ 2902.720086] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 2)
[ 2902.920085] wlan0: direct probe to AP 30:46:9a:83:4a:10 (try 3)
[ 2903.120082] wlan0: direct probe to AP 30:46:9a:83:4a:10 timed out
mike@mike-Ubuntu-desktop:~$ 


```

---

### Post by azmyth on 2011-12-19
Probably the pipe command is messing it up since you need sudo on both just do this in the same order.

```

sudo modprobe -r p54usb
sudo modprobe -r p54common
sudo modprobe p54usb
sudo modprobe p54common

```

---

### Post by MM7 on 2011-12-19
I have tried those commands several times now.  They do make the light on my usb wireless device come on but the light goes out after 8 seconds.

I can see my wireless router, and others nearby.  It does ask for my password to access my network and then looks like it's going to connect but it doesn't.  I've just tried it on my neighbours open network and I still couldn't connect.

I'm starting to think it's not driver related.  Maybe something else.

Any ideas?  Thanks for your efforts so far.

---

### Post by azmyth on 2011-12-19
Are you still getting the errors when you do the modprobe commands?

Another trick is to get the usb device number and do a search with that number on google as you may get additional help.

```
lsusb
```

will give you some numbers like

abcd:wxyz

Take the one for the dell device and search on the net.

after you modprobe what do these commands give you

```
ifconfig
iwconfig
```

---

### Post by MM7 on 2011-12-19
I've come up with a number: 413c:8104

Google has come up with something.  Now not sure what to do.

I'm going to call it a night now and will return in a few days as I'm a bit busy this week.

I'll be glad to get to the bottom of this for sure.

Many thanks for your help so far azmyth. :D

---

### Post by MM7 on 2011-12-19
> **azmyth said:**
> after you modprobe what do these commands give you

```
ifconfig
iwconfig
```

```
mike@mike-Ubuntu-desktop:~$ sudo modprobe -r p54usb
mike@mike-Ubuntu-desktop:~$ sudo modprobe -r p54common
mike@mike-Ubuntu-desktop:~$ sudo modprobe p54usb
mike@mike-Ubuntu-desktop:~$ sudo modprobe p54usb
mike@mike-Ubuntu-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:9f:aa:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mike@mike-Ubuntu-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by praseodym on 2011-12-19
Did you try to install the package "linux-firmware-nonfree"? Direct link:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.8_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.8_all.deb)

Installation by double-click. See the package list:

[http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree/filelist)

> /lib/firmware/isl3887usb

---

### Post by MM7 on 2011-12-19
Yes I've tried that by using these instructions: [http://ubuntuforums.org/showpost.php?p=9304551&postcount=4](http://ubuntuforums.org/showpost.php?p=9304551&postcount=4)

I tried 2.13.25.0.lm87.arm renamed to isl3887usb and then tried 2.13.25.0.lm86.arm renamed to isl3886usb.

I will try again by your method (double clicking) next time I can get to my pc.

Won't be able to do much until Friday, hopefully.

Back soon.

---

### Post by azmyth on 2011-12-19
Everything looks good. How are you trying to connect to the net through Ubuntu? I assume the neighbors doesn't have any encryption. If yes, I'd take your wifi off encryption and try to connect without just to see if it works. Anyhow, I guess you'll try when you get back.

---

### Post by Wayne_V on 2011-12-21
any chance you have MAC address filtering turned on on your router?    Does it log connection attempts?

---

### Post by MM7 on 2011-12-24
Sorry for not being able to get back on this forum for a few days.  I managed to solve the problem this afternoon.

I tried my Dell 1450 usb wireless dongle on my XP machine and it worked.
I took out the usb card out of my Ubuntu pc and installed it into my XP machine, plugged in the dongle and it didn't work.
I bought a new usb card today, installed it and "woohoo", I'm now on the internet.

I'd like to thank all the posters on this thread for your time and effort.  I hope you all have a happy Christmas and all that.

Cheers. :D

ps.  The next question will be along the lines of.....why is the pc running so slow and video stepping like crazy, but I'll wait until I'm totally sober for that question.  Hick!!

---

### Post by MM7 on 2011-12-25
Hi again.  I killed Ubuntu 10.04 due to it using 97% of the CPU for most things (even the process monitor).  Video was unwatchable due to stuttering and everything else would take ages to do anything.  A 1.5Gb Pentium 4 CPU and 1Gb of memory shouldn't be slow!!

So, I've now installed Ubuntu 11.10 and guess what?  No wireless connection again. ](*,)

I have tried double clicking linux-firmware-nonfree_1.8_all.deb file (after going into properties and ticking the "Allow executing file as program" but it keeps opening with Ubuntu Software Centre and the install button is greyed out.

Can anybody help please as I am loosing faith with Ubuntu.  I don't understand why it has to be so complicated yet doesn't work very well.

---

### Post by praseodym on 2011-12-25
Save the file to "Downloads" and install it from terminal:

> sudo dpkg -i ~/Downloads/*.deb

---

### Post by MM7 on 2011-12-25
Thank you praseodym.  That did the job and I'm now online again.

:D

---

