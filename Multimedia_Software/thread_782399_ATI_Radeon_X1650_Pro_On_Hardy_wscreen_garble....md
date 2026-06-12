---
title: "ATI Radeon X1650 Pro On Hardy w/screen garble..."
date: 2008-05-04
forum: Multimedia Software
---

### Post by VitalBodies on 2008-05-04
I am trying Ubuntu for the first time and struggling with getting my Hardware setup. I think all is well except for the Graphics card. 
Most things display well. 
When using the programs called Amaya (for creating web sites) or Carrara 6.1 Pro (A Windows program for creating 3d art under wine - Uses an OpenGL interface) select portions of the screen gets messed up. In Carrara I can not rotate the camera with out the camera view port going white with lines through it. On Amaya editing code create lot&#347; of screen artifacts making the program unusable. 


**COMPUTER:** Core 2 Quad Q6600 Dell Inspiron 530
[http://support.dell.com/support/edocs/systems/inspd530/EN/OM/appendix.htm#wp1123070](http://support.dell.com/support/edocs/systems/inspd530/EN/OM/appendix.htm#wp1123070)
Chipset: ICH9 and Intel G33

**SYSTEM MONITOR:** 
Gnome 2.22.1
Ubuntu Hardy 8.04 (I am running the 64-bit version)
Kernel Linux 2.6.24-16-rt

I also have Wine 0.9.60 installed...

**Diamond Viper:** ATI X1650 pro card 512mb (Rv535)
DRIVER: ATI Catalyst Control Center (CCC) - Linux Edition:
Driver Version: 8.47.3
CCC Version: 1.8
Driver: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)
Install: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)


*fglrxinfo*
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7412 Release 

*glxinfo | grep version*
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 2.1.7412 Release

*glxinfo | grep direct*
direct rendering: Yes


X.Org version: 1.4.0.90
dimensions: 1920x1200 pixels (524x321 millimeters)
depth of root window: 24 planes
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2


Do I need this for the 64-bit version - I would like to stay 64-bit if possible? *sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.476*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb*
If so could you help me correct this command for the current version?

sudo gedit /etc/X11/xorg.conf
**xorg.conf** XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "v4l"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "intl"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
**xorg.conf** XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

TESTING CARRARA ON WINE: 
> cd ~/.wine/drive_c/Program\ Files/DAZ/Carrara\ 6\ Pro
[email]bodies@VitalBodies:~/.wine[/email]/drive_c/Program Files/DAZ/Carrara 6 Pro$ wine Carrara.exe
fixme:dwmapi:DwmEnableComposition (0) stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32fb20,0x32fb24): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
wine: Unhandled page fault on read access to 0x00000200 at address 0xf7fb109d (thread 0009), starting debugger...
[email]bodies@VitalBodies:~/.wine[/email]/drive_c/Program Files/DAZ/Carrara 6 Pro$ cd ~/.wine/drive_c/Program\ Files/DAZ/Carrara\ 6\ Pro
[email]bodies@VitalBodies:~/.wine[/email]/drive_c/Program Files/DAZ/Carrara 6 Pro$ wine Carrara.exe
fixme:dwmapi:DwmEnableComposition (0) stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32fb20,0x32fb24): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:avifile:AVIFileExit (): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32efbc,0x00000000), stub!
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876017c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876017c
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
fixme:avifile:AVIFileExit (): stub!
wine: Unhandled page fault on read access to 0x00000200 at address 0xf7fa709d (thread 0009), starting debugger... 

---

### Post by Fran89 on 2008-05-07
You can always Try CodeWeavers: CrossOver Pro, or Cedega, they're basicly a modified version of WINE that support Cards such are yours... but sadly these are not free... PM me if you ever need more info..

---

### Post by ComradeHaz on 2008-10-28
> **Fran89 said:**
> You can always Try CodeWeavers: CrossOver Pro, or Cedega, they're basicly a modified version of WINE that support Cards such are yours... but sadly these are not free... PM me if you ever need more info..

Why PM? Why not here for people (like me) potentially suffering similar problems to see?

---

### Post by VitalBodies on 2008-10-28
> **Fran89 said:**
> You can always Try CodeWeavers: CrossOver Pro, or Cedega, they're basicly a modified version of WINE that support Cards such are yours... but sadly these are not free... PM me if you ever need more info..

Are there ways to update wine for the card one has, by loading windows drivers in wine for wine?

---

