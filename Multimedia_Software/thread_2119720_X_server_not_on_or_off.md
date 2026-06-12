---
title: "X server not on or off?"
date: 2013-02-24
forum: Multimedia Software
---

### Post by trump600 on 2013-02-24
Hello all, and thanks for looking into this.  I'm a fairly new Ubuntu user, so please have a little patience with me.  I was attempting to install NVidea drivers for a GTX660, and learned that I needed to disable X server before the drivers would install.

After multiple attempts, I believe that I disabled it, but I'm in a very weird place now.  When I try to install the driver via the command screen (Crtl+Alt+F1), NVidea continues to tell me that I need to disable the X server.  However, my GUI crashes and takes me back to the login screen (Ctrl+Alt+F7) every time I try to log in.  From what I've read, it's likely due to the X server crashing. 

So according to NVidea, X server is running, but it doesn't seem like it is.  Now I don't know where to go next.  Please let me know what other information I can post to help you help me.

Thanks,
Trump

---

### Post by gordintoronto on 2013-02-24
I think you have been misinformed. This is from memory, so it might not be perfect: in the latest Ubuntu, run Software Centre, select Software Sources, Additional Drivers will appear as an option. Choose nvidia-current.

When the x-server is disabled, your entire screen is text only.

If you continue to struggle with this, tell us what version of Ubuntu you are using.

---

### Post by Yellow Pasque on 2013-02-24
Always use the repository when possible. Do not download nvidia drivers directly from nvidia's site (this isn't Windows).

---

### Post by trump600 on 2013-02-25
> **gordintoronto said:**
> I think you have been misinformed. This is from memory, so it might not be perfect: in the latest Ubuntu, run Software Centre, select Software Sources, Additional Drivers will appear as an option. Choose nvidia-current.

When the x-server is disabled, your entire screen is text only.

If you continue to struggle with this, tell us what version of Ubuntu you are using.

Thanks for the reply.  I tried to take your advice and run the Software Center, but my problem is that I can't get anything that requires a display to open up:  

Invalid MIT-MAGIC-COOKIE-1 key
** (software-center:2531): WARNING **: Could not open X display
Traceback (most recent call last):
   File "/usr/bin/software-center", line 25, in <module>
     from gi.repository import Gtk, GObject
   File "/usr/lib/python2.7/dist-packages/gi/importer.py", line 76, in load_module
     dynamic_module._load()
   File "usr/lib/python2.7/dist-packages/gi/module.py", line 244, in _load
     overrides_modules = __import__('gi.overrides', fromlist=[self._namespace])
   File "/usr/lib/python2.7/dist-packages/gi/overrides/Gtk/py", line 1624, in <module>
     raise RuntimeError("Gtk couldn't be initialized")
RuntimeError: Gtk couldn't be initialized

That is the error message I get when I try to run the Software Center from the terminal (black and white screen with text only).  Please forgive any typos, as I typed that manually from looking at the screen.

I am running Ubuntu 12.10 (GNU/Linux 3.5.0-17-generic x86_64).

So it seems that my X server is partially disabled or something to that effect, because it's still running, but it's not working.  My screen isn't only text when I boot up; I still get the nice looking login screen with my desktop background-- I just can't actually login to my desktop because it keeps kicking me back to that login screen.

I hope this helps diagnose my real problem, as I'm not even really worried about the Nvidea drivers right now (although that's the end goal).  I'm really just worried that I broke something :eek: and can't access anything in my GUI/desktop area.

---

### Post by trump600 on 2013-02-25
> **Temüjin said:**
> Always use the repository when possible. Do not download nvidia drivers directly from nvidia's site (this isn't Windows).

I won't deny that I'm a humble novice with much to understand.  I'll take this one as a lesson learned and hope I can fix my mistake(s).  Thank you for the tip :D

---

### Post by matt_symes on 2013-02-25
Hi

I would purge the drivers you installed as X cannot start.

