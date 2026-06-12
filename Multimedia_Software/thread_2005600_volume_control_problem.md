---
title: "volume control problem"
date: 2012-06-17
forum: Multimedia Software
---

### Post by azi_linux on 2012-06-17
hi all, my volume control does not effect actual sound and the sound is always at 100%, i have tried many methods; alsamixer and pressing M, pulse volume control and installed gnome mixer but still nothing. i checked the bios to see if i could disable the internal speaker but that didnt work. please help me


lspci
00:00.0 Host bridge: Intel Corporation E7525 Memory Controller Hub (rev 0a)
00:02.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A (rev 0a)
00:03.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A1 (rev 0a)
00:04.0 PCI bridge: Intel Corporation E7525/E7520 PCI Express Port B (rev 0a)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
40:00.0 VGA compatible controller: NVIDIA Corporation NV44 [Quadro NVS 285] (rev a1)

---

### Post by azi_linux on 2012-06-18
forgot to mention, with unity i fixed it so it works properly, sound through my own speakers and volume control affecting it, after installing xfce with;

sudo add-apt-repository ppa:xubuntu-dev/xfce-4.10
sudo apt-get update
sudo apt-get dist-upgrade

i managed to switch it from the internal speakers to external but the volume control has no effect on it at all.

---

