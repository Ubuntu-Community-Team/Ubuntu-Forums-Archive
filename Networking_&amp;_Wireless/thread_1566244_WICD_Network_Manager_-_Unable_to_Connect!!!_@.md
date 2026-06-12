---
title: "WICD Network Manager - Unable to Connect!!! :@"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by nchung1988 on 2010-09-02
Samsung N150 Laptop

I installed WICD. I can see all the wireless networks, and wired works fine, but everytime I try connecting to a wireless network it says, "Unable to get IP"

Can someone help me remedy this? I am very new to ubuntu so I have no idea how to do anything...

When I go to Network Tools, I see:
Network Device: Loopback interface
IPv6 - Ip Address: ::1, Netmask: 128, Scope: Host
Network Device: wlan0
IPv6 - IP Address ::, Netmask 0, Scope Unknown
IPv4 - IP 0.0.0.0, Netmask 0.0.0.0

Help would be greatly appreciated! Thanks!

---

### Post by jmwilli25 on 2010-09-02
What is the output of ifconfig in your terminal? Also, what distribution are you using? To find out, in a terminal type, ```
lsb_version -a
```.

---

### Post by nchung1988 on 2010-09-02
Hey thanks for the quick response!

lsb_version -a resulted in command not found...

but i went to About Ubuntu and it says im using
ubuntu 10.04 LTS lucid lynx

---

### Post by jmwilli25 on 2010-09-02
type into a terminal
```
ifconfig
```
and post the output

---

### Post by jmwilli25 on 2010-09-02
Also, sorry. It was actually
[CODE}lsb_release -a[/CODE]

---