[http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

And then install them from the software center.

How did you install them, What guide you follow ?

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> Hi

I would purge the drivers you installed as X cannot start.

[http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)

And then install them from the software center.

How did you install them, What guide you follow ?

Kind regards

Installation of the drivers I tried to install always failed because Nvidea complained that X server was running, so I have no drivers to purge.  I attempted many ways to disable X server.  I was searching for solutions on my Ubuntu machine, so my web history is currently unavailable, but the following guide seems to sum up the routes I tried to take.

[http://theos.in/news/ubuntu-linux-shutdown-the-x-server/](http://theos.in/news/ubuntu-linux-shutdown-the-x-server/) 

When typing sudo /etc/init.d/gdm stop   the command was not found.  Maybe I'm just not running it correctly to begin with?

The only other thing I tried, and out of frustration I might add, was xstop, after seeing guides on starting X server mention the xstart command.  I don't remember if it did anything or not.

Edit:
Just to be sure, I ran your guide for removing NVidia, but nothing was removed.  

Package 'xxxx' is not installed, so not removed.

0 upgraded, 0 newly installed, 0 to remove and 93 not upgraded

---

### Post by matt_symes on 2013-02-25
Hi

That's good that you did not install the drivers. Let's tackle your other issue the.

> Invalid MIT-MAGIC-COOKIE-1 keyFrom a console (ctl + alt + f2) . Log into your account

```
rm ~/.Xauthority
``````
sudo reboot
```Post back on efficacy.

> When typing sudo /etc/init.d/gdm stop   the command was not found. Ubuntu now uses lightdm. That's the problem with following internet guides. Ubuntu changes and you have to make sure you get an up to date guide to follow.

xstop is not a command so will have done nothing.

```
matthew-S206:/home/matthew/fxp % xstop
zsh: correct 'xstop' to 'stop' [nyae]? n
zsh: command not found: xstop
matthew-S206:/home/matthew/fxp %
```

Kind regards

---

### Post by deadflowr on 2013-02-25
Killing X in Ubuntu is a little different than other systems (and even older Ubuntu versions)
To kill X in Ubuntu:
```
sudo service lghtdm stop
```

Ubuntu uses lightdm, as opposed to gdm. (Or as is the case with Kubuntu, kdm)

When done, run:

```
sudo service lightdm start
```

This will restart X and drop you back at the login screen.

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 
From a console (ctl + alt + f2) . Log into your account

```
rm ~/.Xauthority
``````
sudo reboot
```Post back on efficacy.


I have a GUI again.  Thank you so much.  Can you help me tackle the correct installation of the driver, since I've been reading dated material?

---

### Post by matt_symes on 2013-02-25
Hi

That's great news :)

Please post the output of

```
lspci -nnk | grep -iA3 vga
```

The above command is case sensitive so a captial A

I just want to take a look at your graphics card and driver.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> Hi

That's great news :)

Please post the output of

```
lspci -nnk | grep -iA3 vga
```

The above command is case sensitive so a captial A

I just want to take a look at your graphics card and driver.

Kind regards

I would like to install the driver for a GPU that is not currently connected.  I assume I should put it in first?

---

### Post by matt_symes on 2013-02-25
Hi

Yep. Put it in and disable any onboard graphics in the BIOS.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> Hi

Yep. Put it in and disable any onboard graphics in the BIOS.

Kind regards

Looks like I have a boot order option that is defaulting to the new GPU.  Seems like I can't actually disable the onboard because it's not being used?  That said, I haven't changed anything in my BIOS, but some funny things are happening now.  Upon booting, I'm now prompted to choose a boot method of some kind.  The top of the screen reads GNU GRUB version 2.00-7ubuntu11  Choices are:

Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

I chose Ubuntu.  When I get to my login screen, and everything looks perfectly normal.  However, after logging in to run your command, the screen has a lot of digital distortion; I can see that it's my desktop, but very corrupted.  Before yesterday, I had the GPU installed for about a week(without the drivers of course) without any problems.  Any ideas?

Anyway, I used the console (ctrl+alt+F2) and typed the command.  My manual typing of what came back:

```

01:01.0 VGA compatible controller [0300]: ASPEED Technology, Inc. ASPEED Graphics Family [1a03:2000] (rev 10)
Subsytem: ASPEED Technology, Inc. ASPEED Graphics Family [1a03:2000]
01:02.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW322/323 [TrueFire] 1394a
Controller [11c1:5811] (rev 70)
Subsytem: ASUSTeK Computer Inc. Device [1043:8259]
--
02.00.0 VGA compatible controller [0300]: NVIDIA Corporation Device 010de:11c0] (rev a1)
Subsystem eVga.com. Corp. Device [3842:2662]
Kernel modules: nouveau, nvidiafb
02:00.1 Audio device [0403]: NIVIDIA Corporation Device [10de:0e0b] (rev a1)
Subsystem eVga.com. Corp. Device [3842:2662]
Kernel driver in use: snd_hda_intel
03:00.0 Ethernet controller [0200]: Intel Corporation 82574L GIgabit Network Connection [8086:10d3]

```
Thank you for your patience and staying with me here.  Your constant help is not going to go unrewarded.

---

### Post by matt_symes on 2013-02-25
Hi

Don't worry. Post when your ready.

> 02.00.0 VGA compatible controller [0300]: NVIDIA Corporation Device 010de:11c0] (rev a1) 
Subsystem eVga.com. Corp. Device [3842:2662] 
Kernel modules: nouveau, nvidiafbI assume this is the card ? Interestingly it does not specify the driver it is currently using.

Can you post the output of this command

```
sudo lshw -c display
```Enter your password. it will not be displayed to the screen. It will give us more information.

Kind regards

---

### Post by trump600 on 2013-02-25
Updated

---

### Post by trump600 on 2013-02-25
I can't seem to scroll up to see the whole output, but here's what's on the screen:
```

product: NVIDIA Corportation
vendor: NVIDIA Corportation
physical id: 0
bus info: pci@0000:02:00.0
version: a1
width: 64 bits
clock: 33MHz
compatibilities: pm msi pciexpress vga_controller vus_master cap_list
configuration: latency=0
resources: memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:cc00(size=128) memory:fbc000000-fbc7ffff
*-display UNCLAIMED
description: VGA compatible controller
product: ASPEED Graphics Family
vendor: ASPEED Technology, Inc.
physical id: 1
bus info: pci@-0000:01:01.0
version: 10
width: 32bits
clock:33MHz
capabilities: pm vga_controller cap_list
configuration: latency=0
resources: memory:f9000000-f97fffff memory:f9fc0000-f9fdffff ioport:bc00(size=128)
```

---

### Post by matt_symes on 2013-02-25
Hi

Well it is using the nvidia card but it is not specifying what driver it's using for it. That is quite possibly the reason you are seeing distortion.

This log file may shed some clues and you can post it if you like.

```
/var/log/Xorg.0.log
```

I think the card is quite old ?

Lets try using the nouveau driver to start with.

```
echo nouveau | sudo tee -a /etc/modules
```

```
sudo reboot
```

Kind regards

---

### Post by trump600 on 2013-02-25
removed

---

### Post by matt_symes on 2013-02-25
Hi 

Check out my last post as we just cross posted. Let's try the open source driver first because to known to work with older cards.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 
This log file may shed some clues and you can post it if you like.

```
/var/log/Xorg.0.log
```



permission denied. when I run with sudo, command not found

> **matt_symes said:**
> 
I think the card is quite old ?

Lets try using the nouveau driver to start with.

```
echo nouveau | sudo tee -a /etc/modules
```

```
sudo reboot
```

Kind regards

I didn't think it was too old of a card, but that's all relative.  The driver did not help the distortion.  I posted the GPU earlier but removed it.  Here it is again with hopes that it helps: NVidia EVGA GeForce GTX660

---

### Post by matt_symes on 2013-02-25
Hi

Sorry it should have been

```
gedit /var/log/Xorg.log
```

> I didn't think it was too old of a card, but that's all relative.  

The  driver did not help the distortion. 
Did it load it ?

Can you post the out of

```
sudo lshw -c display
```

> I posted the GPU earlier but  removed it.  Here it is again with hopes that it helps: NVidia EVGA  GeForce GTX660

Alot newer than i though.

we'll install  the nvidia  soon. I'm just trying to find out if there are other things we need to fix first, hence the log file.

Please be patient.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> Hi

Please be patient.



Very patient.  Really, I'm just so grateful that you're being so patient with me as well :D

I'll post up the outs in a minute.

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 
Sorry it should have been

```
gedit /var/log/Xorg.log
```


The log is empty.

> **matt_symes said:**
> 

Can you post the out of

```
sudo lshw -c display
```



```

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:d8000000-dfffffff memory:d6000000-d7ffffff ioport:cc00(size=128) memory:fbc00000-fbc7ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: ASPEED Graphics Family
       vendor: ASPEED Technology, Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller cap_list
       configuration: latency=0
       resources: memory:f9000000-f97fffff memory:f9fc0000-f9fdffff ioport:bc00(size=128)

```

---

### Post by matt_symes on 2013-02-25
Hi

It should be
```
gedit /var/log/Xorg.0.log
```I think i need some coffee :D

Kind regards

---

### Post by matt_symes on 2013-02-25
Hi

It did not load the driver. Lets try with nvidias drivers.

open additional drivers (type into the dash) and select the nvidia-current driver.

I've just checked and the card is supported.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> ]I think i need some coffee :D

I'm in the same boat.  Late night at work and have to be back in about 3 hours.  Decided to plow through the night and just be tired.  Sun should be coming up soon.

```

[    11.547] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    11.547] X Protocol Version 11, Revision 0
[    11.547] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[    11.547] Current Operating System: Linux BTCraft 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    11.547] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=0dc14cc5-b547-4690-a366-e57fe78e9ecb ro quiet splash vt.handoff=7
[    11.547] Build Date: 27 November 2012  07:44:35AM
[    11.547] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see http://www.ubuntu.com/support) 
[    11.547] Current version of pixman: 0.26.0
[    11.547] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    11.547] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.547] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 25 05:25:55 2013
[    11.676] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.676] (==) No Layout section.  Using the first Screen section.
[    11.676] (==) No screen section available. Using defaults.
[    11.676] (**) |-->Screen "Default Screen Section" (0)
[    11.676] (**) |   |-->Monitor "<default monitor>"
[    11.677] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    11.677] (==) Automatically adding devices
[    11.677] (==) Automatically enabling devices
[    11.677] (==) Automatically adding GPU devices
[    11.677] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.677] 	Entry deleted from font path.
[    11.677] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.677] 	Entry deleted from font path.
[    11.677] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.677] 	Entry deleted from font path.
[    11.677] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.677] 	Entry deleted from font path.
[    11.677] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.677] 	Entry deleted from font path.
[    11.677] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    11.677] 	Entry deleted from font path.
[    11.677] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    11.677] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.677] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.677] (II) Loader magic: 0x7fe4b8e55c40
[    11.677] (II) Module ABI versions:
[    11.677] 	X.Org ANSI C Emulation: 0.4
[    11.677] 	X.Org Video Driver: 13.0
[    11.677] 	X.Org XInput driver : 18.0
[    11.677] 	X.Org Server Extension : 7.0
[    11.679] (--) PCI:*(0:1:1:0) 1a03:2000:1a03:2000 rev 16, Mem @ 0xf9000000/8388608, 0xf9fc0000/131072, I/O @ 0x0000bc00/128
[    11.679] (--) PCI: (0:2:0:0) 10de:11c0:3842:2662 rev 161, Mem @ 0xfa000000/16777216, 0xd8000000/134217728, 0xd6000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    11.679] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.679] Initializing built-in extension Generic Event Extension
[    11.679] Initializing built-in extension SHAPE
[    11.679] Initializing built-in extension MIT-SHM
[    11.679] Initializing built-in extension XInputExtension
[    11.679] Initializing built-in extension XTEST
[    11.679] Initializing built-in extension BIG-REQUESTS
[    11.679] Initializing built-in extension SYNC
[    11.679] Initializing built-in extension XKEYBOARD
[    11.679] Initializing built-in extension XC-MISC
[    11.679] Initializing built-in extension SECURITY
[    11.679] Initializing built-in extension XINERAMA
[    11.679] Initializing built-in extension XFIXES
[    11.679] Initializing built-in extension RENDER
[    11.679] Initializing built-in extension RANDR
[    11.679] Initializing built-in extension COMPOSITE
[    11.679] Initializing built-in extension DAMAGE
[    11.679] Initializing built-in extension MIT-SCREEN-SAVER
[    11.679] Initializing built-in extension DOUBLE-BUFFER
[    11.679] Initializing built-in extension RECORD
[    11.679] Initializing built-in extension DPMS
[    11.679] Initializing built-in extension X-Resource
[    11.679] Initializing built-in extension XVideo
[    11.679] Initializing built-in extension XVideo-MotionCompensation
[    11.679] Initializing built-in extension XFree86-VidModeExtension
[    11.679] Initializing built-in extension XFree86-DGA
[    11.679] Initializing built-in extension XFree86-DRI
[    11.679] Initializing built-in extension DRI2
[    11.679] (II) LoadModule: "glx"
[    11.780] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.780] (II) Module glx: vendor="X.Org Foundation"
[    11.780] 	compiled for 1.13.0, module version = 1.0.0
[    11.780] 	ABI class: X.Org Server Extension, version 7.0
[    11.780] (==) AIGLX enabled
[    11.780] Loading extension GLX
[    11.781] (==) Matched ast as autoconfigured driver 0
[    11.781] (==) Matched vesa as autoconfigured driver 1
[    11.781] (==) Matched modesetting as autoconfigured driver 2
[    11.781] (==) Matched fbdev as autoconfigured driver 3
[    11.781] (==) Assigned the driver to the xf86ConfigLayout
[    11.781] (II) LoadModule: "ast"
[    11.781] (WW) Warning, couldn't open module ast
[    11.781] (II) UnloadModule: "ast"
[    11.781] (II) Unloading ast
[    11.781] (EE) Failed to load module "ast" (module does not exist, 0)
[    11.781] (II) LoadModule: "vesa"
[    11.781] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.781] (II) Module vesa: vendor="X.Org Foundation"
[    11.781] 	compiled for 1.12.99.902, module version = 2.3.2
[    11.781] 	Module class: X.Org Video Driver
[    11.781] 	ABI class: X.Org Video Driver, version 13.0
[    11.781] (II) LoadModule: "modesetting"
[    11.782] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.782] (II) Module modesetting: vendor="X.Org Foundation"
[    11.782] 	compiled for 1.13.0, module version = 0.5.0
[    11.782] 	Module class: X.Org Video Driver
[    11.782] 	ABI class: X.Org Video Driver, version 13.0
[    11.782] (II) LoadModule: "fbdev"
[    11.782] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.782] (II) Module fbdev: vendor="X.Org Foundation"
[    11.782] 	compiled for 1.12.99.902, module version = 0.4.3
[    11.782] 	Module class: X.Org Video Driver
[    11.782] 	ABI class: X.Org Video Driver, version 13.0
[    11.782] (==) Matched ast as autoconfigured driver 0
[    11.782] (==) Matched vesa as autoconfigured driver 1
[    11.782] (==) Matched modesetting as autoconfigured driver 2
[    11.782] (==) Matched fbdev as autoconfigured driver 3
[    11.782] (==) Assigned the driver to the xf86ConfigLayout
[    11.782] (II) LoadModule: "ast"
[    11.782] (WW) Warning, couldn't open module ast
[    11.782] (II) UnloadModule: "ast"
[    11.782] (II) Unloading ast
[    11.782] (EE) Failed to load module "ast" (module does not exist, 0)
[    11.782] (II) LoadModule: "vesa"
[    11.782] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.783] (II) Module vesa: vendor="X.Org Foundation"
[    11.783] 	compiled for 1.12.99.902, module version = 2.3.2
[    11.783] 	Module class: X.Org Video Driver
[    11.783] 	ABI class: X.Org Video Driver, version 13.0
[    11.783] (II) UnloadModule: "vesa"
[    11.783] (II) Unloading vesa
[    11.783] (II) Failed to load module "vesa" (already loaded, 0)
[    11.783] (II) LoadModule: "modesetting"
[    11.783] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.783] (II) Module modesetting: vendor="X.Org Foundation"
[    11.783] 	compiled for 1.13.0, module version = 0.5.0
[    11.783] 	Module class: X.Org Video Driver
[    11.783] 	ABI class: X.Org Video Driver, version 13.0
[    11.783] (II) UnloadModule: "modesetting"
[    11.783] (II) Unloading modesetting
[    11.783] (II) Failed to load module "modesetting" (already loaded, 0)
[    11.783] (II) LoadModule: "fbdev"
[    11.783] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.783] (II) Module fbdev: vendor="X.Org Foundation"
[    11.783] 	compiled for 1.12.99.902, module version = 0.4.3
[    11.783] 	Module class: X.Org Video Driver
[    11.783] 	ABI class: X.Org Video Driver, version 13.0
[    11.783] (II) UnloadModule: "fbdev"
[    11.783] (II) Unloading fbdev
[    11.783] (II) Failed to load module "fbdev" (already loaded, 0)
[    11.783] (II) VESA: driver for VESA chipsets: vesa
[    11.783] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    11.783] (II) FBDEV: driver for framebuffer: fbdev
[    11.783] (++) using VT number 7

[    11.783] (WW) Falling back to old probe method for modesetting
[    11.783] (EE) open /dev/dri/card0: No such file or directory
[    11.783] (EE) open /dev/dri/card0: No such file or directory
[    11.783] (WW) Falling back to old probe method for fbdev
[    11.783] (II) Loading sub module "fbdevhw"
[    11.783] (II) LoadModule: "fbdevhw"
[    11.784] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.784] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.784] 	compiled for 1.13.0, module version = 0.0.2
[    11.784] 	ABI class: X.Org Video Driver, version 13.0
[    11.784] (II) Loading sub module "vbe"
[    11.784] (II) LoadModule: "vbe"
[    11.784] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    11.860] (II) Module vbe: vendor="X.Org Foundation"
[    11.860] 	compiled for 1.13.0, module version = 1.1.0
[    11.860] 	ABI class: X.Org Video Driver, version 13.0
[    11.860] (II) Loading sub module "int10"
[    11.860] (II) LoadModule: "int10"
[    11.860] (II) Loading /usr/lib/xorg/modules/libint10.so
[    11.880] (II) Module int10: vendor="X.Org Foundation"
[    11.880] 	compiled for 1.13.0, module version = 1.0.0
[    11.880] 	ABI class: X.Org Video Driver, version 13.0
[    11.880] (II) VESA(0): initializing int10
[    11.884] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    11.884] (II) VESA(0): VESA BIOS detected
[    11.884] (II) VESA(0): VESA VBE Version 3.0
[    11.884] (II) VESA(0): VESA VBE Total Mem: 8192 kB
[    11.884] (II) VESA(0): VESA VBE OEM: ASPEED
[    11.884] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    11.884] (II) VESA(0): VESA VBE OEM Vendor: ASPEED Technology, Inc.
[    11.884] (II) VESA(0): VESA VBE OEM Product: AST GPU
[    11.884] (II) VESA(0): VESA VBE OEM Product Rev: 0.90.07
[    11.900] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    11.900] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    11.900] (==) VESA(0): RGB weight 888
[    11.900] (==) VESA(0): Default visual is TrueColor
[    11.900] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.900] (II) Loading sub module "ddc"
[    11.900] (II) LoadModule: "ddc"
[    11.900] (II) Module "ddc" already built-in
[    12.086] (II) VESA(0): VESA VBE DDC supported
[    12.086] (II) VESA(0): VESA VBE DDC Level 2
[    12.086] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    13.918] (II) VESA(0): VESA VBE DDC read successfully
[    13.918] (II) VESA(0): Manufacturer: ACI  Model: 23fa  Serial#: 50236
[    13.918] (II) VESA(0): Year: 2012  Week: 36
[    13.918] (II) VESA(0): EDID Version: 1.3
[    13.918] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    13.918] (II) VESA(0): Sync:  Separate
[    13.918] (II) VESA(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[    13.918] (II) VESA(0): Gamma: 2.20
[    13.918] (II) VESA(0): DPMS capabilities: Off; RGB/Color Display
[    13.918] (II) VESA(0): First detailed timing is preferred mode
[    13.918] (II) VESA(0): redX: 0.636 redY: 0.333   greenX: 0.303 greenY: 0.626
[    13.918] (II) VESA(0): blueX: 0.153 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    13.918] (II) VESA(0): Supported established timings:
[    13.918] (II) VESA(0): 720x400@70Hz
[    13.918] (II) VESA(0): 640x480@60Hz
[    13.918] (II) VESA(0): 640x480@67Hz
[    13.918] (II) VESA(0): 640x480@75Hz
[    13.918] (II) VESA(0): 800x600@56Hz
[    13.918] (II) VESA(0): 800x600@60Hz
[    13.918] (II) VESA(0): 800x600@72Hz
[    13.918] (II) VESA(0): 800x600@75Hz
[    13.918] (II) VESA(0): 832x624@75Hz
[    13.918] (II) VESA(0): 1024x768@60Hz
[    13.918] (II) VESA(0): 1024x768@70Hz
[    13.918] (II) VESA(0): 1024x768@75Hz
[    13.918] (II) VESA(0): 1280x1024@75Hz
[    13.918] (II) VESA(0): Manufacturer's mask: 0
[    13.918] (II) VESA(0): Supported standard timings:
[    13.918] (II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    13.918] (II) VESA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    13.918] (II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    13.918] (II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    13.918] (II) VESA(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    13.918] (II) VESA(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    13.918] (II) VESA(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    13.918] (II) VESA(0): #7: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    13.918] (II) VESA(0): Supported detailed timing:
[    13.918] (II) VESA(0): clock: 148.5 MHz   Image Size:  509 x 286 mm
[    13.918] (II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    13.918] (II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    13.918] (II) VESA(0): Serial No: C9LMTF050236
[    13.918] (II) VESA(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 83 kHz, PixClock max 175 MHz
[    13.918] (II) VESA(0): Monitor name: ASUS VS238
[    13.918] (II) VESA(0): EDID (in hex):
[    13.918] (II) VESA(0): 	00ffffffffffff000469fa233cc40000
[    13.918] (II) VESA(0): 	2416010368331d782ad945a2554da027
[    13.918] (II) VESA(0): 	125054b7ef00714f814081809500b300
[    13.918] (II) VESA(0): 	d1c081c08100023a801871382d40582c
[    13.918] (II) VESA(0): 	4500fd1e1100001e000000ff0043394c
[    13.918] (II) VESA(0): 	4d54463035303233360a000000fd0032
[    13.918] (II) VESA(0): 	4b185311000a202020202020000000fc
[    13.918] (II) VESA(0): 	00415355532056533233380a202000b5
[    13.918] (II) VESA(0): EDID vendor "ACI", prod id 9210
[    13.918] (II) VESA(0): Using EDID range info for horizontal sync
[    13.918] (II) VESA(0): Using EDID range info for vertical refresh
[    13.918] (II) VESA(0): Printing DDC gathered Modelines:
[    13.918] (II) VESA(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    13.918] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    13.918] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    13.918] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    13.918] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    13.918] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    13.918] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    13.918] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    13.918] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    13.918] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    13.918] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    13.918] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    13.918] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    13.918] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    13.918] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    13.918] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    13.918] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    13.918] (II) VESA(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    13.918] (II) VESA(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    13.918] (II) VESA(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[    13.918] (II) VESA(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    13.918] (II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    13.918] (II) VESA(0): Searching for matching VESA mode(s):
[    13.919] Mode: 101 (640x480)
[    13.919] 	ModeAttributes: 0x9f
[    13.919] 	WinAAttributes: 0x7
[    13.919] 	WinBAttributes: 0x0
[    13.919] 	WinGranularity: 64
[    13.919] 	WinSize: 64
[    13.919] 	WinASegment: 0xa000
[    13.919] 	WinBSegment: 0xa000
[    13.919] 	WinFuncPtr: 0xc00013f5
[    13.919] 	BytesPerScanline: 640
[    13.919] 	XResolution: 640
[    13.919] 	YResolution: 480
[    13.919] 	XCharSize: 8
[    13.919] 	YCharSize: 16
[    13.919] 	NumberOfPlanes: 1
[    13.919] 	BitsPerPixel: 8
[    13.919] 	NumberOfBanks: 1
[    13.919] 	MemoryModel: 4
[    13.919] 	BankSize: 0
[    13.919] 	NumberOfImages: 24
[    13.919] 	RedMaskSize: 0
[    13.919] 	RedFieldPosition: 0
[    13.919] 	GreenMaskSize: 0
[    13.919] 	GreenFieldPosition: 0
[    13.919] 	BlueMaskSize: 0
[    13.919] 	BlueFieldPosition: 0
[    13.919] 	RsvdMaskSize: 0
[    13.919] 	RsvdFieldPosition: 0
[    13.919] 	DirectColorModeInfo: 0
[    13.919] 	PhysBasePtr: 0xf9000000
[    13.919] 	LinBytesPerScanLine: 640
[    13.919] 	BnkNumberOfImagePages: 24
[    13.919] 	LinNumberOfImagePages: 24
[    13.919] 	LinRedMaskSize: 0
[    13.919] 	LinRedFieldPosition: 0
[    13.919] 	LinGreenMaskSize: 0
[    13.919] 	LinGreenFieldPosition: 0
[    13.919] 	LinBlueMaskSize: 0
[    13.919] 	LinBlueFieldPosition: 0
[    13.919] 	LinRsvdMaskSize: 0
[    13.919] 	LinRsvdFieldPosition: 0
[    13.919] 	MaxPixelClock: 1000000
[    13.920] Mode: 102 (800x600)
[    13.920] 	ModeAttributes: 0x1f
[    13.920] 	WinAAttributes: 0x7
[    13.920] 	WinBAttributes: 0x0
[    13.920] 	WinGranularity: 64
[    13.920] 	WinSize: 64
[    13.920] 	WinASegment: 0xa000
[    13.920] 	WinBSegment: 0xa000
[    13.920] 	WinFuncPtr: 0xc00013f5
[    13.920] 	BytesPerScanline: 100
[    13.920] 	XResolution: 800
[    13.920] 	YResolution: 600
[    13.920] 	XCharSize: 8
[    13.920] 	YCharSize: 16
[    13.920] 	NumberOfPlanes: 4
[    13.920] 	BitsPerPixel: 4
[    13.920] 	NumberOfBanks: 1
[    13.920] 	MemoryModel: 3
[    13.920] 	BankSize: 0
[    13.920] 	NumberOfImages: 0
[    13.920] 	RedMaskSize: 0
[    13.920] 	RedFieldPosition: 0
[    13.920] 	GreenMaskSize: 0
[    13.920] 	GreenFieldPosition: 0
[    13.920] 	BlueMaskSize: 0
[    13.920] 	BlueFieldPosition: 0
[    13.920] 	RsvdMaskSize: 0
[    13.920] 	RsvdFieldPosition: 0
[    13.920] 	DirectColorModeInfo: 0
[    13.920] 	PhysBasePtr: 0xf9000000
[    13.920] 	LinBytesPerScanLine: 100
[    13.920] 	BnkNumberOfImagePages: 0
[    13.920] 	LinNumberOfImagePages: 0
[    13.920] 	LinRedMaskSize: 0
[    13.920] 	LinRedFieldPosition: 0
[    13.920] 	LinGreenMaskSize: 0
[    13.920] 	LinGreenFieldPosition: 0
[    13.920] 	LinBlueMaskSize: 0
[    13.920] 	LinBlueFieldPosition: 0
[    13.920] 	LinRsvdMaskSize: 0
[    13.920] 	LinRsvdFieldPosition: 0
[    13.920] 	MaxPixelClock: 1000000
[    13.920] Mode: 103 (800x600)
[    13.920] 	ModeAttributes: 0x9f
[    13.920] 	WinAAttributes: 0x7
[    13.920] 	WinBAttributes: 0x0
[    13.920] 	WinGranularity: 64
[    13.920] 	WinSize: 64
[    13.920] 	WinASegment: 0xa000
[    13.920] 	WinBSegment: 0xa000
[    13.920] 	WinFuncPtr: 0xc00013f5
[    13.920] 	BytesPerScanline: 800
[    13.920] 	XResolution: 800
[    13.920] 	YResolution: 600
[    13.920] 	XCharSize: 8
[    13.920] 	YCharSize: 16
[    13.920] 	NumberOfPlanes: 1
[    13.920] 	BitsPerPixel: 8
[    13.920] 	NumberOfBanks: 1
[    13.920] 	MemoryModel: 4
[    13.920] 	BankSize: 0
[    13.920] 	NumberOfImages: 15
[    13.920] 	RedMaskSize: 0
[    13.920] 	RedFieldPosition: 0
[    13.920] 	GreenMaskSize: 0
[    13.920] 	GreenFieldPosition: 0
[    13.920] 	BlueMaskSize: 0
[    13.920] 	BlueFieldPosition: 0
[    13.920] 	RsvdMaskSize: 0
[    13.920] 	RsvdFieldPosition: 0
[    13.920] 	DirectColorModeInfo: 0
[    13.920] 	PhysBasePtr: 0xf9000000
[    13.920] 	LinBytesPerScanLine: 800
[    13.920] 	BnkNumberOfImagePages: 15
[    13.920] 	LinNumberOfImagePages: 15
[    13.920] 	LinRedMaskSize: 0
[    13.920] 	LinRedFieldPosition: 0
[    13.920] 	LinGreenMaskSize: 0
[    13.920] 	LinGreenFieldPosition: 0
[    13.920] 	LinBlueMaskSize: 0
[    13.920] 	LinBlueFieldPosition: 0
[    13.920] 	LinRsvdMaskSize: 0
[    13.920] 	LinRsvdFieldPosition: 0
[    13.920] 	MaxPixelClock: 1000000
[    13.921] Mode: 105 (1024x768)
[    13.921] 	ModeAttributes: 0x9f
[    13.921] 	WinAAttributes: 0x7
[    13.921] 	WinBAttributes: 0x0
[    13.921] 	WinGranularity: 64
[    13.921] 	WinSize: 64
[    13.921] 	WinASegment: 0xa000
[    13.921] 	WinBSegment: 0xa000
[    13.921] 	WinFuncPtr: 0xc00013f5
[    13.921] 	BytesPerScanline: 1024
[    13.921] 	XResolution: 1024
[    13.921] 	YResolution: 768
[    13.921] 	XCharSize: 8
[    13.921] 	YCharSize: 16
[    13.921] 	NumberOfPlanes: 1
[    13.921] 	BitsPerPixel: 8
[    13.921] 	NumberOfBanks: 1
[    13.921] 	MemoryModel: 4
[    13.921] 	BankSize: 0
[    13.921] 	NumberOfImages: 9
[    13.921] 	RedMaskSize: 0
[    13.921] 	RedFieldPosition: 0
[    13.921] 	GreenMaskSize: 0
[    13.921] 	GreenFieldPosition: 0
[    13.921] 	BlueMaskSize: 0
[    13.921] 	BlueFieldPosition: 0
[    13.921] 	RsvdMaskSize: 0
[    13.921] 	RsvdFieldPosition: 0
[    13.921] 	DirectColorModeInfo: 0
[    13.921] 	PhysBasePtr: 0xf9000000
[    13.921] 	LinBytesPerScanLine: 1024
[    13.921] 	BnkNumberOfImagePages: 9
[    13.921] 	LinNumberOfImagePages: 9
[    13.921] 	LinRedMaskSize: 0
[    13.921] 	LinRedFieldPosition: 0
[    13.921] 	LinGreenMaskSize: 0
[    13.921] 	LinGreenFieldPosition: 0
[    13.921] 	LinBlueMaskSize: 0
[    13.921] 	LinBlueFieldPosition: 0
[    13.921] 	LinRsvdMaskSize: 0
[    13.921] 	LinRsvdFieldPosition: 0
[    13.921] 	MaxPixelClock: 1000000
[    13.922] Mode: 110 (640x480)
[    13.922] 	ModeAttributes: 0x9b
[    13.922] 	WinAAttributes: 0x7
[    13.922] 	WinBAttributes: 0x0
[    13.922] 	WinGranularity: 64
[    13.922] 	WinSize: 64
[    13.922] 	WinASegment: 0xa000
[    13.922] 	WinBSegment: 0xa000
[    13.922] 	WinFuncPtr: 0xc00013f5
[    13.922] 	BytesPerScanline: 1280
[    13.922] 	XResolution: 640
[    13.922] 	YResolution: 480
[    13.922] 	XCharSize: 8
[    13.922] 	YCharSize: 16
[    13.922] 	NumberOfPlanes: 1
[    13.922] 	BitsPerPixel: 15
[    13.922] 	NumberOfBanks: 1
[    13.922] 	MemoryModel: 6
[    13.922] 	BankSize: 0
[    13.922] 	NumberOfImages: 11
[    13.922] 	RedMaskSize: 5
[    13.922] 	RedFieldPosition: 10
[    13.922] 	GreenMaskSize: 5
[    13.922] 	GreenFieldPosition: 5
[    13.922] 	BlueMaskSize: 5
[    13.922] 	BlueFieldPosition: 0
[    13.922] 	RsvdMaskSize: 0
[    13.922] 	RsvdFieldPosition: 0
[    13.922] 	DirectColorModeInfo: 0
[    13.922] 	PhysBasePtr: 0xf9000000
[    13.922] 	LinBytesPerScanLine: 1280
[    13.922] 	BnkNumberOfImagePages: 11
[    13.922] 	LinNumberOfImagePages: 11
[    13.922] 	LinRedMaskSize: 5
[    13.922] 	LinRedFieldPosition: 10
[    13.922] 	LinGreenMaskSize: 5
[    13.922] 	LinGreenFieldPosition: 5
[    13.922] 	LinBlueMaskSize: 5
[    13.922] 	LinBlueFieldPosition: 0
[    13.922] 	LinRsvdMaskSize: 0
[    13.922] 	LinRsvdFieldPosition: 0
[    13.922] 	MaxPixelClock: 1000000
[    13.922] Mode: 111 (640x480)
[    13.922] 	ModeAttributes: 0x9b
[    13.922] 	WinAAttributes: 0x7
[    13.922] 	WinBAttributes: 0x0
[    13.922] 	WinGranularity: 64
[    13.922] 	WinSize: 64
[    13.922] 	WinASegment: 0xa000
[    13.922] 	WinBSegment: 0xa000
[    13.922] 	WinFuncPtr: 0xc00013f5
[    13.922] 	BytesPerScanline: 1280
[    13.922] 	XResolution: 640
[    13.922] 	YResolution: 480
[    13.922] 	XCharSize: 8
[    13.922] 	YCharSize: 16
[    13.923] 	NumberOfPlanes: 1
[    13.923] 	BitsPerPixel: 16
[    13.923] 	NumberOfBanks: 1
[    13.923] 	MemoryModel: 6
[    13.923] 	BankSize: 0
[    13.923] 	NumberOfImages: 11
[    13.923] 	RedMaskSize: 5
[    13.923] 	RedFieldPosition: 11
[    13.923] 	GreenMaskSize: 6
[    13.923] 	GreenFieldPosition: 5
[    13.923] 	BlueMaskSize: 5
[    13.923] 	BlueFieldPosition: 0
[    13.923] 	RsvdMaskSize: 0
[    13.923] 	RsvdFieldPosition: 0
[    13.923] 	DirectColorModeInfo: 0
[    13.923] 	PhysBasePtr: 0xf9000000
[    13.923] 	LinBytesPerScanLine: 1280
[    13.923] 	BnkNumberOfImagePages: 11
[    13.923] 	LinNumberOfImagePages: 11
[    13.923] 	LinRedMaskSize: 5
[    13.923] 	LinRedFieldPosition: 11
[    13.923] 	LinGreenMaskSize: 6
[    13.923] 	LinGreenFieldPosition: 5
[    13.923] 	LinBlueMaskSize: 5
[    13.923] 	LinBlueFieldPosition: 0
[    13.923] 	LinRsvdMaskSize: 0
[    13.923] 	LinRsvdFieldPosition: 0
[    13.923] 	MaxPixelClock: 1000000
[    13.923] Mode: 113 (800x600)
[    13.923] 	ModeAttributes: 0x9b
[    13.923] 	WinAAttributes: 0x7
[    13.923] 	WinBAttributes: 0x0
[    13.923] 	WinGranularity: 64
[    13.923] 	WinSize: 64
[    13.923] 	WinASegment: 0xa000
[    13.923] 	WinBSegment: 0xa000
[    13.923] 	WinFuncPtr: 0xc00013f5
[    13.923] 	BytesPerScanline: 1600
[    13.923] 	XResolution: 800
[    13.923] 	YResolution: 600
[    13.923] 	XCharSize: 8
[    13.923] 	YCharSize: 16
[    13.923] 	NumberOfPlanes: 1
[    13.923] 	BitsPerPixel: 15
[    13.923] 	NumberOfBanks: 1
[    13.923] 	MemoryModel: 6
[    13.923] 	BankSize: 0
[    13.923] 	NumberOfImages: 7
[    13.923] 	RedMaskSize: 5
[    13.923] 	RedFieldPosition: 10
[    13.923] 	GreenMaskSize: 5
[    13.923] 	GreenFieldPosition: 5
[    13.923] 	BlueMaskSize: 5
[    13.923] 	BlueFieldPosition: 0
[    13.923] 	RsvdMaskSize: 0
[    13.923] 	RsvdFieldPosition: 0
[    13.923] 	DirectColorModeInfo: 0
[    13.923] 	PhysBasePtr: 0xf9000000
[    13.923] 	LinBytesPerScanLine: 1600
[    13.923] 	BnkNumberOfImagePages: 7
[    13.923] 	LinNumberOfImagePages: 7
[    13.923] 	LinRedMaskSize: 5
[    13.923] 	LinRedFieldPosition: 10
[    13.923] 	LinGreenMaskSize: 5
[    13.923] 	LinGreenFieldPosition: 5
[    13.923] 	LinBlueMaskSize: 5
[    13.923] 	LinBlueFieldPosition: 0
[    13.923] 	LinRsvdMaskSize: 0
[    13.923] 	LinRsvdFieldPosition: 0
[    13.923] 	MaxPixelClock: 1000000
[    13.924] Mode: 114 (800x600)
[    13.924] 	ModeAttributes: 0x9b
[    13.924] 	WinAAttributes: 0x7
[    13.924] 	WinBAttributes: 0x0
[    13.924] 	WinGranularity: 64
[    13.924] 	WinSize: 64
[    13.924] 	WinASegment: 0xa000
[    13.924] 	WinBSegment: 0xa000
[    13.924] 	WinFuncPtr: 0xc00013f5
[    13.924] 	BytesPerScanline: 1600
[    13.924] 	XResolution: 800
[    13.924] 	YResolution: 600
[    13.924] 	XCharSize: 8
[    13.924] 	YCharSize: 16
[    13.924] 	NumberOfPlanes: 1
[    13.924] 	BitsPerPixel: 16
[    13.924] 	NumberOfBanks: 1
[    13.924] 	MemoryModel: 6
[    13.924] 	BankSize: 0
[    13.924] 	NumberOfImages: 7
[    13.924] 	RedMaskSize: 5
[    13.924] 	RedFieldPosition: 11
[    13.924] 	GreenMaskSize: 6
[    13.924] 	GreenFieldPosition: 5
[    13.924] 	BlueMaskSize: 5
[    13.924] 	BlueFieldPosition: 0
[    13.924] 	RsvdMaskSize: 0
[    13.924] 	RsvdFieldPosition: 0
[    13.924] 	DirectColorModeInfo: 0
[    13.924] 	PhysBasePtr: 0xf9000000
[    13.924] 	LinBytesPerScanLine: 1600
[    13.924] 	BnkNumberOfImagePages: 7
[    13.924] 	LinNumberOfImagePages: 7
[    13.924] 	LinRedMaskSize: 5
[    13.924] 	LinRedFieldPosition: 11
[    13.924] 	LinGreenMaskSize: 6
[    13.924] 	LinGreenFieldPosition: 5
[    13.924] 	LinBlueMaskSize: 5
[    13.924] 	LinBlueFieldPosition: 0
[    13.924] 	LinRsvdMaskSize: 0
[    13.924] 	LinRsvdFieldPosition: 0
[    13.924] 	MaxPixelClock: 1000000
[    13.925] Mode: 116 (1024x768)
[    13.925] 	ModeAttributes: 0x9b
[    13.925] 	WinAAttributes: 0x7
[    13.925] 	WinBAttributes: 0x0
[    13.925] 	WinGranularity: 64
[    13.925] 	WinSize: 64
[    13.925] 	WinASegment: 0xa000
[    13.925] 	WinBSegment: 0xa000
[    13.925] 	WinFuncPtr: 0xc00013f5
[    13.925] 	BytesPerScanline: 2048
[    13.925] 	XResolution: 1024
[    13.925] 	YResolution: 768
[    13.925] 	XCharSize: 8
[    13.925] 	YCharSize: 16
[    13.925] 	NumberOfPlanes: 1
[    13.925] 	BitsPerPixel: 15
[    13.925] 	NumberOfBanks: 1
[    13.925] 	MemoryModel: 6
[    13.925] 	BankSize: 0
[    13.925] 	NumberOfImages: 4
[    13.925] 	RedMaskSize: 5
[    13.925] 	RedFieldPosition: 10
[    13.925] 	GreenMaskSize: 5
[    13.925] 	GreenFieldPosition: 5
[    13.925] 	BlueMaskSize: 5
[    13.925] 	BlueFieldPosition: 0
[    13.925] 	RsvdMaskSize: 0
[    13.925] 	RsvdFieldPosition: 0
[    13.925] 	DirectColorModeInfo: 0
[    13.925] 	PhysBasePtr: 0xf9000000
[    13.925] 	LinBytesPerScanLine: 2048
[    13.925] 	BnkNumberOfImagePages: 4
[    13.925] 	LinNumberOfImagePages: 4
[    13.925] 	LinRedMaskSize: 5
[    13.925] 	LinRedFieldPosition: 10
[    13.925] 	LinGreenMaskSize: 5
[    13.925] 	LinGreenFieldPosition: 5
[    13.925] 	LinBlueMaskSize: 5
[    13.925] 	LinBlueFieldPosition: 0
[    13.925] 	LinRsvdMaskSize: 0
[    13.925] 	LinRsvdFieldPosition: 0
[    13.925] 	MaxPixelClock: 1000000
[    13.925] Mode: 117 (1024x768)
[    13.925] 	ModeAttributes: 0x9b
[    13.925] 	WinAAttributes: 0x7
[    13.925] 	WinBAttributes: 0x0
[    13.925] 	WinGranularity: 64
[    13.925] 	WinSize: 64
[    13.925] 	WinASegment: 0xa000
[    13.925] 	WinBSegment: 0xa000
[    13.925] 	WinFuncPtr: 0xc00013f5
[    13.925] 	BytesPerScanline: 2048
[    13.925] 	XResolution: 1024
[    13.925] 	YResolution: 768
[    13.925] 	XCharSize: 8
[    13.925] 	YCharSize: 16
[    13.925] 	NumberOfPlanes: 1
[    13.925] 	BitsPerPixel: 16
[    13.925] 	NumberOfBanks: 1
[    13.925] 	MemoryModel: 6
[    13.925] 	BankSize: 0
[    13.925] 	NumberOfImages: 4
[    13.925] 	RedMaskSize: 5
[    13.925] 	RedFieldPosition: 11
[    13.925] 	GreenMaskSize: 6
[    13.925] 	GreenFieldPosition: 5
[    13.925] 	BlueMaskSize: 5
[    13.925] 	BlueFieldPosition: 0
[    13.926] 	RsvdMaskSize: 0
[    13.926] 	RsvdFieldPosition: 0
[    13.926] 	DirectColorModeInfo: 0
[    13.926] 	PhysBasePtr: 0xf9000000
[    13.926] 	LinBytesPerScanLine: 2048
[    13.926] 	BnkNumberOfImagePages: 4
[    13.926] 	LinNumberOfImagePages: 4
[    13.926] 	LinRedMaskSize: 5
[    13.926] 	LinRedFieldPosition: 11
[    13.926] 	LinGreenMaskSize: 6
[    13.926] 	LinGreenFieldPosition: 5
[    13.926] 	LinBlueMaskSize: 5
[    13.926] 	LinBlueFieldPosition: 0
[    13.926] 	LinRsvdMaskSize: 0
[    13.926] 	LinRsvdFieldPosition: 0
[    13.926] 	MaxPixelClock: 1000000
[    13.926] Mode: 119 (1280x1024)
[    13.926] 	ModeAttributes: 0x9b
[    13.926] 	WinAAttributes: 0x7
[    13.926] 	WinBAttributes: 0x0
[    13.926] 	WinGranularity: 64
[    13.926] 	WinSize: 64
[    13.926] 	WinASegment: 0xa000
[    13.926] 	WinBSegment: 0xa000
[    13.926] 	WinFuncPtr: 0xc00013f5
[    13.926] 	BytesPerScanline: 2560
[    13.926] 	XResolution: 1280
[    13.926] 	YResolution: 1024
[    13.926] 	XCharSize: 8
[    13.926] 	YCharSize: 16
[    13.926] 	NumberOfPlanes: 1
[    13.926] 	BitsPerPixel: 15
[    13.926] 	NumberOfBanks: 1
[    13.926] 	MemoryModel: 6
[    13.926] 	BankSize: 0
[    13.926] 	NumberOfImages: 2
[    13.926] 	RedMaskSize: 5
[    13.926] 	RedFieldPosition: 10
[    13.926] 	GreenMaskSize: 5
[    13.926] 	GreenFieldPosition: 5
[    13.926] 	BlueMaskSize: 5
[    13.926] 	BlueFieldPosition: 0
[    13.926] 	RsvdMaskSize: 0
[    13.926] 	RsvdFieldPosition: 0
[    13.926] 	DirectColorModeInfo: 0
[    13.926] 	PhysBasePtr: 0xf9000000
[    13.926] 	LinBytesPerScanLine: 2560
[    13.926] 	BnkNumberOfImagePages: 2
[    13.926] 	LinNumberOfImagePages: 2
[    13.926] 	LinRedMaskSize: 5
[    13.926] 	LinRedFieldPosition: 10
[    13.926] 	LinGreenMaskSize: 5
[    13.926] 	LinGreenFieldPosition: 5
[    13.926] 	LinBlueMaskSize: 5
[    13.926] 	LinBlueFieldPosition: 0
[    13.926] 	LinRsvdMaskSize: 0
[    13.926] 	LinRsvdFieldPosition: 0
[    13.926] 	MaxPixelClock: 1000000
[    13.927] Mode: 11a (1280x1024)
[    13.927] 	ModeAttributes: 0x9b
[    13.927] 	WinAAttributes: 0x7
[    13.927] 	WinBAttributes: 0x0
[    13.927] 	WinGranularity: 64
[    13.927] 	WinSize: 64
[    13.927] 	WinASegment: 0xa000
[    13.927] 	WinBSegment: 0xa000
[    13.927] 	WinFuncPtr: 0xc00013f5
[    13.927] 	BytesPerScanline: 2560
[    13.927] 	XResolution: 1280
[    13.927] 	YResolution: 1024
[    13.927] 	XCharSize: 8
[    13.927] 	YCharSize: 16
[    13.927] 	NumberOfPlanes: 1
[    13.927] 	BitsPerPixel: 16
[    13.927] 	NumberOfBanks: 1
[    13.927] 	MemoryModel: 6
[    13.927] 	BankSize: 0
[    13.927] 	NumberOfImages: 2
[    13.927] 	RedMaskSize: 5
[    13.927] 	RedFieldPosition: 11
[    13.927] 	GreenMaskSize: 6
[    13.927] 	GreenFieldPosition: 5
[    13.927] 	BlueMaskSize: 5
[    13.927] 	BlueFieldPosition: 0
[    13.927] 	RsvdMaskSize: 0
[    13.927] 	RsvdFieldPosition: 0
[    13.927] 	DirectColorModeInfo: 0
[    13.927] 	PhysBasePtr: 0xf9000000
[    13.927] 	LinBytesPerScanLine: 2560
[    13.927] 	BnkNumberOfImagePages: 2
[    13.927] 	LinNumberOfImagePages: 2
[    13.927] 	LinRedMaskSize: 5
[    13.927] 	LinRedFieldPosition: 11
[    13.927] 	LinGreenMaskSize: 6
[    13.927] 	LinGreenFieldPosition: 5
[    13.927] 	LinBlueMaskSize: 5
[    13.927] 	LinBlueFieldPosition: 0
[    13.927] 	LinRsvdMaskSize: 0
[    13.927] 	LinRsvdFieldPosition: 0
[    13.927] 	MaxPixelClock: 1000000
[    13.928] *Mode: 120 (640x480)
[    13.928] 	ModeAttributes: 0x9b
[    13.928] 	WinAAttributes: 0x7
[    13.928] 	WinBAttributes: 0x0
[    13.928] 	WinGranularity: 64
[    13.928] 	WinSize: 64
[    13.928] 	WinASegment: 0xa000
[    13.928] 	WinBSegment: 0xa000
[    13.928] 	WinFuncPtr: 0xc00013f5
[    13.928] 	BytesPerScanline: 2560
[    13.928] 	XResolution: 640
[    13.928] 	YResolution: 480
[    13.928] 	XCharSize: 8
[    13.928] 	YCharSize: 16
[    13.928] 	NumberOfPlanes: 1
[    13.928] 	BitsPerPixel: 32
[    13.928] 	NumberOfBanks: 1
[    13.928] 	MemoryModel: 6
[    13.928] 	BankSize: 0
[    13.928] 	NumberOfImages: 5
[    13.928] 	RedMaskSize: 8
[    13.928] 	RedFieldPosition: 16
[    13.928] 	GreenMaskSize: 8
[    13.928] 	GreenFieldPosition: 8
[    13.928] 	BlueMaskSize: 8
[    13.928] 	BlueFieldPosition: 0
[    13.928] 	RsvdMaskSize: 8
[    13.928] 	RsvdFieldPosition: 24
[    13.928] 	DirectColorModeInfo: 0
[    13.928] 	PhysBasePtr: 0xf9000000
[    13.928] 	LinBytesPerScanLine: 2560
[    13.928] 	BnkNumberOfImagePages: 5
[    13.928] 	LinNumberOfImagePages: 5
[    13.928] 	LinRedMaskSize: 8
[    13.928] 	LinRedFieldPosition: 16
[    13.928] 	LinGreenMaskSize: 8
[    13.928] 	LinGreenFieldPosition: 8
[    13.928] 	LinBlueMaskSize: 8
[    13.928] 	LinBlueFieldPosition: 0
[    13.928] 	LinRsvdMaskSize: 8
[    13.928] 	LinRsvdFieldPosition: 24
[    13.928] 	MaxPixelClock: 1000000
[    13.928] *Mode: 121 (800x600)
[    13.928] 	ModeAttributes: 0x9b
[    13.928] 	WinAAttributes: 0x7
[    13.928] 	WinBAttributes: 0x0
[    13.928] 	WinGranularity: 64
[    13.928] 	WinSize: 64
[    13.928] 	WinASegment: 0xa000
[    13.928] 	WinBSegment: 0xa000
[    13.928] 	WinFuncPtr: 0xc00013f5
[    13.928] 	BytesPerScanline: 3200
[    13.928] 	XResolution: 800
[    13.928] 	YResolution: 600
[    13.928] 	XCharSize: 8
[    13.928] 	YCharSize: 16
[    13.928] 	NumberOfPlanes: 1
[    13.928] 	BitsPerPixel: 32
[    13.928] 	NumberOfBanks: 1
[    13.928] 	MemoryModel: 6
[    13.928] 	BankSize: 0
[    13.928] 	NumberOfImages: 3
[    13.928] 	RedMaskSize: 8
[    13.928] 	RedFieldPosition: 16
[    13.928] 	GreenMaskSize: 8
[    13.928] 	GreenFieldPosition: 8
[    13.928] 	BlueMaskSize: 8
[    13.928] 	BlueFieldPosition: 0
[    13.928] 	RsvdMaskSize: 8
[    13.928] 	RsvdFieldPosition: 24
[    13.928] 	DirectColorModeInfo: 0
[    13.928] 	PhysBasePtr: 0xf9000000
[    13.928] 	LinBytesPerScanLine: 3200
[    13.928] 	BnkNumberOfImagePages: 3
[    13.928] 	LinNumberOfImagePages: 3
[    13.928] 	LinRedMaskSize: 8
[    13.929] 	LinRedFieldPosition: 16
[    13.929] 	LinGreenMaskSize: 8
[    13.929] 	LinGreenFieldPosition: 8
[    13.929] 	LinBlueMaskSize: 8
[    13.929] 	LinBlueFieldPosition: 0
[    13.929] 	LinRsvdMaskSize: 8
[    13.929] 	LinRsvdFieldPosition: 24
[    13.929] 	MaxPixelClock: 1000000
[    13.929] *Mode: 122 (1024x768)
[    13.929] 	ModeAttributes: 0x9b
[    13.929] 	WinAAttributes: 0x7
[    13.929] 	WinBAttributes: 0x0
[    13.929] 	WinGranularity: 64
[    13.929] 	WinSize: 64
[    13.929] 	WinASegment: 0xa000
[    13.929] 	WinBSegment: 0xa000
[    13.929] 	WinFuncPtr: 0xc00013f5
[    13.929] 	BytesPerScanline: 4096
[    13.929] 	XResolution: 1024
[    13.929] 	YResolution: 768
[    13.929] 	XCharSize: 8
[    13.929] 	YCharSize: 16
[    13.929] 	NumberOfPlanes: 1
[    13.929] 	BitsPerPixel: 32
[    13.929] 	NumberOfBanks: 1
[    13.929] 	MemoryModel: 6
[    13.929] 	BankSize: 0
[    13.929] 	NumberOfImages: 1
[    13.929] 	RedMaskSize: 8
[    13.929] 	RedFieldPosition: 16
[    13.929] 	GreenMaskSize: 8
[    13.929] 	GreenFieldPosition: 8
[    13.929] 	BlueMaskSize: 8
[    13.929] 	BlueFieldPosition: 0
[    13.929] 	RsvdMaskSize: 8
[    13.929] 	RsvdFieldPosition: 24
[    13.929] 	DirectColorModeInfo: 0
[    13.929] 	PhysBasePtr: 0xf9000000
[    13.929] 	LinBytesPerScanLine: 4096
[    13.929] 	BnkNumberOfImagePages: 1
[    13.929] 	LinNumberOfImagePages: 1
[    13.929] 	LinRedMaskSize: 8
[    13.929] 	LinRedFieldPosition: 16
[    13.929] 	LinGreenMaskSize: 8
[    13.929] 	LinGreenFieldPosition: 8
[    13.929] 	LinBlueMaskSize: 8
[    13.929] 	LinBlueFieldPosition: 0
[    13.929] 	LinRsvdMaskSize: 8
[    13.929] 	LinRsvdFieldPosition: 24
[    13.929] 	MaxPixelClock: 1000000
[    13.930] *Mode: 123 (1280x1024)
[    13.930] 	ModeAttributes: 0x9b
[    13.930] 	WinAAttributes: 0x7
[    13.930] 	WinBAttributes: 0x0
[    13.930] 	WinGranularity: 64
[    13.930] 	WinSize: 64
[    13.930] 	WinASegment: 0xa000
[    13.930] 	WinBSegment: 0xa000
[    13.930] 	WinFuncPtr: 0xc00013f5
[    13.930] 	BytesPerScanline: 5120
[    13.930] 	XResolution: 1280
[    13.930] 	YResolution: 1024
[    13.930] 	XCharSize: 8
[    13.930] 	YCharSize: 16
[    13.930] 	NumberOfPlanes: 1
[    13.930] 	BitsPerPixel: 32
[    13.930] 	NumberOfBanks: 1
[    13.930] 	MemoryModel: 6
[    13.930] 	BankSize: 0
[    13.930] 	NumberOfImages: 0
[    13.930] 	RedMaskSize: 8
[    13.930] 	RedFieldPosition: 16
[    13.930] 	GreenMaskSize: 8
[    13.930] 	GreenFieldPosition: 8
[    13.930] 	BlueMaskSize: 8
[    13.930] 	BlueFieldPosition: 0
[    13.930] 	RsvdMaskSize: 8
[    13.930] 	RsvdFieldPosition: 24
[    13.930] 	DirectColorModeInfo: 0
[    13.930] 	PhysBasePtr: 0xf9000000
[    13.930] 	LinBytesPerScanLine: 5120
[    13.930] 	BnkNumberOfImagePages: 0
[    13.930] 	LinNumberOfImagePages: 0
[    13.930] 	LinRedMaskSize: 8
[    13.930] 	LinRedFieldPosition: 16
[    13.930] 	LinGreenMaskSize: 8
[    13.930] 	LinGreenFieldPosition: 8
[    13.930] 	LinBlueMaskSize: 8
[    13.930] 	LinBlueFieldPosition: 0
[    13.930] 	LinRsvdMaskSize: 8
[    13.930] 	LinRsvdFieldPosition: 24
[    13.930] 	MaxPixelClock: 1000000
[    13.931] Mode: 125 (1600x1200)
[    13.931] 	ModeAttributes: 0x9b
[    13.931] 	WinAAttributes: 0x7
[    13.931] 	WinBAttributes: 0x0
[    13.931] 	WinGranularity: 64
[    13.931] 	WinSize: 64
[    13.931] 	WinASegment: 0xa000
[    13.931] 	WinBSegment: 0xa000
[    13.931] 	WinFuncPtr: 0xc00013f5
[    13.931] 	BytesPerScanline: 3200
[    13.931] 	XResolution: 1600
[    13.931] 	YResolution: 1200
[    13.931] 	XCharSize: 8
[    13.931] 	YCharSize: 16
[    13.931] 	NumberOfPlanes: 1
[    13.931] 	BitsPerPixel: 15
[    13.931] 	NumberOfBanks: 1
[    13.931] 	MemoryModel: 6
[    13.931] 	BankSize: 0
[    13.931] 	NumberOfImages: 1
[    13.931] 	RedMaskSize: 5
[    13.931] 	RedFieldPosition: 10
[    13.931] 	GreenMaskSize: 5
[    13.931] 	GreenFieldPosition: 5
[    13.931] 	BlueMaskSize: 5
[    13.931] 	BlueFieldPosition: 0
[    13.931] 	RsvdMaskSize: 0
[    13.931] 	RsvdFieldPosition: 0
[    13.931] 	DirectColorModeInfo: 0
[    13.931] 	PhysBasePtr: 0xf9000000
[    13.931] 	LinBytesPerScanLine: 3200
[    13.931] 	BnkNumberOfImagePages: 1
[    13.931] 	LinNumberOfImagePages: 1
[    13.931] 	LinRedMaskSize: 5
[    13.931] 	LinRedFieldPosition: 10
[    13.931] 	LinGreenMaskSize: 5
[    13.931] 	LinGreenFieldPosition: 5
[    13.931] 	LinBlueMaskSize: 5
[    13.931] 	LinBlueFieldPosition: 0
[    13.931] 	LinRsvdMaskSize: 0
[    13.931] 	LinRsvdFieldPosition: 0
[    13.931] 	MaxPixelClock: 1000000
[    13.931] Mode: 126 (1600x1200)
[    13.931] 	ModeAttributes: 0x9b
[    13.931] 	WinAAttributes: 0x7
[    13.931] 	WinBAttributes: 0x0
[    13.931] 	WinGranularity: 64
[    13.931] 	WinSize: 64
[    13.931] 	WinASegment: 0xa000
[    13.931] 	WinBSegment: 0xa000
[    13.931] 	WinFuncPtr: 0xc00013f5
[    13.931] 	BytesPerScanline: 3200
[    13.931] 	XResolution: 1600
[    13.931] 	YResolution: 1200
[    13.931] 	XCharSize: 8
[    13.931] 	YCharSize: 16
[    13.931] 	NumberOfPlanes: 1
[    13.931] 	BitsPerPixel: 16
[    13.931] 	NumberOfBanks: 1
[    13.931] 	MemoryModel: 6
[    13.931] 	BankSize: 0
[    13.931] 	NumberOfImages: 1
[    13.931] 	RedMaskSize: 5
[    13.931] 	RedFieldPosition: 11
[    13.931] 	GreenMaskSize: 6
[    13.931] 	GreenFieldPosition: 5
[    13.931] 	BlueMaskSize: 5
[    13.931] 	BlueFieldPosition: 0
[    13.931] 	RsvdMaskSize: 0
[    13.931] 	RsvdFieldPosition: 0
[    13.931] 	DirectColorModeInfo: 0
[    13.931] 	PhysBasePtr: 0xf9000000
[    13.931] 	LinBytesPerScanLine: 3200
[    13.931] 	BnkNumberOfImagePages: 1
[    13.931] 	LinNumberOfImagePages: 1
[    13.931] 	LinRedMaskSize: 5
[    13.931] 	LinRedFieldPosition: 11
[    13.932] 	LinGreenMaskSize: 6
[    13.932] 	LinGreenFieldPosition: 5
[    13.932] 	LinBlueMaskSize: 5
[    13.932] 	LinBlueFieldPosition: 0
[    13.932] 	LinRsvdMaskSize: 0
[    13.932] 	LinRsvdFieldPosition: 0
[    13.932] 	MaxPixelClock: 1000000
[    13.932] Mode: 130 (320x240)
[    13.932] 	ModeAttributes: 0x9f
[    13.932] 	WinAAttributes: 0x7
[    13.932] 	WinBAttributes: 0x0
[    13.932] 	WinGranularity: 64
[    13.932] 	WinSize: 64
[    13.932] 	WinASegment: 0xa000
[    13.932] 	WinBSegment: 0xa000
[    13.932] 	WinFuncPtr: 0xc00013f5
[    13.932] 	BytesPerScanline: 320
[    13.932] 	XResolution: 320
[    13.932] 	YResolution: 240
[    13.932] 	XCharSize: 8
[    13.932] 	YCharSize: 8
[    13.932] 	NumberOfPlanes: 1
[    13.932] 	BitsPerPixel: 8
[    13.932] 	NumberOfBanks: 1
[    13.932] 	MemoryModel: 4
[    13.932] 	BankSize: 0
[    13.932] 	NumberOfImages: 63
[    13.932] 	RedMaskSize: 0
[    13.932] 	RedFieldPosition: 0
[    13.932] 	GreenMaskSize: 0
[    13.932] 	GreenFieldPosition: 0
[    13.932] 	BlueMaskSize: 0
[    13.932] 	BlueFieldPosition: 0
[    13.932] 	RsvdMaskSize: 0
[    13.932] 	RsvdFieldPosition: 0
[    13.932] 	DirectColorModeInfo: 0
[    13.932] 	PhysBasePtr: 0xf9000000
[    13.932] 	LinBytesPerScanLine: 320
[    13.932] 	BnkNumberOfImagePages: 63
[    13.932] 	LinNumberOfImagePages: 63
[    13.932] 	LinRedMaskSize: 0
[    13.932] 	LinRedFieldPosition: 0
[    13.932] 	LinGreenMaskSize: 0
[    13.932] 	LinGreenFieldPosition: 0
[    13.932] 	LinBlueMaskSize: 0
[    13.932] 	LinBlueFieldPosition: 0
[    13.932] 	LinRsvdMaskSize: 0
[    13.932] 	LinRsvdFieldPosition: 0
[    13.932] 	MaxPixelClock: 1000000
[    13.933] Mode: 131 (320x240)
[    13.933] 	ModeAttributes: 0x9b
[    13.933] 	WinAAttributes: 0x7
[    13.933] 	WinBAttributes: 0x0
[    13.933] 	WinGranularity: 64
[    13.933] 	WinSize: 64
[    13.933] 	WinASegment: 0xa000
[    13.933] 	WinBSegment: 0xa000
[    13.933] 	WinFuncPtr: 0xc00013f5
[    13.933] 	BytesPerScanline: 640
[    13.933] 	XResolution: 320
[    13.933] 	YResolution: 240
[    13.933] 	XCharSize: 8
[    13.933] 	YCharSize: 8
[    13.933] 	NumberOfPlanes: 1
[    13.933] 	BitsPerPixel: 15
[    13.933] 	NumberOfBanks: 1
[    13.933] 	MemoryModel: 6
[    13.933] 	BankSize: 0
[    13.933] 	NumberOfImages: 41
[    13.933] 	RedMaskSize: 5
[    13.933] 	RedFieldPosition: 10
[    13.933] 	GreenMaskSize: 5
[    13.933] 	GreenFieldPosition: 5
[    13.933] 	BlueMaskSize: 5
[    13.933] 	BlueFieldPosition: 0
[    13.933] 	RsvdMaskSize: 0
[    13.933] 	RsvdFieldPosition: 0
[    13.933] 	DirectColorModeInfo: 0
[    13.933] 	PhysBasePtr: 0xf9000000
[    13.933] 	LinBytesPerScanLine: 640
[    13.933] 	BnkNumberOfImagePages: 41
[    13.933] 	LinNumberOfImagePages: 41
[    13.933] 	LinRedMaskSize: 5
[    13.933] 	LinRedFieldPosition: 10
[    13.933] 	LinGreenMaskSize: 5
[    13.933] 	LinGreenFieldPosition: 5
[    13.933] 	LinBlueMaskSize: 5
[    13.933] 	LinBlueFieldPosition: 0
[    13.933] 	LinRsvdMaskSize: 0
[    13.933] 	LinRsvdFieldPosition: 0
[    13.933] 	MaxPixelClock: 1000000
[    13.934] Mode: 132 (320x240)
[    13.934] 	ModeAttributes: 0x9b
[    13.934] 	WinAAttributes: 0x7
[    13.934] 	WinBAttributes: 0x0
[    13.934] 	WinGranularity: 64
[    13.934] 	WinSize: 64
[    13.934] 	WinASegment: 0xa000
[    13.934] 	WinBSegment: 0xa000
[    13.934] 	WinFuncPtr: 0xc00013f5
[    13.934] 	BytesPerScanline: 640
[    13.934] 	XResolution: 320
[    13.934] 	YResolution: 240
[    13.934] 	XCharSize: 8
[    13.934] 	YCharSize: 8
[    13.934] 	NumberOfPlanes: 1
[    13.934] 	BitsPerPixel: 16
[    13.934] 	NumberOfBanks: 1
[    13.934] 	MemoryModel: 6
[    13.934] 	BankSize: 0
[    13.934] 	NumberOfImages: 41
[    13.934] 	RedMaskSize: 5
[    13.934] 	RedFieldPosition: 11
[    13.934] 	GreenMaskSize: 6
[    13.934] 	GreenFieldPosition: 5
[    13.934] 	BlueMaskSize: 5
[    13.934] 	BlueFieldPosition: 0
[    13.934] 	RsvdMaskSize: 0
[    13.934] 	RsvdFieldPosition: 0
[    13.934] 	DirectColorModeInfo: 0
[    13.934] 	PhysBasePtr: 0xf9000000
[    13.934] 	LinBytesPerScanLine: 640
[    13.934] 	BnkNumberOfImagePages: 41
[    13.934] 	LinNumberOfImagePages: 41
[    13.934] 	LinRedMaskSize: 5
[    13.934] 	LinRedFieldPosition: 11
[    13.934] 	LinGreenMaskSize: 6
[    13.934] 	LinGreenFieldPosition: 5
[    13.934] 	LinBlueMaskSize: 5
[    13.934] 	LinBlueFieldPosition: 0
[    13.934] 	LinRsvdMaskSize: 0
[    13.934] 	LinRsvdFieldPosition: 0
[    13.934] 	MaxPixelClock: 1000000
[    13.934] *Mode: 133 (320x240)
[    13.934] 	ModeAttributes: 0x9b
[    13.934] 	WinAAttributes: 0x7
[    13.934] 	WinBAttributes: 0x0
[    13.934] 	WinGranularity: 64
[    13.934] 	WinSize: 64
[    13.934] 	WinASegment: 0xa000
[    13.934] 	WinBSegment: 0xa000
[    13.934] 	WinFuncPtr: 0xc00013f5
[    13.934] 	BytesPerScanline: 1280
[    13.934] 	XResolution: 320
[    13.934] 	YResolution: 240
[    13.934] 	XCharSize: 8
[    13.934] 	YCharSize: 8
[    13.934] 	NumberOfPlanes: 1
[    13.934] 	BitsPerPixel: 32
[    13.934] 	NumberOfBanks: 1
[    13.934] 	MemoryModel: 6
[    13.934] 	BankSize: 0
[    13.934] 	NumberOfImages: 24
[    13.934] 	RedMaskSize: 8
[    13.934] 	RedFieldPosition: 16
[    13.935] 	GreenMaskSize: 8
[    13.935] 	GreenFieldPosition: 8
[    13.935] 	BlueMaskSize: 8
[    13.935] 	BlueFieldPosition: 0
[    13.935] 	RsvdMaskSize: 8
[    13.935] 	RsvdFieldPosition: 24
[    13.935] 	DirectColorModeInfo: 0
[    13.935] 	PhysBasePtr: 0xf9000000
[    13.935] 	LinBytesPerScanLine: 1280
[    13.935] 	BnkNumberOfImagePages: 24
[    13.935] 	LinNumberOfImagePages: 24
[    13.935] 	LinRedMaskSize: 8
[    13.935] 	LinRedFieldPosition: 16
[    13.935] 	LinGreenMaskSize: 8
[    13.935] 	LinGreenFieldPosition: 8
[    13.935] 	LinBlueMaskSize: 8
[    13.935] 	LinBlueFieldPosition: 0
[    13.935] 	LinRsvdMaskSize: 8
[    13.935] 	LinRsvdFieldPosition: 24
[    13.935] 	MaxPixelClock: 1000000
[    13.935] Mode: 134 (400x300)
[    13.935] 	ModeAttributes: 0x9f
[    13.935] 	WinAAttributes: 0x7
[    13.935] 	WinBAttributes: 0x0
[    13.935] 	WinGranularity: 64
[    13.935] 	WinSize: 64
[    13.935] 	WinASegment: 0xa000
[    13.935] 	WinBSegment: 0xa000
[    13.935] 	WinFuncPtr: 0xc00013f5
[    13.935] 	BytesPerScanline: 400
[    13.935] 	XResolution: 400
[    13.935] 	YResolution: 300
[    13.935] 	XCharSize: 8
[    13.935] 	YCharSize: 8
[    13.935] 	NumberOfPlanes: 1
[    13.935] 	BitsPerPixel: 8
[    13.935] 	NumberOfBanks: 1
[    13.935] 	MemoryModel: 4
[    13.935] 	BankSize: 0
[    13.935] 	NumberOfImages: 63
[    13.935] 	RedMaskSize: 0
[    13.935] 	RedFieldPosition: 0
[    13.935] 	GreenMaskSize: 0
[    13.935] 	GreenFieldPosition: 0
[    13.935] 	BlueMaskSize: 0
[    13.935] 	BlueFieldPosition: 0
[    13.935] 	RsvdMaskSize: 0
[    13.935] 	RsvdFieldPosition: 0
[    13.935] 	DirectColorModeInfo: 0
[    13.935] 	PhysBasePtr: 0xf9000000
[    13.935] 	LinBytesPerScanLine: 400
[    13.935] 	BnkNumberOfImagePages: 63
[    13.935] 	LinNumberOfImagePages: 63
[    13.935] 	LinRedMaskSize: 0
[    13.935] 	LinRedFieldPosition: 0
[    13.935] 	LinGreenMaskSize: 0
[    13.935] 	LinGreenFieldPosition: 0
[    13.935] 	LinBlueMaskSize: 0
[    13.935] 	LinBlueFieldPosition: 0
[    13.935] 	LinRsvdMaskSize: 0
[    13.935] 	LinRsvdFieldPosition: 0
[    13.935] 	MaxPixelClock: 1000000
[    13.936] Mode: 135 (400x300)
[    13.936] 	ModeAttributes: 0x9b
[    13.936] 	WinAAttributes: 0x7
[    13.936] 	WinBAttributes: 0x0
[    13.936] 	WinGranularity: 64
[    13.936] 	WinSize: 64
[    13.936] 	WinASegment: 0xa000
[    13.936] 	WinBSegment: 0xa000
[    13.936] 	WinFuncPtr: 0xc00013f5
[    13.936] 	BytesPerScanline: 800
[    13.936] 	XResolution: 400
[    13.936] 	YResolution: 300
[    13.936] 	XCharSize: 8
[    13.936] 	YCharSize: 8
[    13.936] 	NumberOfPlanes: 1
[    13.936] 	BitsPerPixel: 15
[    13.936] 	NumberOfBanks: 1
[    13.936] 	MemoryModel: 6
[    13.936] 	BankSize: 0
[    13.936] 	NumberOfImages: 31
[    13.936] 	RedMaskSize: 5
[    13.936] 	RedFieldPosition: 10
[    13.936] 	GreenMaskSize: 5
[    13.936] 	GreenFieldPosition: 5
[    13.936] 	BlueMaskSize: 5
[    13.936] 	BlueFieldPosition: 0
[    13.936] 	RsvdMaskSize: 0
[    13.936] 	RsvdFieldPosition: 0
[    13.936] 	DirectColorModeInfo: 0
[    13.936] 	PhysBasePtr: 0xf9000000
[    13.936] 	LinBytesPerScanLine: 800
[    13.936] 	BnkNumberOfImagePages: 31
[    13.936] 	LinNumberOfImagePages: 31
[    13.936] 	LinRedMaskSize: 5
[    13.936] 	LinRedFieldPosition: 10
[    13.936] 	LinGreenMaskSize: 5
[    13.936] 	LinGreenFieldPosition: 5
[    13.936] 	LinBlueMaskSize: 5
[    13.936] 	LinBlueFieldPosition: 0
[    13.936] 	LinRsvdMaskSize: 0
[    13.936] 	LinRsvdFieldPosition: 0
[    13.936] 	MaxPixelClock: 1000000
[    13.937] Mode: 136 (400x300)
[    13.937] 	ModeAttributes: 0x9b
[    13.937] 	WinAAttributes: 0x7
[    13.937] 	WinBAttributes: 0x0
[    13.937] 	WinGranularity: 64
[    13.937] 	WinSize: 64
[    13.937] 	WinASegment: 0xa000
[    13.937] 	WinBSegment: 0xa000
[    13.937] 	WinFuncPtr: 0xc00013f5
[    13.937] 	BytesPerScanline: 800
[    13.937] 	XResolution: 400
[    13.937] 	YResolution: 300
[    13.937] 	XCharSize: 8
[    13.937] 	YCharSize: 8
[    13.937] 	NumberOfPlanes: 1
[    13.937] 	BitsPerPixel: 16
[    13.937] 	NumberOfBanks: 1
[    13.937] 	MemoryModel: 6
[    13.937] 	BankSize: 0
[    13.937] 	NumberOfImages: 31
[    13.937] 	RedMaskSize: 5
[    13.937] 	RedFieldPosition: 11
[    13.937] 	GreenMaskSize: 6
[    13.937] 	GreenFieldPosition: 5
[    13.937] 	BlueMaskSize: 5
[    13.937] 	BlueFieldPosition: 0
[    13.937] 	RsvdMaskSize: 0
[    13.937] 	RsvdFieldPosition: 0
[    13.937] 	DirectColorModeInfo: 0
[    13.937] 	PhysBasePtr: 0xf9000000
[    13.937] 	LinBytesPerScanLine: 800
[    13.937] 	BnkNumberOfImagePages: 31
[    13.937] 	LinNumberOfImagePages: 31
[    13.937] 	LinRedMaskSize: 5
[    13.937] 	LinRedFieldPosition: 11
[    13.937] 	LinGreenMaskSize: 6
[    13.937] 	LinGreenFieldPosition: 5
[    13.937] 	LinBlueMaskSize: 5
[    13.937] 	LinBlueFieldPosition: 0
[    13.937] 	LinRsvdMaskSize: 0
[    13.937] 	LinRsvdFieldPosition: 0
[    13.937] 	MaxPixelClock: 1000000
[    13.937] *Mode: 137 (400x300)
[    13.937] 	ModeAttributes: 0x9b
[    13.937] 	WinAAttributes: 0x7
[    13.937] 	WinBAttributes: 0x0
[    13.937] 	WinGranularity: 64
[    13.937] 	WinSize: 64
[    13.937] 	WinASegment: 0xa000
[    13.938] 	WinBSegment: 0xa000
[    13.938] 	WinFuncPtr: 0xc00013f5
[    13.938] 	BytesPerScanline: 1600
[    13.938] 	XResolution: 400
[    13.938] 	YResolution: 300
[    13.938] 	XCharSize: 8
[    13.938] 	YCharSize: 8
[    13.938] 	NumberOfPlanes: 1
[    13.938] 	BitsPerPixel: 32
[    13.938] 	NumberOfBanks: 1
[    13.938] 	MemoryModel: 6
[    13.938] 	BankSize: 0
[    13.938] 	NumberOfImages: 15
[    13.938] 	RedMaskSize: 8
[    13.938] 	RedFieldPosition: 16
[    13.938] 	GreenMaskSize: 8
[    13.938] 	GreenFieldPosition: 8
[    13.938] 	BlueMaskSize: 8
[    13.938] 	BlueFieldPosition: 0
[    13.938] 	RsvdMaskSize: 8
[    13.938] 	RsvdFieldPosition: 24
[    13.938] 	DirectColorModeInfo: 0
[    13.938] 	PhysBasePtr: 0xf9000000
[    13.938] 	LinBytesPerScanLine: 1600
[    13.938] 	BnkNumberOfImagePages: 15
[    13.938] 	LinNumberOfImagePages: 15
[    13.938] 	LinRedMaskSize: 8
[    13.938] 	LinRedFieldPosition: 16
[    13.938] 	LinGreenMaskSize: 8
[    13.938] 	LinGreenFieldPosition: 8
[    13.938] 	LinBlueMaskSize: 8
[    13.938] 	LinBlueFieldPosition: 0
[    13.938] 	LinRsvdMaskSize: 8
[    13.938] 	LinRsvdFieldPosition: 24
[    13.938] 	MaxPixelClock: 1000000
[    13.938] Mode: 138 (512x384)
[    13.938] 	ModeAttributes: 0x9f
[    13.938] 	WinAAttributes: 0x7
[    13.938] 	WinBAttributes: 0x0
[    13.938] 	WinGranularity: 64
[    13.938] 	WinSize: 64
[    13.938] 	WinASegment: 0xa000
[    13.938] 	WinBSegment: 0xa000
[    13.938] 	WinFuncPtr: 0xc00013f5
[    13.938] 	BytesPerScanline: 512
[    13.938] 	XResolution: 512
[    13.938] 	YResolution: 384
[    13.938] 	XCharSize: 8
[    13.938] 	YCharSize: 8
[    13.938] 	NumberOfPlanes: 1
[    13.938] 	BitsPerPixel: 8
[    13.938] 	NumberOfBanks: 1
[    13.938] 	MemoryModel: 4
[    13.938] 	BankSize: 0
[    13.938] 	NumberOfImages: 41
[    13.938] 	RedMaskSize: 0
[    13.938] 	RedFieldPosition: 0
[    13.938] 	GreenMaskSize: 0
[    13.938] 	GreenFieldPosition: 0
[    13.938] 	BlueMaskSize: 0
[    13.938] 	BlueFieldPosition: 0
[    13.938] 	RsvdMaskSize: 0
[    13.938] 	RsvdFieldPosition: 0
[    13.938] 	DirectColorModeInfo: 0
[    13.938] 	PhysBasePtr: 0xf9000000
[    13.938] 	LinBytesPerScanLine: 512
[    13.938] 	BnkNumberOfImagePages: 41
[    13.938] 	LinNumberOfImagePages: 41
[    13.938] 	LinRedMaskSize: 0
[    13.938] 	LinRedFieldPosition: 0
[    13.938] 	LinGreenMaskSize: 0
[    13.938] 	LinGreenFieldPosition: 0
[    13.938] 	LinBlueMaskSize: 0
[    13.938] 	LinBlueFieldPosition: 0
[    13.938] 	LinRsvdMaskSize: 0
[    13.938] 	LinRsvdFieldPosition: 0
[    13.938] 	MaxPixelClock: 1000000
[    13.939] Mode: 139 (512x384)
[    13.939] 	ModeAttributes: 0x9b
[    13.939] 	WinAAttributes: 0x7
[    13.939] 	WinBAttributes: 0x0
[    13.939] 	WinGranularity: 64
[    13.939] 	WinSize: 64
[    13.939] 	WinASegment: 0xa000
[    13.939] 	WinBSegment: 0xa000
[    13.939] 	WinFuncPtr: 0xc00013f5
[    13.939] 	BytesPerScanline: 1024
[    13.939] 	XResolution: 512
[    13.939] 	YResolution: 384
[    13.939] 	XCharSize: 8
[    13.939] 	YCharSize: 8
[    13.939] 	NumberOfPlanes: 1
[    13.939] 	BitsPerPixel: 15
[    13.939] 	NumberOfBanks: 1
[    13.939] 	MemoryModel: 6
[    13.939] 	BankSize: 0
[    13.939] 	NumberOfImages: 20
[    13.939] 	RedMaskSize: 5
[    13.939] 	RedFieldPosition: 10
[    13.939] 	GreenMaskSize: 5
[    13.939] 	GreenFieldPosition: 5
[    13.939] 	BlueMaskSize: 5
[    13.939] 	BlueFieldPosition: 0
[    13.939] 	RsvdMaskSize: 0
[    13.939] 	RsvdFieldPosition: 0
[    13.939] 	DirectColorModeInfo: 0
[    13.939] 	PhysBasePtr: 0xf9000000
[    13.939] 	LinBytesPerScanLine: 1024
[    13.939] 	BnkNumberOfImagePages: 20
[    13.939] 	LinNumberOfImagePages: 20
[    13.939] 	LinRedMaskSize: 5
[    13.939] 	LinRedFieldPosition: 10
[    13.939] 	LinGreenMaskSize: 5
[    13.939] 	LinGreenFieldPosition: 5
[    13.939] 	LinBlueMaskSize: 5
[    13.939] 	LinBlueFieldPosition: 0
[    13.939] 	LinRsvdMaskSize: 0
[    13.939] 	LinRsvdFieldPosition: 0
[    13.939] 	MaxPixelClock: 1000000
[    13.940] Mode: 13a (512x384)
[    13.940] 	ModeAttributes: 0x9b
[    13.940] 	WinAAttributes: 0x7
[    13.940] 	WinBAttributes: 0x0
[    13.940] 	WinGranularity: 64
[    13.940] 	WinSize: 64
[    13.940] 	WinASegment: 0xa000
[    13.940] 	WinBSegment: 0xa000
[    13.940] 	WinFuncPtr: 0xc00013f5
[    13.940] 	BytesPerScanline: 1024
[    13.940] 	XResolution: 512
[    13.940] 	YResolution: 384
[    13.940] 	XCharSize: 8
[    13.940] 	YCharSize: 8
[    13.940] 	NumberOfPlanes: 1
[    13.940] 	BitsPerPixel: 16
[    13.940] 	NumberOfBanks: 1
[    13.940] 	MemoryModel: 6
[    13.940] 	BankSize: 0
[    13.940] 	NumberOfImages: 20
[    13.940] 	RedMaskSize: 5
[    13.940] 	RedFieldPosition: 11
[    13.940] 	GreenMaskSize: 6
[    13.940] 	GreenFieldPosition: 5
[    13.940] 	BlueMaskSize: 5
[    13.940] 	BlueFieldPosition: 0
[    13.940] 	RsvdMaskSize: 0
[    13.940] 	RsvdFieldPosition: 0
[    13.940] 	DirectColorModeInfo: 0
[    13.940] 	PhysBasePtr: 0xf9000000
[    13.940] 	LinBytesPerScanLine: 1024
[    13.940] 	BnkNumberOfImagePages: 20
[    13.940] 	LinNumberOfImagePages: 20
[    13.940] 	LinRedMaskSize: 5
[    13.940] 	LinRedFieldPosition: 11
[    13.940] 	LinGreenMaskSize: 6
[    13.940] 	LinGreenFieldPosition: 5
[    13.940] 	LinBlueMaskSize: 5
[    13.940] 	LinBlueFieldPosition: 0
[    13.940] 	LinRsvdMaskSize: 0
[    13.940] 	LinRsvdFieldPosition: 0
[    13.940] 	MaxPixelClock: 1000000
[    13.941] *Mode: 13b (512x384)
[    13.941] 	ModeAttributes: 0x9b
[    13.941] 	WinAAttributes: 0x7
[    13.941] 	WinBAttributes: 0x0
[    13.941] 	WinGranularity: 64
[    13.941] 	WinSize: 64
[    13.941] 	WinASegment: 0xa000
[    13.941] 	WinBSegment: 0xa000
[    13.941] 	WinFuncPtr: 0xc00013f5
[    13.941] 	BytesPerScanline: 2048
[    13.941] 	XResolution: 512
[    13.941] 	YResolution: 384
[    13.941] 	XCharSize: 8
[    13.941] 	YCharSize: 8
[    13.941] 	NumberOfPlanes: 1
[    13.941] 	BitsPerPixel: 32
[    13.941] 	NumberOfBanks: 1
[    13.941] 	MemoryModel: 6
[    13.941] 	BankSize: 0
[    13.941] 	NumberOfImages: 9
[    13.941] 	RedMaskSize: 8
[    13.941] 	RedFieldPosition: 16
[    13.941] 	GreenMaskSize: 8
[    13.941] 	GreenFieldPosition: 8
[    13.941] 	BlueMaskSize: 8
[    13.941] 	BlueFieldPosition: 0
[    13.941] 	RsvdMaskSize: 8
[    13.941] 	RsvdFieldPosition: 24
[    13.941] 	DirectColorModeInfo: 0
[    13.941] 	PhysBasePtr: 0xf9000000
[    13.941] 	LinBytesPerScanLine: 2048
[    13.941] 	BnkNumberOfImagePages: 9
[    13.941] 	LinNumberOfImagePages: 9
[    13.941] 	LinRedMaskSize: 8
[    13.941] 	LinRedFieldPosition: 16
[    13.941] 	LinGreenMaskSize: 8
[    13.941] 	LinGreenFieldPosition: 8
[    13.941] 	LinBlueMaskSize: 8
[    13.941] 	LinBlueFieldPosition: 0
[    13.941] 	LinRsvdMaskSize: 8
[    13.941] 	LinRsvdFieldPosition: 24
[    13.941] 	MaxPixelClock: 1000000
[    13.941] 
[    13.941] (II) VESA(0): Total Memory: 128 64KB banks (8192kB)
[    13.941] (II) VESA(0): <default monitor>: Using hsync range of 24.00-83.00 kHz
[    13.941] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-75.00 Hz
[    13.941] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    13.941] (WW) VESA(0): Unable to estimate virtual size
[    13.941] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    13.941] (II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
[    13.941] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    13.941] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    13.941] (**) VESA(0): *Built-in mode "1280x1024"
[    13.941] (**) VESA(0): *Built-in mode "1024x768"
[    13.941] (**) VESA(0): *Built-in mode "800x600"
[    13.941] (**) VESA(0): *Built-in mode "640x480"
[    13.941] (**) VESA(0): Display dimensions: (510, 290) mm
[    13.941] (**) VESA(0): DPI set to (63, 89)
[    13.941] (**) VESA(0): Using "Shadow Framebuffer"
[    13.941] (II) Loading sub module "shadow"
[    13.941] (II) LoadModule: "shadow"
[    13.941] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    13.941] (II) Module shadow: vendor="X.Org Foundation"
[    13.942] 	compiled for 1.13.0, module version = 1.1.0
[    13.942] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.942] (II) Loading sub module "fb"
[    13.942] (II) LoadModule: "fb"
[    13.942] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.942] (II) Module fb: vendor="X.Org Foundation"
[    13.942] 	compiled for 1.13.0, module version = 1.0.0
[    13.942] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    13.942] (II) UnloadModule: "modesetting"
[    13.942] (II) Unloading modesetting
[    13.942] (II) UnloadModule: "fbdev"
[    13.942] (II) Unloading fbdev
[    13.942] (II) UnloadSubModule: "fbdevhw"
[    13.942] (II) Unloading fbdevhw
[    13.942] (==) Depth 24 pixmap format is 32 bpp
[    13.942] (II) Loading sub module "int10"
[    13.942] (II) LoadModule: "int10"
[    13.942] (II) Loading /usr/lib/xorg/modules/libint10.so
[    13.942] (II) Module int10: vendor="X.Org Foundation"
[    13.942] 	compiled for 1.13.0, module version = 1.0.0
[    13.942] 	ABI class: X.Org Video Driver, version 13.0
[    13.942] (II) VESA(0): initializing int10
[    13.947] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    13.947] (II) VESA(0): VESA BIOS detected
[    13.947] (II) VESA(0): VESA VBE Version 3.0
[    13.947] (II) VESA(0): VESA VBE Total Mem: 8192 kB
[    13.947] (II) VESA(0): VESA VBE OEM: ASPEED
[    13.947] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    13.947] (II) VESA(0): VESA VBE OEM Vendor: ASPEED Technology, Inc.
[    13.947] (II) VESA(0): VESA VBE OEM Product: AST GPU
[    13.947] (II) VESA(0): VESA VBE OEM Product Rev: 0.90.07
[    13.947] (II) VESA(0): virtual address = 0x7fe4b4109000,
	physical address = 0xf9000000, size = 8388608
[    13.957] (II) VESA(0): Setting up VESA Mode 0x123 (1280x1024)
[    13.991] (==) VESA(0): Default visual is TrueColor
[    13.991] (==) VESA(0): Backing store disabled
[    13.991] (==) VESA(0): DPMS enabled
[    13.991] (==) RandR enabled
[    13.991] (II) Found 2 VGA devices: arbiter wrapping enabled
[    13.998] (II) AIGLX: Screen 0 is not DRI2 capable
[    13.998] (II) AIGLX: Screen 0 is not DRI capable
[    14.007] (II) AIGLX: Loaded and initialized swrast
[    14.007] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    14.023] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.026] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.026] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.026] (II) LoadModule: "evdev"
[    14.026] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.027] (II) Module evdev: vendor="X.Org Foundation"
[    14.027] 	compiled for 1.13.0, module version = 2.7.3
[    14.027] 	Module class: X.Org XInput Driver
[    14.027] 	ABI class: X.Org XInput driver, version 18.0
[    14.027] (II) Using input driver 'evdev' for 'Power Button'
[    14.027] (**) Power Button: always reports core events
[    14.027] (**) evdev: Power Button: Device: "/dev/input/event1"
[    14.027] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.027] (--) evdev: Power Button: Found keys
[    14.027] (II) evdev: Power Button: Configuring as keyboard
[    14.027] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    14.027] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    14.027] (**) Option "xkb_rules" "evdev"
[    14.027] (**) Option "xkb_model" "pc105"
[    14.027] (**) Option "xkb_layout" "us"
[    14.027] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    14.027] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.027] (II) Using input driver 'evdev' for 'Power Button'
[    14.027] (**) Power Button: always reports core events
[    14.027] (**) evdev: Power Button: Device: "/dev/input/event0"
[    14.028] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.028] (--) evdev: Power Button: Found keys
[    14.028] (II) evdev: Power Button: Configuring as keyboard
[    14.028] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    14.028] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    14.028] (**) Option "xkb_rules" "evdev"
[    14.028] (**) Option "xkb_model" "pc105"
[    14.028] (**) Option "xkb_layout" "us"
[    14.028] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event3)
[    14.028] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    14.028] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    14.028] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    14.028] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event3"
[    14.028] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Vendor 0x45e Product 0xf9
[    14.028] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    14.028] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    14.028] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/0000:05:00.0/usb8/8-2/8-2.4/8-2.4:1.0/input/input3/event3"
[    14.028] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD, id 8)
[    14.028] (**) Option "xkb_rules" "evdev"
[    14.028] (**) Option "xkb_model" "pc105"
[    14.029] (**) Option "xkb_layout" "us"
[    14.029] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/event7)
[    14.029] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev pointer catchall"
[    14.029] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: Applying InputClass "evdev keyboard catchall"
[    14.029] (II) Using input driver 'evdev' for 'Microsft Microsoft Wireless Desktop Receiver 3.1'
[    14.029] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: always reports core events
[    14.029] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Device: "/dev/input/event7"
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Vendor 0x45e Product 0xf9
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found 9 mouse buttons
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found scroll wheel(s)
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found relative axes
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found x and y relative axes
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found absolute axes
[    14.029] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Forcing absolute x/y axes to exist.
[    14.029] (--) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Found keys
[    14.029] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as mouse
[    14.029] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Configuring as keyboard
[    14.029] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: Adding scrollwheel support
[    14.029] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: YAxisMapping: buttons 4 and 5
[    14.029] (**) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.029] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/0000:05:00.0/usb8/8-2/8-2.4/8-2.4:1.1/input/input7/event7"
[    14.029] (II) XINPUT: Adding extended input device "Microsft Microsoft Wireless Desktop Receiver 3.1" (type: KEYBOARD, id 9)
[    14.029] (**) Option "xkb_rules" "evdev"
[    14.029] (**) Option "xkb_model" "pc105"
[    14.029] (**) Option "xkb_layout" "us"
[    14.030] (II) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: initialized for relative axes.
[    14.030] (WW) evdev: Microsft Microsoft Wireless Desktop Receiver 3.1: ignoring absolute axes.
[    14.030] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) keeping acceleration scheme 1
[    14.030] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration profile 0
[    14.030] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration factor: 2.000
[    14.030] (**) Microsft Microsoft Wireless Desktop Receiver 3.1: (accel) acceleration threshold: 4
[    14.030] (II) config/udev: Adding input device Microsft Microsoft Wireless Desktop Receiver 3.1 (/dev/input/mouse1)
[    14.030] (II) No input driver specified, ignoring this device.
[    14.030] (II) This device may have been added with another device file.
[    14.031] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event10)
[    14.031] (II) No input driver specified, ignoring this device.
[    14.031] (II) This device may have been added with another device file.
[    14.031] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event11)
[    14.031] (II) No input driver specified, ignoring this device.
[    14.031] (II) This device may have been added with another device file.
[    14.031] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event8)
[    14.031] (II) No input driver specified, ignoring this device.
[    14.031] (II) This device may have been added with another device file.
[    14.031] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event9)
[    14.031] (II) No input driver specified, ignoring this device.
[    14.031] (II) This device may have been added with another device file.
[    14.032] (II) config/udev: Adding input device ATEN ATEN-COMPOSITE (/dev/input/event5)
[    14.032] (**) ATEN ATEN-COMPOSITE: Applying InputClass "evdev keyboard catchall"
[    14.032] (II) Using input driver 'evdev' for 'ATEN ATEN-COMPOSITE'
[    14.032] (**) ATEN ATEN-COMPOSITE: always reports core events
[    14.032] (**) evdev: ATEN ATEN-COMPOSITE: Device: "/dev/input/event5"
[    14.032] (--) evdev: ATEN ATEN-COMPOSITE: Vendor 0x557 Product 0x2214
[    14.032] (--) evdev: ATEN ATEN-COMPOSITE: Found keys
[    14.032] (II) evdev: ATEN ATEN-COMPOSITE: Configuring as keyboard
[    14.032] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2.1/3-2.1:1.0/input/input5/event5"
[    14.032] (II) XINPUT: Adding extended input device "ATEN ATEN-COMPOSITE" (type: KEYBOARD, id 10)
[    14.032] (**) Option "xkb_rules" "evdev"
[    14.032] (**) Option "xkb_model" "pc105"
[    14.032] (**) Option "xkb_layout" "us"
[    14.033] (II) config/udev: Adding input device ATEN ATEN-COMPOSITE (/dev/input/event6)
[    14.033] (**) ATEN ATEN-COMPOSITE: Applying InputClass "evdev pointer catchall"
[    14.033] (II) Using input driver 'evdev' for 'ATEN ATEN-COMPOSITE'
[    14.033] (**) ATEN ATEN-COMPOSITE: always reports core events
[    14.033] (**) evdev: ATEN ATEN-COMPOSITE: Device: "/dev/input/event6"
[    14.033] (--) evdev: ATEN ATEN-COMPOSITE: Vendor 0x557 Product 0x2214
[    14.033] (--) evdev: ATEN ATEN-COMPOSITE: Found 9 mouse buttons
[    14.033] (--) evdev: ATEN ATEN-COMPOSITE: Found scroll wheel(s)
[    14.033] (--) evdev: ATEN ATEN-COMPOSITE: Found relative axes
[    14.033] (--) evdev: ATEN ATEN-COMPOSITE: Found x and y relative axes
[    14.033] (II) evdev: ATEN ATEN-COMPOSITE: Configuring as mouse
[    14.033] (II) evdev: ATEN ATEN-COMPOSITE: Adding scrollwheel support
[    14.033] (**) evdev: ATEN ATEN-COMPOSITE: YAxisMapping: buttons 4 and 5
[    14.033] (**) evdev: ATEN ATEN-COMPOSITE: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.033] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2.1/3-2.1:1.1/input/input6/event6"
[    14.033] (II) XINPUT: Adding extended input device "ATEN ATEN-COMPOSITE" (type: MOUSE, id 11)
[    14.033] (II) evdev: ATEN ATEN-COMPOSITE: initialized for relative axes.
[    14.033] (**) ATEN ATEN-COMPOSITE: (accel) keeping acceleration scheme 1
[    14.033] (**) ATEN ATEN-COMPOSITE: (accel) acceleration profile 0
[    14.033] (**) ATEN ATEN-COMPOSITE: (accel) acceleration factor: 2.000
[    14.033] (**) ATEN ATEN-COMPOSITE: (accel) acceleration threshold: 4
[    14.033] (II) config/udev: Adding input device ATEN ATEN-COMPOSITE (/dev/input/mouse0)
[    14.033] (II) No input driver specified, ignoring this device.
[    14.033] (II) This device may have been added with another device file.
[    14.034] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event2)
[    14.034] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.034] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    14.034] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    14.034] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event2"
[    14.034] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[    14.034] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    14.034] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    14.034] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.1/4-2.1:1.0/input/input2/event2"
[    14.034] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 12)
[    14.034] (**) Option "xkb_rules" "evdev"
[    14.034] (**) Option "xkb_model" "pc105"
[    14.034] (**) Option "xkb_layout" "us"
[    14.034] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event4)
[    14.034] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    14.034] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    14.034] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    14.034] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
[    14.035] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[    14.035] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    14.035] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    14.035] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2.1/4-2.1:1.1/input/input4/event4"
[    14.035] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 13)
[    14.035] (**) Option "xkb_rules" "evdev"
[    14.035] (**) Option "xkb_model" "pc105"
[    14.035] (**) Option "xkb_layout" "us"
[    25.947] (II) VESA(0): Setting up VESA Mode 0x122 (1024x768)
[    35.503] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm

```

---

### Post by matt_symes on 2013-02-25
Hi

See my last post. install the driver and then reboot.

It was using the vesa driver. That could explain the distortion. It is trying to load the driver for the inbuilt graphics card by the looks of it.
```

[    11.679] (--) PCI:*(0:1:1:0) 1a03:2000:1a03:2000 rev 16, Mem @ 0xf9000000/8388608, 0xf9fc0000/131072, I/O @ 0x0000bc00/128 
[    11.679] (--) PCI: (0:2:0:0) 10de:11c0:3842:2662 rev 161, Mem @ 0xfa000000/16777216, 0xd8000000/134217728, 0xd6000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288 
```The star next to the first graphics card, the internal one, means that is the default graphics card.

What BIOS do you have ? We need to turn that card off.

If the worst comes to the worst we may be able to display it by writing to sysfs.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 

open additional drivers (type into the dash) and select the nvidia-current driver.

None of the options infer they are the nvidia-current.  I'm continuing to investigate.

---

### Post by trump600 on 2013-02-25
The option that seemed correct failed to install.  It directed me to this log:

```

2013-02-25 05:56:17,506 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0>
2013-02-25 05:56:20,833 DEBUG: reading modalias file /lib/modules/3.5.0-17-generic/modules.alias
2013-02-25 05:56:20,992 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2013-02-25 05:56:20,992 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2013-02-25 05:56:21,093 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2013-02-25 05:56:21,242 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2013-02-25 05:56:21,244 DEBUG: Firmware for DVB cards not available
2013-02-25 05:56:21,244 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2013-02-25 05:56:21,249 WARNING: Invalid custom handler module /usr/share/jockey/handlers/fglrx.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/fglrx.py", line 11, in <module>
    from NvidiaDetector.alternatives import Alternatives
ImportError: No module named NvidiaDetector.alternatives
2013-02-25 05:56:21,251 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2013-02-25 05:56:21,260 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2013-02-25 05:56:21,261 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2013-02-25 05:56:21,307 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2013-02-25 05:56:21,307 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2013-02-25 05:56:21,319 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2013-02-25 05:56:21,321 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2013-02-25 05:56:21,321 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2013-02-25 05:56:21,321 DEBUG: loading custom handler /usr/share/jockey/handlers/pvr-omap4.py
2013-02-25 05:56:21,335 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr

2013-02-25 05:56:21,347 DEBUG: Instantiated Handler subclass __builtin__.PVROmap4Driver from name PVROmap4Driver
2013-02-25 05:56:21,480 DEBUG: PowerVR SGX proprietary graphics driver for OMAP 4 not available
2013-02-25 05:56:21,481 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2013-02-25 05:56:21,526 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2013-02-25 05:56:21,567 DEBUG: Software modem not available
2013-02-25 05:56:21,568 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2013-02-25 05:56:21,578 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-02-25 05:56:21,618 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2013-02-25 05:56:21,619 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2013-02-25 05:56:21,619 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2013-02-25 05:56:21,626 WARNING: Invalid custom handler module /usr/share/jockey/handlers/nvidia.py
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 950, in get_handlers
    execfile(mod, symb)
  File "/usr/share/jockey/handlers/nvidia.py", line 12, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection
ImportError: No module named NvidiaDetector.nvidiadetector
2013-02-25 05:56:21,626 DEBUG: all custom handlers loaded
2013-02-25 05:56:21,627 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001033d00000194sv0000FFFFsd0000FFFFbc0Csc03i30')
2013-02-25 05:56:21,634 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0003v05ACp0204e0110-e0,1,4,k71,72,73,8E,8F,96,9B,A1,A3,A4,A5,A6,A8,D0,ram4,lsfw')
2013-02-25 05:56:21,639 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:21,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:21,809 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:21,809 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:21,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-25 05:56:21,810 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00008086d000010D3sv00001043sd00008369bc02sc00i00')
2013-02-25 05:56:22,134 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'e1000e'}
2013-02-25 05:56:22,134 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'e1000e', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,135 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd0000844Bbc0Csc03i20')
2013-02-25 05:56:22,466 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v05E3p0608d3298dc09dsc00dp01ic09isc00ip00')
2013-02-25 05:56:22,483 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v05ACp0204d0122dc00dsc00dp00ic03isc01ip01')
2013-02-25 05:56:22,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-25 05:56:22,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,510 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-25 05:56:22,510 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,510 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0003v0557p2214e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2013-02-25 05:56:22,511 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:22,511 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,511 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:22,511 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v05ACp0204d0122dc00dsc00dp00ic03isc00ip00')
2013-02-25 05:56:22,512 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-25 05:56:22,512 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,512 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v0557p2214d0100dc00dsc00dp00ic03isc01ip01')
2013-02-25 05:56:22,515 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-25 05:56:22,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-25 05:56:22,516 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-25 05:56:22,516 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'platform:pcspkr')
2013-02-25 05:56:22,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2013-02-25 05:56:22,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,517 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2013-02-25 05:56:22,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-02-25 05:56:22,518 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd0000844Bbc01sc06i01')
2013-02-25 05:56:22,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:22,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-25 05:56:22,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-25 05:56:22,522 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d00005A10sv00001043sd00008448bc06sc00i00')
2013-02-25 05:56:22,526 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-02-25 05:56:22,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-25 05:56:22,530 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:22,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:22,545 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v1058p0730d1008dc00dsc00dp00ic08isc06ip50')
2013-02-25 05:56:22,546 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'uas'}
2013-02-25 05:56:22,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,546 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v0557p2214d0100dc00dsc00dp00ic03isc01ip02')
2013-02-25 05:56:22,546 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-25 05:56:22,546 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,546 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2013-02-25 05:56:22,547 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,547 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'x86cpu:vendor:0002:family:0010:model:0009:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0017,0018,0019,001A,001C,0020,0021,0022,0023,0024,0025,0026,0027,0028,0029,002B,002C,002D,002E,002F,0030,0031,0034,0036,0037,0038,0039,003A,003B,003D,003E,003F,0064,0068,006A,006E,0070,0071,0074,0078,007A,007B,0080,0083,008D,0097,00C0,00C1,00C2,00C3,00C4,00C5,00C6,00C7,00C8,00C9,00CA,00CC,00CD,00D3,00E8,0105,0106,0107,0108,010D')
2013-02-25 05:56:22,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'kvm_amd'}
2013-02-25 05:56:22,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'kvm_amd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'microcode'}
2013-02-25 05:56:22,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'microcode', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-25 05:56:22,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:22,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,552 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:22,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-25 05:56:22,561 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-25 05:56:22,561 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,562 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'psmouse'}
2013-02-25 05:56:22,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0003v0557p2214e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-02-25 05:56:22,562 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:22,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,562 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:22,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-25 05:56:22,562 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:22,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2013-02-25 05:56:22,563 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:22,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,563 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:22,563 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-25 05:56:22,563 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0902:bd12/03/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnKGP(M)E-D16:rvrRev1.xxG:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-02-25 05:56:22,578 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v000010DEd000011C0sv00003842sd00002662bc03sc00i00')
2013-02-25 05:56:22,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2013-02-25 05:56:22,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,853 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2013-02-25 05:56:22,853 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:22,854 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_310', 'package': 'nvidia-experimental-310'}
2013-02-25 05:56:22,859 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-25 05:56:22,897 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310

2013-02-25 05:56:22,898 DEBUG: got handler kmod:nvidia_experimental_310([KernelModuleHandler, nonfree, disabled] Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-02-25 05:56:22,898 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2013-02-25 05:56:22,907 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-25 05:56:22,957 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-25 05:56:22,958 DEBUG: got handler kmod:nvidia_current_updates([KernelModuleHandler, nonfree, disabled] NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-02-25 05:56:22,958 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_experimental_304', 'package': 'nvidia-experimental-304'}
2013-02-25 05:56:22,967 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-25 05:56:23,017 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304

2013-02-25 05:56:23,018 DEBUG: got handler kmod:nvidia_experimental_304([KernelModuleHandler, nonfree, disabled] Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library)
2013-02-25 05:56:23,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-25 05:56:23,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,019 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,020 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod'}
2013-02-25 05:56:23,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0003v05ACp0204e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-02-25 05:56:23,021 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:23,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,022 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:23,022 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,022 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc01ip01')
2013-02-25 05:56:23,081 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-25 05:56:23,081 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,082 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd'}
2013-02-25 05:56:23,082 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbkbd', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-02-25 05:56:23,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-02-25 05:56:23,082 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd0000844Bbc01sc01i8a')
2013-02-25 05:56:23,087 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp'}
2013-02-25 05:56:23,087 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_atiixp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,087 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v000010DEd00000E0Bsv00003842sd00002662bc04sc03i00')
2013-02-25 05:56:23,091 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2013-02-25 05:56:23,091 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,091 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-25 05:56:23,092 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:23,092 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-25 05:56:23,092 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd0000844Bbc0Csc05i00')
2013-02-25 05:56:23,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4'}
2013-02-25 05:56:23,096 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,096 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco'}
2013-02-25 05:56:23,096 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sp5100_tco', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,096 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v05ACp1002d0122dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-25 05:56:23,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'platform:microcode')
2013-02-25 05:56:23,097 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v0557p7000d0100dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,098 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2013-02-25 05:56:23,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2013-02-25 05:56:23,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,098 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2013-02-25 05:56:23,098 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,099 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid'}
2013-02-25 05:56:23,099 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'mac_hid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,099 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'hid:b0003g0000v0000045Ep000000F9')
2013-02-25 05:56:23,148 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_microsoft'}
2013-02-25 05:56:23,148 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_microsoft', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,148 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc00ip00')
2013-02-25 05:56:23,149 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2013-02-25 05:56:23,149 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,149 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-25 05:56:23,150 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,150 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'k10temp'}
2013-02-25 05:56:23,150 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k10temp', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,151 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd0000844Bbc06sc01i00')
2013-02-25 05:56:23,154 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008259bc0Csc00i10')
2013-02-25 05:56:23,155 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci'}
2013-02-25 05:56:23,155 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,155 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-25 05:56:23,156 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw'}
2013-02-25 05:56:23,156 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,156 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'hid:b0003g0001v000005ACp00000204')
2013-02-25 05:56:23,157 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-02-25 05:56:23,157 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,157 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'hid:b0003g0001v00000557p00002214')
2013-02-25 05:56:23,159 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic'}
2013-02-25 05:56:23,159 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'hid_generic', 'jockey_handler': 'KernelModuleHandler'}
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'pci:v00001A03d00002000sv00001A03sd00002000bc03sc00i00')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x16399e0> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001033d00000194sv0000FFFFsd0000FFFFbc0Csc03i30')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0003v05ACp0204e0110-e0,1,4,k71,72,73,8E,8F,96,9B,A1,A3,A4,A5,A6,A8,D0,ram4,lsfw')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0B00:')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00008086d000010D3sv00001043sd00008369bc02sc00i00')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd0000844Bbc0Csc03i20')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v05E3p0608d3298dc09dsc00dp01ic09isc00ip00')
2013-02-25 05:56:23,159 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v05ACp0204d0122dc00dsc00dp00ic03isc01ip01')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0003v0557p2214e0110-e0,1,2,4,k110,111,112,113,114,r0,1,8,am4,lsfw')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v05ACp0204d0122dc00dsc00dp00ic03isc00ip00')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v0557p2214d0100dc00dsc00dp00ic03isc01ip01')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'platform:pcspkr')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'platform:SP5100 TCO timer')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d00004390sv00001043sd0000844Bbc01sc06i01')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v1D6Bp0001d0305dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0C04:')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0501:')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d00005A10sv00001043sd00008448bc06sc00i00')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2013-02-25 05:56:23,160 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0800:')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v1058p0730d1008dc00dsc00dp00ic08isc06ip50')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v0557p2214d0100dc00dsc00dp00ic03isc01ip02')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'x86cpu:vendor:0002:family:0010:model:0009:feature:,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,000B,000C,000D,000E,000F,0010,0011,0013,0017,0018,0019,001A,001C,0020,0021,0022,0023,0024,0025,0026,0027,0028,0029,002B,002C,002D,002E,002F,0030,0031,0034,0036,0037,0038,0039,003A,003B,003D,003E,003F,0064,0068,006A,006E,0070,0071,0074,0078,007A,007B,0080,0083,008D,0097,00C0,00C1,00C2,00C3,00C4,00C5,00C6,00C7,00C8,00C9,00CA,00CC,00CD,00D3,00E8,0105,0106,0107,0108,010D')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0003v0557p2214e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0103:')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,8,sfw')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0C01:')
2013-02-25 05:56:23,161 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0902:bd12/03/2010:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnKGP(M)E-D16:rvrRev1.xxG:cvnChassisManufacture:ct3:cvrChassisVersion:')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v000010DEd000011C0sv00003842sd00002662bc03sc00i00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0000:')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0003v05ACp0204e0110-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B3,B4,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,3,4,sfw')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc01ip01')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v1D6Bp0003d0305dc09dsc00dp03ic09isc00ip00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v1D6Bp0002d0305dc09dsc00dp01ic09isc00ip00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d0000439Csv00001043sd0000844Bbc01sc01i8a')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v000010DEd00000E0Bsv00003842sd00002662bc04sc03i00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,8,')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0200:')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d00004385sv00001043sd0000844Bbc0Csc05i00')
2013-02-25 05:56:23,162 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v05ACp1002d0122dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0100:')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'platform:microcode')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v0557p7000d0100dc09dsc00dp00ic09isc00ip00')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'input:b0003v045Ep00F9e0111-e0,1,2,3,4,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8B,8C,8E,90,96,98,9B,9C,9E,9F,A1,A3,A4,A5,A6,A7,A8,A9,AB,AC,AD,AE,B0,B1,B2,B3,B4,B5,B6,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,CE,CF,D0,D1,D2,D4,D8,D9,DB,DF,E4,E7,E8,E9,EA,EB,F0,F1,100,110,111,112,113,114,161,162,166,16A,16E,172,174,176,178,179,17A,17B,17C,17D,17F,180,182,183,185,188,189,18C,18D,18E,18F,190,191,192,193,195,198,199,19A,1A0,1A1,1A2,1A3,1A4,1A5,1A6,1A7,1A8,1A9,1AA,1AB,1AC,1AD,1AE,1B0,1B1,1B7,1BA,r0,1,6,7,8,9,A,B,a20,m4,lsfw')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'hid:b0003g0000v0000045Ep000000F9')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'usb:v045Ep00F9d0002dc00dsc00dp00ic03isc00ip00')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd0000844Bbc06sc01i00')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008259bc0Csc00i10')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'serio:ty06pr00id00ex00')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'hid:b0003g0001v000005ACp00000204')
2013-02-25 05:56:23,163 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'hid:b0003g0001v00000557p00002214')
2013-02-25 05:56:23,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'pci:v00001A03d00002000sv00001A03sd00002000bc03sc00i00')
2013-02-25 05:56:23,164 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x1991638> about HardwareID('modalias', 'acpi:PNP0C02:')
2013-02-25 05:57:36,683 DEBUG: Installing package: nvidia-current-updates
2013-02-25 05:57:37,674 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.000000
2013-02-25 05:57:37,676 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.000000
2013-02-25 05:57:37,710 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.000000
2013-02-25 05:57:37,766 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.000000
2013-02-25 05:57:37,824 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.003711
2013-02-25 05:57:38,008 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.102395
2013-02-25 05:57:38,009 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.102395
2013-02-25 05:57:38,064 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.104031
2013-02-25 05:57:38,229 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.228881
2013-02-25 05:57:38,229 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.228881
2013-02-25 05:57:38,288 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 0.232587
2013-02-25 05:57:38,789 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 1.042417
2013-02-25 05:57:39,290 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 1.881318
2013-02-25 05:57:39,791 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 3.002622
2013-02-25 05:57:40,293 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 4.128079
2013-02-25 05:57:40,794 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 5.288835
2013-02-25 05:57:41,295 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 6.717459
2013-02-25 05:57:41,797 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 7.905210
2013-02-25 05:57:42,298 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 9.063891
2013-02-25 05:57:42,799 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 10.322243
2013-02-25 05:57:43,301 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 11.599283
2013-02-25 05:57:43,802 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 13.088125
2013-02-25 05:57:44,303 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 14.616420
2013-02-25 05:57:44,805 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 16.171710
2013-02-25 05:57:45,306 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 17.573339
2013-02-25 05:57:45,807 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 18.837921
2013-02-25 05:57:46,309 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 19.959224
2013-02-25 05:57:46,810 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 21.169817
2013-02-25 05:57:47,311 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 22.604670
2013-02-25 05:57:47,813 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 24.396679
2013-02-25 05:57:48,314 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 26.556227
2013-02-25 05:57:48,815 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 28.825829
2013-02-25 05:57:49,317 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 31.095430
2013-02-25 05:57:49,818 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 33.363116
2013-02-25 05:57:50,319 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 35.615945
2013-02-25 05:57:50,820 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 37.881394
2013-02-25 05:57:51,322 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 40.117771
2013-02-25 05:57:51,823 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 42.385296
2013-02-25 05:57:52,325 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 44.656974
2013-02-25 05:57:52,826 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 46.909964
2013-02-25 05:57:53,327 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 49.175413
2013-02-25 05:57:53,829 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 51.447091
2013-02-25 05:57:54,330 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 53.712539
2013-02-25 05:57:54,831 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 55.967605
2013-02-25 05:57:55,333 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 58.212289
2013-02-25 05:57:55,834 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 60.020910
2013-02-25 05:57:56,336 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 61.385163
2013-02-25 05:57:56,837 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 62.743186
2013-02-25 05:57:57,338 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 64.115745
2013-02-25 05:57:57,840 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 65.457684
2013-02-25 05:57:58,341 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 66.829715
2013-02-25 05:57:58,842 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 68.231344
2013-02-25 05:57:59,343 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 69.601827
2013-02-25 05:57:59,845 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 70.959850
2013-02-25 05:58:00,346 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 72.363556
2013-02-25 05:58:00,847 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 73.729885
2013-02-25 05:58:01,348 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 75.081679
2013-02-25 05:58:01,850 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 76.493691
2013-02-25 05:58:02,351 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 77.833026
2013-02-25 05:58:02,852 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 79.240885
2013-02-25 05:58:03,353 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 80.536613
2013-02-25 05:58:03,855 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 81.951379
2013-02-25 05:58:04,356 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 83.269272
2013-02-25 05:58:04,857 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 84.672978
2013-02-25 05:58:05,359 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 86.031001
2013-02-25 05:58:05,860 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 87.426401
2013-02-25 05:58:06,361 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 88.817648
2013-02-25 05:58:06,863 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 90.215125
2013-02-25 05:58:07,364 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 91.604295
2013-02-25 05:58:07,865 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 92.974777
2013-02-25 05:58:08,367 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 94.386789
2013-02-25 05:58:08,868 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 95.767654
2013-02-25 05:58:09,369 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.150595
2013-02-25 05:58:09,499 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.370676
2013-02-25 05:58:09,500 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.370676
2013-02-25 05:58:09,555 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.372313
2013-02-25 05:58:09,559 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.389517
2013-02-25 05:58:09,560 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.389517
2013-02-25 05:58:09,619 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 97.395302
2013-02-25 05:58:10,120 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 98.487535
2013-02-25 05:58:10,621 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 99.851788
2013-02-25 05:58:10,688 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='amd64' id:16005L> 100.000000
2013-02-25 05:58:10,989 DEBUG: install progress dpkg-exec 0.000000
2013-02-25 05:58:11,504 DEBUG: install progress dkms 0.000000
2013-02-25 05:58:11,605 DEBUG: install progress dkms 4.000000
2013-02-25 05:58:12,494 DEBUG: install progress dkms 8.000000
2013-02-25 05:58:12,613 DEBUG: install progress dkms 12.000000
2013-02-25 05:58:12,988 DEBUG: install progress fakeroot 12.000000
2013-02-25 05:58:13,089 DEBUG: install progress fakeroot 16.000000
2013-02-25 05:58:13,358 DEBUG: install progress fakeroot 20.000000
2013-02-25 05:58:13,454 DEBUG: install progress fakeroot 24.000000
2013-02-25 05:58:13,977 DEBUG: install progress nvidia-current-updates 24.000000
2013-02-25 05:58:13,978 DEBUG: install progress nvidia-current-updates 28.000000
2013-02-25 05:58:23,019 DEBUG: install progress nvidia-current-updates 32.000000
2013-02-25 05:58:23,091 DEBUG: install progress nvidia-current-updates 36.000000
2013-02-25 05:58:23,491 DEBUG: install progress screen-resolution-extra 36.000000
2013-02-25 05:58:23,592 DEBUG: install progress screen-resolution-extra 40.000000
2013-02-25 05:58:23,792 DEBUG: install progress screen-resolution-extra 44.000000
2013-02-25 05:58:23,855 DEBUG: install progress screen-resolution-extra 48.000000
2013-02-25 05:58:24,221 DEBUG: install progress nvidia-settings-updates 48.000000
2013-02-25 05:58:24,322 DEBUG: install progress nvidia-settings-updates 52.000000
2013-02-25 05:58:24,625 DEBUG: install progress nvidia-settings-updates 56.000000
2013-02-25 05:58:24,704 DEBUG: install progress nvidia-settings-updates 60.000000
2013-02-25 05:58:24,802 DEBUG: install progress man-db 60.000000
2013-02-25 05:58:27,144 DEBUG: install progress dpkg-exec 60.000000
2013-02-25 05:58:27,207 DEBUG: install progress dkms 60.000000
2013-02-25 05:58:28,354 DEBUG: install progress dkms 64.000000
2013-02-25 05:58:28,439 DEBUG: install progress dkms 68.000000
2013-02-25 05:58:28,523 DEBUG: install progress fakeroot 68.000000
2013-02-25 05:58:28,614 DEBUG: install progress fakeroot 72.000000
2013-02-25 05:58:28,818 DEBUG: install progress fakeroot 76.000000
2013-02-25 05:58:28,902 DEBUG: install progress nvidia-current-updates 76.000000
2013-02-25 05:58:29,070 DEBUG: install progress nvidia-current-updates 80.000000
2013-02-25 05:58:30,711 DEBUG: install progress nvidia-current-updates 84.000000
2013-02-25 05:58:31,024 DEBUG: install progress screen-resolution-extra 84.000000
2013-02-25 05:58:31,141 DEBUG: install progress screen-resolution-extra 88.000000
2013-02-25 05:58:32,233 DEBUG: install progress screen-resolution-extra 92.000000
2013-02-25 05:58:32,286 DEBUG: install progress nvidia-settings-updates 92.000000
2013-02-25 05:58:32,353 DEBUG: install progress nvidia-settings-updates 96.000000
2013-02-25 05:58:32,625 DEBUG: install progress nvidia-settings-updates 100.000000
2013-02-25 05:58:32,760 DEBUG: install progress bamfdaemon 100.000000
2013-02-25 05:58:33,046 DEBUG: install progress initramfs-tools 100.000000
2013-02-25 05:58:50,093 DEBUG: Selecting previously unselected package dkms.
(Reading database ... 167665 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1.1_all.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_amd64.deb) ...
Selecting previously unselected package nvidia-current-updates.
Unpacking nvidia-current-updates (from .../nvidia-current-updates_304.51-0ubuntu1_amd64.deb) ...
Selecting previously unselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.15_all.deb) ...
Selecting previously unselected package nvidia-settings-updates.
Unpacking nvidia-settings-updates (from .../nvidia-settings-updates_304.51-0ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.2.0.3-1.1ubuntu1.1) ...
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up nvidia-current-updates (304.51-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current-updates/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-current-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match System manufacturer with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match System manufacturer with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-304.51 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-17-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Setting up screen-resolution-extra (0.15) ...
Setting up nvidia-settings-updates (304.51-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-settings-updates/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic

2013-02-25 05:58:50,253 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-25 05:58:50,254 WARNING: /sys/module/nvidia_current_updates/drivers does not exist, cannot rebind nvidia_current_updates driver
2013-02-25 06:03:22,274 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2013-02-25 06:03:22,275 WARNING: /sys/module/nvidia_current_updates/drivers does not exist, cannot rebind nvidia_current_updates driver

```

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 

What BIOS do you have ? We need to turn that card off.



I don't know how to answer that.  How can I look up what you're looking for?

---

### Post by matt_symes on 2013-02-25
Hi

This is turning a bit problematic.

```
sudo apt-get install dmidecode
```

```
sudo dmidecode -t 0
```

Post back.

Kind regards

---

### Post by trump600 on 2013-02-25
I hope it's just the issue that's problematic and not me.  I hate to be a nuisance.
> **matt_symes said:**
> 
Post back.

```

# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 0902   
	Release Date: 12/03/2010
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.15

```

My continued thanks!

---

### Post by matt_symes on 2013-02-25
Hi

> I hope it's just the issue that's problematic and not me.  I hate to be a nuisance.

You're fine. Dont worry. It's just that everything we have tried so far with the  new graphics card has not worked :)

