---
title: "Wireless Tethering Stopped Working After nVidia Video Card Install"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by power.supply on 2012-11-18
Hey everyone,

Hoping I can get some help with this. Before I go any further I have a fresh install of Ubuntu 12.10 64bit Running on a Dell Precision T3500 with a Xeon 2.4GHz processor 2GB of DDR3 RAM and two Nvidia Quadro FX580 video cards.
```
aaron@precision-WorkStation-T3500:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA Controller [RAID mode]
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 VGA compatible controller: NVIDIA Corporation G96 [Quadro FX 580] (rev a1)
03:00.0 VGA compatible controller: NVIDIA Corporation G96 [Quadro FX 580] (rev a1)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)

```

After installing I couldn't get USB tethering to work on my system with my Sony Xperia Arc. It would just start charging on my USB ports but wouldn't actually give me any option for USB tethering like it does on any other PC. I put this down to USB OTG being enabled in the kernel but gave up trying to get it to work after realising I'd probably have compile my own kernel with it disabled. 

Also, on a completely different problem (that I still haven't solved btw), I have been trying to get dual 20" Dell monitors to work with one plugged into each video card via DVI. But the display settings window doesn't detect the second display. So, it was at this point that I decided to try the closed source nvidia driver available in the software centre.

```
nvidia-current 304.51.really.304.43-0ubuntu1
```

After installing this and restarting the computer, the second display still didn't function and further more, after login, I was presented with my blank background image and mouse cursor with no launcher or task bar. Right clicking on the desktop still functioned so I was able to uninstall the nvidia driver by creating a blank text file on the desktop then right clicking on it, choosing to open with a different application and then choosing the Ubuntu Software Centre. The software centre opened with an expected error, saying that the file wasn't a .deb, which was fine. I just wanted to open the program since the super key combo didn't function either.

Once, I uninstalled the driver with the software centre, I restarted again. The PC hang for an extended period of time before presenting me with the log in window. I successfully logged in and the desktop was back to normal. However, I found that using my phone as a WiFi hot spot stopped functioning as the pc, using a belkin wireless dongle, would not connect with it anymore.

```
aaron@precision-WorkStation-T3500:~$ lsusb
Bus 002 Device 002: ID 050d:705a Belkin Components F5D7050 Wireless G Adapter v3000 [Ralink RT2571W]
Bus 002 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 002: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 003 Device 003: ID 413c:1004 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0fce:714f Sony Ericsson Mobile Communications AB 
Bus 003 Device 004: ID 413c:2006 Dell Computer Corp. 

```

But, as can be seen here, my Sony Arc started to tether via USB instead. So, my question is, what's up with that? And, is there a way I can get both to work?

I tryed reinstalling the nouveau driver

```
aaron@precision-WorkStation-T3500:~$ sudo apt-get install --reinstall xserver-xorg-video-nouveau
```

But nothing has changed after restarting. Any help would be great (even if it has to do with getting my dual displays working).

Thanks in advance,
Aaron.

---

### Post by power.supply on 2012-11-18
I should also note that the PC still connects to a wireless router I have hooked up to a network printer without any issues. The router isn't connected to the internet, it just is there to make it possible for me to wirelessly print from anywhere in my house.

Cheers.

---

### Post by power.supply on 2012-11-18
Bump. Still haven't fixed the problem. Any help would be wonderful :)

---

### Post by power.supply on 2012-11-19
Does anyone have any help they can offer? PLEEAASSEE!!!

---