### Post by nchung1988 on 2010-09-02
eth0      Link encap:Ethernet  HWaddr 00:24:54:6f:21:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3888 (3.8 KB)  TX bytes:3888 (3.8 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:6e:e9:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Tracy177 on 2010-09-02
this card is inside your laptop so please paste what lspci say and dmesg

---

### Post by nchung1988 on 2010-09-02
nchung1988@nchung1988-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller

---

### Post by nchung1988 on 2010-09-02
DMESG (it gets cut off here...)

[    0.294614] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:07
[    0.294623] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.294635] pci 0000:00:1c.1:   MEM window: 0x40200000-0x403fffff
[    0.294646] pci 0000:00:1c.1:   PREFETCH window: 0x00000040400000-0x000000405fffff
[    0.294662] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:09
[    0.294671] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    0.294683] pci 0000:00:1c.2:   MEM window: 0xf0200000-0xf02fffff
[    0.294694] pci 0000:00:1c.2:   PREFETCH window: 0x00000040600000-0x000000407fffff
[    0.294709] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0b
[    0.294718] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.294730] pci 0000:00:1c.3:   MEM window: 0x40800000-0x409fffff
[    0.294741] pci 0000:00:1c.3:   PREFETCH window: 0x00000040a00000-0x00000040bfffff
[    0.294757] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:11
[    0.294763] pci 0000:00:1e.0:   IO window: disabled
[    0.294774] pci 0000:00:1e.0:   MEM window: disabled
[    0.294783] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.294824]   alloc irq_desc for 16 on node -1
[    0.294831]   alloc kstat_irqs on node -1
[    0.294847] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.294860] pci 0000:00:1c.0: setting latency timer to 64
[    0.294880] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.294890]   alloc irq_desc for 17 on node -1
[    0.294896]   alloc kstat_irqs on node -1
[    0.294908] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.294924] pci 0000:00:1c.1: setting latency timer to 64
[    0.294948]   alloc irq_desc for 18 on node -1
[    0.294954]   alloc kstat_irqs on node -1
[    0.294965] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.295006] pci 0000:00:1c.2: setting latency timer to 64
[    0.295025] pci 0000:00:1c.3: enabling device (0000 -> 0003)
[    0.295036]   alloc irq_desc for 19 on node -1
[    0.295042]   alloc kstat_irqs on node -1
[    0.295053] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.295065] pci 0000:00:1c.3: setting latency timer to 64
[    0.295082] pci 0000:00:1e.0: setting latency timer to 64
[    0.295093] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.295101] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.295110] pci_bus 0000:05: resource 0 io:  [0x3000-0x3fff]
[    0.295118] pci_bus 0000:05: resource 1 mem: [0xf0100000-0xf01fffff]
[    0.295126] pci_bus 0000:05: resource 2 pref mem [0x40000000-0x401fffff]
[    0.295135] pci_bus 0000:07: resource 0 io:  [0x4000-0x4fff]
[    0.295143] pci_bus 0000:07: resource 1 mem: [0x40200000-0x403fffff]
[    0.295151] pci_bus 0000:07: resource 2 pref mem [0x40400000-0x405fffff]
[    0.295160] pci_bus 0000:09: resource 0 io:  [0x2000-0x2fff]
[    0.295168] pci_bus 0000:09: resource 1 mem: [0xf0200000-0xf02fffff]
[    0.295176] pci_bus 0000:09: resource 2 pref mem [0x40600000-0x407fffff]
[    0.295184] pci_bus 0000:0b: resource 0 io:  [0x5000-0x5fff]
[    0.295192] pci_bus 0000:0b: resource 1 mem: [0x40800000-0x409fffff]
[    0.295201] pci_bus 0000:0b: resource 2 pref mem [0x40a00000-0x40bfffff]
[    0.295209] pci_bus 0000:11: resource 3 io:  [0x00-0xffff]
[    0.295217] pci_bus 0000:11: resource 4 mem: [0x000000-0xffffffff]
[    0.295306] NET: Registered protocol family 2
[    0.295575] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.296449] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.297561] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.298114] TCP: Hash tables configured (established 131072 bind 65536)
[    0.298126] TCP reno registered
[    0.298372] NET: Registered protocol family 1
[    0.298423] pci 0000:00:02.0: Boot video device
[    0.298627] Simple Boot Flag at 0x36 set to 0x1
[    0.299115] cpufreq-nforce2: No nForce2 chipset.
[    0.299208] Scanning for low memory corruption every 60 seconds
[    0.299494] audit: initializing netlink socket (disabled)
[    0.299519] type=2000 audit(1283427529.298:1): initialized
[    0.320303] highmem bounce pool size: 64 pages
[    0.320320] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.325281] VFS: Disk quotas dquot_6.5.2
[    0.325465] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.327404] fuse init (API version 7.13)
[    0.327683] msgmni has been set to 1716
[    0.328321] alg: No test for stdrng (krng)
[    0.328505] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.328515] io scheduler noop registered
[    0.328520] io scheduler anticipatory registered
[    0.328526] io scheduler deadline registered
[    0.328656] io scheduler cfq registered (default)
[    0.328983]   alloc irq_desc for 24 on node -1
[    0.328991]   alloc kstat_irqs on node -1
[    0.329014] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.329032] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.329306]   alloc irq_desc for 25 on node -1
[    0.329313]   alloc kstat_irqs on node -1
[    0.329332] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.329352] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.329613]   alloc irq_desc for 26 on node -1
[    0.329620]   alloc kstat_irqs on node -1
[    0.329637] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.329655] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.329913]   alloc irq_desc for 27 on node -1
[    0.329920]   alloc kstat_irqs on node -1
[    0.329937] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.329955] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.330194] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.330461] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.330480] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.330794] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.330813] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.331165] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.331184] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.331486] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.331505] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.331874] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.331892] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.332194] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.332212] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.332535] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.332554] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.332860] ACPI Error (dsfield-0143): [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.332878] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7010e88), AE_ALREADY_EXISTS
[    0.332985] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.333512] ACPI: AC Adapter [ADP1] (off-line)
[    0.333768] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.333865] ACPI: Lid Switch [LID0]
[    0.334000] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.334016] ACPI: Power Button [PWRB]
[    0.334147] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.334156] ACPI: Sleep Button [SLPB]
[    0.334286] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.334296] ACPI: Power Button [PWRF]
[    0.335892] ACPI: SSDT 3f5b9d48 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.337095] ACPI: SSDT 3f5b961e 006A5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.343395] Monitor-Mwait will be used to enter C-1 state
[    0.343514] processor LNXCPU:00: registered as cooling_device0
[    0.344538] ACPI: SSDT 3f5b9f4b 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.345359] ACPI: SSDT 3f5b9cc3 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.347256] processor LNXCPU:01: registered as cooling_device1
[    0.354217] thermal LNXTHERM:01: registered as thermal_zone0
[    0.354245] ACPI: Thermal Zone [TZ00] (54 C)
[    0.359000] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.362918] brd: module loaded
[    0.364493] loop: module loaded
[    0.364759] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.366104] Fixed MDIO Bus: probed
[    0.366221] PPP generic driver version 2.4.2
[    0.366345] tun: Universal TUN/TAP device driver, 1.6
[    0.366352] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.366614] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.366671]   alloc irq_desc for 23 on node -1
[    0.366678]   alloc kstat_irqs on node -1
[    0.366694] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.366729] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.366738] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.366836] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.366875] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.366896] ehci_hcd 0000:00:1d.7: debug port 1
[    0.370814] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.371016] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0604000
[    0.375227] isapnp: Scanning for PnP cards...
[    0.411135] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.411463] usb usb1: configuration #1 chosen from 1 choice
[    0.411548] hub 1-0:1.0: USB hub found
[    0.411570] hub 1-0:1.0: 8 ports detected
[    0.411745] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.411789] uhci_hcd: USB Universal Host Controller Interface driver
[    0.411865] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.411881] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.411889] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.411987] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.412029] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.412260] usb usb2: configuration #1 chosen from 1 choice
[    0.412340] hub 2-0:1.0: USB hub found
[    0.412362] hub 2-0:1.0: 2 ports detected
[    0.412467] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.412481] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.412490] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.412574] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.412630] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.412859] usb usb3: configuration #1 chosen from 1 choice
[    0.412932] hub 3-0:1.0: USB hub found
[    0.412949] hub 3-0:1.0: 2 ports detected
[    0.413052] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.413066] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.413074] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.413163] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.413215] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.413456] usb usb4: configuration #1 chosen from 1 choice
[    0.413530] hub 4-0:1.0: USB hub found
[    0.413548] hub 4-0:1.0: 2 ports detected
[    0.413656] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.413671] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.413679] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.413763] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.413815] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.414046] usb usb5: configuration #1 chosen from 1 choice
[    0.414139] hub 5-0:1.0: USB hub found
[    0.414156] hub 5-0:1.0: 2 ports detected
[    0.414373] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.416315] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.424061] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.424087] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.424180] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.424248] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.424314] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.424721] mice: PS/2 mouse device common for all mice
[    0.425234] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.425283] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.425584] device-mapper: uevent: version 1.0.3
[    0.458435] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.468737] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.515328] device-mapper: multipath: version 1.1.0 loaded
[    0.515338] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.555518] EISA: Probing bus 0 at eisa.0
[    0.555531] Cannot allocate resource for EISA slot 1
[    0.555539] Cannot allocate resource for EISA slot 2
[    0.555546] Cannot allocate resource for EISA slot 3
[    0.555552] Cannot allocate resource for EISA slot 4
[    0.555558] Cannot allocate resource for EISA slot 5
[    0.555578] EISA: Detected 0 cards.
[    0.598478] ACPI: Battery Slot [BAT1] (battery present)
[    0.611260] cpuidle: using governor ladder
[    0.611269] cpuidle: using governor menu
[    0.612499] TCP cubic registered
[    0.612971] NET: Registered protocol family 10
[    0.614161] lo: Disabled Privacy Extensions
[    0.615073] NET: Registered protocol family 17
[    0.616162] Using IPI No-Shortcut mode
[    0.616384] PM: Resume from disk failed.
[    0.616410] registered taskstats version 1
[    0.617230]   Magic number: 10:912:629
[    0.617290] pci_bus 0000:0b: hash matches
[    0.617369] rtc_cmos 00:04: setting system clock to 2010-09-02 11:38:50 UTC (1283427530)
[    0.617377] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.617382] EDD information not available.
[    0.661884] Freeing initrd memory: 7782k freed
[    0.729678] isapnp: No Plug & Play device found
[    0.729716] Freeing unused kernel memory: 660k freed
[    0.730323] Write protecting the kernel text: 4680k
[    0.730386] Write protecting the kernel read-only data: 1840k
[    0.764973] udev: starting version 151
[    0.836028] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    0.982531] usb 1-8: configuration #1 chosen from 1 choice
[    1.052372] sky2 driver version 1.25
[    1.052524] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.052586] sky2 0000:09:00.0: setting latency timer to 64
[    1.052710] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.053306]   alloc irq_desc for 28 on node -1
[    1.053314]   alloc kstat_irqs on node -1
[    1.053400] sky2 0000:09:00.0: irq 28 for MSI/MSI-X
[    1.058141] sky2 eth0: addr 00:24:54:6f:21:48
[    1.069889] ahci 0000:00:1f.2: version 3.0
[    1.069928] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.070006]   alloc irq_desc for 29 on node -1
[    1.070014]   alloc kstat_irqs on node -1
[    1.070038] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    1.070184] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.070196] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.070209] ahci 0000:00:1f.2: setting latency timer to 64
[    1.070771] scsi0 : ahci
[    1.071124] scsi1 : ahci
[    1.071337] scsi2 : ahci
[    1.071546] scsi3 : ahci
[    1.071974] ata1: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604500 irq 29
[    1.071988] ata2: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604580 irq 29
[    1.072043] ata3: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604600 irq 29
[    1.072054] ata4: SATA max UDMA/133 abar m1024@0xf0604400 port 0xf0604680 irq 29
[    1.224047] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.392148] ata2: SATA link down (SStatus 0 SControl 300)
[    1.392184] ata3: SATA link down (SStatus 0 SControl 300)
[    1.392216] ata4: SATA link down (SStatus 0 SControl 300)
[    1.392396] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.398495] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-06, max UDMA7
[    1.398505] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.398607] usb 4-2: configuration #1 chosen from 1 choice
[    1.404808] ata1.00: configured for UDMA/133
[    1.420293] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HI  HH10 PQ: 0 ANSI: 5
[    1.420686] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.420987] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.421135] sd 0:0:0:0: [sda] Write Protect is off
[    1.421142] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.421213] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.421582]  sda: sda1 sda2 < sda5 >
[    1.517283] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.878060] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   16.576665] Adding 2975736k swap on /dev/sda5.  Priority:-1 extents:1 across:2975736k 
[   16.600427] udev: starting version 151
[   16.863189] lp: driver loaded but no devices found
[   17.131299] Linux agpgart interface v0.103
[   17.259470] Bluetooth: Core ver 2.15
[   17.302957] NET: Registered protocol family 31
[   17.302965] Bluetooth: HCI device and connection manager initialized
[   17.302973] Bluetooth: HCI socket layer initialized
[   17.309574] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   17.309938] usbcore: registered new interface driver btusb
[   17.401885] cfg80211: Calling CRDA to update world regulatory domain
[   17.425994] agpgart-intel 0000:00:00.0: Intel IGD Chipset
[   17.426337] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   17.455107] Samsung-backlight: checking for SABI support.
[   17.455326] Samsung-backlight: SABI is supported (f5191)
[   17.456409] Linux video capture interface: v2.00
[   17.461320] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   17.480425] cfg80211: World regulatory domain updated:
[   17.480435]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.480445]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.480454]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.480463]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.480472]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.480480]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.548692] type=1505 audit(1283420347.430:2):  operation="profile_load" pid=591 name="/sbin/dhclient3"
[ 17.549489] type=1505 audit(1283420347.430:3): operation="profile_load" pid=591 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[ 17.549926] type=1505 audit(1283420347.430:4): operation="profile_load" pid=591 name="/usr/lib/connman/scripts/dhclient-script"
[   17.612262] [drm] Initialized drm 1.1.0 20060810
[   17.614340] uvcvideo: Found UVC 1.00 device WebCam SCB-0340N (0ac8:c33f)
[   17.616928] input: WebCam SCB-0340N as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input6
[   17.617486] usbcore: registered new interface driver uvcvideo
[   17.618095] USB Video Class driver (v0.1.0)
[   17.837048] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.837062] pci 0000:00:02.0: setting latency timer to 64
[   17.850533]   alloc irq_desc for 30 on node -1
[   17.850542]   alloc kstat_irqs on node -1
[   17.850560] pci 0000:00:02.0: irq 30 for MSI/MSI-X
[   17.850611] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.852164] ath9k 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.852189] ath9k 0000:05:00.0: setting latency timer to 64
[   17.901953] ath: EEPROM regdomain: 0x65
[   17.901963] ath: EEPROM indicates we should expect a direct regpair map
[   17.901973] ath: Country alpha2 being used: 00
[   17.901979] ath: Regpair used: 0x65
[   17.909400] vga16fb: initializing
[   17.909409] vga16fb: mapped to 0xc00a0000
[   17.909544] fb0: VGA16 VGA frame buffer device
[   18.073978] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.075857] Registered led device: ath9k-phy0::radio
[   18.075906] Registered led device: ath9k-phy0::assoc
[   18.075951] Registered led device: ath9k-phy0::tx
[   18.076026] Registered led device: ath9k-phy0::rx
[   18.076051] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf85a0000, irq=16
[   18.116199] Console: switching to colour frame buffer device 80x30
[   18.205031] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04771/0xa40000
[   18.247054] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   18.381143]   alloc irq_desc for 22 on node -1
[   18.381152]   alloc kstat_irqs on node -1
[   18.381168] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   18.381256] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   18.424933] type=1505 audit(1283420348.306:5):  operation="profile_load" pid=752 name="/usr/share/gdm/guest-session/Xsession"
[   18.440278] type=1505 audit(1283420348.322:6):  operation="profile_replace" pid=753 name="/sbin/dhclient3"
[ 18.441084] type=1505 audit(1283420348.322:7): operation="profile_replace" pid=753 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.449936] type=1505 audit(1283420348.330:8):  operation="profile_replace" pid=753 name="/usr/lib/connman/scripts/dhclient-script"
[   18.484519] type=1505 audit(1283420348.366:9):  operation="profile_load" pid=755 name="/usr/bin/evince"
[   18.518007] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.524637] type=1505 audit(1283420348.406:10):  operation="profile_load" pid=755 name="/usr/bin/evince-previewer"
[   18.545933] sky2 eth0: enabling interface
[   18.560697] type=1505 audit(1283420348.442:11):  operation="profile_load" pid=755 name="/usr/bin/evince-thumbnailer"
[   18.565726] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.583319] hda_codec: ALC269: BIOS auto-probing.
[   18.583916] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   18.933274] apm: BIOS not found.
[   19.697879] Bluetooth: L2CAP ver 2.14
[   19.697888] Bluetooth: L2CAP socket layer initialized
[   19.731932] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.731941] Bluetooth: BNEP filters: protocol multicast
[   19.756674] Bridge firewalling registered
[   19.804698] Bluetooth: SCO (Voice Link) ver 0.6
[   19.804707] Bluetooth: SCO socket layer initialized
[   19.877189] ppdev: user-space parallel port driver
[   19.973563] Bluetooth: RFCOMM TTY layer initialized
[   19.973657] Bluetooth: RFCOMM socket layer initialized
[   19.973665] Bluetooth: RFCOMM ver 1.11
[   20.345051] CPU0 attaching NULL sched-domain.
[   20.345065] CPU1 attaching NULL sched-domain.
[   20.373101] CPU0 attaching sched-domain:
[   20.373111]  domain 0: span 0-1 level SIBLING
[   20.373118]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   20.373132]   domain 1: span 0-1 level MC
[   20.373138]    groups: 0-1 (cpu_power = 1178)
[   20.373150] CPU1 attaching sched-domain:
[   20.373156]  domain 0: span 0-1 level SIBLING
[   20.373161]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   20.373174]   domain 1: span 0-1 level MC
[   20.373180]    groups: 0-1 (cpu_power = 1178)
[   25.500253] ACPI Error (psargs-0359): [\_SB_.VDRV] Namespace lookup failure, AE_NOT_FOUND
[ 25.500276] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.H_EC._Q51] (Node f7014570), AE_NOT_FOUND
[   25.521128] Easy slow down manager: checking for SABI support.
[   25.521305] Easy slow down manager: SABI is supported (f5191)
[   26.383071] CPU0 attaching NULL sched-domain.
[   26.383087] CPU1 attaching NULL sched-domain.
[   26.401158] CPU0 attaching sched-domain:
[   26.401169]  domain 0: span 0-1 level SIBLING
[   26.401178]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   26.401196]   domain 1: span 0-1 level MC
[   26.401204]    groups: 0-1 (cpu_power = 1178)
[   26.401220] CPU1 attaching sched-domain:
[   26.401228]  domain 0: span 0-1 level SIBLING
[   26.401236]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   26.401253]   domain 1: span 0-1 level MC
[   26.401260]    groups: 0-1 (cpu_power = 1178)
[  102.096069] usb 1-7: new high speed USB device using ehci_hcd and address 4
[  102.230605] usb 1-7: configuration #1 chosen from 1 choice
[  102.308577] Initializing USB Mass Storage driver...
[  102.309547] scsi4 : SCSI emulation for USB Mass Storage devices
[  102.310095] usb-storage: device found at 4
[  102.310106] usb-storage: waiting for device to settle before scanning
[  102.310162] usbcore: registered new interface driver usb-storage
[  102.312503] USB Mass Storage support registered.
[  107.308362] usb-storage: device scan complete
[  107.308942] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[  107.309923] scsi 4:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[  107.315109] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  107.326803] sd 4:0:0:0: [sdb] 8015502 512-byte logical blocks: (4.10 GB/3.82 GiB)
[  107.327440] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[  107.327451] Uniform CD-ROM driver Revision: 3.20
[  107.329785] sr 4:0:0:1: Attached scsi CD-ROM sr0
[  107.330276] sr 4:0:0:1: Attached scsi generic sg2 type 5
[  107.330580] sd 4:0:0:0: [sdb] Write Protect is off
[  107.330590] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  107.330598] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  107.335794] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  107.335811]  sdb: sdb1
[  107.341767] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  107.341782] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  108.202307] ISO 9660 Extensions: Microsoft Joliet Level 3
[  108.434925] ISOFS: changing to secondary root
[  157.238312] usb 1-7: USB disconnect, address 4
[  157.944105] scsi 4:0:0:1: rejecting I/O to dead device
[  247.632901] Monitor-Mwait will be used to enter C-2 state
[  247.632932] Marking TSC unstable due to TSC halts in idle
[  247.638191] Switching to clocksource hpet
[  845.616110] usb 1-7: new high speed USB device using ehci_hcd and address 5
[  845.750867] usb 1-7: configuration #1 chosen from 1 choice
[  845.751821] scsi5 : SCSI emulation for USB Mass Storage devices
[  845.752660] usb-storage: device found at 5
[  845.752672] usb-storage: waiting for device to settle before scanning
[  850.753372] usb-storage: device scan complete
[  850.753953] scsi 5:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[  850.754556] scsi 5:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[  850.761932] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  850.769651] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[  850.770297] sr 5:0:0:1: Attached scsi CD-ROM sr0
[  850.770642] sr 5:0:0:1: Attached scsi generic sg2 type 5
[  850.774742] sd 5:0:0:0: [sdb] 8015502 512-byte logical blocks: (4.10 GB/3.82 GiB)
[  850.779081] sd 5:0:0:0: [sdb] Write Protect is off
[  850.779094] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  850.779102] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  850.783014] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  850.783030]  sdb: sdb1
[  850.791632] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  850.791644] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  851.167859] ISO 9660 Extensions: Microsoft Joliet Level 3
[  851.170831] ISOFS: changing to secondary root

