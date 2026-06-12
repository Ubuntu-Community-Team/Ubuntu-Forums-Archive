---
title: "Must restart system to get HDMI audio working on Lucid"
date: 2010-05-23
forum: Multimedia Software
---

### Post by gabspeck on 2010-05-23
Hi there!

I'm using Ubuntu 10.04 64-bit on a Dell Inspiron 1525 laptop that's got an HDMI a/v output which I use to plug in a Sony Bravia TV. On Karmic, both HDMI video and audio output would work with no need to restart the system, but since I upgraded to Lucid, I must restart Ubuntu to get HDMI audio working on my TV after choosing the "Digital Stereo (HDMI) Output + Analog Stereo Input" (or any other profile which uses HDMI output) on the Sound Preferences applet. The system is fully up-to-date.

Any thoughts? This is the output of lspci:

```
gabriel@gabriel-laptop:~$ lspci
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
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by gabspeck on 2010-05-23
bump

---

### Post by danbodoh on 2010-05-23
You and I are working on exactly the same problem today on the same kind of machine.  I've had no luck on the Inspiron 1525 either, except by rebooting with the HDMI cable plugged in, and then possible switching from HDMI -> analog -> HDMI audio.

---

### Post by gabspeck on 2010-05-24
> **danbodoh said:**
> You and I are working on exactly the same problem today on the same kind of machine.  I've had no luck on the Inspiron 1525 either, except by rebooting with the HDMI cable plugged in, and then possible switching from HDMI -> analog -> HDMI audio.

That's exactly what I have to do to get it working today; I wonder if there's at least any service I could restart so that I wouldn't need to restart the computer just to get audio on the TV!

---

### Post by farbird on 2010-05-24
did u upgrade your alsa to the latest?? ie manual upgrade.

---

### Post by gabspeck on 2010-05-24
> **farbird said:**
> did u upgrade your alsa to the latest?? ie manual upgrade.

How, exactly?

---

### Post by farbird on 2010-05-26
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by farbird on 2010-05-26
u might wanna try to upgrade your nvidia driver as described by me here


[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9361378&postcount=2](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9361378&postcount=2)

---

### Post by misosofos on 2010-08-26
I can't use HDMI. It doesn't work for me. My screen is detected with another name (I suppose the real manufacturer). I just get the well-known black screen. Any ideas? Thank you!

---

