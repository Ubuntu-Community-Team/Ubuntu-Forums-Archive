---
title: "Enabling HDMI audio on Dell 1525 without rebooting with HDMI plugged in"
date: 2009-11-20
forum: Multimedia Software
---

### Post by ukhi on 2009-11-20
[B]NOTE: I am NOT trying to install HDMI. Both HDMI audio and video work.
I would like to know why it works so I am am not cargo-culting the procedures every time I connect my laptop to my TV

[/B]I have a virgin install of Ubuntu 9.10 on my Dell Inspiron 1525.
Overall, I am very pleased with the HDMI video support.
I can get HDMI video out simply by plugging in a cable and pressing Fn+F8.

However, HDMI audio still remains a mysterious black art involving modifications  alsamixer, padevchooser, PulseAudio daemons, default.pa, and possibly sacrificing an MCSE during a planetary alignment.

My problem is that I cannot enable HDMI audio out without first rebooting my laptop with the HDMI cable plugged in.
If I plug my cable into my laptop when it is running and go to "Sound Preferences" > "Hardware" > "Profile" and select "Digital Stereo (HDMI) Output" I get no sound.
If I plug my cable in and reboot, I can select "Digital Stereo (HDMI) Output" and immediately get sound.

I have tried installing paprefs, padevchooser, and paman with no success.
I have gone into alsamixer and enabled 'IEC958', 'IEC958 D' and 'IEC958 1'.
I have added "**load-module module-alsa-sink device=hw:0,3**" to /etc/pulse/default.pa

In all those cases I was only able to get HDMI audio by rebooting the computer with the HDMI cable plugged in.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```This whole "reboot for sound" procedure has the fetid reek of cargo-cult.
I would like to know the better/correct way of enabling HDMI audio as rebooting every time I want to use my laptop as a DVD player is rather awkward.
*[SIZE=1]... and I am running out of MCSEs[/SIZE]*;)

Thank you for your help

---

### Post by hardyn on 2010-04-21
exactly the same question... however i guess being on the cusp of lucid, maybe this is something that will just work.

---

### Post by gustavofuhr on 2010-08-02
I have the same problem, with ubuntu 10.04 on a dell inspiron 1525. I saw in other posts that recommend updating alsa. I'd rather wait for the new alsa be available in the official repositories.

---

