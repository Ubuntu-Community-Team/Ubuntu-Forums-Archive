---
title: "No sound on ICH8"
date: 2011-12-01
forum: Multimedia Software
---

### Post by nickk93 on 2011-12-01
A few days ago I have installed the NVidia Geforce 210 to replace my Geforce 7500 for its hardware decoding capabilities on a system which is mainly used for HD sattelite tv through VDR and XBMC as a frontend. 

What surprised me after installing this card is that my onboard soundcard has suddenly disappeared and my only option is to use the HDMI output. It doesn't even show up in lspci:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:01.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:04.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)

```

Has anyone experienced this problem and maybe knows a solution to this, because no sound is quite annoying! FYI: I'm running yavdr 0.4.0 which is based on Ubuntu 11.04 x64 with only openbox as a dm.

---

### Post by MoreOrLess on 2011-12-01
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by nickk93 on 2011-12-03
[http://www.alsa-project.org/db/?f=f8d85154c53b0e10468fcc9630014fd6b8a83c9f]("http://www.alsa-project.org/db/?f=f8d85154c53b0e10468fcc9630014fd6b8a83c9f")

---

### Post by MoreOrLess on 2011-12-04
Try disabling the onboard audio in the BIOS, booting, then reboot and enable the audio.
EDIT: Oh, and you have pulseaudio disabled. I'm not sure if you did that on purpose or not...

---

### Post by nickk93 on 2011-12-14
I've checked my BIOS and it was quite stupid not to check it earlier, because my onboard audio was on auto-mode and because of the audio-out capabilities of my graphics card, it had automatically been turned off, so I swiched it to enabled and now everything works as it should.

---

