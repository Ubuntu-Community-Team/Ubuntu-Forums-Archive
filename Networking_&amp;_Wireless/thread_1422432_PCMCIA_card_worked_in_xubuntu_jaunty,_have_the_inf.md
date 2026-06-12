---
title: "PCMCIA card worked in xubuntu jaunty, have the inf driver, how can i get it to work?"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by bjaz on 2010-03-05
hello

still stalling after all those months,

everything is explained here

[http://ubuntuforums.org/showthread.php?t=1328098](http://ubuntuforums.org/showthread.php?t=1328098)

[http://ubuntuforums.org/showthread.php?t=1322717](http://ubuntuforums.org/showthread.php?t=1322717)

and here, with plenty of tests suggested by wonderful people who helped.
still stalling to this day : the card works fine in xubuntu jaunty, doesn't in xubuntu karmic or ubuntu karmic. i (my wife) wants to use ubutun karmic, but we still can't get this ATMEL PCMCIA wirelesscard to work on ubuntu karmic like it does on jaunty...

and we have the windows INF drivers

can anyone help ? it would be wonderful

all the  best

ben

---

### Post by bjaz on 2010-03-06
if i run lspcmcia under xubuntu jauty i get : 
, where the pcmcia wireless card works fine i get .

Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
Socket 0 Device 0:    [atmel_cs]             (bus ID: 0.0)

is there anyway to get the same driver runig under ubuntu karmic ?

please help me, i've really been stuck for month and everything else works fine

thanks

ben

---

### Post by bjaz on 2010-03-16
please, can't anyone help ? i'm really lost with this, I have the INF windows driver, on cd and also redownloaded, it works fine on the previous version, why can't I get this ATMEL PCMCIA card to work on Ubuntu Karmic ? there must be a way to fix this but I really do not know how.
i've been searching for a solution ever since karmic came out, somebody please help me out here

thanks

ben

---

### Post by chili555 on 2010-03-16
I notice this in your previously posted *dmesg*:> sony-laptop: acpi_evaluate_object failedThere are multiple repetitions of this message. I am not sure exactly what it means and I am Googling it now and suggest you do the same. *sony-laptop* is a module that is loaded so the kernel knows what to do when you press all the hotkeys, for example, Fn+F4. I am not sure that has much to do with your PCMCIA wireless, but it ought to be corrected if possible.

I also notice this:> Socket 0 Device 0: [[COLOR="Blue"]atmel_cs[/COLOR]] (bus ID: 0.0)*atmel_cs* is the native Linux driver for your device. I wonder why it is not being loaded correctly and creating a wireless interface. Please post:```
sudo modprobe atmel_cs
dmesg | grep atmel
```Thanks.

---

### Post by bjaz on 2010-03-16
doing this in a second, switching from the working jaunty intall to the karmic where the pcmcia doesn't work-- i must say i haven't looked at the hotkeys, it's a old Japanese sony VAIO

ok got 



WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


for sudo modprobe atmel_cs

---

### Post by bjaz on 2010-03-16
i went to synaptic and selected all ndiswrapper related files for a re-install, but still get the same message

---

### Post by chili555 on 2010-03-16
The module inserted without errors. What about the *dmesg* command?

---

### Post by bjaz on 2010-03-16
I get no answer / response for that one (the full 
dmesg | grep atmel

---

### Post by bjaz on 2010-03-16
dmesg by itself gives :

[    0.208875] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0040000-0xb007ffff]
[    0.208916] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]
[    0.209045] pci 0000:00:1b.0: reg 10 64bit mmio: [0xb0000000-0xb0003fff]
[    0.209113] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.209120] pci 0000:00:1b.0: PME# disabled
[    0.209186] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.209258] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.209330] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.209402] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.209478] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0004000-0xb00043ff]
[    0.209548] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.209554] pci 0000:00:1d.7: PME# disabled
[    0.209723] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.209732] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.209738] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.209776] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.209786] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.209796] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.209806] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.209816] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.209904] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]
[    0.210012] pci 0000:06:03.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.210048] pci 0000:06:03.0: supports D1 D2
[    0.210051] pci 0000:06:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.210059] pci 0000:06:03.0: PME# disabled
[    0.210124] pci 0000:06:03.2: reg 10 32bit mmio: [0xb0104000-0xb01047ff]
[    0.210137] pci 0000:06:03.2: reg 14 32bit mmio: [0xb0100000-0xb0103fff]
[    0.210216] pci 0000:06:03.2: supports D1 D2
[    0.210220] pci 0000:06:03.2: PME# supported from D0 D1 D2 D3hot
[    0.210227] pci 0000:06:03.2: PME# disabled
[    0.210288] pci 0000:06:03.3: reg 10 32bit mmio: [0xb0105000-0xb0105fff]
[    0.210376] pci 0000:06:03.3: supports D1 D2
[    0.210379] pci 0000:06:03.3: PME# supported from D0 D1 D2 D3hot
[    0.210386] pci 0000:06:03.3: PME# disabled
[    0.210465] pci 0000:06:08.0: reg 10 32bit mmio: [0xb0106000-0xb0106fff]
[    0.210478] pci 0000:06:08.0: reg 14 io port: [0x2000-0x203f]
[    0.210554] pci 0000:06:08.0: supports D1 D2
[    0.210557] pci 0000:06:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.210565] pci 0000:06:08.0: PME# disabled
[    0.210628] pci 0000:00:1e.0: transparent bridge
[    0.210634] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.210641] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.210687] pci_bus 0000:00: on NUMA node 0
[    0.210694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.211014] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.216320] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.216451] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.216578] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.216706] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.216836] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.216960] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.217087] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.217212] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.217468] SCSI subsystem initialized
[    0.217540] libata version 3.00 loaded.
[    0.217646] usbcore: registered new interface driver usbfs
[    0.217672] usbcore: registered new interface driver hub
[    0.217709] usbcore: registered new device driver usb
[    0.217887] ACPI: WMI: Mapper loaded
[    0.217890] PCI: Using ACPI for IRQ routing
[    0.218094] Bluetooth: Core ver 2.15
[    0.218133] NET: Registered protocol family 31
[    0.218136] Bluetooth: HCI device and connection manager initialized
[    0.218140] Bluetooth: HCI socket layer initialized
[    0.218143] NetLabel: Initializing
[    0.218146] NetLabel:  domain hash size = 128
[    0.218148] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.218168] NetLabel:  unlabeled traffic allowed by default
[    0.218371] hpet clockevent registered
[    0.218375] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.218384] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.218391] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.226470] pnp: PnP ACPI init
[    0.226506] ACPI: bus type pnp registered
[    0.229568] pnp: PnP ACPI: found 8 devices
[    0.229574] ACPI: ACPI bus type pnp unregistered
[    0.229580] PnPBIOS: Disabled by ACPI PNP
[    0.229599] system 00:04: ioport range 0x380-0x383 has been reserved
[    0.229604] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.229608] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.229612] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.229617] system 00:04: ioport range 0x1640-0x164f has been reserved
[    0.229622] system 00:04: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.229627] system 00:04: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.229632] system 00:04: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.229636] system 00:04: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.229641] system 00:04: iomem range 0xe0000000-0xefffffff has been reserved
[    0.264403] AppArmor: AppArmor Filesystem Enabled
[    0.264456] pci 0000:06:03.0: CardBus bridge, secondary bus 0000:07
[    0.264460] pci 0000:06:03.0:   IO window: 0x002400-0x0024ff
[    0.264469] pci 0000:06:03.0:   IO window: 0x002800-0x0028ff
[    0.264477] pci 0000:06:03.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.264485] pci 0000:06:03.0:   MEM window: 0x68000000-0x6bffffff
[    0.264494] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.264499] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.264507] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff
[    0.264514] pci 0000:00:1e.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.264532] pci 0000:00:1e.0: setting latency timer to 64
[    0.264544] pci 0000:06:03.0: enabling device (0000 -> 0003)
[    0.264555]   alloc irq_desc for 16 on node -1
[    0.264559]   alloc kstat_irqs on node -1
[    0.264567] pci 0000:06:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.264580] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.264584] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.264589] pci_bus 0000:06: resource 0 io:  [0x2000-0x2fff]
[    0.264593] pci_bus 0000:06: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.264597] pci_bus 0000:06: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.264601] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.264605] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.264609] pci_bus 0000:07: resource 0 io:  [0x2400-0x24ff]
[    0.264613] pci_bus 0000:07: resource 1 io:  [0x2800-0x28ff]
[    0.264617] pci_bus 0000:07: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.264621] pci_bus 0000:07: resource 3 mem: [0x68000000-0x6bffffff]
[    0.264676] NET: Registered protocol family 2
[    0.264817] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.265250] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.266658] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.267539] TCP: Hash tables configured (established 131072 bind 65536)
[    0.267545] TCP reno registered
[    0.267754] NET: Registered protocol family 1
[    0.267868] Trying to unpack rootfs image as initramfs...
[    0.567743] Freeing initrd memory: 7463k freed
[    0.575971] Simple Boot Flag at 0x36 set to 0x1
[    0.576124] cpufreq-nforce2: No nForce2 chipset.
[    0.576169] Scanning for low memory corruption every 60 seconds
[    0.576363] audit: initializing netlink socket (disabled)
[    0.576392] type=2000 audit(1268754643.575:1): initialized
[    0.589031] highmem bounce pool size: 64 pages
[    0.589040] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.591096] VFS: Disk quotas dquot_6.5.2
[    0.591181] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.591946] fuse init (API version 7.12)
[    0.592082] msgmni has been set to 1719
[    0.592356] alg: No test for stdrng (krng)
[    0.592372] io scheduler noop registered
[    0.592375] io scheduler anticipatory registered
[    0.592378] io scheduler deadline registered
[    0.592439] io scheduler cfq registered (default)
[    0.592459] pci 0000:00:02.0: Boot video device
[    0.592583] pci 0000:06:08.0: Firmware left e100 interrupts enabled; disabling
[    0.592691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.592726] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.594396] ACPI: AC Adapter [ADP1] (on-line)
[    0.594496] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.594502] ACPI: Power Button [PWRF]
[    0.594577] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.595715] ACPI: Lid Switch [LID0]
[    0.595779] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.595787] ACPI: Power Button [PWRB]
[    0.719972] Switched to high resolution mode on CPU 0
[    1.596156] Marking TSC unstable due to TSC halts in idle
[    1.596178] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.596217] processor LNXCPU:00: registered as cooling_device0
[    1.596222] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.602728] thermal LNXTHERM:01: registered as thermal_zone0
[    1.602740] ACPI: Thermal Zone [THRM] (57 C)
[    1.602805] isapnp: Scanning for PnP cards...
[    1.957496] isapnp: No Plug & Play device found
[    1.959016] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.960824] brd: module loaded
[    1.961448] loop: module loaded
[    1.961562] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.961719] ata_piix 0000:00:1f.1: version 2.13
[    1.961743]   alloc irq_desc for 18 on node -1
[    1.961746]   alloc kstat_irqs on node -1
[    1.961756] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.961814] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.961924] scsi0 : ata_piix
[    1.962057] scsi1 : ata_piix
[    1.962968] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.962972] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.964141] Fixed MDIO Bus: probed
[    1.964195] PPP generic driver version 2.4.2
[    1.964328] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.964355]   alloc irq_desc for 23 on node -1
[    1.964358]   alloc kstat_irqs on node -1
[    1.964367] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.964388] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.964394] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.964463] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.968395] ehci_hcd 0000:00:1d.7: debug port 1
[    1.968404] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.968655] ata2: port disabled. ignoring.
[    1.968717] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0004000
[    1.984017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.984128] usb usb1: configuration #1 chosen from 1 choice
[    1.984194] hub 1-0:1.0: USB hub found
[    1.984206] hub 1-0:1.0: 8 ports detected
[    1.984297] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.984326] uhci_hcd: USB Universal Host Controller Interface driver
[    1.984376] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.984385] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.984391] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.984448] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.984482] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.984588] usb usb2: configuration #1 chosen from 1 choice
[    1.984626] hub 2-0:1.0: USB hub found
[    1.984635] hub 2-0:1.0: 2 ports detected
[    1.984708]   alloc irq_desc for 19 on node -1
[    1.984711]   alloc kstat_irqs on node -1
[    1.984720] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.984728] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.984733] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.984771] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.984815] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.984916] usb usb3: configuration #1 chosen from 1 choice
[    1.984951] hub 3-0:1.0: USB hub found
[    1.984960] hub 3-0:1.0: 2 ports detected
[    1.985028] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.985036] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.985041] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.985080] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.985118] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.985233] usb usb4: configuration #1 chosen from 1 choice
[    1.985269] hub 4-0:1.0: USB hub found
[    1.985277] hub 4-0:1.0: 2 ports detected
[    1.985340] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.985348] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.985353] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.985391] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.985431] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    1.985543] usb usb5: configuration #1 chosen from 1 choice
[    1.985583] hub 5-0:1.0: USB hub found
[    1.985592] hub 5-0:1.0: 2 ports detected
[    1.985713] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.989359] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.993998] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.994009] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.994117] ACPI: Battery Slot [BAT0] (battery present)
[    1.994220] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.994225] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.994229] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.994314] mice: PS/2 mouse device common for all mice
[    1.994471] rtc_cmos 00:05: RTC can wake from S4
[    1.994517] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.994556] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.994735] device-mapper: uevent: version 1.0.3
[    1.994871] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.995056] device-mapper: multipath: version 1.1.0 loaded
[    1.995061] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.995268] EISA: Probing bus 0 at eisa.0
[    1.995278] Cannot allocate resource for EISA slot 1
[    1.995282] Cannot allocate resource for EISA slot 2
[    1.995315] EISA: Detected 0 cards.
[    1.995484] cpuidle: using governor ladder
[    1.995573] cpuidle: using governor menu
[    1.996256] TCP cubic registered
[    1.996477] NET: Registered protocol family 10
[    1.997077] lo: Disabled Privacy Extensions
[    1.997487] NET: Registered protocol family 17
[    1.997512] Bluetooth: L2CAP ver 2.13
[    1.997515] Bluetooth: L2CAP socket layer initialized
[    1.997519] Bluetooth: SCO (Voice Link) ver 0.6
[    1.997521] Bluetooth: SCO socket layer initialized
[    1.997630] Bluetooth: RFCOMM TTY layer initialized
[    1.997634] Bluetooth: RFCOMM socket layer initialized
[    1.997637] Bluetooth: RFCOMM ver 1.11
[    1.997676] Using IPI No-Shortcut mode
[    1.997792] PM: Resume from disk failed.
[    1.997819] registered taskstats version 1
[    1.997952]   Magic number: 2:561:841
[    1.998063] rtc_cmos 00:05: setting system clock to 2010-03-16 15:50:45 UTC (1268754645)
[    1.998068] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.998071] EDD information not available.
[    2.004081] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.140552] ata1.00: ATA-6: FUJITSU MHV2060AT, 00000096, max UDMA/100
[    2.140557] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.140614] ata1.01: ATAPI: HL-DT-ST DVDRAM GMA-4080N, 0S37, max UDMA/33
[    2.156467] ata1.00: configured for UDMA/100
[    2.172312] ata1.01: configured for UDMA/33
[    2.174827] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060A 0000 PQ: 0 ANSI: 5
[    2.175003] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.176599] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.176664] sd 0:0:0:0: [sda] Write Protect is off
[    2.176670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.176702] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.176881]  sda:
[    2.216021] Clocksource tsc unstable (delta = -208583804 ns)
[    2.216720]  sda1 sda2 sda3 <
[    2.218991] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GMA-4080N 0S37 PQ: 0 ANSI: 5
[    2.245897]  sda5 sda6 sda7 sda8sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.307881] Uniform CD-ROM driver Revision: 3.20
[    2.308021] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.308087] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.324566]  sda9 >
[    2.325067] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.325092] Freeing unused kernel memory: 540k freed
[    2.325524] Write protecting the kernel text: 4568k
[    2.325576] Write protecting the kernel read-only data: 1836k
[    2.500151] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/input/input5
[    2.500213] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[    2.589544] Linux agpgart interface v0.103
[    2.594566] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    2.595067] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    2.671347] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.671352] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.671431]   alloc irq_desc for 20 on node -1
[    2.671434]   alloc kstat_irqs on node -1
[    2.671447] e100 0000:06:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.704053] e100 0000:06:08.0: PME# disabled
[    2.749645] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    2.804793] e100: eth0: e100_probe: addr 0xb0106000, irq 20, MAC addr 00:01:4a:60:fa:c0
[    2.804866] ohci1394 0000:06:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.805903] [drm] Initialized drm 1.1.0 20060810
[    2.827302] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.827311] i915 0000:00:02.0: setting latency timer to 64
[    2.850519] i2c-adapter i2c-1: unable to read EDID block.
[    2.850527] i915 0000:00:02.0: LVDS-1: no EDID data
[    3.140012] [drm] DAC-6: set mode 640x480 0
[    3.140203] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0104000-b01047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.253441] i2c-adapter i2c-1: unable to read EDID block.
[    3.253450] i915 0000:00:02.0: LVDS-1: no EDID data
[    3.294148] [drm] TV-12: set mode NTSC 480i 0
[    3.424745] [drm] fb0: inteldrmfb frame buffer device
[    3.424759] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.489620] render error detected, EIR: 0x00000010
[    3.489625] page table error
[    3.489627]   PGTBL_ER: 0x00000100
[    3.489631] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    3.489644] render error detected, EIR: 0x00000010
[    3.489646] page table error
[    3.489648]   PGTBL_ER: 0x00000100
[    3.499485] [drm] LVDS-8: set mode 1280x800 16
[    3.526357] Console: switching to colour frame buffer device 160x50
[    4.127319] PM: Starting manual resume from disk
[    4.127326] PM: Resume from partition 8:7
[    4.127329] PM: Checking hibernation image.
[    4.127550] PM: Resume from disk failed.
[    4.160200] EXT4-fs (sda6): barriers enabled
[    4.177134] kjournald2 starting: pid 359, dev sda6:8, commit interval 5 seconds
[    4.177152] EXT4-fs (sda6): delayed allocation enabled
[    4.177157] EXT4-fs: file extents enabled
[    4.178951] EXT4-fs: mballoc enabled
[    4.178972] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    4.412193] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301e57dac]
[    5.147609] type=1505 audit(1268754648.648:2): operation="profile_load" pid=382 name=/usr/share/gdm/guest-session/Xsession
[    5.157168] type=1505 audit(1268754648.657:3): operation="profile_load" pid=383 name=/sbin/dhclient3
[    5.158071] type=1505 audit(1268754648.657:4): operation="profile_load" pid=383 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.158562] type=1505 audit(1268754648.657:5): operation="profile_load" pid=383 name=/usr/lib/connman/scripts/dhclient-script
[    5.248338] type=1505 audit(1268754648.749:6): operation="profile_load" pid=384 name=/usr/bin/evince
[    5.263298] type=1505 audit(1268754648.761:7): operation="profile_load" pid=384 name=/usr/bin/evince-previewer
[    5.272055] type=1505 audit(1268754648.773:8): operation="profile_load" pid=384 name=/usr/bin/evince-thumbnailer
[    5.317939] type=1505 audit(1268754648.817:9): operation="profile_load" pid=386 name=/usr/lib/cups/backend/cups-pdf
[    5.319013] type=1505 audit(1268754648.817:10): operation="profile_load" pid=386 name=/usr/sbin/cupsd
[    5.378144] type=1505 audit(1268754648.879:11): operation="profile_load" pid=387 name=/usr/sbin/tcpdump
[    6.775804] Adding 546168k swap on /dev/sda7.  Priority:-1 extents:1 across:546168k 
[    7.117545] EXT4-fs (sda6): internal journal on sda6:8
[    8.344603] udev: starting version 147
[    9.725165]   alloc irq_desc for 17 on node -1
[    9.725171]   alloc kstat_irqs on node -1
[    9.725181] tifm_7xx1 0000:06:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.748038] tifm_core: MMC/SD card detected in socket 0:0
[    9.908826] sony-laptop: Sony Notebook Control Driver v0.6.
[    9.909021] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/SNY5001:00/input/input6
[    9.909130] input: Sony Vaio Jogdial as /devices/virtual/input/input7
[    9.954811] intel_rng: FWH not detected
[   10.078240] lp: driver loaded but no devices found
[   10.188266] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.263365] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   10.279063] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   10.579111] yenta_cardbus 0000:06:03.0: CardBus bridge found [104d:818f]
[   10.579142] yenta_cardbus 0000:06:03.0: Enabling burst memory read transactions
[   10.579150] yenta_cardbus 0000:06:03.0: Using CSCINT to route CSC interrupts to PCI
[   10.579153] yenta_cardbus 0000:06:03.0: Routing CardBus interrupts to PCI
[   10.579162] yenta_cardbus 0000:06:03.0: TI: mfunc 0x01001b22, devctl 0x64
[   10.816058] yenta_cardbus 0000:06:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   10.816066] yenta_cardbus 0000:06:03.0: Socket status: 30000811
[   10.816072] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   10.816085] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   10.816090] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   10.816374] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   10.816379] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
[   11.452682] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   11.452701] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb0100000-0xb01fffff: excluding 0xb0100000-0xb010ffff
[   11.465781] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   11.893434] scsi2 : pata_pcmcia
[   11.893554] scsi3 : pata_pcmcia
[   11.893606] ata3: PATA max PIO0 cmd 0x2040 ctl 0x204e irq 3
[   11.893610] ata4: PATA max PIO0 cmd 0x2040 ctl 0x204e irq 3
[   11.960902] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.960957] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.013323] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   12.015729] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   12.016796] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   12.017655] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   12.018750] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.204514] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   13.208021] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x100f0000
[   17.064580] type=1505 audit(1268751060.565:12): operation="profile_replace" pid=898 name=/usr/share/gdm/guest-session/Xsession
[   17.067021] type=1505 audit(1268751060.565:13): operation="profile_replace" pid=899 name=/sbin/dhclient3
[   17.068132] type=1505 audit(1268751060.569:14): operation="profile_replace" pid=899 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.068631] type=1505 audit(1268751060.569:15): operation="profile_replace" pid=899 name=/usr/lib/connman/scripts/dhclient-script
[   17.076557] type=1505 audit(1268751060.577:16): operation="profile_replace" pid=900 name=/usr/bin/evince
[   17.097344] type=1505 audit(1268751060.597:17): operation="profile_replace" pid=900 name=/usr/bin/evince-previewer
[   17.106117] type=1505 audit(1268751060.605:18): operation="profile_replace" pid=900 name=/usr/bin/evince-thumbnailer
[   17.119641] type=1505 audit(1268751060.617:19): operation="profile_replace" pid=902 name=/usr/lib/cups/backend/cups-pdf
[   17.120752] type=1505 audit(1268751060.621:20): operation="profile_replace" pid=902 name=/usr/sbin/cupsd
[   17.125126] type=1505 audit(1268751060.625:21): operation="profile_replace" pid=903 name=/usr/sbin/tcpdump
[   17.426058] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.816169] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   19.816516] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.501436] [drm] DAC-6: set mode 640x480 0
[   20.615074] [drm] DAC-6: set mode 640x480 0
[   20.699039] i2c-adapter i2c-1: unable to read EDID block.
[   20.699046] i915 0000:00:02.0: LVDS-1: no EDID data
[   20.743886] [drm] TV-12: set mode NTSC 480i 0
[   20.885229] [drm] TV-12: set mode NTSC 480i 0
[   21.031887] [drm] DAC-6: set mode 640x480 0
[   21.138066] [drm] DAC-6: set mode 640x480 0
[   21.244842] i2c-adapter i2c-1: unable to read EDID block.
[   21.244849] i915 0000:00:02.0: LVDS-1: no EDID data
[   21.286606] [drm] TV-12: set mode NTSC 480i 0
[   21.428446] [drm] TV-12: set mode NTSC 480i 0
[   24.743660] ppdev: user-space parallel port driver
[   25.587561] NET: Registered protocol family 5
[   29.888028] eth0: no IPv6 routers present
[   36.296298] [drm] DAC-6: set mode 640x480 0
[   36.404188] [drm] DAC-6: set mode 640x480 0
[   36.486850] i2c-adapter i2c-1: unable to read EDID block.
[   36.486858] i915 0000:00:02.0: LVDS-1: no EDID data
[   36.528581] [drm] TV-12: set mode NTSC 480i 0
[   36.670993] [drm] TV-12: set mode NTSC 480i 0
[   36.823206] [drm] DAC-6: set mode 640x480 0
[   36.930427] [drm] DAC-6: set mode 640x480 0
[   37.007804] i2c-adapter i2c-1: unable to read EDID block.
[   37.007811] i915 0000:00:02.0: LVDS-1: no EDID data
[   37.050023] [drm] TV-12: set mode NTSC 480i 0
[   37.193542] [drm] TV-12: set mode NTSC 480i 0
[   37.376649] [drm] DAC-6: set mode 640x480 0
[   37.492939] [drm] DAC-6: set mode 640x480 0
[   37.573474] i2c-adapter i2c-1: unable to read EDID block.
[   37.573481] i915 0000:00:02.0: LVDS-1: no EDID data
[   37.615186] [drm] TV-12: set mode NTSC 480i 0
[   37.762013] [drm] TV-12: set mode NTSC 480i 0
[   41.082215] [drm] DAC-6: set mode 640x480 0
[   41.187953] [drm] DAC-6: set mode 640x480 0
[   41.264776] i2c-adapter i2c-1: unable to read EDID block.
[   41.264785] i915 0000:00:02.0: LVDS-1: no EDID data
[   41.306545] [drm] TV-12: set mode NTSC 480i 0
[   41.455899] [drm] TV-12: set mode NTSC 480i 0

