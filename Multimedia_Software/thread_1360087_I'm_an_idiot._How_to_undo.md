---
title: "I'm an idiot. How to undo?"
date: 2009-12-20
forum: Multimedia Software
---

### Post by schmutztaucher on 2009-12-20
I was trying to upgrade my video cards drivers and mudded up my system. I use an ATI Mobility Radeon X1400. What I did was install EnvyNG (gtk and core). I then preceded to go to the terminal and typed in ```
envyng -t
``` I then chose to unistall my ATI driver then it said to do a restart. so I did. upon reboot I got a message saying that i needed to login in low resolution method. I came back in the terminal  and this time I chose to install the ATI driver. There was only one choice (8.660-0ubuntu4) which didn't say it was supported nor recommended. Like an idiot I installed it and rebooted. It again asked if I wanted to go into low graphics mode (just this time or load saved config -which i don't have). Now what is happening is my other monitor isn't detected and avant windows manager isnt working saying the screen isn't composited.

I guess I want to know how to get back to what I had but I don't know if it was a default or what. I am  new to Ubuntu and have limited knowledge. If you need log files just ask but be clear on which ones as. Any help would be greatly appreciated.

---

### Post by Yellow Pasque on 2009-12-20
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by schmutztaucher on 2009-12-20
I tried the link but to no avail. I do have dual monitors but i don't think it makes a difference i just want the generic back. here are some of my logs and an error screen...

When i start up a error message box says Ubuntu is running in low graphics mode
(EE) failed to load module "fglrx" (module doesn't exist)
(EE) no drivers available
----------------------------------(denotes new log)

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Ubuntu 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=ec75ee55-919f-497f-bd82-6445f027146f ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 20 14:28:50 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Configured Screen Device" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Configured Screen Device".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:7145:1028:2003 ATI Technologies Inc Radeon Mobility X1400 rev 0, Mem @ 0xd0000000/268435456, 0xefdf0000/65536, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(==) AIGLX enabled
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
(WW) Warning, couldn't open module fglrx
(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
----------------------------------------------

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
----------------------------------------
Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Virtual    2304 768
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

---

### Post by Yellow Pasque on 2009-12-20
Your xorg.conf is still trying to load fglrx
```
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.back
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by schmutztaucher on 2009-12-20
That did the trick. Thanks a bunch

Im guessing it didn't work the first time through because I didn't use ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` 

Is there a reason why fglrx didn't work in this instance? Isn't fglrx Linux's display driver used for ATI Radeon?

---

### Post by Yellow Pasque on 2009-12-20
The last version to support your card was Catlayst 9-3, which doesn't work in newer Ubuntu versions (because they use recent X servers).

---

