---
title: "Tv Card Doesent work"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by anaoum on 2005-10-21
Hello,

i have a tv card in my pc, im not sure what brand it is, but its code number from the user mannual is "PV-BT878P+ w/FM". I have tried to use tvtime and xawtv, neither of them work. Im not sure if ubuntu has even detected it. Could somebody tell me how i can make it work.

Thanks

---

### Post by ilans on 2005-10-22
[QUOTE=anaoum]Hello,

i have a tv card in my pc, im not sure what brand it is, but its code number from the user mannual is "PV-BT878P+ w/FM". I have tried to use tvtime and xawtv, neither of them work. Im not sure if ubuntu has even detected it. Could somebody tell me how i can make it work.

Thanks[/QUOTE]

Please write the output of:
code:
lspci

---

### Post by burok on 2005-10-22
maybe it helps :)

[http://www.ubuntuforums.org/showthread.php?t=68983&highlight=pixelview](http://www.ubuntuforums.org/showthread.php?t=68983&highlight=pixelview)

---

### Post by anaoum on 2005-10-22
francis@francis:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440-SE] (rev a3)

---

### Post by anaoum on 2005-10-23
hello,

i ran "tvtime-scanner" 

but all it returned was "No Signal"

what does this mean??

---

### Post by ilans on 2005-10-23
[QUOTE=anaoum]francis@francis:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440-SE] (rev a3)[/QUOTE]

I think that you have a pinnacle PCTV card.
Anyway. I have this card and had  problem like you with the card.

Try to add:
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
to Device section in /etc/X11/xorg.conf
In my pc it solve my problem' and I can watch TV

In my pc the device section looked like this:
code:      
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
EndSection

In your pc the graphic card is different so don't change the value:
"Identifier" and "driver"
anyway make a copy of the file before you edit it

---

### Post by jeffreyvergara.NET on 2005-10-23
I have also this problem with my HDTV Wonder PCI

> 0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controll er/Host-Hub Interface (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Br idge (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 0 2)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 I DE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Contr oller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200 ] (rev a1)
0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01 )
0000:02:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
0000:02:0d.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:02:0d.2 Multimedia controller: Conexant: Unknown device 8802 (rev 05)


I add 
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
to Device section in /etc/X11/xorg.conf

under my video card Device Section, but still no luck.

---

### Post by ilans on 2005-10-23
[QUOTE=jeffreyvergara.NET]I have also this problem with my HDTV Wonder PCI



I add 
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
to Device section in /etc/X11/xorg.conf

under my video card Device Section, but still no luck.[/QUOTE]

did your tvtime application start and than close, or not run at all.
open terminal and write:
code:
tvtime

paste all terminal error messages here

---

### Post by anaoum on 2005-10-24
Hello,

[QUOTE=ilans]
Try to add:
        Option "VideoOverlay" "on"
        Option "OpenGLOverlay" "off"
to Device section in /etc/X11/xorg.conf[/QUOTE]

i tried this but i still get the same problem.

---

### Post by anaoum on 2005-10-24
Hello,

when i open tvtime in a terminal, i dont get any errors, even when i scan for channels.

---

### Post by anaoum on 2005-10-27
Hello,

ive tried following all the instructions on this page: [https://wiki.ubuntu.com//HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com//HardwareSupportComponentsMultimedia) but still no luck

somebody please help me!

thanks,

---