In your bois do you have an option 

```
Primary Graphics Adapter
```under 

```
PNP/PCI Configuration
```You may be able to disable on board graphics there.

From here

[http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/Boards/Motherboards/MicroStar/MS6309/6309-3%28ami%29.pdf]("http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/Boards/Motherboards/MicroStar/MS6309/6309-3%28ami%29.pdf")

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 
In your bois do you have an option 

```
Primary Graphics Adapter
```under 

```
PNP/PCI Configuration
```You may be able to disable on board graphics there.


Under Advanced PCI/PnP Settings, I have only one option:

```

Plug and Play O/S   No/Yes

```

The only place I can find mention of anything related to graphics is under:

```

Chipset Configuration

```
```

SR5690 Configuration

```
```

VGA ROM Boot Priority

```

---

### Post by matt_symes on 2013-02-25
Hi

What options do you have under

```
VGA ROM Boot Priority
```

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> Hi

What options do you have under

```
VGA ROM Boot Priority
```

Kind regards

PCIE VGA Card
or
Onboard VGA

---

### Post by matt_symes on 2013-02-25
Hi

Select the option PCIE VGA Card.

Save the settings and exit the BIOS. 

reboot the PC.

Tell me what happens.

Kind regards

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> Hi

Select the option PCIE VGA Card.

