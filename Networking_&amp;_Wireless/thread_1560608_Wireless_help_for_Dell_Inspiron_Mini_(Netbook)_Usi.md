---
title: "Wireless help for Dell Inspiron Mini (Netbook) Using Ubuntu Netbook 10.04"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by jakesch on 2010-08-25
The first question I have is how to I fill out the information that I should have in order to help others help me? I do not know how to access the information about my system in ubuntu. This is my first time ever trying this OS. 

After I receive help on that, I will then be requesting help on how to get the wireless internet working on my Ubuntu OS enabled Netbook. 

Thanks in advanced for anyone who is willing to help me get started learning about this OS. :D

---

### Post by sharathcshekhar on 2010-08-25
If you mean the hardware, you can try 
```

sudo lshw 

```
This will list a complete information of the System Hardware. Please mention the appropriate H/w in the posts you make. Most of the issues can be solved without any of this knowledge!! Unless it is some specific h/w problem.
Also attach any screen shot if you are not aware of the issue or unable to put it. That will help in debugging.

---

### Post by jakesch on 2010-08-25
> **sharathcshekhar said:**
> If you mean the hardware, you can try 
```

sudo lshw 

```
This will list a complete information of the System Hardware. Please mention the appropriate H/w in the posts you make. Most of the issues can be solved without any of this knowledge!! Unless it is some specific h/w problem.
Also attach any screen shot if you are not aware of the issue or unable to put it. That will help in debugging.

Thank you for stepping up to help me. My main problem with filling out the ticket is that I don't understand the "codes" that you are talking about. I have no idea were to put the code "sudo lshw" in the thread explaining how to fill out a ticket is says to use grep, but I do not know what that is. Again, this is my first time (today) ever running Ubuntu. I can tell you that the issue is that everytime I enter in my wireless information is just says that it is disconnected, and seems like it won't even try.

Again, thank you for helping.

---

### Post by dineshs on 2010-08-25
Applications-accessories-terminal
copy the command paste on terminal and enter
```
sudo lshw -C network
```
```
iwconfig
```
And post the results back

---

### Post by jakesch on 2010-08-25
1 ) Machine Brand and Model (PC/Laptop):
Code:

Get it from your product information.

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

jake@jake-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

jake@jake-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:63e3 Microdia 
Bus 001 Device 002: ID 413c:8147 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

(hint) use grep to get only information about the Wireless
Code:

jake@jake-laptop:~$ $ lspci -nn | grep 'Wireless Brand'
$: command not found

3 ) check interface:
Code:

jake@jake-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:a7:d6:24  
          inet addr:192.168.0.119  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fea7:d624/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2947779 (2.9 MB)  TX bytes:254317 (254.3 KB)
          Interrupt:24 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


jake@jake-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff


(hint) if the Wireless interface name is wlan0 you can also use
Code:

jake@jake-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


4 ) Check for modules:
Code:

jake@jake-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
dell_wmi                1793  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
zaurus                  2404  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
compal_laptop           2034  0 
b43                   163523  0 
cdc_ether               3541  1 zaurus
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
psmouse                63245  0 
mac80211              205146  1 b43
dcdbas                  5422  0 
usbnet                 14943  2 zaurus,cdc_ether
cdc_wdm                 8218  0 
cdc_acm                13538  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
vga16fb                11385  1 
i2c_isch                3311  0 
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  0 
r8169                  34076  0 
pata_sch                1963  2 
ssb                    38671  1 b43
mii                     4381  2 usbnet,r8169


(hint) search for the Wireless module
Code:

$ lsmod | grep "wlan_module_name"

5 ) Kernel boot messages
Code:

