---
title: "Lost wireless on a ThinkPad R51e."
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by Ecks51 on 2009-01-17
I've just installed 8.04 on my ThinkPad R51e, and lost my wireless after I installed the recommended updates. Is there anyway to get this running again?

---

### Post by Whizam on 2009-01-18
Can you post the output of the following commands:
lspci
sudo ifconfig -a
sudo iwconfig
dmesg

That info will help diagnose the problem.

---

### Post by Ecks51 on 2009-01-18
> **Whizam said:**
> Can you post the output of the following commands: That info will help diagnose the problem.
lspci
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751F Fast Ethernet PCI Express (rev 21)
04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
04:02.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```
sudo ifconfig -a
```
ath0      Link encap:Ethernet  HWaddr 00:16:ce:5e:ac:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:c6:c4:2b  
          inet addr:192.168.13.12  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fec6:c42b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30034384 (28.6 MB)  TX bytes:1613683 (1.5 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92500 (90.3 KB)  TX bytes:92500 (90.3 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CE-5E-AC-96-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12789 errors:0 dropped:0 overruns:0 frame:1996
          TX packets:14463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1272134 (1.2 MB)  TX bytes:665718 (650.1 KB)
          Interrupt:19 

```
sudo iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-94 dBm  Noise level=-94 dBm
          Rx invalid nwid:12440  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
dmesg
```
42 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1595.484 MHz processor.
[    3.880601] Console: colour VGA+ 80x25
[    3.880606] console [tty0] enabled
[    3.881044] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    3.881420] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    3.895799] Memory: 441580k/457600k available (2178k kernel code, 15444k reserved, 1005k data, 368k init, 0k highmem)
[    3.895808] virtual kernel memory layout:
[    3.895810]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    3.895811]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    3.895812]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[    3.895814]     lowmem  : 0xc0000000 - 0xdbee0000   ( 446 MB)
[    3.895815]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    3.895816]       .data : 0xc0320918 - 0xc041bdc4   (1005 kB)
[    3.895818]       .text : 0xc0100000 - 0xc0320918   (2178 kB)
[    3.895821] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    3.895864] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    3.975791] Calibrating delay using timer specific routine.. 3194.64 BogoMIPS (lpj=6389295)
[    3.975824] Security Framework initialized
[    3.975834] SELinux:  Disabled at boot.
[    3.975850] AppArmor: AppArmor initialized
[    3.975855] Failure registering capabilities with primary security module.
[    3.975865] Mount-cache hash table entries: 512
[    3.976010] Initializing cgroup subsys ns
[    3.976017] Initializing cgroup subsys cpuacct
[    3.976029] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000 00000000
[    3.976041] CPU: L1 I cache: 32K, L1 D cache: 32K
[    3.976044] CPU: L2 cache: 1024K
[    3.976048] CPU: After all inits, caps: afe9fbff 00100000 00000000 00042040 00000000 00000000 00000000 00000000
[    3.976058] Compat vDSO mapped to ffffe000.
[    3.976072] Checking 'hlt' instruction... OK.
[    3.992234] SMP alternatives: switching to UP code
[    3.994391] Freeing SMP alternatives: 11k freed
[    3.994517] Early unpacking initramfs... done
[    4.377309] ACPI: Core revision 20070126
[    4.377416] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    4.392558] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[    4.392579] Total of 1 processors activated (3194.64 BogoMIPS).
[    4.392770] ENABLING IO-APIC IRQs
[    4.392974] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    4.432662] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    4.432715] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[    4.432718] ...trying to set up timer as Virtual Wire IRQ... works.
[    4.579081] Brought up 1 CPUs
[    4.579109] CPU0 attaching sched-domain:
[    4.579112]  domain 0: span 01
[    4.579114]   groups: 01
[    4.579315] net_namespace: 64 bytes
[    4.579324] Booting paravirtualized kernel on bare hardware
[    4.579832] Time: 22:54:49  Date: 01/17/09
[    4.579864] NET: Registered protocol family 16
[    4.580076] EISA bus registered
[    4.580111] ACPI: bus type pci registered
[    4.580398] PCI: PCI BIOS revision 2.10 entry at 0xfd7bd, last bus=8
[    4.580401] PCI: Using configuration type 1
[    4.580408] Setting up standard PCI resources
[    4.582845] ACPI: EC: EC description table is found, configuring boot EC
[    4.588004] ACPI: Interpreter enabled
[    4.588008] ACPI: (supports S0 S3 S4 S5)
[    4.588023] ACPI: Using IOAPIC for interrupt routing
[    4.593856] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    4.593859] ACPI: EC: driver started in poll mode
[    4.594008] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    4.595791] PCI: Transparent bridge - 0000:00:14.4
[    4.595892] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    4.596029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    4.596157] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    4.596285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    4.596405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    4.598739] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.598871] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.599003] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.599142] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11)
[    4.599273] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.599401] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.599533] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.599664] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    4.600290] ACPI: Power Resource [PUBS] (on)
[    4.600341] Linux Plug and Play Support v0.97 (c) Adam Belay
[    4.600375] pnp: PnP ACPI init
[    4.600384] ACPI: bus type pnp registered
[    4.603049] pnp: PnP ACPI: found 11 devices
[    4.603052] ACPI: ACPI bus type pnp unregistered
[    4.603056] PnPBIOS: Disabled by ACPI PNP
[    4.603300] PCI: Using ACPI for IRQ routing
[    4.603303] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    4.603311] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[    4.603314] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[    4.634969] NET: Registered protocol family 8
[    4.634971] NET: Registered protocol family 20
[    4.635051] AppArmor: AppArmor Filesystem Enabled
[    4.638955] Time: tsc clocksource has been installed.
[    4.646988] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    4.646995] system 00:02: iomem range 0xe0000-0xfffff could not be reserved
[    4.646999] system 00:02: iomem range 0xfff80000-0xffffffff has been reserved
[    4.647002] system 00:02: iomem range 0x0-0xfff could not be reserved
[    4.647008] system 00:03: ioport range 0x1080-0x1080 has been reserved
[    4.647011] system 00:03: ioport range 0x220-0x22f has been reserved
[    4.647014] system 00:03: ioport range 0x3bf-0x3bf has been reserved
[    4.647017] system 00:03: ioport range 0x7bf-0x7bf has been reserved
[    4.647020] system 00:03: ioport range 0x40b-0x40b has been reserved
[    4.647023] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    4.647026] system 00:03: ioport range 0x4d6-0x4d6 has been reserved
[    4.647029] system 00:03: ioport range 0x530-0x537 has been reserved
[    4.647032] system 00:03: ioport range 0xc00-0xc01 has been reserved
[    4.647035] system 00:03: ioport range 0xc14-0xc14 has been reserved
[    4.647038] system 00:03: ioport range 0xc50-0xc52 has been reserved
[    4.647041] system 00:03: ioport range 0xc6c-0xc6c has been reserved
[    4.647044] system 00:03: ioport range 0xc6f-0xc6f has been reserved
[    4.647047] system 00:03: ioport range 0xcd4-0xcd5 has been reserved
[    4.647050] system 00:03: ioport range 0xcd6-0xcd7 has been reserved
[    4.647053] system 00:03: ioport range 0xcd8-0xcdf has been reserved
[    4.647056] system 00:03: ioport range 0x8000-0x805f could not be reserved
[    4.647059] system 00:03: ioport range 0xf40-0xf47 has been reserved
[    4.647062] system 00:03: ioport range 0x280-0x293 has been reserved
[    4.677499] PCI: Bridge: 0000:00:01.0
[    4.677502]   IO window: 9000-9fff
[    4.677507]   MEM window: b0100000-b01fffff
[    4.677511]   PREFETCH window: c8000000-cfffffff
[    4.677515] PCI: Bridge: 0000:00:04.0
[    4.677516]   IO window: disabled.
[    4.677520]   MEM window: b0200000-b02fffff
[    4.677523]   PREFETCH window: disabled.
[    4.677527] PCI: Bridge: 0000:00:06.0
[    4.677529]   IO window: disabled.
[    4.677532]   MEM window: disabled.
[    4.677535]   PREFETCH window: disabled.
[    4.677542] PCI: Bus 5, cardbus bridge: 0000:04:00.0
[    4.677544]   IO window: 0000a000-0000a0ff
[    4.677553]   IO window: 0000a400-0000a4ff
[    4.677560]   PREFETCH window: d0000000-d3ffffff
[    4.677566]   MEM window: b4000000-b7ffffff
[    4.677573] PCI: Bridge: 0000:00:14.4
[    4.677576]   IO window: a000-dfff
[    4.677584]   MEM window: b0300000-bfffffff
[    4.677590]   PREFETCH window: d0000000-d7ffffff
[    4.677621] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    4.677634] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    4.677674] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 20 (level, low) -> IRQ 16
[    4.677692] NET: Registered protocol family 2
[    4.714937] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    4.715146] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    4.715286] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    4.715419] TCP: Hash tables configured (established 16384 bind 16384)
[    4.715422] TCP reno registered
[    4.726982] checking if image is initramfs... it is
[    5.178262] Switched to high resolution mode on CPU 0
[    5.485074] Freeing initrd memory: 7317k freed
[    5.485375] Simple Boot Flag at 0x35 set to 0x1
[    5.485921] audit: initializing netlink socket (disabled)
[    5.485941] audit(1232232889.444:1): initialized
[    5.488252] VFS: Disk quotas dquot_6.5.1
[    5.488350] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    5.488533] io scheduler noop registered
[    5.488535] io scheduler anticipatory registered
[    5.488538] io scheduler deadline registered
[    5.488550] io scheduler cfq registered (default)
[    5.921282] Boot video device is 0000:01:05.0
[    5.921430] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    5.921470] assign_interrupt_mode Found MSI capability
[    5.921512] Allocate Port Service[0000:00:04.0:pcie00]
[    5.921605] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    5.921643] assign_interrupt_mode Found MSI capability
[    5.921679] Allocate Port Service[0000:00:06.0:pcie00]
[    5.921927] isapnp: Scanning for PnP cards...
[    6.278982] isapnp: No Plug & Play device found
[    6.309324] Real Time Clock Driver v1.12ac
[    6.309462] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    6.310185] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[    6.310198] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[    6.310904] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    6.310987] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    6.311097] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    6.319592] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.319597] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.328780] mice: PS/2 mouse device common for all mice
[    6.328919] EISA: Probing bus 0 at eisa.0
[    6.328932] Cannot allocate resource for EISA slot 1
[    6.328964] Cannot allocate resource for EISA slot 8
[    6.328966] EISA: Detected 0 cards.
[    6.328970] cpuidle: using governor ladder
[    6.328972] cpuidle: using governor menu
[    6.329090] NET: Registered protocol family 1
[    6.329122] Using IPI No-Shortcut mode
[    6.329163] registered taskstats version 1
[    6.329284]   Magic number: 9:471:957
[    6.329373]   hash matches device ptyze
[    6.329475] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.329477] EDD information not available.
[    6.329852] Freeing unused kernel memory: 368k freed
[    6.329883] Write protecting the kernel read-only data: 801k
[    6.334331] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    7.543005] fuse init (API version 7.9)
[    7.563274] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    7.563282] ACPI: Processor [CPU] (supports 8 throttling states)
[    7.566468] ACPI: Thermal Zone [THM0] (53 C)
[    8.161068] tg3.c:v3.86 (November 9, 2007)
[    8.161103] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[    8.161118] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    8.246293] usbcore: registered new interface driver usbfs
[    8.246325] usbcore: registered new interface driver hub
[    8.258214] usbcore: registered new device driver usb
[    8.269212] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    8.271867] eth0: Tigon3 [partno(BCM95751F) rev 4201 PHY(5750)] (PCI Express) 10/100Base-TX Ethernet 00:0a:e4:c6:c4:2b
[    8.271875] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    8.271878] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    8.271925] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 9 (level, low) -> IRQ 9
[    8.271943] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    8.272459] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    8.272489] ohci_hcd 0000:00:13.0: irq 9, io mem 0xb0000000
[    8.310414] SCSI subsystem initialized
[    8.326742] usb usb1: configuration #1 chosen from 1 choice
[    8.326773] hub 1-0:1.0: USB hub found
[    8.326789] hub 1-0:1.0: 4 ports detected
[    8.372541] libata version 3.00 loaded.
[    8.430137] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 9 (level, low) -> IRQ 9
[    8.430162] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    8.430191] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    8.430213] ohci_hcd 0000:00:13.1: irq 9, io mem 0xb0001000
[    8.486513] usb usb2: configuration #1 chosen from 1 choice
[    8.486544] hub 2-0:1.0: USB hub found
[    8.486559] hub 2-0:1.0: 4 ports detected
[    8.590611] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 9 (level, low) -> IRQ 9
[    8.590632] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    8.590667] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    8.590735] ehci_hcd 0000:00:13.2: irq 9, io mem 0xb0002000
[    8.601728] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    8.601879] usb usb3: configuration #1 chosen from 1 choice
[    8.601907] hub 3-0:1.0: USB hub found
[    8.601915] hub 3-0:1.0: 8 ports detected
[    8.709315] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    8.709380] PCI: Setting latency timer of device 0000:00:14.1 to 64
[    8.709398] ACPI: PCI interrupt for device 0000:00:14.1 disabled
[    8.712824] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    8.713582] scsi0 : pata_atiixp
[    8.714193] scsi1 : pata_atiixp
[    8.715568] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[    8.715572] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[    8.878171] ata1.00: ATA-6: WDC WD800VE-08HDT0, 10.07D10, max UDMA/100
[    8.878177] ata1.00: 156301488 sectors, multi 16: LBA 
[    8.886037] ata1.00: configured for UDMA/100
[    9.205606] ata2.00: ATAPI: DVD/CDRW UJDA770, 1.02, max UDMA/33
[    9.205625] ata2.00: simplex DMA is claimed by other device, disabling DMA
[    9.377353] ata2.00: configured for PIO4
[    9.377522] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800VE-08HD 10.0 PQ: 0 ANSI: 5
[    9.379246] scsi 1:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA770 1.02 PQ: 0 ANSI: 5
[    9.387433] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.387440] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.399036] Driver 'sd' needs updating - please use bus_type methods
[    9.399148] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    9.399163] sd 0:0:0:0: [sda] Write Protect is off
[    9.399166] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.399184] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.399237] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    9.399247] sd 0:0:0:0: [sda] Write Protect is off
[    9.399249] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.399265] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.399270]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    9.451575]  sda1 sda2 < sda5 >
[    9.481743] sd 0:0:0:0: [sda] Attached SCSI disk
[    9.488883] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    9.488906] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    9.492656] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    9.492663] Uniform CD-ROM driver Revision: 3.20
[    9.492730] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    9.751775] Attempting manual resume
[    9.751780] swsusp: Resume From Partition 8:5
[    9.751782] PM: Checking swsusp image.
[    9.752012] PM: Resume from disk failed.
[    9.781341] kjournald starting.  Commit interval 5 seconds
[    9.781359] EXT3-fs: mounted filesystem with ordered data mode.
[   10.167659] Clocksource tsc unstable (delta = -2199005110 ns)
[   10.171636] Time: acpi_pm clocksource has been installed.
[   15.841892] ACPI Error (evgpe-0705): No handler or method for GPE[ 0], disabling event [20070126]
[   15.841902] ACPI Error (evgpe-0705): No handler or method for GPE[ 1], disabling event [20070126]
[   15.841909] ACPI Error (evgpe-0705): No handler or method for GPE[ 2], disabling event [20070126]
[   15.841918] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.841923] ACPI Error (evgpe-0705): No handler or method for GPE[ 4], disabling event [20070126]
[   15.841929] ACPI Error (evgpe-0705): No handler or method for GPE[ 5], disabling event [20070126]
[   15.841946] ACPI Error (evgpe-0705): No handler or method for GPE[ 8], disabling event [20070126]
[   15.841953] ACPI Error (evgpe-0705): No handler or method for GPE[ 9], disabling event [20070126]
[   15.841959] ACPI Error (evgpe-0705): No handler or method for GPE[ A], disabling event [20070126]
[   15.841966] ACPI Error (evgpe-0705): No handler or method for GPE[ C], disabling event [20070126]
[   15.841972] ACPI Error (evgpe-0705): No handler or method for GPE[ D], disabling event [20070126]
[   15.841978] ACPI Error (evgpe-0705): No handler or method for GPE[ E], disabling event [20070126]
[   15.841984] ACPI Error (evgpe-0705): No handler or method for GPE[ F], disabling event [20070126]
[   15.841994] ACPI Error (evgpe-0705): No handler or method for GPE[10], disabling event [20070126]
[   15.842000] ACPI Error (evgpe-0705): No handler or method for GPE[11], disabling event [20070126]
[   15.842007] ACPI Error (evgpe-0705): No handler or method for GPE[13], disabling event [20070126]
[   15.842013] ACPI Error (evgpe-0705): No handler or method for GPE[14], disabling event [20070126]
[   15.842019] ACPI Error (evgpe-0705): No handler or method for GPE[15], disabling event [20070126]
[   15.842026] ACPI Error (evgpe-0705): No handler or method for GPE[16], disabling event [20070126]
[   15.842032] ACPI Error (evgpe-0705): No handler or method for GPE[17], disabling event [20070126]
[   15.842042] ACPI Error (evgpe-0705): No handler or method for GPE[18], disabling event [20070126]
[   15.842048] ACPI Error (evgpe-0705): No handler or method for GPE[19], disabling event [20070126]
[   15.842054] ACPI Error (evgpe-0705): No handler or method for GPE[1A], disabling event [20070126]
[   15.842060] ACPI Error (evgpe-0705): No handler or method for GPE[1B], disabling event [20070126]
[   15.842067] ACPI Error (evgpe-0705): No handler or method for GPE[1C], disabling event [20070126]
[   15.842073] ACPI Error (evgpe-0705): No handler or method for GPE[1D], disabling event [20070126]
[   15.842079] ACPI Error (evgpe-0705): No handler or method for GPE[1E], disabling event [20070126]
[   15.842085] ACPI Error (evgpe-0705): No handler or method for GPE[1F], disabling event [20070126]
[   16.299365] ACPI: EC: missing OBF confirmation, don't expect it any longer.
[   16.795211] ACPI: EC: missing write data confirmation, don't expect it any longer.
[   17.126417] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   17.590946] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.631640] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.729957] Linux agpgart interface v0.102
[   17.893758] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   18.062169] parport_pc 00:0a: reported by Plug and Play ACPI
[   18.062295] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   18.288096] input: Power Button (FF) as /devices/virtual/input/input3
[   18.301113] ACPI: Power Button (FF) [PWRF]
[   18.301239] input: Lid Switch as /devices/virtual/input/input4
[   18.301692] ACPI: Lid Switch [LID]
[   18.301763] input: Sleep Button (CM) as /devices/virtual/input/input5
[   18.317105] ACPI: Sleep Button (CM) [SLPB]
[   18.330784] ath_hal: module license 'Proprietary' taints kernel.
[   18.337085] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   18.445132] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 17
[   18.556792] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2160: MC'97 1 converters and GPIO not ready (0xff00)
[   18.740534] wlan: 0.9.4
[   18.928364] Yenta: CardBus bridge found at 0000:04:00.0 [1410:0528]
[   18.928402] Yenta: Using INTVAL to route CSC interrupts to PCI
[   18.928404] Yenta: Routing CardBus interrupts to PCI
[   18.928412] Yenta TI: socket 0000:04:00.0, mfunc 0x01d21002, devctl 0x64
[   19.120251] Non-volatile memory driver v1.2
[   19.160675] Yenta: ISA IRQ mask 0x0c78, PCI irq 16
[   19.160682] Socket status: 30000007
[   19.160687] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xdfff
[   19.160691] cs: IO port probe 0xa000-0xdfff: clean.
[   19.161903] pcmcia: parent PCI bridge Memory window: 0xb0300000 - 0xbfffffff
[   19.161906] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd7ffffff
[   19.262666] ath_pci: 0.9.4
[   19.262766] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 22 (level, low) -> IRQ 19
[   20.186273] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.199710] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input6
[   20.238641] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   20.238646] thinkpad_acpi: http://ibm-acpi.sf.net/
[   20.238648] thinkpad_acpi: ThinkPad BIOS 78ET67WW (1.57 ), EC 78HT06WW-1.01
[   20.238651] thinkpad_acpi: IBM ThinkPad R51e
[   20.244411] thinkpad_acpi: fan_init: initial fan status is unknown, assuming it is in auto mode
[   20.244560] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   20.618413] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:10/LNXVIDEO:00/input/input8
[   20.641913] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   20.990901] [fglrx] Maximum main memory to use for locked dma buffers: 371 MBytes.
[   20.990948] [fglrx] ASYNCIO init succeed!
[   20.991177] [fglrx] PAT is enabled successfully!
[   20.993117] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   21.026666] ACPI: AC Adapter [AC] (on-line)
[   21.101126] ACPI: Battery Slot [BAT0] (battery present)
[   21.206263] ath_rate_sample: 1.2 (0.9.4)
[   21.206788] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   21.206794] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.206803] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   21.206810] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   21.206814] wifi0: mac 5.9 phy 4.3 radio 4.6
[   21.206819] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   21.206821] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   21.206823] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   21.206825] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   21.206827] wifi0: Use hw queue 8 for CAB traffic
[   21.206829] wifi0: Use hw queue 9 for beacons
[   21.228227] wifi0: Atheros 5212: mem=0xb0300000, irq=19
[   21.228787] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 17
[   22.842264] cs: IO port probe 0x100-0x3af: clean.
[   22.844794] cs: IO port probe 0x3e0-0x4ff: clean.
[   22.845847] cs: IO port probe 0x820-0x8ff: clean.
[   22.846769] cs: IO port probe 0xc00-0xcf7: clean.
[   22.847680] cs: IO port probe 0xa00-0xaff: clean.
[   22.998313] lp0: using parport0 (interrupt-driven).
[   23.040130] Adding 1309256k swap on /dev/sda5.  Priority:-1 extents:1 across:1309256k
[   23.456085] EXT3 FS on sda1, internal journal
[   24.017351] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.366030] No dock devices found.
[   25.446086] IBM machine detected. Enabling interrupts during APM calls.
[   25.446092] apm: BIOS not found.
[   25.674889] ppdev: user-space parallel port driver
[   25.836308] audit(1232232927.573:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4848 profile="/usr/sbin/cupsd" namespace="default"
[   25.946816] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input9
[   26.961134] Bluetooth: Core ver 2.11
[   26.961933] NET: Registered protocol family 31
[   26.961938] Bluetooth: HCI device and connection manager initialized
[   26.961944] Bluetooth: HCI socket layer initialized
[   26.986783] Bluetooth: L2CAP ver 2.9
[   26.986790] Bluetooth: L2CAP socket layer initialized
[   27.067396] Bluetooth: RFCOMM socket layer initialized
[   27.067420] Bluetooth: RFCOMM TTY layer initialized
[   27.067422] Bluetooth: RFCOMM ver 1.8
[   28.535634] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   28.535641] tg3: eth0: Flow control is on for TX and on for RX.
[   29.116656] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.635540] NET: Registered protocol family 17
[   32.504373] [fglrx] GART Table is not in FRAME_BUFFER range 
[   32.504389] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[   32.504392] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[   32.742107] [fglrx] interrupt source 10000000 successfully enabled
[   32.742117] [fglrx] enable ID = 0x00000004
[   32.742478] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   34.347481] NET: Registered protocol family 10
[   34.348048] lo: Disabled Privacy Extensions
[   38.759647] ath0: no IPv6 routers present
[   38.811553] eth0: no IPv6 routers present
[21007.500577] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[21011.101521] ath0: no IPv6 routers present
[21043.475551] eth0: no IPv6 routers present

```

---

### Post by Ecks51 on 2009-03-26
I've also installed madwifi... still nothing.

---

### Post by superprash2003 on 2009-03-27
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

---

