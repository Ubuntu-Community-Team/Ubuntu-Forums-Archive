---
title: "Realtek HD Audio headaches"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by Sparky222B on 2007-08-16
Hi,

After installing Realtek's linux driver, I still only have OSS as a chooseable sound source. Alsamixer doesn't detect the Realtek sound chipset at all.

Also, about 2/3 of the applications I run think I don't have an audio device, while the other 1/3 detect the OSS device and work fine.

??!

---

### Post by Nebby on 2007-08-16
You might be better off without, as I'v got a realtek chipset too, which didn't work in windows, works badly on linux using the driver but whatever ubuntu does with it automatically works great.

---

### Post by Sparky222B on 2007-08-16
Well, it didn't work at all without the drivers, but I could give it a try - how do you uninstall them? :X

---

### Post by Lord Illidan on 2007-08-16
Can you return the output of ```
lspci
``` please?

---

### Post by Sparky222B on 2007-08-16
Will do in a minute, let me boot into Ubuntu.

---

### Post by Sparky222B on 2007-08-16
```

sparky@SparkyPC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:01.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:03.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (ASUS 8211 (ITE IT8212 ATA RAID Controller)) (rev 11)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7280 (rev 9a)
04:00.1 Display controller: ATI Technologies Inc Unknown device 72a0 (rev 9a)

```

---

### Post by Sparky222B on 2007-08-16
However, when I open the sound properties dialog, the selection where you'd normally choose your sound device is blank.

---

### Post by Sparky222B on 2007-08-16
Well, even with the drivers installed, no sound is played, and this happens (see first screenshot). Alsamixer just displays this (see second screenshot).

---

### Post by Sparky222B on 2007-08-17
I still require help to this issue, and if nobody can help me, I'll have to reformat as Windows :\

---

### Post by Sparky222B on 2007-08-18
Ah! Got it!

See [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

