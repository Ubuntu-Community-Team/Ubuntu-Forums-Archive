---
title: "Linksys WUSB54G Wireless Adapter Driver [Ndiswrapper]- wlan0 not showing"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by Mooseeeeey on 2013-05-21
(Followed instructions from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) for installing driver)
Currently have things running pretty smoothly, with an ethernet connection between laptop and Ubuntu Server 12.04.2, feeding Internet connection from laptop to server (Working fine).
I have Ndiswrapper (1.3.8? I believe) installed, and was seemingly successful,** but a wlan0 will not show up in iwconfig. **
I would ideally be setup only with the wireless adapter, but needed the ethernet linkage to get some basic stuff done first, and obviously make driver install easier. However, is the connection with ethernet some how blocking the wlan0 from even showing up? Heres some various dumps to hopefully be of assitance:


ndiswrapper -l
```

wusb54gv2 : driver installed
    device (13B1:000A) present (alternate driver: p54usb)

```

lsusb
```

Bus 001 Device 002: ID 13b1:000a Linksys WUSB54G v2 802.11g Adapter [Intersil ISL3887]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

lspci -nnk
```

00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:2570]
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P AGP Bridge [8086:2571] (rev 02)
    Kernel modules: shpchp
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000/8KNXP motherboard [1458:24d2]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:24d2]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:24d2]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:24d2]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:5006]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
    Kernel modules: lpc_ich, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:24d2]
    Kernel driver in use: ata_piix
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:24d1]
    Kernel driver in use: ata_piix
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE) [1458:24d2]
    Kernel modules: i2c-i801
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
    Subsystem: Giga-byte Technology GA-8IPE1000/8KNXP motherboard [1458:a002]
    Kernel driver in use: snd_intel8x0
    Kernel modules: snd-intel8x0
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV18 [GeForce4 MX 4000] [10de:0185] (rev c1)
    Subsystem: eVga.com. Corp. Device [3842:a096]
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
02:00.0 Communication controller [0780]: LSI Corporation LT WinModem [11c1:044c] (rev 02)
    Subsystem: LSI Corporation LT WinModem [11c1:044c]
02:01.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
    Subsystem: PROLINK Microsystems Corp Device [1554:4011]
    Kernel driver in use: bttv
    Kernel modules: bttv
02:01.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
    Subsystem: PROLINK Microsystems Corp Device [1554:4011]
    Kernel driver in use: snd_bt87x
    Kernel modules: snd-bt87x
02:02.0 Multimedia audio controller [0401]: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller [1412:1724] (rev 01)
    Subsystem: VIA Technologies Inc. Device [1412:2403]
    Kernel driver in use: snd_ice1724
    Kernel modules: snd-ice1724
02:08.0 Ethernet controller [0200]: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller [8086:1051] (rev 02)
    Subsystem: Giga-byte Technology Device [1458:e000]
    Kernel driver in use: e100
    Kernel modules: e100

```

---

### Post by chili555 on 2013-05-21
Were it me, I'd probably install the needed firmware for p54usb and try the native driver first and use ndiswrapper only as a last resort. > $ modinfo p54usb
filename:       /lib/modules/3.8.0-21-generic/kernel/drivers/net/wireless/p54/p54usb.ko
[COLOR="#FF0000"]firmware:       isl3887usb
firmware:       isl3886usb[/COLOR]
alias:          prism54usb
license:        GPL
description:    Prism54 USB wireless driver
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     13A26EB8D52764AFDC16700
<snip>
Use that ethernet to do:```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r ndiswrapper
sudo modprobe -r p54usb && sudo modprobe p54usb
```Is it working? If so, I suggest you remove ndiswrapper altogether.

---

### Post by Mooseeeeey on 2013-05-21
Thank you very much!

Did as instructed, rebooted and worked.

However, just for further potential issues, would there have been a command I could have used instead to 'refresh' the listing. After doing the commands, but before reboot, the wlan0 was still not visible in iwconfig.

Hopefully, I won't have too many problems with actually connecting to the WiFi now...

---

### Post by chili555 on 2013-05-22
> **Mooseeeeey said:**
> Thank you very much!

Did as instructed, rebooted and worked.

However, just for further potential issues, would there have been a command I could have used instead to 'refresh' the listing. After doing the commands, but before reboot, the wlan0 was still not visible in iwconfig.

Hopefully, I won't have too many problems with actually connecting to the WiFi now...Glad it's working. 

Without seeing the actual terminal output, it's hard to know what went wrong. If it works after a reboot, I'm confident it works for good. If not, post back and we'll help.

You may as well remove ndiswrapper:```
sudo apt-get remove --purge ndiswrapper*
```

---

