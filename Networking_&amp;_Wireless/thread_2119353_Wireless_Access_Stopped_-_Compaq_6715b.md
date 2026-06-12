---
title: "Wireless Access Stopped - Compaq 6715b"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by koulson on 2013-02-23
Greetings!
Seeking help on a frustrating issue which developed recently with my WiFi access.  Had been working under 12.04 but all of a sudden stopped.  Worry that - although there may have been an update recently which affected it, I may just have an old and broken down radio because I'm not getting any positive results in following through the many posts on this topic.

Most recently attempted to update to 12.10 to see if that would give me the desired results.  Alas, I'm still connected via my network cable.

I took the opportunity to run a nifty script to produce an output file for your reference and look forward to any help you can provide.

My Wifi radio will not power on.  Somehow it turned off but cannot be turned back on again.  This laptop has a simple touch sensor on the indicator for the wifi radio.  Usually it is blue when working, yellow (orange) when off, but now it's dark.

When I ran rfkill initially I could see that the wifi was off both for hardware and softare control - now it shows nothing.

Thank you for whatever help you may be able to provide.
:???:

[HTML]
*************** info trace ****************



**** uname -a ****


Linux keith-HP-Compaq-6715b-RM353UA-ABA 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:28:26 UTC 2013 i686 athlon i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: tg3


**** lsusb ****


Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****




**** lsmod ****


Module                  Size  Used by
rfcomm                 37277  0 
bnep                   17708  2 
bluetooth             183270  10 rfcomm,bnep
snd_hda_codec_analog    75060  1 
radeon                820764  4 
snd_hda_intel          32516  2 
snd_hda_codec         111548  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
ttm                    75535  1 radeon
snd_pcm                80235  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
drm_kms_helper         47304  1 radeon
snd_rawmidi            25383  1 snd_seq_midi
drm                   238811  6 radeon,ttm,drm_kms_helper
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17162  0 
tpm_infineon           17297  0 
i2c_algo_bit           13198  1 radeon
pcmcia                 39545  0 
kvm_amd                54395  0 
kvm                   357807  1 kvm_amd
snd                    62146  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13418  0 
hp_accel               25729  0 
lis3lv02d              19230  1 hp_accel
soundcore              14600  1 snd
yenta_socket           27096  0 
shpchp                 32190  0 
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
pcmcia_rsrc            18192  1 yenta_socket
psmouse                84878  0 
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_piix4              12984  0 
serio_raw              13032  0 
ati_agp                13178  0 
wmi                    18591  0 
k8temp                 12843  0 
video                  18895  0 
tpm_tis                18209  0 
input_polldev          13649  1 lis3lv02d
mac_hid                13038  0 
ppdev                  12818  0 
parport_pc             31969  1 
b43                   347364  0 
mac80211              461261  1 b43
cfg80211              175574  2 b43,mac80211
bcma                   34484  1 b43
ssb                    50088  1 b43
lp                     13300  0 
parport                40754  3 ppdev,parport_pc,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
firewire_ohci          35522  0 
firewire_core          57493  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
pata_atiixp            13000  0 
tg3                   130449  0 


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1




**** NetworkManager.state ****