---

### Post by Tracy177 on 2010-09-02
we know now you got atheros and atheros is one of the best chips 

first at all there is a button swich on and off network press it and try to connect to network if u cant connect than press it again and aagain try to connect if it doesnt work follow this steps:


open this web 
[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

and download from the bottom latest driver 

it is called 

[SIZE=1][compat-wireless-2010-09-01.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-09-01.tar.bz2")[/SIZE][SIZE=1]2010-Sep-01 21:03:21[/SIZE][SIZE=1]2.5M[/SIZE][SIZE=1]application/octet-stream[/SIZE]
u need just one cuz on that page is many drivers theyre all the same there is many cuz this one driver is updated every single day u need just one the latest one from the bottom

after you download it 

extract it to whatever u want to

and cd to that directory 

than make
and sudo make install

it will take a while cuz in this single driver u will get support for very many wifi and bluetooth devices

than restart you laptop 

and the new driver will be installed

after u rebooted try to connect to internet it should work staright away

but if it doesnt again try to press the wireless button switch in your laptop 

and than try it again if it doesnt work come back

in the future if u would like to update your driver just download the newer one and do the same as above make and sudo make install

---

### Post by nchung1988 on 2010-09-02
thank you so much!!! i will try it but...

a) how do i do cd? say i extract it on the desktop, what are the exact commands i need to do this? i am really sorry but i have never done this before so i dont know how to install things yet.... and what is the command for sudo make install?

b) if i can see wireless networks in wicd shouldnt i already have the driver installed?

