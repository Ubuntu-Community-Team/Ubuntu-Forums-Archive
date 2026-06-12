---
title: "no sound Gateway 4026gz"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by animeh on 2007-06-05
I have done all that I have read to get sound, still I have no sound. I am very sorry for asking, but can any one help further.  I ave fiesty 7.04 and gateway 4026gz. I think that the sound card is ac'97. 

I would appreciate very much for anyones help.

---

### Post by eggdeng on 2007-06-06
Start by posting the output of ```
lspci
``` and ```
cat /proc/asound/cards
```

---

### Post by MianoSM on 2007-11-09
lspci:

```

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```
cat /proc/asound/cards
```

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 10
 1 [Modem          ]: ICH-MODEM - Intel 82801DB-ICH4 Modem
                      Intel 82801DB-ICH4 Modem at irq 10

```

---

### Post by eggdeng on 2007-11-10
Your card is an Intel 82801DB-ICH4 sound card / modem. I'm not familiar with these but you could do a forum search for this model or take a look at [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")
for troubleshooting help.

---

### Post by MianoSM on 2007-11-10
So far I have attempted to load Alsa drivers for it.

Still no audio. The Alsa utils, and lib are now installed as well - but no sound/audio what so ever.

Any file will play, and movies play, the driver appears to be installed, yet nothing. : (

Very disappointing.

---

### Post by Picatta on 2008-02-05
Hey, did you ever happen to find a way of fixing this problem?

---

