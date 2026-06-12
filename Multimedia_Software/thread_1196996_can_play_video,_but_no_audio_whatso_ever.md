---
title: "can play video, but no audio whatso ever"
date: 2009-06-25
forum: Multimedia Software
---

### Post by Navy139 on 2009-06-25
i have recently installed ubuntu9.04 on my LG R710 laptop and am having trouble playing audio of any kind on it.  i can pay dvd's and .avi's fine, but i am not getting any audio.  i have made sure that all sound devices are unmuted and up fully.  any suggestions?

---

### Post by jerrrys on 2009-06-27
what do you get when you do a sound test?

System>Preferences>Sound

---

### Post by philcamlin on 2009-06-27
sudo apt-get upgrade / sudo apt-get update

now do you get any audio ? :popcorn:

---

### Post by Navy139 on 2009-06-29
i get the following:

Sound events, Music and Movies, and sound playback in Audio Conferencing are set to auto detect
Sound Capture in Audio Conferencing is set to HDA Intel ALC663 Analog (OSS)
and Default Mixer Tracks is set to Realtek ALC663 (OSS Mixer)

I have played around with all the setting for the various sections to no avail.  
thanks for the suggestion

---

### Post by Navy139 on 2009-06-29
still nothing

---

### Post by loboc on 2009-06-29
The pulseaudio system might be sending sound to the pc speaker inside our box, try installing and running the pulse audio manager under streams theres is a goffy icon like a triangle thats hard to spot but you can select the output

---

### Post by Navy139 on 2009-07-02
update: i get this when i run lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

