---
title: "Af9015 DVB-T tuner fails to tune"
date: 2010-03-12
forum: Multimedia Software
---

### Post by dandart on 2010-03-12
I've downloaded the firmware from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/) and placed it in /lib/firmware. I'm using Karmic. MythTV and Kaffeine both see the devices. They attempt to tune but I can't get any channels out because they can't tune. A little help please?

---

### Post by TopEnder on 2010-03-20
> **dandart said:**
> I've downloaded the firmware from [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/) and placed it in /lib/firmware. I'm using Karmic. MythTV and Kaffeine both see the devices. They attempt to tune but I can't get any channels out because they can't tune. A little help please?

G'Day dandart,   I tried MythTV on an earlier version of Ubuntu and had a lot of problems trying to get it to work did achieve a channel scan using dvbscan (never tried Kaffeine) maybe it my age anyway I had success with me-tv so I am now using it or VLC media player.   me-tv is in Ubuntu's Synaptic Package Manager or it can be downloaded from launchpad.net, / me-tv, both Michael Lamonthe and Scott Evans have been very helpfully in setting up me tv.   me-tv have a build in channel tuner which is easy to use along with me-tv in general.  TopEnder

---

### Post by steefjeqv on 2010-03-20
Hi, 

Not sure if this helps, but try copying the firmware to /lib/firmware/yourkernelversion.

yourkernelversion is the kernel you use (e.g. 2.6.31-20-generic).

Greetings,
Steven

---

### Post by babarosa on 2010-03-20
Dandart,

I am using v9.10 Karmic with MSI Digivox miniII which also uses the af9015 chip. It is an USB-device, so if yours too is one, try the following:

delete the downloaded firmware from /lib/firmware or whereever you copied it to.

stick your usb-device on, and being online, perform a firmware search by selecting from the (mine is german - similarily) menu "applications/system/hardware drivers". With a bit of luck your device is recognized and the drivers/firmware will be installed

install me-tv from this ppa [https://launchpad.net/~me-tv-development/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~me-tv-development/+archive/ppa?field.series_filter=karmic)

when you first start me-tv, you either can load a channels.config file or do a search

Good luck!

---

