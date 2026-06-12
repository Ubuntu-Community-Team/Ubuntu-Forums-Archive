---
title: "ATI X1270 driver"
date: 2011-01-11
forum: Multimedia Software
---

### Post by Joe Awsome on 2011-01-11
Hey all, I just got a new-to-me Gateway LT3114u netbook that had come with Vista on it. Vista almost ate itself and I had just done an install of Ubuntu 10.10 64 bit (dual boot). I love everything about the 64 bit version of Ubuntu except for the minor quirks and glitches, but the biggest thing I miss about it is the 3D support for my ATI Radeon X1270. I've done several google searches for drivers but none come up, and the additional drivers tab under administration shows a white screen, even after searching ATI. I don't even have the open-source driver running. Needless to say that I can't play any of the 3D games I installed or watch any flash videos over 480p. If anyone has info or (better yet) a solution to the problem, please post back.

---

### Post by tjones00 on 2011-01-11
That card should be of the RS600 series. ATI dropped support for it 2 years ago. 

[http://forum.thinkpads.com/viewtopic.php?f=9&t=75239](http://forum.thinkpads.com/viewtopic.php?f=9&t=75239)

The open source driver is installed by default with Ubuntu. If it wasn't running I don't think you'd even have a 2d graphical display unless you were using vesa or something.

Open a terminal and type lsmod.

If you see ati or radeon in the output from that command the opensource driver is active.

You have a couple options.

1) use a different distro of linux that uses x server version 1.5 and find a copy of the ati proprietary driver < 9.4 (the ati website should have some archives),
- go to distrowatch.com and search by package xserver-xorg =< 1.5
- eg. debian lenny 5.0

2) use a older release of ubuntu that uses x server version 1.5 
- eg. ubuntu 8.04

3) figure out how to tweak the ati/radeon open source driver for your card (which might not even be supported for 3d)

And yes you read this right ATI dropped support for cards that were only 4 years old at the time. RS600 series was being used for integrated graphics on new motherboards circa 2005.

---

### Post by Joe Awsome on 2011-01-12
ok, here is what I've got for lsmod:
```
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_realtek   299844  1 
arc4                    1497  2 
d
radeon                909450  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
ath9k                 101730  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
joydev                 11395  0 
snd_seq_midi            5932  0 
ath9k_common            6874  1 ath9k
snd_rawmidi            22207  1 snd_seq_midi
ttm                    68212  1 radeon
ath9k_hw              314699  2 ath9k,ath9k_common
snd_seq_midi_event      7291  1 snd_seq_midi
ath                    10413  2 ath9k,ath9k_hw
drm_kms_helper         32836  1 radeon
mac80211              266625  2 ath9k,ath9k_common
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62379  0 
drm                   206230  4 radeon,ttm,drm_kms_helper
videodev               49359  1 uvcvideo
cfg80211              170293  4 ath9k,ath9k_common,ath,mac80211
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acerhdf                 8675  0 
v4l1_compat            15519  2 uvcvideo,videodev
video                  22176  0 
edac_core              46822  0 
psmouse                62080  0 
v4l2_compat_ioctl32    12614  1 videodev
i2c_algo_bit            6208  1 radeon
soundcore               1240  1 snd
serio_raw               4910  0 
edac_mce_amd            9387  0 
k8temp                  4128  0 
output                  2527  1 video
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
led_class               3393  1 ath9k
i2c_piix4              10047  0 
shpchp                 34910  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   22210  2 
r8169                  42254  0 
pata_atiixp             4405  0 
libahci                26052  1 ahci
mii                     5261  1 r8169

```

it does appear that radeon is running, but now the question why I don't have any 3D or openGL support from the driver. I've checked what I have installed on my system through software center, and vesa is also present. Thanks for your input on this tjones00.

---

### Post by tjones00 on 2011-01-12
It could simply be that even the opensource driver does not support 3d acceleration on that card. Not all cards are 3d enabled with the opensource driver.

I was messing with a X1250 about half a year ago I was trying out the radeonhd driver though (not recommended since it is no longer in development) to enable hdmi audio. radeonhd didn't support my card for 3d acceleration. Off the top of my head I think my last theory regarding it involved the AtomBIOS on the card not being recognized which is required to setup the card properly.

I can confirm you can install the ati proprietary driver with the card in hardy ubuntu 8.04 and in debian 5.0 lenny.

The radeonhd driver was merged into the radeon project creating one opensource driver.

Try looking at the following logs:

Xorg.0.log at /var/log/Xorg.0.log <--X server log
dmesg at /var/log/dmesg <--driver log
kern.log at /var/log/kern.log <--kernel log

To force custom settings you might have to turn off kms in the kernel via nomodeset and create an xorg.conf.

If you go about troubleshooting I'd start with confirming the AtomBIOS is gathered and setup properly. If not you can force a specific AtomBIOS to be loaded but the hard part is you need to get the one (from somewhere?) that matches your card. Then move onto stuff like dri.

I no longer have my X1250 so that's all the direction I can give you.

---

### Post by Joe Awsome on 2011-01-12
Thanks for all the help on the topic. I've been reading around on the web, but it looks like the only option for getting good 3D support for my card is going to be rolling to 8.04. It would be great for somebody to make a compatible legacy driver for the Twilight Zone that so many people with these cards have fallen into. So if anyone knows someone experienced with graphics drivers, could you please present this problem to them. If anyone has a solution to this problem or has found a work around for it, don't be afraid to post it here. Thanks everyone.

---

### Post by tjones00 on 2011-01-13
According to the distrowatch ubuntu page.

Ubuntu 8.10 uses x server 1.5.2 so you might be able to use that release as well with the ati proprietary driver. It still safer to stick with 8.04 since that was the LTS release.

[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)

---

### Post by Mark Phelps on 2011-01-13
Until recently, I had an ATI x1650 -- and it worked fine with restricted drivers through Ubuntu 8.10.  IT was not until 9.04 that driver support was dropped.

SO, you should be OK with 8.10.

---

### Post by Yellow Pasque on 2011-01-13
I'd suggest trying the xorg-edgers PPA. Those are the best open-source drivers for legacy cards. At any rate, you should have basic 3D acceleration (enough to run desktop effects and openarena). IF you don't, then your install's borked and post output of glxinfo:
```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```

