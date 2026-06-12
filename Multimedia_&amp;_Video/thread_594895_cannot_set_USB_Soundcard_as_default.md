---
title: "cannot set USB Soundcard as default"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by SpaceTeddy on 2007-10-28
OK, been reading in the forums for a while, but i cannot find a solution to this problem.

I have a Samsung X10 laptop with an onboard Intel ICH4 Sound chipset. Now, the sound itself is not a problem, the laptop is playing everything fine, but the speakers in the laptop are crap and the headphones out interefere with the hd and give me all scratchy noises in the background. Since that problem existed like... always... i bought myself a usb soundcard which i plug in and it gives me proper sound. 

And now i am trying to get that working in ubuntu. As i said, the onboard sound is fine - just the USB is not workin. And i cannot disable the onboard soundcard. I have tried unload the driver for the ICH4 chipset - still no luck.

I have used the Gnome supplied manager to change the soundcard
I have used played with the .asoundconf and got nothing to work...
I have tried gstreamer-properties...

really, i am at loss.

to leave anyone willing to help me not totally in the dark, here is some information about my system

aplay -l
> 
**** Liste von PLAYBACK Geräten ****
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 0: Intel ICH [Intel 82801DB-ICH4]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: I82801DBICH4 [Intel 82801DB-ICH4], Gerät 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 1: default [C-Media USB Headphone Set  ], Gerät 0: USB Audio [USB Audio]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 2: Modem [Intel 82801DB-ICH4 Modem], Gerät 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0


asoundconf list
> 
Names of available sound cards:
I82801DBICH4
default
Modem


lspci
> 
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
02:05.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:07.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)


lsusb
> 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0f62:1001 Acrox Technologies Co., Ltd 
Bus 001 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 0000:0000  


so, i anyone can tell me how i can set the usb soundcard so that everything defaults to it - that would be great...

What i forgot to say... if i launch xmms and choose the usb soundcard directly, i can hear sound over it. also, gdm defaults to the usb soundcard.
Just everything else that uses some default device does not... 

please, anyone help me - i am going crazy here...

---

### Post by eggdeng on 2007-10-28
Take a look at the section Configuring Default Soundcards in [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by KalTorak on 2007-12-07
take a look at my post [http://ubuntuforums.org/showthread.php?t=492241]("http://ubuntuforums.org/showthread.php?t=492241")

hope it can help

---

