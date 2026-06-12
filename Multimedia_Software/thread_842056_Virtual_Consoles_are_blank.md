---
title: "Virtual Consoles are blank"
date: 2008-06-27
forum: Multimedia Software
---

### Post by shortspecialbus on 2008-06-27
Hi,

Just installing ubuntu to try it out.  Currently I am unable to switch to any virtual consoles once X has started.  I added "vga=normal" to hopefully turn off the framebuffer for the kernel, in case that was affecting things, but it hasn't seemed to have made a difference.  The screen still seems to switch to some sort of VGA mode shortly into the boot sequence rather than straight text that it starts with and that the BIOS uses and such.  CTRL-S/CTRL-Q to try to figure out where/when it's doing it has been less than fruitful, although I can tell you that the lights on my backlit USB keyboard go off when it switches around.

I can still log in and execute commands, as logging in and running "sudo shutdown -r now" will reboot the system, but the monitor remains on standby until the system reboots.  This only seems to occur once X has started.  I've searched through the ubuntu bugzilla but none of them seem to have a solution, and they're all listed as "Invalid" even though as far as I can tell, most weren't actually resolved.

System specs, currently vga=normal is specified.
```

stefan@megatron:~$ uname -a
Linux megatron 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

stefan@megatron:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy

stefan@megatron:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)
01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
05:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

stefan@megatron:~$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.447]
  Unique ID: rdCR.PDyRCHLZXt3
  Hardware Class: framebuffer
  Model: "ATI ATOMBIOS R580"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "R580"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0394: 320x240 (+640), 15 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b4: 512x384 (+1024), 15 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c4: 640x350 (+1280), 15 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0384: 640x400 (+1280), 15 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0334: 720x400 (+1472), 15 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0354: 1152x864 (+2304), 15 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0364: 1280x1024 (+2560), 15 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0344: 1400x1050 (+2816), 15 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0374: 1600x1200 (+3200), 15 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 24 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0384: 640x400 (+1280), 15 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 24 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d4: 1856x1392 (+3712), 15 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 24 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e4: 1920x1440 (+3840), 15 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown


```
It's an ATI Radeon X1900XTX, by the way, if that wasn't obvious in the lspci output.  On an unrelated note that I'll deal with later, using the ATI proprietary driver causes the X server to crash and hang the system after several seconds.  But that can wait for a different time, as I can get by with the open source driver for time being.

I'm a linux sysadmin with about 12 years of linux experience, but lately it's been mostly with RHEL5 and prior to that Centos 4 and various older RedHats.  Also Gentoo, but not much Debian (or variants) at all, so I haven't quite picked up on all the nuances since I installed it several hours ago ;)

Any help would be appreciated, and feel free to ask for whatever else you need.  Thanks!

-stefan

---

### Post by MusicianX on 2008-07-27
I have the same problem with my ATI Radeon X1300.
I used a mixture of the auto-generated xorg.conf with my old xorg.conf from Ubuntu Feisty and it works, allthough it produses some artifacts on the screen while switching from X to console. Here it is:

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "XkbRules" "xorg"
    Option	"XkbModel" "pc104"
    Option	"XkbLayout"	"us,el"
    Option	"XkbVariant"	"basic,extended"
    Option	"XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier	"Eizo S1911 DVI"
	Option		"DPMS"
	HorizSync	38-64
	VertRefresh	60-60
EndSection

Section "Device"
	Identifier  "Radeon X1300"
	Driver      "vesa"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon X1300"
	Monitor    "Eizo S1911 DVI"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
EndSection

It's ugly and I don't know why it works...

I tried Debian Testing and I could switch from X to console using the auto-generated xorg.conf and the open driver.
But The fglrx driver hungs the system in Debian as in Ubuntu.

---

### Post by MusicianX on 2008-07-27
Well, I cleaned my xorg.conf and it seems the only essential is in line:

Driver    "vesa"

This line in Section "Device" is the only differnce from  the auto generated file and it is enough to be able to do <Ctl> + <Alt> + <Func key>.

The fglrx driver is still a dream though...

---

