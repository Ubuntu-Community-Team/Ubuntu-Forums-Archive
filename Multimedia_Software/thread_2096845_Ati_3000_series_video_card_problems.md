---
title: "Ati 3000 series video card problems"
date: 2012-12-21
forum: Multimedia Software
---

### Post by 37fleetwood on 2012-12-21
HI, I'm hoping someone will be able to help me.

I'm running Ubuntu 12.04 and an onboard Ati Radeon 3000 series video card. I have 16 gig of ram and around 8tb of hard drive space. I have the AMD Phenom processor with 6 cores.


now for the problem. when I first installed Ubuntu 12.04 I was thinking I was having trouble with the video drivers it would let me install the FGLRX driver but wouldn't install the one marked (post-release updates) everything video and screen related was really sluggish and crashed a lot. it ran much better in Classic Gnome. so I un-installed the "Additional Driver" and installed the Ati Catalyst Control Center and drivers. it didn't seem to change much. along with being sluggish all around, during video playback it will just stop playing in the middle of a video, the player will crash and from there if you try to restart the video the sound will play but no video. you have to log out and log back in to get it to go again.

what should I do to get this fixed? I'm willing to buy a new video card if this is a known problem and there is no simple fix. this thing should scream and it never has. please someone help!
Sorry if this doesn't make sense, please ask me questions and I'll try to answer as best I can.
Thank you.

---

### Post by 37fleetwood on 2012-12-21
just in case this would help after a crash I opened a terminal an ran ```
lspci -vvnn | grep VGA
``` and this was the output:

```
scott@ubuntu:~$ lspci -vvnn | grep VGA
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS780L [Radeon HD 3000] [1002:9616] (prog-if 00 [VGA controller])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
scott@ubuntu:~$ 


```

---

### Post by SR_ELPIRATA on 2012-12-21
I used to have a Ati HD3300 (Asus mobo) and let me tell you it was screaming (like yours is supposed to). I could run HD files easily and all I had with it was a Amd Dual Core 7750 (Black Edition) with 2gigs of ram. Different thing on my case was I had 10.10 and since all I use it for is Home Theather I never got to upgrade to 12.04 (I have the LiveCDs but I dont want to get into getting soundcard and stuff working again). Ocasionally I would do other things of course, and far as I can tell, I could throw anything at it and it would run nicely. The board fried after that and I got a Dimension 5150 with a nvidia GT230 and installation has kept working (same home theather performance and all). After that, Dimension died, and now moved the drive and video card to another PC with less ram (640MB) and now I notice it sluggish :)

I can only tell you a few things, if you do home theather and 3D stuff, I would turn off the desktop effects, games and htpc software run better. But your problem is definitely software, cause you have more than enough to run all that fine.

---

### Post by SR_ELPIRATA on 2012-12-21
Also try [www.xbmc.org](www.xbmc.org) for playing HD videos. VLC is great but I had troubles before with the Asus/Amd (minor things) but with XBMC it rocked after.

If memory serves well, 12.04 had a 2D desktop on login (session I think), try with that too.

---

### Post by 37fleetwood on 2012-12-24
ever hear the old saying, it's better to leave well enough alone?
I decided I'd try to upgrade to Ubuntu 12.10 not realizing that it would only make it worse. 12.10 doesn't work with this video card at all and you have to use a "Legacy" driver which barely works at all. now not only can't I watch videos almost all programs crash all the time and I can't get any graphics programs to even start up at all!
this is the only thing I hate about Linux. it has terrible driver support. this is a fairly common card and is already dropped from being supported.
this really bugs me because this machine is less than a year old!

so on to the next question, what's the best card that still has support?
I watch videos and use GIMP quite a bit, but do not game.

---

### Post by 37fleetwood on 2012-12-24
this is my new output:

```
scott@ubuntu:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

---

### Post by 37fleetwood on 2012-12-24
OK, I think I have it fixed... I hope...

I upgraded to 12.10 then the graphics were terrible. wrong screen settings and all, so I installed the ATI Legacy driver which made the screen look fine but everything was crashing and the Plymouth screen at boot was gone.
that looked like this:

```
sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy
```

from there I did this and it seems to have reset everything to a working setting.

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:makson96/fglrx
```

trying to figure out why this was so jacked up all I can come up with is that the Ati drivers were not working correctly from the get go. they also would not let me simply uninstall them. when I upgraded to 12.10 they really didn't work. installing the legacy driver let me have something that would finally uninstall and all of the Ati driver stuff went with it. then the settings reconfigured themselves to what I should have started with in the first place!

of course this explanation is unintelligible as I'm kinda a user and not that interested in the inner workings of the OS, or command line stuff. it's a wonder it still works at all!

anyway, it's fixed... for now at least, I may still consider a new video card in the near future, Linux doesn't seem to be too happy with this one!

---

### Post by Yellow Pasque on 2012-12-24
Well, you ran into some bugs.
The version of fglrx in Quantal/12.10 doesn't support "older" RadeonHD cards (2x00-4x00): [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1058040)

