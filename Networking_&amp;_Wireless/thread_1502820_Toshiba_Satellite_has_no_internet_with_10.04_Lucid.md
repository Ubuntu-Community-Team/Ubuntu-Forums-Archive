---
title: "Toshiba Satellite has no internet with 10.04 Lucid"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by Samwise Hamfast on 2010-06-06
Dear All,

I am posting this thread because I really need advice on connecting my Toshiba Satellite Pro L20 to the internet. This is a dual boot machine and I have no problems connecting with the XP 'side'. However, I would like to connect my Ubuntu Lucid Lynx since I really want to use Ubuntu in preference to Windows. So my installation is exactly as it came of the disk except that I have read the WifiDocs Wireless Trouble Shooting Guide and tuned off ipv6 (whatever that is) in Firefox and I've made a file called /etc/modprobe.d/aliases (because it didn't exist before - or I couldn't find it) and put in the suggested lines to turn off ipv6. I've turned off ipv6 in the 'Edit Connections' network settings. I've also altered the grub file by putting in pci=noacpi, whatever that means, (and have got rid of the splash screen as well at the same time) as suggested.

All to no avail! The wireless card can see my network and sometimes other networks are listed but I can't ping my router but I can ping the loopback on my card.

I've read the HOWTO post a Wireless issue (ticket) message and here is the suggested output (apologies for the length but it seems to contain all the information). The last response about ignoring the unknown interface eth1 seems very strange since earlier on in the responses it seem to indicate that the wireless connection is associated with eth1.

I'd very much like to solve the problem - otherwise I shall have to go back to using Windows and there are so many applications I want to use in Ubuntu. In the longer term I'd like to convert the whole family to Ubuntu but if I can't even connect to the internet, no one is even willing to listen!

I'd appreciate any advice - I'm stuck and don't know what to try next.

Sincerely,

Samwise H

***************************************************************************************************************************
fred@fred-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
fred@fred-laptop:~$ lsusb
Bus 003 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**************************************************************************************************************************
fred@fred-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:fe:58:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:b2:03:21  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:feb2:321/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:2 overruns:0 frame:0
          TX packets:675 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26633 (26.6 KB)
          Interrupt:10 Base address:0x2000 Memory:b0102000-b0102fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42643 (42.6 KB)  TX bytes:42643 (42.6 KB)