---

### Post by bjaz on 2010-03-16
I guess this part's a little odd, but at least it's recognizing a card in the socket

[   10.579111] yenta_cardbus 0000:06:03.0: CardBus bridge found  [104d:818f]
[   10.579142] yenta_cardbus 0000:06:03.0: Enabling burst memory read  transactions
[   10.579150] yenta_cardbus 0000:06:03.0: Using CSCINT to route CSC  interrupts to PCI
[   10.579153] yenta_cardbus 0000:06:03.0: Routing CardBus interrupts to  PCI
[   10.579162] yenta_cardbus 0000:06:03.0: TI: mfunc 0x01001b22, devctl  0x64
[   10.816058] yenta_cardbus 0000:06:03.0: ISA IRQ mask 0x0cf8, PCI irq  16
[   10.816066] yenta_cardbus 0000:06:03.0: Socket status: 30000811
[   10.816072] pci_bus 0000:06: Raising subordinate bus# of parent bus  (#06) from #07 to #0a
[   10.816085] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge I/O  window: 0x2000 - 0x2fff
[   10.816090] pcmcia_socket pcmcia_socket0: cs: IO port probe  0x2000-0x2fff: clean.
[   10.816374] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge  Memory window: 0xb0100000 - 0xb01fffff
[   10.816379] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge  Memory window: 0x60000000 - 0x63ffffff
[   11.452682] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card  inserted into slot 0
[   11.452701] pcmcia_socket pcmcia_socket0: cs: memory probe  0xb0100000-0xb01fffff: excluding 0xb0100000-0xb010ffff
[   11.465781] pcmcia 0.0: pcmcia: registering new device pcmcia0.0

