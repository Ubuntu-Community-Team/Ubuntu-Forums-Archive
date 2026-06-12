---
title: "dell E6500 wireless network"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by trevorthomas on 2012-07-15
hi all, 
I have just installed ubuntu 12.04 on my dell e6500 but cannot get the wireless internet to work.  there is a switch on side of laptop to turn on and off the wireless, when it is on I am supposed to get a blue indicator light above the keyboard to show that it is on but I don't get that either. 

any help much appreciated

trevor

---

### Post by praseodym on 2012-07-15
Hi,

please show the terminal (CTRL+ALT+T) outputs of these commands:

```
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```
Any key combination like Fn+F2?

---

### Post by irv on 2012-07-15
If you have a broadcom card make sure you have dkms installed.
```
sudo apt-get install dkms
```

I have a Dell Inspiron 1521 with Broadcom STA wireless
This is what I had to do to get the wireless going.

1. I uninstalled &#8220;bcmwl-kernel-source&#8221; package,
```
sudo apt-get remove bcmwl-kernel-source
```

2. I installed &#8220;firmware-b43-installer&#8221; package
```
sudo apt-get install firmware-b43-installer
```

3. I installed &#8220;b43-fwcutter&#8221; packager
```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:
 > cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'

This was the out put:
> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

EDIT: I forgot to mention that I have a Broadcom BCM4311 card.

---

### Post by trevorthomas on 2012-07-15
> **praseodym said:**
> Hi,

please show the terminal (CTRL+ALT+T) outputs of these commands:

```
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```Any key combination like Fn+F2?

Hope this helps

trevor@trevor-Latitude-E6500:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Dell Device [1028:024f]
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel modules: iTCO_wdt
00:1f.2 IDE interface [0101]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] [8086:2928] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel modules: i2c-i801
00:1f.5 IDE interface [0101]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 2 port SATA Controller [IDE mode] [8086:292d] (rev 03)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: ata_piix
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
    Subsystem: Dell Device [1028:024f]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
trevor@trevor-Latitude-E6500:~$

---

### Post by irv on 2012-07-16
I see you have the Broadcom Corporation BCM4312.
I found an older post on this card. Take a look at the last post, #4. Maybe this will help.

---

### Post by trevorthomas on 2012-07-17
> **irv said:**
> I see you have the Broadcom Corporation BCM4312.
I found an older post on this card. Take a look at the last post, #4. Maybe this will help.

many thanks, all working now.
It was a simple matter of typing Additional Drivers and adding it. 

Trevor

---

### Post by irv on 2012-07-17
> **trevorthomas said:**
> many thanks, all working now.
It was a simple matter of typing Additional Drivers and adding it. 

Trevor

That's great, maybe you can mark this thread "solved".
[ATTACH]221386[/ATTACH]

---

