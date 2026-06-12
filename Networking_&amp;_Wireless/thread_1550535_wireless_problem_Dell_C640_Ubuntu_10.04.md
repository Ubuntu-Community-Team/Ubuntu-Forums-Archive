---
title: "wireless problem Dell C640 Ubuntu 10.04"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by captain rhodes on 2010-08-11
[B]Hello

 I've been having some trouble in getting my laptop connected to my wireless router. I previously upgraded from an older version of Ubuntu (Heron) which connected fine using 128bit WEP. My current router is set up as WPA psk. Since upgrading to 10.04 I've tried connecting via this and also WEP again but to no avail. Network manager can detect the network but it keeps asking me again and again for WEP or WPA keys and does not connect.
Ethernet connection is ok.

Many thanks in advance for any help. Let me know if i need to submit any additional info.

Regards.
BM



1 ) Machine Brand and Model (PC/Laptop)[/B]:
     Dell Latitude C640 

**2 ) Wireless Brand, Model and Wireless Chipset**
ben@ben-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 7
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
ben@ben-laptop:~$ lspsub
lspsub: command not found
ben@ben-laptop:~$ lspcsub
lspcsub: command not found
ben@ben-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ben@ben-laptop:~$ 


     Code:
     $ lspci -nn | grep 'Wireless Brand' 
**3 ) check interface:**
     Code:
ben@ben-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:72:f5:c8  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe72:f5c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3321 errors:0 dropped:0 overruns:1 frame:0
          TX packets:2338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3549286 (3.5 MB)  TX bytes:334958 (334.9 KB)
          Interrupt:11 Base address:0xc00 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:7b:8e:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ben@ben-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"mother12"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:5
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ben@ben-laptop:~$ 


([COLOR=Red]hint[/COLOR]) if the Wireless interface name is wlan0 you can also use
     Code:
     $ iwconfig wlan0 
**4 ) Check for modules:**
     Code:
ben@ben-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
michael_mic             1732  4 
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126517  1 orinoco
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia                 33024  1 orinoco_cs
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
joydev                  8708  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674824  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  5 
dell_wmi                1793  0 
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
dcdbas                  5422  0 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24119  1 
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28820  0 
agpgart                31724  3 ttm,drm,intel_agp
ppdev                   5259  0 
video                  17375  0 
output                  1871  1 video
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
3c59x                  31839  0 
mii                     4381  1 3c59x
floppy                 53016  0 
ben@ben-laptop:~$ 


([COLOR=Red]hint[/COLOR]) search for the Wireless module
     Code:
     $ lsmod | grep "wlan_module_name" 
**5 ) Kernel boot messages**
     Code:
[    0.370297] Switching to clocksource tsc
[    0.372689] AppArmor: AppArmor Filesystem Enabled
[    0.372731] pnp: PnP ACPI init
[    0.372770] ACPI: bus type pnp registered
[    0.424351] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.424363] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.424550] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.424561] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.424573] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.425849] pnp 00:04: io resource (0xf000-0xf0fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425859] pnp 00:04: io resource (0xf100-0xf1fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425869] pnp 00:04: io resource (0xf200-0xf2fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425878] pnp 00:04: io resource (0xf400-0xf4fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425887] pnp 00:04: io resource (0xf500-0xf5fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425896] pnp 00:04: io resource (0xf600-0xf6fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425905] pnp 00:04: io resource (0xf800-0xf8fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425914] pnp 00:04: io resource (0xf900-0xf9fe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425923] pnp 00:04: io resource (0xfa00-0xfafe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425932] pnp 00:04: io resource (0xfc00-0xfcfe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425942] pnp 00:04: io resource (0xfd00-0xfdfe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425951] pnp 00:04: io resource (0xfe00-0xfefe) overlaps 0000:00:1e.0 BAR 13 (0xe000-0xffff), disabling
[    0.425961] pnp 00:04: mem resource (0xfa000000-0xfbffffff) overlaps 0000:00:1e.0 BAR 14 (0xf4000000-0xfbffffff), disabling
[    0.548137] pnp: PnP ACPI: found 17 devices
[    0.548144] ACPI: ACPI bus type pnp unregistered
[    0.548156] PnPBIOS: Disabled by ACPI PNP
[    0.548187] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.548197] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.548205] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.548213] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.548221] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.548229] system 00:00: iomem range 0x1fff0000-0x1fffffff has been reserved
[    0.548238] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.548246] system 00:00: iomem range 0xfff80000-0xffffffff has been reserved
[    0.548266] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.548286] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.548297] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.548305] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.548334] system 00:09: ioport range 0x900-0x91f has been reserved
[    0.548344] system 00:09: ioport range 0x3f0-0x3f1 has been reserved
[    0.548372] system 00:0f: ioport range 0xbf40-0xbf5f has been reserved
[    0.548382] system 00:0f: ioport range 0xbf20-0xbf3f has been reserved
[    0.548400] system 00:10: iomem range 0xfebffc00-0xfebfffff has been reserved
[    0.583417] pci 0000:02:00.0: BAR 6: address space collision on of device [0xf9000000-0xf901ffff]
[    0.583470] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.583478] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.583488] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.583498] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.583539] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.583545] pci 0000:02:01.0:   IO window: 0x00e000-0x00e0ff
[    0.583555] pci 0000:02:01.0:   IO window: 0x00e400-0x00e4ff
[    0.583564] pci 0000:02:01.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.583574] pci 0000:02:01.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.583584] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.583591] pci 0000:02:01.1:   IO window: 0x00e800-0x00e8ff
[    0.583600] pci 0000:02:01.1:   IO window: 0x00f000-0x00f0ff
[    0.583609] pci 0000:02:01.1:   PREFETCH window: 0x24000000-0x27ffffff
[    0.583619] pci 0000:02:01.1:   MEM window: 0x30000000-0x33ffffff
[    0.583629] pci 0000:02:03.0: CardBus bridge, secondary bus 0000:0b
[    0.583635] pci 0000:02:03.0:   IO window: 0x00f400-0x00f4ff
[    0.583644] pci 0000:02:03.0:   IO window: 0x00f800-0x00f8ff
[    0.583654] pci 0000:02:03.0:   PREFETCH window: 0x28000000-0x2bffffff
[    0.583663] pci 0000:02:03.0:   MEM window: 0x34000000-0x37ffffff
[    0.583673] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.583681] pci 0000:00:1e.0:   IO window: 0xe000-0xffff
[    0.583692] pci 0000:00:1e.0:   MEM window: 0xf4000000-0xfbffffff
[    0.583702] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x2dffffff
[    0.583735] pci 0000:00:1e.0: setting latency timer to 64
[    0.583752] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.584480] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.584488] PCI: setting IRQ 11 as level-triggered
[    0.584499] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.584523] pci 0000:02:01.1: enabling device (0000 -> 0003)
[    0.584534] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.585225] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.585232] PCI: setting IRQ 5 as level-triggered
[    0.585241] pci 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.585255] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.585263] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.585273] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.585280] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.585287] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.585294] pci_bus 0000:02: resource 0 io:  [0xe000-0xffff]
[    0.585301] pci_bus 0000:02: resource 1 mem: [0xf4000000-0xfbffffff]
[    0.585308] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x2dffffff]
[    0.585315] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.585321] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.585328] pci_bus 0000:03: resource 0 io:  [0xe000-0xe0ff]
[    0.585335] pci_bus 0000:03: resource 1 io:  [0xe400-0xe4ff]
[    0.585341] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.585348] pci_bus 0000:03: resource 3 mem: [0xf4000000-0xf7ffffff]
[    0.585355] pci_bus 0000:07: resource 0 io:  [0xe800-0xe8ff]
[    0.585362] pci_bus 0000:07: resource 1 io:  [0xf000-0xf0ff]
[    0.585369] pci_bus 0000:07: resource 2 pref mem [0x24000000-0x27ffffff]
[    0.585376] pci_bus 0000:07: resource 3 mem: [0x30000000-0x33ffffff]
[    0.585383] pci_bus 0000:0b: resource 0 io:  [0xf400-0xf4ff]
[    0.585389] pci_bus 0000:0b: resource 1 io:  [0xf800-0xf8ff]
[    0.585396] pci_bus 0000:0b: resource 2 pref mem [0x28000000-0x2bffffff]
[    0.585403] pci_bus 0000:0b: resource 3 mem: [0x34000000-0x37ffffff]
[    0.585492] NET: Registered protocol family 2
[    0.585761] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.586525] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.586666] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.586800] TCP: Hash tables configured (established 16384 bind 16384)
[    0.586806] TCP reno registered
[    0.586981] NET: Registered protocol family 1
[    0.587067] pci 0000:01:00.0: Boot video device
[    0.587722] Marking TSC unstable due to cpufreq changes
[    0.587878] cpufreq-nforce2: No nForce2 chipset.
[    0.587922] Scanning for low memory corruption every 60 seconds
[    0.588084] audit: initializing netlink socket (disabled)
[    0.588105] type=2000 audit(1281518053.585:1): initialized
[    0.605007] Trying to unpack rootfs image as initramfs...
[    0.610536] Switching to clocksource acpi_pm
[    0.624536] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.632686] VFS: Disk quotas dquot_6.5.2
[    0.632848] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.633929] fuse init (API version 7.13)
[    0.634084] msgmni has been set to 978
[    0.634457] alg: No test for stdrng (krng)
[    0.634568] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.634573] io scheduler noop registered
[    0.634577] io scheduler anticipatory registered
[    0.634580] io scheduler deadline registered
[    0.634645] io scheduler cfq registered (default)
[    0.634825] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.634868] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.635701] ACPI: AC Adapter [AC] (off-line)
[    0.635860] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.636666] ACPI: Lid Switch [LID]
[    0.636746] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.636754] ACPI: Power Button [PBTN]
[    0.636828] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.636833] ACPI: Sleep Button [SBTN]
[    0.637280] processor LNXCPU:00: registered as cooling_device0
[    0.734588] thermal LNXTHERM:01: registered as thermal_zone0
[    0.734609] ACPI: Thermal Zone [THM] (47 C)
[    0.776337] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.776726] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.777366] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.777518] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.777529] serial 0000:00:1f.6: PCI INT B disabled
[    0.779181] brd: module loaded
[    0.779971] loop: module loaded
[    0.784142] isapnp: Scanning for PnP cards...
[    0.789822] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.790038] ata_piix 0000:00:1f.1: version 2.13
[    0.790063] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.085220] ACPI: Battery Slot [BAT1] (battery absent)
[    1.085640] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    1.085650] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.085745] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.088060] scsi0 : ata_piix
[    1.088270] scsi1 : ata_piix
[    1.098377] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.098383] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.099318] Fixed MDIO Bus: probed
[    1.099388] PPP generic driver version 2.4.2
[    1.099521] tun: Universal TUN/TAP device driver, 1.6
[    1.099525] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.099683] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.099716] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.099738] uhci_hcd: USB Universal Host Controller Interface driver
[    1.099812] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.099828] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.099835] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.099892] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.099931] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    1.108195] usb usb1: configuration #1 chosen from 1 choice
[    1.108260] hub 1-0:1.0: USB hub found
[    1.108278] hub 1-0:1.0: 2 ports detected
[    1.108472] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13S2M] at 0x60,0x64 irq 1,12
[    1.124750] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.124772] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.125077] mice: PS/2 mouse device common for all mice
[    1.125418] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.125445] rtc0: alarms up to one day, 114 bytes nvram
[    1.125676] device-mapper: uevent: version 1.0.3
[    1.125895] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.129320] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.132137] device-mapper: multipath: version 1.1.0 loaded
[    1.132145] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.140219] EISA: Probing bus 0 at eisa.0
[    1.140252] EISA: Detected 0 cards.
[    1.144332] cpuidle: using governor ladder
[    1.144413] cpuidle: using governor menu
[    1.145183] TCP cubic registered
[    1.145393] NET: Registered protocol family 10
[    1.146081] lo: Disabled Privacy Extensions
[    1.146637] NET: Registered protocol family 17
[    1.146727] Using IPI No-Shortcut mode
[    1.146895] PM: Resume from disk failed.
[    1.146915] registered taskstats version 1
[    1.147173]   Magic number: 6:957:221
[    1.147310] rtc_cmos 00:07: setting system clock to 2010-08-11 09:14:16 UTC (1281518056)
[    1.147316] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.147318] EDD information not available.
[    1.164745] ACPI: Battery Slot [BAT0] (battery present)
[    1.304502] ata1.00: ATA-5: IC25N040ATCS05-0, CS4OA63A, max UDMA/100
[    1.304509] ata1.00: 78140160 sectors, multi 8: LBA 
[    1.307918] ata2.00: ATAPI: Samsung CD-RW/DVD-ROM SN-308B, U003, max MWDMA2
[    1.317101] ata2.00: configured for MWDMA2
[    1.317228] ata1.00: configured for UDMA/100
[    1.487786] Freeing initrd memory: 7786k freed
[    1.546263] isapnp: No Plug & Play device found
[    1.546538] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS05-0 CS4O PQ: 0 ANSI: 5
[    1.546863] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.547143] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.547225] sd 0:0:0:0: [sda] Write Protect is off
[    1.547231] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.547272] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.547554]  sda:
[    1.548375] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-308B U003 PQ: 0 ANSI: 5
[    1.553783] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.553789] Uniform CD-ROM driver Revision: 3.20
[    1.553961] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.554062] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.564041]  sda1 sda2 < sda5 >
[    1.586815] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.586840] Freeing unused kernel memory: 660k freed
[    1.587972] Write protecting the kernel text: 4680k
[    1.588062] Write protecting the kernel read-only data: 1840k
[    1.624748] udev: starting version 151
[    2.020325] Floppy drive(s): fd0 is 1.44M
[    2.038041] FDC 0 is a post-1991 82077
[    2.043408] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    2.043418] 3c59x 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.043441] 3c59x: Donald Becker and others.
[    2.043451] 0000:02:00.0: 3Com PCI 3c905C Tornado at e0840c00.
[    2.277591] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   15.838282] udev: starting version 151
[   15.897174] Adding 1490936k swap on /dev/sda5.  Priority:-1 extents:1 across:1490936k 
[   16.026164] lp: driver loaded but no devices found
[   16.213864] parport_pc 00:0e: reported by Plug and Play ACPI
[   16.213925] parport0: PC-style at 0x378 (0x77, irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.237005] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:15/LNXVIDEO:00/input/input5
[   16.237301] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.300435] lp0: using parport0 (interrupt-driven).
[   16.312940] ppdev: user-space parallel port driver
[   16.501386] Linux agpgart interface v0.103
[   16.536242] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.562115] intel_rng: FWH not detected
[   16.703581] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   16.786628] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[   16.871316] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.993091] dell-wmi: No known WMI GUID found
[   17.010320] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:012a]
[   17.010347] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   17.010351] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   17.010358] yenta_cardbus 0000:02:01.0: TI: mfunc 0x01261222, devctl 0x64
[   17.015339] [drm] Initialized drm 1.1.0 20060810
[   17.016957] type=1505 audit(1281518072.368:2):  operation="profile_load" pid=544 name="/sbin/dhclient3"
[   17.017737] type=1505 audit(1281518072.368:3):  operation="profile_load" pid=544 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.018158] type=1505 audit(1281518072.368:4):  operation="profile_load" pid=544 name="/usr/lib/connman/scripts/dhclient-script"
[   17.240541] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0418, PCI irq 11
[   17.240548] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   17.240562] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.240568] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xe000-0xffff: clean.
[   17.241315] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.241320] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   17.251089] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:012a]
[   17.251113] yenta_cardbus 0000:02:01.1: Using CSCINT to route CSC interrupts to PCI
[   17.251117] yenta_cardbus 0000:02:01.1: Routing CardBus interrupts to PCI
[   17.251125] yenta_cardbus 0000:02:01.1: TI: mfunc 0x01261222, devctl 0x64
[   17.369605] [drm] radeon defaulting to kernel modesetting.
[   17.369613] [drm] radeon kernel modesetting enabled.
[   17.369702] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.390953] [drm] radeon: Initializing kernel modesetting.
[   17.391056] [drm] register mmio base: 0xFCFF0000
[   17.391060] [drm] register mmio size: 65536
[   17.391406] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   17.391437] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   17.391461] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   17.391486] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   17.391519] [drm] radeon: VRAM 64M
[   17.391522] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   17.391525] [drm] radeon: GTT 64M
[   17.391528] [drm] radeon: GTT from 0xE8000000 to 0xEBFFFFFF
[   17.391564] [drm] radeon: irq initialized.
[   17.391722] [drm] Detected VRAM RAM=64M, BAR=128M
[   17.391729] [drm] RAM width 64bits DDR
[   17.394231] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x9b4cb1, caps: 0x884793/0x0
[   17.394242] serio: Synaptics pass-through port at isa0060/serio1/input0
[   17.397960] [TTM] Zone  kernel: Available graphics memory: 254610 kiB.
[   17.397999] [drm] radeon: 32M of VRAM memory ready
[   17.398003] [drm] radeon: 64M of GTT memory ready.
[   17.398267] [drm] radeon: cp idle (0x00008383)
[   17.398464] [drm] Loading R100 Microcode
[   17.399010] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   17.441186] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   17.447951] [drm] radeon: ring at 0x00000000E8000000
[   17.447977] [drm] ring test succeeded in 1 usecs
[   17.480517] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0418, PCI irq 11
[   17.480525] yenta_cardbus 0000:02:01.1: Socket status: 30000006
[   17.480539] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.480547] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xe000-0xffff: clean.
[   17.481270] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.481277] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   17.488886] yenta_cardbus 0000:02:03.0: CardBus bridge found [12a3:ab01]
[   17.488910] yenta_cardbus 0000:02:03.0: Enabling burst memory read transactions
[   17.488918] yenta_cardbus 0000:02:03.0: Using CSCINT to route CSC interrupts to PCI
[   17.488922] yenta_cardbus 0000:02:03.0: Routing CardBus interrupts to PCI
[   17.488930] yenta_cardbus 0000:02:03.0: TI: mfunc 0x01000002, devctl 0x60
[   17.491728] [drm] radeon: ib pool ready.
[   17.491873] [drm] ib test succeeded in 0 usecs
[   17.493801] [drm] Panel ID String: QDI141X1LH03            
[   17.493808] [drm] Panel Size 1024x768
[   17.494063] [drm] Default TV standard: NTSC
[   17.494067] [drm] 27.000000000 MHz TV ref clk
[   17.494070] [drm] No TV DAC info found in BIOS
[   17.494075] [drm] Default TV standard: NTSC
[   17.494078] [drm] 27.000000000 MHz TV ref clk
[   17.494271] [drm] Radeon Display Connectors
[   17.494275] [drm] Connector 0:
[   17.494278] [drm]   VGA
[   17.494283] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   17.494286] [drm]   Encoders:
[   17.494288] [drm]     CRT1: INTERNAL_DAC1
[   17.494291] [drm] Connector 1:
[   17.494294] [drm]   LVDS
[   17.494296] [drm]   Encoders:
[   17.494298] [drm]     LCD1: INTERNAL_LVDS
[   17.494301] [drm] Connector 2:
[   17.494303] [drm]   S-video
[   17.494306] [drm]   Encoders:
[   17.494308] [drm]     TV1: INTERNAL_DAC2
[   17.642074] [drm] fb mappable at 0xE0040000
[   17.642080] [drm] vram apper at 0xE0000000
[   17.642083] [drm] size 786432
[   17.642086] [drm] fb depth is 8
[   17.642089] [drm]    pitch is 1024
[   17.643384] type=1505 audit(1281518072.992:5):  operation="profile_load" pid=665 name="/usr/share/gdm/guest-session/Xsession"
[   17.667022] type=1505 audit(1281518073.016:6):  operation="profile_replace" pid=668 name="/sbin/dhclient3"
[   17.667829] type=1505 audit(1281518073.016:7):  operation="profile_replace" pid=668 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.681711] fb0: radeondrmfb frame buffer device
[   17.681717] registered panic notifier
[   17.681729] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   17.689288] type=1505 audit(1281518073.040:8):  operation="profile_replace" pid=668 name="/usr/lib/connman/scripts/dhclient-script"
[   17.715572] vga16fb: initializing
[   17.715581] vga16fb: mapped to 0xc00a0000
[   17.715590] vga16fb: not registering due to another framebuffer present
[   17.720405] yenta_cardbus 0000:02:03.0: ISA IRQ mask 0x0000, PCI irq 5
[   17.720413] yenta_cardbus 0000:02:03.0: Socket status: 30000010
[   17.720428] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.720435] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xe000-0xffff: clean.
[   17.721173] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.721179] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   17.785651] type=1505 audit(1281518073.136:9):  operation="profile_load" pid=671 name="/usr/bin/evince"
[   17.913076] eth0:  setting half-duplex.
[   17.913929] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.942884] type=1505 audit(1281518073.292:10):  operation="profile_load" pid=671 name="/usr/bin/evince-previewer"
[   17.982263] type=1505 audit(1281518073.332:11):  operation="profile_load" pid=671 name="/usr/bin/evince-thumbnailer"
[   18.048085] Console: switching to colour frame buffer device 128x48
[   18.054655] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x100-0x3af: clean.
[   18.055906] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.057004] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   18.058234] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.058771] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   18.059192] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   18.060160] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   18.062073] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x820-0x8ff: clean.
[   18.062164] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xc00-0xcf7: clean.
[   18.062864] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xa00-0xaff: clean.
[   18.213301] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   18.213331] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   18.380128] pcmcia_socket pcmcia_socket2: pccard: PCMCIA card inserted into slot 2
[   18.704086] pcmcia_socket pcmcia_socket2: cs: memory probe 0xf4000000-0xfbffffff: excluding 0xf4000000-0xf8ffffff
[   18.708954] pcmcia 2.0: pcmcia: registering new device pcmcia2.0
[   18.721653] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   18.726281] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.726822] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.726904] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.728924] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.834592] cfg80211: Calling CRDA to update world regulatory domain
[   18.874288] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   18.884969] cfg80211: World regulatory domain updated:
[   18.884977]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.884982]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.884987]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.884992]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.884997]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.885002]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.894360] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   18.976144] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   18.976267] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   18.976273] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   19.032069] intel8x0_measure_ac97_clock: measured 55100 usecs (2648 samples)
[   19.032076] intel8x0: clocking to 48000
[   19.168039] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   19.278162] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   19.278297] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   19.278303] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   19.278307] orinoco_cs 2.0: Ad-hoc demo mode supported
[   19.278310] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   19.278314] orinoco_cs 2.0: WEP supported, 104-bit key
[   19.278317] orinoco_cs 2.0: WPA-PSK supported
[   19.368112] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.988236] psmouse serio2: ID: 10 00 64
[   22.414866] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/serio2/input/input7
[   67.531821] eth1: Lucent/Agere firmware doesn't support manual roaming
[   72.842785] eth1: Lucent/Agere firmware doesn't support manual roaming
[   78.126908] eth1: Lucent/Agere firmware doesn't support manual roaming
[   83.494651] eth1: Lucent/Agere firmware doesn't support manual roaming
[   88.789962] eth1: Lucent/Agere firmware doesn't support manual roaming
[   94.130196] eth1: Lucent/Agere firmware doesn't support manual roaming
[   99.434004] eth1: Lucent/Agere firmware doesn't support manual roaming
[  104.799486] eth1: Lucent/Agere firmware doesn't support manual roaming
[  110.116530] eth1: Lucent/Agere firmware doesn't support manual roaming
[  115.517268] eth1: Lucent/Agere firmware doesn't support manual roaming
[  120.846197] eth1: Lucent/Agere firmware doesn't support manual roaming
[  126.294980] eth1: Lucent/Agere firmware doesn't support manual roaming
[  155.912736] eth0:  setting full-duplex.
[  155.912852] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  166.236100] eth0: no IPv6 routers present
ben@ben-laptop:~$
([COLOR=Red]hint[/COLOR]) the same as in (4)