---

### Post by chili555 on 2010-03-16
I think when you boot back and forth, the atmel_cs module is not getting loaded automatically and so we don't see it in *dmesg*. That's why I wanted to load it explicitly and *without rebooting* see what the kernel did, or more probably, didn't do with atmel_cs. Please do:```
sudo modprobe atmel_cs
dmesg | grep atmel
```If it says nothing at all, that's still useful, albeit, puzzling information. I'd also like to see:```
lspcmcia -v ident
```Thanks.

---

### Post by bjaz on 2010-03-16
thanks to you.

i'm not booting back and forth, just staying on ubuntu karmic connected through ethernet

ok here it goes :

kayo@kayo-oppo:~$ sudo modprobe atmel_cs
[sudo] password for kayo: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
kayo@kayo-oppo:~$ dmesg | grep atmel
kayo@kayo-oppo:~$ 


the second command did nothing

now for 

kayo@kayo-oppo:~$ lspcmcia -v ident
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:06:03.0)
	Configuration:	state: on	ready: unknown
			Voltage: 3.3V Vcc: 3.3V Vpp: 0.0V
Socket 0 Device 0:	[pata_pcmcia]		(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   ATMEL AT76C502AR_E 
	Identification:	manf_id: 0x0000	card_id: 0x0000
			function: 6 (network)
			prod_id(1): "ATMEL" (0xabda4164)
			prod_id(2): "AT76C502AR_E" (0x4172e792)
			prod_id(3): --- (---)
			prod_id(4): --- (---)
kayo@kayo-oppo:~$

---

### Post by chili555 on 2010-03-16
I wonder if you have the firmware. Please do:```
sudo updatedb
locate atmel | grep firmware
```Thanks.

---

### Post by bjaz on 2010-03-16
got this

kayo@kayo-oppo:~$ sudo updatedb
[sudo] password for kayo: 
kayo@kayo-oppo:~$ locate atmel | grep firmware
/lib/firmware/atmel_at76c502-wpa.bin
/lib/firmware/atmel_at76c502.bin
/lib/firmware/atmel_at76c502_3com-wpa.bin
/lib/firmware/atmel_at76c502_3com.bin
/lib/firmware/atmel_at76c502d-wpa.bin
/lib/firmware/atmel_at76c502d.bin
/lib/firmware/atmel_at76c502e-wpa.bin
/lib/firmware/atmel_at76c502e.bin
/lib/firmware/atmel_at76c503-i3861.bin
/lib/firmware/atmel_at76c503-i3863.bin
/lib/firmware/atmel_at76c503-rfmd-0.90.2-140.bin
/lib/firmware/atmel_at76c503-rfmd-acc.bin
/lib/firmware/atmel_at76c503-rfmd.bin
/lib/firmware/atmel_at76c504.bin
/lib/firmware/atmel_at76c504_2958-wpa.bin
/lib/firmware/atmel_at76c504a_2958-wpa.bin
/lib/firmware/atmel_at76c504c-wpa.bin
/lib/firmware/atmel_at76c505-rfmd.bin
/lib/firmware/atmel_at76c505-rfmd2958.bin
/lib/firmware/atmel_at76c505a-rfmd2958.bin
/lib/firmware/atmel_at76c506-wpa.bin
/lib/firmware/atmel_at76c506.bin
/usr/share/doc/atmel-firmware
/usr/share/doc/atmel-firmware/README.gz
/usr/share/doc/atmel-firmware/changelog.Debian.gz
/usr/share/doc/atmel-firmware/copyright
/var/cache/apt/archives/atmel-firmware_1.3-4_all.deb
/var/lib/dpkg/info/atmel-firmware.list
/var/lib/dpkg/info/atmel-firmware.md5sums
/var/lib/dpkg/info/atmel-firmware.postinst
kayo@kayo-oppo:~$ 


thanks

b

---

### Post by bjaz on 2010-03-17
thanks again for your help
got any clues as to how i can  get this pcmcia card to work on karmic, when it works on jaunty and windows ?

thanks again

ben

---

### Post by chili555 on 2010-03-17
No idea. I have a couple of reports of cards that work in Jaunty perfectly well, but not Karmic. I suggest you search for bug reports on Launchpad and add to them or start a new one if your situation doesn't exactly match any existing bugs.

I noticed that *atmel_cs* is dependent on two other modules, *atmel* and *pcmcia*. You might do:```
sudo modprobe atmel_cs atmel pcmcia
```Then check:```
lsmod | grep -e atmel -e pcmcia
```Are they all loading correctly? Then check:```
dmesg | grep atmel
```Any signs of life?

You might also simply stick with Jaunty! You could also download the latest daily build of Lucid's live CD and see if it is an improvement. I have been trying it myself and I have found no significant issues. 

I am puzzled that your system doesn't seem to recognize your card and associate a driver with it at all. When the card is inserted, *dmesg* ought to spew out 3 or 4 messages.

---

### Post by bjaz on 2010-03-17
thanks- the problem is that her version of jaunty is a Xubuntu version, and it's really not the same workflow. my wife's been waiting for this wireless fix to get on ubuntu as with her now ram updated box it really runs better....
i think the card did work on ubuntu jaunty but still, i might buy a new more compatible card thqat do a reinstall downgrade.
i'll try your proposals :

kayo@kayo-oppo:~$ sudo modprobe atmel_cs atmel pcmcia
[sudo] password for kayo: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
kayo@kayo-oppo:~$ 

kayo@kayo-oppo:~$ lsmod | grep -e atmel -e pcmcia
atmel_cs                5436  0 
atmel                  35808  1 atmel_cs
pata_pcmcia            11228  1 
pcmcia                 36808  2 atmel_cs,pata_pcmcia
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
kayo@kayo-oppo:~$ 
kayo@kayo-oppo:~$ dmesg | grep atmel
kayo@kayo-oppo:~$

---

### Post by chili555 on 2010-03-17
> i might buy a new more compatible cardI reluctantly agree. I don't think your system is properly recognizing the card. I just inserted my old PCMCIA card and *dmesg* says:> [ 1721.392102] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[ 1721.392115] pcmcia_socket pcmcia_socket0: cs: memory probe 0xe4300000-0xe7ffffff: excluding 0xe4300000-0xe46cffff 0xe4e70000-0xe523ffff 0xe5db0000-0xe617ffff 0xe6cf0000-0xe70bffff
[ 1721.404843] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[ 1721.459633] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 1721.477645] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[ 1721.711887] eth1: Hardware identity 800c:0000:0001:0000
[ 1721.712060] eth1: Station identity  001f:0000:0001:0008
[ 1721.712066] eth1: Firmware determined as Intersil 1.8.0
[ 1721.712073] eth1: Ad-hoc demo mode supported
[ 1721.712078] eth1: IEEE standard IBSS ad-hoc mode supported
[ 1721.712084] eth1: WEP supported, 104-bit key
[ 1721.712210] eth1: MAC address 00:02:6f:09:5a:6f
[ 1721.712344] eth1: Station name "Prism  I"
[ 1721.713122] eth1: ready
[ 1721.714287] eth1: orinoco_cs at 0.0, irq 4, io 0xa100-0xa13f
[ 1721.740517] lib80211: common routines for IEEE802.11 drivers
[ 1721.740524] lib80211_crypt: registered algorithm 'NULL'In contrast, you get nothing.

I am sorry I was not able to help you further.

---

### Post by bjaz on 2010-03-18
thanks for the time you put into this.
I've started looking for cards today- would you by anychance know of an index of sorts to check for compatibility issues if i'm going to buy 2nd hand online ?
this is an old Japanese model of a sony VAIO, VGN FS21B--which might not be easy to see listed somewhere- running ubuntu karmic

---

### Post by chili555 on 2010-03-18
Here is the supported cards document: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It lists cards old and new for just the reasons you imply; some of us have to or even like to buy used.

If your PCMCIA slot is sound, and it may or may not be, any such card should work. I would try to buy it with an option to return it in case it's actually the laptop and not the card. I hope the fault is ***not*** the laptop!!

Good hunting and I hope you are successful.

---

### Post by bjaz on 2010-03-18
> **chili555 said:**
> Here is the supported cards document: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

It lists cards old and new for just the reasons you imply; some of us have to or even like to buy used.

If your PCMCIA slot is sound, and it may or may not be, any such card should work. I would try to buy it with an option to return it in case it's actually the laptop and not the card. I hope the fault is ***not*** the laptop!!

Good hunting and I hope you are successful.

hi and thanks. since the same PCMCIA card works fine on the same laptop under xubuntu jaunty and japanese windows XP, i think the slot is fine. but i'm still going to try and test the new card under ubuntu karmic. 

thanks again

b

---

### Post by bjaz on 2010-03-18
fixed....ended up buying an ASUS WL107G, worked out of the box....

thanks for your help

one last question for the road---what is the procedure for desinstalling the previous jaunty Xubuntu installs ? I'd like to keep just ubuntu karmic and the japanese windows XP--


should i be careful a use Gparted to delete partitions or is there a safer way to get rid of the xubuntu jaunty installs ? the grub is Ubuntu Karmic's anyway

thanks again

ben

---

### Post by chili555 on 2010-03-18
> should i be careful a use Gparted to delete partitions or is there a safer way to get rid of the xubuntu jaunty installs ? the grub is Ubuntu Karmic's anywayIf they are on separate partitions, then yes, *carefully *use Gparted on a live CD so the partitions are unmounted.

Great news about your new card!

---