[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1329.934 MHz processor.
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 2659.86 BogoMIPS (lpj=5319736)
[    0.004055] Security Framework initialized
[    0.004112] AppArmor: AppArmor initialized
[    0.004132] Mount-cache hash table entries: 512
[    0.004426] Initializing cgroup subsys ns
[    0.004439] Initializing cgroup subsys cpuacct
[    0.004452] Initializing cgroup subsys memory
[    0.004469] Initializing cgroup subsys devices
[    0.004476] Initializing cgroup subsys freezer
[    0.004483] Initializing cgroup subsys net_cls
[    0.004529] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004538] CPU: L2 cache: 512K
[    0.004544] CPU: Physical Processor ID: 0
[    0.004550] CPU: Processor Core ID: 0
[    0.004559] mce: CPU supports 5 MCE banks
[    0.004580] CPU0: Thermal monitoring enabled (TM1)
[    0.004591] using mwait in idle threads.
[    0.004606] Performance Events: Atom events, Intel PMU driver.
[    0.004628] ... version:                3
[    0.004634] ... bit width:              40
[    0.004639] ... generic registers:      2
[    0.004645] ... value mask:             000000ffffffffff
[    0.004651] ... max period:             000000007fffffff
[    0.004657] ... fixed-purpose events:   3
[    0.004663] ... event mask:             0000000700000003
[    0.004674] Checking 'hlt' instruction... OK.
[    0.020016] Disabling 4MB page tables to avoid TLB bug
[    0.025279] ACPI: Core revision 20090903
[    0.036020] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036035] ftrace: allocating 21780 entries in 43 pages
[    0.040124] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040457] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.083237] CPU0: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.168152] CPU1: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.168185] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172043] Brought up 2 CPUs
[    0.172052] Total of 2 processors activated (5319.83 BogoMIPS).
[    0.172302] CPU0 attaching sched-domain:
[    0.172313]  domain 0: span 0-1 level SIBLING
[    0.172320]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.172335]   domain 1: span 0-1 level MC
[    0.172341]    groups: 0-1 (cpu_power = 1178)
[    0.172357] CPU1 attaching sched-domain:
[    0.172363]  domain 0: span 0-1 level SIBLING
[    0.172369]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.172383]   domain 1: span 0-1 level MC
[    0.172389]    groups: 0-1 (cpu_power = 1178)
[    0.172660] devtmpfs: initialized
[    0.172660] regulator: core version 0.5
[    0.172660] Time: 21:55:02  Date: 08/25/10
[    0.172660] NET: Registered protocol family 16
[    0.172660] Trying to unpack rootfs image as initramfs...
[    0.172660] EISA bus registered
[    0.172688] ACPI: bus type pci registered
[    0.172896] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172907] PCI: MCFG area at e0000000 reserved in E820
[    0.172914] PCI: Using MMCONFIG for extended config space
[    0.172922] PCI: Using configuration type 1 for base access
[    0.179041] bio: create slab <bio-0> at 0
[    0.181443] ACPI: EC: Look up EC in DSDT
[    0.188962] ACPI: Interpreter enabled
[    0.188962] ACPI: (supports S0 S3 S4 S5)
[    0.188962] ACPI: Using IOAPIC for interrupt routing
[    0.241656] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[    0.242394] ACPI: No dock devices found.
[    0.243172] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.243437] pci 0000:00:02.0: reg 10 32bit mmio: [0xd8100000-0xd817ffff]
[    0.243454] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.243470] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.243486] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd8380000-0xd839ffff]
[    0.243638] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd83a0000-0xd83a3fff]
[    0.243702] pci 0000:00:1b.0: PME# supported from D0 D3hot
[    0.243713] pci 0000:00:1b.0: PME# disabled
[    0.243813] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.243826] pci 0000:00:1c.0: PME# disabled
[    0.243936] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.243951] pci 0000:00:1c.1: PME# disabled
[    0.244086] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.244175] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.244258] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.244360] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd83a4000-0xd83a43ff]
[    0.244456] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.244468] pci 0000:00:1d.7: PME# disabled
[    0.244605] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.244721] pci 0000:02:00.0: reg 10 io port: [0x2000-0x20ff]
[    0.244756] pci 0000:02:00.0: reg 18 64bit mmio pref: [0xd8410000-0xd8410fff]
[    0.244782] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xd8400000-0xd840ffff]
[    0.244801] pci 0000:02:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.244862] pci 0000:02:00.0: supports D1 D2
[    0.244871] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.244883] pci 0000:02:00.0: PME# disabled
[    0.244978] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.244994] pci 0000:00:1c.0: bridge 32bit mmio pref: [0xd8400000-0xd84fffff]
[    0.245101] pci 0000:03:00.0: reg 10 64bit mmio: [0xd8000000-0xd8003fff]
[    0.245204] pci 0000:03:00.0: supports D1 D2
[    0.245213] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.245225] pci 0000:03:00.0: PME# disabled
[    0.245325] pci 0000:00:1c.1: bridge 32bit mmio: [0xd8000000-0xd80fffff]
[    0.245351] pci_bus 0000:00: on NUMA node 0
[    0.245372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.245882] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.246138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.259586] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 5 6 *7 10 12 14 15)
[    0.259884] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 5 6 7 *11 12 14 15)
[    0.260238] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 5 6 7 10 12 14 15)
[    0.260529] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 *5 6 7 11 12 14 15)
[    0.260817] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 5 6 7 10 12 14 15) *0, disabled.
[    0.261114] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 5 6 7 *11 12 14 15)
[    0.261411] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 5 6 7 *10 12 14 15)
[    0.261698] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 5 6 7 11 12 14 15) *10
[    0.262060] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.262090] vgaarb: loaded
[    0.262509] SCSI subsystem initialized
[    0.262798] libata version 3.00 loaded.
[    0.263071] usbcore: registered new interface driver usbfs
[    0.263126] usbcore: registered new interface driver hub
[    0.263287] usbcore: registered new device driver usb
[    0.263823] ACPI: WMI: Mapper loaded
[    0.263831] PCI: Using ACPI for IRQ routing
[    0.264290] NetLabel: Initializing
[    0.264298] NetLabel:  domain hash size = 128
[    0.264304] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.264348] NetLabel:  unlabeled traffic allowed by default
[    0.264485] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.264504] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.268600] Switching to clocksource tsc
[    0.273915] AppArmor: AppArmor Filesystem Enabled
[    0.273969] pnp: PnP ACPI init
[    0.274018] ACPI: bus type pnp registered
[    0.294931] pnp: PnP ACPI: found 10 devices
[    0.294942] ACPI: ACPI bus type pnp unregistered
[    0.294953] PnPBIOS: Disabled by ACPI PNP
[    0.294995] system 00:01: iomem range 0xfd000000-0xfd003fff has been reserved
[    0.295008] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.295020] system 00:01: iomem range 0xfed00000-0xfed3ffff could not be reserved
[    0.295032] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.295044] system 00:01: iomem range 0xfed45000-0xfed4bfff has been reserved
[    0.295072] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.295098] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.295111] system 00:06: ioport range 0x8080-0x8080 has been reserved
[    0.295122] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.295134] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.295145] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.295158] system 00:06: ioport range 0x374-0x375 has been reserved
[    0.295169] system 00:06: ioport range 0x3f4-0x3f5 has been reserved
[    0.330422] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.330437] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.330452] pci 0000:00:1c.0:   MEM window: 0x40000000-0x403fffff
[    0.330465] pci 0000:00:1c.0:   PREFETCH window: 0xd8400000-0xd84fffff
[    0.330481] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.330491] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.330504] pci 0000:00:1c.1:   MEM window: 0xd8000000-0xd80fffff
[    0.330516] pci 0000:00:1c.1:   PREFETCH window: 0x40400000-0x405fffff
[    0.330559]   alloc irq_desc for 17 on node -1
[    0.330567]   alloc kstat_irqs on node -1
[    0.330591] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.330607] pci 0000:00:1c.0: setting latency timer to 64
[    0.330638]   alloc irq_desc for 16 on node -1
[    0.330646]   alloc kstat_irqs on node -1
[    0.330662] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.330675] pci 0000:00:1c.1: setting latency timer to 64
[    0.330692] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.330703] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.330714] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.330725] pci_bus 0000:02: resource 1 mem: [0x40000000-0x403fffff]
[    0.330736] pci_bus 0000:02: resource 2 pref mem [0xd8400000-0xd84fffff]
[    0.330747] pci_bus 0000:03: resource 0 io:  [0x3000-0x3fff]
[    0.330758] pci_bus 0000:03: resource 1 mem: [0xd8000000-0xd80fffff]
[    0.330770] pci_bus 0000:03: resource 2 pref mem [0x40400000-0x405fffff]
[    0.330890] NET: Registered protocol family 2
[    0.331224] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.332347] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.333831] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.334721] TCP: Hash tables configured (established 131072 bind 65536)
[    0.334737] TCP reno registered
[    0.335112] NET: Registered protocol family 1
[    0.335193] pci 0000:00:02.0: Boot video device
[    0.335397] Simple Boot Flag at 0x36 set to 0x1
[    0.336014] cpufreq-nforce2: No nForce2 chipset.
[    0.336125] Scanning for low memory corruption every 60 seconds
[    0.336525] audit: initializing netlink socket (disabled)
[    0.336558] type=2000 audit(1282773302.334:1): initialized
[    0.362577] highmem bounce pool size: 64 pages
[    0.362597] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.368994] VFS: Disk quotas dquot_6.5.2
[    0.369231] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.371732] fuse init (API version 7.13)
[    0.372119] msgmni has been set to 1716
[    0.372975] alg: No test for stdrng (krng)
[    0.373238] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.373249] io scheduler noop registered
[    0.373257] io scheduler anticipatory registered
[    0.373264] io scheduler deadline registered
[    0.373427] io scheduler cfq registered (default)
[    0.373744] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.373962] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.374201] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.374487] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.375177] ACPI: AC Adapter [ACAD] (off-line)
[    0.375396] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.375500] ACPI: Lid Switch [LID0]
[    0.375675] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.375691] ACPI: Power Button [PWRB]
[    0.375897] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.375909] ACPI: Power Button [PWRF]
[    0.375926] ACPI Error: Could not enable PowerButton event (20090903/evxfevnt-193)
[    0.375943] ACPI Warning: Could not enable fixed event 2 (20090903/evxface-146)
[    0.376101] button: probe of LNXPWRBN:00 failed with error -22
[    0.377905] ACPI: SSDT 3f6bbfd9 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.379424] ACPI: SSDT 3f6bb915 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.380845] Monitor-Mwait will be used to enter C-1 state
[    0.380967] Monitor-Mwait will be used to enter C-2 state
[    0.381070] Monitor-Mwait will be used to enter C-3 state
[    0.381170] Monitor-Mwait will be used to enter C-3 state
[    0.381196] Marking TSC unstable due to TSC halts in idle
[    0.381373] processor LNXCPU:00: registered as cooling_device0
[    0.382295] ACPI: SSDT 3f6bc1dc 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.382295] ACPI: SSDT 3f6bbf54 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.382684] Switching to clocksource hpet
[    0.416301] processor LNXCPU:01: registered as cooling_device1
[    0.450769] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.455701] brd: module loaded
[    0.458025] loop: module loaded
[    0.458373] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.458942] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    0.460248] Fixed MDIO Bus: probed
[    0.460400] PPP generic driver version 2.4.2
[    0.460584] tun: Universal TUN/TAP device driver, 1.6
[    0.460594] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.460905] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.460974]   alloc irq_desc for 21 on node -1
[    0.460982]   alloc kstat_irqs on node -1
[    0.461003] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.461051] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.461062] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.461191] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.461263] ehci_hcd 0000:00:1d.7: debug port 1
[    0.465179] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.465289] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xd83a4000
[    0.469253] isapnp: Scanning for PnP cards...
[    0.562666] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.563080] usb usb1: configuration #1 chosen from 1 choice
[    0.563193] hub 1-0:1.0: USB hub found
[    0.563223] hub 1-0:1.0: 8 ports detected
[    0.563439] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.563499] uhci_hcd: USB Universal Host Controller Interface driver
[    0.563610]   alloc irq_desc for 23 on node -1
[    0.563619]   alloc kstat_irqs on node -1
[    0.563641] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.563662] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.563674] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.563851] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.563924] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.564318] usb usb2: configuration #1 chosen from 1 choice
[    0.564425] hub 2-0:1.0: USB hub found
[    0.564451] hub 2-0:1.0: 2 ports detected
[    0.564601]   alloc irq_desc for 19 on node -1
[    0.564609]   alloc kstat_irqs on node -1
[    0.564628] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.564647] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.564657] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.564803] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.564872] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.565209] usb usb3: configuration #1 chosen from 1 choice
[    0.565316] hub 3-0:1.0: USB hub found
[    0.565341] hub 3-0:1.0: 2 ports detected
[    0.565497]   alloc irq_desc for 18 on node -1
[    0.565506]   alloc kstat_irqs on node -1
[    0.565522] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.565541] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.565551] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.565699] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.565764] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.566107] usb usb4: configuration #1 chosen from 1 choice
[    0.566213] hub 4-0:1.0: USB hub found
[    0.566238] hub 4-0:1.0: 2 ports detected
[    0.566558] PNP: PS/2 Controller [PNP0303S2K,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    0.588708] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.588743] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.589326] mice: PS/2 mouse device common for all mice
[    0.589756] rtc_cmos 00:07: RTC can wake from S4
[    0.589894] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.589943] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.590394] device-mapper: uevent: version 1.0.3
[    0.608427] ACPI: Battery Slot [BAT1] (battery present)
[    0.634636] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.722537] Freeing initrd memory: 7773k freed
[    0.722738] device-mapper: multipath: version 1.1.0 loaded
[    0.722754] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.724637] EISA: Probing bus 0 at eisa.0
[    0.724674] Cannot allocate resource for EISA slot 1
[    0.724689] Cannot allocate resource for EISA slot 2
[    0.724699] Cannot allocate resource for EISA slot 3
[    0.724737] Cannot allocate resource for EISA slot 8
[    0.724745] EISA: Detected 0 cards.
[    0.735050] cpuidle: using governor ladder
[    0.735549] cpuidle: using governor menu
[    0.737150] TCP cubic registered
[    0.737742] NET: Registered protocol family 10
[    0.739261] lo: Disabled Privacy Extensions
[    0.740369] NET: Registered protocol family 17
[    0.741871] Using IPI No-Shortcut mode
[    0.742174] PM: Resume from disk failed.
[    0.742213] registered taskstats version 1
[    0.742740]   Magic number: 6:12:956
[    0.742880] rtc_cmos 00:07: setting system clock to 2010-08-25 21:55:03 UTC (1282773303)
[    0.742890] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.742896] EDD information not available.
[    0.745695] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.856091] isapnp: No Plug & Play device found
[    0.856130] Freeing unused kernel memory: 660k freed
[    0.856897] Write protecting the kernel text: 4680k
[    0.856987] Write protecting the kernel read-only data: 1844k
[    0.888142] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    0.902882] udev: starting version 151
[    1.024815] usb 1-5: configuration #1 chosen from 2 choices
[    1.144176] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.261413] pata_sch 0000:00:1f.1: version 0.2
[    1.261527] pata_sch 0000:00:1f.1: setting latency timer to 64
[    1.261880] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.261903] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[    1.284784] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.284838] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.284912] r8169 0000:02:00.0: setting latency timer to 64
[    1.284980]   alloc irq_desc for 24 on node -1
[    1.284990]   alloc kstat_irqs on node -1
[    1.285024] r8169 0000:02:00.0: irq 24 for MSI/MSI-X
[    1.285134] scsi0 : pata_sch
[    1.287628] eth0: RTL8102e at 0xf8096000, 00:24:e8:a7:d6:24, XID 04a00000 IRQ 24
[    1.294631] scsi1 : pata_sch
[    1.295849] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.295862] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.327758] usb 1-6: configuration #1 chosen from 1 choice
[    1.328718] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.440302] usb 1-7: new high speed USB device using ehci_hcd and address 4
[    1.506916] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.506929] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.513337] ata1.00: configured for UDMA/100
[    1.513828] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.514512] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.516187] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.516366] sd 0:0:0:0: [sda] Write Protect is off
[    1.516376] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.516466] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.516961]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.566304] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.585442] usb 1-7: configuration #1 chosen from 1 choice
[    1.611167] Initializing USB Mass Storage driver...
[    1.611619] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.611894] usbcore: registered new interface driver usb-storage
[    1.611907] USB Mass Storage support registered.
[    1.611931] usb-storage: device found at 4
[    1.611938] usb-storage: waiting for device to settle before scanning
[    2.166663] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    6.608544] usb-storage: device scan complete
[    6.610718] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.612049] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    6.616052] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.504248] udev: starting version 151
[   11.526971] Adding 1803256k swap on /dev/sda6.  Priority:-1 extents:1 across:1803256k 
[   11.666780] lp: driver loaded but no devices found
[   12.444618] cfg80211: Calling CRDA to update world regulatory domain
[   12.469600] vga16fb: initializing
[   12.469617] vga16fb: mapped to 0xc00a0000
[   12.470046] fb0: VGA16 VGA frame buffer device
[   12.494515] Linux video capture interface: v2.00
[   12.529869] cdc_acm 1-5:1.1: ttyACM0: USB ACM device
[   12.542437] cdc_wdm 1-5:1.5: cdc-wdm0: USB WDM device
[   12.542841] cdc_acm 1-5:1.3: ttyACM1: USB ACM device
[   12.553452] cdc_wdm 1-5:1.6: cdc-wdm1: USB WDM device
[   12.553662] usbcore: registered new interface driver cdc_wdm
[   12.554935] cdc_acm 1-5:1.9: ttyACM2: USB ACM device
[   12.558952] usbcore: registered new interface driver cdc_acm
[   12.559538] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   12.580510] cfg80211: World regulatory domain updated:
[   12.580522]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.580535]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.580546]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.580557]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.580568]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.580579]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.640293] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.719411] type=1505 audit(1282791315.473:2):  operation="profile_load" pid=608 name="/sbin/dhclient3"
[   12.720441] type=1505 audit(1282791315.477:3):  operation="profile_load" pid=608 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.721003] type=1505 audit(1282791315.477:4):  operation="profile_load" pid=608 name="/usr/lib/connman/scripts/dhclient-script"
[   12.789400] uvcvideo: Found UVC 1.00 device Integrated Webcam (0c45:63e3)
[   12.809077] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input5
[   12.809306] usbcore: registered new interface driver uvcvideo
[   12.809320] USB Video Class driver (v0.1.0)
[   12.825281] usb0: register 'cdc_ether' at usb-0000:00:1d.7-5, CDC Ethernet Device, 02:80:37:ec:02:00
[   12.825382] usbcore: registered new interface driver cdc_ether
[   12.897648] compal-laptop: Identified laptop model 'Dell Mini 10'.
[   12.905853] compal-laptop: driver 0.2.6 successfully loaded.
[   12.906635] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.924844] usbcore: registered new interface driver zaurus
[   12.928338] dell-laptop: Blacklisted hardware detected - not loading
[   13.107101] dell-wmi: No known WMI GUID found
[   13.231509] phy0: Selected rate control algorithm 'minstrel'
[   13.231748] psmouse serio1: ID: 10 00 64
[   13.234329] Registered led device: b43-phy0::tx
[   13.234404] Registered led device: b43-phy0::rx
[   13.234477] Registered led device: b43-phy0::radio
[   13.234708] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   13.304342] Console: switching to colour frame buffer device 80x30
[   13.665741]   alloc irq_desc for 22 on node -1
[   13.665753]   alloc kstat_irqs on node -1
[   13.665775] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.665875] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.671259] type=1505 audit(1282791316.425:5):  operation="profile_replace" pid=765 name="/sbin/dhclient3"
[   13.672462] type=1505 audit(1282791316.429:6):  operation="profile_replace" pid=765 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.673044] type=1505 audit(1282791316.429:7):  operation="profile_replace" pid=765 name="/usr/lib/connman/scripts/dhclient-script"
[   13.693718] type=1505 audit(1282791316.449::  operation="profile_load" pid=768 name="/usr/bin/evince"
[   13.723053] type=1505 audit(1282791316.477:9):  operation="profile_load" pid=768 name="/usr/bin/evince-previewer"
[   13.757538] type=1505 audit(1282791316.513:10):  operation="profile_load" pid=768 name="/usr/bin/evince-thumbnailer"
[   13.820241] type=1505 audit(1282791316.577:11):  operation="profile_load" pid=781 name="/usr/lib/cups/backend/cups-pdf"
[   13.887889] r8169: eth0: link down
[   13.893871] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.936372] hda_codec: ALC269: BIOS auto-probing.
[   13.937094] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   13.958245] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   14.003349] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   14.047089] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   14.047715] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   14.048428] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   14.095222] ADDRCONF(NETDEV_UP): usb0: link is not ready
[   14.281096] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   14.295468] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   14.311228] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   14.311828] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   14.312447] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   14.682336] ppdev: user-space parallel port driver
[   15.279865] CPU0 attaching NULL sched-domain.
[   15.279884] CPU1 attaching NULL sched-domain.
[   15.312186] CPU0 attaching sched-domain:
[   15.312200]  domain 0: span 0-1 level SIBLING
[   15.312211]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   15.312235]   domain 1: span 0-1 level MC
[   15.312245]    groups: 0-1 (cpu_power = 117
[   15.312266] CPU1 attaching sched-domain:
[   15.312275]  domain 0: span 0-1 level SIBLING
[   15.312285]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   15.312307]   domain 1: span 0-1 level MC
[   15.312317]    groups: 0-1 (cpu_power = 117
[   15.366539] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
[   18.648656] CPU0 attaching NULL sched-domain.
[   18.648675] CPU1 attaching NULL sched-domain.
[   18.676193] CPU0 attaching sched-domain:
[   18.676207]  domain 0: span 0-1 level SIBLING
[   18.676218]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   18.676238]   domain 1: span 0-1 level MC
[   18.676247]    groups: 0-1 (cpu_power = 117
[   18.676265] CPU1 attaching sched-domain:
[   18.676274]  domain 0: span 0-1 level SIBLING
[   18.676283]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   18.676303]   domain 1: span 0-1 level MC
[   18.676313]    groups: 0-1 (cpu_power = 117
[   19.772328] hda-intel: Invalid position buffer, using LPIB read method instead.
[   19.772364] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   37.225092] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   37.246413] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   37.261574] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   37.261593] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   37.261603] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 1212.454263] r8169: eth0: link up
[ 1212.455223] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1222.576142] eth0: no IPv6 routers present


