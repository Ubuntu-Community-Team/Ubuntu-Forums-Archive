---
title: "Sound not playing properly in games"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by Daminvar on 2007-09-23
Hi.  I've been having a bit of trouble with getting games to function.  Specifically, whenever I play a game, the music skips/stutters to the point where it becomes a distraction.  Sound works fine everywhere else, though--I can listen to music and watch DVDs without any problems of the sort.  (e.g.  An mp3 plays fine in Totem, but if I try to play the same song in a sample OpenAL project, it has the nasty skipping effect)

I am using an Acer Aspire 5570z with the 32 bit version of Ubuntu 7.04 (Feisty Fawn).

lspci returned:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

Does anyone know why the sound isn't working properly, or has anyone else had a previous experience with this problem?  If someone would point me in the right direction, I'd be grateful.  I did a few searches for similar issues, but so far I've got nothing.  If anyone has better luck than I do, could you please send me the link(s)?

Thanks in advance.

EDIT:  Some of the games I tried were Sauerbraten ([http://www.sauerbraten.org/](http://www.sauerbraten.org/)), SuperTux (obtained via the Add-Remove Applications program), Neverball (also obtained via the Add-Remove Applications program), and Battle for Wesnoth (obtained the same way).

---

### Post by Explodinglemur on 2007-10-20
I'm having similar issues, documented what I've tried so far here: [http://ubuntuforums.org/showthread.php?t=580726](http://ubuntuforums.org/showthread.php?t=580726)

---

