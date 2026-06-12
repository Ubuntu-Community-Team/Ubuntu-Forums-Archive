---
title: "Random system freeze when opening video in VLC / SMPlayer"
date: 2008-12-22
forum: Multimedia Software
---

### Post by badger_8007 on 2008-12-22
Hi :(

I am getting ramdom system freezes when I try to open a video with VLC or SMPlayer, is not related to a specific video, but it happens more with SMplayer. Usually i double click a video from Konqueror and when it launches the video on either player it just opens the player window and it doesn't show video, but i can hear audio. At that moment i am able to move the mouse but the keyboard is unresponsive, so i can not restart X (ctrl+alt+bcksp) or make any other key command to work, and the whole desktop is not responding. Usually I have to shut down my laptop using the power button and power it up again.

The strange thing is that I can hear the audio of the video actually playing normally, and i can wait until the video finishes and the audio keeps playing without any issue, i only can not use any other thing apart from the mouse (only  move it around the screen).

Once i restart i can open the video that caused the problem and it can play fine. and I would not have any other problem until later, and that may be _minutes or days_.

Here is the output from lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

The computer is a Toshiba Laptop A135-S4427, Intel Centrino Duo T2250 @ 1.73 GHz, 1 GB RAM, 120 GB HD, dual boot Kubuntu Hardy 8.04 - Windows Vista, using kernel 2.6.24.22-generic.

VLC version is 0.9.3 grishenko version (i was using the version found on the ubuntu repos but it did the same, so i thought upgrading would fix it... wrong)

Mplayer 1.0-rc2 svn28035
SMplayer 0.6.5.1

I have the most usual codecs installed (ffmpeg, xvid, lame, w32, etc.), everything plays fine, including DVDs. I use pulseaudio as audio driver, i installed it following a how-to from the forums and i have had no problems regarding it. Actually the freezing presented before when i was using only ALSA. The audio outputs from the players are using pulseaudio.

I should also note that i have enabled Compiz-Fusion w/ Emerald.

Hope somebody could give me some advice, or point to any other thread covering a similar issue.

---

### Post by rvm4000 on 2008-12-23
Have you tried to select a different video output driver? In smplayer, Preferences->General->Video.

---

### Post by zantetsuken on 2008-12-23
im having a similar issue here as well, i just made a thread on that like 10 misn ago anyone please help? but im running ubuntu not kubuntu.

---

### Post by badger_8007 on 2008-12-24
Actually I am using XV as the video output by default, but I tried X11 but the quality gets very degraded, and with OpenGl I need to shutdown compiz, because otherwise the video flickers incesantly. Anyway, with X11 i got 1 freeze also, but I didn't test it for very long, then returned to XV as output.

Thanks for the advice. Any other ideas???

---