**6 ) Network configuration**
     Code:
1e.0 BAR 14 (0xf4000000-0xfbffffff), disabling
[    0.548137] pnp: PnP ACPI: found 17 devices
[    0.548144] ACPI: ACPI bus type pnp unregistered
[    0.548156] PnPBIOS: Disabled by ACPI PNP
[    0.548187] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.548197] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.548205] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.548213] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.548221] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.548229] system 00:00: iomem range 0x1fff0000-0x1fffffff has been reserved
[    0.548238] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.548246] system 00:00: iomem range 0xfff80000-0xffffffff has been reserved
[    0.548266] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.548286] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.548297] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.548305] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.548334] system 00:09: ioport range 0x900-0x91f has been reserved
[    0.548344] system 00:09: ioport range 0x3f0-0x3f1 has been reserved
[    0.548372] system 00:0f: ioport range 0xbf40-0xbf5f has been reserved
[    0.548382] system 00:0f: ioport range 0xbf20-0xbf3f has been reserved
[    0.548400] system 00:10: iomem range 0xfebffc00-0xfebfffff has been reserved
[    0.583417] pci 0000:02:00.0: BAR 6: address space collision on of device [0xf9000000-0xf901ffff]
[    0.583470] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.583478] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.583488] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.583498] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xe7ffffff
[    0.583539] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.583545] pci 0000:02:01.0:   IO window: 0x00e000-0x00e0ff
[    0.583555] pci 0000:02:01.0:   IO window: 0x00e400-0x00e4ff
[    0.583564] pci 0000:02:01.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.583574] pci 0000:02:01.0:   MEM window: 0xf4000000-0xf7ffffff
[    0.583584] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.583591] pci 0000:02:01.1:   IO window: 0x00e800-0x00e8ff
[    0.583600] pci 0000:02:01.1:   IO window: 0x00f000-0x00f0ff
[    0.583609] pci 0000:02:01.1:   PREFETCH window: 0x24000000-0x27ffffff
[    0.583619] pci 0000:02:01.1:   MEM window: 0x30000000-0x33ffffff
[    0.583629] pci 0000:02:03.0: CardBus bridge, secondary bus 0000:0b
[    0.583635] pci 0000:02:03.0:   IO window: 0x00f400-0x00f4ff
[    0.583644] pci 0000:02:03.0:   IO window: 0x00f800-0x00f8ff
[    0.583654] pci 0000:02:03.0:   PREFETCH window: 0x28000000-0x2bffffff
[    0.583663] pci 0000:02:03.0:   MEM window: 0x34000000-0x37ffffff
[    0.583673] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.583681] pci 0000:00:1e.0:   IO window: 0xe000-0xffff
[    0.583692] pci 0000:00:1e.0:   MEM window: 0xf4000000-0xfbffffff
[    0.583702] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x2dffffff
[    0.583735] pci 0000:00:1e.0: setting latency timer to 64
[    0.583752] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.584480] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.584488] PCI: setting IRQ 11 as level-triggered
[    0.584499] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.584523] pci 0000:02:01.1: enabling device (0000 -> 0003)
[    0.584534] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.585225] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.585232] PCI: setting IRQ 5 as level-triggered
[    0.585241] pci 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.585255] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.585263] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.585273] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.585280] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.585287] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xe7ffffff]
[    0.585294] pci_bus 0000:02: resource 0 io:  [0xe000-0xffff]
[    0.585301] pci_bus 0000:02: resource 1 mem: [0xf4000000-0xfbffffff]
[    0.585308] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x2dffffff]
[    0.585315] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.585321] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.585328] pci_bus 0000:03: resource 0 io:  [0xe000-0xe0ff]
[    0.585335] pci_bus 0000:03: resource 1 io:  [0xe400-0xe4ff]
[    0.585341] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.585348] pci_bus 0000:03: resource 3 mem: [0xf4000000-0xf7ffffff]
[    0.585355] pci_bus 0000:07: resource 0 io:  [0xe800-0xe8ff]
[    0.585362] pci_bus 0000:07: resource 1 io:  [0xf000-0xf0ff]
[    0.585369] pci_bus 0000:07: resource 2 pref mem [0x24000000-0x27ffffff]
[    0.585376] pci_bus 0000:07: resource 3 mem: [0x30000000-0x33ffffff]
[    0.585383] pci_bus 0000:0b: resource 0 io:  [0xf400-0xf4ff]
[    0.585389] pci_bus 0000:0b: resource 1 io:  [0xf800-0xf8ff]
[    0.585396] pci_bus 0000:0b: resource 2 pref mem [0x28000000-0x2bffffff]
[    0.585403] pci_bus 0000:0b: resource 3 mem: [0x34000000-0x37ffffff]
[    0.585492] NET: Registered protocol family 2
[    0.585761] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.586525] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.586666] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.586800] TCP: Hash tables configured (established 16384 bind 16384)
[    0.586806] TCP reno registered
[    0.586981] NET: Registered protocol family 1
[    0.587067] pci 0000:01:00.0: Boot video device
[    0.587722] Marking TSC unstable due to cpufreq changes
[    0.587878] cpufreq-nforce2: No nForce2 chipset.
[    0.587922] Scanning for low memory corruption every 60 seconds
[    0.588084] audit: initializing netlink socket (disabled)
[    0.588105] type=2000 audit(1281518053.585:1): initialized
[    0.605007] Trying to unpack rootfs image as initramfs...
[    0.610536] Switching to clocksource acpi_pm
[    0.624536] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.632686] VFS: Disk quotas dquot_6.5.2
[    0.632848] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.633929] fuse init (API version 7.13)
[    0.634084] msgmni has been set to 978
[    0.634457] alg: No test for stdrng (krng)
[    0.634568] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.634573] io scheduler noop registered
[    0.634577] io scheduler anticipatory registered
[    0.634580] io scheduler deadline registered
[    0.634645] io scheduler cfq registered (default)
[    0.634825] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.634868] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.635701] ACPI: AC Adapter [AC] (off-line)
[    0.635860] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.636666] ACPI: Lid Switch [LID]
[    0.636746] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.636754] ACPI: Power Button [PBTN]
[    0.636828] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.636833] ACPI: Sleep Button [SBTN]
[    0.637280] processor LNXCPU:00: registered as cooling_device0
[    0.734588] thermal LNXTHERM:01: registered as thermal_zone0
[    0.734609] ACPI: Thermal Zone [THM] (47 C)
[    0.776337] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.776726] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.777366] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.777518] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.777529] serial 0000:00:1f.6: PCI INT B disabled
[    0.779181] brd: module loaded
[    0.779971] loop: module loaded
[    0.784142] isapnp: Scanning for PnP cards...
[    0.789822] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.790038] ata_piix 0000:00:1f.1: version 2.13
[    0.790063] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.085220] ACPI: Battery Slot [BAT1] (battery absent)
[    1.085640] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    1.085650] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.085745] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.088060] scsi0 : ata_piix
[    1.088270] scsi1 : ata_piix
[    1.098377] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.098383] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.099318] Fixed MDIO Bus: probed
[    1.099388] PPP generic driver version 2.4.2
[    1.099521] tun: Universal TUN/TAP device driver, 1.6
[    1.099525] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.099683] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.099716] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.099738] uhci_hcd: USB Universal Host Controller Interface driver
[    1.099812] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    1.099828] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.099835] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.099892] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.099931] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    1.108195] usb usb1: configuration #1 chosen from 1 choice
[    1.108260] hub 1-0:1.0: USB hub found
[    1.108278] hub 1-0:1.0: 2 ports detected
[    1.108472] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.124750] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.124772] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.125077] mice: PS/2 mouse device common for all mice
[    1.125418] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.125445] rtc0: alarms up to one day, 114 bytes nvram
[    1.125676] device-mapper: uevent: version 1.0.3
[    1.125895] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.129320] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.132137] device-mapper: multipath: version 1.1.0 loaded
[    1.132145] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.140219] EISA: Probing bus 0 at eisa.0
[    1.140252] EISA: Detected 0 cards.
[    1.144332] cpuidle: using governor ladder
[    1.144413] cpuidle: using governor menu
[    1.145183] TCP cubic registered
[    1.145393] NET: Registered protocol family 10
[    1.146081] lo: Disabled Privacy Extensions
[    1.146637] NET: Registered protocol family 17
[    1.146727] Using IPI No-Shortcut mode
[    1.146895] PM: Resume from disk failed.
[    1.146915] registered taskstats version 1
[    1.147173]   Magic number: 6:957:221
[    1.147310] rtc_cmos 00:07: setting system clock to 2010-08-11 09:14:16 UTC (1281518056)
[    1.147316] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.147318] EDD information not available.
[    1.164745] ACPI: Battery Slot [BAT0] (battery present)
[    1.304502] ata1.00: ATA-5: IC25N040ATCS05-0, CS4OA63A, max UDMA/100
[    1.304509] ata1.00: 78140160 sectors, multi 8: LBA 
[    1.307918] ata2.00: ATAPI: Samsung CD-RW/DVD-ROM SN-308B, U003, max MWDMA2
[    1.317101] ata2.00: configured for MWDMA2
[    1.317228] ata1.00: configured for UDMA/100
[    1.487786] Freeing initrd memory: 7786k freed
[    1.546263] isapnp: No Plug & Play device found
[    1.546538] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS05-0 CS4O PQ: 0 ANSI: 5
[    1.546863] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.547143] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.547225] sd 0:0:0:0: [sda] Write Protect is off
[    1.547231] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.547272] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.547554]  sda:
[    1.548375] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SN-308B U003 PQ: 0 ANSI: 5
[    1.553783] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.553789] Uniform CD-ROM driver Revision: 3.20
[    1.553961] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.554062] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.564041]  sda1 sda2 < sda5 >
[    1.586815] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.586840] Freeing unused kernel memory: 660k freed
[    1.587972] Write protecting the kernel text: 4680k
[    1.588062] Write protecting the kernel read-only data: 1840k
[    1.624748] udev: starting version 151
[    2.020325] Floppy drive(s): fd0 is 1.44M
[    2.038041] FDC 0 is a post-1991 82077
[    2.043408] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    2.043418] 3c59x 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.043441] 3c59x: Donald Becker and others.
[    2.043451] 0000:02:00.0: 3Com PCI 3c905C Tornado at e0840c00.
[    2.277591] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   15.838282] udev: starting version 151
[   15.897174] Adding 1490936k swap on /dev/sda5.  Priority:-1 extents:1 across:1490936k 
[   16.026164] lp: driver loaded but no devices found
[   16.213864] parport_pc 00:0e: reported by Plug and Play ACPI
[   16.213925] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.237005] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:15/LNXVIDEO:00/input/input5
[   16.237301] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.300435] lp0: using parport0 (interrupt-driven).
[   16.312940] ppdev: user-space parallel port driver
[   16.501386] Linux agpgart interface v0.103
[   16.536242] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.562115] intel_rng: FWH not detected
[   16.703581] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   16.786628] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[   16.871316] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.993091] dell-wmi: No known WMI GUID found
[   17.010320] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:012a]
[   17.010347] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   17.010351] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   17.010358] yenta_cardbus 0000:02:01.0: TI: mfunc 0x01261222, devctl 0x64
[   17.015339] [drm] Initialized drm 1.1.0 20060810
[   17.016957] type=1505 audit(1281518072.368:2):  operation="profile_load" pid=544 name="/sbin/dhclient3"
[   17.017737] type=1505 audit(1281518072.368:3):  operation="profile_load" pid=544 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.018158] type=1505 audit(1281518072.368:4):  operation="profile_load" pid=544 name="/usr/lib/connman/scripts/dhclient-script"
[   17.240541] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0418, PCI irq 11
[   17.240548] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   17.240562] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.240568] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xe000-0xffff: clean.
[   17.241315] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.241320] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   17.251089] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:012a]
[   17.251113] yenta_cardbus 0000:02:01.1: Using CSCINT to route CSC interrupts to PCI
[   17.251117] yenta_cardbus 0000:02:01.1: Routing CardBus interrupts to PCI
[   17.251125] yenta_cardbus 0000:02:01.1: TI: mfunc 0x01261222, devctl 0x64
[   17.369605] [drm] radeon defaulting to kernel modesetting.
[   17.369613] [drm] radeon kernel modesetting enabled.
[   17.369702] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.390953] [drm] radeon: Initializing kernel modesetting.
[   17.391056] [drm] register mmio base: 0xFCFF0000
[   17.391060] [drm] register mmio size: 65536
[   17.391406] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   17.391437] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   17.391461] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   17.391486] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   17.391519] [drm] radeon: VRAM 64M
[   17.391522] [drm] radeon: VRAM from 0x00000000 to 0x03FFFFFF
[   17.391525] [drm] radeon: GTT 64M
[   17.391528] [drm] radeon: GTT from 0xE8000000 to 0xEBFFFFFF
[   17.391564] [drm] radeon: irq initialized.
[   17.391722] [drm] Detected VRAM RAM=64M, BAR=128M
[   17.391729] [drm] RAM width 64bits DDR
[   17.394231] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x9b4cb1, caps: 0x884793/0x0
[   17.394242] serio: Synaptics pass-through port at isa0060/serio1/input0
[   17.397960] [TTM] Zone  kernel: Available graphics memory: 254610 kiB.
[   17.397999] [drm] radeon: 32M of VRAM memory ready
[   17.398003] [drm] radeon: 64M of GTT memory ready.
[   17.398267] [drm] radeon: cp idle (0x00008383)
[   17.398464] [drm] Loading R100 Microcode
[   17.399010] platform radeon_cp.0: firmware: requesting radeon/R100_cp.bin
[   17.441186] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   17.447951] [drm] radeon: ring at 0x00000000E8000000
[   17.447977] [drm] ring test succeeded in 1 usecs
[   17.480517] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0418, PCI irq 11
[   17.480525] yenta_cardbus 0000:02:01.1: Socket status: 30000006
[   17.480539] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.480547] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xe000-0xffff: clean.
[   17.481270] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.481277] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   17.488886] yenta_cardbus 0000:02:03.0: CardBus bridge found [12a3:ab01]
[   17.488910] yenta_cardbus 0000:02:03.0: Enabling burst memory read transactions
[   17.488918] yenta_cardbus 0000:02:03.0: Using CSCINT to route CSC interrupts to PCI
[   17.488922] yenta_cardbus 0000:02:03.0: Routing CardBus interrupts to PCI
[   17.488930] yenta_cardbus 0000:02:03.0: TI: mfunc 0x01000002, devctl 0x60
[   17.491728] [drm] radeon: ib pool ready.
[   17.491873] [drm] ib test succeeded in 0 usecs
[   17.493801] [drm] Panel ID String: QDI141X1LH03            
[   17.493808] [drm] Panel Size 1024x768
[   17.494063] [drm] Default TV standard: NTSC
[   17.494067] [drm] 27.000000000 MHz TV ref clk
[   17.494070] [drm] No TV DAC info found in BIOS
[   17.494075] [drm] Default TV standard: NTSC
[   17.494078] [drm] 27.000000000 MHz TV ref clk
[   17.494271] [drm] Radeon Display Connectors
[   17.494275] [drm] Connector 0:
[   17.494278] [drm]   VGA
[   17.494283] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   17.494286] [drm]   Encoders:
[   17.494288] [drm]     CRT1: INTERNAL_DAC1
[   17.494291] [drm] Connector 1:
[   17.494294] [drm]   LVDS
[   17.494296] [drm]   Encoders:
[   17.494298] [drm]     LCD1: INTERNAL_LVDS
[   17.494301] [drm] Connector 2:
[   17.494303] [drm]   S-video
[   17.494306] [drm]   Encoders:
[   17.494308] [drm]     TV1: INTERNAL_DAC2
[   17.642074] [drm] fb mappable at 0xE0040000
[   17.642080] [drm] vram apper at 0xE0000000
[   17.642083] [drm] size 786432
[   17.642086] [drm] fb depth is 8
[   17.642089] [drm]    pitch is 1024
[   17.643384] type=1505 audit(1281518072.992:5):  operation="profile_load" pid=665 name="/usr/share/gdm/guest-session/Xsession"
[   17.667022] type=1505 audit(1281518073.016:6):  operation="profile_replace" pid=668 name="/sbin/dhclient3"
[   17.667829] type=1505 audit(1281518073.016:7):  operation="profile_replace" pid=668 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.681711] fb0: radeondrmfb frame buffer device
[   17.681717] registered panic notifier
[   17.681729] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   17.689288] type=1505 audit(1281518073.040:8):  operation="profile_replace" pid=668 name="/usr/lib/connman/scripts/dhclient-script"
[   17.715572] vga16fb: initializing
[   17.715581] vga16fb: mapped to 0xc00a0000
[   17.715590] vga16fb: not registering due to another framebuffer present
[   17.720405] yenta_cardbus 0000:02:03.0: ISA IRQ mask 0x0000, PCI irq 5
[   17.720413] yenta_cardbus 0000:02:03.0: Socket status: 30000010
[   17.720428] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   17.720435] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xe000-0xffff: clean.
[   17.721173] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   17.721179] yenta_cardbus 0000:02:03.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x2dffffff
[   17.785651] type=1505 audit(1281518073.136:9):  operation="profile_load" pid=671 name="/usr/bin/evince"
[   17.913076] eth0:  setting half-duplex.
[   17.913929] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.942884] type=1505 audit(1281518073.292:10):  operation="profile_load" pid=671 name="/usr/bin/evince-previewer"
[   17.982263] type=1505 audit(1281518073.332:11):  operation="profile_load" pid=671 name="/usr/bin/evince-thumbnailer"
[   18.048085] Console: switching to colour frame buffer device 128x48
[   18.054655] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x100-0x3af: clean.
[   18.055906] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.057004] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   18.058234] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.058771] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   18.059192] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   18.060160] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   18.062073] pcmcia_socket pcmcia_socket2: cs: IO port probe 0x820-0x8ff: clean.
[   18.062164] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xc00-0xcf7: clean.
[   18.062864] pcmcia_socket pcmcia_socket2: cs: IO port probe 0xa00-0xaff: clean.
[   18.213301] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   18.213331] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   18.380128] pcmcia_socket pcmcia_socket2: pccard: PCMCIA card inserted into slot 2
[   18.704086] pcmcia_socket pcmcia_socket2: cs: memory probe 0xf4000000-0xfbffffff: excluding 0xf4000000-0xf8ffffff
[   18.708954] pcmcia 2.0: pcmcia: registering new device pcmcia2.0
[   18.721653] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   18.726281] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.726822] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   18.726904] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   18.728924] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.834592] cfg80211: Calling CRDA to update world regulatory domain
[   18.874288] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   18.884969] cfg80211: World regulatory domain updated:
[   18.884977]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.884982]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.884987]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.884992]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.884997]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.885002]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.894360] orinoco_cs 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   18.976144] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   18.976267] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   18.976273] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   19.032069] intel8x0_measure_ac97_clock: measured 55100 usecs (2648 samples)
[   19.032076] intel8x0: clocking to 48000
[   19.168039] orinoco_cs 2.0: firmware: requesting agere_sta_fw.bin
[   19.278162] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   19.278297] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   19.278303] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   19.278307] orinoco_cs 2.0: Ad-hoc demo mode supported
[   19.278310] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   19.278314] orinoco_cs 2.0: WEP supported, 104-bit key
[   19.278317] orinoco_cs 2.0: WPA-PSK supported
[   19.368112] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.988236] psmouse serio2: ID: 10 00 64
[   22.414866] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/serio2/input/input7
[   67.531821] eth1: Lucent/Agere firmware doesn't support manual roaming
[   72.842785] eth1: Lucent/Agere firmware doesn't support manual roaming
[   78.126908] eth1: Lucent/Agere firmware doesn't support manual roaming
[   83.494651] eth1: Lucent/Agere firmware doesn't support manual roaming
[   88.789962] eth1: Lucent/Agere firmware doesn't support manual roaming
[   94.130196] eth1: Lucent/Agere firmware doesn't support manual roaming
[   99.434004] eth1: Lucent/Agere firmware doesn't support manual roaming
[  104.799486] eth1: Lucent/Agere firmware doesn't support manual roaming
[  110.116530] eth1: Lucent/Agere firmware doesn't support manual roaming
[  115.517268] eth1: Lucent/Agere firmware doesn't support manual roaming
[  120.846197] eth1: Lucent/Agere firmware doesn't support manual roaming
[  126.294980] eth1: Lucent/Agere firmware doesn't support manual roaming
[  155.912736] eth0:  setting full-duplex.
[  155.912852] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  166.236100] eth0: no IPv6 routers present
ben@ben-laptop:~$ clear