---

### Post by nchung1988 on 2010-09-02
i installed everything and i still get a cannot get ip address.....

---

### Post by Tracy177 on 2010-09-02
> **nchung1988 said:**
> thank you so much!!! i will try it but...

a) how do i do cd? say i extract it on the desktop, what are the exact commands i need to do this? i am really sorry but i have never done this before so i dont know how to install things yet.... and what is the command for sudo make install?

b) if i can see wireless networks in wicd shouldnt i already have the driver installed?

open the web click on the file it will show two options click save.

in 2sec it will be downloaded to your downloads

look on the top of your screen u see your panel there are places click on it open downloads 

there is the file u downloaded right click on it scroll down and extract it

after is extracted open terminal and type cd /home/name of your system/Downloads/name of the file you extracted 

and after that just type make and after it finished type sudo make install

if u have still probs come back


b) if i can see wireless networks in wicd shouldnt i already have the driver installed?[/QUOTE]
sometimes u maight have bad driver or your card use bad driver did you try to press the network button and try to connect to internet again?

---

### Post by Tracy177 on 2010-09-02
> **nchung1988 said:**
> i installed everything and i still get a cannot get ip address.....

did u install the compat wireless already ?

 do u see networks in wicd ? 

i dont believe u cant get connected cuz i have ath too and never had even little problem with it 

