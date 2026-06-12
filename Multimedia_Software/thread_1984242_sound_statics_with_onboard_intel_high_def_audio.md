---
title: "sound statics with onboard intel high def audio"
date: 2012-05-21
forum: Multimedia Software
---

### Post by moita001 on 2012-05-21
Using ubuntu 12.04 fresh install, just formated and installed using a cd copy.

hardware:

VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

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

00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA Controller [IDE mode] (rev 01)

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)

01:04.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

------------------------------------------------------------

The problem:

When i play any kind of media, audio or video (i tried several file types .mp3, .flac, .avi, .mp4, etc...) the audio quality is good but it's like it has some static. It's hard to explain, like it goes off and on "blinking".
Also i don't know if it has something to do with the problem, but every now and then my mouse stops working. To get it back i have to open console and “sudo modprobe -r psmouse && sudo modprobe psmouse”.

---

### Post by moita001 on 2012-05-21
I forgot to mention, I'm using a headset, but I don't think it has a problem, since i tested the sound with a couple speakers and the "blinking" persists.

plus I followed this troubleshooting: 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I've got this result:
[http://www.alsa-project.org/db/?f=0b15355e4e8a6c11b108b0dd537b2c17ed7955af](http://www.alsa-project.org/db/?f=0b15355e4e8a6c11b108b0dd537b2c17ed7955af)

my alsa version:
Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25

I couldn't update the driver...

---

### Post by moita001 on 2012-05-26
and now there is no sound
also can't open alsamixer on terminal, it tells me the directory cannot be found...

---

### Post by moita001 on 2012-05-26
can anybody help me please
i can't make the sound work at all
reading a lot of material on the net but nothing seems to work.
seriusly thinking about giving up on ubuntu ¬¬

---

