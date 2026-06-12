---
title: "Ubuntu begginer sound problems"
date: 2009-12-29
forum: Multimedia Software
---

### Post by premamotion on 2009-12-29
[COLOR=Red]Hi there to all the comunity! [/COLOR]

I need your help, after searching days and days on internet and this forum. Maybe my problems are simple, but for me are so difficult, so please help me.

**First problem** is with my input sound device. I`m using a Creative Live! VF0400 webcamera in Ubuntu 9.10 and I want it to be my default input device. The problem is that it`s not as default, because the system uses the onboard input device - the audio device on my motherboard.. how to choose my webcam`s microfone as the default input source?

**My second problem** is that anytime that I restart the pc, I need to reconfigure the sound settings, like volume of the speakers and the volume of the mic... how to save the audio settings permanently? command **sudo alsactl store **does not help me...[B]

My third problem [/B]is that somehow... the sound from my Creative webcam`s mic is distorted... and my voice sound like a duck`s voice... this does not happen all the time, but is a frequent problem for me... my audio setting are not ok... or the audio drivers are unstable... there is some/more bug/s or what?? 
 Take a look, this is my problem: (please see also the [sample playback]("http://launchpadlibrarian.net/34407801/Untitled.ogg")) - [https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/460983](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/460983)

**My fourth and last problem** is with gnome-sound-recorder 2.28.1 - I can`t get it to work... If I choose any of the recording formats, when pressing play gives me the error: "Cannot use the selected profile ... Check the configurations. Maybe the necessary modules are missing".

 Please help me and I hope some day I can help others.
Thank you so much, best wishes for the New Year!

---

### Post by premamotion on 2009-12-29
P.S. This is what [FONT=Courier New][SIZE=2][FONT=Verdana]**lspci **returns me:[B]
[COLOR=DarkGreen]
[/COLOR][/B][COLOR=DarkGreen]00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
[COLOR=Black]
and this is what **lsusb** returns:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 041e:4061 Creative Technology, Ltd Live! Cam Notebook Pro [VF0400]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[/COLOR][/COLOR][/FONT][/SIZE][/FONT]

---