(hint) the same as in (4)

6 ) Network configuration
Code:

jake@jake-laptop:~$ sudo lshw -C network
[sudo] password for jake: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:a7:d6:24
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.119 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:24 ioport:2000(size=256) memory:d8410000-d8410fff(prefetchable) memory:d8400000-d840ffff(prefetchable) memory:d8420000-d843ffff(prefetchable)
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
       resources: irq:17 memory:d8000000-d8003fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 00:25:56:31:5f:43
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


7 ) Scan for networks:
Code:

jake@jake-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down


(hint) the same as in (3)
Code:

jake@jake-laptop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

8 ) Ubuntu Version:
Code:

jake@jake-laptop:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

jake@jake-laptop:~$ uname -mr
2.6.32-24-generic i686

10 ) Restarting the network:
Code:

jake@jake-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                           Ignoring unknown interface eth0=eth0.

---

### Post by DavidOfLondon on 2010-08-25
Welcome to "I Use Linux And Assume Everyone Does Too" Land !!

This drove me insane too - the Linux-Speak.

My advice to you as a new user is to devour the manual. It's on the Ubuntu site and should be in your documents folder or other obvious location.
Using the terminal is the most fundamental difference between using Windows or Linux operating systems.

The thing to get your head around is that Linux-based operating systems rely heavily on basic programming language. It sounds terrifying but once you understand the Terminal everything becomes straightforward. Ubuntu has the software centre and Synaptics Package Manager for downloading software which you can then link (if it doesn't automatically) to the Applications tab on the taskbar by right clicking and then selecting the program to add.

But many programs do not have a "plug and go" interface that you're used to in Windows. In other words, you download a program and then think "Ok...now where the f**k did my program go?!" only to discover after much weeping that you have to open the Terminal and type a command prompt.

The good news is that it's extremely difficult to break Ubuntu etc, the file structures (READ THE MANUAL ON THIS OR YOU'RE GONNA HAVE A HARD TIME ADJUSTING) are so segregated that you can mess about with the OS without killing it....touch anything in Windows and the thing explodes.

