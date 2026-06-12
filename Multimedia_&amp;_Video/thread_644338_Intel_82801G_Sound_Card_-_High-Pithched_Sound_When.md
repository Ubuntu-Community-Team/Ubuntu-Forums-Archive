---
title: "Intel 82801G Sound Card - High-Pithched Sound When Playing Audio"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by MenZa on 2007-12-18
I have a bit of an issue with my new laptop, a Toshiba L40-10Q.

Whenever it plays any sound, I get a high-pitched tone for the duration of the title played. This applies to music files, system sounds (login, etc.), etc.

I've tried a bunch of things; I've re-compiled ALSA, I've tried using tons of different model settings in my 'snd-hda-intel' line in my /etc/modules (laptop, hp, toshiba, 3stack, 6stack).

Here's the output of tsalsa (an ALSA diagnostics script): ([link](http://pastebin.ca/822893))

My lspci is as follows:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Any help is HIGHLY appreciated.

**Edit:** Instructions on how to fix can be found [here](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3662).

---

### Post by ukblacknight on 2007-12-19
Try muting your CD volume in the volume control.  I had this issue on Windows XP, Vista and Ubuntu 7.10.

---

