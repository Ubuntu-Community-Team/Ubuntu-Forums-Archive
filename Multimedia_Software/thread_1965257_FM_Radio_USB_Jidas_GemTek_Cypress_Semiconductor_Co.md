---
title: "FM Radio USB Jidas GemTek Cypress Semiconductor Corp. CY7C63001"
date: 2012-04-25
forum: Multimedia Software
---

### Post by fadec on 2012-04-25
Given: USB FM Tuner Jidas/GemTek. Under  9th FreeBSD is detected & managed easily by ufmcontrol. Under Ubuntu 11.10 - no way (neither radio nor fmtools).

**lsusb**
Bus 004 Device 003: ID 04b4:1002 Cypress Semiconductor Corp. CY7C63001 R100 FM Radio

Device **/dev/radio0 81, 0** exists, access rights 666

**radio** -c /dev/radio0 -f 104.5
tuned 104.50 MHz
VIDIOCGAUDIO: Invalid argument
VIDIOCSAUDIO: Invalid argument

**fm** -d /dev/radio0 104.5
fm: VIDIOC_QUERYCTRL: Invalid argument

 [IMG]http://forum.ubuntu.ru/Smileys/webby/cry.gif[/IMG] [IMG]http://forum.ubuntu.ru/Smileys/webby/cry.gif[/IMG] [IMG]http://forum.ubuntu.ru/Smileys/webby/cry.gif[/IMG]

Help, please...

---

