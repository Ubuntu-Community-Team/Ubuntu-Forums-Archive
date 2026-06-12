---
title: "No Wired Network. Wireless Works. Wired Network Works in Debian"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by tdrusk on 2012-08-30
As the title says, my wired internet is not working. I really *really* need this.

Here is some more information:

lspci -v
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:01.0 PCI bridge: Toshiba America Info Systems Device 9602 (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: f4100000-f42fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00007000-0000afff
    Memory behind bridge: f3100000-f40fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f0ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: f3000000-f30fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Toshiba America Info Systems Device fd50
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at c038 [size=8]
    I/O ports at c04c [size=4]
    I/O ports at c030 [size=8]
    I/O ports at c048 [size=4]
    I/O ports at c010 [size=16]
    Memory at f4307000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4306000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4307600 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4305000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4307500 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f4300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=64

00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=0
    I/O behind bridge: 00002000-00005fff
    Memory behind bridge: f2000000-f2ffffff
    Prefetchable memory behind bridge: 00000000f1000000-00000000f1ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices [AMD] nee ATI Device 0000
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f4304000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f4307400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at b000 [size=256]
    Memory at f4200000 (32-bit, non-prefetchable) [size=64K]
    Memory at f4100000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon

02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f3100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 58-94-6b-ff-ff-52-ce-6c
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

08:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Toshiba America Info Systems Device fd50
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f3000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 6000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-3f-b4-bc-60-eb-69-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

``` 

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback

```

cat /etc/NetworkManager/NetworkManager.conf
```

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


```

dmesg | grep -e eth0 -e bcm
```
[    5.215625] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.150241] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.153963] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 60:eb:69:3f:b4:bc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130035 (130.0 KB)  TX bytes:130035 (130.0 KB)

wlan0     Link encap:Ethernet  HWaddr 58:94:6b:52:ce:6c  
          inet addr:192.168.254.106  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::5a94:6bff:fe52:ce6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10496 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12089716 (12.0 MB)  TX bytes:834313 (834.3 KB)

```

Also, as noted, this did work in Debian. I found some information [here]("http://ubuntuforums.org/archive/index.php/t-1505697.html"), but it looks like the driver they were modprobing is already in use. Please help!

---

### Post by chili555 on 2012-08-30
Please hook up the ethernet cable. Click the Network Manager icon and under Wireless, disconnect. Now open the terminal and run and post:```
dmesg | grep -e atl1c -e 08:00
```Thanks.

---

### Post by tdrusk on 2012-08-30
> **chili555 said:**
> Please hook up the ethernet cable. Click the Network Manager icon and under Wireless, disconnect. Now open the terminal and run and post:```
dmesg | grep -e atl1c -e 08:00
```Thanks.


Thanks for your response.

Here is the output:
```
[    0.259361] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.259361] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf7ffffff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xfed3ffff]
[    0.259361] pci_root PNP0A08:00: host bridge window [mem 0xfed45000-0xffffffff]
[    0.259361] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf1ff])
[    0.259361] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000d3fff] (conflicts with Adapter ROM [mem 0x000cf800-0x000d07ff])
[    0.272138] pci 0000:08:00.0: [1969:2060] type 0 class 0x000200
[    0.272159] pci 0000:08:00.0: reg 10: [mem 0xf3000000-0xf303ffff 64bit]
[    0.272170] pci 0000:08:00.0: reg 18: [io  0x6000-0x607f]
[    0.272263] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.272268] pci 0000:08:00.0: PME# disabled
[    0.654509] pci 0000:08:00.0: Signaling PME through PCIe PME interrupt
[    1.379336] atl1c 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.379347] atl1c 0000:08:00.0: setting latency timer to 64
[    1.504717] atl1c 0000:08:00.0: version 1.0.1.0-NAPI
[    7.422684] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input4
[   23.783978] atl1c 0000:08:00.0: irq 44 for MSI/MSI-X
[ 1805.456160] PM: resume of drv:atl1c dev:0000:08:00.0 complete after 115.359 msecs
[ 1825.514420] atl1c 0000:08:00.0: irq 44 for MSI/MSI-X
[ 3887.780147] PM: resume of drv:atl1c dev:0000:08:00.0 complete after 111.027 msecs
[ 3908.528794] atl1c 0000:08:00.0: irq 44 for MSI/MSI-X
[ 4002.296158] PM: resume of drv:atl1c dev:0000:08:00.0 complete after 110.414 msecs
[ 4022.109787] atl1c 0000:08:00.0: irq 44 for MSI/MSI-X
[ 7443.508168] PM: resume of drv:atl1c dev:0000:08:00.0 complete after 110.360 msecs
[ 7453.436658] Modules linked in: usbhid hid pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_conexant snd_hda_intel snd_hda_codec binfmt_misc snd_hwdep snd_pcm uvcvideo videodev v4l2_compat_ioctl32 snd_seq_midi joydev snd_rawmidi arc4 psmouse snd_seq_midi_event snd_seq snd_timer snd_seq_device radeon serio_raw snd edac_core ttm drm_kms_helper drm iwlwifi mac_hid mac80211 toshiba_acpi sparse_keymap edac_mce_amd sp5100_tco soundcore k10temp i2c_algo_bit cfg80211 wmi video i2c_piix4 snd_page_alloc shpchp lp parport ums_realtek uas usb_storage atl1c
[ 7463.296280] atl1c 0000:08:00.0: irq 44 for MSI/MSI-X
[ 7516.780170] PM: resume of drv:atl1c dev:0000:08:00.0 complete after 110.939 msecs
[ 7526.768516] Modules linked in: usbhid hid pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) bnep rfcomm bluetooth parport_pc ppdev snd_hda_codec_conexant snd_hda_intel snd_hda_codec binfmt_misc snd_hwdep snd_pcm uvcvideo videodev v4l2_compat_ioctl32 snd_seq_midi joydev snd_rawmidi arc4 psmouse snd_seq_midi_event snd_seq snd_timer snd_seq_device radeon serio_raw snd edac_core ttm drm_kms_helper drm iwlwifi mac_hid mac80211 toshiba_acpi sparse_keymap edac_mce_amd sp5100_tco soundcore k10temp i2c_algo_bit cfg80211 wmi video i2c_piix4 snd_page_alloc shpchp lp parport ums_realtek uas usb_storage atl1c
[ 7537.380040] atl1c 0000:08:00.0: irq 44 for MSI/MSI-X
```

I almost feel like if I installed with the cable plugged in it would work...

---

### Post by tdrusk on 2012-08-30
Ah-Ha! I fixed it. 

My speculation that Ubuntu would pick it up on original live-cd boot was true. That got me thinking, "Is the card just disabled?"

The card is eth0, so I ran:
```
sudo ifconfig eth0 up
```

This has it up and running. Hopefully it will be enabled from now on. :popcorn:

---

### Post by chili555 on 2012-08-30
Excellent! Glad it's working.

---

