---
title: "how to use wifi connection"
date: 2013-08-09
forum: Networking &amp; Wireless
---

### Post by utsav2 on 2013-08-09
Hi

I have just installed "lubuntu-13.04-desktop-i386" along with windows xp sp2.
My laptop is HP compaq 6710b

In lubuntu I don't know how to access the internet using wifi, however I am able to access the internet via wired connection (by default)

Please help.

---

### Post by carl4926 on 2013-08-09
Open a terminal and post the result of

```
lspci -nnk
```

---

### Post by utsav2 on 2013-08-09
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
    Kernel driver in use: pcieport
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: lpc_ich
00:1f.2 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] [8086:2828] (rev 03)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: ata_piix
02:04.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
    Subsystem: Hewlett-Packard Company Compaq 6710b [103c:30c0]
    Kernel driver in use: yenta_cardbus
02:04.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30c0]
    Kernel driver in use: firewire_ohci
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1371]
    Kernel driver in use: b43-pci-bridge
18:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30c2]
    Kernel driver in use: tg3



```

---

### Post by carl4926 on 2013-08-09
Open a terminal and do

```
[COLOR=#000000][FONT=courier]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]
```
when done you may want to reboot

---

### Post by utsav2 on 2013-08-09
Thanks Carl

It's working now.

I want to know that what does [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk[/FONT][/COLOR] do?
What did you see in its output that you said to install firmware-b43-installer?

---

### Post by carl4926 on 2013-08-09
> **utsav2 said:**
> Thanks Carl

It's working now.

I want to know that what does [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk[/FONT][/COLOR] do?
What did you see in its output that you said to install firmware-b43-installer?

lspci lists your hardware, the -nnk shows kernel modules

I was interested in
```
[FONT=Ubuntu Mono]10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 02)[/FONT]    Subsystem: Hewlett-Packard Company Broadcom 802.11a/b/g WLAN [103c:1371] [FONT=Ubuntu Mono]    Kernel driver in use: b43-pci-bridge[/FONT]
```

The info here: [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
Your device spec: BCM4311 [14e4:4312]
Shows it working with b43.

---

