---
title: "Wireless driver not working"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by Candlehawk on 2012-02-21
I just installed xubuntu 11.10 on this laptop. here is the output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 1800 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0
    Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at d8240000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d6000000-d7ffffff
    Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d4000000-d5ffffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d8000000-d80fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18b0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 4
    I/O ports at 18c0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d6000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 4000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at d8001000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at d8001800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 21
    Memory at d8002000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
    Subsystem: Hewlett-Packard Company Device 30a0
    Flags: medium devsel, IRQ 21
    Memory at d8002400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852
    Kernel modules: r852

```

When I am not using the proprietary driver, the connection settings says that wireless is blocked by a hardware switch, when I try the proprietary drier, I don't even have a wireless option. Ethernet works (typing this up on the laptop) if you need any other information, please let me know.

---

### Post by praseodym on 2012-02-21
Hi,

uninstall the STA driver and install the missing firmwre:

```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
sudo modprobe b43
```
Check:

```
lsmod
iwconfig
rfkill list
```
What kind of computer is this?

---

### Post by Candlehawk on 2012-02-21
Did what you said, modprobe -rf wl gave me this:

```
FATAL: Module wl not found.
```
Everything else went through without a hitch.

Output of lsmod:
```
Module                  Size  Used by
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
b43                   318816  0 
snd_hda_intel          24262  3 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393421  1 b43
snd                    55902  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17901  0 
sm_common              16737  1 r852
cfg80211              172427  2 b43,mac80211
wmi                    18744  1 hp_wmi
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
r592                   17808  0 
i915                  509519  2 
mtd                    35852  2 sm_common,nand
memstick               15857  1 r592
psmouse                73673  0 
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
drm                   192194  3 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
e100                   36289  0 
ssb                    50682  1 b43
alex@BLackHP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
alex@BLackHP:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
alex@BLackHP:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  4 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
arc4                   12473  2 
snd_hda_codec_conexant    52418  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
b43                   318816  0 
snd_hda_intel          24262  3 
snd_hda_codec          91859  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              393421  1 b43
snd                    55902  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   17901  0 
sm_common              16737  1 r852
cfg80211              172427  2 b43,mac80211
wmi                    18744  1 hp_wmi
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
r592                   17808  0 
i915                  509519  2 
mtd                    35852  2 sm_common,nand
memstick               15857  1 r592
psmouse                73673  0 
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
drm                   192194  3 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
e100                   36289  0 
ssb                    50682  1 b43

```

Output of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

Output of rfkill list:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

The computer is an HP Pavilion dv1000

---

### Post by praseodym on 2012-02-22
>    Hard blocked: yes
Button/switch/key/key combination (Fn+F2 or sth.)?

---

### Post by Candlehawk on 2012-02-22
No, I have tried to press that button a number of times with both the proprietary and the the open driver. Neither work

---

### Post by praseodym on 2012-02-22
Try to reset the BIOS

---