**************************************************************************************************************************
fred@fred-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"vdoma"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:81:E0:84   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/100  Signal level=-53 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2
***************************************************************************************************************************
fred@fred-laptop:~$ lsmod
Module                  Size  Used by
arc4                    1153  2 
lib80211_crypt_wep      2667  1 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
joydev                  8708  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
i915                  282354  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 i915
drm                   162471  4 i915,drm_kms_helper
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ipw2200               135216  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
intel_agp              24177  2 i915
soundcore               6620  1 snd
libipw                 39896  1 ipw2200
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lib80211                5046  3 lib80211_crypt_wep,ipw2200,libipw
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
**************************************************************************************************************************
fred@fred-laptop:~$ PART OF THE OUTPUT TO THE COMMAND 'dmesg' - NOT ALL OF THE OUTPUT WOULD FIT INTO THE TERMINAL WINDOW (buffer?) SO I'VE JUST COPIED WHAT WAS DISPLAYED:
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f670
[    0.000000]   HighMem  0x0001f670 -> 0x0001f670
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001f670
[    0.000000] On node 0 totalpages: 128523
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123555 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0x0 is invalid
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:c0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127518
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=e47c5170-6ad3-43c4-ba52-d7ff0de6fbf0 ro pci=noacpi
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2572480 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 490836k/514496k available (4673k kernel code, 22880k reserved, 2122k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xdfe70000 - 0xff7fe000   ( 505 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xdf670000   ( 502 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1729.477 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.95 BogoMIPS (lpj=6917908)
[    0.004136] Security Framework initialized
[    0.004218] AppArmor: AppArmor initialized
[    0.004280] Mount-cache hash table entries: 512
[    0.004470] Initializing cgroup subsys ns
[    0.004529] Initializing cgroup subsys cpuacct
[    0.004589] Initializing cgroup subsys memory
[    0.004653] Initializing cgroup subsys devices
[    0.004710] Initializing cgroup subsys freezer
[    0.004767] Initializing cgroup subsys net_cls
[    0.004846] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004935] CPU: L2 cache: 2048K
[    0.004993] mce: CPU supports 5 MCE banks
[    0.005056] CPU0: Thermal monitoring enabled (TM2)
[    0.005120] Performance Events: p6 PMU driver.
[    0.005221] ... version:                0
[    0.005278] ... bit width:              32
[    0.005334] ... generic registers:      2
[    0.005390] ... value mask:             00000000ffffffff
[    0.005449] ... max period:             000000007fffffff
[    0.005506] ... fixed-purpose events:   0
[    0.005562] ... event mask:             0000000000000003
[    0.005622] Checking 'hlt' instruction... OK.
[    0.020969] SMP alternatives: switching to UP code
[    0.028884] Freeing SMP alternatives: 19k freed
[    0.028947] ACPI: Core revision 20090903
[    0.036699] ACPI: setting ELCR to 0e00 (from 0c00)
[    0.040009] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040071] ftrace: allocating 21771 entries in 43 pages
[    0.044076] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.044147] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.048001] Brought up 1 CPUs
[    0.048001] Total of 1 processors activated (3458.95 BogoMIPS).
[    0.048001] CPU0 attaching NULL sched-domain.
[    0.048001] devtmpfs: initialized
[    0.048001] regulator: core version 0.5
[    0.048001] Time:  5:24:02  Date: 06/06/10
[    0.048001] NET: Registered protocol family 16
[    0.048001] EISA bus registered
[    0.048001] ACPI: bus type pci registered
[    0.048001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.048001] PCI: MCFG area at e0000000 reserved in E820
[    0.048001] PCI: Using MMCONFIG for extended config space
[    0.048001] PCI: Using configuration type 1 for base access
[    0.048001] bio: create slab <bio-0> at 0
[    0.048407] ACPI: EC: Look up EC in DSDT
[    0.056638] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.188060] ACPI: Interpreter enabled
[    0.188122] ACPI: (supports S0 S3 S4 S5)
[    0.188319] ACPI: Using PIC for interrupt routing
[    0.191677] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.191960] ACPI: No dock devices found.
[    0.192055] vgaarb: loaded
[    0.192244] SCSI subsystem initialized
[    0.192344] libata version 3.00 loaded.
[    0.192423] usbcore: registered new interface driver usbfs
[    0.192495] usbcore: registered new interface driver hub
[    0.192579] usbcore: registered new device driver usb
[    0.192772] ACPI: WMI: Mapper loaded
[    0.192827] PCI: Probing PCI hardware
[    0.192882] PCI: Probing PCI hardware (bus 00)
[    0.192963] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0080000-0xb00fffff]
[    0.192969] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.192974] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.192980] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0000000-0xb003ffff]
[    0.193012] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]
[    0.193153] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.193216] pci 0000:00:1c.0: PME# disabled
[    0.193360] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.193423] pci 0000:00:1c.1: PME# disabled
[    0.193567] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.193630] pci 0000:00:1c.2: PME# disabled
[    0.193749] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.193811] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.193879] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0040000-0xb00403ff]
[    0.193940] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.194003] pci 0000:00:1d.7: PME# disabled
[    0.194164] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]
[    0.194173] pci 0000:00:1e.2: reg 14 io port: [0x18c0-0x18ff]
[    0.194182] pci 0000:00:1e.2: reg 18 32bit mmio: [0xb0040800-0xb00409ff]
[    0.194190] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xb0040400-0xb00404ff]
[    0.194228] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.194291] pci 0000:00:1e.2: PME# disabled
[    0.194383] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.194392] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]
[    0.194440] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.194503] pci 0000:00:1e.3: PME# disabled
[    0.194646] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.194656] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.194737] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.194801] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 1600-167f
[    0.194864] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0060-006f
[    0.194965] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.194973] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.194981] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.194991] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.194999] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.195033] pci 0000:00:1f.2: PME# supported from D3hot
[    0.195094] pci 0000:00:1f.2: PME# disabled
[    0.195210] pci 0000:00:1f.3: reg 20 io port: [0x20a0-0x20bf]
[    0.195298] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.195304] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.195312] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.195368] pci 0000:00:1c.1: bridge io port: [0x00-0xfff]
[    0.195373] pci 0000:00:1c.1: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.195381] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.195437] pci 0000:00:1c.2: bridge io port: [0x00-0xfff]
[    0.195442] pci 0000:00:1c.2: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.195451] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.195501] pci 0000:06:01.0: reg 10 32bit mmio: [0xb0100000-0xb0100fff]
[    0.195529] pci 0000:06:01.0: supports D1 D2
[    0.195532] pci 0000:06:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.195596] pci 0000:06:01.0: PME# disabled
[    0.195697] pci 0000:06:02.0: reg 10 io port: [0x3000-0x30ff]
[    0.195707] pci 0000:06:02.0: reg 14 32bit mmio: [0xb0101000-0xb01010ff]
[    0.195767] pci 0000:06:02.0: supports D1 D2
[    0.195770] pci 0000:06:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.195834] pci 0000:06:02.0: PME# disabled
[    0.195937] pci 0000:06:04.0: reg 10 32bit mmio: [0xb0102000-0xb0102fff]
[    0.196026] pci 0000:06:04.0: PME# supported from D0 D3hot D3cold
[    0.196089] pci 0000:06:04.0: PME# disabled
[    0.196203] pci 0000:00:1e.0: transparent bridge
[    0.196263] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.196268] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.196368] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.197022] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    0.197082] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.197142] pci 0000:00:1c.0: BAR 15: can't allocate resource
[    0.197201] pci 0000:00:1c.1: BAR 13: can't allocate resource
[    0.197261] pci 0000:00:1c.1: BAR 14: can't allocate resource
[    0.197320] pci 0000:00:1c.1: BAR 15: can't allocate resource
[    0.197379] pci 0000:00:1c.2: BAR 13: can't allocate resource
[    0.197438] pci 0000:00:1c.2: BAR 14: can't allocate resource
[    0.197498] pci 0000:00:1c.2: BAR 15: can't allocate resource
[    0.197724] NetLabel: Initializing
[    0.197779] NetLabel:  domain hash size = 128
[    0.197834] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197904] NetLabel:  unlabeled traffic allowed by default
[    0.198124] hpet clockevent registered
[    0.198127] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.198194] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.198375] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.204011] Switching to clocksource tsc
[    0.206328] AppArmor: AppArmor Filesystem Enabled
[    0.206403] pnp: PnP ACPI init
[    0.206470] ACPI: bus type pnp registered
[    0.207922] pnp: PnP ACPI: found 8 devices
[    0.207978] ACPI: ACPI bus type pnp unregistered
[    0.208001] PnPBIOS: Disabled by ACPI PNP
[    0.208017] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.208081] system 00:01: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.208145] system 00:01: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.208209] system 00:01: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.208272] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.208335] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.208399] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.208466] system 00:04: ioport range 0x680-0x6ff has been reserved
[    0.208528] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.208589] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.208651] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.208713] system 00:04: ioport range 0x1600-0x167f has been reserved
[    0.243541] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.243603] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
[    0.243666] pci 0000:00:1c.0:   MEM window: 0x24000000-0x241fffff
[    0.243729] pci 0000:00:1c.0:   PREFETCH window: 0x00000024200000-0x000000243fffff
[    0.243814] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0a
[    0.243875] pci 0000:00:1c.1:   IO window: 0x5000-0x5fff
[    0.243945] pci 0000:00:1c.1:   MEM window: 0x24400000-0x245fffff
[    0.244009] pci 0000:00:1c.1:   PREFETCH window: 0x00000024600000-0x000000247fffff
[    0.244094] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.244155] pci 0000:00:1c.2:   IO window: 0x6000-0x6fff
[    0.244218] pci 0000:00:1c.2:   MEM window: 0x24800000-0x249fffff
[    0.244281] pci 0000:00:1c.2:   PREFETCH window: 0x00000024a00000-0x00000024bfffff
[    0.244368] pci 0000:06:01.0: CardBus bridge, secondary bus 0000:07
[    0.244429] pci 0000:06:01.0:   IO window: 0x003400-0x0034ff
[    0.244492] pci 0000:06:01.0:   IO window: 0x003800-0x0038ff
[    0.244554] pci 0000:06:01.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.244619] pci 0000:06:01.0:   MEM window: 0x28000000-0x2bffffff
[    0.244682] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.244744] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.244806] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff
[    0.244869] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.244944] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.245012] pci 0000:00:1c.0: setting latency timer to 64
[    0.245022] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.245089] pci 0000:00:1c.1: setting latency timer to 64
[    0.245099] pci 0000:00:1c.2: enabling device (0000 -> 0003)
[    0.245166] pci 0000:00:1c.2: setting latency timer to 64
[    0.245175] pci 0000:00:1e.0: setting latency timer to 64
[    0.245196] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.245199] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.245202] pci_bus 0000:09: resource 0 io:  [0x4000-0x4fff]
[    0.245206] pci_bus 0000:09: resource 1 mem: [0x24000000-0x241fffff]
[    0.245209] pci_bus 0000:09: resource 2 pref mem [0x24200000-0x243fffff]
[    0.245212] pci_bus 0000:0a: resource 0 io:  [0x5000-0x5fff]
[    0.245215] pci_bus 0000:0a: resource 1 mem: [0x24400000-0x245fffff]
[    0.245219] pci_bus 0000:0a: resource 2 pref mem [0x24600000-0x247fffff]
[    0.245222] pci_bus 0000:02: resource 0 io:  [0x6000-0x6fff]
[    0.245225] pci_bus 0000:02: resource 1 mem: [0x24800000-0x249fffff]
[    0.245228] pci_bus 0000:02: resource 2 pref mem [0x24a00000-0x24bfffff]
[    0.245232] pci_bus 0000:06: resource 0 io:  [0x3000-0x3fff]
[    0.245235] pci_bus 0000:06: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.245238] pci_bus 0000:06: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.245241] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.245244] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.245248] pci_bus 0000:07: resource 0 io:  [0x3400-0x34ff]
[    0.245251] pci_bus 0000:07: resource 1 io:  [0x3800-0x38ff]
[    0.245254] pci_bus 0000:07: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.245257] pci_bus 0000:07: resource 3 mem: [0x28000000-0x2bffffff]
[    0.245294] NET: Registered protocol family 2
[    0.245444] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.245796] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.245980] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.246147] TCP: Hash tables configured (established 16384 bind 16384)
[    0.246209] TCP reno registered
[    0.246330] NET: Registered protocol family 1
[    0.246402] pci 0000:00:02.0: Boot video device
[    0.246530] Simple Boot Flag at 0x36 set to 0x1
[    0.246665] cpufreq-nforce2: No nForce2 chipset.
[    0.246743] Scanning for low memory corruption every 60 seconds
[    0.246932] audit: initializing netlink socket (disabled)
[    0.247003] type=2000 audit(1275801842.243:1): initialized
[    0.259060] Trying to unpack rootfs image as initramfs...
[    0.272097] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.278001] VFS: Disk quotas dquot_6.5.2
[    0.278127] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.278866] fuse init (API version 7.13)
[    0.279021] msgmni has been set to 959
[    0.284177] alg: No test for stdrng (krng)
[    0.284316] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284395] io scheduler noop registered
[    0.284451] io scheduler anticipatory registered
[    0.284507] io scheduler deadline registered
[    0.284610] io scheduler cfq registered (default)
[    0.284845]   alloc irq_desc for 16 on node -1
[    0.284847]   alloc kstat_irqs on node -1
[    0.284861] pcieport 0000:00:1c.0: irq 16 for MSI/MSI-X
[    0.284874] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.285029]   alloc irq_desc for 17 on node -1
[    0.285031]   alloc kstat_irqs on node -1
[    0.285040] pcieport 0000:00:1c.1: irq 17 for MSI/MSI-X
[    0.285050] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.285201]   alloc irq_desc for 18 on node -1
[    0.285203]   alloc kstat_irqs on node -1
[    0.285212] pcieport 0000:00:1c.2: irq 18 for MSI/MSI-X
[    0.285222] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.285331] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.285443] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.300388] ACPI: AC Adapter [ACAD] (on-line)
[    0.300544] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.316156] ACPI: Lid Switch [LID]
[    0.316309] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.316394] ACPI: Power Button [PWRB]
[    0.316502] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.316580] ACPI: Power Button [PWRF]
[    0.316924] Marking TSC unstable due to TSC halts in idle
[    0.317046] processor LNXCPU:00: registered as cooling_device0
[    0.321076] Switching to clocksource hpet
[    0.348394] thermal LNXTHERM:01: registered as thermal_zone0
[    0.348474] ACPI: Thermal Zone [THRM] (47 C)
[    0.350251] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.351814] brd: module loaded
[    0.356425] ACPI: Battery Slot [BAT1] (battery absent)
[    0.356505] isapnp: Scanning for PnP cards...
[    0.362515] loop: module loaded
[    0.362684] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.362897] ata_piix 0000:00:1f.2: version 2.13
[    0.362920] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.516353] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.520046] scsi0 : ata_piix
[    0.520273] scsi1 : ata_piix
[    0.520368] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    0.520431] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    0.520912] Fixed MDIO Bus: probed
[    0.521007] PPP generic driver version 2.4.2
[    0.521145] tun: Universal TUN/TAP device driver, 1.6
[    0.521204] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.521372] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.521480] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.521485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.521577] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.521690] ehci_hcd 0000:00:1d.7: debug port 1
[    0.525629] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.528418] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xb0040000
[    0.548429] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.548683] usb usb1: configuration #1 chosen from 1 choice
[    0.548780] hub 1-0:1.0: USB hub found
[    0.548844] hub 1-0:1.0: 8 ports detected
[    0.548986] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.549067] uhci_hcd: USB Universal Host Controller Interface driver
[    0.549195] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.549199] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.549301] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.549412] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    0.549572] usb usb2: configuration #1 chosen from 1 choice
[    0.549658] hub 2-0:1.0: USB hub found
[    0.550711] hub 2-0:1.0: 2 ports detected
[    0.550822] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.550826] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.550923] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.551025] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    0.551179] usb usb3: configuration #1 chosen from 1 choice
[    0.551265] hub 3-0:1.0: USB hub found
[    0.551325] hub 3-0:1.0: 2 ports detected
[    0.551487] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.604369] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.604443] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.604691] mice: PS/2 mouse device common for all mice
[    0.604914] rtc_cmos 00:05: RTC can wake from S4
[    0.605020] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.605105] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.605315] device-mapper: uevent: version 1.0.3
[    0.605518] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.608062] device-mapper: multipath: version 1.1.0 loaded
[    0.608122] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.608340] EISA: Probing bus 0 at eisa.0
[    0.608402] Cannot allocate resource for EISA slot 1
[    0.608460] Cannot allocate resource for EISA slot 2
[    0.608518] Cannot allocate resource for EISA slot 3
[    0.608575] Cannot allocate resource for EISA slot 4
[    0.608633] Cannot allocate resource for EISA slot 5
[    0.608690] Cannot allocate resource for EISA slot 6
[    0.608755] EISA: Detected 0 cards.
[    0.612303] cpuidle: using governor ladder
[    0.612444] cpuidle: using governor menu
[    0.613007] TCP cubic registered
[    0.613241] NET: Registered protocol family 10
[    0.613802] lo: Disabled Privacy Extensions
[    0.614199] NET: Registered protocol family 17
[    0.614559] Using IPI No-Shortcut mode
[    0.614711] PM: Resume from disk failed.
[    0.614732] registered taskstats version 1
[    0.615140]   Magic number: 14:351:415
[    0.615301] rtc_cmos 00:05: setting system clock to 2010-06-06 05:24:03 UTC (1275801843)
[    0.615382] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.615441] EDD information not available.
[    0.637163] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.705268] ata2.00: ATAPI: DV-W28EADT, 1.AA, max UDMA/33
[    0.705496] ata1.00: ATA-6: TOSHIBA MK6032GSX, AS311G, max UDMA/100
[    0.705559] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.712685] ata2.00: configured for UDMA/33
[    0.713468] ata1.00: configured for UDMA/100
[    0.726554] Freeing initrd memory: 7773k freed
[    0.907459] isapnp: No Plug & Play device found
[    0.907723] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6032GS AS31 PQ: 0 ANSI: 5
[    0.908056] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.908343] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    0.908474] sd 0:0:0:0: [sda] Write Protect is off
[    0.908533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.908561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.908848]  sda:
[    0.909617] scsi 1:0:0:0: CD-ROM            TEAC     DV-W28EADT       1.AA PQ: 0 ANSI: 5
[    0.913728] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.913809] Uniform CD-ROM driver Revision: 3.20
[    0.913982] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.914044] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.940549]  sda1 sda2 < sda5 sda6 >
[    0.991601] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.991673] Freeing unused kernel memory: 656k freed
[    0.992224] Write protecting the kernel text: 4676k
[    0.992322] Write protecting the kernel read-only data: 1840k
[    1.009036] udev: starting version 151
[    1.112074] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.206891] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.206982] 8139cp 0000:06:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.211152] 8139too Fast Ethernet driver 0.9.28
[    1.212605] eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:fe:58:11, IRQ 11
[    1.288260] usb 3-1: configuration #1 chosen from 1 choice
[    1.305874] usbcore: registered new interface driver hiddev
[    1.319609] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    1.319907] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1/input0
[    1.320029] usbcore: registered new interface driver usbhid
[    1.320181] usbhid: v2.6:USB HID core driver
[    1.467555] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   14.568469] udev: starting version 151
[   14.649667] Adding 634528k swap on /dev/sda6.  Priority:-1 extents:1 across:634528k 
[   14.797232] lp: driver loaded but no devices found
[   15.087451] type=1505 audit(1275798257.970:2):  operation="profile_load" pid=417 name="/sbin/dhclient3"
[   15.088170] type=1505 audit(1275798257.972:3):  operation="profile_load" pid=417 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.088549] type=1505 audit(1275798257.972:4):  operation="profile_load" pid=417 name="/usr/lib/connman/scripts/dhclient-script"
[   15.409738] lib80211: common routines for IEEE802.11 drivers
[   15.409742] lib80211_crypt: registered algorithm 'NULL'
[   15.410064] Linux agpgart interface v0.103
[   15.416877] intel_rng: FWH not detected
[   15.451621] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.451625] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.453542] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   15.453995] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   15.490617] yenta_cardbus 0000:06:01.0: CardBus bridge found [1179:ff31]
[   15.490646] yenta_cardbus 0000:06:01.0: Using CSCINT to route CSC interrupts to PCI
[   15.490649] yenta_cardbus 0000:06:01.0: Routing CardBus interrupts to PCI
[   15.490656] yenta_cardbus 0000:06:01.0: TI: mfunc 0x015c1d22, devctl 0x44
[   15.492713] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   15.528092] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   15.528097] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.529544] eth0: link down
[   15.529776] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.645860] [drm] Initialized drm 1.1.0 20060810
[   15.720583] yenta_cardbus 0000:06:01.0: ISA IRQ mask 0x00f8, PCI irq 10
[   15.720590] yenta_cardbus 0000:06:01.0: Socket status: 30000007
[   15.720595] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #08
[   15.720607] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   15.720612] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   15.720847] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   15.720851] yenta_cardbus 0000:06:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   15.723878] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   15.723934] ipw2200 0000:06:04.0: firmware: requesting ipw2200-bss.fw
[   15.728885] i915 0000:00:02.0: setting latency timer to 64
[   15.747241] [drm] set up 7M of stolen space
[   15.925312] type=1505 audit(1275798258.808:5):  operation="profile_load" pid=636 name="/usr/share/gdm/guest-session/Xsession"
[   15.928981] type=1505 audit(1275798258.812:6):  operation="profile_replace" pid=637 name="/sbin/dhclient3"
[   15.929680] type=1505 audit(1275798258.812:7):  operation="profile_replace" pid=637 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.930062] type=1505 audit(1275798258.812:8):  operation="profile_replace" pid=637 name="/usr/lib/connman/scripts/dhclient-script"
[   15.941377] type=1505 audit(1275798258.824:9):  operation="profile_load" pid=640 name="/usr/bin/evince"
[   15.997450] type=1505 audit(1275798258.880:10):  operation="profile_load" pid=640 name="/usr/bin/evince-previewer"
[   16.010770] type=1505 audit(1275798258.892:11):  operation="profile_load" pid=640 name="/usr/bin/evince-thumbnailer"
[   16.158979] [drm] initialized overlay support
[   16.614557] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   16.628018] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   16.628028] synaptics: Toshiba Satellite PRO L20                detected, limiting rate to 40pps.
[   16.640121] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   16.641867] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.642597] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.643238] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   16.647349] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.668775] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   16.924961] ppdev: user-space parallel port driver
[   17.048883] fb0: inteldrmfb frame buffer device
[   17.048887] registered panic notifier
[   17.048897] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   17.048961] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   17.054310] vga16fb: initializing
[   17.054314] vga16fb: mapped to 0xc00a0000
[   17.054318] vga16fb: not registering due to another framebuffer present
[   17.184440] Console: switching to colour frame buffer device 128x48
[   17.368055] intel8x0_measure_ac97_clock: measured 54087 usecs (2606 samples)
[   17.368060] intel8x0: clocking to 48000
[   27.432028] eth1: no IPv6 routers present
[  222.925790] lib80211_crypt: registered algorithm 'WEP'
***************************************************************************************************************************
fred@fred-laptop:~$ sudo lshw -C network
[sudo] password for fred: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:fe:58:11
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:3000(size=256) memory:b0101000-b01010ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:b2:03:21
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.2.3 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:10 memory:b0102000-b0102fff
**************************************************************************************************************************
fred@fred-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:50:81:E0:84
                    ESSID:"\x00"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=75/100  Signal level=-54 dBm  
                    Extra: Last beacon: 3016ms ago
***************************************************************************************************************************
fred@fred-laptop:~$ lsb_release -d
Description:	Ubuntu 10.04 LTS
***************************************************************************************************************************
fred@fred-laptop:~$ uname -mr
2.6.32-21-generic i686
***************************************************************************************************************************
fred@fred-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for fred: 
 * Reconfiguring network interfaces...                                                                                     Ignoring unknown interface eth1=eth1.
***************************************************************************************************************************

---

