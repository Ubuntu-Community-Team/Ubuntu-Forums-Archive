---
title: "Wired connection not working"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by RustamM on 2013-03-02
The wired connection from my laptop to the router has stopped working. It's definitely a problem with the computer as a light turns on both on the router and inside the socket that the cable plugs into. The computer appears to have no idea that the ethernet port even exists, so I'm not sure what to do. Very occasionally the connection comes back, but I can't figure out why.

Here are some outputs that appear to always be asked for in similar posts I've seen, but I'm not really sure what you need to know so let me know if you need more.

```
kay@kay-MM061:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Dell Device [1028:01bd]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
    Subsystem: Dell Device [1028:01bd]
    Kernel modules: i2c-i801
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel modules: b44
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: r592
    Kernel modules: r592
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
    Subsystem: Dell Device [1028:01bd]
    Kernel driver in use: r852
    Kernel modules: r852
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel modules: ssb
```

```
kay@kay-MM061:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
joydev                 17393  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
r852                   17901  0 
snd_hwdep              13276  1 snd_hda_codec
sm_common              16772  1 r852
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
nand                   49667  2 r852,sm_common
i915                  423416  3 
psmouse                96718  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
dell_laptop            17767  0 
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
usbhid                 41937  0 
hid                    77428  1 usbhid
snd_rawmidi            25424  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
nand_bch               13003  1 nand
bch                    21784  1 nand_bch
serio_raw              13027  0 
bnep                   17830  2 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         45466  1 i915
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
nand_ecc               13105  1 nand
r592                   17808  0 
drm                   197641  4 i915,drm_kms_helper
memstick               15857  1 r592
btusb                  17948  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 i915
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
video                  19115  1 i915
wmi                    18744  1 dell_wmi
rfcomm                 38139  12 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
bluetooth             158479  23 bnep,btusb,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci


``````
kay@kay-MM061:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7008 (7.0 KB)  TX bytes:7008 (7.0 KB)

``````

kay@kay-MM061:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: 7C:C5:37:81:2A:E1 ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:


``````

kay@kay-MM061:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

``````

kay@kay-MM061:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
kay@kay-MM061:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

---