do you use wep or wpa ?

can u try without encryption?

---

### Post by nchung1988 on 2010-09-02
i installed it and still cant connect...

before i installed it i could still see networks but everytime i pressed connect it would say cannot obtain ip address

i am still getting the same error after i installed it...

and i dont know if there is a network button on the laptop... i looked on the keyboard and i dont see anything so i dunno...

---

### Post by Tracy177 on 2010-09-02
> **nchung1988 said:**
> i installed it and still cant connect...

before i installed it i could still see networks but everytime i pressed connect it would say cannot obtain ip address

i am still getting the same error after i installed it...

and i dont know if there is a network button on the laptop... i looked on the keyboard and i dont see anything so i dunno...


if u see networks it mean your wifi is switched on thats funny for me cuz my wifi does work and i have ath like u and compat like u.

what about windows ? do u have windows or any other OS ? can u connect to the internet over there ?

if so when u boot ubuntu and u try to connect to the internet do u use encryption? wep or wpa? can u try to connect without encryption? or direct connect without wifi?

---

### Post by nchung1988 on 2010-09-02
i only have ubuntu installed....

i am not sure about what kind of wireless it is but when i use ehternet, i immediately get online to some homepage where i have to enter in my username and password...

for some reason my wireless can detect all the networks and it says connected but then it says cannot get ip address!!!

