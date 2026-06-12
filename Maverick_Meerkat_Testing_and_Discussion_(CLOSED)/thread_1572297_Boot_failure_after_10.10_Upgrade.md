---
title: "Boot failure after 10.10 Upgrade"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by DomesDKG on 2010-09-10
After upgrading to 10.10 the other day, when I boot my laptop it will only get as far as plymouth.  The purple screen with the orange dots plays normally, at native resolution, but then it just sits there with full orange dots and doesn't go to the login screen.
I tried booting recovery and choosing failsafe graphics, but this just gives me a black screen that goes nowhere.
Any ideas?

---

### Post by lisati on 2010-09-10
Moved to Maverick Meerkat Testing and Discussion. Please read the announcement at the top of the page.

---

### Post by DomesDKG on 2010-09-10
Thanks, didn't realize there was a different forum for 10.10

---

### Post by ktp on 2010-09-10
what video card do you have?  Also do you know what drivers you are using?

---

### Post by ranch hand on 2010-09-11
> **ktp said:**
> what video card do you have?  Also do you know what drivers you are using?
There you go again.

---

### Post by jerrylamos on 2010-09-11
> **DomesDKG said:**
> After upgrading to 10.10 the other day, when I boot my laptop it will only get as far as plymouth.  The purple screen with the orange dots plays normally, at native resolution, but then it just sits there with full orange dots and doesn't go to the login screen.
I tried booting recovery and choosing failsafe graphics, but this just gives me a black screen that goes nowhere.
Any ideas?
Try booting in recovery mode.to see if you can get a menu.
If so, go to the very bottom and select a command line prompt.
Enter:
lspci | grep VGA
to see what video graphics chip you have and report back here.

Another method would be at your orange dots screen try
Ctrl-Alt-F1
Sometimes this will give a command line, then do the lspci thing.

Jerry

---

### Post by ktp on 2010-09-11
> **ranch hand said:**
> There you go again.

i never learn from my mistakes. :D

---

### Post by VMC on 2010-09-11
> **ktp said:**
> i never learn from my mistakes. :D
LOL! Very funny. You should thank RH keeping you on the straight and narrow.

Back on topic. Try booting without "quiet" and see what progress is being made.

---

### Post by al090187 on 2010-09-12
Hi, I was having this same problem yesterday after upgrading from lynx. This morning, however, it doesnt get that far and just drops down to a shell. Entering the lspci command gets me 

> 01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

I read in another thread that there were problems with the proprietary drivers or something, which may be causing this. Any more info?

---

### Post by plun on 2010-09-12
> **al090187 said:**
> 
I read in another thread that there were problems with the proprietary drivers or something, which may be causing this. Any more info?

Yep, you must remove fglrx (proprietary driver)

Start in recovery, normal boot

```
sudo aptitude purge fglrx

sudo rm /etc/X11/xorg.conf
```

Ctrl-Alt-Del for reboot

Reference:
[http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872)

---

### Post by Domes66 on 2010-09-14
I had too much work the past few days to get back to my ubuntu, but, my graphics cards are:
ATI MOBILITY RADEON 3470
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller

---

### Post by Domes66 on 2010-09-14
Removing the driver fixed the problem, yay!
Though, when I use the integrated card I only get a text interface, no GUI

---

### Post by DomesDKG on 2010-09-15
After installing several updates I rebooted for the second time, and get no GUI on either card.  I do get the command line, and a prompt saying 110 updates available...

How do I tell it to install said updates? I assume this will fix the current GUI problem

---

### Post by ranch hand on 2010-09-15
Can you boot to recovery?

---

### Post by jerrylamos on 2010-09-15
> **ranch hand said:**
> Can you boot to recovery?

NO!

Just "tried" to update 2.6.35.20.  Update stopped moving.  I could do very little.  Tried a re-boot and dead in the water.  Gets nowhere, recovery mode or not, previous kernel or not.

Too messed up to report a bug and ubuntu-bug wouldn't run from chroot.

