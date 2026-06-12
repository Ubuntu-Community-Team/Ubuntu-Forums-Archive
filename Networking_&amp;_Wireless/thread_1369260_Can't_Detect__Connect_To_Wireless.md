---
title: "Can't Detect / Connect To Wireless"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by br0wnie on 2009-12-31
So my friend came over today, showed me his duel boot laptop system [he has the choice to boot up in XP or Ubuntu] and I wanted to do this as well. So, I install it and all that, it loads up fine [says one of my drivers might break in the future? It looked like my C drive or whatever] but anyway, so I couldn't connect to the internet. I clicked on the thing where the wireless normally shows and it said "Wireless: Disconnected" I searched around, look through folders, etc, and am unable to connect. My friend is able to connect and all that but yeah. I run Vista or Ubuntu, my laptop is a XPS M1730, here is all the information you guys asked for in the sticky [some of them didn't work, I tried but yeah] so this is the best information I can provide:

**_1. Machine Brand and Mode_l**

Machine Brand: Dell
Model: XPS M1730

[U]
**2. Wireless Brand, Model and Wieless Chipset: **[/U] 

**$ lspci**

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
03:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8700M GT] (rev a1)
04:00.0 3D controller: nVidia Corporation G84 [GeForce 8700M GT] (rev a1)
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
05:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
05:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
05:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

**$ lsusb**

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c251 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**$ lspci -nn | grep 'Wireless Brand'     **
{Nothing showed up}

Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

_**3. Check Interface:**_

**$ ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:23:ae:04:88:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

**$ iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


$ iwconfig wlan0

wlan0     No such device

_**4. Check for Modules**_

[B]$lsmod
[/B] 
Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
ppdev                   6688  0 
bnep                   12060  2 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
joydev                 10272  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
b43                   122136  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
uvcvideo               59080  0 
mac80211              181236  1 b43
ip_tables              11692  1 iptable_filter
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
sdhci_pci               7100  0 
soundcore               7264  1 snd
ricoh_mmc               3676  0 
sdhci                  17472  1 sdhci_pci
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
serio_raw               5280  0 
videodev               36736  1 uvcvideo
cfg80211               93052  2 b43,mac80211
dell_wmi                2564  0 
v4l1_compat            14496  2 uvcvideo,videodev
dell_laptop             8128  0 
x_tables               16544  1 ip_tables
lp                      8964  0 
led_class               4096  2 b43,sdhci
btusb                  11856  2 
shpchp                 32272  0 
parport                35340  2 ppdev,lp
dcdbas                  7292  1 dell_laptop
usbhid                 38208  0 
ohci1394               29900  0 
ssb                    35300  1 b43
tg3                   109600  0 
ieee1394               86596  1 ohci1394
video                  19380  0 
output                  2780  1 video
intel_agp              27484  0 
agpgart                34988  1 intel_agp

**$ lsmod | grep "wlan_module_name"**
{Nothing came up}