[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****



[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


auto lo
iface lo inet loopback



**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search home


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist hp-wmi


**** dmesg ****


[    0.000000] DMI: Hewlett-Packard HP Compaq 6715b (RM353UA#ABA)/30C2, BIOS 68YTT Ver. F.0B 03/04/2008
[    1.201575] tg3.c:v3.123 (March 21, 2012)
[    1.280027] tg3 0000:10:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[    1.340017] tg3 0000:10:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[    1.400018] tg3 0000:10:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
[    1.401111] tg3 0000:10:00.0: eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address <MAC address removed>
[    1.401116] tg3 0000:10:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.401120] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.401124] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   10.818785] wmi: Mapper loaded
[   20.246627] type=1400 audit(1361616675.775:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1012 comm="apparmor_parser"
[   27.842266] tg3 0000:10:00.0: irq 44 for MSI/MSI-X
[  109.363943] tg3 0000:10:00.0: eth0: Link is up at 100 Mbps, full duplex
[  109.363963] tg3 0000:10:00.0: eth0: Flow control is on for TX and on for RX


**************** done ********************

[/HTML]

---

### Post by praseodym on 2013-02-23
Try to reset the BIOS.

Change

```
WirelessEnabled=[COLOR="Red"]false[/COLOR]
```

to "true"

---

### Post by koulson on 2013-02-23
Thank you for your reply.
The bios shows that the wireless is enabled.

I have modified the "/var/lib/NetworkManager/NetworkManager.state" using gedit to true and after reboot, still no wifi function.
[HTML]
[main]
NetworkingEnabled=true
WirelessEnabled=[COLOR="Blue"]true[/COLOR]
WWANEnabled=true
WimaxEnabled=true
[/HTML]

---

### Post by praseodym on 2013-02-23
Please show:
```

lspci -nnk
pccardctl info
```
Obviously a Broadcom device?! Module b43 is (still?) loaded.

---

### Post by koulson on 2013-02-23
[HTML]
keith@keith-HP-Compaq-6715b-RM353UA-ABA:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge [1002:7910]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
	Kernel modules: shpchp
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI Device [1002:7914]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:12.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA [1002:4380]
	Subsystem: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA [1002:4380]
	Kernel driver in use: ahci
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0) [1002:4387]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: ohci_hcd
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1) [1002:4388]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2) [1002:4389]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: ohci_hcd
00:13.3 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3) [1002:438a]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: ohci_hcd
00:13.4 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4) [1002:438b]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: ohci_hcd
00:13.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI) [1002:4386]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 14)
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: piix4_smbus
	Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB600 IDE [1002:438c]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge [1002:438d]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Kernel driver in use: k8temp
	Kernel modules: k8temp
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series] [1002:791f]
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: radeon
	Kernel modules: radeon
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:30c2]
	Kernel driver in use: tg3
	Kernel modules: tg3

[/HTML]

[HTML]
keith@keith-HP-Compaq-6715b-RM353UA-ABA:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
keith@keith-HP-Compaq-6715b-RM353UA-ABA:~$ 
[/HTML]

---

### Post by aat2bd on 2013-06-21
> **koulson said:**
> [HTML]
keith@keith-HP-Compaq-6715b-RM353UA-ABA:~$ lspci -nnk
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge [1002:7910]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel modules: ati-agp
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
    Kernel modules: shpchp
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI Device [1002:7914]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:12.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA [1002:4380]
    Subsystem: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA [1002:4380]
    Kernel driver in use: ahci
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0) [1002:4387]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: ohci_hcd
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1) [1002:4388]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: ohci_hcd
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2) [1002:4389]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: ohci_hcd
00:13.3 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3) [1002:438a]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: ohci_hcd
00:13.4 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4) [1002:438b]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: ohci_hcd
00:13.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI) [1002:4386]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: ehci_hcd
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 14)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB600 IDE [1002:438c]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge [1002:438d]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series] [1002:791f]
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: radeon
    Kernel modules: radeon
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: tg3
    Kernel modules: tg3

[/HTML]

[HTML]
keith@keith-HP-Compaq-6715b-RM353UA-ABA:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
keith@keith-HP-Compaq-6715b-RM353UA-ABA:~$ 
[/HTML]

I HAVE THE SAME PROBLEM.  iT WORKED WHEN i FIRST INSTALLED THE OS, BUT STOPPED WORKING WHEN THE UPDATES WERE APPLIED.

---

### Post by praseodym on 2013-06-21
Hi,

the wireless card is not shown. Try to reset the BIOS to default settings

---

### Post by aat2bd on 2013-07-08
> **praseodym said:**
> Hi,

the wireless card is not shown. Try to reset the BIOS to default settings

I did that and still no go

mae@mae-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:c4:c8:fe:8b
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb v2.09 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:d0000000-d000ffff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c8000000-c8003fff
mae@mae-laptop:~$

---