I cannot stress this enough - the more you get used to using the Terminal the more you will get out of Linux. But if that all frightens you then just be aware that with every passing day the Linux OSs create more and more completely user-friendly programs.

The terminal just makes it quicker to do certain things, it doesn't rule your use of your PC at all.

so....

1. Read about file structures on Linux OSs (Manual)
2. Read about the Ubuntu Software Centre
3. Read about the fundamental commands such as Sudo (manual and google)

You won't be able to alter certain files without knowing how to make yourself the superuser, for example. 

Go with the flow, enjoy it, and pat yourself on the back for refusing to spend a fortune on something you just got for free.

It's quick, it's yours, you can alter it, and if you ever have a problem someone else will have had it and there are millions of people willing to help you.

Good bye, Windows, Hello Liberty!

David.

---

### Post by jakesch on 2010-08-29
So that's it? No one is going to help me with my problem? Wonderful community  :confused:

---

### Post by gordintoronto on 2010-08-30
Your wireless adapter is this one:
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

If you can arrange to temporarily connect by ethernet cable to your router, and run Administration/Hardware Drivers, a driver might appear. (I'm not sure, I have a different Broadcom wireless adapter.) Select it, then click "activate." Then have a look on youtube for the video called "connect to wireless networks in Ubuntu."

If the driver does not appear in Administration/Hardware drivers, Google Broadcom bcm4312 linux and I think you will find what you need. One caution: the "rev 01" is important: wireless manufacturers make major changes under the hood, and call it a different rev, so they don't have to change their advertising.

---

### Post by dineshs on 2010-08-30
+1 to gordintoronto
You may first click Network manager and tick enable wireless
Then as gordintoronto suggested connect via ethernet cable and ensure that wireless(access point) is enabled in router/modem and security is set as explained[ here]("http://ubuntuforums.org/showpost.php?p=9680300&postcount=14")
If your wireless is OK ```
iwconfig 
```should show some ESSID and something similar to Access Point: 00:14:BF:7F:59:B2 
Regarding drivers 
[http://ubuntuforums.org/showthread.php?t=1307995](http://ubuntuforums.org/showthread.php?t=1307995)
says ```
sudo apt-get install bcmwl-kernel-source
```will work
or try try googling

---