_**5) Kernel boot messages**_
[B]
$ dmseg [/B]
{It seems like it cut out information, because it cut out all the other commands I had written previously, and it makes it so that I can't scroll up anymore past the top of this information I am about to provide}

[    0.247065] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 9 10 11)
[    0.247158] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.247253] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.247347] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.247430] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.247570] SCSI subsystem initialized
[    0.247585] libata version 3.00 loaded.
[    0.247585] usbcore: registered new interface driver usbfs
[    0.247585] usbcore: registered new interface driver hub
[    0.247585] usbcore: registered new device driver usb
[    0.247585] ACPI: WMI: Mapper loaded
[    0.247585] PCI: Using ACPI for IRQ routing
[    0.260006] Bluetooth: Core ver 2.15
[    0.260017] NET: Registered protocol family 31
[    0.260017] Bluetooth: HCI device and connection manager initialized
[    0.260017] Bluetooth: HCI socket layer initialized
[    0.260017] NetLabel: Initializing
[    0.260017] NetLabel:  domain hash size = 128
[    0.260017] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.260027] NetLabel:  unlabeled traffic allowed by default
[    0.260051] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.260055] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.276006] pnp: PnP ACPI init
[    0.276013] ACPI: bus type pnp registered
[    0.289666] pnp 00:09: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.289669] pnp 00:09: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.289742] pnp 00:0a: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.289746] pnp 00:0a: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.289748] pnp 00:0a: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.307150] pnp: PnP ACPI: found 12 devices
[    0.307152] ACPI: ACPI bus type pnp unregistered
[    0.307155] PnPBIOS: Disabled by ACPI PNP
[    0.307163] system 00:05: ioport range 0xc80-0xcff could not be reserved
[    0.307169] system 00:08: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.307174] system 00:09: ioport range 0x900-0x97f has been reserved
[    0.307176] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.307181] system 00:0a: ioport range 0xf400-0xf4fe has been reserved
[    0.307183] system 00:0a: ioport range 0x1080-0x10bf has been reserved
[    0.307185] system 00:0a: ioport range 0x10c0-0x10df has been reserved
[    0.307188] system 00:0a: ioport range 0x809-0x809 has been reserved
[    0.307192] system 00:0b: iomem range 0x0-0x9efff could not be reserved
[    0.307195] system 00:0b: iomem range 0x9f000-0x9ffff could not be reserved
[    0.307197] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.307199] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.307202] system 00:0b: iomem range 0x100000-0xbfe71fff could not be reserved
[    0.307204] system 00:0b: iomem range 0xbfe72000-0xbfefffff has been reserved
[    0.307206] system 00:0b: iomem range 0xbff00000-0xbfffffff has been reserved
[    0.307208] system 00:0b: iomem range 0xffe00000-0xffffffff has been reserved
[    0.307211] system 00:0b: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.307213] system 00:0b: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.307215] system 00:0b: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.307218] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.307220] system 00:0b: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.307222] system 00:0b: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.307224] system 00:0b: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.307227] system 00:0b: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.307229] system 00:0b: iomem range 0xfed1c800-0xfed1cfff has been reserved
[    0.307233] system 00:0b: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.307236] system 00:0b: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.341867] AppArmor: AppArmor Filesystem Enabled
[    0.341958] pci 0000:02:00.0: PCI bridge, secondary bus 0000:03
[    0.341961] pci 0000:02:00.0:   IO window: 0xe000-0xefff
[    0.341967] pci 0000:02:00.0:   MEM window: 0xf4000000-0xf7dfffff
[    0.341972] pci 0000:02:00.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.341979] pci 0000:02:01.0: PCI bridge, secondary bus 0000:04
[    0.341981] pci 0000:02:01.0:   IO window: 0xd000-0xdfff
[    0.341987] pci 0000:02:01.0:   MEM window: 0xf0f00000-0xf3ffffff
[    0.341991] pci 0000:02:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.341998] pci 0000:01:00.0: PCI bridge, secondary bus 0000:02
[    0.342001] pci 0000:01:00.0:   IO window: 0xd000-0xefff
[    0.342006] pci 0000:01:00.0:   MEM window: 0xf0f00000-0xf7dfffff
[    0.342011] pci 0000:01:00.0:   PREFETCH window: 0x000000d0000000-0x000000efffffff
[    0.342017] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.342020] pci 0000:00:01.0:   IO window: 0xd000-0xefff
[    0.342023] pci 0000:00:01.0:   MEM window: 0xf0f00000-0xf7efffff
[    0.342026] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000efffffff
[    0.342030] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.342032] pci 0000:00:1c.0:   IO window: disabled
[    0.342037] pci 0000:00:1c.0:   MEM window: disabled
[    0.342042] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.342046] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.342048] pci 0000:00:1c.1:   IO window: disabled
[    0.342054] pci 0000:00:1c.1:   MEM window: 0xf0e00000-0xf0efffff
[    0.342058] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.342063] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0d
[    0.342066] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.342072] pci 0000:00:1c.3:   MEM window: 0xf0c00000-0xf0dfffff
[    0.342077] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.342084] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:09
[    0.342086] pci 0000:00:1c.5:   IO window: disabled
[    0.342091] pci 0000:00:1c.5:   MEM window: 0xf0b00000-0xf0bfffff
[    0.342096] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.342101] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.342102] pci 0000:00:1e.0:   IO window: disabled
[    0.342108] pci 0000:00:1e.0:   MEM window: 0xf0a00000-0xf0afffff
[    0.342112] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.342121]   alloc irq_desc for 16 on node -1
[    0.342123]   alloc kstat_irqs on node -1
[    0.342127] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.342130] pci 0000:00:01.0: setting latency timer to 64
[    0.342139] pci 0000:01:00.0: setting latency timer to 64
[    0.342148] pci 0000:02:00.0: setting latency timer to 64
[    0.342158] pci 0000:02:01.0: setting latency timer to 64
[    0.342166] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.342170] pci 0000:00:1c.0: setting latency timer to 64
[    0.342178]   alloc irq_desc for 17 on node -1
[    0.342180]   alloc kstat_irqs on node -1
[    0.342182] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.342187] pci 0000:00:1c.1: setting latency timer to 64
[    0.342195]   alloc irq_desc for 19 on node -1
[    0.342196]   alloc kstat_irqs on node -1
[    0.342199] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.342203] pci 0000:00:1c.3: setting latency timer to 64
[    0.342212] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.342216] pci 0000:00:1c.5: setting latency timer to 64
[    0.342224] pci 0000:00:1e.0: setting latency timer to 64
[    0.342228] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.342230] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.342232] pci_bus 0000:01: resource 0 io:  [0xd000-0xefff]
[    0.342234] pci_bus 0000:01: resource 1 mem: [0xf0f00000-0xf7efffff]
[    0.342236] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xefffffff]
[    0.342238] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.342240] pci_bus 0000:02: resource 1 mem: [0xf0f00000-0xf7dfffff]
[    0.342242] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xefffffff]
[    0.342244] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.342246] pci_bus 0000:03: resource 1 mem: [0xf4000000-0xf7dfffff]
[    0.342248] pci_bus 0000:03: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.342250] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.342252] pci_bus 0000:04: resource 1 mem: [0xf0f00000-0xf3ffffff]
[    0.342254] pci_bus 0000:04: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.342257] pci_bus 0000:0c: resource 1 mem: [0xf0e00000-0xf0efffff]
[    0.342259] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff]
[    0.342261] pci_bus 0000:0d: resource 1 mem: [0xf0c00000-0xf0dfffff]
[    0.342263] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.342265] pci_bus 0000:09: resource 1 mem: [0xf0b00000-0xf0bfffff]
[    0.342267] pci_bus 0000:05: resource 1 mem: [0xf0a00000-0xf0afffff]
[    0.342269] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.342271] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.342294] NET: Registered protocol family 2
[    0.342361] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.342589] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.342877] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.343025] TCP: Hash tables configured (established 131072 bind 65536)
[    0.343027] TCP reno registered
[    0.343074] NET: Registered protocol family 1
[    0.343113] Trying to unpack rootfs image as initramfs...
[    0.500475] Freeing initrd memory: 7724k freed
[    0.501836] Switched to high resolution mode on CPU 1
[    0.504024] Switched to high resolution mode on CPU 0
[    0.504164] Simple Boot Flag at 0x79 set to 0x1
[    0.504317] cpufreq-nforce2: No nForce2 chipset.
[    0.504340] Scanning for low memory corruption every 60 seconds
[    0.504428] audit: initializing netlink socket (disabled)
[    0.504444] type=2000 audit(1262242158.500:1): initialized
[    0.511385] highmem bounce pool size: 64 pages
[    0.511389] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.512572] VFS: Disk quotas dquot_6.5.2
[    0.512619] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.513052] fuse init (API version 7.12)
[    0.513116] msgmni has been set to 1679
[    0.513293] alg: No test for stdrng (krng)
[    0.513304] io scheduler noop registered
[    0.513306] io scheduler anticipatory registered
[    0.513307] io scheduler deadline registered
[    0.513342] io scheduler cfq registered (default)
[    0.513527] pci 0000:03:00.0: Boot video device
[    0.513656]   alloc irq_desc for 24 on node -1
[    0.513658]   alloc kstat_irqs on node -1
[    0.513666] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.513672] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.513793]   alloc irq_desc for 25 on node -1
[    0.513794]   alloc kstat_irqs on node -1
[    0.513802] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.513813] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.513956]   alloc irq_desc for 26 on node -1
[    0.513958]   alloc kstat_irqs on node -1
[    0.513966] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.513976] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.514119]   alloc irq_desc for 27 on node -1
[    0.514120]   alloc kstat_irqs on node -1
[    0.514128] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.514139] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.514283]   alloc irq_desc for 28 on node -1
[    0.514285]   alloc kstat_irqs on node -1
[    0.514293] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.514303] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.514534] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.514645] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.514781] ACPI: AC Adapter [AC] (on-line)
[    0.514842] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.515274] ACPI: Lid Switch [LID]
[    0.515313] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.515319] ACPI: Power Button [PBTN]
[    0.515353] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.515355] ACPI: Sleep Button [SBTN]
[    0.515905] ACPI: SSDT bfe72cb4 002C8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.516306] ACPI: SSDT bfe7264a 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.516558] Monitor-Mwait will be used to enter C-1 state
[    0.516578] Monitor-Mwait will be used to enter C-2 state
[    0.516596] Monitor-Mwait will be used to enter C-3 state
[    0.516602] Marking TSC unstable due to TSC halts in idle
[    0.516619] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.516639] processor LNXCPU:00: registered as cooling_device0
[    0.516641] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.516914] ACPI: SSDT bfe72f7c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.517142] ACPI: SSDT bfe72c2f 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.517483] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.517503] processor LNXCPU:01: registered as cooling_device1
[    0.517506] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.523368] thermal LNXTHERM:01: registered as thermal_zone0
[    0.523374] ACPI: Thermal Zone [THM] (64 C)
[    0.523423] isapnp: Scanning for PnP cards...
[    0.635303] ACPI: Battery Slot [BAT0] (battery present)
[    0.881310] isapnp: No Plug & Play device found
[    0.882181] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.883249] brd: module loaded
[    0.883609] loop: module loaded
[    0.883662] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.883721] ahci 0000:00:1f.2: version 3.0
[    0.883734] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.883761]   alloc irq_desc for 29 on node -1
[    0.883763]   alloc kstat_irqs on node -1
[    0.883771] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.883845] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    0.883848] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    0.883853] ahci 0000:00:1f.2: setting latency timer to 64
[    0.893056] scsi0 : ahci
[    0.893123] scsi1 : ahci
[    0.893171] scsi2 : ahci
[    0.893325] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 29
[    0.893327] ata2: DUMMY
[    0.893329] ata3: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1ca00 irq 29
[    0.893369] ata_piix 0000:00:1f.1: version 2.13
[    0.893376] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.893410] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.893482] scsi3 : ata_piix
[    0.893531] scsi4 : ata_piix
[    0.893974] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.893977] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.894163] ata5: port disabled. ignoring.
[    0.894718] Fixed MDIO Bus: probed
[    0.894744] PPP generic driver version 2.4.2
[    0.894805] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.894820]   alloc irq_desc for 22 on node -1
[    0.894821]   alloc kstat_irqs on node -1
[    0.894825] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.894834] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.894837] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.894872] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.898781] ehci_hcd 0000:00:1a.7: debug port 1
[    0.898787] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.898799] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.912016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.912076] usb usb1: configuration #1 chosen from 1 choice
[    0.912099] hub 1-0:1.0: USB hub found
[    0.912106] hub 1-0:1.0: 4 ports detected
[    0.912153]   alloc irq_desc for 20 on node -1
[    0.912154]   alloc kstat_irqs on node -1
[    0.912158] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.912166] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.912169] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.912192] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.916081] ehci_hcd 0000:00:1d.7: debug port 1
[    0.916087] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.916098] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.928017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.928077] usb usb2: configuration #1 chosen from 1 choice
[    0.928097] hub 2-0:1.0: USB hub found
[    0.928103] hub 2-0:1.0: 6 ports detected
[    0.928156] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.928170] uhci_hcd: USB Universal Host Controller Interface driver
[    0.928187] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.928193] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.928196] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.928225] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.928251] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.928315] usb usb3: configuration #1 chosen from 1 choice
[    0.928335] hub 3-0:1.0: USB hub found
[    0.928341] hub 3-0:1.0: 2 ports detected
[    0.928380]   alloc irq_desc for 21 on node -1
[    0.928382]   alloc kstat_irqs on node -1
[    0.928385] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.928391] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.928394] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.928418] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.928452] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.928518] usb usb4: configuration #1 chosen from 1 choice
[    0.928538] hub 4-0:1.0: USB hub found
[    0.928543] hub 4-0:1.0: 2 ports detected
[    0.928589] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.928595] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.928598] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.928620] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.928646] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.928710] usb usb5: configuration #1 chosen from 1 choice
[    0.928730] hub 5-0:1.0: USB hub found
[    0.928735] hub 5-0:1.0: 2 ports detected
[    0.928776] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.928782] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.928785] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.928807] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.928833] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.928898] usb usb6: configuration #1 chosen from 1 choice
[    0.928918] hub 6-0:1.0: USB hub found
[    0.928923] hub 6-0:1.0: 2 ports detected
[    0.928962] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.928967] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.928970] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.928992] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.929031] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.929094] usb usb7: configuration #1 chosen from 1 choice
[    0.929117] hub 7-0:1.0: USB hub found
[    0.929122] hub 7-0:1.0: 2 ports detected
[    0.929205] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.940254] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.940258] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.940298] mice: PS/2 mouse device common for all mice
[    0.940380] rtc_cmos 00:03: RTC can wake from S4
[    0.940403] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.940434] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.940509] device-mapper: uevent: version 1.0.3
[    0.940584] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.940664] device-mapper: multipath: version 1.1.0 loaded
[    0.940666] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.940764] EISA: Probing bus 0 at eisa.0
[    0.940816] EISA: Mainboard BG_FFFF detected.
[    0.940827] Cannot allocate resource for EISA slot 1
[    0.940855] EISA: Detected 0 cards.
[    0.941017] cpuidle: using governor ladder
[    0.941110] cpuidle: using governor menu
[    0.941487] TCP cubic registered
[    0.941608] NET: Registered protocol family 10
[    0.941968] lo: Disabled Privacy Extensions
[    0.942226] NET: Registered protocol family 17
[    0.942239] Bluetooth: L2CAP ver 2.13
[    0.942240] Bluetooth: L2CAP socket layer initialized
[    0.942243] Bluetooth: SCO (Voice Link) ver 0.6
[    0.942244] Bluetooth: SCO socket layer initialized
[    0.942274] Bluetooth: RFCOMM TTY layer initialized
[    0.942276] Bluetooth: RFCOMM socket layer initialized
[    0.942277] Bluetooth: RFCOMM ver 1.11
[    0.942734] Using IPI No-Shortcut mode
[    0.942782] PM: Resume from disk failed.
[    0.942791] registered taskstats version 1
[    0.942910]   Magic number: 5:788:823
[    0.942991] rtc_cmos 00:03: setting system clock to 2009-12-31 06:49:19 UTC (1262242159)
[    0.942993] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.943002] EDD information not available.
[    0.944214] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.072475] ata4.00: ATAPI: TSSTcorp DVD+/-RW TS-L632H, D400, max UDMA/33
[    1.104371] ata4.00: configured for UDMA/33
[    1.212091] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.212119] ata3: SATA link down (SStatus 0 SControl 300)
[    1.212458] ata1.00: ATA-8: FUJITSU MHZ2320BJ FFS G2, 0085001C, max UDMA/100
[    1.212463] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.213015] ata1.00: configured for UDMA/100
[    1.228223] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2320B 0085 PQ: 0 ANSI: 5
[    1.228299] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.228336] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.228371] sd 0:0:0:0: [sda] Write Protect is off
[    1.228374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.228392] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.228483]  sda:
[    1.232345] scsi 3:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632H D400 PQ: 0 ANSI: 5
[    1.248308] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.248313] Uniform CD-ROM driver Revision: 3.20
[    1.248424] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.248483] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.258997]  sda1 sda2 sda3 sda4 < sda5 >
[    1.293964] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.294027] Freeing unused kernel memory: 540k freed
[    1.294337] Write protecting the kernel text: 4568k
[    1.294387] Write protecting the kernel read-only data: 1836k
[    1.376032] Linux agpgart interface v0.103
[    1.436243] tg3.c:v3.99 (April 20, 2009)
[    1.436304] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.436314] tg3 0000:09:00.0: setting latency timer to 64
[    1.440114] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.440128] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    1.452997] tg3 0000:09:00.0: PME# disabled
[    1.460932] acpi device:34: registered as cooling_device2
[    1.461579] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/device:30/device:31/input/input5
[    1.461608] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.461655] ACPI Warning: \_SB_.PCI0.AGP_.SLI_.SLI1.VID1._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    1.461706] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/device:36/device:37/input/input6
[    1.461726] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.466320] eth0: Tigon3 [partno(BCM95754m) rev b002] (PCI Express) MAC address 00:23:ae:04:88:ba
[    1.466324] eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.466326] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.466328] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.471081] ohci1394 0000:05:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.500079] Clocksource tsc unstable (delta = -211677076 ns)
[    1.509062] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    1.509202] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    1.530074] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f0aff800-f0afffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.646299] usb 2-6: configuration #1 chosen from 1 choice
[    1.893012] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.161402] usb 3-2: configuration #1 chosen from 1 choice
[    2.164384] hub 3-2:1.0: USB hub found
[    2.166360] hub 3-2:1.0: 3 ports detected
[    2.409050] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.624042] usb 4-1: configuration #1 chosen from 1 choice
[    2.644071] usbcore: registered new interface driver hiddev
[    2.649679] generic-usb 0003:046D:C251.0001: hiddev96,hidraw0: USB HID v1.11 Device [GamePanel LCD] on usb-0000:00:1a.1-1/input0
[    2.649700] usbcore: registered new interface driver usbhid
[    2.649704] usbhid: v2.6:USB HID core driver
[    2.809788] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc0003379ede1]
[    2.865011] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    3.048041] usb 6-1: configuration #1 chosen from 1 choice
[    3.102644] input: Microsoft Microsoft Notebook Receiver v2.0 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input7
[    3.102704] generic-usb 0003:045E:00E1.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Notebook Receiver v2.0] on usb-0000:00:1d.1-1/input0
[    3.177400] usb 3-2.1: new full speed USB device using uhci_hcd and address 3
[    3.304493] usb 3-2.1: configuration #1 chosen from 1 choice
[    3.367103] EXT4-fs (loop0): barriers enabled
[    3.382595] kjournald2 starting: pid 475, dev loop0:8, commit interval 5 seconds
[    3.382628] EXT4-fs (loop0): delayed allocation enabled
[    3.382631] EXT4-fs: file extents enabled
[    3.383498] EXT4-fs: mballoc enabled
[    3.383508] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    3.394403] usb 3-2.2: new full speed USB device using uhci_hcd and address 4
[    3.523517] usb 3-2.2: configuration #1 chosen from 1 choice
[    3.529683] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input8
[    3.529727] generic-usb 0003:0A5C:4502.0003: input,hidraw2: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1a.0-2.2/input0
[    3.601425] usb 3-2.3: new full speed USB device using uhci_hcd and address 5
[    3.731538] usb 3-2.3: configuration #1 chosen from 1 choice
[    3.738716] input: Broadcom Corp as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input9
[    3.738772] generic-usb 0003:0A5C:4503.0004: input,hidraw3: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1a.0-2.3/input0
[    4.172111] type=1505 audit(1262242162.729:2): operation="profile_load" pid=505 name=/usr/share/gdm/guest-session/Xsession
[    4.173827] type=1505 audit(1262242162.729:3): operation="profile_load" pid=506 name=/sbin/dhclient3
[    4.174371] type=1505 audit(1262242162.729:4): operation="profile_load" pid=506 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.174665] type=1505 audit(1262242162.729:5): operation="profile_load" pid=506 name=/usr/lib/connman/scripts/dhclient-script
[    4.207085] type=1505 audit(1262242162.762:6): operation="profile_load" pid=507 name=/usr/bin/evince
[    4.215390] type=1505 audit(1262242162.770:7): operation="profile_load" pid=507 name=/usr/bin/evince-previewer
[    4.220335] type=1505 audit(1262242162.774:8): operation="profile_load" pid=507 name=/usr/bin/evince-thumbnailer
[    4.242301] type=1505 audit(1262242162.798:9): operation="profile_load" pid=509 name=/usr/lib/cups/backend/cups-pdf
[    4.242927] type=1505 audit(1262242162.798:10): operation="profile_load" pid=509 name=/usr/sbin/cupsd
[    4.966609] udev: starting version 147
[    5.612580] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    5.659767] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    5.711208] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    5.711306] usbcore: registered new interface driver btusb
[    5.899739] input: Dell WMI hotkeys as /devices/virtual/input/input10
[    5.918286] Linux video capture interface: v2.00
[    5.973083] sdhci: Secure Digital Host Controller Interface driver
[    5.973085] sdhci: Copyright(c) Pierre Ossman
[    5.973480] ricoh-mmc: Ricoh MMC Controller disabling driver
[    5.973482] ricoh-mmc: Copyright(c) Philip Langdale
[    5.973509] ricoh-mmc: Ricoh MMC controller found at 0000:05:01.2 [1180:0843] (rev 12)
[    5.973526] ricoh-mmc: Controller is now disabled.
[    5.981111] cfg80211: Calling CRDA to update world regulatory domain
[    6.014716] lp: driver loaded but no devices found
[    6.030005] sdhci-pci 0000:05:01.1: SDHCI controller found [1180:0822] (rev 22)
[    6.030021]   alloc irq_desc for 18 on node -1
[    6.030023]   alloc kstat_irqs on node -1
[    6.030029] sdhci-pci 0000:05:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.032700] Registered led device: mmc0::
[    6.033720] mmc0: SDHCI controller on PCI [0000:05:01.1] using DMA
[    6.142845] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.202100] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    6.203094] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    6.203726] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input11
[    6.203790] usbcore: registered new interface driver uvcvideo
[    6.203793] USB Video Class driver (v0.1.0)
[    6.493736] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    6.537125] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[    6.537172] b43: probe of ssb0:0 failed with error -95
[    6.537206] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    6.694346] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[    6.694354] serio: Synaptics pass-through port at isa0060/serio1/input0
[    6.716268] cfg80211: World regulatory domain updated:
[    6.716270]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.716272]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.716275]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.716277]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.716279]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.716281]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.732586] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[    6.914216] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.914241] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.295158] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input13
[    7.488251] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    7.488312] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    7.488378] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    7.488425] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    7.488471] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[    7.488519] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[    7.488566] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[    7.488612] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input21
[    9.430632] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:3 across:127222436k 
[    9.483124] EXT4-fs (loop0): internal journal on loop0:8
[   10.076829] __ratelimit: 3 callbacks suppressed
[   10.076831] type=1505 audit(1262260168.633:12): operation="profile_replace" pid=967 name=/usr/share/gdm/guest-session/Xsession
[   10.078156] type=1505 audit(1262260168.633:13): operation="profile_replace" pid=968 name=/sbin/dhclient3
[   10.078694] type=1505 audit(1262260168.633:14): operation="profile_replace" pid=968 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.078987] type=1505 audit(1262260168.633:15): operation="profile_replace" pid=968 name=/usr/lib/connman/scripts/dhclient-script
[   10.081900] type=1505 audit(1262260168.637:16): operation="profile_replace" pid=969 name=/usr/bin/evince
[   10.090222] type=1505 audit(1262260168.645:17): operation="profile_replace" pid=969 name=/usr/bin/evince-previewer
[   10.095575] type=1505 audit(1262260168.649:18): operation="profile_replace" pid=969 name=/usr/bin/evince-thumbnailer
[   10.102762] type=1505 audit(1262260168.657:19): operation="profile_replace" pid=971 name=/usr/lib/cups/backend/cups-pdf
[   10.103443] type=1505 audit(1262260168.657:20): operation="profile_replace" pid=971 name=/usr/sbin/cupsd
[   10.105842] type=1505 audit(1262260168.661:21): operation="profile_replace" pid=972 name=/usr/sbin/tcpdump
[   11.473234] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.473236] Bluetooth: BNEP filters: protocol multicast
[   11.475707] ppdev: user-space parallel port driver
[   11.597324] Bridge firewalling registered
[   12.085768] tg3 0000:09:00.0: PME# disabled
[   12.085869]   alloc irq_desc for 30 on node -1
[   12.085871]   alloc kstat_irqs on node -1
[   12.085887] tg3 0000:09:00.0: irq 30 for MSI/MSI-X
[   12.164560] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  557.176091] CE: hpet increasing min_delta_ns to 15000 nsec

