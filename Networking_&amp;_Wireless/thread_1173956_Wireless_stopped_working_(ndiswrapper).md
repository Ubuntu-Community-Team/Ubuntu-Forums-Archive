---
title: "Wireless stopped working (ndiswrapper)"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by GetOutOfBox on 2009-05-30
distro = Linux Mint 6 Felicia

Hi, I just recently installed my wifi adapter through ndiswrapper (no it's not mad wifi compatible and doesn't have a manufacturer linux driver). It worked fine at first for about 2 boots, then my adapter just no longer appeared in the network manager. The drivers still said hardware present when I checked with ndiswrapper. My device worked completely fine, the internet functioned properly then just stopped. I googled it and found a thread over at the ubuntu forums that said to remove from modprobe then add again (modprobe ndiswrapper -r, modprobe ndiswrapper). That didn't work. So I uninstalled the drivers and than reinstalled them again doing exactly what I did the firs time. Restarted and still no response. Something to take note of though would be that I installed a few programs through mintInstall (notably wine) and installed the linux ati driver for my video card. Here are my specs:

Wifi adapter=TP-Link TL-WN620G USB adapter
mobo: Asus and Fujitsu-Siemen P5SD2-FM
CPU: Intel Pentium 4 2.8 GHZ HT Prescott core
Video Card= ATI Radeon 4350

The driver for the vid card was installed through Envy-NG

Linux Mint version 6

Software installed before the problem started: A few assorted 3D games, Wine, Wine-door (a wine GUI), updated firefox.

I didn't update Ndiswrapper, its the same version that ships with Mint 6.

Thanks in advance!

---

