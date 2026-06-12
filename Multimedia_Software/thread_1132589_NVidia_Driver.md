---
title: "NVidia Driver"
date: 2009-04-22
forum: Multimedia Software
---

### Post by ashwinismu on 2009-04-22
Hi. I am absolutely new to Linux. I just installed Ubuntu 8.10 . I am trying to install the driver for my NVidia graphics card.

I clicked the "Activate" button on the Hardware Drivers Screen to enable the accelerated graphics driver (177). I got a popup screen that read "Downloading and installing driver". However, the popup screen got killed after a few seconds. 

When I attempt to use the "extra" settings in "Appearance" section, I am unable to do so as the driver hasnt been activated. 

Please advise.

Regards,
Ash.

---

### Post by balaknair on 2009-04-22
Were you connected to the internet when you attempted to activate the drivers?

If the hardware drivers applet didn't work for you, try opening the Synaptic Package Manager(System menu> Administration> Synaptic Package Manager), search for 'nvidia drivers' and select the version you want(eg. *nvidia-glx-180* or *nvidia-glx-177*). After installing the drivers it is necessary to restart the system, open 'Hardware Drivers', and activate the drivers you want. before you can use the drivers and enable desktop effects.

PS: The nVidia driver recommended for Ubuntu 8.10 is version 180. Install the *nvidia-180-modaliases* package as well in Synaptic if you want it to be available in 'Hardware Drivers'

---

### Post by gewitty on 2009-04-22
I also have a problem with the installation of the driver for an Nvidia card.

This is on a new system which I am currently setting up, using 8.10.

I have tried both the 177 and 180 drivers (as recommended above) but without success. With the 177 driver, I seem to get full graphics capability, as Compiz effects seem to work. But I cannot access any screen resolution above 640x480. When I tried the 180 driver, the system failed during boot and wanted to revert to low graphics mode. I checked the Xorg log and found that the problem appears to be a failure to recognise the monitor. This was the log output:

The :0.log was as follows:

6070 5811
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dave-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Apr 22 22:32:47 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xeb000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
6070 5811


The Xorg.0 log was as follows:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dave-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 22 22:32:45 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation unknown chipset (0x065b) rev 161, Mem @ 0xec000000/16777216, 0xd0000000/268435456, 0xea000000/33554432, I/O @ 0x0000bf00/128, BIOS @ 0x????????/524288
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:17:21 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 10:59:18 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(EE) No devices detected.

Fatal server error:
no screens found


The Xorg.conf file reads:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



The monitor perform OK in the default Ubuntu driver setup (is this Open GL?). However, if I go into the screen resolution settings, the screen is shown as 'unknown' and I can only change the resolution. The refresh rate option is fixed at 0Hz and clicking on 'Detect Displays' has no effect at all.

