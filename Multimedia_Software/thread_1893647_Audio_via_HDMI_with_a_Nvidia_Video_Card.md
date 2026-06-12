---
title: "Audio via HDMI with a Nvidia Video Card"
date: 2011-12-10
forum: Multimedia Software
---

### Post by Kottizen on 2011-12-10
Good day everyone,

Two days ago I got my new PC and it's working like a charm. After having downloaded Kubuntu I immediately installed it and I'm not back on track! Two months ago I purchased and installed a home cinema system with a few speakers and an amplifier. There's both a TV box and a blue-ray player connected to the amplifier, as well as a lonely HDMI cable that currently isn't used for anything.

I've used that lonely little HDMI cable in the past to play music from my laptop (which also happens to run Kubuntu 11.10). It has worked from day one and it's still working. The MacBook Pro works as well.

The problem I'm experiencing is that it doesn't work on the new PC I bought. I plugged in the HDMI cable into what I think is the video/graphics card and expected it to play music there when I chose HDMI in KDE's sound preferences. It did not.

I plugged the HDMI cable into the built-in HDMI port. It still didn't work.

So I followed the tutorial [here](http://ubuntuforums.org/showthread.php?t=1668737), and I came to this step:
"If you don't receive a 1 for one of the devices you need to return to Step 1) and ensure you have a properly patched alsa 1.0.23 or 2.6.35+ kernel."

I went to the linked tutorial ([https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)) but it seemed to be out of date as firstly I had to use natty's repository and secondly there wasn't any package available for the kernel version I run (3.0.0-14-generic). It might be possible that way, but when I saw that I promptly stopped.

After a fresh installation of Kubuntu again I had the same problem. Via #kubuntu I was introduced to [http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_audio_over_HDMI_on_nVidia_GeForce/nForce_controller](http://wiki.xbmc.org/index.php?title=HOW-TO:Setup_audio_over_HDMI_on_nVidia_GeForce/nForce_controller) and I tried that. Didn't get a single error (from what I could see), but it didn't work. Instead of using 0,3 I used 1,3 because that's what I could see from my aplay -l output:
> **** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I also tried with 1,7, 1,8 and 1,9. Didn't work.

Worth to mention is that it works on the Windows partition on the same PC.

Here's my lspci:
> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)            
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF114 [GeForce GTX 560] (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0e0c (rev a1)
03:00.0 PCI bridge: ASMedia Technology Inc. Device 1080 (rev 01)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

and my alsamixer:
[http://wstaw.org/m/2011/12/10/plasma-desktopjk1501.jpg](http://wstaw.org/m/2011/12/10/plasma-desktopjk1501.jpg)
As you can see, the S/PDIF is not muted, but set to 00. I can't find a way to increase that value.

The driver I'm using looks like this (I bet there is a fancier terminal command giving more information - if you need it, please tell):
[http://wstaw.org/m/2011/12/10/plasma-desktopgc1501.jpg](http://wstaw.org/m/2011/12/10/plasma-desktopgc1501.jpg)

All help appreciated and thanks in advance,
Martin

---

### Post by wolfen69 on 2011-12-10
Even though the info [here]("http://ubuntuforums.org/showthread.php?t=1668737") is slightly dated, it may be of some help to you.

---

### Post by Kottizen on 2011-12-11
I tried that, but because of the outdated content I didn't succeed.

---

### Post by BarryDocks on 2011-12-11
try this:
[http://ubuntuforums.org/showthread.php?t=1646202]("http://ubuntuforums.org/showthread.php?t=1646202")

---