---

### Post by nchung1988 on 2010-09-02
still unable to connect... any help would be great thanks guys!

---

### Post by nchung1988 on 2010-09-03
bump???

---

### Post by nchung1988 on 2010-09-06
bump

---

### Post by Mze on 2010-09-06
install linux-backports-modules-wireless-lucid-generic

see if that helps. Seems to have helped users from way back in Jaunty

---

### Post by Mze on 2010-09-06
here is a [thread]("http://ubuntuforums.org/showthread.php?t=1476231") you might want to check out..

---

### Post by nchung1988 on 2010-09-06
ok thanks ill try that out.... but its wierd because i can see all the wireless networks! where is this error coming from?

---

### Post by nchung1988 on 2010-09-06
i typed install linux-backports....

it said missing destination file operand?

---

### Post by Mze on 2010-09-06
you need **sudo** to install anything in Ubuntu

---

### Post by nchung1988 on 2010-09-06
i typed in 
			 		   		 		 		sudo install linux-backports-modules-wireless-lucid-generic

i still ge tthe same error,
missing desintation file operand after linux-backports-modules-wireless-lucid-generic

---

### Post by Mze on 2010-09-06
sudo apt-get install linux-backports-modules-wireless-lucid-generic

or you can use the Synaptic package manager found under System>>Administration>>Synaptic package manager and paste "linux-backports-modules-wireless-lucid-generic" into the search window. Mark it for installation and install.

