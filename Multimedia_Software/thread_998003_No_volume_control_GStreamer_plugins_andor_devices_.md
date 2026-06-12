---
title: "No volume control GStreamer plugins and/or devices found"
date: 2008-11-30
forum: Multimedia Software
---

### Post by ^NeoPhyt3^ on 2008-11-30
Hello Everyone.. my soundcard suddenly stopped working ... 
It works fine in Failsafe GNOME mode .. 

On clicking on volume control i get the message 
"No volume control GStreamer plugins and/or devices found"

On doing aplay -i 
I get the message "No soundcards found"
After doing lspci i get the following log..

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by ^NeoPhyt3^ on 2008-11-30
Guys need help ... 

Please help ..

---

### Post by unclesam.xu on 2008-11-30
Just like my vix8233. and webcam too. it happened after upgrade to 2.6.24-22, you can just use 2.6.24-21-generic to start the ubuntu and then it is working. But not with 2.6.24-22-generic. It is a glitch in new kernel for sure

---

### Post by ^NeoPhyt3^ on 2008-12-01
Hey..Thanks for Reply ...
But I am new to ubuntu and can u tell me how can i start ubuntu using the old kernel ??

---

### Post by jose158 on 2008-12-01
Try typing in a terminal (Applications > Accessories > Terminal):
```
usermod -g audio <YOURUSERNAME>
```

---