So I'm doing a Beta re-install and update.....

Jerry

---

### Post by jfernyhough on 2010-09-15
Sounds like you interrupted the update process on your last attempt. Read: [http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

From the terminal, remember to do

$ sudo apt-get upgrade
(or $ sudo aptitude safe-upgrade )

rather than 

$ sudo apt-get dist-upgrade
(or $ sudo aptitude full-upgrade )

otherwise random stuff can end up getting removed and probably breaking, like X.

(Aside: thanks for the link, plun!)

---

### Post by ranch hand on 2010-09-15
I would get to the terminal and run;
```

sudo dpkg --configure -a

```
before doing anything else.  It may straighten out your screwed update/upgrade.

---

### Post by jerrylamos on 2010-09-15
> **ranch hand said:**
> I would get to the terminal and run;
```

sudo dpkg --configure -a

```
before doing anything else.  It may straighten out your screwed update/upgrade.

I tried that.  It said there was a locked process even though there was nothing running.  So I re-booted. Took a couple of tries, finally came up at 1280x1024 75 Hz.  This screen will only do 1440x900 60 Hz.  The display was screwy but I was able to change the monitor default. Wrote bug #640059.

Booted in recovery mode and ran fix broken packages.  I don't think it found anything to fix.  Anyway, back up and running.

I'm sure something is screwed up in update in that it doesn't finish.  I haven't been able to catch a repeatable sequence since re-install and update is a drag to repeat.

Jerry

---

### Post by ranch hand on 2010-09-15
I would try both:
```

sudo dpkg --configure -a

sudo dpkg-reconfigure -a

```
now that you are in.

```

sudo apt-get update -f

```
might be a help too.

---

### Post by DomesDKG on 2010-09-16
Well, I've gone from 110 packages to upgrade to 0, but still no GUI.

...even though the splash screen is all pretty and native resolution...

Is there just a setting somewhere that's telling it to skip the GUI or something?

---

### Post by cariboo on 2010-09-16
What happens when you type:

```
startx
```

after you've logged in?

---

### Post by DomesDKG on 2010-09-16
Interesting, I get a good amount of output, but I'd guess the important part is:

```

Fatal server error:
No screens found

```

Edit:
I'm getting the 
```

(EE) Screen(s) found, but none have a usable configuration.

```
version of this error.  I tried looking at the log file but I'm having trouble making sense of it. Is there some way I can post it here without having to type everything out?

---

### Post by VMC on 2010-09-16
> **DomesDKG said:**
> Interesting, I get a good amount of output, but I'd guess the important part is:

```

Fatal server error:
No screens found

```

Edit:
I'm getting the 
```

(EE) Screen(s) found, but none have a usable configuration.

```
version of this error.  I tried looking at the log file but I'm having trouble making sense of it. Is there some way I can post it here without having to type everything out?

I had this exact same error, way back when, I then did a manual install of my video driver, in my case its nvidia, and then it all worked. Maybe the same for ATI.

---

### Post by cariboo on 2010-09-16
You'll get that error if the proper driver isn't installed. If you know what driver you need, you can install it from the command line.

---

### Post by DomesDKG on 2010-09-16
What information do I need to determine the driver, just the model number of the graphics card?

I'm more than familiar with getting drivers through the windows GUI but I'm a little stumped when it comes to the command line here...

---

### Post by ktp on 2010-09-16
do you have /etc/X11/xorg.conf?

---

### Post by DomesDKG on 2010-09-16
> **ktp said:**
> do you have /etc/X11/xorg.conf?

no, I deleted it per previous instructions >.<

I have xorg.conf~ but I assume that's different.

---

### Post by ktp on 2010-09-16
xorg.conf~ is just back up file created by gedit.  You can delete it if you want.

can you try to config gl lib:
> sudo update-alternatives --config gl_conf
select the alternative provided by mesa, then
> sudo ldconfig
sudo update-initramfs -u
reboot

---

### Post by DomesDKG on 2010-09-16
Running: 
```
sudo update-alternatives --config gl_conf
```
Gives:
```
There is only one alternative in link group gl_conf: /usr/lib/mesa/ld.so.conf
Nothing to configure.
```

ld config blinks for a second and then I get a new prompt, and update-initramfs -u gives me 
```
Generating /boot/initrd.img-2.6.35-21-generic
```

on reboot I still get a text interface, and startx still doesn't work.

---

### Post by ktp on 2010-09-17
i lost for ideas...but something to try if you are using the ati card:

[http://ubuntuforums.org/showpost.php?p=9850568&postcount=24](http://ubuntuforums.org/showpost.php?p=9850568&postcount=24)

Also can you look at /var/log/Xorg.0.log to see if something like of error in there.

---

### Post by DomesDKG on 2010-09-21
I took a look at the post, but it's just about disabling the splash screen, which is working fine for me.

I took a look at the log but couldn't make sense of it, is there some way I can copy it off the machine? How do I mount a flash drive from the command prompt to copy it over?

Edit: Also, I was trying to run an update to see if would fix anything, but the earlier removal of fglrx is causing an error:

```

Preconfiguring packages...
(Reading database ... 207478 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
   when removing 'diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found 'diversion of /user/lib/fglrx/libL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subrocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried rebooting and running it again, but I get the same error.

---

### Post by cariboo on 2010-09-21
Your usb device should auto mount, if it doesn't find out what device label it is assign by typing:

```
dmesg | tail -n10
```

the above command will print out the last 10 lines of dmesg, the output should look similar to this:

```
dmesg | tail -n10
[10196.411925] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           8.02 PQ: 0 ANSI: 0 CCS
[10196.412614] sd 4:0:0:0: Attached scsi generic sg3 type 0
[10196.415596] sd 4:0:0:0: [sdc] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[10196.416157] sd 4:0:0:0: [sdc] Write Protect is off
[10196.416161] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[10196.416164] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[10196.418650] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[10196.418659]  sdc: **[COLOR="Red"]sdc1[/COLOR]**
[10196.421514] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[10196.421520] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

In my case the usb device is call /dev/sdc1. To mount it manually, at the prompt type:

```
sudo mount /dev/scd1 /mnt
```

then you can just copy the log file to it:

```
sudo cp /var/log/Xorg.0.log /mnt
```

---

### Post by DomesDKG on 2010-09-21
when I run dmsg 30 or so I see info on bluetooth, iwlagn, pcmia and a few other things, but not my flash drive.  Is there some way I can see the whole output? it scrolls past on the screen and I can't see the earlier parts?

Edit:

Aha, 

```
dmesg > output.txt

nano output.txt
```

solved that, now to look through it...

---

### Post by DomesDKG on 2010-09-21
And, at long last, I have the contents of the log file for you:

```

[  1408.313] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  1408.318] X Protocol Version 11, Revision 0
[  1408.320] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[  1408.321] Current Operating System: Linux flatbox 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64
[  1408.323] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=0314d0c8-f5c7-4e25-bb67-08fe5111aa5a ro quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap
[  1408.326] Build Date: 16 September 2010  06:18:41PM
[  1408.328] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[  1408.329] Current version of pixman: 0.18.4
[  1408.331] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1408.334] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1408.340] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 21 09:37:51 2010
[  1408.342] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1408.343] (==) No Layout section.  Using the first Screen section.
[  1408.343] (==) No screen section available. Using defaults.
[  1408.343] (**) |-->Screen "Default Screen Section" (0)
[  1408.343] (**) |   |-->Monitor "<default monitor>"
[  1408.344] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1408.344] (==) Automatically adding devices
[  1408.344] (==) Automatically enabling devices
[  1408.344] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1408.344] 	Entry deleted from font path.
[  1408.344] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1408.344] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1408.344] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1408.344] (II) Loader magic: 0x7d0200
[  1408.344] (II) Module ABI versions:
[  1408.344] 	X.Org ANSI C Emulation: 0.4
[  1408.344] 	X.Org Video Driver: 8.0
[  1408.344] 	X.Org XInput driver : 11.0
[  1408.344] 	X.Org Server Extension : 4.0
[  1408.345] (--) PCI:*(0:0:2:0) 8086:2a42:17aa:2112 rev 7, Mem @ 0xf4400000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[  1408.345] (--) PCI: (0:0:2:1) 8086:2a43:17aa:2112 rev 7, Mem @ 0xf4200000/1048576
[  1408.345] (II) Open ACPI successful (/var/run/acpid.socket)
[  1408.345] (II) LoadModule: "extmod"
[  1408.345] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1408.345] (II) Module extmod: vendor="X.Org Foundation"
[  1408.345] 	compiled for 1.9.0, module version = 1.0.0
[  1408.345] 	Module class: X.Org Server Extension
[  1408.345] 	ABI class: X.Org Server Extension, version 4.0
[  1408.345] (II) Loading extension MIT-SCREEN-SAVER
[  1408.345] (II) Loading extension XFree86-VidModeExtension
[  1408.345] (II) Loading extension XFree86-DGA
[  1408.345] (II) Loading extension DPMS
[  1408.345] (II) Loading extension XVideo
[  1408.345] (II) Loading extension XVideo-MotionCompensation
[  1408.345] (II) Loading extension X-Resource
[  1408.345] (II) LoadModule: "dbe"
[  1408.346] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1408.346] (II) Module dbe: vendor="X.Org Foundation"
[  1408.346] 	compiled for 1.9.0, module version = 1.0.0
[  1408.346] 	Module class: X.Org Server Extension
[  1408.346] 	ABI class: X.Org Server Extension, version 4.0
[  1408.346] (II) Loading extension DOUBLE-BUFFER
[  1408.346] (II) LoadModule: "glx"
[  1408.346] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[  1408.346] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[  1408.346] 	compiled for 7.5.0, module version = 1.0.0
[  1408.346] (II) Loading extension GLX
[  1408.346] (II) LoadModule: "record"
[  1408.346] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1408.346] (II) Module record: vendor="X.Org Foundation"
[  1408.346] 	compiled for 1.9.0, module version = 1.13.0
[  1408.346] 	Module class: X.Org Server Extension
[  1408.346] 	ABI class: X.Org Server Extension, version 4.0
[  1408.346] (II) Loading extension RECORD
[  1408.346] (II) LoadModule: "dri"
[  1408.346] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1408.347] (II) Module dri: vendor="X.Org Foundation"
[  1408.347] 	compiled for 1.9.0, module version = 1.0.0
[  1408.347] 	ABI class: X.Org Server Extension, version 4.0
[  1408.347] (II) Loading extension XFree86-DRI
[  1408.347] (II) LoadModule: "dri2"
[  1408.347] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1408.347] (II) Module dri2: vendor="X.Org Foundation"
[  1408.347] 	compiled for 1.9.0, module version = 1.2.0
[  1408.347] 	ABI class: X.Org Server Extension, version 4.0
[  1408.347] (II) Loading extension DRI2
[  1408.347] (==) Matched intel as autoconfigured driver 0
[  1408.347] (==) Matched vesa as autoconfigured driver 1
[  1408.347] (==) Matched fbdev as autoconfigured driver 2
[  1408.347] (==) Assigned the driver to the xf86ConfigLayout
[  1408.347] (II) LoadModule: "intel"
[  1408.347] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1408.347] (II) Module intel: vendor="X.Org Foundation"
[  1408.347] 	compiled for 1.9.0, module version = 2.12.0
[  1408.347] 	Module class: X.Org Video Driver
[  1408.347] 	ABI class: X.Org Video Driver, version 8.0
[  1408.347] (II) LoadModule: "vesa"
[  1408.348] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1408.348] (II) Module vesa: vendor="X.Org Foundation"
[  1408.348] 	compiled for 1.8.99.905, module version = 2.3.0
[  1408.348] 	Module class: X.Org Video Driver
[  1408.348] 	ABI class: X.Org Video Driver, version 8.0
[  1408.348] (II) LoadModule: "fbdev"
[  1408.348] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1408.348] (II) Module fbdev: vendor="X.Org Foundation"
[  1408.348] 	compiled for 1.8.99.905, module version = 0.4.2
[  1408.348] 	ABI class: X.Org Video Driver, version 8.0
[  1408.348] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[  1408.349] (II) VESA: driver for VESA chipsets: vesa
[  1408.349] (II) FBDEV: driver for framebuffer: fbdev
[  1408.349] (--) using VT number 8

[  1408.352] (WW) Falling back to old probe method for vesa
[  1408.352] (WW) Falling back to old probe method for fbdev
[  1408.352] (II) Loading sub module "fbdevhw"
[  1408.352] (II) LoadModule: "fbdevhw"
[  1408.352] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1408.352] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1408.352] 	compiled for 1.9.0, module version = 0.0.2
[  1408.352] 	ABI class: X.Org Video Driver, version 8.0
[  1408.354] (EE) intel(0): No kernel modesetting driver detected.
[  1408.354] (II) UnloadModule: "intel"
[  1408.354] (EE) Screen(s) found, but none have a usable configuration.
[  1408.354] 
Fatal server error:
[  1408.354] no screens found
[  1408.354] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  1408.355] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1408.355] 
[  1408.494]  ddxSigGiveUp: Closing log
 
```

---

### Post by cariboo on 2010-09-21
It doesn't look like your device is plugged in, there was an error in my command, that is now fixed. Make sure your device is plugged in, then run:

```
dmesg | tail -n10
```

Looking at your log file, the Intel driver isn't being loaded, it looks like yo're running fbdev. Try loading the driver manually:

```
sudo modprobe i915
```

---

### Post by DomesDKG on 2010-09-21
I'm still not getting a GUI with the Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller, though something seems to have fixed the ATI mobility radeon... so my guess is that the modprobe didn't work. I didn't get any output when I ran it, is that normal?

would a new copy of the error log for startx or the contents of the dmesg readout be helpful?

---

### Post by ktp on 2010-09-21
> **DomesDKG said:**
> I took a look at the post, but it's just about disabling the splash screen, which is working fine for me.

I took a look at the log but couldn't make sense of it, is there some way I can copy it off the machine? How do I mount a flash drive from the command prompt to copy it over?

Edit: Also, I was trying to run an update to see if would fix anything, but the earlier removal of fglrx is causing an error:

```

Preconfiguring packages...
(Reading database ... 207478 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
   when removing 'diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found 'diversion of /user/lib/fglrx/libL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subrocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried rebooting and running it again, but I get the same error.

this should fix that...seems like something didn't work right

first i would try
> sudo dpkg --force all --remove

if that doesn't work, then
> sudo dpkg-divert --rename --remove /usr/lib/libGL.so.1.2
sudo dpkg --force-all --purge xorg-driver-fglrx

if that doesn't work then you can move the file manually
> sudo mv /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.backup
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.backup
sudo apt-get remove xorg-driver-fglrx

---

### Post by cariboo on 2010-09-22
> **DomesDKG said:**
> I'm still not getting a GUI with the Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller, though something seems to have fixed the ATI mobility radeon... so my guess is that the modprobe didn't work. I didn't get any output when I ran it, is that normal?

would a new copy of the error log for startx or the contents of the dmesg readout be helpful?

If the modprobe command doesn't show any output, it usually means that the command worked, to check type:

```
lsmod | grep i915
```

If the module loaded correctly, it should show up in the output.

---

### Post by ktp on 2010-09-23
at last, there is updated fglrx which supports xserver 1.9 so ati should be good to go after update and enabling/installing it.

---

