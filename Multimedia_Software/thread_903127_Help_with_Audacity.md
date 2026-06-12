---
title: "Help with Audacity"
date: 2008-08-28
forum: Multimedia Software
---

### Post by johnnyxxxcakes on 2008-08-28
I used to record a few files off of the Internet using Audacity when I was on Windows. I downloaded the Linux version of Audacity from Synaptic Package Manager, but my issue is that the record source (or whatever it's called) button isn't there.

I'll show you what I'm talking about. This is exactly what I used on Windows:
[http://i37.tinypic.com/eqs707.jpg](http://i37.tinypic.com/eqs707.jpg)

The part I circled red isn't on the version I downloaded for Ubuntu. Here is my version:
[http://i34.tinypic.com/esraty.png](http://i34.tinypic.com/esraty.png)

Any idea on what I can do to fix this, or if it's a different button on Ubuntu.

Thanks.

---

### Post by Crafty Kisses on 2008-08-28
Post the output of > lspci

---

### Post by johnnyxxxcakes on 2008-08-28
> **Codename said:**
> Post the output of > lspci

john@john-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
john@john-laptop:~$

---

### Post by vanadium on 2008-08-28
You are using Audacity 3 under Linux. With "View - Toolbars - Device toolbar", you can display what you want but I am not sure if this is going to help a lot.

A good way to monitor if Audacity is receiving a signal is to click on the down arrow on the Input level meter and select "Start monitoring". Then start the Volume control applet.

To test, I tried to record audio from a playing youtube clip, and it is not at all obvious. The PCM control is controlling the sound from the video. However, I had a very weak signal. Then I turned all controls on using Edit - Preferences in the Volume Control applet. Extra tabs appear. I found I had to activate "Mic Boost (+20 dB)" (even though I am not recording from the microphone) in order to receive a signal of proper stength, that then can be adjusted with the PCM slider in the Volume control applet.

For a strange reason, Audacity defaults recording in 8000 Hz even if the defaults are set differently, even when playing back a CD quality file.

---