Also, this might interest you: [http://www.phoronix.com/scan.php?page=article&item=ati_r500_pflipper&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r500_pflipper&num=1)

---

### Post by Joe Awsome on 2011-01-16
```

joe@joe-LT31:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
thanks for the info about that Temujin, I'll be sure to read through it. Would mesa-utils fix the lacking 3D support in the open-source driver? Is there any way to get 3D support for this card? By the way, I already have the xorg stable ppa installed right now with no improvement, but i'll keep edgers in mind and try it tonight.

---

### Post by Yellow Pasque on 2011-01-16
I'm guessing you tried to install ATI proprietary drivers anyway. Follow this: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by tjones00 on 2011-01-16
If you're using the opensource driver (radeon/ati) again in 10.10 post your /var/log/Xorg.0.log

If it's an AtomBIOS error like I had (will be visible in the log) it's pretty much game over. Maybe the radeon/ati developers dropped support for the older cards as well with all the kms work they're doing.

---

### Post by imsael on 2011-01-17
I have an ATI X1250 and I also have a pproblem with it. But it is a bit different. I use the xserver packages....What happen is that i do get 2d and 3d options enable...but then, the background image of my desktop is messed up....It doesn't happen if I uninstall xserver....

Any help?

---

### Post by imsael on 2011-01-17
I have an ATI X1250 and I also have a pproblem with it. But it is a bit different. I use the xserver packages....What happen is that i do get 2d and 3d options enable...but then, the background image of my desktop is messed up....It doesn't happen if I uninstall xserver....

Any help?

---

### Post by imsael on 2011-01-17
I have an ATI X1250 and I also have a pproblem with it. But it is a bit different. I use the xserver packages....What happen is that i do get 2d and 3d options enable...but then, the background image of my desktop is messed up....It doesn't happen if I uninstall xserver....

Any help?

---

### Post by tjones00 on 2011-01-17
post your /var/log/Xorg.0.log

---

### Post by imsael on 2011-01-17
First sorry that I post 3 times the same reply....my browser frozed and I pushed the button post too much I think....

Here is my Xorg.0.log file:

[    22.493] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    22.493] X Protocol Version 11, Revision 0
[    22.493] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    22.493] Current Operating System: Linux daniel-U210 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    22.494] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=e5c4bd6f-65c2-4dab-a73f-a76685d0fe5a ro vga=792 quiet splash
[    22.494] Build Date: 23 November 2010  09:54:06PM
[    22.494] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.494] Current version of pixman: 0.18.4
[    22.494] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.494] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.494] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 17 14:20:30 2011
[    22.512] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.513] (==) No Layout section.  Using the first Screen section.
[    22.513] (==) No screen section available. Using defaults.
[    22.513] (**) |-->Screen "Default Screen Section" (0)
[    22.513] (**) |   |-->Monitor "<default monitor>"
[    22.513] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.513] (==) Automatically adding devices
[    22.513] (==) Automatically enabling devices
[    22.513] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.513] 	Entry deleted from font path.
[    22.514] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.514] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.514] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.514] (II) Loader magic: 0x81f8e00
[    22.514] (II) Module ABI versions:
[    22.514] 	X.Org ANSI C Emulation: 0.4
[    22.514] 	X.Org Video Driver: 8.0
[    22.514] 	X.Org XInput driver : 11.0
[    22.514] 	X.Org Server Extension : 4.0
[    22.515] (--) PCI:*(0:1:5:0) 1002:791f:1462:1022 rev 0, Mem @ 0xf0000000/134217728, 0xfe9f0000/65536, 0xfe800000/1048576, I/O @ 0x0000d000/256
[    22.515] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.515] (II) LoadModule: "extmod"
[    22.528] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.529] (II) Module extmod: vendor="X.Org Foundation"
[    22.529] 	compiled for 1.9.0, module version = 1.0.0
[    22.529] 	Module class: X.Org Server Extension
[    22.529] 	ABI class: X.Org Server Extension, version 4.0
[    22.529] (II) Loading extension MIT-SCREEN-SAVER
[    22.529] (II) Loading extension XFree86-VidModeExtension
[    22.529] (II) Loading extension XFree86-DGA
[    22.529] (II) Loading extension DPMS
[    22.529] (II) Loading extension XVideo
[    22.529] (II) Loading extension XVideo-MotionCompensation
[    22.529] (II) Loading extension X-Resource
[    22.529] (II) LoadModule: "dbe"
[    22.529] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.529] (II) Module dbe: vendor="X.Org Foundation"
[    22.529] 	compiled for 1.9.0, module version = 1.0.0
[    22.529] 	Module class: X.Org Server Extension
[    22.529] 	ABI class: X.Org Server Extension, version 4.0
[    22.530] (II) Loading extension DOUBLE-BUFFER
[    22.530] (II) LoadModule: "glx"
[    22.530] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.530] (II) Module glx: vendor="X.Org Foundation"
[    22.530] 	compiled for 1.9.0, module version = 1.0.0
[    22.530] 	ABI class: X.Org Server Extension, version 4.0
[    22.530] (==) AIGLX enabled
[    22.530] (II) Loading extension GLX
[    22.530] (II) LoadModule: "record"
[    22.531] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.531] (II) Module record: vendor="X.Org Foundation"
[    22.531] 	compiled for 1.9.0, module version = 1.13.0
[    22.531] 	Module class: X.Org Server Extension
[    22.531] 	ABI class: X.Org Server Extension, version 4.0
[    22.531] (II) Loading extension RECORD
[    22.531] (II) LoadModule: "dri"
[    22.536] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.536] (II) Module dri: vendor="X.Org Foundation"
[    22.536] 	compiled for 1.9.0, module version = 1.0.0
[    22.536] 	ABI class: X.Org Server Extension, version 4.0
[    22.536] (II) Loading extension XFree86-DRI
[    22.536] (II) LoadModule: "dri2"
[    22.536] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.536] (II) Module dri2: vendor="X.Org Foundation"
[    22.537] 	compiled for 1.9.0, module version = 1.2.0
[    22.537] 	ABI class: X.Org Server Extension, version 4.0
[    22.537] (II) Loading extension DRI2
[    22.537] (==) Matched ati as autoconfigured driver 0
[    22.537] (==) Matched vesa as autoconfigured driver 1
[    22.537] (==) Matched fbdev as autoconfigured driver 2
[    22.537] (==) Assigned the driver to the xf86ConfigLayout
[    22.537] (II) LoadModule: "ati"
[    22.537] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    22.542] (II) Module ati: vendor="X.Org Foundation"
[    22.542] 	compiled for 1.9.0, module version = 6.13.1
[    22.543] 	Module class: X.Org Video Driver
[    22.543] 	ABI class: X.Org Video Driver, version 8.0
[    22.543] (II) LoadModule: "radeon"
[    22.543] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.574] (II) Module radeon: vendor="X.Org Foundation"
[    22.574] 	compiled for 1.9.0, module version = 6.13.1
[    22.574] 	Module class: X.Org Video Driver
[    22.574] 	ABI class: X.Org Video Driver, version 8.0
[    22.575] (II) LoadModule: "vesa"
[    22.575] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.575] (II) Module vesa: vendor="X.Org Foundation"
[    22.575] 	compiled for 1.8.99.905, module version = 2.3.0
[    22.576] 	Module class: X.Org Video Driver
[    22.576] 	ABI class: X.Org Video Driver, version 8.0
[    22.576] (II) LoadModule: "fbdev"
[    22.576] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.576] (II) Module fbdev: vendor="X.Org Foundation"
[    22.576] 	compiled for 1.8.99.905, module version = 0.4.2
[    22.576] 	ABI class: X.Org Video Driver, version 8.0
[    22.576] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
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
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
[    22.600] (II) VESA: driver for VESA chipsets: vesa
[    22.600] (II) FBDEV: driver for framebuffer: fbdev
[    22.600] (++) using VT number 7

[    22.600] (II) [KMS] Kernel modesetting enabled.
[    22.600] (WW) Falling back to old probe method for vesa
[    22.600] (WW) Falling back to old probe method for fbdev
[    22.601] (II) Loading sub module "fbdevhw"
[    22.601] (II) LoadModule: "fbdevhw"
[    22.601] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.601] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.601] 	compiled for 1.9.0, module version = 0.0.2
[    22.601] 	ABI class: X.Org Video Driver, version 8.0
[    22.601] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.601] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    22.601] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    22.601] (==) RADEON(0): Default visual is TrueColor
[    22.601] (==) RADEON(0): RGB weight 888
[    22.601] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    22.601] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    22.602] (II) RADEON(0): PCI card detected
[    22.602] (II) RADEON(0): KMS Color Tiling: enabled
[    22.602] drmOpenDevice: node name is /dev/dri/card0
[    22.602] drmOpenDevice: open result is 9, (OK)
[    22.602] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    22.602] drmOpenDevice: node name is /dev/dri/card0
[    22.602] drmOpenDevice: open result is 9, (OK)
[    22.602] drmOpenByBusid: drmOpenMinor returns 9
[    22.602] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    22.752] (II) RADEON(0): Output VGA-0 has no monitor section
[    22.752] (II) RADEON(0): Output LVDS has no monitor section
[    22.760] (II) RADEON(0): Output HDMI-0 has no monitor section
[    22.904] (II) RADEON(0): EDID for output VGA-0
[    22.904] (II) RADEON(0): EDID for output LVDS
[    22.904] (II) RADEON(0): Manufacturer: HSD  Model: 4b6  Serial#: 9918
[    22.904] (II) RADEON(0): Year: 2009  Week: 24
[    22.904] (II) RADEON(0): EDID Version: 1.3
[    22.904] (II) RADEON(0): Digital Display Input
[    22.904] (II) RADEON(0): Max Image Size [cm]: horiz.: 27  vert.: 15
[    22.904] (II) RADEON(0): Gamma: 2.20
[    22.904] (II) RADEON(0): No DPMS capabilities specified
[    22.904] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    22.904] (II) RADEON(0): First detailed timing is preferred mode
[    22.904] (II) RADEON(0): redX: 0.591 redY: 0.354   greenX: 0.322 greenY: 0.547
[    22.904] (II) RADEON(0): blueX: 0.153 blueY: 0.098   whiteX: 0.313 whiteY: 0.329
[    22.904] (II) RADEON(0): Manufacturer's mask: 0
[    22.904] (II) RADEON(0): Supported detailed timing:
[    22.904] (II) RADEON(0): clock: 71.9 MHz   Image Size:  270 x 150 mm
[    22.904] (II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1480 h_blank_end 1486 h_border: 0
[    22.904] (II) RADEON(0): v_active: 768  v_sync: 774  v_sync_end 782 v_blanking: 806 v_border: 0
[    22.904] (II) RADEON(0):  
[    22.904] (II) RADEON(0): Monitor name: HSD121PHW1
[    22.904] (II) RADEON(0): EDID (in hex):
[    22.904] (II) RADEON(0): 	00ffffffffffff002264b604be260000
[    22.904] (II) RADEON(0): 	18130103801b0f780a6845975a528c27
[    22.904] (II) RADEON(0): 	19505400000001010101010101010101
[    22.904] (II) RADEON(0): 	010101010101161c5678500026303042
[    22.904] (II) RADEON(0): 	68000e9610000019000000fe00000000
[    22.904] (II) RADEON(0): 	00000000000000000000000000fc0048
[    22.904] (II) RADEON(0): 	5344313231504857310a202000000010
[    22.904] (II) RADEON(0): 	000a2020202020202020202020200059
[    22.904] (II) RADEON(0): Printing probed modes for output LVDS
[    22.904] (II) RADEON(0): Modeline "1366x768"x60.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    22.904] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    22.905] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    22.905] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    22.905] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    22.905] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    22.905] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    22.905] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    22.913] (II) RADEON(0): EDID for output HDMI-0
[    22.913] (II) RADEON(0): Output VGA-0 disconnected
[    22.913] (II) RADEON(0): Output LVDS connected
[    22.913] (II) RADEON(0): Output HDMI-0 disconnected
[    22.913] (II) RADEON(0): Using exact sizes for initial modes
[    22.913] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    22.913] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.913] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:8000000 visible:7ba0000
[    22.913] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    22.914] (==) RADEON(0): DPI set to (96, 96)
[    22.914] (II) Loading sub module "fb"
[    22.914] (II) LoadModule: "fb"
[    22.915] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.915] (II) Module fb: vendor="X.Org Foundation"
[    22.915] 	compiled for 1.9.0, module version = 1.0.0
[    22.915] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.915] (II) Loading sub module "ramdac"
[    22.915] (II) LoadModule: "ramdac"
[    22.915] (II) Module "ramdac" already built-in
[    22.915] (II) Loading sub module "exa"
[    22.915] (II) LoadModule: "exa"
[    22.915] (II) Loading /usr/lib/xorg/modules/libexa.so
[    22.926] (II) Module exa: vendor="X.Org Foundation"
[    22.926] 	compiled for 1.9.0, module version = 2.5.0
[    22.926] 	ABI class: X.Org Video Driver, version 8.0
[    22.926] (II) UnloadModule: "vesa"
[    22.926] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.926] (II) UnloadModule: "fbdev"
[    22.926] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.926] (II) UnloadModule: "fbdevhw"
[    22.926] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    22.926] (--) Depth 24 pixmap format is 32 bpp
[    22.926] (II) RADEON(0): [DRI2] Setup complete
[    22.926] (II) RADEON(0): [DRI2]   DRI driver: r300
[    22.926] (II) RADEON(0): Front buffer size: 4224K
[    22.926] (II) RADEON(0): VRAM usage limit set to 110131K
[    22.926] (==) RADEON(0): Backing store disabled
[    22.926] (II) RADEON(0): Direct rendering enabled
[    22.926] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    22.926] (II) RADEON(0): Setting EXA maxPitchBytes
[    22.926] (II) EXA(0): Driver allocated offscreen pixmaps
[    22.926] (II) EXA(0): Driver registered support for the following operations:
[    22.927] (II)         Solid
[    22.927] (II)         Copy
[    22.927] (II)         Composite (RENDER acceleration)
[    22.927] (II)         UploadToScreen
[    22.927] (II)         DownloadFromScreen
[    22.927] (II) RADEON(0): Acceleration enabled
[    22.927] (==) RADEON(0): DPMS enabled
[    22.927] (==) RADEON(0): Silken mouse enabled
[    22.928] (II) RADEON(0): Set up textured video
[    22.928] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.928] (--) RandR disabled
[    22.928] (II) Initializing built-in extension Generic Event Extension
[    22.928] (II) Initializing built-in extension SHAPE
[    22.928] (II) Initializing built-in extension MIT-SHM
[    22.928] (II) Initializing built-in extension XInputExtension
[    22.928] (II) Initializing built-in extension XTEST
[    22.928] (II) Initializing built-in extension BIG-REQUESTS
[    22.928] (II) Initializing built-in extension SYNC
[    22.928] (II) Initializing built-in extension XKEYBOARD
[    22.928] (II) Initializing built-in extension XC-MISC
[    22.928] (II) Initializing built-in extension SECURITY
[    22.928] (II) Initializing built-in extension XINERAMA
[    22.928] (II) Initializing built-in extension XFIXES
[    22.928] (II) Initializing built-in extension RENDER
[    22.928] (II) Initializing built-in extension RANDR
[    22.928] (II) Initializing built-in extension COMPOSITE
[    22.928] (II) Initializing built-in extension DAMAGE
[    22.928] (II) Initializing built-in extension GESTURE
[    23.032] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.032] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.032] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.032] (II) AIGLX: enabled GLX_SGI_make_current_read
[    23.032] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.033] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    23.033] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.048] (II) RADEON(0): Setting screen physical size to 361 x 203
[    23.114] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.144] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.144] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.144] (II) LoadModule: "evdev"
[    23.145] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.145] (II) Module evdev: vendor="X.Org Foundation"
[    23.145] 	compiled for 1.9.0, module version = 2.3.2
[    23.145] 	Module class: X.Org XInput Driver
[    23.145] 	ABI class: X.Org XInput driver, version 11.0
[    23.145] (**) Power Button: always reports core events
[    23.146] (**) Power Button: Device: "/dev/input/event2"
[    23.146] (II) Power Button: Found keys
[    23.146] (II) Power Button: Configuring as keyboard
[    23.146] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.146] (**) Option "xkb_rules" "evdev"
[    23.146] (**) Option "xkb_model" "evdev"
[    23.146] (**) Option "xkb_layout" "ca"
[    23.153] (II) XKB: reuse xkmfile /var/lib/xkb/server-4DD1055D4556C32D774518CD79B413B9137529F7.xkm
[    23.155] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    23.155] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.155] (**) Video Bus: always reports core events
[    23.155] (**) Video Bus: Device: "/dev/input/event7"
[    23.155] (II) Video Bus: Found keys
[    23.155] (II) Video Bus: Configuring as keyboard
[    23.155] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    23.155] (**) Option "xkb_rules" "evdev"
[    23.155] (**) Option "xkb_model" "evdev"
[    23.155] (**) Option "xkb_layout" "ca"
[    23.161] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.161] (II) No input driver/identifier specified (ignoring)
[    23.162] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.162] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.162] (**) Power Button: always reports core events
[    23.162] (**) Power Button: Device: "/dev/input/event1"
[    23.162] (II) Power Button: Found keys
[    23.162] (II) Power Button: Configuring as keyboard
[    23.162] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.162] (**) Option "xkb_rules" "evdev"
[    23.162] (**) Option "xkb_model" "evdev"
[    23.162] (**) Option "xkb_layout" "ca"
[    23.170] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Nano Transceiver v2.0 (/dev/input/event4)
[    23.171] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    23.171] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: always reports core events
[    23.171] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Device: "/dev/input/event4"
[    23.171] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found keys
[    23.171] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Configuring as keyboard
[    23.171] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Nano Transceiver v2.0" (type: KEYBOARD)
[    23.171] (**) Option "xkb_rules" "evdev"
[    23.171] (**) Option "xkb_model" "evdev"
[    23.171] (**) Option "xkb_layout" "ca"
[    23.176] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Nano Transceiver v2.0 (/dev/input/event5)
[    23.176] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[    23.176] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    23.176] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: always reports core events
[    23.176] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Device: "/dev/input/event5"
[    23.176] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found 9 mouse buttons
[    23.176] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found scroll wheel(s)
[    23.176] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found relative axes
[    23.176] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found x and y relative axes
[    23.176] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found absolute axes
[    23.176] (II) evdev-grail: failed to open grail, no gesture support
[    23.176] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found keys
[    23.177] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Configuring as mouse
[    23.177] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Configuring as keyboard
[    23.177] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    23.177] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.177] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Nano Transceiver v2.0" (type: KEYBOARD)
[    23.177] (**) Option "xkb_rules" "evdev"
[    23.177] (**) Option "xkb_model" "evdev"
[    23.177] (**) Option "xkb_layout" "ca"
[    23.177] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: initialized for relative axes.
[    23.177] (WW) Microsoft MicrosoftÂ® Nano Transceiver v2.0: ignoring absolute axes.
[    23.178] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Nano Transceiver v2.0 (/dev/input/mouse0)
[    23.178] (II) No input driver/identifier specified (ignoring)
[    23.178] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Nano Transceiver v2.0 (/dev/input/event6)
[    23.178] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[    23.178] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: always reports core events
[    23.178] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Device: "/dev/input/event6"
[    23.178] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found 1 mouse buttons
[    23.178] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found scroll wheel(s)
[    23.178] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found relative axes
[    23.179] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found absolute axes
[    23.179] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found x and y absolute axes
[    23.179] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Found keys
[    23.179] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Configuring as mouse
[    23.179] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: Configuring as keyboard
[    23.179] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[    23.179] (**) Microsoft MicrosoftÂ® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.179] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® Nano Transceiver v2.0" (type: KEYBOARD)
[    23.179] (**) Option "xkb_rules" "evdev"
[    23.179] (**) Option "xkb_model" "evdev"
[    23.179] (**) Option "xkb_layout" "ca"
[    23.179] (EE) Microsoft MicrosoftÂ® Nano Transceiver v2.0: failed to initialize for relative axes.
[    23.179] (WW) Device 'Microsoft MicrosoftÂ® Nano Transceiver v2.0' has 37 axes, only using first 36.
[    23.179] (II) Microsoft MicrosoftÂ® Nano Transceiver v2.0: initialized for absolute axes.
[    23.184] (II) config/udev: Adding input device Microsoft MicrosoftÂ® Nano Transceiver v2.0 (/dev/input/js0)
[    23.184] (II) No input driver/identifier specified (ignoring)
[    23.186] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event8)
[    23.186] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    23.186] (**) BisonCam, NB Pro: always reports core events
[    23.186] (**) BisonCam, NB Pro: Device: "/dev/input/event8"
[    23.186] (II) BisonCam, NB Pro: Found keys
[    23.186] (II) BisonCam, NB Pro: Configuring as keyboard
[    23.187] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD)
[    23.187] (**) Option "xkb_rules" "evdev"
[    23.187] (**) Option "xkb_model" "evdev"
[    23.187] (**) Option "xkb_layout" "ca"
[    23.192] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.192] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.192] (**) AT Translated Set 2 keyboard: always reports core events
[    23.192] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.192] (II) AT Translated Set 2 keyboard: Found keys
[    23.192] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.192] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.192] (**) Option "xkb_rules" "evdev"
[    23.192] (**) Option "xkb_model" "evdev"
[    23.192] (**) Option "xkb_layout" "ca"
[    23.193] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    23.193] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.193] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.193] (II) LoadModule: "synaptics"
[    23.194] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.194] (II) Module synaptics: vendor="X.Org Foundation"
[    23.194] 	compiled for 1.9.0, module version = 1.2.2
[    23.194] 	Module class: X.Org XInput Driver
[    23.194] 	ABI class: X.Org XInput driver, version 11.0
[    23.194] (II) Synaptics touchpad driver version 1.2.2
[    23.194] (**) Option "Device" "/dev/input/event9"
[    23.194] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    23.194] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    23.194] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.194] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    23.194] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[    23.194] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.194] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.194] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    23.195] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.195] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    23.195] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.195] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.195] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.195] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    23.195] (II) No input driver/identifier specified (ignoring)
[    24.188] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    24.188] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.188] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    24.344] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    24.344] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.344] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    24.504] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    24.504] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.504] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    24.660] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    24.660] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.660] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    33.616] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    33.616] (II) RADEON(0): Printing DDC gathered Modelines:
[    33.616] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    33.764] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    33.764] (II) RADEON(0): Printing DDC gathered Modelines:
[    33.764] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[    36.216] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[    36.216] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.216] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[  3408.212] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[  3408.212] (II) RADEON(0): Printing DDC gathered Modelines:
[  3408.212] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[  3408.368] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[  3408.368] (II) RADEON(0): Printing DDC gathered Modelines:
[  3408.368] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[  3409.000] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[  3409.000] (II) RADEON(0): Printing DDC gathered Modelines:
[  3409.000] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[  3409.520] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[  3409.520] (II) RADEON(0): Printing DDC gathered Modelines:
[  3409.520] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[  3410.108] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[  3410.108] (II) RADEON(0): Printing DDC gathered Modelines:
[  3410.108] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)
[  3410.288] (II) RADEON(0): EDID vendor "HSD", prod id 1206
[  3410.288] (II) RADEON(0): Printing DDC gathered Modelines:
[  3410.288] (II) RADEON(0): Modeline "1366x768"x0.0   71.90  1366 1414 1480 1486  768 774 782 806 -hsync -vsync (48.4 kHz)

Is it the right way to pos it? it makes a lot of text!!!

Thanks!!

---

### Post by tjones00 on 2011-01-17
It appears to recognize your card.

Try turning kms off and using an xorg.conf see if the problem is still there.

The only thing I see is.

[ 22.600] (II) [KMS] Kernel modesetting enabled.
[ 22.600] (WW) Falling back to old probe method for vesa
[ 22.600] (WW) Falling back to old probe method for fbdev
[ 22.601] (II) Loading sub module "fbdevhw"

I'm not sure if this is the standard way kms should work with radeon/ati hence the suggestion of turning it off and using a standard xorg.conf.

```
sudo Xorg -configure

gksudo gedit /etc/default/grub
```

change quiet splash to nomodeset and save the file.

```
sudo update-grub2

sudo reboot
```

To reverse this change undo the /etc/default/grub edit update-grub2 and remove the xorg.conf 

```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Joe Awsome on 2011-01-17
lsmod still shows that I'm using the standard radeon driver, but how would I switch over to the Gallium driver? I already have both the stable and edgers ppa for xorg, and I have kept my computer up to date since, so the Gallium driver should be downloaded. But I don't know how I would have Ubuntu use the Gallium instead of radeon.
```
joe@joe-LT31:~$ lsmod
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_realtek   299844  1 
arc4                    1497  2 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
radeon                909450  2 
snd_hwdep               6660  1 snd_hda_codec
joydev                 11395  0 
ath9k                 101730  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
ath9k_common            6874  1 ath9k
snd_rawmidi            22207  1 snd_seq_midi
ath9k_hw              314699  2 ath9k,ath9k_common
ttm                    68212  1 radeon
snd_seq_midi_event      7291  1 snd_seq_midi
ath                    10413  2 ath9k,ath9k_hw
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32836  1 radeon
mac80211              266625  2 ath9k,ath9k_common
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62379  0 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170293  4 ath9k,ath9k_common,ath,mac80211
acerhdf                 8675  0 
drm                   206230  4 radeon,ttm,drm_kms_helper
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
edac_core              46822  0 
v4l2_compat_ioctl32    12614  1 videodev
i2c_algo_bit            6208  1 radeon
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
psmouse                62080  0 
serio_raw               4910  0 
video                  22176  0 
output                  2527  1 video
edac_mce_amd            9387  0 
k8temp                  4128  0 
i2c_piix4              10047  0 
shpchp                 34910  0 
led_class               3393  1 ath9k
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
r8169                  42254  0 
ahci                   22210  3 
pata_atiixp             4405  0 
mii                     5261  1 r8169
libahci                26052  1 ahci

```

---

### Post by imsael on 2011-01-17
it worked!! thanks!

---

### Post by tjones00 on 2011-01-17
I know you might not visit this thread again but if you could imsael can you post the new Xorg.0.log so people can compare it vs the old one you posted.

Maybe it was the KMS probe method for vesa and fbdev but we can't tell for sure without the log.

---

### Post by Joe Awsome on 2011-01-21
Well i still don't have 3D support for my graphics card even with the edgers ppa installed on my system. that and it's still using the old radeon driver and not the Gallium driver. Since imsael was able to fix his x1250 card by modifying his xorg.0.log, so the problem might also be with mine too.
```
[    19.391] 
X.Org X Server 1.9.2.901 (1.9.3 RC 1)
Release Date: 2010-11-13
[    19.392] X Protocol Version 11, Revision 0
[    19.392] Build Operating System: Linux 2.6.24-28-xen x86_64 Ubuntu
[    19.392] Current Operating System: Linux joe-LT31 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    19.392] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=9e6f38fa-81ed-4c47-ad55-8c04c1f2e1c4 ro quiet splash
[    19.392] Build Date: 29 November 2010  03:31:56PM
[    19.392] xorg-server 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick (For technical support please see http://www.ubuntu.com/support) 
[    19.392] Current version of pixman: 0.21.2
[    19.392] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.392] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.392] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 21 13:50:12 2011
[    19.440] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.478] (==) No Layout section.  Using the first Screen section.
[    19.478] (==) No screen section available. Using defaults.
[    19.478] (**) |-->Screen "Default Screen Section" (0)
[    19.478] (**) |   |-->Monitor "<default monitor>"
[    19.496] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    19.496] (==) Automatically adding devices
[    19.496] (==) Automatically enabling devices
[    19.519] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.520] 	Entry deleted from font path.
[    19.603] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.603] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.603] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.603] (II) Loader magic: 0x7d1d00
[    19.603] (II) Module ABI versions:
[    19.603] 	X.Org ANSI C Emulation: 0.4
[    19.603] 	X.Org Video Driver: 8.0
[    19.603] 	X.Org XInput driver : 11.0
[    19.603] 	X.Org Server Extension : 4.0
[    19.605] (--) PCI:*(0:1:5:0) 1002:791f:1025:028c rev 0, Mem @ 0xd0000000/268435456, 0xf0100000/65536, 0xf0000000/1048576, I/O @ 0x00009000/256
[    19.605] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.606] (II) LoadModule: "extmod"
[    19.679] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.715] (II) Module extmod: vendor="X.Org Foundation"
[    19.715] 	compiled for 1.9.2.901, module version = 1.0.0
[    19.715] 	Module class: X.Org Server Extension
[    19.715] 	ABI class: X.Org Server Extension, version 4.0
[    19.715] (II) Loading extension MIT-SCREEN-SAVER
[    19.715] (II) Loading extension XFree86-VidModeExtension
[    19.715] (II) Loading extension XFree86-DGA
[    19.715] (II) Loading extension DPMS
[    19.715] (II) Loading extension XVideo
[    19.715] (II) Loading extension XVideo-MotionCompensation
[    19.715] (II) Loading extension X-Resource
[    19.715] (II) LoadModule: "dbe"
[    19.715] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.723] (II) Module dbe: vendor="X.Org Foundation"
[    19.723] 	compiled for 1.9.2.901, module version = 1.0.0
[    19.723] 	Module class: X.Org Server Extension
[    19.723] 	ABI class: X.Org Server Extension, version 4.0
[    19.723] (II) Loading extension DOUBLE-BUFFER
[    19.723] (II) LoadModule: "glx"
[    19.723] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    20.744] (II) Module glx: vendor="NVIDIA Corporation"
[    20.765] 	compiled for 4.0.2, module version = 1.0.0
[    20.765] 	Module class: X.Org Server Extension
[    20.765] (II) NVIDIA GLX Module  260.19.29  Wed Dec  8 12:24:30 PST 2010
[    20.765] (II) Loading extension GLX
[    20.765] (II) LoadModule: "record"
[    20.765] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.786] (II) Module record: vendor="X.Org Foundation"
[    20.786] 	compiled for 1.9.2.901, module version = 1.13.0
[    20.786] 	Module class: X.Org Server Extension
[    20.786] 	ABI class: X.Org Server Extension, version 4.0
[    20.786] (II) Loading extension RECORD
[    20.786] (II) LoadModule: "dri"
[    20.786] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.793] (II) Module dri: vendor="X.Org Foundation"
[    20.793] 	compiled for 1.9.2.901, module version = 1.0.0
[    20.793] 	ABI class: X.Org Server Extension, version 4.0
[    20.793] (II) Loading extension XFree86-DRI
[    20.793] (II) LoadModule: "dri2"
[    20.794] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.802] (II) Module dri2: vendor="X.Org Foundation"
[    20.802] 	compiled for 1.9.2.901, module version = 1.2.0
[    20.802] 	ABI class: X.Org Server Extension, version 4.0
[    20.802] (II) Loading extension DRI2
[    20.802] (==) Matched fglrx as autoconfigured driver 0
[    20.802] (==) Matched ati as autoconfigured driver 1
[    20.802] (==) Matched vesa as autoconfigured driver 2
[    20.802] (==) Matched fbdev as autoconfigured driver 3
[    20.802] (==) Assigned the driver to the xf86ConfigLayout
[    20.802] (II) LoadModule: "fglrx"
[    20.842] (WW) Warning, couldn't open module fglrx
[    20.842] (II) UnloadModule: "fglrx"
[    20.842] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    20.842] (II) LoadModule: "ati"
[    20.843] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    20.868] (II) Module ati: vendor="X.Org Foundation"
[    20.868] 	compiled for 1.9.2.901, module version = 6.13.99
[    20.868] 	Module class: X.Org Video Driver
[    20.868] 	ABI class: X.Org Video Driver, version 8.0
[    20.868] (II) LoadModule: "radeon"
[    20.868] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    20.909] (II) Module radeon: vendor="X.Org Foundation"
[    20.909] 	compiled for 1.9.2.901, module version = 6.13.99
[    20.909] 	Module class: X.Org Video Driver
[    20.909] 	ABI class: X.Org Video Driver, version 8.0
[    20.910] (II) LoadModule: "vesa"
[    20.911] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.920] (II) Module vesa: vendor="X.Org Foundation"
[    20.920] 	compiled for 1.9.2.901, module version = 2.3.0
[    20.920] 	Module class: X.Org Video Driver
[    20.920] 	ABI class: X.Org Video Driver, version 8.0
[    20.920] (II) LoadModule: "fbdev"
[    20.920] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.923] (II) Module fbdev: vendor="X.Org Foundation"
[    20.924] 	compiled for 1.8.99.904, module version = 0.4.2
[    20.924] 	ABI class: X.Org Video Driver, version 8.0
[    20.924] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
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
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
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
	ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS,
	Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS
[    20.946] (II) VESA: driver for VESA chipsets: vesa
[    20.946] (II) FBDEV: driver for framebuffer: fbdev
[    20.946] (++) using VT number 7

[    20.946] (II) [KMS] Kernel modesetting enabled.
[    20.947] (WW) Falling back to old probe method for vesa
[    20.947] (WW) Falling back to old probe method for fbdev
[    20.947] (II) Loading sub module "fbdevhw"
[    20.947] (II) LoadModule: "fbdevhw"
[    20.948] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.036] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.036] 	compiled for 1.9.2.901, module version = 0.0.2
[    21.036] 	ABI class: X.Org Video Driver, version 8.0
[    21.050] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    21.050] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    21.050] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    21.050] (==) RADEON(0): Default visual is TrueColor
[    21.050] (==) RADEON(0): RGB weight 888
[    21.050] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    21.050] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    21.050] (II) RADEON(0): PCI card detected
[    21.051] drmOpenDevice: node name is /dev/dri/card0
[    21.051] drmOpenDevice: open result is 9, (OK)
[    21.051] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    21.051] drmOpenDevice: node name is /dev/dri/card0
[    21.051] drmOpenDevice: open result is 9, (OK)
[    21.051] drmOpenByBusid: drmOpenMinor returns 9
[    21.051] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    21.051] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    21.051] (II) RADEON(0): KMS Color Tiling: enabled
[    21.051] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    21.230] (II) RADEON(0): Output VGA-0 has no monitor section
[    21.230] (II) RADEON(0): Output LVDS has no monitor section
[    21.410] (II) RADEON(0): EDID for output VGA-0
[    21.410] (II) RADEON(0): EDID for output LVDS
[    21.410] (II) RADEON(0): Manufacturer: AUO  Model: 205c  Serial#: 0
[    21.410] (II) RADEON(0): Year: 2008  Week: 1
[    21.410] (II) RADEON(0): EDID Version: 1.3
[    21.410] (II) RADEON(0): Digital Display Input
[    21.410] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 14
[    21.410] (II) RADEON(0): Gamma: 2.20
[    21.410] (II) RADEON(0): No DPMS capabilities specified
[    21.410] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    21.410] (II) RADEON(0): First detailed timing is preferred mode
[    21.410] (II) RADEON(0): redX: 0.584 redY: 0.333   greenX: 0.338 greenY: 0.571
[    21.410] (II) RADEON(0): blueX: 0.158 blueY: 0.133   whiteX: 0.313 whiteY: 0.329
[    21.410] (II) RADEON(0): Manufacturer's mask: 0
[    21.410] (II) RADEON(0): Supported detailed timing:
[    21.410] (II) RADEON(0): clock: 72.0 MHz   Image Size:  256 x 144 mm
[    21.411] (II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1494 h_border: 0
[    21.411] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    21.411] (II) RADEON(0): Unknown vendor-specific block f
[    21.411] (II) RADEON(0):  AUO
[    21.411] (II) RADEON(0):  B116XW02 V0
[    21.411] (II) RADEON(0): EDID (in hex):
[    21.411] (II) RADEON(0): 	00ffffffffffff0006af5c2000000000
[    21.411] (II) RADEON(0): 	01120103801a0e780a99859555569228
[    21.411] (II) RADEON(0): 	22505400000001010101010101010101
[    21.411] (II) RADEON(0): 	010101010101201c5680500023303020
[    21.411] (II) RADEON(0): 	36000090100000180000000f00000000
[    21.411] (II) RADEON(0): 	00000000000000000020000000fe0041
[    21.411] (II) RADEON(0): 	554f0a202020202020202020000000fe
[    21.411] (II) RADEON(0): 	004231313658573032205630200a00be
[    21.411] (II) RADEON(0): Printing probed modes for output LVDS
[    21.411] (II) RADEON(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    21.411] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    21.411] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    21.411] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    21.411] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    21.411] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    21.412] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    21.412] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    21.412] (II) RADEON(0): Output VGA-0 disconnected
[    21.412] (II) RADEON(0): Output LVDS connected
[    21.412] (II) RADEON(0): Using exact sizes for initial modes
[    21.412] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    21.412] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    21.412] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:18000000 visible:17ba0000
[    21.412] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    21.412] (==) RADEON(0): DPI set to (96, 96)
[    21.412] (II) Loading sub module "fb"
[    21.412] (II) LoadModule: "fb"
[    21.413] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.607] (II) Module fb: vendor="X.Org Foundation"
[    21.607] 	compiled for 1.9.2.901, module version = 1.0.0
[    21.607] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.607] (II) Loading sub module "ramdac"
[    21.607] (II) LoadModule: "ramdac"
[    21.607] (II) Module "ramdac" already built-in
[    21.607] (II) Loading sub module "exa"
[    21.607] (II) LoadModule: "exa"
[    21.608] (II) Loading /usr/lib/xorg/modules/libexa.so
[    21.609] (II) Module exa: vendor="X.Org Foundation"
[    21.609] 	compiled for 1.9.2.901, module version = 2.5.0
[    21.610] 	ABI class: X.Org Video Driver, version 8.0
[    21.610] (II) UnloadModule: "vesa"
[    21.610] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.610] (II) UnloadModule: "fbdev"
[    21.610] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.610] (II) UnloadModule: "fbdevhw"
[    21.610] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    21.610] (--) Depth 24 pixmap format is 32 bpp
[    21.610] (II) RADEON(0): [DRI2] Setup complete
[    21.610] (II) RADEON(0): [DRI2]   DRI driver: r300
[    21.611] (II) RADEON(0): Front buffer size: 4224K
[    21.611] (II) RADEON(0): VRAM usage limit set to 346060K
[    22.010] (==) RADEON(0): Backing store disabled
[    22.010] (II) RADEON(0): Direct rendering enabled
[    22.026] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    22.026] (II) RADEON(0): Setting EXA maxPitchBytes
[    22.026] (II) EXA(0): Driver allocated offscreen pixmaps
[    22.026] (II) EXA(0): Driver registered support for the following operations:
[    22.026] (II)         Solid
[    22.026] (II)         Copy
[    22.026] (II)         Composite (RENDER acceleration)
[    22.026] (II)         UploadToScreen
[    22.026] (II)         DownloadFromScreen
[    22.026] (II) RADEON(0): Acceleration enabled
[    22.027] (==) RADEON(0): DPMS enabled
[    22.027] (==) RADEON(0): Silken mouse enabled
[    22.034] (II) RADEON(0): Set up textured video
[    22.034] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.053] (--) RandR disabled
[    22.053] (II) Initializing built-in extension Generic Event Extension
[    22.053] (II) Initializing built-in extension SHAPE
[    22.053] (II) Initializing built-in extension MIT-SHM
[    22.053] (II) Initializing built-in extension XInputExtension
[    22.053] (II) Initializing built-in extension XTEST
[    22.053] (II) Initializing built-in extension BIG-REQUESTS
[    22.053] (II) Initializing built-in extension SYNC
[    22.053] (II) Initializing built-in extension XKEYBOARD
[    22.053] (II) Initializing built-in extension XC-MISC
[    22.053] (II) Initializing built-in extension SECURITY
[    22.053] (II) Initializing built-in extension XINERAMA
[    22.053] (II) Initializing built-in extension XFIXES
[    22.053] (II) Initializing built-in extension RENDER
[    22.054] (II) Initializing built-in extension RANDR
[    22.054] (II) Initializing built-in extension COMPOSITE
[    22.054] (II) Initializing built-in extension DAMAGE
[    22.054] (II) Initializing built-in extension GESTURE
[    22.072] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    22.086] (II) RADEON(0): Setting screen physical size to 361 x 203
[    22.383] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.435] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    22.435] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.435] (II) LoadModule: "evdev"
[    22.436] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.454] (II) Module evdev: vendor="X.Org Foundation"
[    22.454] 	compiled for 1.9.2.901, module version = 2.5.99
[    22.454] 	Module class: X.Org XInput Driver
[    22.454] 	ABI class: X.Org XInput driver, version 11.0
[    22.454] (**) Power Button: always reports core events
[    22.454] (**) Power Button: Device: "/dev/input/event3"
[    22.454] (--) Power Button: Found keys
[    22.454] (II) Power Button: Configuring as keyboard
[    22.455] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.455] (**) Option "xkb_rules" "evdev"
[    22.455] (**) Option "xkb_model" "pc105"
[    22.455] (**) Option "xkb_layout" "us"
[    22.458] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    22.458] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.458] (**) Video Bus: always reports core events
[    22.458] (**) Video Bus: Device: "/dev/input/event6"
[    22.459] (--) Video Bus: Found keys
[    22.459] (II) Video Bus: Configuring as keyboard
[    22.459] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    22.459] (**) Option "xkb_rules" "evdev"
[    22.459] (**) Option "xkb_model" "pc105"
[    22.459] (**) Option "xkb_layout" "us"
[    22.460] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    22.460] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.460] (**) Power Button: always reports core events
[    22.460] (**) Power Button: Device: "/dev/input/event2"
[    22.460] (--) Power Button: Found keys
[    22.460] (II) Power Button: Configuring as keyboard
[    22.460] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.460] (**) Option "xkb_rules" "evdev"
[    22.460] (**) Option "xkb_model" "pc105"
[    22.460] (**) Option "xkb_layout" "us"
[    22.461] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    22.461] (II) No input driver/identifier specified (ignoring)
[    22.462] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    22.462] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    22.462] (**) Sleep Button: always reports core events
[    22.462] (**) Sleep Button: Device: "/dev/input/event1"
[    22.462] (--) Sleep Button: Found keys
[    22.462] (II) Sleep Button: Configuring as keyboard
[    22.462] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    22.462] (**) Option "xkb_rules" "evdev"
[    22.462] (**) Option "xkb_model" "pc105"
[    22.462] (**) Option "xkb_layout" "us"
[    22.468] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/event5)
[    22.468] (**) PIXART USB OPTICAL MOUSE: Applying InputClass "evdev pointer catchall"
[    22.468] (**) PIXART USB OPTICAL MOUSE: always reports core events
[    22.468] (**) PIXART USB OPTICAL MOUSE: Device: "/dev/input/event5"
[    22.469] (--) PIXART USB OPTICAL MOUSE: Found 3 mouse buttons
[    22.469] (--) PIXART USB OPTICAL MOUSE: Found scroll wheel(s)
[    22.469] (--) PIXART USB OPTICAL MOUSE: Found relative axes
[    22.469] (--) PIXART USB OPTICAL MOUSE: Found x and y relative axes
[    22.469] (II) PIXART USB OPTICAL MOUSE: Configuring as mouse
[    22.469] (II) PIXART USB OPTICAL MOUSE: Adding scrollwheel support
[    22.469] (**) PIXART USB OPTICAL MOUSE: YAxisMapping: buttons 4 and 5
[    22.469] (**) PIXART USB OPTICAL MOUSE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.469] (II) XINPUT: Adding extended input device "PIXART USB OPTICAL MOUSE" (type: MOUSE)
[    22.469] (**) PIXART USB OPTICAL MOUSE: (accel) keeping acceleration scheme 1
[    22.469] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration profile 0
[    22.469] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration factor: 2.000
[    22.469] (**) PIXART USB OPTICAL MOUSE: (accel) acceleration threshold: 4
[    22.469] (II) PIXART USB OPTICAL MOUSE: initialized for relative axes.
[    22.470] (II) config/udev: Adding input device PIXART USB OPTICAL MOUSE (/dev/input/mouse0)
[    22.470] (II) No input driver/identifier specified (ignoring)
[    22.472] (II) config/udev: Adding input device CNF9011 (/dev/input/event7)
[    22.473] (**) CNF9011: Applying InputClass "evdev keyboard catchall"
[    22.473] (**) CNF9011: always reports core events
[    22.473] (**) CNF9011: Device: "/dev/input/event7"
[    22.473] (--) CNF9011: Found keys
[    22.473] (II) CNF9011: Configuring as keyboard
[    22.473] (II) XINPUT: Adding extended input device "CNF9011" (type: KEYBOARD)
[    22.473] (**) Option "xkb_rules" "evdev"
[    22.473] (**) Option "xkb_model" "pc105"
[    22.473] (**) Option "xkb_layout" "us"
[    22.477] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    22.477] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.477] (**) AT Translated Set 2 keyboard: always reports core events
[    22.477] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    22.477] (--) AT Translated Set 2 keyboard: Found keys
[    22.477] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.477] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.477] (**) Option "xkb_rules" "evdev"
[    22.477] (**) Option "xkb_model" "pc105"
[    22.477] (**) Option "xkb_layout" "us"
[    22.478] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    22.478] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.478] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.478] (II) LoadModule: "synaptics"
[    22.479] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.498] (II) Module synaptics: vendor="X.Org Foundation"
[    22.498] 	compiled for 1.8.99.904, module version = 1.2.99
[    22.499] 	Module class: X.Org XInput Driver
[    22.499] 	ABI class: X.Org XInput driver, version 11.0
[    22.499] (II) Synaptics touchpad driver version 1.2.99
[    22.499] (**) Option "Device" "/dev/input/event8"
[    22.499] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[    22.499] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5012
[    22.499] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.499] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    22.499] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    22.499] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.499] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.499] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    22.499] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.499] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    22.499] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.499] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.500] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    22.501] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    22.501] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.501] (II) Synaptics touchpad driver version 1.2.99
[    22.501] (EE) SynPS/2 Synaptics TouchPad no synaptics event device found
[    22.501] (**) Option "Device" "/dev/input/mouse1"
[    22.522] (EE) Query no Synaptics: 6003C8
[    22.522] (--) SynPS/2 Synaptics TouchPad: no supported touchpad found
[    22.522] (EE) SynPS/2 Synaptics TouchPad Unable to query/initialize Synaptics hardware.
[    22.523] (EE) PreInit failed for input device "SynPS/2 Synaptics TouchPad"
[    22.523] (II) UnloadModule: "synaptics"
[    24.940] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    24.940] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.940] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.120] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    25.120] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.120] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.320] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    25.320] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.320] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.500] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    25.500] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.500] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    42.620] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    42.620] (II) RADEON(0): Printing DDC gathered Modelines:
[    42.620] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    42.800] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    42.800] (II) RADEON(0): Printing DDC gathered Modelines:
[    42.800] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    43.070] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    43.070] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.070] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    43.250] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    43.250] (II) RADEON(0): Printing DDC gathered Modelines:
[    43.250] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    49.722] (II) RADEON(0): EDID vendor "AUO", prod id 8284
[    49.722] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.722] (II) RADEON(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
```

---

### Post by Yellow Pasque on 2011-01-21
From your xorg log, it looks like you have tried to install both the ATI and Nvidia proprietary driver. You need to purge those out and start with a fresh xorg.conf before you'll get working 3D.

---

### Post by Joe Awsome on 2011-01-22
Not to be a noob here, but how do I reset my xorg.conf and purge the specific drivers from my system with out getting rid of the edgers ppa? should I keep the edgers and stable ppa's or get rid of them? could you put the instructions to be used in the terminal. Sorry about this whole thing, but i'm a noob when it comes to linux graphics, so i'm gona need to be spoon fed on this one.

---

### Post by Joe Awsome on 2011-01-22
nevermind about those instructions temujin. I did an accidental full reinstall by trying to redo by dual boot ubuntu setup. turns out my hard drive got wiped while trying to recover my files. Anyways, my graphics card is fully recognized and working with desktop effects. I do have the problem that imsael was having with the blurry screen happening on some webpages. I can work around that by hitting the windows key and E at the same time. If anyone has a solution for the problem I originally posted on without having to reinstall ubuntu on a chance fix, just post it. I'm sure others besides me will apreciate being able to fix the problem without losing all thier personal data or having to back it up. Joe awsome, over and out. 8)

---

### Post by twade on 2011-01-25
I have the mobile ati x1250 video card and was getting crappy video after an upgrade to 10.10 (Maverick Meerkat).  It looks like something got broken in the new xserver-xorg-video-ati driver.  Downgrading the driver to an older version seems to be working for me at the moment.  
[http://wwww.ubuntuforums.org/showthread.php?t=1593410&highlight=glxinfo+ati+sgi+mesa&page=2](http://wwww.ubuntuforums.org/showthread.php?t=1593410&highlight=glxinfo+ati+sgi+mesa&page=2)

With the 10.10 version of xserver-xorg-video-ati glxgears gave a frame rate of ~50, and I couldn't enable desktop effects.  After downgrading the driver, glxgears was close to 200, and desktop effects work again.

A bug report should probably be filed, but I don't have the time now.  

Good Luck!

---

### Post by Savore on 2011-01-26
Huge thanks to tjones00
That command allowed me to enjoy Ubuntu without any of those nasty garbled images I was getting.
I'm running a Gateway lt3119u with the olde' X1270 card in it. 
  
I think I can wait for the devs to publish some nice 3D support now that 2D works for me. (Once again thanks to tjones00)

The reason I'm here though is to post my log file after tjones00's tweaks.
(Didn't think to copy it before the tweaks...)

Maybe this will be helpful to others. ;)

[PHP][    14.144] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    14.144] X Protocol Version 11, Revision 0
[    14.145] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    14.145] Current Operating System: Linux LT31 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    14.145] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=0f2df575-2aac-4c1d-9522-8e8239c0052c ro nomodeset
[    14.145] Build Date: 09 January 2011  12:14:27PM
[    14.145] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    14.145] Current version of pixman: 0.18.4
[    14.145]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.145] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.145] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 25 21:06:22 2011
[    14.162] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.163] (==) No Layout section.  Using the first Screen section.
[    14.163] (==) No screen section available. Using defaults.
[    14.163] (**) |-->Screen "Default Screen Section" (0)
[    14.163] (**) |   |-->Monitor "<default monitor>"
[    14.164] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.164] (==) Automatically adding devices
[    14.164] (==) Automatically enabling devices
[    14.164] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.164]     Entry deleted from font path.
[    14.164] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.164] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.164] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.164] (II) Loader magic: 0x7d17a0
[    14.164] (II) Module ABI versions:
[    14.164]     X.Org ANSI C Emulation: 0.4
[    14.164]     X.Org Video Driver: 8.0
[    14.164]     X.Org XInput driver : 11.0
[    14.164]     X.Org Server Extension : 4.0
[    14.166] (--) PCI:*(0:1:5:0) 1002:791f:1025:028c rev 0, Mem @ 0xd0000000/268435456, 0xf0100000/65536, 0xf0000000/1048576, I/O @ 0x00009000/256
[    14.166] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.166] (II) LoadModule: "extmod"
[    14.178] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.178] (II) Module extmod: vendor="X.Org Foundation"
[    14.178]     compiled for 1.9.0, module version = 1.0.0
[    14.178]     Module class: X.Org Server Extension
[    14.178]     ABI class: X.Org Server Extension, version 4.0
[    14.178] (II) Loading extension MIT-SCREEN-SAVER
[    14.178] (II) Loading extension XFree86-VidModeExtension
[    14.178] (II) Loading extension XFree86-DGA
[    14.178] (II) Loading extension DPMS
[    14.178] (II) Loading extension XVideo
[    14.178] (II) Loading extension XVideo-MotionCompensation
[    14.178] (II) Loading extension X-Resource
[    14.178] (II) LoadModule: "dbe"
[    14.179] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.179] (II) Module dbe: vendor="X.Org Foundation"
[    14.179]     compiled for 1.9.0, module version = 1.0.0
[    14.179]     Module class: X.Org Server Extension
[    14.179]     ABI class: X.Org Server Extension, version 4.0
[    14.179] (II) Loading extension DOUBLE-BUFFER
[    14.179] (II) LoadModule: "glx"
[    14.179] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.180] (II) Module glx: vendor="X.Org Foundation"
[    14.180]     compiled for 1.9.0, module version = 1.0.0
[    14.180]     ABI class: X.Org Server Extension, version 4.0
[    14.180] (==) AIGLX enabled
[    14.180] (II) Loading extension GLX
[    14.180] (II) LoadModule: "record"
[    14.180] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.180] (II) Module record: vendor="X.Org Foundation"
[    14.180]     compiled for 1.9.0, module version = 1.13.0
[    14.180]     Module class: X.Org Server Extension
[    14.180]     ABI class: X.Org Server Extension, version 4.0
[    14.180] (II) Loading extension RECORD
[    14.180] (II) LoadModule: "dri"
[    14.181] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.181] (II) Module dri: vendor="X.Org Foundation"
[    14.181]     compiled for 1.9.0, module version = 1.0.0
[    14.181]     ABI class: X.Org Server Extension, version 4.0
[    14.181] (II) Loading extension XFree86-DRI
[    14.181] (II) LoadModule: "dri2"
[    14.182] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.182] (II) Module dri2: vendor="X.Org Foundation"
[    14.182]     compiled for 1.9.0, module version = 1.2.0
[    14.182]     ABI class: X.Org Server Extension, version 4.0
[    14.182] (II) Loading extension DRI2
[    14.182] (==) Matched ati as autoconfigured driver 0
[    14.182] (==) Matched vesa as autoconfigured driver 1
[    14.182] (==) Matched fbdev as autoconfigured driver 2
[    14.182] (==) Assigned the driver to the xf86ConfigLayout
[    14.182] (II) LoadModule: "ati"
[    14.183] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    14.183] (II) Module ati: vendor="X.Org Foundation"
[    14.183]     compiled for 1.9.0, module version = 6.13.1
[    14.184]     Module class: X.Org Video Driver
[    14.184]     ABI class: X.Org Video Driver, version 8.0
[    14.184] (II) LoadModule: "radeon"
[    14.184] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.185] (II) Module radeon: vendor="X.Org Foundation"
[    14.185]     compiled for 1.9.0, module version = 6.13.1
[    14.185]     Module class: X.Org Video Driver
[    14.185]     ABI class: X.Org Video Driver, version 8.0
[    14.185] (II) LoadModule: "vesa"
[    14.186] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.186] (II) Module vesa: vendor="X.Org Foundation"
[    14.186]     compiled for 1.8.99.905, module version = 2.3.0
[    14.186]     Module class: X.Org Video Driver
[    14.186]     ABI class: X.Org Video Driver, version 8.0
[    14.186] (II) LoadModule: "fbdev"
[    14.187] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.187] (II) Module fbdev: vendor="X.Org Foundation"
[    14.187]     compiled for 1.8.99.905, module version = 0.4.2
[    14.187]     ABI class: X.Org Video Driver, version 8.0
[    14.187] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
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
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
    CEDAR