Older versions of fglrx (like the "legacy" 12-6 fglrx/Catalyst driver from AMD's site or the version of fglrx found in Precise repo) haven't been updated for Xserver 1.13, so that's why you had to use the makson PPA, which is an ugly hack that downgrades Xserver and makes older fglrx releases run in Quantal/12.10.

Now, if one upgrades 12.04->12.10 and has fglrx driver installed, you'd think the upgrader would notify the user about the aforementioned bug if it's not smart enough to detect his/her GPU and remove fglrx appropriately. I think there was a LP bug on that too, but can't remember the number off the top of my head.

As for difficulty removing fglrx, that seems pretty common to me: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641)
Even though it's marked fixed, I still see people running into it.

Finally, you seemed to be operating under the assumption (as a lot of n00bs and folks coming from Windows do) that you needed the proprietary Catalyst driver installed when the open-source radeon driver actually works better for a lot of folks (I'm runnin it now on my HD4550).

---

### Post by 37fleetwood on 2012-12-27
Thanks for your post, I'm still having some problems. Movie Player doesn't work at all and random stuff seems to crash all the time. not sure what it is, but somehow it's either related to the Ati driver, or it's related to 12.10.

---

### Post by Yellow Pasque on 2012-12-27
Can you post/pastebin your /var/log/Xorg.0.log?

---

### Post by 37fleetwood on 2012-12-28
> **Temüjin said:**
> Can you post/pastebin your /var/log/Xorg.0.log?

```
[ 31714.843] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[ 31714.843] X Protocol Version 11, Revision 0
[ 31714.843] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[ 31714.843] Current Operating System: Linux ubuntu 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64
[ 31714.843] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-21-generic root=/dev/mapper/ubuntu-root ro plymouth:debug splash quiet drm.debug=0xe
[ 31714.843] Build Date: 27 November 2012  07:44:35AM
[ 31714.843] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[ 31714.843] Current version of pixman: 0.26.0
[ 31714.843] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[ 31714.843] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 31714.844] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 27 11:47:27 2012
[ 31714.844] (==) Using config file: "/etc/X11/xorg.conf"
[ 31714.844] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 31714.845] (==) ServerLayout "aticonfig Layout"
[ 31714.845] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[ 31714.845] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[ 31714.845] (**) |   |-->Device "aticonfig-Device[0]-0"
[ 31714.845] (==) Automatically adding devices
[ 31714.845] (==) Automatically enabling devices
[ 31714.845] (==) Automatically adding GPU devices
[ 31714.845] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 31714.845] 	Entry deleted from font path.
[ 31714.845] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 31714.845] 	Entry deleted from font path.
[ 31714.845] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 31714.845] 	Entry deleted from font path.
[ 31714.846] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 31714.846] 	Entry deleted from font path.
[ 31714.846] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 31714.846] 	Entry deleted from font path.
[ 31714.846] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[ 31714.846] 	Entry deleted from font path.
[ 31714.846] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[ 31714.846] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 31714.846] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[ 31714.846] (II) Loader magic: 0x7fe5066f8c40
[ 31714.846] (II) Module ABI versions:
[ 31714.846] 	X.Org ANSI C Emulation: 0.4
[ 31714.846] 	X.Org Video Driver: 13.0
[ 31714.846] 	X.Org XInput driver : 18.0
[ 31714.846] 	X.Org Server Extension : 7.0
[ 31714.846] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 31714.849] (--) PCI:*(0:1:5:0) 1002:9616:1462:7501 rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
[ 31714.849] (II) Open ACPI successful (/var/run/acpid.socket)
[ 31714.849] Initializing built-in extension Generic Event Extension
[ 31714.849] Initializing built-in extension SHAPE
[ 31714.849] Initializing built-in extension MIT-SHM
[ 31714.849] Initializing built-in extension XInputExtension
[ 31714.849] Initializing built-in extension XTEST
[ 31714.849] Initializing built-in extension BIG-REQUESTS
[ 31714.849] Initializing built-in extension SYNC
[ 31714.849] Initializing built-in extension XKEYBOARD
[ 31714.849] Initializing built-in extension XC-MISC
[ 31714.849] Initializing built-in extension SECURITY
[ 31714.849] Initializing built-in extension XINERAMA
[ 31714.849] Initializing built-in extension XFIXES
[ 31714.849] Initializing built-in extension RENDER
[ 31714.849] Initializing built-in extension RANDR
[ 31714.849] Initializing built-in extension COMPOSITE
[ 31714.849] Initializing built-in extension DAMAGE
[ 31714.849] Initializing built-in extension MIT-SCREEN-SAVER
[ 31714.849] Initializing built-in extension DOUBLE-BUFFER
[ 31714.849] Initializing built-in extension RECORD
[ 31714.849] Initializing built-in extension DPMS
[ 31714.849] Initializing built-in extension X-Resource
[ 31714.849] Initializing built-in extension XVideo
[ 31714.849] Initializing built-in extension XVideo-MotionCompensation
[ 31714.849] Initializing built-in extension XFree86-VidModeExtension
[ 31714.849] Initializing built-in extension XFree86-DGA
[ 31714.849] Initializing built-in extension XFree86-DRI
[ 31714.849] Initializing built-in extension DRI2
[ 31714.849] (II) "glx" will be loaded by default.
[ 31714.849] (II) LoadModule: "glx"
[ 31714.850] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 31714.850] (II) Module glx: vendor="X.Org Foundation"
[ 31714.850] 	compiled for 1.13.0, module version = 1.0.0
[ 31714.850] 	ABI class: X.Org Server Extension, version 7.0
[ 31714.850] (==) AIGLX enabled
[ 31714.850] Loading extension GLX
[ 31714.851] (II) LoadModule: "fglrx"
[ 31714.852] (WW) Warning, couldn't open module fglrx
[ 31714.852] (II) UnloadModule: "fglrx"
[ 31714.852] (II) Unloading fglrx
[ 31714.852] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 31714.852] (==) Matched fglrx as autoconfigured driver 0
[ 31714.852] (==) Matched ati as autoconfigured driver 1
[ 31714.852] (==) Matched fglrx as autoconfigured driver 2
[ 31714.852] (==) Matched ati as autoconfigured driver 3
[ 31714.852] (==) Matched vesa as autoconfigured driver 4
[ 31714.852] (==) Matched modesetting as autoconfigured driver 5
[ 31714.852] (==) Matched fbdev as autoconfigured driver 6
[ 31714.852] (==) Assigned the driver to the xf86ConfigLayout
[ 31714.852] (II) LoadModule: "fglrx"
[ 31714.853] (WW) Warning, couldn't open module fglrx
[ 31714.853] (II) UnloadModule: "fglrx"
[ 31714.853] (II) Unloading fglrx
[ 31714.853] (EE) Failed to load module "fglrx" (module does not exist, 0)
[ 31714.853] (II) LoadModule: "ati"
[ 31714.853] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 31714.853] (II) Module ati: vendor="X.Org Foundation"
[ 31714.853] 	compiled for 1.13.0, module version = 6.99.99
[ 31714.853] 	Module class: X.Org Video Driver
[ 31714.853] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.853] (II) LoadModule: "radeon"
[ 31714.854] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 31714.854] (II) Module radeon: vendor="X.Org Foundation"
[ 31714.854] 	compiled for 1.13.0, module version = 6.99.99
[ 31714.854] 	Module class: X.Org Video Driver
[ 31714.854] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.854] (II) LoadModule: "vesa"
[ 31714.855] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 31714.855] (II) Module vesa: vendor="X.Org Foundation"
[ 31714.855] 	compiled for 1.12.99.902, module version = 2.3.2
[ 31714.855] 	Module class: X.Org Video Driver
[ 31714.855] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.855] (II) LoadModule: "modesetting"
[ 31714.856] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[ 31714.856] (II) Module modesetting: vendor="X.Org Foundation"
[ 31714.856] 	compiled for 1.13.0, module version = 0.5.0
[ 31714.856] 	Module class: X.Org Video Driver
[ 31714.856] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.856] (II) LoadModule: "fbdev"
[ 31714.856] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 31714.856] (II) Module fbdev: vendor="X.Org Foundation"
[ 31714.856] 	compiled for 1.12.99.902, module version = 0.4.3
[ 31714.856] 	Module class: X.Org Video Driver
[ 31714.856] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.856] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE
[ 31714.858] (II) VESA: driver for VESA chipsets: vesa
[ 31714.858] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[ 31714.858] (II) FBDEV: driver for framebuffer: fbdev
[ 31714.858] (++) using VT number 7

[ 31714.858] (II) [KMS] Kernel modesetting enabled.
[ 31714.858] (WW) Falling back to old probe method for vesa
[ 31714.858] (WW) Falling back to old probe method for modesetting
[ 31714.858] (WW) Falling back to old probe method for fbdev
[ 31714.858] (II) Loading sub module "fbdevhw"
[ 31714.858] (II) LoadModule: "fbdevhw"
[ 31714.858] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 31714.858] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 31714.858] 	compiled for 1.13.0, module version = 0.0.2
[ 31714.858] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.858] (**) RADEON(0): Depth 24, (--) framebuffer bpp 32
[ 31714.858] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[ 31714.858] (==) RADEON(0): Default visual is TrueColor
[ 31714.858] (==) RADEON(0): RGB weight 888
[ 31714.858] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[ 31714.858] (--) RADEON(0): Chipset: "ATI Radeon 3000 Graphics" (ChipID = 0x9616)
[ 31714.858] (II) Loading sub module "dri2"
[ 31714.858] (II) LoadModule: "dri2"
[ 31714.858] (II) Module "dri2" already built-in
[ 31714.858] (II) Loading sub module "exa"
[ 31714.858] (II) LoadModule: "exa"
[ 31714.859] (II) Loading /usr/lib/xorg/modules/libexa.so
[ 31714.859] (II) Module exa: vendor="X.Org Foundation"
[ 31714.859] 	compiled for 1.13.0, module version = 2.6.0
[ 31714.859] 	ABI class: X.Org Video Driver, version 13.0
[ 31714.859] (II) RADEON(0): KMS Color Tiling: enabled
[ 31714.859] (II) RADEON(0): KMS Pageflipping: enabled
[ 31714.859] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[ 31714.884] (II) RADEON(0): Output VGA-0 using monitor section aticonfig-Monitor[0]-0
[ 31714.915] (II) RADEON(0): Output DVI-0 has no monitor section
[ 31714.940] (II) RADEON(0): EDID for output VGA-0
[ 31714.971] (II) RADEON(0): EDID for output DVI-0
[ 31714.971] (II) RADEON(0): Manufacturer: DEL  Model: a06c  Serial#: 825839189
[ 31714.971] (II) RADEON(0): Year: 2010  Week: 47
[ 31714.971] (II) RADEON(0): EDID Version: 1.3
[ 31714.971] (II) RADEON(0): Digital Display Input
[ 31714.971] (II) RADEON(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[ 31714.971] (II) RADEON(0): Gamma: 2.20
[ 31714.971] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[ 31714.972] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 31714.972] (II) RADEON(0): First detailed timing is preferred mode
[ 31714.972] (II) RADEON(0): redX: 0.631 redY: 0.349   greenX: 0.341 greenY: 0.622
[ 31714.972] (II) RADEON(0): blueX: 0.152 blueY: 0.058   whiteX: 0.313 whiteY: 0.329
[ 31714.972] (II) RADEON(0): Supported established timings:
[ 31714.972] (II) RADEON(0): 720x400@70Hz
[ 31714.972] (II) RADEON(0): 640x480@60Hz
[ 31714.972] (II) RADEON(0): 640x480@75Hz
[ 31714.972] (II) RADEON(0): 800x600@60Hz
[ 31714.972] (II) RADEON(0): 800x600@75Hz
[ 31714.972] (II) RADEON(0): 1024x768@60Hz
[ 31714.972] (II) RADEON(0): 1024x768@75Hz
[ 31714.972] (II) RADEON(0): 1280x1024@75Hz
[ 31714.972] (II) RADEON(0): Manufacturer's mask: 0
[ 31714.972] (II) RADEON(0): Supported standard timings:
[ 31714.972] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[ 31714.972] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[ 31714.972] (II) RADEON(0): #2: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[ 31714.972] (II) RADEON(0): Supported detailed timing:
[ 31714.972] (II) RADEON(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[ 31714.972] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[ 31714.972] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[ 31714.972] (II) RADEON(0): Serial No: WCMFT0BJ19NU
[ 31714.972] (II) RADEON(0): Monitor name: DELL ST2421L
[ 31714.972] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[ 31714.972] (II) RADEON(0): EDID (in hex):
[ 31714.972] (II) RADEON(0): 	00ffffffffffff0010ac6ca0554e3931
[ 31714.972] (II) RADEON(0): 	2f14010380351e78ea9535a159579f27
[ 31714.972] (II) RADEON(0): 	0e5054a54b00714f8180d1c001010101
[ 31714.972] (II) RADEON(0): 	010101010101023a801871382d40582c
[ 31714.972] (II) RADEON(0): 	4500132b2100001e000000ff0057434d
[ 31714.972] (II) RADEON(0): 	465430424a31394e550a000000fc0044
[ 31714.972] (II) RADEON(0): 	454c4c205354323432314c0a000000fd
[ 31714.972] (II) RADEON(0): 	00384c1e5311000a2020202020200083
[ 31714.972] (II) RADEON(0): Printing probed modes for output DVI-0
[ 31714.972] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 31714.972] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[ 31714.972] (II) RADEON(0): Modeline "1680x945"x60.0  131.48  1680 1784 1960 2240  945 946 949 978 -hsync +vsync (58.7 kHz)
[ 31714.972] (II) RADEON(0): Modeline "1400x1050"x74.9  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[ 31714.972] (II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[ 31714.973] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1366x768"x60.0   85.89  1366 1439 1583 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[ 31714.973] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1280x768"x60.0   68.25  1280 1328 1360 1440  768 771 778 790 +hsync -vsync (47.4 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[ 31714.973] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 31714.973] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 31714.973] (II) RADEON(0): Output VGA-0 disconnected
[ 31714.973] (II) RADEON(0): Output DVI-0 connected
[ 31714.973] (II) RADEON(0): Using exact sizes for initial modes
[ 31714.973] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080
[ 31714.973] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 31714.973] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:f7d7000
[ 31714.973] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[ 31714.973] (==) RADEON(0): DPI set to (96, 96)
[ 31714.973] (II) Loading sub module "fb"
[ 31714.973] (II) LoadModule: "fb"
[ 31714.974] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 31714.974] (II) Module fb: vendor="X.Org Foundation"
[ 31714.974] 	compiled for 1.13.0, module version = 1.0.0
[ 31714.974] 	ABI class: X.Org ANSI C Emulation, version 0.4
[ 31714.974] (II) Loading sub module "ramdac"
[ 31714.974] (II) LoadModule: "ramdac"
[ 31714.974] (II) Module "ramdac" already built-in
[ 31714.974] (II) UnloadModule: "vesa"
[ 31714.974] (II) Unloading vesa
[ 31714.974] (II) UnloadModule: "modesetting"
[ 31714.974] (II) Unloading modesetting
[ 31714.974] (II) UnloadModule: "fbdev"
[ 31714.974] (II) Unloading fbdev
[ 31714.974] (II) UnloadSubModule: "fbdevhw"
[ 31714.974] (II) Unloading fbdevhw
[ 31714.975] (--) Depth 24 pixmap format is 32 bpp
[ 31714.975] (II) RADEON(0): [DRI2] Setup complete
[ 31714.975] (II) RADEON(0): [DRI2]   DRI driver: r600
[ 31714.975] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[ 31714.975] (II) RADEON(0): Front buffer size: 8100K
[ 31714.975] (II) RADEON(0): VRAM usage limit set to 221119K
[ 31714.975] (==) RADEON(0): Backing store disabled
[ 31714.975] (II) RADEON(0): Direct rendering enabled
[ 31714.975] (II) RADEON(0): Setting EXA maxPitchBytes
[ 31714.975] (II) EXA(0): Driver allocated offscreen pixmaps
[ 31714.975] (II) EXA(0): Driver registered support for the following operations:
[ 31714.975] (II)         Solid
[ 31714.975] (II)         Copy
[ 31714.975] (II)         Composite (RENDER acceleration)
[ 31714.975] (II)         UploadToScreen
[ 31714.975] (II)         DownloadFromScreen
[ 31714.976] (II) RADEON(0): Acceleration enabled
[ 31714.976] (**) RADEON(0): DPMS enabled
[ 31714.976] (==) RADEON(0): Silken mouse enabled
[ 31714.976] (II) RADEON(0): Set up textured video
[ 31714.976] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[ 31714.976] (II) RADEON(0): [XvMC] Extension initialized.
[ 31714.976] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 31714.976] (WW) RADEON(0): Option "VendorName" is not used
[ 31714.976] (WW) RADEON(0): Option "ModelName" is not used
[ 31714.976] (--) RandR disabled
[ 31714.994] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[ 31714.994] (II) AIGLX: enabled GLX_INTEL_swap_event
[ 31714.994] (II) AIGLX: enabled GLX_ARB_create_context
[ 31714.994] (II) AIGLX: enabled GLX_ARB_create_context_profile
[ 31714.994] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[ 31714.994] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[ 31714.994] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[ 31714.995] (II) AIGLX: Loaded and initialized r600
[ 31714.995] (II) GLX: Initialized DRI2 GL provider for screen 0
[ 31714.995] (II) RADEON(0): Setting screen physical size to 508 x 285
[ 31715.000] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 31715.002] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 31715.002] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 31715.002] (II) LoadModule: "evdev"
[ 31715.002] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 31715.002] (II) Module evdev: vendor="X.Org Foundation"
[ 31715.002] 	compiled for 1.13.0, module version = 2.7.3
[ 31715.002] 	Module class: X.Org XInput Driver
[ 31715.002] 	ABI class: X.Org XInput driver, version 18.0
[ 31715.002] (II) Using input driver 'evdev' for 'Power Button'
[ 31715.003] (**) Power Button: always reports core events
[ 31715.003] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 31715.003] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 31715.003] (--) evdev: Power Button: Found keys
[ 31715.003] (II) evdev: Power Button: Configuring as keyboard
[ 31715.003] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 31715.003] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 31715.003] (**) Option "xkb_rules" "evdev"
[ 31715.003] (**) Option "xkb_model" "pc105"
[ 31715.003] (**) Option "xkb_layout" "us"
[ 31715.003] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 31715.003] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 31715.003] (II) Using input driver 'evdev' for 'Power Button'
[ 31715.003] (**) Power Button: always reports core events
[ 31715.003] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 31715.003] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 31715.003] (--) evdev: Power Button: Found keys
[ 31715.003] (II) evdev: Power Button: Configuring as keyboard
[ 31715.003] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[ 31715.003] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 31715.003] (**) Option "xkb_rules" "evdev"
[ 31715.003] (**) Option "xkb_model" "pc105"
[ 31715.003] (**) Option "xkb_layout" "us"
[ 31715.003] (II) config/udev: Adding drm device (/dev/dri/card0)
[ 31715.003] (II) config/udev: Adding input device Chicony Saitek Eclipse Keyboard (/dev/input/event2)
[ 31715.003] (**) Chicony Saitek Eclipse Keyboard: Applying InputClass "evdev keyboard catchall"
[ 31715.003] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse Keyboard'
[ 31715.003] (**) Chicony Saitek Eclipse Keyboard: always reports core events
[ 31715.003] (**) evdev: Chicony Saitek Eclipse Keyboard: Device: "/dev/input/event2"
[ 31715.004] (--) evdev: Chicony Saitek Eclipse Keyboard: Vendor 0x6a3 Product 0x8020
[ 31715.004] (--) evdev: Chicony Saitek Eclipse Keyboard: Found keys
[ 31715.004] (II) evdev: Chicony Saitek Eclipse Keyboard: Configuring as keyboard
[ 31715.004] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input2/event2"
[ 31715.004] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse Keyboard" (type: KEYBOARD, id 8)
[ 31715.004] (**) Option "xkb_rules" "evdev"
[ 31715.004] (**) Option "xkb_model" "pc105"
[ 31715.004] (**) Option "xkb_layout" "us"
[ 31715.004] (II) config/udev: Adding input device Chicony Saitek Eclipse Keyboard (/dev/input/event3)
[ 31715.004] (**) Chicony Saitek Eclipse Keyboard: Applying InputClass "evdev keyboard catchall"
[ 31715.004] (II) Using input driver 'evdev' for 'Chicony Saitek Eclipse Keyboard'
[ 31715.004] (**) Chicony Saitek Eclipse Keyboard: always reports core events
[ 31715.004] (**) evdev: Chicony Saitek Eclipse Keyboard: Device: "/dev/input/event3"
[ 31715.004] (--) evdev: Chicony Saitek Eclipse Keyboard: Vendor 0x6a3 Product 0x8020
[ 31715.004] (--) evdev: Chicony Saitek Eclipse Keyboard: Found keys
[ 31715.004] (II) evdev: Chicony Saitek Eclipse Keyboard: Configuring as keyboard
[ 31715.004] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input3/event3"
[ 31715.004] (II) XINPUT: Adding extended input device "Chicony Saitek Eclipse Keyboard" (type: KEYBOARD, id 9)
[ 31715.004] (**) Option "xkb_rules" "evdev"
[ 31715.004] (**) Option "xkb_model" "pc105"
[ 31715.004] (**) Option "xkb_layout" "us"
[ 31715.004] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.00 (/dev/input/event4)
[ 31715.004] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: Applying InputClass "evdev pointer catchall"
[ 31715.004] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Mouse® 1.00'
[ 31715.004] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: always reports core events
[ 31715.004] (**) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Device: "/dev/input/event4"
[ 31715.004] (--) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Vendor 0x45e Product 0xe1
[ 31715.004] (--) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Found 9 mouse buttons
[ 31715.004] (--) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Found scroll wheel(s)
[ 31715.004] (--) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Found relative axes
[ 31715.004] (--) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Found x and y relative axes
[ 31715.004] (II) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Configuring as mouse
[ 31715.004] (II) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: Adding scrollwheel support
[ 31715.004] (**) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: YAxisMapping: buttons 4 and 5
[ 31715.004] (**) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 31715.004] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input4/event4"
[ 31715.004] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse® 1.00" (type: MOUSE, id 10)
[ 31715.005] (II) evdev: Microsoft Microsoft Wireless Optical Mouse® 1.00: initialized for relative axes.
[ 31715.005] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: (accel) keeping acceleration scheme 1
[ 31715.005] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: (accel) acceleration profile 0
[ 31715.005] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: (accel) acceleration factor: 2.000
[ 31715.005] (**) Microsoft Microsoft Wireless Optical Mouse® 1.00: (accel) acceleration threshold: 4
[ 31715.005] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.00 (/dev/input/mouse0)
[ 31715.005] (II) No input driver specified, ignoring this device.
[ 31715.005] (II) This device may have been added with another device file.
[ 31715.005] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event10)
[ 31715.005] (II) No input driver specified, ignoring this device.
[ 31715.005] (II) This device may have been added with another device file.
[ 31715.005] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event11)
[ 31715.005] (II) No input driver specified, ignoring this device.
[ 31715.005] (II) This device may have been added with another device file.
[ 31715.005] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event12)
[ 31715.005] (II) No input driver specified, ignoring this device.
[ 31715.005] (II) This device may have been added with another device file.
[ 31715.005] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event5)
[ 31715.005] (II) No input driver specified, ignoring this device.
[ 31715.005] (II) This device may have been added with another device file.
[ 31715.005] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event6)
[ 31715.005] (II) No input driver specified, ignoring this device.
[ 31715.005] (II) This device may have been added with another device file.
[ 31715.006] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event7)
[ 31715.006] (II) No input driver specified, ignoring this device.
[ 31715.006] (II) This device may have been added with another device file.
[ 31715.006] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event8)
[ 31715.006] (II) No input driver specified, ignoring this device.
[ 31715.006] (II) This device may have been added with another device file.
[ 31715.006] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event9)
[ 31715.006] (II) No input driver specified, ignoring this device.
[ 31715.006] (II) This device may have been added with another device file.
[ 31715.583] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 31715.848] (II) RADEON(0): Using EDID range info for horizontal sync
[ 31715.848] (II) RADEON(0): Using EDID range info for vertical refresh
[ 31715.848] (II) RADEON(0): Printing DDC gathered Modelines:
[ 31715.848] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 31715.848] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 31715.848] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 31717.275] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 31717.276] (II) RADEON(0): Using hsync ranges from config file
[ 31717.276] (II) RADEON(0): Using vrefresh ranges from config file
[ 31717.276] (II) RADEON(0): Printing DDC gathered Modelines:
[ 31717.276] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 31717.276] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 31717.276] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 31725.507] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 31725.507] (II) RADEON(0): Using hsync ranges from config file
[ 31725.507] (II) RADEON(0): Using vrefresh ranges from config file
[ 31725.507] (II) RADEON(0): Printing DDC gathered Modelines:
[ 31725.508] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 31725.508] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 31725.508] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 31725.691] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 31725.691] (II) RADEON(0): Using hsync ranges from config file
[ 31725.692] (II) RADEON(0): Using vrefresh ranges from config file
[ 31725.692] (II) RADEON(0): Printing DDC gathered Modelines:
[ 31725.692] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 31725.692] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 31725.692] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 31725.734] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[ 31746.244] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 31746.244] (II) RADEON(0): Using hsync ranges from config file
[ 31746.244] (II) RADEON(0): Using vrefresh ranges from config file
[ 31746.244] (II) RADEON(0): Printing DDC gathered Modelines:
[ 31746.244] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 31746.244] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 31746.244] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 32792.767] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 32792.767] (II) RADEON(0): Using hsync ranges from config file
[ 32792.767] (II) RADEON(0): Using vrefresh ranges from config file
[ 32792.767] (II) RADEON(0): Printing DDC gathered Modelines:
[ 32792.767] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 32792.767] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 32792.767] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 33651.751] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 33651.752] (II) RADEON(0): Using hsync ranges from config file
[ 33651.752] (II) RADEON(0): Using vrefresh ranges from config file
[ 33651.752] (II) RADEON(0): Printing DDC gathered Modelines:
[ 33651.752] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 33651.752] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 33651.752] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 42860.756] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 43750.415] (II) Open ACPI successful (/var/run/acpid.socket)
[ 43750.415] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 43750.471] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 43750.471] (II) RADEON(0): Using hsync ranges from config file
[ 43750.471] (II) RADEON(0): Using vrefresh ranges from config file
[ 43750.471] (II) RADEON(0): Printing DDC gathered Modelines:
[ 43750.471] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 43750.471] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 43750.471] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 43750.472] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 43752.563] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[ 46376.523] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 46376.524] (II) RADEON(0): Using hsync ranges from config file
[ 46376.524] (II) RADEON(0): Using vrefresh ranges from config file
[ 46376.524] (II) RADEON(0): Printing DDC gathered Modelines:
[ 46376.524] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 46376.524] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 46376.524] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 50757.611] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 50757.612] (II) RADEON(0): Using hsync ranges from config file
[ 50757.612] (II) RADEON(0): Using vrefresh ranges from config file
[ 50757.612] (II) RADEON(0): Printing DDC gathered Modelines:
[ 50757.612] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 50757.612] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 50757.612] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 53004.727] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 53004.727] (II) RADEON(0): Using hsync ranges from config file
[ 53004.727] (II) RADEON(0): Using vrefresh ranges from config file
[ 53004.727] (II) RADEON(0): Printing DDC gathered Modelines:
[ 53004.727] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 53004.727] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 53004.727] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 53004.728] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 54544.743] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 54544.743] (II) RADEON(0): Using hsync ranges from config file
[ 54544.743] (II) RADEON(0): Using vrefresh ranges from config file
[ 54544.743] (II) RADEON(0): Printing DDC gathered Modelines:
[ 54544.743] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 54544.743] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 54544.743] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 54854.251] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 54854.251] (II) RADEON(0): Using hsync ranges from config file
[ 54854.251] (II) RADEON(0): Using vrefresh ranges from config file
[ 54854.251] (II) RADEON(0): Printing DDC gathered Modelines:
[ 54854.252] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 54854.252] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 54854.252] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 56375.239] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 56375.239] (II) RADEON(0): Using hsync ranges from config file
[ 56375.240] (II) RADEON(0): Using vrefresh ranges from config file
[ 56375.240] (II) RADEON(0): Printing DDC gathered Modelines:
[ 56375.240] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 56375.240] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 56375.240] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 59883.555] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 59883.555] (II) RADEON(0): Using hsync ranges from config file
[ 59883.555] (II) RADEON(0): Using vrefresh ranges from config file
[ 59883.555] (II) RADEON(0): Printing DDC gathered Modelines:
[ 59883.555] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 59883.555] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 59883.555] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61477.832] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61477.832] (II) RADEON(0): Using hsync ranges from config file
[ 61477.832] (II) RADEON(0): Using vrefresh ranges from config file
[ 61477.832] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61477.832] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61477.832] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61477.832] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61477.940] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61477.940] (II) RADEON(0): Using hsync ranges from config file
[ 61477.940] (II) RADEON(0): Using vrefresh ranges from config file
[ 61477.940] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61477.940] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61477.940] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61477.940] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61478.216] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61478.216] (II) RADEON(0): Using hsync ranges from config file
[ 61478.216] (II) RADEON(0): Using vrefresh ranges from config file
[ 61478.216] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61478.216] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61478.216] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61478.216] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61478.499] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61478.499] (II) RADEON(0): Using hsync ranges from config file
[ 61478.499] (II) RADEON(0): Using vrefresh ranges from config file
[ 61478.499] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61478.499] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61478.499] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61478.499] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61478.628] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61478.628] (II) RADEON(0): Using hsync ranges from config file
[ 61478.628] (II) RADEON(0): Using vrefresh ranges from config file
[ 61478.628] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61478.628] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61478.628] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61478.628] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61479.476] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61479.476] (II) RADEON(0): Using hsync ranges from config file
[ 61479.476] (II) RADEON(0): Using vrefresh ranges from config file
[ 61479.476] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61479.476] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61479.476] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61479.476] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61481.092] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61481.092] (II) RADEON(0): Using hsync ranges from config file
[ 61481.092] (II) RADEON(0): Using vrefresh ranges from config file
[ 61481.092] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61481.092] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61481.092] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61481.092] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61481.907] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61481.907] (II) RADEON(0): Using hsync ranges from config file
[ 61481.907] (II) RADEON(0): Using vrefresh ranges from config file
[ 61481.907] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61481.907] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61481.907] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61481.907] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61515.600] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61515.600] (II) RADEON(0): Using hsync ranges from config file
[ 61515.600] (II) RADEON(0): Using vrefresh ranges from config file
[ 61515.600] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61515.600] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61515.600] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61515.600] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61533.323] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61533.323] (II) RADEON(0): Using hsync ranges from config file
[ 61533.323] (II) RADEON(0): Using vrefresh ranges from config file
[ 61533.323] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61533.323] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61533.323] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61533.323] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61533.559] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61533.560] (II) RADEON(0): Using hsync ranges from config file
[ 61533.560] (II) RADEON(0): Using vrefresh ranges from config file
[ 61533.560] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61533.560] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61533.560] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61533.560] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61534.391] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61534.392] (II) RADEON(0): Using hsync ranges from config file
[ 61534.392] (II) RADEON(0): Using vrefresh ranges from config file
[ 61534.392] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61534.392] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61534.392] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61534.392] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61541.136] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61541.136] (II) RADEON(0): Using hsync ranges from config file
[ 61541.136] (II) RADEON(0): Using vrefresh ranges from config file
[ 61541.136] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61541.136] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61541.136] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61541.136] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61555.083] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61555.083] (II) RADEON(0): Using hsync ranges from config file
[ 61555.083] (II) RADEON(0): Using vrefresh ranges from config file
[ 61555.083] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61555.083] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61555.083] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61555.083] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 61555.740] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 61555.740] (II) RADEON(0): Using hsync ranges from config file
[ 61555.740] (II) RADEON(0): Using vrefresh ranges from config file
[ 61555.740] (II) RADEON(0): Printing DDC gathered Modelines:
[ 61555.740] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 61555.740] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 61555.740] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 67608.999] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 67609.000] (II) RADEON(0): Using hsync ranges from config file
[ 67609.000] (II) RADEON(0): Using vrefresh ranges from config file
[ 67609.000] (II) RADEON(0): Printing DDC gathered Modelines:
[ 67609.000] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 67609.000] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 67609.000] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 82693.703] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 82693.703] (II) RADEON(0): Using hsync ranges from config file
[ 82693.703] (II) RADEON(0): Using vrefresh ranges from config file
[ 82693.703] (II) RADEON(0): Printing DDC gathered Modelines:
[ 82693.703] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 82693.703] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 82693.703] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 82693.704] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 82693.704] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 98091.007] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[ 98091.008] (II) RADEON(0): Using hsync ranges from config file
[ 98091.008] (II) RADEON(0): Using vrefresh ranges from config file
[ 98091.008] (II) RADEON(0): Printing DDC gathered Modelines:
[ 98091.008] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 98091.008] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 98091.008] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[ 98907.165] (II) AIGLX: Suspending AIGLX clients for VT switch
[101052.266] (II) Open ACPI successful (/var/run/acpid.socket)
[101052.266] (II) AIGLX: Resuming AIGLX clients after VT switch
[101052.323] (II) RADEON(0): EDID vendor "DEL", prod id 41068
[101052.323] (II) RADEON(0): Using hsync ranges from config file
[101052.323] (II) RADEON(0): Using vrefresh ranges from config file
[101052.323] (II) RADEON(0): Printing DDC gathered Modelines:
[101052.323] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[101052.323] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[101052.323] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[101052.323] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[101052.323] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[101052.323] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[101052.323] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[101052.323] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[101052.323] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[101052.323] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[101052.323] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[101052.323] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[101055.093] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
```

---

