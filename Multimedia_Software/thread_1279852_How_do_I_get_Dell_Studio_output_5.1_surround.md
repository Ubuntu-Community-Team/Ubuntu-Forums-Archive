---
title: "How do I get Dell Studio output 5.1 surround?"
date: 2009-10-01
forum: Multimedia Software
---

### Post by rafalcieslak on 2009-10-01
Hello,

The notebook I use is Dell Studio 17. It have 2 headphone outputs and line-in. At first I thought "fine, this way I will get only a stereo output, these headphone outlets are surely connected together so that they output the same signal". But on windows vista (pre-installed on this notebook) I found a nice application that _allowed me to get full 5.1 surround_ sound! It used one headphone outlet to output Front channel, the second for Center/Sub and line-in outlet for Rear channel (that really surprised me, I was sure line-in is just an input, seems I was wrong;P ). I enjoyed the music!

Well then, I am quite sure my notebook CAN play 5.1 surround sound. Now I want to get this feature working on Ubuntu;)

I searched the forums and the Internet, but didn't found anything that worked to me. I set pulseaudio to 6 channels, I un-muted everything in alsamixer, but, of course, thats not enough.

=======
I want to use both** headphone outlets** and **line-in** (that is three jack outlets)** to output 5.1 sound**. I am NOT a linux newbie, compiling ALSA shouldn't be a problem. I have some basic experience of using sound in Ubuntu. However, I have NONE experience with hardware support, and I am even not sure how to check my soundcard chipset :P

Does anyone can help me? Any tips are welcome;)

---

### Post by HappyFeet on 2009-10-01
> **rafalcieslak said:**
> I am even not sure how to check my soundcard chipset :P


Do
```
lspci
```
to show all your device chipsets.

---

### Post by HappyFeet on 2009-10-01
Also right click your speaker icon>open volume control>preferences. Check if you have the right things checked off.

---

### Post by rafalcieslak on 2009-10-01
Thanks. Thats what I got:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

I can see two lines labeled as "Audio Device":

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
```

> right things checked off. 
Well what are these right things? As for now I have everything checked on;) I can list them, if there is such need.

---

### Post by rafalcieslak on 2009-10-05
Wow. I have upgraded my system to Karmic Beta, and now I can choose "4.0 output + stereo input" in Audio settings. That is ALMOST what I wanted;)

---

### Post by pappfer on 2009-11-09
@rafalcieslak: I just realised that I opened a topic not long after you did with the same problem. Here it is: [http://ubuntuforums.org/showthread.php?t=1286863](http://ubuntuforums.org/showthread.php?t=1286863)

Note that not only Vista was able to give 5.1 sound for our notebook but Jaunty was also able to do so. You could just set an option to "set line-in as output" and 5.1 was working fine. Now I can't find this option in Karmic and I really miss it, cause my rear speakers not working.

---

