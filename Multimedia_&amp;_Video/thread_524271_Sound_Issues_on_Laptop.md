---
title: "Sound Issues on Laptop"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by Zerloch on 2007-08-12
Hello Community

Henry here, new to Ubuntu.
I recently installed Feisty on my Asus A9 series laptop and was blown away by the fluidity of it's operation and huge repositories.

However, the only exception is that the sound is too soft, and the master volume does not change the volume.

These are the devices i have

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any help would be appreciated very much
Thanks in  advance

---

### Post by moore.bryan on 2007-08-13
*could you post the full output of ```
lspci
```?*

---

### Post by Zerloch on 2007-08-13
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 13)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 04)

Cheers man, hope it helps solve the problem.

---

### Post by moore.bryan on 2007-08-13
[I]try this... it took all this to get my sound working on a lenovo thinkpad z61e...
grab the alsa stuff and compile from source:
[alsa-driver-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")
[alsa-lib-1.0.14a]("ftp://ftp.alsa-project.org/pub/driver/alsa-lib-1.0.14a.tar.bz2")
[alsa-utils-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-utils-1.0.14.tar.bz2")
[alsa-tools-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-tools-1.0.14.tar.bz2")
[alsa-firmware-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-firmware-1.0.14.tar.bz2")
[alsa-plugins-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-plugins-1.0.14.tar.bz2")
[alsa-oss-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-oss-1.0.14.tar.bz2")
[pyalsa-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/pyalsa-1.0.14.tar.bz2")
and then run ```
alsamixergui
``` to set the volumes, ```
sudo alsactl store
``` to keep your settings and add ```
alsactl restore
``` to your /etc/rc.local file.
[/I]

---

### Post by Zerloch on 2007-08-13
Thanks for your help, I'll see how it goes.

---

### Post by moore.bryan on 2007-08-13
*no problem... just post any issues.*

---

### Post by Zerloch on 2007-08-13
My sound is now fully operational.
Thanks a bunch, dude.
I also learned what compiling from source is. I'm pretty new at Linux.

Now I can ROCK OUT!!
:guitar:

---

### Post by moore.bryan on 2007-08-13
[I]excellent...
and a good thing you dove into the well of compiling from source; it can be a useful tool.
keep on rockin' in the [foss] world![/I]

---

### Post by ashwinjm on 2007-11-12
I'm having similar problems on a Z61e - sound is not working for Flash player (i.e., Youtube) and for Skype. It does, however, work for Rhythmbox, and system sounds. I followed the instructions to get the latest ALSA driver and utilities, but it hasn't made any difference. Help!

---

