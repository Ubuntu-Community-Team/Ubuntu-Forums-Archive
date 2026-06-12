---
title: "Netgear WG111v3 speed problems on lucid lynx"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by com.cr33p on 2010-05-05
Hi folks,

i decided to change the OS from Windows to Linux.
But now I am encountering some problems that are discouraging me from using Ubuntu.

With my Netgear WG111v3 USB WiFi Adapter, I got perfect speeds on Windows 7 but on Ubuntu 10.04 it seems a little bit buggy, because after I changed the encryption to WPA2 it worked with fullspeed (420kb/s) but then after 10 minutes it slowed down to ~100kb/s and is now permanently that slow.

My Specs:

Intel Core2Quad Q6600
Gigabyte GA-G32...(i forgot the full name)
4 GB Ram
OS: Ubuntu Lucid Lynx 10.04 64-bit
WiFi-Adapter: Netgear WG111v3
Router: Thomson TG585v7 (austrian)

$lspci
```
Bus 005 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04f9:01ce Brother Industries, Ltd DCP-135C
Bus 004 Device 002: ID 046d:c242 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
robert@robert-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
robert@robert-desktop:~$ clear

robert@robert-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```$lsusb
```
Bus 005 Device 002: ID 1532:0007 Razer USA, Ltd DeathAdder Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04f9:01ce Brother Industries, Ltd DCP-135C
Bus 004 Device 002: ID 046d:c242 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```$ifconfig
```
eth0      Link encap:Ethernet  Hardware Adresse 00:1f:d0:54:d0:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Basisadresse:0x8000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

wlan0     Link encap:Ethernet  Hardware Adresse 00:1e:2a:ce:5a:73  
          inet Adresse:10.0.0.1  Bcast:10.0.0.255  Maske:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:238103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141704 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:345939543 (345.9 MB)  TX bytes:13843168 (13.8 MB)
```$iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Thomson706478"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1F:9F:D1:A1:25   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```$lsmod
```
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
arc4                    1473  2 
rtl8187                53204  0 
mac80211              238128  1 rtl8187
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  0 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              148386  2 rtl8187,mac80211
nvidia              10799466  38 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6            1765  1 rtl8187
snd                    70978  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  0 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
parport_pc             29958  1 
vga16fb                12757  1 
joydev                 11072  0 
vgastate                9857  1 vga16fb
usblp                  12407  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
usb_storage            49833  0 
xpad                   10711  0 
led_class               3732  2 rtl8187,xpad
ff_memless              5109  1 xpad
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
r8169                  39554  0 
mii                     5237  1 r8169
```$dmesg
```
[    0.641811] Time: 22:05:45  Date: 05/05/10
[    0.641811] NET: Registered protocol family 16
[    0.641811] Trying to unpack rootfs image as initramfs...
[    0.641811] ACPI: bus type pci registered
[    0.641811] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.641811] PCI: MCFG area at c0000000 reserved in E820
[    0.646360] PCI: Using MMCONFIG at c0000000 - cfffffff
[    0.646361] PCI: Using configuration type 1 for base access
[    0.647012] bio: create slab <bio-0> at 0
[    0.650202] ACPI: EC: Look up EC in DSDT
[    0.655328] ACPI: Interpreter enabled
[    0.655334] ACPI: (supports S0 S3 S4 S5)
[    0.655354] ACPI: Using IOAPIC for interrupt routing
[    0.659411] ACPI: No dock devices found.
[    0.659505] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.659603] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.659606] pci 0000:00:01.0: PME# disabled
[    0.659663] pci 0000:00:1b.0: reg 10 64bit mmio: [0xe5200000-0xe5203fff]
[    0.659702] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.659705] pci 0000:00:1b.0: PME# disabled
[    0.659761] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.659764] pci 0000:00:1c.0: PME# disabled
[    0.659821] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.659824] pci 0000:00:1c.1: PME# disabled
[    0.659869] pci 0000:00:1d.0: reg 20 io port: [0xe000-0xe01f]
[    0.659912] pci 0000:00:1d.1: reg 20 io port: [0xe100-0xe11f]
[    0.659955] pci 0000:00:1d.2: reg 20 io port: [0xe200-0xe21f]
[    0.660024] pci 0000:00:1d.3: reg 20 io port: [0xe300-0xe31f]
[    0.660078] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe5204000-0xe52043ff]
[    0.660228] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.660231] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.660235] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0800 (mask 000f)
[    0.660238] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0290 (mask 000f)
[    0.660241] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 4700 (mask 000b)
[    0.660285] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.660290] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.660295] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.660300] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.660305] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.660325] pci 0000:00:1f.2: PME# supported from D3hot
[    0.660329] pci 0000:00:1f.2: PME# disabled
[    0.660369] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.660417] pci 0000:01:00.0: reg 10 32bit mmio: [0xe2000000-0xe2ffffff]
[    0.660425] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.660433] pci 0000:01:00.0: reg 1c 64bit mmio: [0xe0000000-0xe1ffffff]
[    0.660438] pci 0000:01:00.0: reg 24 io port: [0xc000-0xc07f]
[    0.660443] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.660502] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.660505] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.660509] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.660546] pci 0000:00:1c.0: bridge io port: [0xb000-0xbfff]
[    0.660594] pci 0000:03:00.0: reg 10 io port: [0xd000-0xd0ff]
[    0.660613] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xe5010000-0xe5010fff]
[    0.660626] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xe5000000-0xe500ffff]
[    0.660633] pci 0000:03:00.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.660670] pci 0000:03:00.0: supports D1 D2
[    0.660672] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.660676] pci 0000:03:00.0: PME# disabled
[    0.660730] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.660734] pci 0000:00:1c.1: bridge 32bit mmio: [0xe4000000-0xe4ffffff]
[    0.660740] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xe5000000-0xe50fffff]
[    0.660780] pci 0000:04:07.0: reg 10 32bit mmio: [0xe5104000-0xe51047ff]
[    0.660787] pci 0000:04:07.0: reg 14 32bit mmio: [0xe5100000-0xe5103fff]
[    0.660827] pci 0000:04:07.0: supports D1 D2
[    0.660828] pci 0000:04:07.0: PME# supported from D0 D1 D2 D3hot
[    0.660832] pci 0000:04:07.0: PME# disabled
[    0.660868] pci 0000:00:1e.0: transparent bridge
[    0.660873] pci 0000:00:1e.0: bridge 32bit mmio: [0xe5100000-0xe51fffff]
[    0.660893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.661009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.661054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.661108] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.670834] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.670921] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.671007] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.671092] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.671177] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.671264] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.671349] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.671434] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.671537] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.671540] vgaarb: loaded
[    0.671633] SCSI subsystem initialized
[    0.671671] libata version 3.00 loaded.
[    0.671671] usbcore: registered new interface driver usbfs
[    0.671671] usbcore: registered new interface driver hub
[    0.671671] usbcore: registered new device driver usb
[    0.671671] ACPI: WMI: Mapper loaded
[    0.671671] PCI: Using ACPI for IRQ routing
[    0.671671] NetLabel: Initializing
[    0.671671] NetLabel:  domain hash size = 128
[    0.671671] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.671671] NetLabel:  unlabeled traffic allowed by default
[    0.671671] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.671671] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.690074] Switching to clocksource tsc
[    0.691834] AppArmor: AppArmor Filesystem Enabled
[    0.691842] pnp: PnP ACPI init
[    0.691851] ACPI: bus type pnp registered
[    0.694174] pnp: PnP ACPI: found 14 devices
[    0.694176] ACPI: ACPI bus type pnp unregistered
[    0.694185] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.694188] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.694190] system 00:01: ioport range 0x800-0x805 has been reserved
[    0.694192] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.694195] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.694201] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[    0.694207] system 00:0b: iomem range 0xc0000000-0xcfffffff has been reserved
[    0.694211] system 00:0c: iomem range 0xcd400-0xcffff has been reserved
[    0.694214] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.694217] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.694219] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.694221] system 00:0c: iomem range 0xbfeb0000-0xbfefffff could not be reserved
[    0.694224] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.694227] system 00:0c: iomem range 0x100000-0xbfeaffff could not be reserved
[    0.694229] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.694232] system 00:0c: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.694234] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.694237] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.694239] system 00:0c: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.694242] system 00:0c: iomem range 0xfff00000-0xffffffff has been reserved
[    0.694244] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.698933] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.698936] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.698939] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe3ffffff
[    0.698942] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.698946] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.698948] pci 0000:00:1c.0:   IO window: 0xb000-0xbfff
[    0.698953] pci 0000:00:1c.0:   MEM window: 0xe5300000-0xe54fffff
[    0.698956] pci 0000:00:1c.0:   PREFETCH window: 0x000000e5500000-0x000000e56fffff
[    0.698962] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.698964] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.698969] pci 0000:00:1c.1:   MEM window: 0xe4000000-0xe4ffffff
[    0.698972] pci 0000:00:1c.1:   PREFETCH window: 0x000000e5000000-0x000000e50fffff
[    0.698977] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.698979] pci 0000:00:1e.0:   IO window: disabled
[    0.698983] pci 0000:00:1e.0:   MEM window: 0xe5100000-0xe51fffff
[    0.698986] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.698996]   alloc irq_desc for 16 on node -1
[    0.698998]   alloc kstat_irqs on node -1
[    0.699002] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.699006] pci 0000:00:01.0: setting latency timer to 64
[    0.699013] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.699016] pci 0000:00:1c.0: setting latency timer to 64
[    0.699022]   alloc irq_desc for 17 on node -1
[    0.699024]   alloc kstat_irqs on node -1
[    0.699026] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.699030] pci 0000:00:1c.1: setting latency timer to 64
[    0.699035] pci 0000:00:1e.0: setting latency timer to 64
[    0.699039] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.699041] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.699043] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.699045] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe3ffffff]
[    0.699047] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.699049] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    0.699051] pci_bus 0000:02: resource 1 mem: [0xe5300000-0xe54fffff]
[    0.699053] pci_bus 0000:02: resource 2 pref mem [0xe5500000-0xe56fffff]
[    0.699055] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.699057] pci_bus 0000:03: resource 1 mem: [0xe4000000-0xe4ffffff]
[    0.699059] pci_bus 0000:03: resource 2 pref mem [0xe5000000-0xe50fffff]
[    0.699061] pci_bus 0000:04: resource 1 mem: [0xe5100000-0xe51fffff]
[    0.699063] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.699065] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.699099] NET: Registered protocol family 2
[    0.699244] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.700310] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.704143] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.704652] TCP: Hash tables configured (established 524288 bind 65536)
[    0.704655] TCP reno registered
[    0.704771] NET: Registered protocol family 1
[    0.704889] pci 0000:01:00.0: Boot video device
[    0.705218] Scanning for low memory corruption every 60 seconds
[    0.705364] audit: initializing netlink socket (disabled)
[    0.705374] type=2000 audit(1273097144.699:1): initialized
[    0.713809] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.715066] VFS: Disk quotas dquot_6.5.2
[    0.715112] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.715655] fuse init (API version 7.13)
[    0.715731] msgmni has been set to 7910
[    0.716005] alg: No test for stdrng (krng)
[    0.716073] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.716076] io scheduler noop registered
[    0.716078] io scheduler anticipatory registered
[    0.716079] io scheduler deadline registered
[    0.716108] io scheduler cfq registered (default)
[    0.716218]   alloc irq_desc for 24 on node -1
[    0.716220]   alloc kstat_irqs on node -1
[    0.716228] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.716234] pcieport 0000:00:01.0: setting latency timer to 64
[    0.716318]   alloc irq_desc for 25 on node -1
[    0.716319]   alloc kstat_irqs on node -1
[    0.716325] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.716332] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.716432]   alloc irq_desc for 26 on node -1
[    0.716433]   alloc kstat_irqs on node -1
[    0.716439] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.716446] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.716518] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.716585] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.716677] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.716680] ACPI: Power Button [PWRB]
[    0.716725] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.716727] ACPI: Power Button [PWRF]
[    0.716975] processor LNXCPU:00: registered as cooling_device0
[    0.717143] ACPI: SSDT 00000000bfee7cc0 00087 (v01  PmRef  Cpu1Ist 00003000 INTL 20040311)
[    0.717363] processor LNXCPU:01: registered as cooling_device1
[    0.717585] ACPI: SSDT 00000000bfee7d50 00087 (v01  PmRef  Cpu2Ist 00003000 INTL 20040311)
[    0.717793] processor LNXCPU:02: registered as cooling_device2
[    0.717961] ACPI: SSDT 00000000bfee7de0 00087 (v01  PmRef  Cpu3Ist 00003000 INTL 20040311)
[    0.718226] processor LNXCPU:03: registered as cooling_device3
[    0.721067] Linux agpgart interface v0.103
[    0.721099] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.721193] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.721459] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.722375] brd: module loaded
[    0.722767] loop: module loaded
[    0.722845] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.722928] ata_piix 0000:00:1f.2: version 2.13
[    0.722943]   alloc irq_desc for 19 on node -1
[    0.722945]   alloc kstat_irqs on node -1
[    0.722952] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.722956] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.722988] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.723199] scsi0 : ata_piix
[    0.723417] scsi1 : ata_piix
[    0.724016] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.724018] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.724290] Fixed MDIO Bus: probed
[    0.724320] PPP generic driver version 2.4.2
[    0.724347] tun: Universal TUN/TAP device driver, 1.6
[    0.724349] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.724412] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.724427]   alloc irq_desc for 23 on node -1
[    0.724428]   alloc kstat_irqs on node -1
[    0.724432] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.724445] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.724448] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.724477] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.724493] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.728367] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.728379] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe5204000
[    0.749641] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.749728] usb usb1: configuration #1 chosen from 1 choice
[    0.749752] hub 1-0:1.0: USB hub found
[    0.749760] hub 1-0:1.0: 8 ports detected
[    0.749814] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.749824] uhci_hcd: USB Universal Host Controller Interface driver
[    0.749846] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.749851] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.749854] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.749886] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.749910] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000
[    0.749986] usb usb2: configuration #1 chosen from 1 choice
[    0.750006] hub 2-0:1.0: USB hub found
[    0.750012] hub 2-0:1.0: 2 ports detected
[    0.750050] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.750055] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.750058] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.750083] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.750109] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100
[    0.750183] usb usb3: configuration #1 chosen from 1 choice
[    0.750203] hub 3-0:1.0: USB hub found
[    0.750208] hub 3-0:1.0: 2 ports detected
[    0.750242]   alloc irq_desc for 18 on node -1
[    0.750244]   alloc kstat_irqs on node -1
[    0.750247] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.750252] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.750255] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.750283] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.750309] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200
[    0.750375] usb usb4: configuration #1 chosen from 1 choice
[    0.750398] hub 4-0:1.0: USB hub found
[    0.750403] hub 4-0:1.0: 2 ports detected
[    0.750437] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.750442] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.750444] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.750470] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.750496] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300
[    0.750564] usb usb5: configuration #1 chosen from 1 choice
[    0.750585] hub 5-0:1.0: USB hub found
[    0.750590] hub 5-0:1.0: 2 ports detected
[    0.750660] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.750662] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.750776] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.750852] mice: PS/2 mouse device common for all mice
[    0.750949] rtc_cmos 00:04: RTC can wake from S4
[    0.750981] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.751003] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.751104] device-mapper: uevent: version 1.0.3
[    0.751217] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.751396] device-mapper: multipath: version 1.1.0 loaded
[    0.751398] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.751745] cpuidle: using governor ladder
[    0.751747] cpuidle: using governor menu
[    0.752037] TCP cubic registered
[    0.752139] NET: Registered protocol family 10
[    0.752507] lo: Disabled Privacy Extensions
[    0.752734] NET: Registered protocol family 17
[    0.757218] PM: Resume from disk failed.
[    0.757230] registered taskstats version 1
[    0.757481]   Magic number: 10:216:97
[    0.757540] rtc_cmos 00:04: setting system clock to 2010-05-05 22:05:45 UTC (1273097145)
[    0.757543] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.757544] EDD information not available.
[    0.773707] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.809040] Freeing initrd memory: 8135k freed
[    0.889894] ata2.01: NODEV after polling detection
[    0.929897] ata2.00: ATAPI: ATAPI   DVD D  DH16D2S, EH33, max UDMA/100
[    0.989957] ata2.00: configured for UDMA/100
[    1.110187] ata1.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[    1.110191] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    1.110194] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.177589] ata1.00: configured for UDMA/133
[    1.177719] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    1.177835] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.177870] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.177919] sd 0:0:0:0: [sda] Write Protect is off
[    1.177922] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.177943] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.178093]  sda:
[    1.179338] scsi 1:0:0:0: CD-ROM            ATAPI    DVD D  DH16D2S   EH33 PQ: 0 ANSI: 5
[    1.185076] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.185080] Uniform CD-ROM driver Revision: 3.20
[    1.185183] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.185219] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.217236]  sda1 sda2 sda3 < sda5 sda6 >
[    1.242881] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.242912] Freeing unused kernel memory: 876k freed
[    1.243130] Write protecting the kernel read-only data: 7680k
[    1.257477] udev: starting version 151
[    1.281141] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.281163] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.281208] r8169 0000:03:00.0: setting latency timer to 64
[    1.281252]   alloc irq_desc for 27 on node -1
[    1.281254]   alloc kstat_irqs on node -1
[    1.281267] r8169 0000:03:00.0: irq 27 for MSI/MSI-X
[    1.281763] eth0: RTL8168c/8111c at 0xffffc90000658000, 00:1f:d0:54:d0:cd, XID 1c4000c0 IRQ 27
[    1.309336] ohci1394 0000:04:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.362585] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e5104000-e51047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.450057] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    1.616922] usb 1-8: configuration #1 chosen from 1 choice
[    1.718721] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    1.891330] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.087256] usb 4-1: configuration #1 chosen from 1 choice
[    2.370085] usb 4-2: new full speed USB device using uhci_hcd and address 3
[    2.556205] usb 4-2: configuration #1 chosen from 1 choice
[    2.691453] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dfa8a400001d7d]
[    2.831287] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    3.017328] usb 5-1: configuration #1 chosen from 1 choice
[   12.202774] udev: starting version 151
[   12.268817] Registered led device: xpad0
[   12.268876] input: Logitech Chillstream Controller as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[   12.268943] usbcore: registered new interface driver xpad
[   12.268945] xpad: X-Box pad driver
[   12.275479] Adding 2055160k swap on /dev/sda6.  Priority:-1 extents:1 across:2055160k 
[   12.276163] Initializing USB Mass Storage driver...
[   12.300654] lp: driver loaded but no devices found
[   12.305741] vga16fb: initializing
[   12.305744] vga16fb: mapped to 0xffff8800000a0000
[   12.305797] fb0: VGA16 VGA frame buffer device
[   12.314530] usbcore: registered new interface driver hiddev
[   12.314576] scsi2 : SCSI emulation for USB Mass Storage devices
[   12.318213] input: Razer DeathAdder as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input5
[   12.318327] generic-usb 0003:1532:0007.0001: input,hidraw0: USB HID v1.11 Mouse [Razer DeathAdder] on usb-0000:00:1d.3-1/input0
[   12.318362] usbcore: registered new interface driver usbhid
[   12.318365] usbhid: v2.6:USB HID core driver
[   12.321042] parport_pc 00:08: reported by Plug and Play ACPI
[   12.321093] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.324947] usb-storage: device found at 3
[   12.324949] usb-storage: waiting for device to settle before scanning
[   12.324968] usbcore: registered new interface driver usb-storage
[   12.324971] USB Mass Storage support registered.
[   12.326475] type=1505 audit(1273089957.063:2):  operation="profile_load" pid=459 name="/sbin/dhclient3"
[   12.327041] type=1505 audit(1273089957.063:3):  operation="profile_load" pid=459 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.327345] type=1505 audit(1273089957.063:4):  operation="profile_load" pid=459 name="/usr/lib/connman/scripts/dhclient-script"
[   12.328859] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01CE
[   12.328883] usbcore: registered new interface driver usblp
[   12.333055] ppdev: user-space parallel port driver
[   12.428039] intel_rng: FWH not detected
[   12.470213] lp0: using parport0 (interrupt-driven).
[   12.486298] Console: switching to colour frame buffer device 80x30
[   13.014866] nvidia: module license 'NVIDIA' taints kernel.
[   13.014871] Disabling lock debugging due to kernel taint
[   13.360942] cfg80211: Calling CRDA to update world regulatory domain
[   13.417893] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.418007] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.551301] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   13.602521] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.602529] nvidia 0000:01:00.0: setting latency timer to 64
[   13.602533] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.602763] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.15  Fri Mar 12 00:29:13 PST 2010
[   13.663812] cfg80211: World regulatory domain updated:
[   13.663815]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.663818]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.663820]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.663822]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.663824]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.663826]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.862002] r8169: eth0: link down
[   13.862485] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.040680] phy0: Selected rate control algorithm 'minstrel'
[   14.041240] phy0: hwaddr 00:1e:2a:ce:5a:73, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   14.062728] rtl8187: Customer ID is 0x00
[   14.062760] Registered led device: rtl8187-phy0::tx
[   14.062780] Registered led device: rtl8187-phy0::rx
[   14.063596] rtl8187: wireless switch is on
[   14.063632] usbcore: registered new interface driver rtl8187
[   17.322095] usb-storage: device scan complete
[   17.343076] scsi 2:0:0:0: Direct-Access     Brother  DCP-135C         1.00 PQ: 0 ANSI: 2
[   17.343693] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.423048] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   17.982803] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.071393] wlan0: deauthenticating from 00:1f:9f:d1:a1:25 by local choice (reason=3)
[   32.271314] wlan0: direct probe to AP 00:1f:9f:d1:a1:25 (try 1)
[   32.274939] wlan0: direct probe responded
[   32.274943] wlan0: authenticate with AP 00:1f:9f:d1:a1:25 (try 1)
[   32.277945] wlan0: authenticated
[   32.277971] wlan0: associate with AP 00:1f:9f:d1:a1:25 (try 1)
[   32.280936] wlan0: RX AssocResp from 00:1f:9f:d1:a1:25 (capab=0x411 status=0 aid=1)
[   32.280940] wlan0: associated
[   32.286631] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.333628] Intel AES-NI instructions are not detected.
[   33.395630] padlock: VIA PadLock not detected.
[  571.663497] npviewer.bin[1456]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000fffb5dcc error 14
[ 3845.541307] No probe response from AP 00:1f:9f:d1:a1:25 after 500ms, disconnecting.
[ 3848.941213] wlan0: direct probe to AP 00:1f:9f:d1:a1:25 (try 1)
[ 3848.944353] wlan0: direct probe responded
[ 3848.944357] wlan0: authenticate with AP 00:1f:9f:d1:a1:25 (try 1)
[ 3848.946834] wlan0: authenticated
[ 3848.946862] wlan0: associate with AP 00:1f:9f:d1:a1:25 (try 1)
[ 3848.949216] wlan0: RX AssocResp from 00:1f:9f:d1:a1:25 (capab=0x411 status=0 aid=1)
[ 3848.949220] wlan0: associated
[ 3862.020091] wlan0: deauthenticating from 00:1f:9f:d1:a1:25 by local choice (reason=3)
[ 3866.610315] wlan0: deauthenticating from 00:1f:9f:d1:a1:25 by local choice (reason=3)
[ 3867.041950] wlan0: direct probe to AP 00:1f:9f:d1:a1:25 (try 1)
[ 3867.045086] wlan0: direct probe responded
[ 3867.045091] wlan0: authenticate with AP 00:1f:9f:d1:a1:25 (try 1)
[ 3867.047574] wlan0: authenticated
[ 3867.047593] wlan0: associate with AP 00:1f:9f:d1:a1:25 (try 1)
[ 3867.050083] wlan0: RX AssocResp from 00:1f:9f:d1:a1:25 (capab=0x411 status=0 aid=1)
[ 3867.050087] wlan0: associated
[ 6273.823197] npviewer.bin[2113]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ff9efdac error 14
[ 6640.777659] npviewer.bin[2678]: segfault at ff999ea8 ip 00000000ff999ea8 sp 00000000ffc976fc error 14
```$sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:54:d0:cd
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:d000(size=256) memory:e5010000-e5010fff(prefetchable) memory:e5000000-e500ffff(prefetchable) memory:e5020000-e502ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:2a:ce:5a:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.1 multicast=yes wireless=IEEE 802.11bg 
```$iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:D1:A1:25
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Thomson706478"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ddc8d6fe
                    Extra: Last beacon: 33220ms ago
                    IE: Unknown: 000D54686F6D736F6E373036343738
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102EA8A8953A5559249089AEB22ED6B8A71021000754484F4D534F4E1023000A54686F6D736F6E20544710240006353835207637104200093038343654464556551054000800060050F20400011011001054686F6D736F6E20544735383520763710080002008410570001001041000100
                    IE: Unknown: DD060010180200F0
```$lsb-release -d
```
Ubuntu 10.04 LTS
```$uname -mr
```
2.6.32-21-generic x86_64
```$restart
```
* Reconfiguring network interfaces...                                          ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
                                                                         [fail]
```Phew, that was a bunch of code, I hope you can do something with it.