ben@ben-laptop:~$ sudo lshw -C network
[sudo] password for ben: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:0d:56:72:f5:c8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.102 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:2c000000-2c01ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:7b:8e:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
ben@ben-laptop:~$ 


**7 ) Scan for networks:**
     Code:
ben@ben-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

ben@ben-laptop:~$ 


([COLOR=Red]hint[/COLOR]) the same as in (3)
     Code:
     $ iwlist scan wlan0 
**8 ) Ubuntu Version: **
     Code:
en@ben-laptop:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS


**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
2.6.32-24-generic i686
**10 ) Restarting the network:**
ben@ben-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
ben@ben-laptop:~$
Add this information to the post, even is the output is and error, and m

---

### Post by grahammechanical on 2010-08-11
Are you using the correct password? The dialog box does not tell you that you put in an incorrect password. It just reappears asking for the password or to authenticate. I had this problem. Enter the wrong password and the system remembers it. In this way I reset the password for the WPS-PSK key to my logon password, which repeatedly failed. Re-entering the correct WPS-PSK key corrected the problem. I may be wrong. This may be too simple an answer.

Regards.

---

### Post by captain rhodes on 2010-08-11
It's definately the correct password.
I've tried the following so far - 

Changing the ssid and WPA and WEP password on the router
Changing the broadcast channel of the router

Changing the WPA and WEP on the laptop
Re-installing Ubuntu 10.04 and starting from scratch

Still no luck

A previous version of Ubuntu, Heron worked fine on the same laptop with the same wireless hardware using network manager (set up for 128bit WEP)

Cheers

---

### Post by larrydag on 2010-08-15
I'm having the exact same problem.  The only thing I can think of is it is a driver issue.  It detects the wifi network but just doesn't appear to connect.  I even tried disabling all security.

---