_**6. Network configuration**_

**$ sudo lshw -C network**

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0efc000-f0efffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5754M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:23:ae:04:88:ba
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5754m-v3.23 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:f0bf0000-f0bfffff

_**7. $ iwlist scan**_

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

_**8. Version**_
[B]
$ lsb_release -d[/B]

Description:    Ubuntu 9.10

_**9. Kernel/Architecture**_

**$ uname -mr**

2.6.31-14-generic i686

_**10. Restarting Network**_
[B]
$ sudo /etc/init.d/networking restart[/B]
 * Reconfiguring network interfaces...                                                                                                                               [ OK ] 


Thank you for all the help! If you need anymore information just ask and I'll do the best I can to provide you with it! Thanks!

-Alex

---

### Post by Mahngiel on 2009-12-31
Read my post [here]("http://ubuntuforums.org/showthread.php?t=1369112")

---

### Post by br0wnie on 2009-12-31
Well from your posts it seems you are asking for my wireless card, which when I looked into my device manager under "Network Adapters" there was Dell Wireless 1395 WLAN Mini-Card. I'm not sure if that's it or not, you may know. I looked through "System" and my card isn't there so yeah.

Also after following that link, my card thing was 14e4:4315
Which means:

14e4:4315 
   in progress 
   BCM4312 802.11b/g - low power 
   b43 