[    14.203] (II) VESA: driver for VESA chipsets: vesa
[    14.203] (II) FBDEV: driver for framebuffer: fbdev
[    14.203] (++) using VT number 7

[    14.204] (II) [KMS] drm report modesetting isn't supported.
[    14.204] (WW) Falling back to old probe method for vesa
[    14.204] (WW) Falling back to old probe method for fbdev
[    14.204] (II) Loading sub module "fbdevhw"
[    14.204] (II) LoadModule: "fbdevhw"
[    14.205] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.205] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.205]     compiled for 1.9.0, module version = 0.0.2
[    14.205]     ABI class: X.Org Video Driver, version 8.0
[    14.205] (EE) open /dev/fb0: No such file or directory
[    14.205] (II) RADEON(0): TOTO SAYS 00000000f0100000
[    14.205] (II) RADEON(0): MMIO registers at 0x00000000f0100000: size 64KB
[    14.206] (II) RADEON(0): PCI bus 1 card 5 func 0
[    14.206] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.206] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    14.206] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.206] (==) RADEON(0): Default visual is TrueColor
[    14.206] (II) Loading sub module "vgahw"
[    14.206] (II) LoadModule: "vgahw"
[    14.206] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    14.255] (II) Module vgahw: vendor="X.Org Foundation"
[    14.255]     compiled for 1.9.0, module version = 0.1.0
[    14.256]     ABI class: X.Org Video Driver, version 8.0
[    14.256] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    14.256] (==) RADEON(0): RGB weight 888
[    14.256] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    14.256] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x791f)
[    14.256] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[    14.256] (II) RADEON(0): PCI card detected
[    14.256] (II) Loading sub module "int10"
[    14.256] (II) LoadModule: "int10"
[    14.257] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.265] (II) Module int10: vendor="X.Org Foundation"
[    14.265]     compiled for 1.9.0, module version = 1.0.0
[    14.265]     ABI class: X.Org Video Driver, version 8.0
[    14.265] (II) RADEON(0): initializing int10
[    14.266] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    14.269] (II) RADEON(0): ATOM BIOS detected
[    14.269] (II) RADEON(0): ATOM BIOS Rom: 
[    14.269]     SubsystemVendorID: 0x1025 SubsystemID: 0x028c
[    14.269]     IOBaseAddress: 0x9000
[    14.269]     Filename: BR33431.bin 
[    14.269]     BIOS Bootup Message:  
ATI Radeon Xpress for SJM11-YK                                               