When using the Live CD, were you able to connect to any wireless network?

---

### Post by nchung1988 on 2010-09-06
no i wasnt able to connect then... but i was able to see wireless networks

so i installed the package but i still get a connection failed: unable to obtain ip addresss 
error.....

?!?!?!?

---

### Post by Mze on 2010-09-06
are these WEP or WPA-2 networks you are trying to connect too?

---

### Post by nchung1988 on 2010-09-06
im not sure.... but it should connect automatically and then send me to a login page set by my university

everyone else on campus can log in and has no problem...

---

### Post by nchung1988 on 2010-09-06
right now i see two networks at my home:

WPA2 and unsecured

neither work

---

### Post by Mze on 2010-09-06
can you run sudo iwlist scan and post output?

---

### Post by nchung1988 on 2010-09-06
yes sir:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:97:25:46
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c762712c14
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 32080C1218602430486C
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
          Cell 02 - Address: 00:22:3F:C0:88:AA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Spaceport 54"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028b74da183
                    Extra: Last beacon: 384ms ago
                    IE: Unknown: 000C5370616365706F7274203534
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:25:4B:00:27:19
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Gile001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009a896b7177
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 000747696C65303031
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706534520010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120

pan0      Interface doesn't support scanning.

---

### Post by nchung1988 on 2010-09-06
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:97:25:46
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c762712c14
                    Extra: Last beacon: 556ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 32080C1218602430486C
                    IE: Unknown: CC0700CC020000018A
                    IE: Unknown: CC0700CC0300000100
          Cell 02 - Address: 00:22:3F:C0:88:AA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Spaceport 54"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028b74da183
                    Extra: Last beacon: 384ms ago
                    IE: Unknown: 000C5370616365706F7274203534
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:25:4B:00:27:19
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Gile001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009a896b7177
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 000747696C65303031
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 0706534520010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A2C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C0217FFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001100000000000000000000000000000000000000
                    IE: Unknown: DD07000393016B0120

