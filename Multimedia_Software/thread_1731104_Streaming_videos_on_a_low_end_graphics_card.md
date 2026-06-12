---
title: "Streaming videos on a low end graphics card"
date: 2011-04-16
forum: Multimedia Software
---

### Post by psycho5 on 2011-04-16
hi, my friend she has a computer with ubuntu 10.04 32 bit installed, the latest update to flash 10 was also installed. The computer can't play any streaming videos fullscreen, it just has audio and the video is replaced by a white screen. 

Can anyone help me troubleshoot this? Thanks 

```
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
ash@ash-desktop:~$ 

```

The system has 1gb of ram running on Amd Athlon 64 3000+ processor.

*Edit* sometimes after exiting the nonresponsive fullscreen, it will say flash plugin has crashed.

---

### Post by owise1 on 2011-04-16
I had a problem with fullscreen and flash - found this and worked for me

[http://ubuntuforums.org/showthread.php?t=1271256](http://ubuntuforums.org/showthread.php?t=1271256)

---

### Post by psycho5 on 2011-04-16
tried it, didn't work.

---

### Post by psycho5 on 2011-04-16
is it a flash problem or lack of powerful hardware? i'd like to narrow it down cause if its flash nonfree thingy then maybe an alternative could be there.

---

### Post by psycho5 on 2011-04-16
how do i find out the amount of video ram? and other details about this card?

---

### Post by psycho5 on 2011-04-16
I went to gstreamer-properties videos tab and the default input can't be changed to (X11/XShm/Xv) does that mean the video card drivers can't handle it? its a s3 unichrome pro ver 01 driver.

---

### Post by K_45 on 2011-04-16
Google flashaid, its a Firefox add-on, then execute the script. I'd use Xubuntu on that system instead of the regular GNOME environment that comes with Ubuntu.

---

