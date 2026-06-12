---
title: "Soundless on some games"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by Dylnuge on 2007-06-27
Original Problem Solved (by myself). Go a few posts down for new problem.

---

### Post by Dylnuge on 2007-06-28
Go down

---

### Post by Dylnuge on 2007-06-28
Keep Going

---

### Post by Dylnuge on 2007-06-28
A little further

---

### Post by Dylnuge on 2007-11-04
Okay, after 7.10 upgrade, guess what?

GNOME fails to have any sound for NWN whatsoever. Here is some data to help:

```
dnugent@tzWS001:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dnugent@tzWS001:~$ 

```

```
dnugent@tzWS001:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

```

```

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=esd

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@

```

```

[Sound Options]
Speaker Type=-1
SoundFX Volume=0.60
Voice Volume=0.85
Music Volume=0.60
2D3D Bias=1.00
Number 3D Voices=8
Number 2D Voices=8
3D Provider=Miles Fast 2D Positional Audio
Environment Effects=0
DisableSound=0
[Display Options]
UseLargeFont=0
RefreshRate=0
BitsPerPixels=32
Height=900
Width=1440
TexturePack=2
FullScreen=1
[Video Options]
Enable CreatureEnvironmentMapping=1
Enable TextureAnimations=1
EnableSkyboxes=0
CreatureShadowDetail=1
Gamma=1.000000
VideoQualitySetting=2
EnableEnvironmentShadows=1
EnableFastGrass=0
EnableGrass=1
CreatureWindSetting=2
Enable AnisotropicFiltering=0
Enable Truform=0
EnableVisualEffectsHigh=1
NumShadowCastingLights=3
ShinyWater=1
Enable VSync=1
AntiAliasing Mode=4
NumDynamicLights=8

```

Any help?

PS: Just a note, I installed NwMovies after sound stopped working to see if Movies worked (they didn't). There was no traceback before nwmovies, if anyone wants the stuff that appears now, I can post it too.

---

### Post by Dylnuge on 2007-11-06
Hello?

---