Am I right in concluding that the problem is not with the Nvidia driver(s), but with the recognition of the monitor (this is a 19" edge 10, model W193)?

---

### Post by rotary12 on 2009-04-22
> **ashwinismu said:**
> Hi. I am absolutely new to Linux. I just installed Ubuntu 8.10 . I am trying to install the driver for my NVidia graphics card.

I clicked the "Activate" button on the Hardware Drivers Screen to enable the accelerated graphics driver (177). I got a popup screen that read "Downloading and installing driver". However, the popup screen got killed after a few seconds. 

When I attempt to use the "extra" settings in "Appearance" section, I am unable to do so as the driver hasnt been activated. 

Please advise.

Regards,
Ash.

did you activate the third-party software. if you didnt go to system-> administration->software sources and in third party software tick the one thats there then go to  updates and tick unsupported updates and reload,it should work

---

### Post by balaknair on 2009-04-22
@gewitty

Hello gewitty

From what I can make of it, the problem is indeed with the nVidia drivers in this case(since things seem to work fine in the LiveCD session).

From the Xorg log, it seems that it doesn't reconize your graphics card chipset, or the drivers are not properly installed. What model is your graphics card?
Use this link to see which driver your card needs
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I suggest uninstalling the drivers and reinstalling them, and then rebooting.

Method 1: via the GUI
I suggest using EnvyNG to uninstall the drivers and reinstall them

*Install EnvyNG using the Synaptic Package Manager

*Start EnvyNG(Applications> System tools> EnvyNG

*Choose the option to remove the nVidia drivers

*Reboot

*Start EnvyNG and use it to reinstall the drivers, and reboot again.


Method 2: via the command line
* Open a terminal(Applications> Accessories> Terminal) and type in or Copy/Paste the following commands to uninstall the nvidia drivers


```
sudo apt-get --purge remove nvidia-glx* nvidia-settings nvidia-kernel-common

```
```
sudo rm /etc/init.d/nvidia-*
```

* Now use this command to reinstall the nVidia driver
```
sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
```

* Reboot the system

* Open hardware drivers and activate the version 180 drivers.

*Reboot if prompted.

I hope this helps.

---

### Post by gewitty on 2009-04-23
Thanks for the driver installation ideas, but it now appears that the driver problem may not be with the Nvidia graphics card (I installed the latest driver version, 180, as you suggested, with no improvement), but with the monitor.

Having spoken to the PC supplier and the monitor manufacturer, both seem to think that the issue is that Nvidia cannot find a driver for the screen and therefore does not recognise it.

The monitor is an edge10 W193. I've had a quick look around, but so far have not been able to find a Linux driver for this model. edge10 tech support do not supply one and they suggested that I try the Nvidia web site, where they thought I would find one. However, that does not seem to be the case.

I posted a query on the Nvidia forum, but have had no replies yet.

Any ideas on where I go from here?

---

### Post by balaknair on 2009-04-25
@gewitty

Sorry for the delay in replying

I think it's an improperly configured driver that's causing this. You shouldn't otherwise be getting the 'no devices detected' error.
The steps outlined in my previous post would basically reinstall the drivers and reconfigure Xserver.

You could also try booting into recovery mode and choose the option to fix graphics or reconfigure graphics(I don't remember the exact wording). This should generate a new xorg.conf file.

Once the graphics card is up and running, we can add the higher resolution to xorg.conf manually if necessary.

---

### Post by gewitty on 2009-04-25
Hi Balaknair. Thanks for the help.

OK. I ran through the uninstall/reinstall routine you suggested, using the terminal option. This is the terminal output as I ran through it:

dave@dave-desktop ~ $ sudo apt-get --purge remove nvidia-glx* nvidia-settings nvidia-kernel-common
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-new-envy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-dev-legacy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-96-dev for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-dev-new for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-dev for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-ia32 for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-new for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-173-dev for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-dev-new-envy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-src for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-lrm-dev for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-envy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-173 for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-180 for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-177 for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-177-dev for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-legacy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-dev-legacy-envy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-71-dev for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-legacy-envy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-dev-envy for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-71 for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-96 for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx for regex &#8216;nvidia-glx*&#8217;
Note, selecting nvidia-glx-180-dev for regex &#8216;nvidia-glx*&#8217;
Package nvidia-kernel-common is not installed, so not removed
The following packages were automatically installed and are no longer required:
  localechooser-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  nvidia-glx-177* nvidia-settings*
0 upgraded, 0 newly installed, 2 to remove and 275 not upgraded.
After this operation, 49.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115393 files and directories currently installed.)
Removing nvidia-glx-177 ...
Purging configuration files for nvidia-glx-177 ...
dpkg - warning: while removing nvidia-glx-177, directory `/usr/lib32/tls' not empty so not removed.
dpkg - warning: while removing nvidia-glx-177, directory `/usr/lib/tls' not empty so not removed.
Removing nvidia-settings ...
Purging configuration files for nvidia-settings ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dave@dave-desktop ~ $ sudo rm /etc/init.d/nvidia-*
rm: cannot remove `/etc/init.d/nvidia-*': No such file or directory
dave@dave-desktop ~ $ sudo apt-get install nvidia-glx-180 nvidia-180-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  localechooser-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-180-kernel-source nvidia-settings
The following packages will be REMOVED
  nvidia-177-kernel-source
The following NEW packages will be installed
  nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180
  nvidia-settings
0 upgraded, 4 newly installed, 1 to remove and 275 not upgraded.
Need to get 19.5MB/20.3MB of archives.
After this operation, 53.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  nvidia-180-kernel-source nvidia-180-modaliases nvidia-glx-180
  nvidia-settings
Authentication warning overridden.
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted nvidia-180-kernel-source 180.11-0ubuntu1~intrepid1 [2838kB]
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main nvidia-180-modaliases 180.11-0ubuntu1~intrepid1 [7698B]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted nvidia-glx-180 180.11-0ubuntu1~intrepid1 [16.6MB]
Fetched 19.5MB in 47s (409kB/s)                                                
(Reading database ... 115306 files and directories currently installed.)
Removing nvidia-177-kernel-source ...
Removing all DKMS Modules
Done.
Selecting previously deselected package nvidia-180-kernel-source.
(Reading database ... 115269 files and directories currently installed.)
Unpacking nvidia-180-kernel-source (from .../nvidia-180-kernel-source_180.11-0ubuntu1~intrepid1_amd64.deb) ...
Selecting previously deselected package nvidia-180-modaliases.
Unpacking nvidia-180-modaliases (from .../nvidia-180-modaliases_180.11-0ubuntu1~intrepid1_amd64.deb) ...
Selecting previously deselected package nvidia-glx-180.
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.11-0ubuntu1~intrepid1_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_177.78-0ubuntu2.1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-180-kernel-source (180.11-0ubuntu1~intrepid1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.11
Doing initial module build
Installing initial module
Done.

Setting up nvidia-180-modaliases (180.11-0ubuntu1~intrepid1) ...
Setting up nvidia-glx-180 (180.11-0ubuntu1~intrepid1) ...

Setting up nvidia-settings (177.78-0ubuntu2.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dave@dave-desktop ~ $ 

After this, I opened up the Hardware Drivers utility and saw that the 180 driver was available and recommended, so went ahead and installed it. Then I rebooted.

As the boot started, I got an error panel show up with this message:

**Ubuntu is running in low-graphics mode.**
The following error was encountered. You may need to update your configuration to solve this.

(EE) No devices detected

I then got an option screen and selected 'Run Ubuntu in low-graphics mode'. Got a message saying that the display was restarting. The system then started up OK, with the correct resolution. After everything had loaded, I got a message pop-up on the desktop which said, 'New restricted drivers in use'. When I checked the Hardware Drivers utility, it confirmed that the 180 driver is enabled. However, the system remains in low-graphics mode and is ignoring any Compiz effects settings. If I try to launch Google Earth, it gets as far as the splash screen and then quits.

I checked the Screen Resolution utility again and it still says it doesn't recognise the monitor.

The current set-up in xorg.conf is as follows:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


The two logs which show the startup errors are Xorg.0.log and :0.log. The contents of these are as follows:

**Xorg.o.log**

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dave-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 25 15:43:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation unknown chipset (0x065b) rev 161, Mem @ 0xec000000/16777216, 0xd0000000/268435456, 0xea000000/33554432, I/O @ 0x0000bf00/128, BIOS @ 0x????????/524288
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:17:21 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 10:59:18 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(EE) No devices detected.

Fatal server error:
no screens found


**:0.log**

6076 5817
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dave-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Sat Apr 25 15:43:24 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xeb000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
6076 5817


If it's any help, my hardware set-up is as follows:

Processor (CPU) Intel® CoreTM2 Duo E8400 (2 X 3.00GHz) 1333MHz FSB/6MB L2 Cache
Memory (RAM) 4GB CORSAIR XMS2 800MHz - LIFETIME WARRANTY! (2x2GB)
Motherboard ASUS® P5N73-AM: DDR2, S-ATA II, 1 x PCI-E x16, 2 PCI, etc
Operating System Mint 64 bit
1st Hard Disk 160GB SERIAL ATA II HARD DRIVE WITH 8MB CACHE (7,200rpm)
2nd Hard Disk 1000GB SERIAL ATA II HARD DRIVE WITH 16MB CACHE (7,200rpm)
1st CD/DVD Drive 22x DUAL LAYER LIGHTSCRIBE DVD WRITER ±R/±RW/RAM
2nd CD/DVD Drive 16x DVD-ROM & 52x CD-ROM DRIVE
Graphics Card 512MB GEFORCE 9400GT PCI Express + DVI + TV-OUT
Sound Card ONBOARD 6 CHANNEL (5.1) HIGH DEF AUDIO
Monitor edge10 W193

Does any of that make sense to you?

---

### Post by balaknair on 2009-04-25
OK, now it makes more sense.

The GeForce 9400GT is not fully supported by the driver version in Ubuntu Intrepid Ibex(180.11)

9400GT support was added only with the most recent version(180.51)
This will have to be downloaded from the nVidia site since as far as I know,it is not available in the Ubuntu repositories.
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

After downloading the file, you will need to completely uninstall the previous driver version(180.11) and switch to a text console to install the nVidia drivers.

The problem with installing drivers from non-repository sources is that you will have to repeat the install process every time the kernel is updated. The advantage of course is that you can use the very latest driver available, which in some cases(like in your situation with the 9400GT) would be worth the inconvenience.

How to install the nVidia-packaged drivers:

Download the nvidia driver from the nvidia site(link given above) and save it your Home folder.
Write down or print out the instructions, since you will have to do the following steps without a GUI.

1) Switch to a tty console by pressing ctrl-alt-F1--> login with your user name and paaword.

2) Stop the GUI
```
sudo /etc/init.d/gdm stop
```

3) Uninstall the previously installed drivers.
```
sudo apt-get --purge remove nvidia-glx* nvidia-settings nvidia-kernel-common
```

4) Install the packages needed to compile a kernel module
```
sudo apt-get install build-essential linux-headers-`uname -r`

```

5) Install the nVidia drivers
```
sudo sh ./NVIDIA***.run
```
(just hit 'Tab' after NV to autocomplete the filename)

The installer will offer a few options, just stick with the defaults, except for the last one where it asks if you want it to configure xorg- the default option is 'No', choose 'Yes'

6) Start the GUI
```
sudo /etc/init.d/gdm start
```

You might need to restart to get the drivers working properly.

Hope this is helpful.

All the best.

---

### Post by gewitty on 2009-04-25
Sorry to be thick. But can you clarify what should go in the line:

sudo apt-get install build-essential linux-headers-`uname -r`

I tried it as it is written and also substituted uname with my own log-in name, but it just throws up an error saying that it can't find package linux-headers-'uname -r', or can't find package linux-headers-'dave -r'

I'm obviously not getting this line right.

---

### Post by balaknair on 2009-04-25
Could you try just copy pasting that command exactly as it is into a terminal(from within the GUI). Don't substitute `uname -r` for anything- It basically asks the system which version of the kernel is in use.

I think there might have been a typo when you typed it in(those are not quote marks around the uname -r, it's the little squiggly thing in the top row of the keyboard to the left of the 1,2,3 buttons- `uname -r' not 'uname -r' ) This was the same mistake I made the first time I tried :D


eg:
```

bala@bala-desktop:~$ uname -r
[COLOR="Red"]2.6.28-11-generic
[/COLOR]
bala@bala-desktop:~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for bala: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
linux-headers-[COLOR="Red"]2.6.28-11-generic[/COLOR] is already the newest version.
linux-headers-2.6.28-11-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

In Intrepid, I think the current version should be *linux-headers-2.6.27-11-generic*

So you can also just substitute `uname -r` with 2.6.27-11-generic so that the command looks like this 
```
sudo apt-get install build-essential linux-headers-2.6.27-11-generic
```

Hope this clears your doubt.

All the best.

---

### Post by gewitty on 2009-04-25
Ah! Got that thanks.

OK. I got through to the installation sequence of the driver. It went as you said, but at one point it threw up a warning, as follows:

WARNING:
The runtime configuration check failed for library `libGL.so.180.51 (Expected: `/emul/ia32-linux/usr/lib/libGL.so.1  Found: (not found)). The most likely reason for this is that the library was installed to the wrong location.


After that, it seemed to complete the installation OK, so I restarted the GUI. The I got the same old 'Ubuntu is running in low-graphics mode' message, followed by the following errors:

(EE) NVIDIA(0) failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA device files have been created properly.
Please consult the NVIDIA README for details.
***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

I checked the file location mentioned in the warning and the libGL.so.1 is there, in exactly the right place. So I'm not sure why that error occurred.

---

### Post by balaknair on 2009-04-25
Could you reboot and see how it goes? This really is pretty unusual. It looks pretty much like an installation failure. Did you run the `uname -r` part correctly?

The only other reason I can think of is an improperly packaged driver installer.
BTW, since you're using the 64-bit version of Ubuntu, did you download the 64-bit driver?

I don't have an nVidia card at present, but I could dig out my old one on Monday and give it a go and see if I can replicate the error.

Doing a quick search shows a lot of people having trouble with the new drivers.
I wonder if anyone on the nVidia forums has had similar issues.

I think maybe for now, you should stick with the 'nv' drivers(the free open source drivers).

---

### Post by balaknair on 2009-04-25
OK, hunting around a bit more, I found another option

A PPA repository which has the latest nVidia drivers packaged for Ubuntu.
[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

Uninstall the drivers you installed- open a console shell(ctrl-alt-F1) and stop GDM, then run the commands 
*sudo sh ./NVIDIA***.run --uninstall*
*sudo dpkg-reconfigure -phigh xserver-xorg *

This returns the GUI configuration to a basic fallback state.
Now reboot after starting the GUI with the command 
*sudo /etc/init.d/gdm start*

After rebooting, just follow the link given above and follow the instructions given to add the PPA to your repositories. Run update manager and check for updates. Then you can install the drivers via the 'Hardware manager'
This seems to have worked for a few people who ran into trouble with the nvidia package.

Hopefully, it'll work for you :D

All the best.

---

### Post by gewitty on 2009-04-25
Hi Balaknair. Thanks for all your help, your time was really appreciated.

I tried your last idea, but sadly, got the same errors.

I think I'm going to have to try a complete re-installation of the OS. There has to be something screwed up somewhere to cause all this trouble and I could spend hours looking for it.

It's a real pain, as I had the whole system set up the way I want it, with all the packages installed and the whole thing configured. But that's life.

Thanks again for your help. I'll post here again once I've rebuilt the system, hopefully with good news. Might not be for a couple of days though.

---

### Post by inobe on 2009-04-25
gewitty if you want the latest 180.51 driver use this repo and save the trouble of manually installing.

[http://ubuntuforums.org/showpost.php?p=7132429&postcount=2](http://ubuntuforums.org/showpost.php?p=7132429&postcount=2)

a side note: manually installed drivers will break with future linux kernel updates, when installed from synaptic is best.

in your situation i noticed you purged some stuff, you may need to manually select the components in synaptic, i could name them if you wish.

---

### Post by balaknair on 2009-04-25
If you're going to reinstall, you could try Ubuntu 9.04, I've been using it since Alpha 6 and it's pretty good, hardware support seems better than in Intrepid(though I've only tested it on two systems so far).

If you're going to install the same version of Ubuntu(8.10) then I suggest you follow the howto on this page to get all the packages you want back when you reinstall.
[http://mybrainrunslinux.squarespace.com/journal/2009/3/7/how-to-setup-ubuntu-for-reinstalling-your-applications-witho.html](http://mybrainrunslinux.squarespace.com/journal/2009/3/7/how-to-setup-ubuntu-for-reinstalling-your-applications-witho.html)

To avoid having to download the packages again, use Apt-on-CD to save all the packages you have in the apt-cache(sudo apt-get install aptoncd) to CD or DVD and after reinstalling Ubuntu, put the disk in the drive and add it to your repositories(System menu> Admin...> Software Sources--> add CD). Apt-get will use the packages on the disk unless there is a new version available in the repos.

To save and restore your custom settings, app settings, bookmarks etc, copy the files in your home folder(most of these settings are in hidden folders, press ctrl-h to view hidden folders in the file browser) to an external drive or CD/DVD, and copy them over to the new home folder after installation.
It is always advisable to have a separate partition for your home folder since it preserves your personal data in the event of reinstalling the OS. An excellent guide here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Since you're reinstalling you can start afresh and create a new /home partition by opting for 'Manual Partitioning' this time around and then copy all the files(including hidden files) into your new /home/user_name folder to restore your custom settings(most of them anyway); this would probably be easier right now.

Hope you find this useful.

All the best.

---

### Post by ibuclaw on 2009-04-25
Not that it matters now, considering the direction this thread has gone, but I have a documented howto on manually installing nvidia drivers in ubuntu, and how to keep them in sync with kernel updates.
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

@balaknair
The reason why the OP didn't have success with manually installing earlier was because the Ubuntu drivers were still installed on the system, and were conflicting with the NViDIA ones.

Regards
Iain

---

### Post by inobe on 2009-04-25
> **tinivole said:**
> Not that it matters now, considering the direction this thread has gone, but I have a documented howto on manually installing nvidia drivers in ubuntu, and how to keep them in sync with kernel updates.
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)



i like testing the beta's, thanks for the tutorial tinivole.


tinivole we need a thumbs up smile for the forums :)

---

### Post by balaknair on 2009-04-25
> **tinivole said:**
> Not that it matters now, considering the direction this thread has gone, but I have a documented howto on manually installing nvidia drivers in ubuntu, and how to keep them in sync with kernel updates.
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

@balaknair
The reason why the OP didn't have success with manually installing earlier was because the Ubuntu drivers were still installed on the system, and were conflicting with the NViDIA ones.

Regards
Iain

I was going through your howto earlier today, nice work. 

I believe I'd added the step to uninstall the Ubuntu drivers in the instructions I'd given
```
sudo apt-get --purge remove nvidia-glx* nvidia-settings nvidia-kernel-common
```

This wouldn't have affected the nv drivers though, and from your howto, it seems that could be a problem for some. Is that what you meant here?

---

### Post by ibuclaw on 2009-04-25
> **balaknair said:**
> I was going through your howto earlier today, nice work. 

I believe I'd added the step to uninstall the Ubuntu drivers in the instructions I'd given
```
sudo apt-get --purge remove nvidia-glx* nvidia-settings nvidia-kernel-common
```

This wouldn't have affected the nv drivers though, and from your howto, it seems that could be a problem for some. Is that what you meant here?

The xorg-nv driver only affected a minority of cards.
I actually meant the apt-get --purge line altogether... I prefer to use what I state in the howto.
either:
```
sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')
```
or
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
As that will ensure everything is gone, including those that may not have been matched by yours.

Also, I've just noticed this:
> The installer will offer a few options, just stick with the defaults, except for the last one where it asks if you want it to configure xorg- the default option is 'No', choose 'Yes'
This is probably where it failed. You should never let the NViDIA installer reconfigure the xorg.conf file unless you are prepared to edit it afterwards. ;)

Regards
Iain

---

### Post by balaknair on 2009-04-25
> **tinivole said:**
> The xorg-nv driver only affected a minority of cards.
I actually meant the apt-get --purge line altogether... I prefer to use what I state in the howto.
either:
```
sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')
```
or
```
sudo aptitude purge $(dpkg -l | grep nvidia | awk '{print $2}')
```
As that will ensure everything is gone, including those that may not have been matched by yours.

Also, I've just noticed this:

This is probably where it failed. You should never let the NViDIA installer reconfigure the xorg.conf file unless you are prepared to edit it afterwards. ;)

Regards
Iain

Hmmm.
Point noted.

About the xorg.conf though, I've usually had better results with letting the installer configure xorg.conf(especially when it's practically empty as in OP's case), but yeah, I sometimes have to edit it myself afterwards. In most cases though, I've just needed to run *gksudo nvidia-xconfig* to get things just right. I guess it's a case of YMMV.

---

### Post by jbfriend on 2009-04-25
> **gewitty said:**
> I also have a problem with the installation of the driver for an Nvidia card.

This is on a new system which I am currently setting up, using 8.10.

I have tried both the 177 and 180 drivers (as recommended above) but without success. With the 177 driver, I seem to get full graphics capability, as Compiz effects seem to work. But I cannot access any screen resolution above 640x480. When I tried the 180 driver, the system failed during boot and wanted to revert to low graphics mode. I checked the Xorg log and found that the problem appears to be a failure to recognise the monitor. This was the log output:

The :0.log was as follows:

6070 5811
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dave-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Apr 22 22:32:47 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
error setting MTRR (base = 0xeb000000, size = 0x00e00000, type = 1) Invalid argument (22)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
6070 5811


The Xorg.0 log was as follows:

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux dave-desktop 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Apr 22 22:32:45 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation unknown chipset (0x065b) rev 161, Mem @ 0xec000000/16777216, 0xd0000000/268435456, 0xea000000/33554432, I/O @ 0x0000bf00/128, BIOS @ 0x????????/524288
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.11  Wed Nov 26 11:17:21 PST 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.11  Wed Nov 26 10:59:18 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(EE) No devices detected.

Fatal server error:
no screens found


The Xorg.conf file reads:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



The monitor perform OK in the default Ubuntu driver setup (is this Open GL?). However, if I go into the screen resolution settings, the screen is shown as 'unknown' and I can only change the resolution. The refresh rate option is fixed at 0Hz and clicking on 'Detect Displays' has no effect at all.

Am I right in concluding that the problem is not with the Nvidia driver(s), but with the recognition of the monitor (this is a 19" edge 10, model W193)?

-------

the Nvidia driver 180 works super on my Ubuntu 8.10 installation with 2 Samsung 21.5 monitors running at 1920 x 1080 x 60 resolution in TwinView.

i had to copy the X Server Display Configuration > Save to X Configuration File > Show Preview (xorg.conf) as my system would not let me save that thru the above. i then replaced the old xorg.conf with the copy made that way.

my Nvidia card is model 7300 with 256 MB of RAM.

jack
PS: my desktop is about 40 inches wide

---

### Post by jbfriend on 2009-04-25
> **gewitty said:**
> Thanks for the driver installation ideas, but it now appears that the driver problem may not be with the Nvidia graphics card (I installed the latest driver version, 180, as you suggested, with no improvement), but with the monitor.

Having spoken to the PC supplier and the monitor manufacturer, both seem to think that the issue is that Nvidia cannot find a driver for the screen and therefore does not recognise it.

The monitor is an edge10 W193. I've had a quick look around, but so far have not been able to find a Linux driver for this model. edge10 tech support do not supply one and they suggested that I try the Nvidia web site, where they thought I would find one. However, that does not seem to be the case.

I posted a query on the Nvidia forum, but have had no replies yet.

Any ideas on where I go from here?

------


are you sure you have the Nvidia driver installed? do you see NVIDIA X server settings in the System>Administration menu?

if yes then click on NVIDIA and configure it. remember that you will have to copy the configuration file (xorg.conf) that NVIDIA shows you and replace the xorg.conf with that copy. on my system the NVIDIA configuration could not save. (permissions)

if you don't see NVIDIA X server settings then Nvidia is not installed.

go to System>Administration>Hardware drivers to see if Nvidia's preferred driver (180) is there. otherwise you will have to install as noted in other querries on this forum.

jack

---

### Post by gewitty on 2009-04-26
Thanks for all the overnight thoughts.

I'll work my way through all the suggestions and decide what route to take before I do a complete re-install.

I did check to see if the NVIDIA Xserver settings had appeared in the Admin menu and it has. I ran the xorg.conf option and it saved properly. Sadly, it had no effect. When I rebooted, the system just dropped back into low graphics mode again.

Stubborn little gnome, isn't it? :twisted:

---

### Post by gewitty on 2009-04-27
Just as an update (if anyone is still tracking this saga); I eventually did a complete re-installation of the OS. Before I added anything to the system I checked the monitor settings. It appeared as 'unrecognised', but the resolution was correct at 1440x900 16:10. I then tried the recommended graphics driver (177)in the Hardware Drivers utility. When this was installed and I rebooted I found that the graphics card appeared to be working (all Compix effects enabled), but the monitor was still unrecognised and limited to a maximum resolution of 640x480 4:3. The same thing happened when I tried the manual install of the 180 driver, recommended by Balaknair.

So I'm back to square one. I can have the correct screen resolution _or_ a working graphics card - but not both.

Given that we know the screen is capable of running at 1440x900, is there no way I can force this via some terminal command(s), or through the NVIDIA manager, or is it only addressable via the Screen Resolution utility?

---

### Post by balaknair on 2009-04-27
You can edit xorg.conf and add the resolution option there.

A (relatively) safe way to do this is to run the nVidia settings applet and do as jbfriend suggests(set resolution> click 'save to xorg.conf'> click 'show preview'> copy the contents seen in the preview> open xorg.conf> paste the contents into the xorg.conf file(replacing the earlier contents> save and exit)

Note:
* Hit Alt-F2--> *gksudo gedit /etc/X11/xorg.conf* to open xorg.conf in the text editor with root privileges(you won't be able to save changes otherwise).

* You should make a backup of your existing xorg.conf before making any changes
In a terminal--> *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup*

  To restore the backup in case something goes wrong
*sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf*

---

### Post by balaknair on 2009-04-27
You can also add stuff manually to the xorg.conf file if you know the settings for your monitor, but I'd suggest you try that only if the above method doesn't work.

---

### Post by gewitty on 2009-04-27
That was interesting. When I tried to run the NVIDIA X Server, I got a message saying, 'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root, and restart the server.'

When I tried this, this is what I got:


dave@dave-desktop ~ $ sudo nvidia-xconfig
[sudo] password for dave: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

dave@dave-desktop ~ $ 


Does that offer any new clues?

---

### Post by balaknair on 2009-04-27
What does the new xorg.conf file say?

What we basically need in there is
1) 'nvidia' in the device section
2) 1440 x 900 modeline in the Screen section(subsection> display)

so that you get to use the nvidia drivers with the 1440 x 900 resolution.

---

### Post by gewitty on 2009-04-27
I'll try installing the driver again. One odd thing I noticed is that when the driver is active and I reboot, the NVIDIA X server option disappears from the menu.

I'll try again now.

---

### Post by gewitty on 2009-04-27
The 'nvidia' bit appears OK in the Device section, but, as you can see below, the Screen section looks wrong:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by balaknair on 2009-04-27
Is that how it looks after you adjust the resolution with nvidia settings?

---

### Post by gewitty on 2009-04-27
No, that's how it looked after I installed the driver and before a reboot. I am not able to make any changes to the resolution through the NVIDIA server, because of the warnings that came up (see my previous post). All that shows up is an initial Settings panel with the following tickbox options:

Enable Tooltips (ticked)
Display Staus Bar (ticked)
Slider Text Entries (ticked)
Include X Display Names In The Config File (not ticked)
Show "Really Quit?" Dialogue (ticked)

Below that is a button, 'Save Current Configuration', plus a Help and a Quit button. So this is just a set-up screen for the real Settings utility.

If I run sudo nvidia-xconfig in a terminal, then it reconfigures to:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Tue Nov  4 17:18:57 PST 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Immediately following this, the NVIDIA Server option disappears from the menu.

---

### Post by balaknair on 2009-04-27
Normally, once you have installed the driver and restarted the system, you ought to be able to open nvidia settings(alt-F2> *gksudo nvidia-settings*) and set the resolution there under XServer Display Information. Then save the settings to xorg.conf.

If that doesn't seem to be working, we can edit xorg.conf manually(if the nvidia settings app doesn't detect the correct resolutions). To do that however we have to know the correct parameters for your monitor(resolution, horizontal refresh rate, vertical refresh rate, etc), this should be available along with the manual provided by the manufacturer.

Then go to this page
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Enter the parameters in the appropriate boxes, and click the 'Calculate Modeline' button.
This will generate a line like
```
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
```

Copy paste this line into xorg.conf in the 'Monitor' section so that it looks something like this
```
Section "Monitor"
Identifier "Configured Monitor"
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection
```

Next, in the Screens section, add this mode to subsection 'Display'
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
        Depth        24
        Modes      "1440x900@60"
    EndSubSection

EndSection
```

You can also add a line to set a preferred mode line to the 'Monitor' section thus
```
Option          "PreferredMode" "1440x900@60"
```

Save the file and exit. Restart X by logging out and back in.

As always, make a backup of xorg.conf(the one which works best) before making changes(you can have multiple backups- named backup1, 2, 3 and so on).

Try this carefully(no typos, copy paste wherever possible, and make backups as described earlier).

---

### Post by gewitty on 2009-04-28
This is really starting to annoy me. I've tried every which way to get this thing working and it STILL refuses to cooperate!

Right. Here's what I currently have:

A completely fresh installation of 9.04
NVIDIA 180 driver enabled
xorg.conf set up as follows:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline        "1440x810@60" 95.28 1440 1472 1832 1864 810 826 834 851
	Option          "PreferredMode" "1440x900@60"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth           24
		Modes           "1440x900@60"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Result: Same as before. The graphics card seems to be enabled OK and I have Compiz effects working. However, the screen resolution is stuck at 640x480 4:3. If I uninstall the driver, the screen resolution reverts to 1440x900 16:10. 

Does the message at the top of the xorg.conf file have any bearing on the fact that the graphics card seems to be ignoring the settings? This says:

# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.

If so, then maybe the NVIDIA server set-up screen is the only place where things can be changed. If I go to the X Screen 0 options in there, I see the following:

Layout
(hidden because the screen height is less than 600 pixels)
Display
Model:           DFP-0 (DFP-0 on GPU-0)
Configuration:   Separate X screen
Resolution:      Auto (the max setting in the drop-down options here 
                 is 640x480)

The Detect Displays button has no effect.

Are we running out of ideas? This surely has to be something to do with the hardware, otherwise there would be loads of other reports on the forum. I can't be the only one running this particular combination of screen and graphics card.

---

### Post by balaknair on 2009-04-28
[I]Section "Monitor"
Identifier "Configured Monitor"
Modeline "**1440x810@60**" 95.28 1440 1472 1832 1864 810 826 834 851
Option "PreferredMode" "1440x900@60"
EndSection[/I]


I believe the modeline should match the preferred mode.
Could you just try changing that to "1440x900@60"(you might need to change the rest of the modeline too; use the modeline generator on the webpage link I mentioned earlier) and log off and log in again?

Maybe that will make a difference(nothing to lose anyway).

BTW, changing stuff at the nvidia-settings applet doesn't matter, since those changes will need to be saved to xorg.conf anyway(the nvidia drivers still use xorg.conf settings, whereas (I think) the xorg.conf method has been deprecated in most recent open source drivers).

---

### Post by gewitty on 2009-04-28
For some reason, the Modeline generator will only accept either 1440x810 or 1600x900. If I try entering the actual resolution of my screen, it forces one of these two options.

I tried using the 1440x810 modeline, but with no effect.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline 	"1440x810@60" 95.28 1440 1472 1832 1864 810 826 834 851
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
SubSection "Display"
        Depth           24
        Modes           "1440x810@60"
EndSubSection

EndSection

---

### Post by balaknair on 2009-04-28
Try this(what I got with the parameters 1440x900, 60Hz, 16/10 ratio).

Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946


Right now I'm not sure if this just a flaky nVidia driver that's the issue here. Something seems out of place, not sure what.
Will do some more digging around, and post here if I can come up with something.

If nothing seems to work, the way I see it, you have two options:
1) Try the nv drivers(the open sourced drivers)- you won't get 3D and hardware acceleration, but it ought to give you the proper resolution and be stable. You'll be able to use metacity compositing and xcompmgr to use stuff like docks and screenlets.
2) Try the nVidia beta drivers(185)- they're not all that stable, and there's absolutely no guarantee that they'll solve your problem, but some people seem to have found that it fixes some issues with the newer cards. I wouldn't recommend this on your primary PC, it's pretty much a shot in the dark and risky. Beta drivers are to tried only if you - know what you're doing, and/or have nothing to lose, and/or are desperate. If you do want to give it a shot, there's a thread here by tinivole(posted in this thread earlier)  
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

All the best, buddy.

---

### Post by gewitty on 2009-04-28
Thanks balaknair.You have the patience of Gandhi himself (and he was a pretty patient guy).

I tried that last modeline, again with no improvement, so I guess we've run out of ideas.

One last thing I did notice, quite by chance, was that when using Nautilus just now, I got this message:

** (nautilus:4217): WARNING **: Unable to add monitor: Operation not supported

It may mean nothing, or just be because the NVIDIA driver is not installed currently.

Once again, thanks for all the time and help. If I ever get this fixed, I'll post here with the solution.

---

### Post by balaknair on 2009-04-28
"** (nautilus:4217): WARNING **: Unable to add monitor: Operation not supported"

Not quite sure where that came from, don't recall seeing that one before.

Like I said earler, I'll try searching around a bit, there's tons of documentation out there, and I just might get lucky. I'll also have a look at Debian, Arch and OpenSuse forums, most of what I found so far is stuff that we've already tried or stuff that I just didn't understand(or too complicated like compiling a new customized kernel). Will post back soon as I hit something that looks feasible.

In the meantime, wish you luck.

---

