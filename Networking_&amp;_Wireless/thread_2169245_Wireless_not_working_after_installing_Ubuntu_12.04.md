---
title: "Wireless not working after installing Ubuntu 12.04 alongside Windows 7"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by lsadeasy on 2013-08-21
Hi, I recently installed Ubuntu 12.10 (32 bit) on my Dell Inspiron 1545 alongside Windows 7 (64 bit) running for a long time.
Ubuntu Installation went smoothly, after installation I can't seem to connect to my wireless network on Ubuntu, yet the wired connection works fine.
Does anyone know if I need a wireless driver?

---

### Post by carl4926 on 2013-08-21
It's probably a broadcom device

But let us see the output from a terminal using

```
lspci -nnk
```

---

### Post by lsadeasy on 2013-08-21
lauren@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Dell Device [1028:02aa]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Dell Device [1028:02aa]
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
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Dell Device [1028:02aa]
    Kernel modules: i2c-i801
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
    Kernel modules: sky2
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

---

### Post by carl4926 on 2013-08-21
```
[COLOR=#000000]0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/COLOR]
[COLOR=#000000]Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c][/COLOR]
[COLOR=#000000]Kernel driver in use: b43-pci-bridge
[/COLOR][COLOR=#000000]Kernel modules: ssb[/COLOR]
```

This is your device
Please do

```
[COLOR=#000000][FONT=courier]sudo apt-get install firmware-b43-installer[/FONT][/COLOR]
```

---

### Post by lsadeasy on 2013-08-21
I tried sudo apt-get install firmware-b43-installer but it aborted it and recommended the firmware-b43-lpphy-installer package.
So I installed that package and this is what i got...

Creating new firmware directory...
broadcom-wl-4.178.10.4/
broadcom-wl-4.178.10.4/config/
broadcom-wl-4.178.10.4/config/wlconfig_nomimo
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_wl_sdstd
broadcom-wl-4.178.10.4/config/wlconfig_lx_shared
broadcom-wl-4.178.10.4/config/diffupdate.sh
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_sdstd
broadcom-wl-4.178.10.4/config/wl.mk
broadcom-wl-4.178.10.4/config/wltunable_lx_router.h
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta
broadcom-wl-4.178.10.4/config/wl_default
broadcom-wl-4.178.10.4/config/wltunable_lx_router_1chipG.h
broadcom-wl-4.178.10.4/config/wl_hnd
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta
broadcom-wl-4.178.10.4/config/wlconfig_apdef
broadcom-wl-4.178.10.4/README
broadcom-wl-4.178.10.4/linux/
broadcom-wl-4.178.10.4/linux/wl_sta.o
broadcom-wl-4.178.10.4/linux/wl.o
broadcom-wl-4.178.10.4/linux/wl_ap.o
broadcom-wl-4.178.10.4/linux/wl_apsta.o
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  478.104
  MD5        :  bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw

---

### Post by carl4926 on 2013-08-21
> **lsadeasy said:**
> I tried sudo apt-get install firmware-b43-installer but it aborted it and recommended the firmware-b43-lpphy-installer package.
So I installed that package and this is what i got...

Creating new firmware directory...
broadcom-wl-4.178.10.4/
broadcom-wl-4.178.10.4/config/
broadcom-wl-4.178.10.4/config/wlconfig_nomimo
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_wl_sdstd
broadcom-wl-4.178.10.4/config/wlconfig_lx_shared
broadcom-wl-4.178.10.4/config/diffupdate.sh
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_ap_sdstd
broadcom-wl-4.178.10.4/config/wl.mk
broadcom-wl-4.178.10.4/config/wltunable_lx_router.h
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta
broadcom-wl-4.178.10.4/config/wl_default
broadcom-wl-4.178.10.4/config/wltunable_lx_router_1chipG.h
broadcom-wl-4.178.10.4/config/wl_hnd
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_sta_1chipG
broadcom-wl-4.178.10.4/config/wlconfig_lx_router_apsta
broadcom-wl-4.178.10.4/config/wlconfig_apdef
broadcom-wl-4.178.10.4/README
broadcom-wl-4.178.10.4/linux/
broadcom-wl-4.178.10.4/linux/wl_sta.o
broadcom-wl-4.178.10.4/linux/wl.o
broadcom-wl-4.178.10.4/linux/wl_ap.o
broadcom-wl-4.178.10.4/linux/wl_apsta.o
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  478.104
  MD5        :  bb8537e3204a1ea5903fe3e66b5e2763
Extracting b43/ucode5.fw
Extracting b43/pcm5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/ucode9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/ucode13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/ucode14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/ucode16.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/n0initvals16.fw
Extracting b43/lp0initvals16.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/lp0bsinitvals16.fw

So let us see now

```
[COLOR=#000000][FONT=Droid Sans]lspci -nnk | grep -iA2 net[/FONT][/COLOR]

```

---

### Post by carl4926 on 2013-08-21
I have a similar device
```
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: b43-pci-bridge
```

It uses b43 just fine

It looks to me like you might have been trying a little bit of everything to get it going before coming here?

---

### Post by lsadeasy on 2013-08-22
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

Your right I have tried so many things to try get it working, it is driving me crazy...

---

### Post by carl4926 on 2013-08-22
> **lsadeasy said:**
> 09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

Your right I have tried so many things to try get it working, it is driving me crazy...

Please try

```
sudo modprobe -rv b43
```
```
sudo modprobe -v b43
```

---

### Post by lsadeasy on 2013-08-22
It works! Thank you soo much fo all your help.

---

### Post by carl4926 on 2013-08-22
> **lsadeasy said:**
> It works! Thank you soo much fo all your help.
No worries, happy to help

---

