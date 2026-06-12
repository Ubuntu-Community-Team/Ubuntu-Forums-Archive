---
title: "No video out from webcam"
date: 2009-07-12
forum: Multimedia Software
---

### Post by zagabar on 2009-07-12
Hi there!

I got a Deltaco webcam (seems impossible to get a model name) that I tried to use in ubuntu Jaunty. It works flawlessly in windows. I have gotten other webcams to work in ubuntu by just letting it become video0 and then use that for output. However when I connect this cam, it doesn't work. It appears in lsusb and detects nicely as video0. The problem comes when using that for video output. It just gives no screen/a black screen depending on what application I use. I have tried vlc, mplayer, camorama, motion and cheese. The error outputs are scarce. Sometimes there are none. Motion just says unable to open for input, and cheese says:

libv4l2: error dequeing buf: input/output error


I think it has something to do with libv4l2 since I read that it could be some problems or something, but I don't really know what to do from here.

Help is really appreciated. =)

---

### Post by zagabar on 2009-07-13
Bump! 

No one has a clue? :(

---

### Post by zagabar on 2009-07-14
Please? =)

This problem is annoying and I cannot use the cam that I bought. :(

---

### Post by zagabar on 2009-07-17
Please-bump!

---

### Post by zipperback on 2009-07-17
Please provide the output from the following commands:

```

lsusb
lspci

```

Thank you.

- zipperback
:popcorn:

---

### Post by zagabar on 2009-07-17
Okay, here we go ^^ :

zagabar@jouka:~$ lsusb
Bus 001 Device 004: ID 0ac8:0323 Z-Star Microelectronics Corp. Luxya WC-1200 USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
zagabar@jouka:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
zagabar@jouka:~$

---

### Post by zagabar on 2009-07-19
Now what? =)

---

### Post by zagabar on 2009-07-27
Bump!

---

### Post by zagabar on 2009-08-02
Bump bump bump!

Please, no one knows how to fix this? =(

---

### Post by zagabar on 2009-08-14
Bumpeli

---

### Post by zagabar on 2009-08-16
bump

---

### Post by zagabar on 2009-08-21
Bumpeli

---

### Post by zagabar on 2009-08-27
Bump! (this is getting ridiculous. XD)

---

