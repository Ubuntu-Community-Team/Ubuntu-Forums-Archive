---
title: "Philips Semiconductors SAA7131/SAA7133/SAA7135"
date: 2011-10-15
forum: Multimedia Software
---

### Post by @ndreX! on 2011-10-15
I'm trying to configure this tv card: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev 10) Ubuntu) but I have some issues, when I start TVTime I got a blank screen, I cannot scan any channel, not even change them, I tried a lot of tutos & howtos but with no success.

Here is my lspci

```

andrex@silver:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev 10)

```

And this my dmesg

```

andrex@silver:~$ dmesg | grep saa7133
[   10.607450] saa7133[0]: found at 0000:04:05.0, rev: 16, irq: 20, latency: 32, mmio: 0xfb100000
[   10.607454] saa7133[0]: subsystem: 5169:0138, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.607465] saa7133[0]: board init: gpio is 39900
[   10.607468] IRQ 20/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.758418] saa7133[0]: i2c eeprom 00: 69 51 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   10.758428] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758436] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758445] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758453] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758461] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758470] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758478] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758486] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758494] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758503] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758511] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758519] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758527] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758535] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.758544] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.759573] saa7133[0]: registered device video0 [v4l2]
[   10.759593] saa7133[0]: registered device vbi0
[   10.763801] IRQ 20/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.763817] saa7133[0]/alsa: saa7133[0] at 0xfb100000 irq 20 registered as card -2


```

Any help, will be appreciate.

Regards.
Andrés Ortiz.

---

### Post by dodle on 2012-02-16
Does anyone mind if I revive this? I have the same card and haven't figured out how to get it to work.

```
:~$ lspci | grep -i "philips"
00:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev 10)
```

I've been trying to get it to work with VLC and me-tv. me-tv reports that there are no dvb devices and VLC looks for devices in /dev/dvb but that folder does not exist on my system. I have installed firmware-linux-nonfree which created a folder called /usr/share/dvb. I have also come across [this tutorial](http://www.wikihow.com/Make-a-Tv-Tuner-Card-Work-on-Ubuntu-Hardy-Heron) but I will need to remove my card to get the specific chipset number. Any advice is much appreciated.

Note: I am using Debian 6.

---

### Post by wolfen69 on 2012-02-16
Maybe [this]("http://www.cyberciti.biz/tips/debian-ubuntu-linux-configure-pinnacle-pctv-tuner.html") will help.

---

### Post by dodle on 2012-02-16
apparently tvtime doesn't work with my video card.

```
:~$ lspci | grep -i "nvidia"
01:00.0 VGA compatible controller: NVIDIA Corporation NV20 [GeForce3] (rev a3)
```

---

