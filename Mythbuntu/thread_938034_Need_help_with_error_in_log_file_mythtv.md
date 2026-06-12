---
title: "Need help with error in log file mythtv"
date: 2008-10-04
forum: Mythbuntu
---

### Post by sdowney717 on 2008-10-04
I have not been able to start mythtv as I assume my capture card is not correctly configured in mythtv.

It is simply a video4linux capture card hooked to an external VCR tuner.
(avc-2010)

```

scott@scott-desktop:~$ mythtv -geometry 640x480
2008-10-04 13:21:46.097 Using runtime prefix = /usr
2008-10-04 13:21:46.109 XScreenSaver support enabled
2008-10-04 13:21:46.112 DPMS is active.
2008-10-04 13:21:46.113 Empty LocalHostName.
2008-10-04 13:21:46.113 Using localhost value of scott-desktop
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
2008-10-04 13:21:46.123 New DB connection, total: 1
2008-10-04 13:21:46.140 Connected to database 'mythconverg' at host: localhost
2008-10-04 13:21:46.141 Closing DB connection named 'DBManager0'
2008-10-04 13:21:46.143 Primary screen 0.
2008-10-04 13:21:46.144 Connected to database 'mythconverg' at host: localhost
2008-10-04 13:21:46.145 Using screen 0, 1280x1024 at 0,0
2008-10-04 13:21:46.155 Overriding GUI, width=640, height=480 at 0,0
2008-10-04 13:21:46.168 No theme dir: /home/scott/.mythtv/themes/G.A.N.T
2008-10-04 13:21:46.351 max_width: 1792 max_height: 1344
2008-10-04 13:21:46.354 No theme dir: /home/scott/.mythtv/themes/G.A.N.T
2008-10-04 13:21:46.355 Switching to square mode (G.A.N.T)
2008-10-04 13:21:46.402 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2008-10-04 13:21:46.403 lirc_init failed for mythtv, see preceding messages
2008-10-04 13:21:46.404 JoystickMenuClient Error: Joystick disabled - Failed to read /home/scott/.mythtv/joystickmenurc
2008-10-04 13:21:46.965 New DB connection, total: 2
2008-10-04 13:21:46.966 Connected to database 'mythconverg' at host: localhost
2008-10-04 13:21:47.036 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-10-04 13:21:47.051 Using protocol version 40
2008-10-04 13:21:47.063 TV: Attempting to change from None to WatchingLiveTV
2008-10-04 13:21:47.065 Using protocol version 40
2008-10-04 13:21:48.336 LiveTVChain(live-scott-desktop-2008-10-04T13:21:47): ReloadAll(): Added new recording
2008-10-04 13:21:48.345 RingBuf(/var/lib/mythtv/recordings/4294967295_20081004132147.nuv): OpenFile(/var/lib/mythtv/recordings/4294967295_20081004132147.nuv, 12)
2008-10-04 13:21:48.354 RingBuf(/var/lib/mythtv/recordings/4294967295_20081004132147.nuv): CalcReadAheadThresh(141790592 KB)
			 -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2008-10-04 13:21:48.401 DPMS Deactivated 
2008-10-04 13:22:28.357 TV Error: StartRecorder() -- timed out waiting for recorder to start
2008-10-04 13:22:28.357 TV Error: LiveTV not successfully started
2008-10-04 13:22:28.487 TV: Deleting TV Chain in destructor
2008-10-04 13:22:28.501 DPMS Reactivated.
Mutex destroy failure: Device or resource busy
scott@scott-desktop:~$ 



```

---

### Post by DemonBob on 2008-10-04
please post the output from 

```
dmesg
```
```
lspic -vvn
```
```
lsusb -vvn
```

Also open and post the out of these log files.

/var/log/mythtv/mythfrontend.log
/var/log/mythtv/mythbackend.log

---

### Post by sdowney717 on 2008-10-04
this is not the entire lspci list as it runs off the terminal 