According to that chart.

Anything else you need to know..?

---

### Post by bkratz on 2009-12-31
You might want to look at this thread

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by br0wnie on 2009-12-31
I have no idea what any of that means.. lol.
Explain what I need to do and what it will allow me to do..?

---

### Post by br0wnie on 2009-12-31
Bump

---

### Post by bkratz on 2009-12-31
> **br0wnie said:**
> Bump



Just go to the numbered statements just below: 

**This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.**


And do them in that order.  The terminal is located at 

Applications>>Accessories>>Terminal

What part are you having problems with?


The actual statements are in the block labeled code just below the description of what happens: you can just copy/paste these in the terminal in the order given or be very careful and type them in.

---

### Post by br0wnie on 2009-12-31
Okay, so I need to download the patch found here: 
[http://software.6368.co.cc/linux/b43...2.6.32.2.patch]("http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.patch").

Then follow the instructions following the lines here: This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.(?)

After that I should be able to use Ubuntu internet right?

Also quick question, can I download + install that patch on the Vista part of my laptop? Cause otherwise I can download it at all on the Ubuntu site since I have no internet there..

---

### Post by bkratz on 2009-12-31
> **br0wnie said:**
> Okay, so I need to download the patch found here: 
[http://software.6368.co.cc/linux/b43...2.6.32.2.patch]("http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.patch").

Then follow the instructions following the lines here: This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.(?)

After that I should be able to use Ubuntu internet right?

Also quick question, can I download + install that patch on the Vista part of my laptop? Cause otherwise I can download it at all on the Ubuntu site since I have no internet there..





No, you don't need to download the patch at all. Wait just a minute until I look at it again.

---

### Post by br0wnie on 2009-12-31
Okay thank you for being patient and helping :D

---

### Post by bkratz on 2009-12-31
> **br0wnie said:**
> Okay, so I need to download the patch found here: 
[http://software.6368.co.cc/linux/b43...2.6.32.2.patch]("http://software.6368.co.cc/linux/b43/patches/b43_kernel_2.6.32.2.patch").

Then follow the instructions following the lines here: This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.(?)

After that I should be able to use Ubuntu internet right?

Also quick question, can I download + install that patch on the Vista part of my laptop? Cause otherwise I can download it at all on the Ubuntu site since I have no internet there..




This is the part you need

```

This is the new, updated information for Karmic. The steps are much easier in Karmic than in Jaunty. The steps for Jaunty are at the bottom of the post for reference and for people who still use Karmic.

1. Open up Terminal.

2. Install the "linux-backports-modules-karmic" (newer wireless drivers from compat-wireless) package and the "b43-fwcutter" package (wireless firmware). During installation, if it asks you to fetch the firmware automatically, make sure you select yes.

Code:
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
3. Blacklist the ssb module.

Code:
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
4. Blacklist the wl module.

Code:
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
5. Reboot

6. Enjoy your wireless!!!



```

The numbers are just descriptions of what is happening in the line just below code:
is what you need to copy to the terminal--use copy paste to prevent accidents.
don't forget to reboot as in step 5

---

### Post by br0wnie on 2009-12-31
On step two this is what I typed..

alex@ubuntu:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic
alex@ubuntu:~$ 

That's what happened. What am I doing wrong? My friend said that there is some command to get packages or whatever but he couldn't remember.

---

### Post by bkratz on 2009-12-31
> **br0wnie said:**
> On step two this is what I typed..

alex@ubuntu:~$ sudo apt-get install linux-backports-modules-karmic b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-karmic
alex@ubuntu:~$ 

That's what happened. What am I doing wrong? My friend said that there is some command to get packages or whatever but he couldn't remember.

Hold on I think we will have to go to synaptic and change the repositories---checking now

---

### Post by bkratz on 2009-12-31
Go to system>> administration>>Synaptic Package Manager  needs password

Then
Settings>>Repositories and make sure the first four are checkmarked--I think it is there---press reload  for that matter while you are there you could just go ahead and do step 2 by putting 
linux-backports-modules-karmic b43-fwcutter in the search box and ticking the result when it finds it.  You would still have to do the echo commands at the terminal though, so I guess ignore that and do it from the terminal to prevent confusion.

---

### Post by br0wnie on 2009-12-31
I did all that password stuff, checkmarks, reloading thing. Yet when I typed the stuff in the terminal it came up with the same thing saying it couldnt find the package..

---

### Post by br0wnie on 2009-12-31
My bad, I didn't hit reload so that may be why. When I click reload it comes up with a big error, basically saying it failed to fetch a bunch of files to update or whatever.

I can't update them because I don't have the internet to download them from :/ 

[I'm on my friends laptop right now to reply to you guys]

This is what the error said:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by SeaJayEmm on 2010-01-01
you need to get the .inf file (probably bcmwl5.inf) from the windows xp driver for the wireless card. run ndisgtk from terminal "sudo ndisgtk" load the .inf file, click install and reboot.

---

### Post by br0wnie on 2010-01-01
I tried what you said:

alex@ubuntu:~$ sudo ndisgtk
[sudo] password for alex: 
sudo: ndisgtk: command not found
alex@ubuntu:~$ ndisgtk
The program 'ndisgtk' is currently not installed.  You can install it by typing:
sudo apt-get install ndisgtk
ndisgtk: command not found
alex@ubuntu:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndisgtk
alex@ubuntu:~$ 


It didn't work

---

### Post by br0wnie on 2010-01-01
bump

---

### Post by bkratz on 2010-01-01
When I was posting last night I did not realize that you don't have even wired Ethernet available, so obviously downloads won't work. You don't have wired--do you?  I think the ndisgtk is on the live CD--I'm not actually sure so I will have to find mine and see. Will post back when I know for sure.

---

### Post by br0wnie on 2010-01-01
I can now do wired, I found the cord, my mom put it hidden away >.>

So I will repeat your steps provided earlier and see how it goes :D

---

### Post by bkratz on 2010-01-01
Good because I couldn't find my live disk anyway!

---

### Post by br0wnie on 2010-01-01
Works perfectly now, thank you so much for all the help/patience :D

---

### Post by bkratz on 2010-01-01
When you do get it solved (and you will ) remember to go to the thread tools and mark it as [solved} and it is really ideal to tell people what you found so that they may benefit.

Good Luck

---

### Post by br0wnie on 2010-01-01
Okay it works perfectly :D Thank you once again

---

### Post by keithb685 on 2010-01-01
This solution worked perfect for me. I had a problem with my dell laptop not picking up my router, works fine now. Thanks a million for your help. Another happy ubuntu user :)

---