Save the settings and exit the BIOS. 

reboot the PC.

Tell me what happens.

Kind regards

This is when the screen gets distorted.  However, I found a manual on my motherboard:

[HTML]http://www.manualowl.com/m/Asus/KGPE-D16/Manual/271267[/HTML]

It shows that disabling the onboard graphics takes a manual flip of a jumper on the board itself.  I'm going to shut down, flip the jumper, make sure the PCIE VGA Card is selected, then provide an update.

---

### Post by matt_symes on 2013-02-25
Hi

Excellent. I think we are making progress.

When it boots to the desktop can you post the xorg log file again.

```
gedit /var/log/Xorg.0.log
```

I want to take a look at it under the new card and see where we are.

Kind regards

---

### Post by trump600 on 2013-02-25
With the onboard graphics disabled and the new GPU giving a distorted screen, I can't open gedit to see the log.  However, I did think of your previous steps and looked into this:

```
sudo lshw -c display 
```

I don't want to type in the return unless you want to see it, but the onboard card definitely isn't represented there like it was before.

Are there any assumptions we can make?

---

### Post by matt_symes on 2013-02-25
Hi

Excellent. As long as the onboard graphics is disabled then we are making progress.

Open a terminal and type (be careful typing if you are having trouble seeing the display, take your time)

