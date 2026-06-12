---
title: "Sound Card Problems - Alsa Drivers"
date: 2008-11-29
forum: Multimedia Software
---

### Post by johnveix on 2008-11-29
Ok I am completely new to Ubuntu, I just installed last Saturday and have been working all week to get the proper drivers for all my cards and devices. So far I've gotten everything to work but the sound. I have tried to search and have viewed countless guides, but am getting extremely frustrated as I can't figure out what to do. Now I have searched google countless times and it seems I need to install the Alsa Drivers. Only problem is that I'm used to being spoon fed by Microsoft with GUIs to guide me through the installation, and I can't figure out how to install/compile the drivers through the terminal, which is what I think the guides tell me to do.  

So basically what I'm looking for is for someone to walk me through step by step what commands to input to install the drivers, and even where to input them. I am a complete noob desperately looking for help!

---

### Post by Skripka on 2008-11-29
1st things first, but not necessarily in that order:

What soundcard, or on-motherboard sound are we dealing with?

---

### Post by johnveix on 2008-11-29
It's an older gateway laptop. It uses the  AC'97 audio codec, and on windows they worked with the realtek drivers.

---

### Post by Skripka on 2008-11-29
Ubuntu should come with the ALSA drivers already installed....


1) Open up Synaptic Package Manager

2) In the search box type Alsa

3) In the results you shouls see "Alsa-base" and "Alsa-utils" amonst other things, are these already installed?  If not install them (right click, select "install" and click apply).

---

### Post by johnveix on 2008-11-29
Yeah there all in the package manager, so I guess that's not the problem. But I still have no sound output from speakers or headphones..

---

### Post by Skripka on 2008-11-29
> **johnveix said:**
> Yeah there all in the package manager, so I guess that's not the problem. But I still have no sound output from speakers or headphones..

They should not only be there, but Alsa-base etc should be installed :)

Do you have a software mixer installed (such as Alsamixergui in Synaptic)?  Sometimes the default levels are wierd.  If your motherboad has a Realtek audio chipset on it--odds are it should just work, my mobo as a ALC883 Realtek audio chipset on it-and it worked from install.

---

### Post by johnveix on 2008-11-29
Okay there all there and installed, and I looked in the alsamixergui and all the levels seem to be turned up all the way, but I'm still not getting any sound.

---

### Post by Skripka on 2008-11-29
> **johnveix said:**
> Okay there all there and installed, and I looked in the alsamixergui and all the levels seem to be turned up all the way, but I'm still not getting any sound.

Please open Terminal and type the following and post the output:

```

lspci

```

---

### Post by johnveix on 2008-11-29
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
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by Skripka on 2008-11-29
Okay, I've done some searching for you, and here are a few leads to seek out:

[http://ubuntuforums.org/showthread.php?t=161193&highlight=82801db-ICH4](http://ubuntuforums.org/showthread.php?t=161193&highlight=82801db-ICH4)

The link in post 16 may be helpful, which leads here;

[http://ubuntuforums.org/showthread.php?p=5169942](http://ubuntuforums.org/showthread.php?p=5169942)



I also hunted down your chipset (Intel 82801DB) on the ALSA website, and folks have reported issues using this older laptop and it's audio chipset under *nix:

[http://alsa.opensrc.org/index.php/82801DB](http://alsa.opensrc.org/index.php/82801DB)

Also there is some good troubleshooting tips o'er on the ALSA Wiki:

[http://alsa.opensrc.org/index.php/TroubleShooting](http://alsa.opensrc.org/index.php/TroubleShooting)

---

### Post by johnveix on 2008-11-29
Thank you so much I finally figured it out. It was the external switch that needed to be added to the mixer so I could disable it. Those posts worked fantastic thank you! 

On the other hand, it took me 4 days to figure out how to uncheck a box :mad:

---

### Post by Skripka on 2008-11-29
> **johnveix said:**
> Thank you so much I finally figured it out. It was the external switch that needed to be added to the mixer so I could disable it. Those posts worked fantastic thank you! 

On the other hand, it took me 4 days to figure out how to uncheck a box :mad:

You're welcome :)


That is how it is sometimes.  In Linux, the only way you learn things is by having to fix them--and when the light-bulb and "eureka" occur finally, you're usually at least a bit wiser than when you started.  The 1st problems are always the roughest and most annoying, and from there is gets easier.

Now kick back have a beer and celebrate.:popcorn:

---