Thanks in advance, com.cr33p

---

### Post by com.cr33p on 2010-05-06
Push. No suggestions?

---

### Post by com.cr33p on 2010-05-06
Push. Is there really no one that knows what to do?

---

### Post by com.cr33p on 2010-05-07
I found out that if I install the rtl8187b driver through ndiswrapper and open the ndisgtk gui it shows me that the device is not installed (my adapter) but when I install the wg111v3 driver the same way it shows me that the device is installed but i cant find any wireless networks, like if there wouldn't be any device pluged in.

(the text above may sound a little crappy, sorry for that english is not my native language)

Any ideas how to get the driver working so that i can connect to a wireless network?

PS: I feel like I am talking to myself on the whole thread...

---

### Post by keypox on 2010-09-04
same issue any fix?  Super slow stuck at 100-150KBps.  Horribly slow.

---

### Post by Scott. on 2010-09-05
Ditto.  And...I found this antenna on a site that said is was compatible (green vs yellow or red or gray).  Mine tells me I'm connected but after much digging and comparing with my Ethernet output, I feel like this is a driver issue.

---

### Post by anandkumargupta on 2010-10-02
I feed the same. My Same USB adopter is working in my office but in home network it use to search continuously for network and ask for password again and again. In my office the AP belongs to Cisco and In home that belongs to Netgear it self. I thought to change the smps of my system( funny thing I did) but no luck.
I think there is some band problem.

---