```
sudo apt-get install -y nvidia-current
```

Then type

```
sudo sed -i 's/nouveau//g' /etc/modules
```

Finally 

```
sudo reboot
```

Then cross your fingers :D

Kind regards
**[]("http://nouveau.freedesktop.org/")**

---

### Post by trump600 on 2013-02-25
> **matt_symes said:**
> 
Then cross your fingers :D


I crossed my fingers and smiled too, but it didn't work :(

One thing I can see through the distortion is that the icons are quite large on the screen.  Could it possibly be as simple as a resolution problem?  

I have to leave for work in about 20 minutes.  Any resources you can point me toward for when I get home would be greatly appreciated, and we can talk later about how I can repay your generosity.

---

### Post by matt_symes on 2013-02-25
HI

I do this for free. Don't worry about anything.

It may be a resolution problem and we can change that easily if everything else is good. I want to look at the log at some point.

I think we are making progress as we have the new card working, just not working well yet :D.

Any chance you can upload a photo of the screen for me to see ? If you don't have time now then after work is fine.

Kind regards

---

### Post by matt_symes on 2013-02-25
Hi

After looking at the photo, you either have a broken nvidia graphics card or major problems with your scan lines.

To test the first can you boot from a LiveCD/USB and see if you see the same effect. When was the last time you used the card ? Are you confident its good ?

