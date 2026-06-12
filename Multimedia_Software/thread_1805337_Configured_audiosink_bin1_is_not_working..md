---
title: "Configured audiosink bin1 is not working."
date: 2011-07-15
forum: Multimedia Software
---

### Post by alpar1225 on 2011-07-15
I've tried everything that I could find on google, and nothing is working.  Whenever I try to play anything in rhythmbox, the song doesn't play and an "x" shows up next to the song title.  When you click on the "x" it says,
```
Configured audiosink bin1 is not working.
```
[IMG]http://i51.tinypic.com/9097if.png[/IMG]

Here's what lspci says:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
08:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)

Hopefully someone can help?

---

### Post by buntudawg on 2011-07-30
Hi alpar1225

I don't know if you are still trying to fix this, but I stumbled across your post when trying to find the solution to the same problem.

In the end:
```
sudo apt-get install gstreamer0.10-alsa
```worked for me.

Hope this helps if you haven't fixed it yet.

---

### Post by .... on 2011-07-30
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink pulsesink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink pulsesink
```

---

### Post by MaxxJ on 2011-08-01
Thanks buntudawg, just worked for me on Lunbuntu with Rhythmbox.

---