I gather this is the relevant info for my capture card

[   25.676870] Linux video capture interface: v2.00
[   25.800348] ivtv:  Start initialization, version 1.4.0
[   25.800540] ivtv0: Initializing card #0
[   25.800552] ivtv0: Autodetected Adaptec VideOh! AVC-2010 card (cx23416 based)
[   25.817388] ivtv 0000:05:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.987126] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   26.353665] cs53l32a 0-0011: chip found @ 0x22 (ivtv i2c driver #0)
[   26.385860] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   26.386127] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   26.386209] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   26.386280] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   26.386285] ivtv0: Initialized card #0: Adaptec VideOh! AVC-2010
[   26.386331] ivtv:  End initialization



```

  0.004000]       .init : 0xc04c8000 - 0xc0533000   ( 428 kB)
[    0.004000]       .data : 0xc0399388 - 0xc04c0640   (1180 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0399388   (2660 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 4784.55 BogoMIPS (lpj=9569104)
[    0.004057] Security Framework initialized
[    0.004076] SELinux:  Disabled at boot.
[    0.004114] AppArmor: AppArmor initialized <NULL>
[    0.004134] Mount-cache hash table entries: 512
[    0.004445] Initializing cgroup subsys ns
[    0.004454] Initializing cgroup subsys cpuacct
[    0.004458] Initializing cgroup subsys memory
[    0.004486] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004492] CPU: L2 cache: 512K
[    0.004496] CPU: Hyper-Threading is disabled
[    0.004523] Checking 'hlt' instruction... OK.
[    0.020666] SMP alternatives: switching to UP code
[    0.030871] Freeing SMP alternatives: 12k freed
[    0.030878] ACPI: Core revision 20080609
[    0.030950] ACPI: Checking initramfs for custom DSDT
[    0.423165] ENABLING IO-APIC IRQs
[    0.423361] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.463057] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[    0.464029] Brought up 1 CPUs
[    0.464029] Total of 1 processors activated (4784.55 BogoMIPS).
[    0.464029] CPU0 attaching sched-domain:
[    0.464029]  domain 0: span 0 level CPU
[    0.464029]   groups: 0
[    0.464029] net_namespace: 840 bytes
[    0.464029] Booting paravirtualized kernel on bare hardware
[    0.464029] Time: 22:53:05  Date: 10/02/08
[    0.464029] NET: Registered protocol family 16
[    0.464029] EISA bus registered
[    0.464029] ACPI: bus type pci registered
[    0.464029] PCI: PCI BIOS revision 2.20 entry at 0xeca48, last bus=5
[    0.464029] PCI: Using configuration type 1 for base access
[    0.465170] ACPI: EC: Look up EC in DSDT
[    0.470991] ACPI: Interpreter enabled
[    0.470998] ACPI: (supports S0 S1 S3 S4 S5)
[    0.471034] ACPI: Using IOAPIC for interrupt routing
[    0.482119] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.482273] PCI: 0000:00:00.0 reg 10 32bit mmio: [dc000000, dfffffff]
[    0.482449] PCI: 0000:00:1d.0 reg 20 io port: [3440, 345f]
[    0.482517] PCI: 0000:00:1d.1 reg 20 io port: [3460, 347f]
[    0.482583] PCI: 0000:00:1d.2 reg 20 io port: [3480, 349f]
[    0.482658] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f0a00000, f0a003ff]
[    0.482725] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.482734] pci 0000:00:1d.7: PME# disabled
[    0.482784] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.482787] * this clock source is slow. If you are sure your timer does not have
[    0.482791] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.482843] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.482855] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[    0.482863] pci 0000:00:1f.0: quirk: region fa00-fa3f claimed by ICH4 GPIO
[    0.482891] PCI: 0000:00:1f.1 reg 10 io port: [34d0, 34d7]
[    0.482904] PCI: 0000:00:1f.1 reg 14 io port: [34e0, 34e3]
[    0.482915] PCI: 0000:00:1f.1 reg 18 io port: [34d8, 34df]
[    0.482927] PCI: 0000:00:1f.1 reg 1c io port: [34e4, 34e7]
[    0.482938] PCI: 0000:00:1f.1 reg 20 io port: [34c0, 34cf]
[    0.482949] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.483007] PCI: 0000:00:1f.5 reg 10 io port: [3000, 30ff]
[    0.483019] PCI: 0000:00:1f.5 reg 14 io port: [3400, 343f]
[    0.483030] PCI: 0000:00:1f.5 reg 18 32bit mmio: [f0a00400, f0a005ff]
[    0.483042] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [f0a00600, f0a006ff]
[    0.483079] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.483086] pci 0000:00:1f.5: PME# disabled
[    0.483151] PCI: 0000:01:00.0 reg 10 32bit mmio: [e0000000, efffffff]
[    0.483161] PCI: 0000:01:00.0 reg 14 io port: [2000, 20ff]
[    0.483171] PCI: 0000:01:00.0 reg 18 32bit mmio: [f0400000, f040ffff]
[    0.483198] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.483224] pci 0000:01:00.0: supports D1
[    0.483227] pci 0000:01:00.0: supports D2
[    0.483262] PCI: 0000:01:00.1 reg 10 32bit mmio: [f0410000, f041ffff]
[    0.483314] pci 0000:01:00.1: supports D1
[    0.483318] pci 0000:01:00.1: supports D2
[    0.483369] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.483377] PCI: bridge 0000:00:01.0 32bit mmio: [f0200000, f04fffff]
[    0.483386] PCI: bridge 0000:00:01.0 32bit mmio pref: [e0000000, f01fffff]
[    0.483442] PCI: 0000:05:08.0 reg 10 32bit mmio: [f0500000, f0500fff]
[    0.483452] PCI: 0000:05:08.0 reg 14 io port: [1000, 103f]
[    0.483497] pci 0000:05:08.0: supports D1
[    0.483501] pci 0000:05:08.0: supports D2
[    0.483505] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.483513] pci 0000:05:08.0: PME# disabled
[    0.483550] PCI: 0000:05:0a.0 reg 10 32bit mmio: [f4000000, f7ffffff]
[    0.483636] pci 0000:00:1e.0: transparent bridge
[    0.483644] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.483653] PCI: bridge 0000:00:1e.0 32bit mmio: [f0500000, f07fffff]
[    0.483662] PCI: bridge 0000:00:1e.0 32bit mmio pref: [f4000000, f81fffff]
[    0.483682] bus 00 -> node 0
[    0.483697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.484307] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.498331] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.498571] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.498805] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.499047] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.499299] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.499551] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.499801] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.500078] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.500494] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.500577] pnp: PnP ACPI init
[    0.500599] ACPI: bus type pnp registered
[    0.507322] pnp 00:0d: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.507331] pnp 00:0d: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.507338] pnp 00:0d: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.507345] pnp 00:0d: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.508831] pnp: PnP ACPI: found 15 devices
[    0.508839] ACPI: ACPI bus type pnp unregistered
[    0.508847] PnPBIOS: Disabled by ACPI PNP
[    0.509541] PCI: Using ACPI for IRQ routing
[    0.509765] NET: Registered protocol family 8
[    0.509765] NET: Registered protocol family 20
[    0.509765] NetLabel: Initializing
[    0.509765] NetLabel:  domain hash size = 128
[    0.509765] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.509765] NetLabel:  unlabeled traffic allowed by default
[    0.509765] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.509765]    actual entries 65620
[    0.509765] AppArmor: AppArmor Filesystem Enabled 
[    0.509765] ACPI: RTC can wake from S4
[    0.509765] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.509765] system 00:0d: ioport range 0x400-0x41f has been reserved
[    0.509765] system 00:0d: ioport range 0x420-0x43f has been reserved
[    0.509765] system 00:0d: ioport range 0x440-0x45f has been reserved
[    0.509765] system 00:0d: ioport range 0x460-0x47f has been reserved
[    0.509765] system 00:0d: ioport range 0xfa00-0xfa3f has been reserved
[    0.509765] system 00:0d: ioport range 0xfc00-0xfc7f has been reserved
[    0.509765] system 00:0d: ioport range 0xfc80-0xfcff has been reserved
[    0.509765] system 00:0d: ioport range 0xfe00-0xfe7f has been reserved
[    0.509765] system 00:0d: ioport range 0xfe80-0xfeff has been reserved
[    0.509765] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.509765] system 00:0e: iomem range 0x100000-0x3fffffff could not be reserved
[    0.509765] system 00:0e: iomem range 0x40000000-0x400fffff has been reserved
[    0.509765] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.509765] system 00:0e: iomem range 0xfec01000-0xffffffff could not be reserved
[    0.509765] system 00:0e: iomem range 0xd0800-0xdffff has been reserved
[    0.547020] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.547028] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.547037] pci 0000:00:01.0:   MEM window: 0xf0200000-0xf04fffff
[    0.547045] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000f01fffff
[    0.547056] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.547063] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.547072] pci 0000:00:1e.0:   MEM window: 0xf0500000-0xf07fffff
[    0.547080] pci 0000:00:1e.0:   PREFETCH window: 0x000000f4000000-0x000000f81fffff
[    0.547109] pci 0000:00:1e.0: setting latency timer to 64
[    0.547118] bus: 00 index 0 io port: [0, ffff]
[    0.547123] bus: 00 index 1 mmio: [0, ffffffff]
[    0.547129] bus: 01 index 0 io port: [2000, 2fff]
[    0.547134] bus: 01 index 1 mmio: [f0200000, f04fffff]
[    0.547140] bus: 01 index 2 mmio: [e0000000, f01fffff]
[    0.547145] bus: 01 index 3 mmio: [0, 0]
[    0.547150] bus: 05 index 0 io port: [1000, 1fff]
[    0.547155] bus: 05 index 1 mmio: [f0500000, f07fffff]
[    0.547161] bus: 05 index 2 mmio: [f4000000, f81fffff]
[    0.547166] bus: 05 index 3 io port: [0, ffff]
[    0.547171] bus: 05 index 4 mmio: [0, ffffffff]
[    0.547195] NET: Registered protocol family 2
[    0.547446] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.548075] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.549471] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.550418] TCP: Hash tables configured (established 131072 bind 65536)
[    0.550433] TCP reno registered
[    0.550757] NET: Registered protocol family 1
[    0.551025] checking if image is initramfs... it is
[    1.048086] Switched to high resolution mode on CPU 0
[    1.393474] Freeing initrd memory: 7945k freed
[    1.394854] audit: initializing netlink socket (disabled)
[    1.394888] type=2000 audit(1222987985.392:1): initialized
[    1.401794] highmem bounce pool size: 64 pages
[    1.401812] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.407248] VFS: Disk quotas dquot_6.5.1
[    1.407465] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.407738] msgmni has been set to 1761
[    1.408086] io scheduler noop registered
[    1.408094] io scheduler anticipatory registered
[    1.408101] io scheduler deadline registered
[    1.408141] io scheduler cfq registered (default)
[    1.408255] pci 0000:01:00.0: Boot video device
[    1.408275] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    1.409534] isapnp: Scanning for PnP cards...
[    1.763532] isapnp: No Plug & Play device found
[    1.813547] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.813717] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.813988] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.815056] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.815574] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.818091] brd: module loaded
[    1.818202] input: Macintosh mouse button emulation as /class/input/input0
[    1.818398] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    1.821390] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.821401] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.822127] mice: PS/2 mouse device common for all mice
[    1.822362] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.822391] rtc0: alarms up to one month, y3k
[    1.822591] EISA: Probing bus 0 at eisa.0
[    1.822606] Cannot allocate resource for EISA slot 1
[    1.822611] Cannot allocate resource for EISA slot 2
[    1.822616] Cannot allocate resource for EISA slot 3
[    1.822641] EISA: Detected 0 cards.
[    1.822649] cpuidle: using governor ladder
[    1.822654] cpuidle: using governor menu
[    1.823182] aufs 20080609
[    1.823847] Using IPI No-Shortcut mode
[    1.824262] registered taskstats version 1
[    1.824405]   Magic number: 12:846:905
[    1.824489] tty ptyz1: hash matches
[    1.824593] rtc_cmos 00:03: setting system clock to 2008-10-02 22:53:07 UTC (1222987987)
[    1.824598] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.824603] EDD information not available.
[    1.825286] Freeing unused kernel memory: 428k freed
[    1.825330] Write protecting the kernel read-only data: 952k
[    1.843287] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.069569] fuse init (API version 7.9)
[    2.200651] uvesafb: failed to execute /sbin/v86d
[    2.200659] uvesafb: make sure that the v86d helper is installed and executable
[    2.200664] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    2.200668] uvesafb: vbe_init() failed with -22
[    2.200677] uvesafb: probe of uvesafb.0 failed with error -22
[    2.267842] processor ACPI0007:00: registered as cooling_device0
[    2.267849] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.786047] usbcore: registered new interface driver usbfs
[    3.786086] usbcore: registered new interface driver hub
[    3.786160] usbcore: registered new device driver usb
[    3.792253] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    3.792273] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.792279] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.792392] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.796337] ehci_hcd 0000:00:1d.7: debug port 1
[    3.796346] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.796363] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0a00000
[    3.811901] USB Universal Host Controller Interface driver v3.0
[    3.828234] No dock devices found.
[    3.847387] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.847728] usb usb1: configuration #1 chosen from 1 choice
[    3.847776] hub 1-0:1.0: USB hub found
[    3.847797] hub 1-0:1.0: 6 ports detected
[    3.922163] SCSI subsystem initialized
[    3.925481] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    3.925486] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.975433] libata version 3.00 loaded.
[    4.052435] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.052449] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.052454] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.052492] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.052530] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00003440
[    4.052696] usb usb2: configuration #1 chosen from 1 choice
[    4.052736] hub 2-0:1.0: USB hub found
[    4.052751] hub 2-0:1.0: 2 ports detected
[    4.156405] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.156419] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.156424] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.156465] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    4.156501] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003460
[    4.156666] usb usb3: configuration #1 chosen from 1 choice
[    4.156707] hub 3-0:1.0: USB hub found
[    4.156722] hub 3-0:1.0: 2 ports detected
[    4.366455] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.366470] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.366475] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.366544] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    4.366583] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003480
[    4.366839] usb usb4: configuration #1 chosen from 1 choice
[    4.366880] hub 4-0:1.0: USB hub found
[    4.366896] hub 4-0:1.0: 2 ports detected
[    4.468487] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.555054] e100 0000:05:08.0: PME# disabled
[    4.555636] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    4.559439] e100: eth0: e100_probe: addr 0xf0500000, irq 20, MAC addr 00:0b:cd:62:97:c2
[    4.565066] ata_piix 0000:00:1f.1: version 2.12
[    4.565085] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    4.565096] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.565178] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.565704] scsi0 : ata_piix
[    4.566185] scsi1 : ata_piix
[    4.566440] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x34c0 irq 14
[    4.566445] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x34c8 irq 15
[    4.732683] usb 3-2: configuration #1 chosen from 1 choice
[    4.761176] usbcore: registered new interface driver hiddev
[    4.763937] ata1.00: ATA-7: MAXTOR STM3200820A, 3.AAE, max UDMA/100
[    4.763942] ata1.00: 390721968 sectors, multi 16: LBA48 
[    4.773895] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    4.774489] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-2
[    4.774519] usbcore: registered new interface driver usbhid
[    4.774524] usbhid: v2.6:USB HID core driver
[    4.838750] ata1.00: configured for UDMA/100
[    5.016313] ata2.00: ATAPI: LITE-ON DVDRW SHW-1635S, YV6J, max UDMA/66
[    5.048241] ata2.00: configured for UDMA/66
[    5.048477] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM320082 3.AA PQ: 0 ANSI: 5
[    5.049529] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YV6J PQ: 0 ANSI: 5
[    5.074439] Driver 'sd' needs updating - please use bus_type methods
[    5.074609] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.074642] sd 0:0:0:0: [sda] Write Protect is off
[    5.074646] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.074695] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.074811] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[    5.074839] sd 0:0:0:0: [sda] Write Protect is off
[    5.074842] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.074891] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.074898]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    5.094495]  sda1 sda2 sda3 < sda5 >
[    5.122294] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.131411] sr0: scsi3-mmc drive: 94x/94x writer cd/rw xa/form2 cdda tray
[    5.131421] Uniform CD-ROM driver Revision: 3.20
[    5.131559] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.138517] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.138571] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    8.435093] PM: Starting manual resume from disk
[    8.435098] PM: Resume from partition 8:5
[    8.435100] PM: Checking hibernation image.
[    8.435336] PM: Resume from disk failed.
[    8.500342] kjournald starting.  Commit interval 5 seconds
[    8.500366] EXT3-fs: mounted filesystem with ordered data mode.
[   20.475096] udevd version 124 started
[   23.072746] Linux agpgart interface v0.103
[   23.156405] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.229379] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   23.233528] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xdc000000
[   23.328081] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.420394] intel_rng: Firmware space is locked read-only. If you can't or
[   23.420396] intel_rng: don't want to disable this in firmware setup, and if
[   23.420398] intel_rng: you are certain that your system has a functional
[   23.420400] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   23.502904] input: Power Button (FF) as /class/input/input3
[   23.531028] ACPI: Power Button (FF) [PWRF]
[   23.531172] input: Power Button (CM) as /class/input/input4
[   23.560294] ACPI: Power Button (CM) [PBTN]
[   23.612498] iTCO_vendor_support: vendor-support=0
[   23.671874] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   23.672040] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0xf860)
[   23.672237] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.556293] parport_pc 00:07: reported by Plug and Play ACPI
[   24.556353] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   25.676870] Linux video capture interface: v2.00
[   25.800348] ivtv:  Start initialization, version 1.4.0
[   25.800540] ivtv0: Initializing card #0
[   25.800552] ivtv0: Autodetected Adaptec VideOh! AVC-2010 card (cx23416 based)
[   25.817388] ivtv 0000:05:0a.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   25.987126] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   26.353665] cs53l32a 0-0011: chip found @ 0x22 (ivtv i2c driver #0)
[   26.385860] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   26.386127] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   26.386209] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   26.386280] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   26.386285] ivtv0: Initialized card #0: Adaptec VideOh! AVC-2010
[   26.386331] ivtv:  End initialization
[   26.693905] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   26.693940] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   27.064014] intel8x0_measure_ac97_clock: measured 54906 usecs
[   27.064019] intel8x0: clocking to 48000
[   28.128503] lp0: using parport0 (interrupt-driven).
[   28.335650] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   28.928198] EXT3 FS on sda2, internal journal
[   31.474250] type=1505 audit(1223002416.698:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3970
[   31.696828] type=1505 audit(1223002416.922:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3975
[   31.697252] type=1505 audit(1223002416.922:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3975
[   31.758002] type=1505 audit(1223002416.982:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=3979
[   31.826646] type=1505 audit(1223002417.050:6): operation="profile_load" name="/usr/sbin/named" name2="default" pid=3983
[   31.985066] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.448218] RPC: Registered udp transport module.
[   32.448223] RPC: Registered tcp transport module.
[   33.472217] ACPI: WMI: Mapper loaded
[   39.762728] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   40.625953] type=1503 audit(1223002425.850:7): operation="capable" name="sys_resource" pid=4874 profile="/usr/sbin/named"
[   44.378573] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   44.378584] apm: overridden by ACPI.
[   45.106197] ppdev: user-space parallel port driver
[   50.608244] NET: Registered protocol family 10
[   50.611020] lo: Disabled Privacy Extensions
[   53.642324] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   54.433943] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   54.442883] NFSD: starting 90-second grace period
[   55.172046] NET: Registered protocol family 17
[   76.578376] pads[6259]: segfault at 25 ip 0804d888 sp bfd58570 error 4 in pads[8048000+b000]
[   80.512030] firmware: requesting v4l-cx2341x-enc.fw
[   80.626210] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   80.824148] ivtv0: Encoder revision: 0x02060039
[   87.331780] Bluetooth: Core ver 2.13
[   87.335974] NET: Registered protocol family 31
[   87.335982] Bluetooth: HCI device and connection manager initialized
[   87.335992] Bluetooth: HCI socket layer initialized
[   87.425188] Bluetooth: L2CAP ver 2.11
[   87.425196] Bluetooth: L2CAP socket layer initialized
[   87.479984] Bluetooth: RFCOMM socket layer initialized
[   87.480963] Bluetooth: RFCOMM TTY layer initialized
[   87.480977] Bluetooth: RFCOMM ver 1.10
[   87.758150] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   87.758154] Bluetooth: BNEP filters: protocol multicast
[   87.902090] Bridge firewalling registered
[   87.903235] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   89.010960] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   89.431632] [drm] Initialized drm 1.1.0 20060810
[   89.465603] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   90.014329] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   90.014374] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[   90.014413] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[   90.293652] [drm] Setting GART location based on new memory map
[   90.293675] [drm] Loading R500 Microcode
[   90.293736] [drm] Num pipes: 1
[   90.293746] [drm] writeback test succeeded in 1 usecs
[   91.689629] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   91.692162] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   91.695191] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  102.040024] eth0: no IPv6 routers present
[25953.367532] UDF-fs: Partition marked readonly; forcing readonly mount
[25953.390826] UDF-fs INFO UDF: Mounting volume 'LG_COMBI_RECORDER', timestamp 2007/01/23 15:23 (1f10)
[26020.048177] ppdev0: registered pardevice
[26020.096057] ppdev0: unregistered pardevice
[26023.369453] ppdev0: registered pardevice
[26023.417283] ppdev0: unregistered pardevice
[26024.317941] ppdev0: registered pardevice
[26024.364330] ppdev0: unregistered pardevice
[31724.000321] e100: eth0: e100_watchdog: link down
[31736.000122] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[31738.000319] e100: eth0: e100_watchdog: link down
[31740.000125] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[33078.116045] usb 1-5: new high speed USB device using ehci_hcd and address 3
[33078.285098] usb 1-5: configuration #1 chosen from 1 choice
[33078.425979] usbcore: registered new interface driver libusual
[33078.454794] Initializing USB Mass Storage driver...
[33078.458639] scsi2 : SCSI emulation for USB Mass Storage devices
[33078.460044] usbcore: registered new interface driver usb-storage
[33078.468282] USB Mass Storage support registered.
[33078.470579] usb-storage: device found at 3
[33078.470594] usb-storage: waiting for device to settle before scanning
[33083.468356] usb-storage: device scan complete
[33083.469189] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[33084.002318] sd 2:0:0:0: [sdb] 1007616 512-byte hardware sectors (516 MB)
[33084.003194] sd 2:0:0:0: [sdb] Write Protect is off
[33084.003201] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[33084.003205] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[33084.016943] sd 2:0:0:0: [sdb] 1007616 512-byte hardware sectors (516 MB)
[33084.018944] sd 2:0:0:0: [sdb] Write Protect is off
[33084.018952] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[33084.018956] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[33084.022058]  sdb: sdb1
[33084.023584] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[33084.024071] sd 2:0:0:0: Attached scsi generic sg2 type 0
[33130.716047] usb 1-5: USB disconnect, address 3
[131963.983655] [drm] Num pipes: 1
[131965.042291] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[131965.042337] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[131965.042375] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[131965.087394] [drm] Setting GART location based on new memory map
[131965.087419] [drm] Loading R500 Microcode
[131965.087477] [drm] Num pipes: 1
[131965.087487] [drm] writeback test succeeded in 1 usecs
[132108.244158] ppdev0: registered pardevice
[132108.292049] ppdev0: unregistered pardevice
[132112.060321] ppdev0: registered pardevice
[132112.108432] ppdev0: unregistered pardevice
[132113.306704] ppdev0: registered pardevice
[132113.356278] ppdev0: unregistered pardevice
[132353.576002] [drm] Num pipes: 1
[132355.090947] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[132355.090989] agpgart-intel 0000:00:00.0: putting AGP V2 device into 1x mode
[132355.091027] pci 0000:01:00.0: putting AGP V2 device into 1x mode
[132355.142940] [drm] Setting GART location based on new memory map
[132355.142970] [drm] Loading R500 Microcode
[132355.143027] [drm] Num pipes: 1
[132355.143038] [drm] writeback test succeeded in 1 usecs
[150296.394846] qdvdauthor[26479]: segfault at ffffffff ip ffffffff sp b68f71ac error 4
scott@scott-desktop:~$ 



```