Did you create an xorg.conf file ?

I suspect it's still loading the vesa driver.

We need to get the log files to see what is happening. You can do that from a console assuming that does not have the same problem.

If the card is not broken we may be able to create some valid modelines for it.

Kind regards

---

### Post by trump600 on 2013-02-26
Been home from work for a while, but as an FYI, the machine also runs a dedicated Minecraft server, so I was waiting for peak hours to finish up so I could shut down and get back at this.  Creating a new USB boot drive to test.  I'll let you know what I find out.

---

### Post by trump600 on 2013-02-26
> **matt_symes said:**
> 
To test the first can you boot from a LiveCD/USB and see if you see the same effect. When was the last time you used the card ? Are you confident its good ?


I'm starting to get smart about this :D.  I was having a difficult time booting from the USB (as I did when I first installed), but I realized that we really just wanted to see if a different session produced the same result.  So at the login, instead of logging in as myself, I started a guest session.  Crystal clear. :D

> **matt_symes said:**
> 
Did you create an xorg.conf file ?


Since I was able to get a GUI I could read, I created the file and saved it to a flash drive.  The file is too large to post here, so I uploaded it elsewhere: [http://www.datafilehost.com/download-7a351c95.html](http://www.datafilehost.com/download-7a351c95.html)

---

### Post by matt_symes on 2013-02-26
Hi

It's good to know that the display was fine from a USB. It sounds like we have a config problem then.

I will take a look at the logs and post back.

I am going to be a bit busy over the next couple of days but i will post back when i can.

EDIT:

```

[    17.015] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    17.015] (EE) NVIDIA:     system's kernel log for additional error messages.
[    17.015] (EE) Failed to load module "nvidia" (module-specific error, 0)
```It is not loading the nvidia driver.I believe this log file is at /var/log/kern.log or /var/log/syslog or /var/log/demsg. Please post these log files.

At the moment, we are still falling back to the vesa driver at low resolution which is causing you the problems.

There are a number of modes we can try to see if we can fix the resolution for you with the vesa driver.

To set a new mode (screen resolution) you use the command 

```
xrandr -s <mode>
```These are the available mode lines. Most will not work but, hopefully, one or two will.

```

"1920x1080"
 "800x600"
"640x480"
 "720x400"
"1280x1024"
 "1024x768"
"832x624"
"800x600"
"1152x864"
"1280x960"
"1280x1024"
"1440x900"
 "1680x1050"
"1920x1080"
"1280x720"
"1280x800"
```Open a terminal and type

```
xrandr -s "1920x1080"
```That will change the mode. Experiement with the other ones as well and we may get a working resolution using the vesa driver.

Another example

```
xrandr -s "800x600"
```Post back on efficacy.

I'll post back when i can. get those other log files :D

Kind regards

---

### Post by matt_symes on 2013-02-26
Hi

Another thought.

If you can boot into LiveUSB again take a note of the resolution. 

You can do this with xrandr again.

This is mine.

```

matthew-S206:/home/matthew % xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
[COLOR=Red]   1366x768       60.0*+[/COLOR]
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
matthew-S206:/home/matthew % 
```The one with the star and plus signs next to it are the native resolution.

Make a note of all those resolutions as they are the ones to try. Try the native resolution first.

If you are have trouble with the terminal when logged in to the dist on the computer and not the liveUSB then heres another thought.

From the liveUSB create a file on the desktop of the dist on the computer under your account. Add the xrandr -s "xxxxx" command to it and make it executable.

chmod 777 file_name.

Make sure you position the file at a location where you will be able to see it when booted into the dist on your pc.

Then when you log into your account on the computer you only have to click that file on your desktop to change the resolution.

Kind regards

---

### Post by matt_symes on 2013-02-26
FTR. Here's what the display is currently showing.

---

### Post by Uranium78 on 2013-02-26
When I installed my Nvidia Driver (GForce GTX650) at first I downloaded the driver for the official site (linux vertion and the apropriate version for your card) [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
I put it in the Downloads folder the pressed ctrl+alt+F1 to go into the terminal. Then I typed this to stop the x server:
```
sudo service lightdm stop 
```
Then this to install the driver:
```
cd Downloads
sudo sh [The file you just downloaded for the NVidia site]
```
I followed the instructions accepting everything (even the errors) and that was it.
The second way I did it was to create a new partition for /home store my files in it and then re install Ubuntu but I press the something else when it asks me where to install. I choose a / partition (root) which is recommended to not have any important files in for it will be deleted. The I choose the The /home partition with all my files in it and start the installation. At the end my driver was already installed and configured. Just watch out because some of the kernel updates deconfigure it and so you have to re install it (don't create a new /home or / partition just reuse the same ones).
I hope this works ;)
PS:
The second technique is longer and will install your system in a special way so use it if you are a more advanced linux user or you don't have any valuable files. Give the / partition approx 1/3 of the /home partition (My /home partition is 100Gb so my / is 35Bg and it works fine and I'm using it at the moment).

---

### Post by trump600 on 2013-02-26
> **matt_symes said:**
> 

To set a new mode (screen resolution) you use the command 

```
xrandr -s <mode>
```



I had to blindly open a terminal to try this because the display wouldn't open from the Ctrl+Alt+F2 console, but I managed to do it without seeing what I was doing, and everything came in clear at 1920x1080.  The new problem is that I don't have a taskbar.  The difference is that the taskbar doesn't show up under ANY of the users I log into, whereas the resolution issue was just with my main login.  Problem after problem... :p

After a little research (and having Ubuntu hint at me the Compiz was continually crashing), I think it's being caused by Compiz after attempting to install the nvidia driver.  I'll deal with this later unless it is at the core of the original problem.

> **matt_symes said:**
> 
It is not loading the nvidia driver.I believe this log file is at /var/log/kern.log or /var/log/syslog or /var/log/demsg. Please post these log files.


kern.log:
[http://www.datafilehost.com/download-65f102ad.html](http://www.datafilehost.com/download-65f102ad.html)

syslog:
[http://www.datafilehost.com/download-2b7681b3.html](http://www.datafilehost.com/download-2b7681b3.html)

The demsg does not exist.

> **Uranium78 said:**
> Then I typed this to stop the x server:
```
sudo service lightdm stop 
```


I have to wonder if I'd be in the same boat right now if I knew this was the correct way to stop the x server...  :rolleyes:

---

### Post by matt_symes on 2013-02-26
Hi

 > and everything came in clear at 1920x1080.

That is great news. You now have a fall back position with the vesa driver.

> The new problem is that I don't have a taskbar.  The difference is that  the taskbar doesn't show up under ANY of the users I log into, whereas  the resolution issue was just with my main login.  Problem after  problem...

We can look at each problem as they arise. Bear in mind you are using the vesa driver at the moment.

I'll take a look at the logs now and post back soon.

Kind regards

---

### Post by matt_symes on 2013-02-26
Hi

Let's see if we can make this easy. 

Make sure you are connected to the internet.

Open a terminal and type

```
sudo apt-get remove --purge nvidia-current
```then type

```
jockey-gtk
```The show bring up the driver wizard.

select nvidia-current

That should, hopefully, insytall the driver and any other packages missing.

I say hopefully because i have not used an nvidia card for a very long time :D

Let's see where this takes us.

Problems with X are
```

[    17.138] (EE) [drm] failed to open device
[    17.239] (EE) [drm] failed to open device

[    17.239] (EE) open /dev/dri/card0: No such file or directory
[    17.239] (EE) open /dev/dri/card0: No such file or directory
```Kind regards

---

### Post by trump600 on 2013-02-27
> **matt_symes said:**
> 
```
jockey-gtk
```The show bring up the driver wizard.


Return, with my input as well:

```

trump@BTCraft:~$ jockey-gtk
The program 'jockey-gtk' is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk
trump@BTCraft:~$ sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia dkms k3b k3b-data k3b-i18n kde-l10n-engb
  kde-l10n-zhcn kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
  language-pack-kde-en libflac++6 libk3b6 libkcddb4
  linux-headers-3.5.0-17 nvidia-settings-updates screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  jockey-gtk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/3,158 B of archives.
After this operation, 53.2 kB of additional disk space will be used.
Selecting previously unselected package jockey-gtk.
(Reading database ... 174961 files and directories currently installed.)
Unpacking jockey-gtk (from .../jockey-gtk_0.9.7-0ubuntu11_all.deb) ...
Setting up jockey-gtk (0.9.7-0ubuntu11) ...
trump@BTCraft:~$ jockey-gtk
The program 'jockey-gtk' is currently not installed. You can install it by typing:
sudo apt-get install jockey-gtk
trump@BTCraft:~$ sudo apt-get install jockey-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jockey-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia dkms k3b k3b-data k3b-i18n kde-l10n-engb
  kde-l10n-zhcn kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
  language-pack-kde-en libflac++6 libk3b6 libkcddb4
  linux-headers-3.5.0-17 nvidia-settings-updates screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by matt_symes on 2013-02-27
Hi

What is it with your computer :)

First a bit of house-keeping for it while i digest the jockey issues.

```
sudo apt-get auto-remove
```Could you also post the output of
```

uname -a
cat /etc/lsb-release
```

```
apt-cache policy jockey-gtk
dpkg -l jockey-gtk
```

Kind regards

---

### Post by trump600 on 2013-02-27
> **matt_symes said:**
> Could you also post the output of
```

uname -a
cat /etc/lsb-release
```

```
apt-cache policy jockey-gtk
dpkg -l jockey-gtk
```

```

trump@BTCraft:~$ uname -a
Linux BTCraft 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:27:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
trump@BTCraft:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
trump@BTCraft:~$ apt-cache policy jockey-gtk
jockey-gtk:
  Installed: 0.9.7-0ubuntu11
  Candidate: 0.9.7-0ubuntu11
  Version table:
 *** 0.9.7-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
trump@BTCraft:~$ dpkg -l jockey-gtk
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  jockey-gtk     0.9.7-0ubunt all          transitional package for driver m
trump@BTCraft:~$ 
```

---

### Post by matt_symes on 2013-02-27
Hi

I was going to suggest that we use jockey-gtk to install the nvidia drivers in 12.10 until i can across this article

[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

I am now unsure what to do.

I have always prefered the manual way of installing things anyway as i can get more feedback about what the system is doing.

I am going to do a bit more research as to whether this is a major issue using jokey in 12.10 with the nvidia drivers.

Please be patient as i do not want to damage your system.

EDIT: 

A quick Google search and we are going to use the  manual method of installing the drivers and not jockey.

Do you think you can follow the steps in that how-to for the manual method. 

It looks pretty good and accurate to me and would be  the steps i would be looking at performing.

Kind regards

---

### Post by matt_symes on 2013-02-27
Hi

This has been a useful thread for me as i have just found out that jockey-gtk was dropped for Ubuntu 12.10.

I am a bit behind the times with Ubuntu and nvidia.

The additional drivers dialog seems to have had problems with the nvidia drivers as well.

I hope the best way is using the manual install as i stated in my last post.

I am up for advice from others here.

There is one last thing i would like to check before we proceed. Can you post the output of

```
dpkg -l | grep nvidia
```

Kind regards

---

### Post by schragge on 2013-02-27
Well, *jockey-gtk* is now a transitional dummy package that actually installs *software-properties-gtk*. From what I see, it was successfully installed. To invoke it, try
```

software-properties-gtk

```

But *jockey-kde* is still there in the repositories and can be installed. That's what dedoimedo tried, but jockey-kde failed at him.

---

### Post by matt_symes on 2013-02-27
Hi 

Thanks for the input [[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515"). I did not know that.

I think the manual method of installing may be the way to go then.

Kind regards

---

### Post by schragge on 2013-02-27
I guess *NVidia EVGA GeForce GTX660* is supported by *nvidia-current* from restricted repository (version 304.43). This is from the [README.txt](http://http.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/supportedchips.html) of that package:
```

NVIDIA GPU product                    Device PCI ID*     VDPAU features
...
GeForce GTX 660M                      0x0FD4             D
GeForce GTX 660M                      0x0FE0             D
GeForce GTX 660 Ti                    0x1183             D

```

[highlight]Update 1.[/highlight]
Hmm, I don't see there the Device PCI ID 11C0 that we have got:
```

NVIDIA Corporation Device 010de:11c0] (rev a1)

```
Still, it's worth trying.

[highlight]Update 2.[/highlight]
Well, 11C0 is listed as supported in [version 304.64](http://us.download.nvidia.com/XFree86/Linux-x86_64/304.64/README/supportedchips.html) which is *nvidia-current* from *ppa:[i]*xorg-edgers/ppa[/I] and in [version 310.14](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.14/README/supportedchips.html) which is *nvidia-experimental-310* from *quantal-updates*.

:?: What do you think, should we first try the older driver from *restricted*,  install *nvidia-experimental-310*, or directly go and install the latest version from the PPA?

---

### Post by matt_symes on 2013-02-27
Hi

@[[COLOR=#000000]schragge[/COLOR]]("http://ubuntuforums.org/member.php?u=1783515")

I think we should go for the one we are sure is supported.

Cheers for your input here. I'm an ATI guy and not so hot with nvidia.

I will be to and from keyboard for the next couple of days.

Kind regards

---

### Post by schragge on 2013-02-27
OK, then I'd proceed like this
```

software-properties-gtk

```
and ensure that *restricted* is enabled.
[center][[img]http://screenshots.debian.net/screenshots/s/software-properties-gtk/9302_small.png[/img]](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png)[/center]
 After that,
```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install ppa-purge nvidia-{current,settings} 

```
I've included ppa-purge to be sure we can then easily remove the PPA repository from command line if something goes wrong.

---

### Post by trump600 on 2013-02-27
> **schragge said:**
> OK, then I'd proceed like this
```

software-properties-gtk

```
and ensure that *restricted* is enabled.
[center][[img]http://screenshots.debian.net/screenshots/s/software-properties-gtk/9302_small.png[/img]](http://screenshots.debian.net/screenshots/s/software-properties-gtk/9302_large.png)[/center]
 After that,
```

sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install ppa-purge nvidia-{current,settings} 

```
I've included ppa-purge to be sure we can then easily remove the PPA repository from command line if something goes wrong.

I followed this.  I'm about to reboot to check efficacy, but I wanted to show the install log so we can see if anything didn't go correctly. 

```
trump@BTCraft:~$ sudo apt-add-repository ppa:xorg-edgers/ppa
[sudo] password for trump: 
You are about to add the following PPA to your system:
 == Xorg packages fresh from git ==

Currently supported releases are Precise/12.04, Quantal/12.10 and Raring/13.04

If you are still using Natty/11.04 then please upgrade since those packages will be removed soon!

* For less fresh, more stable updates, see https://launchpad.net/~ubuntu-x-swat/+archive/x-updates

* WARNING: Do not use this PPA with the precise X backport stacks.

See https://wiki.ubuntu.com/XorgOnTheEdge for a script that installs and runs the test packages in a live CD/media session, for quick and easy temporary testing.

To revert to official packages, install the ppa-purge package and run "sudo ppa-purge xorg-edgers". Note: This currently has issues in oneiric because ppa-purge there does not work with multiarch. ppa-purge packages from this PPA do purge correctly on precise and newer.

== New features ==

June 29th, 2012: SNA is now on by default on intel. If you have problems (such as screen corruption, parts of the screen not updating, or crashes with intel_drv.so in the Xorg.0.log backtrace), save this as /etc/X11/xorg.conf

Section "Device"
********Identifier      "intel"
********Driver          "intel"
********Option          "AccelMethod"   "uxa"
EndSection

== Important notice ==

This PPA is currently meant to be used as a whole. Please do _not_ individually install packages from it, add it to your sources and let your package manager pull in every update. The packages here build against each other and compile different features based on whats available at build time. Do not assume that because it lets you install a DDX with just the driver and libdrm update that it will work.  These packages are made with scripts that use the the current packages as the base, so some dependencies can be wrong and your package manager will not resolve that for you.  If you want to individually install something from here, grab the source and rebuild it in your current environment instead.

** Please do not publish instructions for how to install from this archive without linking to this page! Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. **
 More info: https://launchpad.net/~xorg-edgers/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp5zfdyv/secring.gpg' created
gpg: keyring `/tmp/tmp5zfdyv/pubring.gpg' created
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp5zfdyv/trustdb.gpg: trustdb created
gpg: key 8844C542: public key "Launchpad PPA for xorg crack pushers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
trump@BTCraft:~$ sudo apt-get update
[sudo] password for trump: 
Ign http://security.ubuntu.com quantal-security InRelease
Ign http://us.archive.ubuntu.com quantal InRelease                        
Ign http://extras.ubuntu.com quantal InRelease                            
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]
Ign http://us.archive.ubuntu.com quantal-updates InRelease           
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]  
Ign http://ppa.launchpad.net quantal InRelease                            
Ign http://us.archive.ubuntu.com quantal-backports InRelease              
Get:3 http://extras.ubuntu.com quantal Release.gpg [72 B]                 
Hit http://us.archive.ubuntu.com quantal Release.gpg                      
Get:4 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]    
Ign http://ppa.launchpad.net quantal InRelease                        
Hit http://extras.ubuntu.com quantal Release                              
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg            
Get:5 http://security.ubuntu.com quantal-security/main Sources [34.4 kB]
Hit http://us.archive.ubuntu.com quantal Release                          
Hit http://ppa.launchpad.net quantal Release.gpg                          
Get:6 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]      
Hit http://extras.ubuntu.com quantal/main Sources                         
Get:7 http://ppa.launchpad.net quantal Release.gpg [316 B]                
Get:8 http://security.ubuntu.com quantal-security/restricted Sources [14 B]
Get:9 http://security.ubuntu.com quantal-security/universe Sources [15.5 kB]
Hit http://extras.ubuntu.com quantal/main amd64 Packages                  
Hit http://ppa.launchpad.net quantal Release                              
Get:10 http://security.ubuntu.com quantal-security/multiverse Sources [700 B]
Hit http://us.archive.ubuntu.com quantal-backports Release                
Get:11 http://security.ubuntu.com quantal-security/main amd64 Packages [92.9 kB]
Hit http://extras.ubuntu.com quantal/main i386 Packages                   
Hit http://us.archive.ubuntu.com quantal/main Sources                     
Get:12 http://ppa.launchpad.net quantal Release [11.9 kB]                 
Hit http://us.archive.ubuntu.com quantal/restricted Sources               
Hit http://us.archive.ubuntu.com quantal/universe Sources                 
Hit http://us.archive.ubuntu.com quantal/multiverse Sources               
Get:13 http://security.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Hit http://us.archive.ubuntu.com quantal/main amd64 Packages              
Get:14 http://security.ubuntu.com quantal-security/universe amd64 Packages [41.7 kB]
Hit http://ppa.launchpad.net quantal/main Sources                         
Hit http://us.archive.ubuntu.com quantal/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com quantal/universe amd64 Packages          
Get:15 http://security.ubuntu.com quantal-security/multiverse amd64 Packages [1,155 B]
Hit http://ppa.launchpad.net quantal/main amd64 Packages                  
Hit http://us.archive.ubuntu.com quantal/multiverse amd64 Packages        
Get:16 http://security.ubuntu.com quantal-security/main i386 Packages [92.4 kB]
Hit http://ppa.launchpad.net quantal/main i386 Packages                   
Get:17 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Hit http://us.archive.ubuntu.com quantal/main i386 Packages               
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages         
Get:18 http://security.ubuntu.com quantal-security/universe i386 Packages [42.3 kB]
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages           
Get:19 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,397 B]
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages         
Get:20 http://ppa.launchpad.net quantal/main Sources [24.6 kB]            
Hit http://us.archive.ubuntu.com quantal/main Translation-en              
Get:21 http://security.ubuntu.com quantal-security/main Translation-en [49.0 kB]
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en        
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en 
Ign http://extras.ubuntu.com quantal/main Translation-en_US               
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en        
Hit http://security.ubuntu.com quantal-security/restricted Translation-en 
Ign http://extras.ubuntu.com quantal/main Translation-en                  
Get:22 http://ppa.launchpad.net quantal/main amd64 Packages [34.6 kB] 
Hit http://us.archive.ubuntu.com quantal/universe Translation-en          
Get:23 http://us.archive.ubuntu.com quantal-updates/main Sources [80.3 kB]
Hit http://security.ubuntu.com quantal-security/universe Translation-en   
Get:24 http://ppa.launchpad.net quantal/main i386 Packages [33.6 kB]      
Get:25 http://us.archive.ubuntu.com quantal-updates/restricted Sources [1,302 B]
Get:26 http://us.archive.ubuntu.com quantal-updates/universe Sources [79.0 kB]
Get:27 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [2,932 B]
Get:28 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [210 kB]
Get:29 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [3,048 B]
Ign http://security.ubuntu.com quantal-security/main Translation-en_US    
Get:30 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [168 kB]
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Get:31 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [7,938 B]
Get:32 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [209 kB]
Get:33 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [3,067 B]
Ign http://ppa.launchpad.net quantal/main Translation-en_US               
Get:34 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [169 kB]
Ign http://ppa.launchpad.net quantal/main Translation-en 
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en                
Get:35 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [8,109 B]
Hit http://us.archive.ubuntu.com quantal-updates/main Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://us.archive.ubuntu.com quantal-backports/main Sources
Hit http://us.archive.ubuntu.com quantal-backports/restricted Sources
Hit http://us.archive.ubuntu.com quantal-backports/universe Sources
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://us.archive.ubuntu.com quantal-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com quantal-backports/main i386 Packages     
Hit http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/universe i386 Packages 
Hit http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en    
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US           
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US     
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US     
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US       
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US   
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US 
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Fetched 1,519 kB in 9s (156 kB/s)                                         
Reading package lists... Done
trump@BTCraft:~$ sudo apt-get install ppa-purge nvidia-{current,settings}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms linux-headers-3.7.0-7 linux-headers-3.7.0-7-generic
  linux-headers-generic screen-resolution-extra
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed:
  dkms linux-headers-3.7.0-7 linux-headers-3.7.0-7-generic
  linux-headers-generic nvidia-current nvidia-settings ppa-purge
  screen-resolution-extra
0 upgraded, 8 newly installed, 0 to remove and 43 not upgraded.
Need to get 15.1 MB/82.9 MB of archives.
After this operation, 280 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal/main nvidia-settings amd64 304.51-0ubuntu2 [1,820 kB]
Get:2 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main linux-headers-3.7.0-7 all 3.7.0-7.15 [12.2 MB]
Get:3 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main linux-headers-3.7.0-7-generic amd64 3.7.0-7.15 [1,009 kB]
Get:4 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main linux-headers-generic amd64 3.7.0.7.11 [8,016 B]
Get:5 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ quantal/main ppa-purge all 0.2.8+bzr57+edgers1~quantal [5,896 B]
Fetched 15.1 MB in 16s (902 kB/s)                                         
Selecting previously unselected package dkms.
(Reading database ... 158089 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1.1ubuntu1.1_all.deb) ...
Selecting previously unselected package linux-headers-3.7.0-7.
Unpacking linux-headers-3.7.0-7 (from .../linux-headers-3.7.0-7_3.7.0-7.15_all.deb) ...
Selecting previously unselected package linux-headers-3.7.0-7-generic.
Unpacking linux-headers-3.7.0-7-generic (from .../linux-headers-3.7.0-7-generic_3.7.0-7.15_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_3.7.0.7.11_amd64.deb) ...
Selecting previously unselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_304.51.really.304.43-0ubuntu1_amd64.deb) ...
Selecting previously unselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.15_all.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_304.51-0ubuntu2_amd64.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr57+edgers1~quantal_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up dkms (2.2.0.3-1.1ubuntu1.1) ...
Setting up linux-headers-3.7.0-7 (3.7.0-7.15) ...
Setting up linux-headers-3.7.0-7-generic (3.7.0-7.15) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
Setting up linux-headers-generic (3.7.0.7.11) ...
Setting up nvidia-current (304.51.really.304.43-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match System manufacturer with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match System manufacturer with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.43 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Setting up screen-resolution-extra (0.15) ...
Setting up nvidia-settings (304.51-0ubuntu2) ...
update-alternatives: warning: alternative /usr/lib/nvidia-settings-updates/ld.so.conf (part of link group nvidia_settings_conf) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/nvidia_settings_conf is dangling; it will be updated with best choice
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode
Setting up ppa-purge (0.2.8+bzr57+edgers1~quantal) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-25-generic
trump@BTCraft:~$ 
```

---

### Post by schragge on 2013-02-27
Hmm, this is strange: *linux-headers-3.7.0-7* got installed
```

Setting up linux-headers-3.7.0-7 (3.7.0-7.15) ...
Setting up linux-headers-3.7.0-7-generic (3.7.0-7.15) ...

```
but
```

Building only for 3.5.0-25-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

```
Now, try
```

sudo apt-get upgrade

```
This should pull the newest nvidia driver from the PPA. Hopefully, this time it will also build it for the current kernel (3.7.0). If not, try to reboot into the previous kernel to check that at least the built nvidia driver works.

---

### Post by trump600 on 2013-02-27
> **schragge said:**
> 
Now, try
```

sudo apt-get upgrade

```
This should pull the newest nvidia driver from the PPA. 


I don't see anything for nvidia in here, but I see things that I thought we disabled.  Not continuing for now; waiting for further advice.
```

trump@BTCraft:~$ sudo apt-get upgrade

[sudo] password for trump: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages have been kept back:
  libgl1-mesa-dri linux-image-generic

The following packages will be upgraded:
  
flashplugin-installer 
libcairo-gobject2 
libcairo2 
libdbus-glib-1-2
  
libdrm-intel1 
libdrm-nouveau1a 
libdrm-nouveau2 
libdrm-radeon1 
libdrm2
  
libgl1-mesa-glx 
libglapi-mesa 
libgnutls26 
libkms1 
libpixman-1-0
  
libxatracker1 
linux-firmware 
linux-image-3.5.0-25-generic
  
linux-image-extra-3.5.0-25-generic 
linux-libc-dev xserver-common
  
xserver-xorg-core 
xserver-xorg-input-mouse 
xserver-xorg-input-synaptics
  
xserver-xorg-input-vmmouse 
xserver-xorg-video-ati
  
xserver-xorg-video-cirrus 
xserver-xorg-video-fbdev
  
xserver-xorg-video-intel 
xserver-xorg-video-mach64
  
xserver-xorg-video-neomagic 
xserver-xorg-video-nouveau
  
xserver-xorg-video-r128 
xserver-xorg-video-radeon 
xserver-xorg-video-s3
  
xserver-xorg-video-savage 
xserver-xorg-video-siliconmotion
  
xserver-xorg-video-sis 
xserver-xorg-video-sisusb
  
xserver-xorg-video-trident 
xserver-xorg-video-vesa
  
xserver-xorg-video-vmware

41 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

Need to get 69.7 MB of archives.

After this operation, 2,832 kB of additional disk space will be used.

Do you want to continue [Y/n]? 

```

> **schragge said:**
> 
Hopefully, this time it will also build it for the current kernel (3.7.0). If not, try to reboot into the previous kernel to check that at least the built nvidia driver works.

If you haven't kept up with the entire thread, I'm quite new to this.  Not looking for a hand-holder, but can you point me to a good resource on how to do this?



And for you, Matt:

> **matt_symes said:**
> 

There is one last thing i would like to check before we proceed. Can you post the output of

```
dpkg -l | grep nvidia
```


```
trump@BTCraft:~$ dpkg -l | grep nvidia

ii  nvidia-common                             1:0.2.71.1                                amd64        transitional package for ubuntu-drivers-common

ii  nvidia-current                            304.51.really.304.43-0ubuntu1             amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library

rc  nvidia-current-updates                    304.51-0ubuntu1                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library

ii  nvidia-settings                           304.51-0ubuntu2                           amd64        Tool for configuring the NVIDIA graphics driver

rc  nvidia-settings-updates                   304.51-0ubuntu2                           amd64        Tool for configuring the NVIDIA graphics driver
```


Thank you both; I won't be back for another 10 hours or so...

---

### Post by schragge on 2013-02-27
[highlight]Edit.[/highlight] See my next post. I think we're better off using another PPA.

> **trump600 said:**
> can you point me to a good resource on how to do this?Oh sorry. Sure, take a look at this page: [uhelp]community/Grub2[/uhelp]. When computer boots up, usually the Grub boot menu gets displayed:
[center][img]http://pix.toile-libre.org/upload/original/1353953772.png[/img][/center]But for some installations, this step is skipped. In this case, you can force display of the menu by pressing **Shift** key while booting. The first entry, *Ubuntu*, boots the latest installed kernel. Previously installed kernels are hidden under *Advanced options for Ubuntu*.

[list]
[*]The kernel you were running two days ago was 3.5.0-17 (so you said).
[*]The latest kernel for quantal (Ubuntu 12.10) is 3.5.0-25 from quantal-security (this is a security update)
[*]The PPA *xorg-edgers* that we've added contains kernel 3.7.0-7
[/list]

To build the nvidia driver, the package *linux-headers* for corresponding kernel is needed. We've installed linux-headers-3.7.0-7, but not the kernel itself. The graphics driver was built only for 3.5.0-25. I suppose, the kernel 3.5.0-25 is what you're currently running. To check this, please post the output of ```
uname -a
```

Obviously, the driver from PPA needs a newer kernel (3.7.0). From the notice you got when adding the PPA:
> 
This PPA is currently meant to be used as a whole. Please do _not_ individually install packages from it, add it to your sources and let your package manager pull in every update. The packages here build against each other and compile different features based on whats available at build time. Do not assume that because it lets you install a DDX with just the driver and libdrm update that it will work.  These packages are made with scripts that use the the current packages as the base, so some dependencies can be wrong and your package manager will not resolve that for you.  If you want to individually install something from here, grab the source and rebuild it in your current environment instead.
 This means that the only way to install the driver from PPA is by upgrading all requested packages.

In the list of packages to be upgraded, there're some that you definitely not need (like drivers for all graphic cards that come with Ubuntu), but upgrading them should make no harm. You can dry-run the upgrade with
```

sudo apt-get -s upgrade

```
to check what apt is actually going to do.

I see that two packages, *libgl1-mesa-dri* and *linux-image-generic*, are not going to be upgraded. That means that after *sudo apt-get upgrade* you may need to run
```
sudo apt-get dist-upgrade
``` to upgrade them. You can test this command with the **-s** option, too, to see what is going to get upgraded in this case.

To ensure that the package management system is in the healthy state, you can also run
```

sudo apt-get check
sudo dpkg -C

```
before doing the actual upgrade.

---

### Post by schragge on 2013-02-27
I've just found out that an nvidia driver supporting GTX 660 is also included in the [X Updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) PPA, which is less bleeding-edge than [uwiki]XorgOnTheEdge[/uwiki] we're trying to use now. So I'm glad **trump600** was cautious and didn't upgrade.

I suggest removing *xorg-edgers* and adding *ubuntu-x-swat* instead:
```

sudo ppa-purge xorg-edgers
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update

```

After that, I'd still like to see the output of
```

uname -a
sudo apt-get check
sudo dpkg -C
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package} ${Version}\n' nvidia\*

```
just to be sure we didn't screw up anything in the process.

---

### Post by trump600 on 2013-02-28
> **schragge said:**
> I'd still like to see the output of
```

uname -a
sudo apt-get check
sudo dpkg -C
dpkg-query -Wf'${db:Status-Abbrev}${binary:Package} ${Version}\n' nvidia\*

```
```

trump@BTCraft:~$ uname -a
Linux BTCraft 3.5.0-25-generic #38-Ubuntu SMP Mon Feb 18 23:27:42 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
trump@BTCraft:~$ sudo apt-get check
[sudo] password for trump: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
trump@BTCraft:~$ sudo dpkg -C
trump@BTCraft:~$ dpkg-query -Wf'${db:Status-Abbrev}${binary:Package} ${Version}\n' nvidia\*
un nvidia-173 
un nvidia-173-updates 
un nvidia-180-modaliases 
un nvidia-185-modaliases 
un nvidia-96 
un nvidia-96-updates 
ii nvidia-common 1:0.2.71.1
ii nvidia-current 304.51.really.304.43-0ubuntu1
un nvidia-current-experimental-304 
un nvidia-current-modaliases 
rc nvidia-current-updates 304.51-0ubuntu1
un nvidia-experimental-304 
ii nvidia-settings 304.51-0ubuntu2
un nvidia-settings-experimental-304 
un nvidia-settings-experimental-310 
rc nvidia-settings-updates 304.51-0ubuntu2
trump@BTCraft:~$ 
```

I feel like this looks like a success?  I'm trying to figure out how to test it...

---

### Post by schragge on 2013-03-01
Yes, this looks good. Now, **rc** before some packages indicates that while those packages themselves were removed (**r**), there are some configuration files for them left (**c**). Purge them with
```

sudo apt-get purge ^nvidia-.\*-updates

```

Then
```

sudo apt-get upgrade

```

And finally, if some packages are held back
```

sudo apt-get dist-upgrade

```

After that, reboot.

---