pan0      Interface doesn't support scanning.

---

### Post by Mze on 2010-09-06
If you are unable to connect to the "dlink" network which is unencrypted, unable to come up with any solution unfortunately.

If you have a fast connection try a Live CD of another distro, e.g.  Linux Mint and see if you are able to connect.

---

### Post by nchung1988 on 2010-09-06
ok....

[http://www.sammynetbook.com/forum/threads/12900-Ubuntu-9.10-on-N150](http://www.sammynetbook.com/forum/threads/12900-Ubuntu-9.10-on-N150)

is it possible that the newest ubuntu isnt compatible with N150? this person seemed to have it working with 9.10

also, should i use ndiswrapper maybe?

---

### Post by Mze on 2010-09-06
Others have had your card work with the newer Ubuntu version from what I read online.

Also check in synaptic if **wpa-supplicant** is installed

---

### Post by nchung1988 on 2010-09-06
yeah it is man.... you gotta help me fix this problem bra! im losing my sanity

---

### Post by Mze on 2010-09-06
this [thread]("http://ubuntuforums.org/showthread.php?t=1309072") suggests using Madwifi driver for 9.10, there are others who have applied it to Lucid.

---

### Post by nchung1988 on 2010-09-06
ok this is really wierd but my ubuntu just crashed by itself wtf??? i am running 10.0.4 desktop on N150....

is it possible that if i reinstall everything will be ok?

---

### Post by Mze on 2010-09-06
If a restart doesn't help, you might want to go with that option.

But like I wrote earlier give the Linux Mint Live CD a try too..

---

### Post by mathia on 2010-09-16
Hi,
please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8040 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by slingshotsuicide on 2010-11-13
> **Mze said:**
> here is a [thread]("http://ubuntuforums.org/showthread.php?t=1476231") you might want to check out..

Sorry, should have come back here, but posted what worked for me on this thread. (after the point where they had solved their PBKAC)

---