[    14.269] (II) RADEON(0): Framebuffer space used by Firmware (kb): 16
[    14.269] (II) RADEON(0): Start of VRAM area used by Firmware: 0x17ffc000
[    14.269] (II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space
[    14.269] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x17ffc000
[    14.269] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    14.269] (II) RADEON(0): Default Engine Clock: 300000
[    14.269] (II) RADEON(0): Default Memory Clock: 333000
[    14.269] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    14.269] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    14.269] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    14.269] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    14.269] (II) RADEON(0): Maximum Pixel Clock: 400000
[    14.269] (II) RADEON(0): Reference Clock: 14320
[    14.270] drmOpenDevice: node name is /dev/dri/card0
[    14.270] drmOpenDevice: open result is 11, (OK)
[    14.271] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    14.271] drmOpenDevice: node name is /dev/dri/card0
[    14.271] drmOpenDevice: open result is 11, (OK)
[    14.271] drmOpenByBusid: drmOpenMinor returns 11
[    14.271] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    14.272] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.33.0
[    14.272] (==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

[    14.272] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    14.272] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    14.272] (II) RADEON(0): Detected total video RAM=393216K, accessible=262144K (PCI BAR=262144K)
[    14.272] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    14.272] (II) RADEON(0): Color tiling enabled by default
[    14.272] (II) Loading sub module "ddc"
[    14.272] (II) LoadModule: "ddc"
[    14.272] (II) Module "ddc" already built-in
[    14.273] (II) Loading sub module "i2c"
[    14.273] (II) LoadModule: "i2c"
[    14.273] (II) Module "i2c" already built-in
[    14.273] (II) RADEON(0): PLL parameters: rf=1432 rd=12 min=80000 max=120000; xclk=40000
[    14.273] (WW) RADEON(0): LVDS Info:
XRes: 1366, YRes: 768, DotClock: 65560
HBlank: 42, HOverPlus: 7, HSyncWidth: 14
VBlank: 8, VOverPlus: 1, VSyncWidth: 3
[    14.273] (II) RADEON(0): Output VGA-0 has no monitor section
[    14.273] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    14.273] (II) RADEON(0): Output LVDS has no monitor section
[    14.273] (II) RADEON(0): I2C bus "LVDS" initialized.
[    14.273] (II) RADEON(0): Port0:
[    14.273]   XRANDR name: VGA-0
[    14.273]   Connector: VGA
[    14.273]   CRT1: INTERNAL_KLDSCP_DAC1
[    14.273]   DDC reg: 0x7e50
[    14.273] (II) RADEON(0): Port1:
[    14.273]   XRANDR name: LVDS
[    14.273]   Connector: LVDS
[    14.273]   LCD1: INTERNAL_LVTM1
[    14.273]   DDC reg: 0x7e40
[    14.273] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    14.341] Dac detection success
[    14.341] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    14.341] finished output detect: 0
[    14.341] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    14.400] (II) RADEON(0): EDID for output LVDS
[    14.400] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    14.400] (II) RADEON(0): Year: 2009  Week: 9
[    14.400] (II) RADEON(0): EDID Version: 1.3
[    14.400] (II) RADEON(0): Digital Display Input
[    14.400] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    14.400] (II) RADEON(0): Gamma: 2.20
[    14.400] (II) RADEON(0): No DPMS capabilities specified
[    14.401] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.401] (II) RADEON(0): First detailed timing is preferred mode
[    14.401] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    14.401] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    14.401] (II) RADEON(0): Manufacturer's mask: 0
[    14.401] (II) RADEON(0): Supported detailed timing:
[    14.401] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    14.401] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    14.401] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    14.401] (II) RADEON(0):  N116B6-L02
[    14.401] (II) RADEON(0):  CMO
[    14.401] (II) RADEON(0):  N116B6-L02
[    14.401] (II) RADEON(0): EDID (in hex):
[    14.401] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    14.401] (II) RADEON(0):     0913010380190e780acf459059579529
[    14.401] (II) RADEON(0):     1f505400000001010101010101010101
[    14.401] (II) RADEON(0):     0101010101019c19562a50000830070e
[    14.401] (II) RADEON(0):     1300009010000018000000fe004e3131
[    14.401] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    14.401] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    14.401] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    14.401] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    14.401] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    14.401] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    14.401] (II) RADEON(0): Year: 2009  Week: 9
[    14.401] (II) RADEON(0): EDID Version: 1.3
[    14.401] (II) RADEON(0): Digital Display Input
[    14.401] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    14.401] (II) RADEON(0): Gamma: 2.20
[    14.401] (II) RADEON(0): No DPMS capabilities specified
[    14.402] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.402] (II) RADEON(0): First detailed timing is preferred mode
[    14.402] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    14.402] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    14.402] (II) RADEON(0): Manufacturer's mask: 0
[    14.402] (II) RADEON(0): Supported detailed timing:
[    14.402] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    14.402] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    14.402] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    14.402] (II) RADEON(0):  N116B6-L02
[    14.402] (II) RADEON(0):  CMO
[    14.402] (II) RADEON(0):  N116B6-L02
[    14.402] (II) RADEON(0): EDID (in hex):
[    14.402] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    14.402] (II) RADEON(0):     0913010380190e780acf459059579529
[    14.402] (II) RADEON(0):     1f505400000001010101010101010101
[    14.402] (II) RADEON(0):     0101010101019c19562a50000830070e
[    14.402] (II) RADEON(0):     1300009010000018000000fe004e3131
[    14.402] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    14.402] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    14.402] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    14.402] finished output detect: 1
[    14.402] finished all detect
[    14.470] Dac detection success
[    14.470] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    14.470] (II) RADEON(0): EDID for output VGA-0
[    14.529] (II) RADEON(0): EDID for output LVDS
[    14.529] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    14.529] (II) RADEON(0): Year: 2009  Week: 9
[    14.529] (II) RADEON(0): EDID Version: 1.3
[    14.530] (II) RADEON(0): Digital Display Input
[    14.530] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    14.530] (II) RADEON(0): Gamma: 2.20
[    14.530] (II) RADEON(0): No DPMS capabilities specified
[    14.530] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.530] (II) RADEON(0): First detailed timing is preferred mode
[    14.530] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    14.530] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    14.530] (II) RADEON(0): Manufacturer's mask: 0
[    14.530] (II) RADEON(0): Supported detailed timing:
[    14.530] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    14.530] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    14.530] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    14.530] (II) RADEON(0):  N116B6-L02
[    14.530] (II) RADEON(0):  CMO
[    14.530] (II) RADEON(0):  N116B6-L02
[    14.530] (II) RADEON(0): EDID (in hex):
[    14.530] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    14.530] (II) RADEON(0):     0913010380190e780acf459059579529
[    14.530] (II) RADEON(0):     1f505400000001010101010101010101
[    14.530] (II) RADEON(0):     0101010101019c19562a50000830070e
[    14.530] (II) RADEON(0):     1300009010000018000000fe004e3131
[    14.530] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    14.530] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    14.530] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    14.530] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    14.530] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    14.530] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    14.530] (II) RADEON(0): Year: 2009  Week: 9
[    14.531] (II) RADEON(0): EDID Version: 1.3
[    14.531] (II) RADEON(0): Digital Display Input
[    14.531] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    14.531] (II) RADEON(0): Gamma: 2.20
[    14.531] (II) RADEON(0): No DPMS capabilities specified
[    14.531] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.531] (II) RADEON(0): First detailed timing is preferred mode
[    14.531] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    14.531] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    14.531] (II) RADEON(0): Manufacturer's mask: 0
[    14.531] (II) RADEON(0): Supported detailed timing:
[    14.531] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    14.531] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    14.531] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    14.531] (II) RADEON(0):  N116B6-L02
[    14.531] (II) RADEON(0):  CMO
[    14.531] (II) RADEON(0):  N116B6-L02
[    14.531] (II) RADEON(0): EDID (in hex):
[    14.531] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    14.531] (II) RADEON(0):     0913010380190e780acf459059579529
[    14.531] (II) RADEON(0):     1f505400000001010101010101010101
[    14.531] (II) RADEON(0):     0101010101019c19562a50000830070e
[    14.531] (II) RADEON(0):     1300009010000018000000fe004e3131
[    14.531] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    14.531] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    14.531] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    14.531] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    14.531] (II) RADEON(0): Printing probed modes for output LVDS
[    14.531] (II) RADEON(0): Modeline "1366x768"x60.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    14.531] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    14.532] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    14.532] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    14.532] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    14.532] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    14.532] (II) RADEON(0): Output VGA-0 disconnected
[    14.532] (II) RADEON(0): Output LVDS connected
[    14.532] (II) RADEON(0): Using exact sizes for initial modes
[    14.532] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    14.532] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.532] (==) RADEON(0): DPI set to (96, 96)
[    14.532] (II) Loading sub module "fb"
[    14.532] (II) LoadModule: "fb"
[    14.533] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.533] (II) Module fb: vendor="X.Org Foundation"
[    14.533]     compiled for 1.9.0, module version = 1.0.0
[    14.533]     ABI class: X.Org ANSI C Emulation, version 0.4
[    14.533] (II) Loading sub module "ramdac"
[    14.533] (II) LoadModule: "ramdac"
[    14.533] (II) Module "ramdac" already built-in
[    14.533] (==) RADEON(0): Using EXA acceleration architecture
[    14.533] (II) Loading sub module "exa"
[    14.533] (II) LoadModule: "exa"
[    14.534] (II) Loading /usr/lib/xorg/modules/libexa.so
[    14.534] (II) Module exa: vendor="X.Org Foundation"
[    14.534]     compiled for 1.9.0, module version = 2.5.0
[    14.534]     ABI class: X.Org Video Driver, version 8.0
[    14.535] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    14.535] (II) UnloadModule: "vesa"
[    14.535] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.535] (II) UnloadModule: "fbdev"
[    14.535] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.535] (II) UnloadModule: "fbdevhw"
[    14.535] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    14.535] (--) Depth 24 pixmap format is 32 bpp
[    14.535] (II) RADEON(0): RADEONScreenInit d0000000 0 0
[    14.909] Output LCD1 disable success
[    14.912] Blank CRTC 0 success
[    14.912] Disable CRTC 0 success
[    14.912] Blank CRTC 1 success
[    14.912] Disable CRTC 1 success
[    14.912] (II) RADEON(0): Dynamic Power Management Disabled
[    14.912] (==) RADEON(0): Using 24 bit depth buffer
[    14.912] (II) RADEON(0): RADEONInitMemoryMap() : 
[    14.913] (II) RADEON(0):   mem_size         : 0x18000000
[    14.913] (II) RADEON(0):   MC_FB_LOCATION   : 0x7fff6800
[    14.913] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    14.913] (II) RADEON(0): Depth moves disabled by default
[    14.913] (II) RADEON(0): Allocating from a screen of 262144 kb
[    14.913] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00764000
[    14.913] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00768000
[    14.913] (II) RADEON(0): Will use 7568 kb for front buffer at offset 0x00000000
[    14.913] (II) RADEON(0): Will use 7568 kb for back buffer at offset 0x0076c000
[    14.913] (II) RADEON(0): Will use 7568 kb for depth buffer at offset 0x00ed0000
[    14.913] (II) RADEON(0): Will use 118784 kb for textures at offset 0x01634000
[    14.913] (II) RADEON(0): Will use 120624 kb for X Server offscreen at offset 0x08a34000
[    14.913] drmOpenDevice: node name is /dev/dri/card0
[    14.913] drmOpenDevice: open result is 11, (OK)
[    14.914] drmOpenDevice: node name is /dev/dri/card0
[    14.915] drmOpenDevice: open result is 11, (OK)
[    14.915] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    14.915] drmOpenDevice: node name is /dev/dri/card0
[    14.915] drmOpenDevice: open result is 11, (OK)
[    14.916] drmOpenByBusid: drmOpenMinor returns 11
[    14.916] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    14.916] (II) [drm] DRM interface version 1.3
[    14.916] (II) [drm] DRM open master succeeded.
[    14.916] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    14.916] (II) RADEON(0): [drm] framebuffer handle = 0xd0000000
[    14.916] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    14.916] (II) RADEON(0): X context handle = 0x1
[    14.916] (II) RADEON(0): [drm] installed DRM signal handler
[    14.945] (II) RADEON(0): [pci] 32768 kB allocated with handle 0x01d90900
[    14.945] (II) RADEON(0): [pci] ring handle = 0x2b800000
[    14.945] (II) RADEON(0): [pci] Ring mapped at 0x7f2f9d2da000
[    14.945] (II) RADEON(0): [pci] Ring contents 0x00000000
[    14.945] (II) RADEON(0): [pci] ring read ptr handle = 0x1b7ff000
[    14.945] (II) RADEON(0): [pci] Ring read ptr mapped at 0x7f2f9d2d9000
[    14.945] (II) RADEON(0): [pci] Ring read ptr contents 0x00000000
[    14.945] (II) RADEON(0): [pci] vertex/indirect buffers handle = 0x2b801000
[    14.945] (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0x7f2f8837d000
[    14.946] (II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
[    14.946] (II) RADEON(0): [pci] GART texture map handle = 0x2b802000
[    14.946] (II) RADEON(0): [pci] GART Texture map mapped at 0x7f2f866fd000
[    14.946] (II) RADEON(0): [drm] register handle = 0x2fff8000
[    14.946] (II) RADEON(0): [dri] Visual configs initialized
[    14.946] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    14.946] (II) RADEON(0):   MC_FB_LOCATION   : 0x7fff6800 0x7fff6800
[    14.946] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    14.946] (==) RADEON(0): Backing store disabled
[    14.946] (II) RADEON(0): [DRI] installation complete
[    15.081] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    15.081] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    15.081] (II) RADEON(0): [drm] dma control initialized, using IRQ 18
[    15.081] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
[    15.081] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    15.081] (WW) RADEON(0):   MC_FB_LOCATION  was: 0x7fff6800 is: 0x7fff6800
[    15.081] (WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x81ff8000
[    15.081] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    15.081] (II) RADEON(0):   MC_FB_LOCATION   : 0x7fff6800 0x7fff6800
[    15.081] (II) RADEON(0):   MC_AGP_LOCATION  : 0x81ff8000
[    15.081] (II) RADEON(0): Direct rendering enabled
[    15.081] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    15.081] (II) RADEON(0): Setting EXA maxPitchBytes
[    15.081] (II) RADEON(0): num quad-pipes is 1
[    15.081] (II) EXA(0): Offscreen pixmap area of 123518976 bytes
[    15.081] (II) EXA(0): Driver registered support for the following operations:
[    15.081] (II)         Solid
[    15.081] (II)         Copy
[    15.081] (II)         Composite (RENDER acceleration)
[    15.081] (II)         UploadToScreen
[    15.082] (II)         DownloadFromScreen
[    15.082] (II) RADEON(0): Acceleration enabled
[    15.082] (==) RADEON(0): DPMS enabled
[    15.082] (==) RADEON(0): Silken mouse enabled
[    15.082] (II) RADEON(0): Set up textured video
[    15.102] Output CRT1 disable success
[    15.102] Output LCD1 disable success
[    15.102] Blank CRTC 0 success
[    15.102] Disable CRTC 0 success
[    15.102] Blank CRTC 1 success
[    15.102] Disable CRTC 1 success
[    15.102] Output LCD1 disable success
[    15.102] Blank CRTC 0 success
[    15.102] Disable CRTC 0 success
[    15.102] Mode 1366x768 - 1408 776 10
[    15.102] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    15.102] (II) RADEON(0):   MC_FB_LOCATION   : 0x7fff6800 0x7fff6800
[    15.102] (II) RADEON(0):   MC_AGP_LOCATION  : 0x81ff8000
[    15.103] Picked PLL 0
[    15.103] best_freq: 65633
[    15.103] best_feedback_div: 165
[    15.103] best_frac_feedback_div: 0
[    15.103] best_ref_div: 2
[    15.103] best_post_div: 18
[    15.103] (II) RADEON(0): crtc(0) Clock: mode 65560, PLL 656330
[    15.103] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0xA5(165), fracfbdiv 0, pdiv 18
[    15.105] Set CRTC 0 PLL success
[    15.105] Set CRTC Timing success
[    15.105] Set CRTC 0 Overscan success
[    15.105] Not using RMX
[    15.105] scaler 0 setup success
[    15.105] Set CRTC 0 Source success
[    15.105] crtc 0 YUV disable setup success
[    15.107] Output digital setup success
[    15.433] Output LCD1 enable success
[    15.433] Enable CRTC 0 success
[    15.433] Unblank CRTC 0 success
[    15.433] Output CRT1 disable success
[    15.433] Blank CRTC 1 success
[    15.433] Disable CRTC 1 success
[    15.433] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.434] (--) RandR disabled
[    15.434] (II) Initializing built-in extension Generic Event Extension
[    15.434] (II) Initializing built-in extension SHAPE
[    15.434] (II) Initializing built-in extension MIT-SHM
[    15.434] (II) Initializing built-in extension XInputExtension
[    15.434] (II) Initializing built-in extension XTEST
[    15.434] (II) Initializing built-in extension BIG-REQUESTS
[    15.434] (II) Initializing built-in extension SYNC
[    15.434] (II) Initializing built-in extension XKEYBOARD
[    15.434] (II) Initializing built-in extension XC-MISC
[    15.434] (II) Initializing built-in extension SECURITY
[    15.434] (II) Initializing built-in extension XINERAMA
[    15.434] (II) Initializing built-in extension XFIXES
[    15.434] (II) Initializing built-in extension RENDER
[    15.434] (II) Initializing built-in extension RANDR
[    15.434] (II) Initializing built-in extension COMPOSITE
[    15.434] (II) Initializing built-in extension DAMAGE
[    15.434] (II) Initializing built-in extension GESTURE
[    15.449] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.450] drmOpenDevice: node name is /dev/dri/card0
[    15.450] drmOpenDevice: open result is 12, (OK)
[    15.450] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    15.450] drmOpenDevice: node name is /dev/dri/card0
[    15.450] drmOpenDevice: open result is 12, (OK)
[    15.450] drmOpenByBusid: drmOpenMinor returns 12
[    15.450] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    15.495] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    15.495] (II) AIGLX: enabled GLX_SGI_make_current_read
[    15.495] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    15.495] (II) AIGLX: enabled GLX_texture_from_pixmap with driver support
[    15.495] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    15.495] (II) GLX: Initialized DRI GL provider for screen 0
[    15.496] (II) RADEON(0): Setting screen physical size to 361 x 203
[    15.532] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.550] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    15.550] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.550] (II) LoadModule: "evdev"
[    15.551] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.552] (II) Module evdev: vendor="X.Org Foundation"
[    15.552]     compiled for 1.9.0, module version = 2.3.2
[    15.552]     Module class: X.Org XInput Driver
[    15.552]     ABI class: X.Org XInput driver, version 11.0
[    15.552] (**) Power Button: always reports core events
[    15.552] (**) Power Button: Device: "/dev/input/event3"
[    15.582] (II) Power Button: Found keys
[    15.582] (II) Power Button: Configuring as keyboard
[    15.582] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.582] (**) Option "xkb_rules" "evdev"
[    15.582] (**) Option "xkb_model" "pc105"
[    15.582] (**) Option "xkb_layout" "us"
[    15.586] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    15.586] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    15.586] (**) Video Bus: always reports core events
[    15.586] (**) Video Bus: Device: "/dev/input/event6"
[    15.622] (II) Video Bus: Found keys
[    15.622] (II) Video Bus: Configuring as keyboard
[    15.622] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    15.622] (**) Option "xkb_rules" "evdev"
[    15.622] (**) Option "xkb_model" "pc105"
[    15.622] (**) Option "xkb_layout" "us"
[    15.623] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    15.623] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.623] (**) Power Button: always reports core events
[    15.623] (**) Power Button: Device: "/dev/input/event2"
[    15.662] (II) Power Button: Found keys
[    15.662] (II) Power Button: Configuring as keyboard
[    15.662] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    15.662] (**) Option "xkb_rules" "evdev"
[    15.662] (**) Option "xkb_model" "pc105"
[    15.662] (**) Option "xkb_layout" "us"
[    15.663] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    15.663] (II) No input driver/identifier specified (ignoring)
[    15.664] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    15.664] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    15.664] (**) Sleep Button: always reports core events
[    15.664] (**) Sleep Button: Device: "/dev/input/event1"
[    15.702] (II) Sleep Button: Found keys
[    15.702] (II) Sleep Button: Configuring as keyboard
[    15.702] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    15.702] (**) Option "xkb_rules" "evdev"
[    15.702] (**) Option "xkb_model" "pc105"
[    15.702] (**) Option "xkb_layout" "us"
[    15.709] (II) config/udev: Adding input device CNF9011 (/dev/input/event5)
[    15.709] (**) CNF9011: Applying InputClass "evdev keyboard catchall"
[    15.709] (**) CNF9011: always reports core events
[    15.709] (**) CNF9011: Device: "/dev/input/event5"
[    15.742] (II) CNF9011: Found keys
[    15.742] (II) CNF9011: Configuring as keyboard
[    15.742] (II) XINPUT: Adding extended input device "CNF9011" (type: KEYBOARD)
[    15.742] (**) Option "xkb_rules" "evdev"
[    15.742] (**) Option "xkb_model" "pc105"
[    15.742] (**) Option "xkb_layout" "us"
[    15.745] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    15.745] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    15.746] (**) AT Translated Set 2 keyboard: always reports core events
[    15.746] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    15.782] (II) AT Translated Set 2 keyboard: Found keys
[    15.782] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    15.782] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    15.782] (**) Option "xkb_rules" "evdev"
[    15.782] (**) Option "xkb_model" "pc105"
[    15.782] (**) Option "xkb_layout" "us"
[    15.783] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event7)
[    15.783] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    15.783] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    15.783] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event7"
[    15.822] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    15.822] (II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    15.822] (II) ImPS/2 Generic Wheel Mouse: Found relative axes
[    15.822] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    15.822] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    15.822] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    15.822] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.822] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    15.822] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    15.823] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    15.823] (II) No input driver/identifier specified (ignoring)
[    16.429] Dac detection success
[    16.430] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    16.489] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.489] (II) RADEON(0): Printing DDC gathered Modelines:
[    16.489] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    16.489] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    16.489] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    16.489] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    16.489] (II) RADEON(0): Year: 2009  Week: 9
[    16.489] (II) RADEON(0): EDID Version: 1.3
[    16.489] (II) RADEON(0): Digital Display Input
[    16.489] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    16.489] (II) RADEON(0): Gamma: 2.20
[    16.489] (II) RADEON(0): No DPMS capabilities specified
[    16.489] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.489] (II) RADEON(0): First detailed timing is preferred mode
[    16.489] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    16.489] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    16.489] (II) RADEON(0): Manufacturer's mask: 0
[    16.489] (II) RADEON(0): Supported detailed timing:
[    16.489] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    16.489] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    16.489] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    16.489] (II) RADEON(0):  N116B6-L02
[    16.489] (II) RADEON(0):  CMO
[    16.489] (II) RADEON(0):  N116B6-L02
[    16.489] (II) RADEON(0): EDID (in hex):
[    16.489] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    16.489] (II) RADEON(0):     0913010380190e780acf459059579529
[    16.490] (II) RADEON(0):     1f505400000001010101010101010101
[    16.490] (II) RADEON(0):     0101010101019c19562a50000830070e
[    16.490] (II) RADEON(0):     1300009010000018000000fe004e3131
[    16.490] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    16.490] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    16.490] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    16.490] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.512] Dac detection success
[    16.512] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    16.571] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.571] (II) RADEON(0): Printing DDC gathered Modelines:
[    16.571] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    16.571] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    16.571] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    16.572] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    16.572] (II) RADEON(0): Year: 2009  Week: 9
[    16.572] (II) RADEON(0): EDID Version: 1.3
[    16.572] (II) RADEON(0): Digital Display Input
[    16.572] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    16.572] (II) RADEON(0): Gamma: 2.20
[    16.572] (II) RADEON(0): No DPMS capabilities specified
[    16.572] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.572] (II) RADEON(0): First detailed timing is preferred mode
[    16.572] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    16.572] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    16.572] (II) RADEON(0): Manufacturer's mask: 0
[    16.572] (II) RADEON(0): Supported detailed timing:
[    16.572] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    16.572] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    16.572] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    16.572] (II) RADEON(0):  N116B6-L02
[    16.572] (II) RADEON(0):  CMO
[    16.572] (II) RADEON(0):  N116B6-L02
[    16.572] (II) RADEON(0): EDID (in hex):
[    16.572] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    16.572] (II) RADEON(0):     0913010380190e780acf459059579529
[    16.572] (II) RADEON(0):     1f505400000001010101010101010101
[    16.572] (II) RADEON(0):     0101010101019c19562a50000830070e
[    16.572] (II) RADEON(0):     1300009010000018000000fe004e3131
[    16.572] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    16.572] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    16.572] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    16.572] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.611] Dac detection success
[    16.611] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    16.670] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.670] (II) RADEON(0): Printing DDC gathered Modelines:
[    16.670] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    16.670] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    16.670] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    16.671] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    16.671] (II) RADEON(0): Year: 2009  Week: 9
[    16.671] (II) RADEON(0): EDID Version: 1.3
[    16.671] (II) RADEON(0): Digital Display Input
[    16.671] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    16.671] (II) RADEON(0): Gamma: 2.20
[    16.671] (II) RADEON(0): No DPMS capabilities specified
[    16.671] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.671] (II) RADEON(0): First detailed timing is preferred mode
[    16.671] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    16.671] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    16.671] (II) RADEON(0): Manufacturer's mask: 0
[    16.671] (II) RADEON(0): Supported detailed timing:
[    16.671] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    16.671] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    16.671] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    16.671] (II) RADEON(0):  N116B6-L02
[    16.671] (II) RADEON(0):  CMO
[    16.671] (II) RADEON(0):  N116B6-L02
[    16.671] (II) RADEON(0): EDID (in hex):
[    16.671] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    16.671] (II) RADEON(0):     0913010380190e780acf459059579529
[    16.671] (II) RADEON(0):     1f505400000001010101010101010101
[    16.671] (II) RADEON(0):     0101010101019c19562a50000830070e
[    16.671] (II) RADEON(0):     1300009010000018000000fe004e3131
[    16.671] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    16.671] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    16.671] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    16.672] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.693] Dac detection success
[    16.693] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    16.752] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    16.752] (II) RADEON(0): Printing DDC gathered Modelines:
[    16.752] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    16.752] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    16.752] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    16.752] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    16.752] (II) RADEON(0): Year: 2009  Week: 9
[    16.752] (II) RADEON(0): EDID Version: 1.3
[    16.752] (II) RADEON(0): Digital Display Input
[    16.752] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    16.753] (II) RADEON(0): Gamma: 2.20
[    16.753] (II) RADEON(0): No DPMS capabilities specified
[    16.753] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    16.753] (II) RADEON(0): First detailed timing is preferred mode
[    16.753] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    16.753] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    16.753] (II) RADEON(0): Manufacturer's mask: 0
[    16.753] (II) RADEON(0): Supported detailed timing:
[    16.753] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    16.753] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    16.753] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    16.753] (II) RADEON(0):  N116B6-L02
[    16.753] (II) RADEON(0):  CMO
[    16.753] (II) RADEON(0):  N116B6-L02
[    16.753] (II) RADEON(0): EDID (in hex):
[    16.753] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    16.753] (II) RADEON(0):     0913010380190e780acf459059579529
[    16.753] (II) RADEON(0):     1f505400000001010101010101010101
[    16.753] (II) RADEON(0):     0101010101019c19562a50000830070e
[    16.753] (II) RADEON(0):     1300009010000018000000fe004e3131
[    16.753] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    16.753] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    16.753] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    16.753] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    17.973] Dac detection success
[    17.973] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    18.032] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    18.032] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.032] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    18.032] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    18.032] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    18.032] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    18.032] (II) RADEON(0): Year: 2009  Week: 9
[    18.032] (II) RADEON(0): EDID Version: 1.3
[    18.032] (II) RADEON(0): Digital Display Input
[    18.032] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    18.032] (II) RADEON(0): Gamma: 2.20
[    18.032] (II) RADEON(0): No DPMS capabilities specified
[    18.033] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.033] (II) RADEON(0): First detailed timing is preferred mode
[    18.033] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    18.033] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    18.033] (II) RADEON(0): Manufacturer's mask: 0
[    18.033] (II) RADEON(0): Supported detailed timing:
[    18.033] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    18.033] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    18.033] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    18.033] (II) RADEON(0):  N116B6-L02
[    18.033] (II) RADEON(0):  CMO
[    18.033] (II) RADEON(0):  N116B6-L02
[    18.033] (II) RADEON(0): EDID (in hex):
[    18.033] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    18.033] (II) RADEON(0):     0913010380190e780acf459059579529
[    18.033] (II) RADEON(0):     1f505400000001010101010101010101
[    18.033] (II) RADEON(0):     0101010101019c19562a50000830070e
[    18.033] (II) RADEON(0):     1300009010000018000000fe004e3131
[    18.033] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    18.033] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    18.033] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    18.033] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.692] Dac detection success
[    24.692] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    24.753] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.753] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.753] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    24.753] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    24.753] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    24.753] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    24.753] (II) RADEON(0): Year: 2009  Week: 9
[    24.753] (II) RADEON(0): EDID Version: 1.3
[    24.753] (II) RADEON(0): Digital Display Input
[    24.753] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    24.753] (II) RADEON(0): Gamma: 2.20
[    24.753] (II) RADEON(0): No DPMS capabilities specified
[    24.753] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.753] (II) RADEON(0): First detailed timing is preferred mode
[    24.753] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    24.754] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    24.754] (II) RADEON(0): Manufacturer's mask: 0
[    24.754] (II) RADEON(0): Supported detailed timing:
[    24.754] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    24.754] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    24.754] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    24.754] (II) RADEON(0):  N116B6-L02
[    24.754] (II) RADEON(0):  CMO
[    24.754] (II) RADEON(0):  N116B6-L02
[    24.754] (II) RADEON(0): EDID (in hex):
[    24.754] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    24.754] (II) RADEON(0):     0913010380190e780acf459059579529
[    24.754] (II) RADEON(0):     1f505400000001010101010101010101
[    24.754] (II) RADEON(0):     0101010101019c19562a50000830070e
[    24.754] (II) RADEON(0):     1300009010000018000000fe004e3131
[    24.754] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    24.754] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    24.754] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    24.754] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.777] Dac detection success
[    24.777] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    24.836] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.836] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.836] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    24.836] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    24.836] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    24.837] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    24.837] (II) RADEON(0): Year: 2009  Week: 9
[    24.837] (II) RADEON(0): EDID Version: 1.3
[    24.837] (II) RADEON(0): Digital Display Input
[    24.837] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    24.837] (II) RADEON(0): Gamma: 2.20
[    24.837] (II) RADEON(0): No DPMS capabilities specified
[    24.837] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.837] (II) RADEON(0): First detailed timing is preferred mode
[    24.837] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    24.837] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    24.837] (II) RADEON(0): Manufacturer's mask: 0
[    24.837] (II) RADEON(0): Supported detailed timing:
[    24.837] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    24.837] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    24.837] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    24.837] (II) RADEON(0):  N116B6-L02
[    24.837] (II) RADEON(0):  CMO
[    24.837] (II) RADEON(0):  N116B6-L02
[    24.837] (II) RADEON(0): EDID (in hex):
[    24.837] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    24.837] (II) RADEON(0):     0913010380190e780acf459059579529
[    24.837] (II) RADEON(0):     1f505400000001010101010101010101
[    24.837] (II) RADEON(0):     0101010101019c19562a50000830070e
[    24.837] (II) RADEON(0):     1300009010000018000000fe004e3131
[    24.837] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    24.837] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    24.837] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    24.837] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.859] Dac detection success
[    24.859] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    24.919] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.919] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.919] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    24.919] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    24.919] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    24.919] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    24.919] (II) RADEON(0): Year: 2009  Week: 9
[    24.919] (II) RADEON(0): EDID Version: 1.3
[    24.919] (II) RADEON(0): Digital Display Input
[    24.919] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    24.919] (II) RADEON(0): Gamma: 2.20
[    24.919] (II) RADEON(0): No DPMS capabilities specified
[    24.919] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    24.919] (II) RADEON(0): First detailed timing is preferred mode
[    24.919] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    24.919] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    24.919] (II) RADEON(0): Manufacturer's mask: 0
[    24.919] (II) RADEON(0): Supported detailed timing:
[    24.919] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    24.919] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    24.919] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    24.919] (II) RADEON(0):  N116B6-L02
[    24.919] (II) RADEON(0):  CMO
[    24.919] (II) RADEON(0):  N116B6-L02
[    24.919] (II) RADEON(0): EDID (in hex):
[    24.919] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    24.919] (II) RADEON(0):     0913010380190e780acf459059579529
[    24.919] (II) RADEON(0):     1f505400000001010101010101010101
[    24.919] (II) RADEON(0):     0101010101019c19562a50000830070e
[    24.920] (II) RADEON(0):     1300009010000018000000fe004e3131
[    24.920] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    24.920] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    24.920] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    24.920] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    24.941] Dac detection success
[    24.941] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    25.000] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    25.000] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.000] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    25.000] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    25.000] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    25.000] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    25.000] (II) RADEON(0): Year: 2009  Week: 9
[    25.000] (II) RADEON(0): EDID Version: 1.3
[    25.000] (II) RADEON(0): Digital Display Input
[    25.000] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    25.000] (II) RADEON(0): Gamma: 2.20
[    25.000] (II) RADEON(0): No DPMS capabilities specified
[    25.001] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.001] (II) RADEON(0): First detailed timing is preferred mode
[    25.001] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    25.001] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    25.001] (II) RADEON(0): Manufacturer's mask: 0
[    25.001] (II) RADEON(0): Supported detailed timing:
[    25.001] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    25.001] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    25.001] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    25.001] (II) RADEON(0):  N116B6-L02
[    25.001] (II) RADEON(0):  CMO
[    25.001] (II) RADEON(0):  N116B6-L02
[    25.001] (II) RADEON(0): EDID (in hex):
[    25.001] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    25.001] (II) RADEON(0):     0913010380190e780acf459059579529
[    25.001] (II) RADEON(0):     1f505400000001010101010101010101
[    25.001] (II) RADEON(0):     0101010101019c19562a50000830070e
[    25.001] (II) RADEON(0):     1300009010000018000000fe004e3131
[    25.001] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    25.001] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    25.001] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    25.001] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    25.211] Dac detection success
[    25.211] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    25.270] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    25.270] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.270] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    25.270] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    25.270] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    25.270] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    25.270] (II) RADEON(0): Year: 2009  Week: 9
[    25.270] (II) RADEON(0): EDID Version: 1.3
[    25.270] (II) RADEON(0): Digital Display Input
[    25.270] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    25.270] (II) RADEON(0): Gamma: 2.20
[    25.270] (II) RADEON(0): No DPMS capabilities specified
[    25.270] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.270] (II) RADEON(0): First detailed timing is preferred mode
[    25.270] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    25.271] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    25.271] (II) RADEON(0): Manufacturer's mask: 0
[    25.271] (II) RADEON(0): Supported detailed timing:
[    25.271] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    25.271] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    25.271] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    25.271] (II) RADEON(0):  N116B6-L02
[    25.271] (II) RADEON(0):  CMO
[    25.271] (II) RADEON(0):  N116B6-L02
[    25.271] (II) RADEON(0): EDID (in hex):
[    25.271] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    25.271] (II) RADEON(0):     0913010380190e780acf459059579529
[    25.271] (II) RADEON(0):     1f505400000001010101010101010101
[    25.271] (II) RADEON(0):     0101010101019c19562a50000830070e
[    25.271] (II) RADEON(0):     1300009010000018000000fe004e3131
[    25.271] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    25.271] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    25.271] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    25.271] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    30.626] Dac detection success
[    30.626] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    30.686] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[    30.686] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.686] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[    30.686] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    30.686] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    30.686] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[    30.686] (II) RADEON(0): Year: 2009  Week: 9
[    30.686] (II) RADEON(0): EDID Version: 1.3
[    30.686] (II) RADEON(0): Digital Display Input
[    30.686] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[    30.686] (II) RADEON(0): Gamma: 2.20
[    30.686] (II) RADEON(0): No DPMS capabilities specified
[    30.686] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.686] (II) RADEON(0): First detailed timing is preferred mode
[    30.686] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[    30.686] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[    30.686] (II) RADEON(0): Manufacturer's mask: 0
[    30.686] (II) RADEON(0): Supported detailed timing:
[    30.686] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[    30.686] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[    30.686] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[    30.686] (II) RADEON(0):  N116B6-L02
[    30.686] (II) RADEON(0):  CMO
[    30.686] (II) RADEON(0):  N116B6-L02
[    30.686] (II) RADEON(0): EDID (in hex):
[    30.687] (II) RADEON(0):     00ffffffffffff000daf001100000000
[    30.687] (II) RADEON(0):     0913010380190e780acf459059579529
[    30.687] (II) RADEON(0):     1f505400000001010101010101010101
[    30.687] (II) RADEON(0):     0101010101019c19562a50000830070e
[    30.687] (II) RADEON(0):     1300009010000018000000fe004e3131
[    30.687] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[    30.687] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[    30.687] (II) RADEON(0):     004e31313642362d4c30320a20200065
[    30.687] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[   542.656] Dac detection success
[   542.656] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[   542.715] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[   542.715] (II) RADEON(0): Printing DDC gathered Modelines:
[   542.715] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[   542.715] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   542.715] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[   542.715] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[   542.715] (II) RADEON(0): Year: 2009  Week: 9
[   542.715] (II) RADEON(0): EDID Version: 1.3
[   542.715] (II) RADEON(0): Digital Display Input
[   542.715] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[   542.715] (II) RADEON(0): Gamma: 2.20
[   542.715] (II) RADEON(0): No DPMS capabilities specified
[   542.715] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   542.715] (II) RADEON(0): First detailed timing is preferred mode
[   542.715] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[   542.716] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[   542.716] (II) RADEON(0): Manufacturer's mask: 0
[   542.716] (II) RADEON(0): Supported detailed timing:
[   542.716] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[   542.716] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[   542.716] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[   542.716] (II) RADEON(0):  N116B6-L02
[   542.716] (II) RADEON(0):  CMO
[   542.716] (II) RADEON(0):  N116B6-L02
[   542.716] (II) RADEON(0): EDID (in hex):
[   542.716] (II) RADEON(0):     00ffffffffffff000daf001100000000
[   542.716] (II) RADEON(0):     0913010380190e780acf459059579529
[   542.716] (II) RADEON(0):     1f505400000001010101010101010101
[   542.716] (II) RADEON(0):     0101010101019c19562a50000830070e
[   542.716] (II) RADEON(0):     1300009010000018000000fe004e3131
[   542.716] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[   542.716] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[   542.716] (II) RADEON(0):     004e31313642362d4c30320a20200065
[   542.716] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  1662.378] Dac detection success
[  1662.378] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[  1662.437] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  1662.437] (II) RADEON(0): Printing DDC gathered Modelines:
[  1662.438] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[  1662.438] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[  1662.438] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[  1662.438] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[  1662.438] (II) RADEON(0): Year: 2009  Week: 9
[  1662.438] (II) RADEON(0): EDID Version: 1.3
[  1662.438] (II) RADEON(0): Digital Display Input
[  1662.438] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[  1662.438] (II) RADEON(0): Gamma: 2.20
[  1662.438] (II) RADEON(0): No DPMS capabilities specified
[  1662.438] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  1662.438] (II) RADEON(0): First detailed timing is preferred mode
[  1662.438] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[  1662.438] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[  1662.438] (II) RADEON(0): Manufacturer's mask: 0
[  1662.438] (II) RADEON(0): Supported detailed timing:
[  1662.438] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[  1662.438] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[  1662.438] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[  1662.438] (II) RADEON(0):  N116B6-L02
[  1662.438] (II) RADEON(0):  CMO
[  1662.438] (II) RADEON(0):  N116B6-L02
[  1662.438] (II) RADEON(0): EDID (in hex):
[  1662.438] (II) RADEON(0):     00ffffffffffff000daf001100000000
[  1662.439] (II) RADEON(0):     0913010380190e780acf459059579529
[  1662.439] (II) RADEON(0):     1f505400000001010101010101010101
[  1662.439] (II) RADEON(0):     0101010101019c19562a50000830070e
[  1662.439] (II) RADEON(0):     1300009010000018000000fe004e3131
[  1662.439] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[  1662.439] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[  1662.439] (II) RADEON(0):     004e31313642362d4c30320a20200065
[  1662.439] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  2101.956] Dac detection success
[  2101.956] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[  2102.015] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  2102.015] (II) RADEON(0): Printing DDC gathered Modelines:
[  2102.015] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[  2102.015] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[  2102.015] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[  2102.015] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[  2102.015] (II) RADEON(0): Year: 2009  Week: 9
[  2102.015] (II) RADEON(0): EDID Version: 1.3
[  2102.015] (II) RADEON(0): Digital Display Input
[  2102.015] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[  2102.015] (II) RADEON(0): Gamma: 2.20
[  2102.015] (II) RADEON(0): No DPMS capabilities specified
[  2102.015] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2102.015] (II) RADEON(0): First detailed timing is preferred mode
[  2102.015] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[  2102.016] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[  2102.016] (II) RADEON(0): Manufacturer's mask: 0
[  2102.016] (II) RADEON(0): Supported detailed timing:
[  2102.016] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[  2102.016] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[  2102.016] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[  2102.016] (II) RADEON(0):  N116B6-L02
[  2102.016] (II) RADEON(0):  CMO
[  2102.016] (II) RADEON(0):  N116B6-L02
[  2102.016] (II) RADEON(0): EDID (in hex):
[  2102.016] (II) RADEON(0):     00ffffffffffff000daf001100000000
[  2102.016] (II) RADEON(0):     0913010380190e780acf459059579529
[  2102.016] (II) RADEON(0):     1f505400000001010101010101010101
[  2102.016] (II) RADEON(0):     0101010101019c19562a50000830070e
[  2102.016] (II) RADEON(0):     1300009010000018000000fe004e3131
[  2102.016] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[  2102.016] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[  2102.016] (II) RADEON(0):     004e31313642362d4c30320a20200065
[  2102.016] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  2412.894] Output LCD1 disable success
[  2412.894] Blank CRTC 0 success
[  2412.894] Disable CRTC 0 success
[  2412.894] Blank CRTC 1 success
[  2412.894] Disable CRTC 1 success
[  2412.894] Output LCD1 disable success
[  2412.894] Blank CRTC 0 success
[  2412.894] Disable CRTC 0 success
[  3487.707] Enable CRTC 0 success
[  3487.724] Unblank CRTC 0 success
[  3487.725] Output LCD1 enable success
[  3852.449] Dac detection success
[  3852.449] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[  3852.509] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  3852.509] (II) RADEON(0): Printing DDC gathered Modelines:
[  3852.509] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[  3852.509] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[  3852.509] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[  3852.509] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[  3852.509] (II) RADEON(0): Year: 2009  Week: 9
[  3852.509] (II) RADEON(0): EDID Version: 1.3
[  3852.509] (II) RADEON(0): Digital Display Input
[  3852.509] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[  3852.509] (II) RADEON(0): Gamma: 2.20
[  3852.509] (II) RADEON(0): No DPMS capabilities specified
[  3852.509] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  3852.509] (II) RADEON(0): First detailed timing is preferred mode
[  3852.509] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[  3852.509] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[  3852.509] (II) RADEON(0): Manufacturer's mask: 0
[  3852.509] (II) RADEON(0): Supported detailed timing:
[  3852.509] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[  3852.509] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[  3852.509] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[  3852.510] (II) RADEON(0):  N116B6-L02
[  3852.510] (II) RADEON(0):  CMO
[  3852.510] (II) RADEON(0):  N116B6-L02
[  3852.510] (II) RADEON(0): EDID (in hex):
[  3852.510] (II) RADEON(0):     00ffffffffffff000daf001100000000
[  3852.510] (II) RADEON(0):     0913010380190e780acf459059579529
[  3852.510] (II) RADEON(0):     1f505400000001010101010101010101
[  3852.510] (II) RADEON(0):     0101010101019c19562a50000830070e
[  3852.510] (II) RADEON(0):     1300009010000018000000fe004e3131
[  3852.510] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[  3852.510] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[  3852.510] (II) RADEON(0):     004e31313642362d4c30320a20200065
[  3852.510] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  6817.408] (II) XKB: reuse xkmfile /var/lib/xkb/server-81EC4871279DB1D73113D19E789F270C19322F52.xkm
[  9163.894] Dac detection success
[  9163.894] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[  9163.953] (II) RADEON(0): EDID vendor "CMO", prod id 4352
[  9163.953] (II) RADEON(0): Printing DDC gathered Modelines:
[  9163.953] (II) RADEON(0): Modeline "1366x768"x0.0   65.56  1366 1373 1387 1408  768 769 772 776 -hsync -vsync (46.6 kHz)
[  9163.953] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[  9163.953] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[  9163.953] (II) RADEON(0): Manufacturer: CMO  Model: 1100  Serial#: 0
[  9163.953] (II) RADEON(0): Year: 2009  Week: 9
[  9163.953] (II) RADEON(0): EDID Version: 1.3
[  9163.953] (II) RADEON(0): Digital Display Input
[  9163.953] (II) RADEON(0): Max Image Size [cm]: horiz.: 25  vert.: 14
[  9163.953] (II) RADEON(0): Gamma: 2.20
[  9163.953] (II) RADEON(0): No DPMS capabilities specified
[  9163.953] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  9163.953] (II) RADEON(0): First detailed timing is preferred mode
[  9163.954] (II) RADEON(0): redX: 0.565 redY: 0.348   greenX: 0.343 greenY: 0.585
[  9163.954] (II) RADEON(0): blueX: 0.161 blueY: 0.121   whiteX: 0.313 whiteY: 0.329
[  9163.954] (II) RADEON(0): Manufacturer's mask: 0
[  9163.954] (II) RADEON(0): Supported detailed timing:
[  9163.954] (II) RADEON(0): clock: 65.6 MHz   Image Size:  256 x 144 mm
[  9163.954] (II) RADEON(0): h_active: 1366  h_sync: 1373  h_sync_end 1387 h_blank_end 1408 h_border: 0
[  9163.954] (II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 776 v_border: 0
[  9163.954] (II) RADEON(0):  N116B6-L02
[  9163.954] (II) RADEON(0):  CMO
[  9163.954] (II) RADEON(0):  N116B6-L02
[  9163.954] (II) RADEON(0): EDID (in hex):
[  9163.954] (II) RADEON(0):     00ffffffffffff000daf001100000000
[  9163.954] (II) RADEON(0):     0913010380190e780acf459059579529
[  9163.954] (II) RADEON(0):     1f505400000001010101010101010101
[  9163.954] (II) RADEON(0):     0101010101019c19562a50000830070e
[  9163.954] (II) RADEON(0):     1300009010000018000000fe004e3131
[  9163.954] (II) RADEON(0):     3642362d4c30320a2020000000fe0043
[  9163.954] (II) RADEON(0):     4d4f0a202020202020202020000000fe
[  9163.954] (II) RADEON(0):     004e31313642362d4c30320a20200065
[  9163.954] (II) RADEON(0): EDID vendor "CMO", prod id 4352[/PHP]

---

### Post by Joe Awsome on 2011-01-29
Even with tjones help on how to make the desktop not get blurry, I'm still having tons of trouble with urban terror. The pic attached is on the light side of the glitches I'm dealing with. Sometimes whole sections of the map will look like moving rainbow painting with the colors constantly rearanging themselves, and other times the textures will get all gumbled up. An example of this was one room was pasted with a terrorists face all over the wall, while another displayed the bottom of a 5.56x45 round.

---

### Post by Savore on 2011-01-31
That is what I saw when I tried to visit colostate.edu... 
Seems like our little chipset is sorely unhappy with these drivers.

---

### Post by tjones00 on 2011-01-31
So I noticed from Savores xorg.0.log and from what I remember with my old 1250. The chipset does not have it's own ram and uses the systems.

His atombios seems fine as reported here.

```
[COLOR=#000000][COLOR=#DD0000][    14.265] (II) RADEON(0): initializing int10
[    14.266] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    14.269] (II) RADEON(0): ATOM BIOS detected
[    14.269] (II) RADEON(0): ATOM BIOS Rom: 
[    14.269]     SubsystemVendorID: 0x1025 SubsystemID: 0x028c
[    14.269]     IOBaseAddress: 0x9000
[    14.269]     Filename: BR33431.bin 
[    14.269]     BIOS Bootup Message:  
ATI Radeon Xpress for SJM11-YK                                               

[    14.269] (II) RADEON(0): Framebuffer space used by Firmware (kb): 16
[    14.269] (II) RADEON(0): Start of VRAM area used by Firmware: 0x17ffc000
[    14.269] (II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space
[    14.269] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x17ffc000
[    14.269] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[/COLOR][/COLOR] 
```

The bios on the motherboard should have a ram option that indicates how much of the systems ram can be used by the chipset.

Try bumping up the ram allocated to the chipset in the bios and see if that fixes your issue. If you use high resolutions or do 3d gaming more ram may be required. I remember with my 1250 I could take it up to 512mb. 256mb is the suggested standard to use a 1920x1080 resolution with things like video. So go for the max.

Graphical artifacts may be due to heat and power consumption as well. I know with nvidia there are tools to regulate performance vs heat I'm not so sure with ati.

---

### Post by Joe Awsome on 2011-02-01
my video ram is fine, it's up at 384MB in the BIOS. I'm still getting blurry screens and messed up textures though, and the VRAM amount is unchangeable in my BIOS. Anyone know where I can download the Gallium driver for ubuntu without adding a ppa?

---

### Post by Joe Awsome on 2011-02-01
I think I found a fix for the blurry textures I'm getting during 3D gaming in this thread. I still need to test the fix cuz I'm waiting for a download to finish so I can reboot. Thanks a billion to everyone who's posted on this thread! :)

---

### Post by fenofonts on 2011-02-24
Hi All, I have always used the forum for reference and the xorg-edgers driver advice on this post helped me loads. 

However, I found an alternative solution that worked for me, stopping 99% of the crashes* on my Radeon X1270 and still keeping the 3D acceleration (The only bug I have seen so far (apart from losing the Ubuntu splash  screen at boot) is that I have occasional rendering problems when  loading World of Goo. Then sometimes it works fine. All the issues of  crashing in firefox, scrolling etc have gone! I can live with these  settings now! :grin:)

Here it is:
According to bluelamp999 on this post: ([http://ubuntuforums.org/archive/index.php/t-1471701.html](http://ubuntuforums.org/archive/index.php/t-1471701.html)) all you need to do is to add the line GRUB_CMDLINE_LINUX="nomodeset" to /etc/default/grub then update the grub with sudo update-grub.

Yes, it also confused me as to why would the grub influence my graphics performance... but somehow it seems to work.


The general info: 
Packard Bell Dot m/a 020 (UK) 
AMD L110 2GB RAM  
ATI Radeon X1270 (RS690) A.K.A. "the culprit" using the standard xserver-xorg-video-radeon driver that Ubuntu 10.10 defaults (but crashes on the X1270)
Pulled out the HDD in favour of SSD but I don't see why this should influence

---

### Post by Yellow Pasque on 2011-02-24
> **fenofonts said:**
> Yes, it also confused me as to why would the grub influence my graphics performance... but somehow it seems to work.

For a long time, modesetting was done in user space. Recently, it's been done in the kernel instead. Your grub option reverts to the old behavior. Ideally, you would file a bug report (if it's not already documented) on freedesktop and get it fixed in the kernel (if it hasn't been fixed in a newer kernel already).

---

### Post by Joe Awsome on 2011-03-07
So I decided to do a flesh install of Ubuntu 10.10 with the new gallium3d driver for my card to see if I could get better 3d support with urban terror. I added the correct ppa for the drivers, updated my fresh install with 300Mb of updates w/ the new ppa, but i'm still using the crapy open source support. How would I switch over to the new Gallium driver via the terminal? I've also tried configuring that file for "nomodeset" in hopes of getting rid of the blurry lines in the opensource driver but it won't let me for some odd reason, all I get out of the command is
```

Fatal server error:
Server is already active for display 0
     If this server is no linger running, remove /tmp/.X0lock and start again.

Please consult the The X.Org Foundation support
     at http://wiki.x.org for help

ddxSigGiveUp: Closing log
```

---

### Post by gordintoronto on 2011-03-07
Joe, I suspect half of the problems you report are because your CPU is brutally slow. For example, the 480P flash limit.

It's great to get use out of low-power systems, but you can't expect to get the same performance as the current top-of-the-line.

---

### Post by fenofonts on 2011-03-07
> **gordintoronto said:**
> Joe, I suspect half of the problems you report are because your CPU is brutally slow. For example, the 480P flash limit.

It's great to get use out of low-power systems, but you can't expect to get the same performance as the current top-of-the-line.

Hi Gorditoronto, I believe Joe is referring to the lack of 3D acceleration on the custom Radeon HD drivers built to halt the crashes (xorg-edgers-radeonhd). It does make vector and 3D painfully slow.

The processor as such is not a problem. My system is pretty much the same as his (AMD L110 1.2GHz, ATI X1270, 2GB RAM) and with 3D acceleration you can even play h.264 720p MKVs in VLC. You are right in saying flash/youtube only 480p though...

Overall, it ain't bad at all. Doesn't even feel like a netbook and I hardly use my desktop now.

---

### Post by Joe Awsome on 2011-03-07
fenofonts is right, I was able to watch a fulllength movie in 720p MKV in my last install. All I want to know is how to get gallium loaded as my default driver, and how to get the blurry texture corruptions from plagueing my install. I'm kinda looking at some other distros in hopes of better graphics support. I am in no way looking for desktop performance from this little netbook (though the cpu is a huge bottleneck for the GPU and other parts of the PC, been looking to upgrade to an AMD l310). I'm just asking for the comunity to help me with my problem so this system becomes usable again.;)

---

### Post by Joe Awsome on 2011-03-09
apparently I am using the gallium driver already, I just didn't know it.
```
joe@joe-LT31:~$ glxinfo | grep OpenGL
r300: DRM version: 2.5.0, Name: ATI RS690, ID: 0x791f, GB: 1, Z: 1
r300: GART size: 509 MB, VRAM size: 384 MB
r300: AA compression: NO, Z compression: NO, HiZ: NO
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS690
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
joe@joe-LT31:~$ 

```
And yes 3d is pretty slow; In urban terror i'll look at a wall and get 30fps, but when i look to somewhere where people are fighting or moving the fps will drop to the single digits. I'll be lucky to get around 12fps in combat. The only problem I have now is that Xorg still won't configure
```
joe@joe-LT31:~$ sudo Xorg -configure

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```
If anyone has a workaround or genuine fix please don't be shy to post. :) I was also thinking of updating mesa to it's latest development release. comments questions, or concerns?

---

### Post by Yellow Pasque on 2011-03-09
You really don't need an xorg.conf and the xorg-edgers PPA already has the latest mesa.
BTW, you need to stop gdm/X before doing that Xorg command. Log out, press Ctrl+Alt+F1, log in to the terminal, and:
```
sudo service gdm stop
sudo rm /etc/X11/xorg.conf
sudo Xorg -configure
sudo service gdm start
```

Are you using the 2.6.38 kernel?
```
uname -a
```

---

### Post by Joe Awsome on 2011-03-11
apparently not:
```
joe@joe-LT31:~$ uname -a
Linux joe-LT31 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux
joe@joe-LT31:~$ 

```

---

### Post by fenofonts on 2011-03-29
Has anyone else noticed that with the recent updates the 3D acceleration was killed??

Driver xserver-xorg-video-radeon
Version 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick

Has no 3D acceleration, or could it be something else like a mesa update? All was fine and I updated the system yesterday allowing all packages, then back to crappy 3D performance again.

Suggestions anyone? 
```

glxinfo | grep OpenGL
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
rob@rob-DOT:~$ ^C
rob@rob-DOT:~$ glxinfo | grep OpenGL
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
rob@rob-DOT:~$ sudo apt-get install mesa-utils
[sudo] password for rob: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rob@rob-DOT:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglew1.5
Suggested packages:
  glew-utils
The following NEW packages will be installed
  libglew1.5 mesa-utils
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 129kB of archives.
After this operation, 496kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick/main libglew1.5 i386 1.5.2-0ubuntu1 [102kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ maverick/universe mesa-utils i386 8.0.1-0ubuntu1 [27.0kB]
Fetched 129kB in 0s (502kB/s)       
Selecting previously deselected package libglew1.5.
(Reading database ... 146024 files and directories currently installed.)
Unpacking libglew1.5 (from .../libglew1.5_1.5.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package mesa-utils.
Unpacking mesa-utils (from .../mesa-utils_8.0.1-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libglew1.5 (1.5.2-0ubuntu1) ...
Setting up mesa-utils (8.0.1-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
rob@rob-DOT:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_draw_instanced, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_framebuffer_object, GL_ARB_half_float_pixel, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query2, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_provoking_vertex, GL_ARB_shader_objects, 
    GL_ARB_shading_language_100, GL_ARB_shadow_ambient, GL_ARB_shadow, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_texture_rg, GL_ARB_texture_swizzle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_bounds_test, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_array, GL_OES_read_format, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_object_purgeable, 
    GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ATI_blend_equation_separate, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_resize_buffers, GL_MESA_texture_array, 
    GL_MESA_window_pos, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_point_sprite, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGI_texture_color_table, GL_SUN_multi_draw_arrays

64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0dd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0de 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0df 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0e5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ea 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ed 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ee 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ef 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0f4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0f5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0f6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0f7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0f8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0f9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0fa 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0fb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0fc 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0fd 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0fe 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ff 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x100 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x101 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x102 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x103 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x104 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x105 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x106 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x107 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x108 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x109 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x10a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x10b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x10c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x10d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x10e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x10f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x110 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x111 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x112 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x113 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x114 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x115 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x116 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x117 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x118 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x119 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05c 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05d  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05e  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05f  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x061  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x062  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x063  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x064  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x065  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x066  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x067  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x068  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x069  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x06a  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x06b  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x06c  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x06d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x06f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x071  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x072  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x073  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x075  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x076  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x078  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x079  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x07a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x07d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x07f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x080 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x081 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x082 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x083 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x084 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x085 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x086 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x087 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x088 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x089 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x091 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x092 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x093 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x095 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x097 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x098 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x099 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09d  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x09f  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a0  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a1  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a2  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0a3  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a4  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0a5  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x0a6  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x0a7  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x0a8  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x0a9  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x0aa  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x0ab  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x0ac  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x0ad  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ae  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0af  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0b0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0b1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0b2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0b3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0b4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0b5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0b7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0b8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0b9  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0ba  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0bb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0bc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0bd 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0be 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0bf 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0c3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0c4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0c5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0ca 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cb 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cc 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ce 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0cf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0d3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0d4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0d5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0d7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0d9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0da 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0db 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0dc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```

---