```


scott@scott-desktop:~$ lspci -vvn
00:00.0 0600: 8086:2560 (rev 01)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at dc000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 0604: 8086:2561 (rev 01) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f04fffff
	Prefetchable memory behind bridge: e0000000-f01fffff
	Secondary status: 66MHz+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1d.0 0c03: 8086:24c2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: 0e11:00b8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 3440 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 0c03: 8086:24c4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: 0e11:00b8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at 3460 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 0c03: 8086:24c7 (rev 01) (prog-if 00 [UHCI])
	Subsystem: 0e11:00b8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at 3480 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 0c03: 8086:24cd (rev 01) (prog-if 20 [EHCI])
	Subsystem: 0e11:00b8
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 23
	Region 0: Memory at f0a00000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 0604: 8086:244e (rev 81) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0500000-f07fffff
	Prefetchable memory behind bridge: f4000000-f81fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:1f.0 0601: 8086:24c0 (rev 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 0101: 8086:24cb (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: 0e11:00b8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at 34c0 [size=16]
	Region 5: Memory at 50000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.5 0401: 8086:24c5 (rev 01)
	Subsystem: 0e11:00b8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 3000 [size=256]
	Region 1: I/O ports at 3400 [size=64]
	Region 2: Memory at f0a00400 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at f0a00600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 0300: 1002:7142 (prog-if 00 [VGA controller])
	Subsystem: 1002:030b
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 2000 [size=256]
	Region 2: Memory at f0400000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 0380: 1002:7162
	Subsystem: 1002:030a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min), Cache Line Size: 64 bytes
	Region 0: Memory at f0410000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

05:08.0 0200: 8086:103b (rev 81)
	Subsystem: 0e11:0012
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min, 14000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at f0500000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at 1000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100, eepro100

05:0a.0 0400: 4444:0016 (rev 01)
	Subsystem: 9005:0092
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (32000ns min, 2000ns max), Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: ivtv
	Kernel modules: ivtv


```

```

scott@scott-desktop:~$ lsusb -vvn
lsusb: invalid option -- 'n'

scott@scott-desktop:~$ lsusb -vv

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc00e M-BJ58/M-BJ69 Optical Wheel Mouse
  bcdDevice           11.10
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
scott@scott-desktop:~$ 


```

---

### Post by sdowney717 on 2008-10-04
For some reason, i can not paste the contents of the logs, So I archived them

---

