---
title: "No Sound in Ubuntu 9.04"
date: 2009-10-21
forum: Multimedia Software
---

### Post by Whitey_22 on 2009-10-21
Hi,

I installed Ubuntu after deleting OpenSUSE off my laptop.  It's running great apart from having no sound at all.

I've looked at other threads on this and other boards and followed the solutions that worked for others to no avail.

Here is some outputs that may give you more information:

> **~ >aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


> **~ >lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
***00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)***
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Any help you provide would be great.

Thanks

---

### Post by RichardLinx on 2009-10-21
It's probably Pulse Audio:
Open a terminal and type:
```
sudo apt-get remove --purge pulseaudio
```
```
sudo apt-get install esound
```
```
sudo apt-get remove gstreamer0.10-pulseaudio
```
```
sudo apt-get install gstreamer0.10-esd
```
```
sudo /etc/init.d/alsa-utils restart
```

Then:
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
```

Reboot.

PS: Since you're a new user you probably don't have multimedia codecs installed. Type:
```
sudo apt-get install ubuntu-restricted-extras
```
For other multimedia playback (eg. DVD) see this wiki: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Whitey_22 on 2009-10-21
Hi, thanks for the help.  This has improved the situation, but not totally solved it.  I now get sound using headphones, but not through the speakers.  As I say, this is a big improvement as I couldn't get *any* sound before.

Edit:  Went into the mixer and unmuted "Surround Sound" and got the speaker sound.  Thanks for the help!

---

### Post by danm91 on 2009-10-23
How do i find the mixer to unmute surround sound, probably a really easy question but im still getting used to ubuntu

---

### Post by RichardLinx on 2009-10-24
> **danm91 said:**
> How do i find the mixer to unmute surround sound, probably a really easy question but im still getting used to ubuntu

Right click on the speaker icon in the top right corner of gnome-panel (Top menu) Select "Open Volume Control" and select preferences under the playback tab.

> Went into the mixer and unmuted "Surround Sound" and got the speaker sound. Thanks for the help!
No worries, I'm happy it fixed it for you. :)

---

