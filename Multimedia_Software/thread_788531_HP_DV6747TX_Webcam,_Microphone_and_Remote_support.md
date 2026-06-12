---
title: "HP DV6747TX Webcam, Microphone and Remote support?"
date: 2008-05-09
forum: Multimedia Software
---

### Post by BuRn_sLuG on 2008-05-09
Hey guys,

Recently purchased an HP DV6747TX notebook. Have updated my BIOS to the latest version, and successfully installed Ubuntu 8.04. I have upgraded all of my installed software (sudo apt-get update and sudo apt-get upgrade). 

**What works:**
[LIST]
[*]Screen
[*]Keyboard
[*]Touchpad
[*]Speakers
[*]RJ-45
[*]HDMI
[*]USB 
[*]Optical Drive
[/LIST]

**What doesn't work:**
[LIST]
[*]Microphone
[*]Webcam
[*]Some keys on media remote, some keys on quicklaunch buttons.
[/LIST]


Everything else is untested. 
[B]
lspci returns the following;[/B]

[LIST]
[*]00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
[*]00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
[*]00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
[*]00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
[*]00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
[*]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
[*]00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
[*]00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
[*]00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
[*]00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
[*]00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
[*]00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
[*]00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
[*]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
[*]00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
[*]00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
[*]00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
[*]00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
[*]01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
[*]02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
[*]06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
[*]07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
[*]07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
[*]07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
[*]07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
[*]07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
[/LIST]


**lsusb returns the following;**

[LIST]
[*]Bus 007 Device 001: ID 0000:0000  
[*]Bus 005 Device 001: ID 0000:0000  
[*]Bus 004 Device 001: ID 0000:0000  
[*]Bus 006 Device 001: ID 0000:0000  
[*]Bus 003 Device 001: ID 0000:0000  
[*]Bus 002 Device 002: ID 064e:a110 Suyin Corp. 
[*]Bus 002 Device 001: ID 0000:0000  
[*]Bus 001 Device 001: ID 0000:0000
[/LIST]
Basically the microphone doesn't appear to record (gnome-sound-recorder doesn't take in any input but appears to be recording. Same issue with each input).

The webcam doesn't appear to work either (launching camorama results in "Could not connect to video device (/dev/video0). Please check connection.").

And finally the remote doesn't seem to work completely (shares the same function as the quick launch keys with errors). 

**What works with the remote (and quick launch buttons):**\
[LIST]
[*]Power
[*]Output switch (Hdmi/VGA/main screen)
[*]Volume Up/Down/On/Off
[*]"Up"/"Dn" Keys
[*]Stop (In Exaile, but not in VLC) 
[*]Play/Pause (In Exaile, but not in VLC)
[*]Skip foward/Skip Back (In Exaile, but not in VLC)
[*]Directional Keys
[*]"OK" Key
[*]"Backspace" Key (Though not working for up a directory in VLC, I believe it should)
[*]"I" Key
[/LIST]


**What doesn't work with the remote (and quick launch buttons):**
[LIST]
[*]"Refresh key" (looks like the refresh button in Firefox, not sure what you would use it for though)
[*]"DVD Key" (Has the DVD logo on it)
[*]"Media Center Key" (Has the Windows logo on it)
[*]Foward/Rewind Keys
[/LIST]


If anyone knows of a fix for these problems, it would be much appreciated.

Thanks in advance.

---

### Post by linuxwizard on 2008-05-10
For Webcam > Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by charlemagne86 on 2008-05-23
okay mine is a ricoh 1870 webcam and i got it working in ekiga alright...but after a few seconds the pic starts distorting and ends up getting all funny red and green shades every where 

help!

---

### Post by linuxwizard on 2008-05-23
Are you using any desktop effect ? If so try and disable the effects and see if that helps.

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

