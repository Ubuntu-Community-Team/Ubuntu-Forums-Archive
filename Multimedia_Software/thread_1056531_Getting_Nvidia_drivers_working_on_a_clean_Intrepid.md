---
title: "Getting Nvidia drivers working on a clean Intrepid Install (or a broken Hardy)"
date: 2009-01-31
forum: Multimedia Software
---

### Post by Yoshiman007 on 2009-01-31
After upgrading my lovely Hardy install to Intrepid, I found my system to have some serious problems starting the x server. I was booted to a terminal when booted, and "startx" resulted in a no screen found error. I may have done additional damage attempting to repair the xorg.conf in a couple ways, so i prepared a fresh Intrepid install on another partition.

So I can get a fresh install working, but without any restricted drivers, and by installing the 177 drivers, it re-breaks X. So my question is, can someone tell me the best way to get the nvidia drivers working with a clean install of Intrepid? I can get the system up initially, but it seems with any nvidia drivers installed, X throws the "no screen found" error upon rebooting.

So what's the best way to get nvidia drivers (any version) working in a clean install of Intrepid, OR what is the best way to get my Hardy install working again (using command line only)? Any help would be greatly appreciated.

If it helps:
64-bit Hardy/Intrepid
2GB Ram, 2x Nvidia 7900 GT
AMD X2 5000
Symptom(s): After upgrading Hardy, the system is unable to start X. Same happens when installing restricted Nvidia drivers in Intrepid.

Thanks again.

I managed to get the Hardy side to get x started by uninstalling all nvidia packages (sudo apt-get remove --purge Nvidia*) however, this does not enable any graphical enhancements, so I am merely at a middle ground.

---

### Post by Yoshiman007 on 2009-02-01
I really hope this helps someone.

For my situation, with X not working and a command line only, this got my system back up:

1. removing all nvidia related packages (which allowed X to realize why it wasn't working and build a barebones xorg.conf)

```
sudo apt-get remove --purge nvidia*
```

That made it so i could have a gui for a time, but no graphical acceleration. X prompted me when it started for it to create a basic xorg, and I clicked yes. Shortly after, x started and i had my screen working. (yay!)

2. Ensure that all nvidia packages are gone in Synaptic. So I just searched for nvidia and uninstalled anything directly related to it (had nvidia in the name).

3. Now for the tough part, getting graphical acceleration working again. First step is to make sure the old types of drivers are on the disabled list in /etc/default/linux-restricted-modules-common

```
sudo gedit /etc/default/linux-restricted-modules-common
```

and in the DisabledModules section, put, "nv nvidia_new" ,in the quotes and save.

4. Before stopping the xserver, I downloaded the *latest* nvidia drivers, 180.22, from their site [here]("http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-LINUX-x86-180.22-pkg1.run"). There is also 64 bit [here]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.22/NVIDIA-Linux-x86_64-180.22-pkg2.run"). Yea, it turns out I was delusional about having 64bit :-(. 

There are of course new drivers now (185.18.14) for 32-bit [here]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run") and 64-bit [here]("http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run").

5. Once the package was downloaded, i did ctrl+alt+F1 in order to get to a command line outside of x and stopped x with ```
sudo /etc/init.d/gdm stop
``` This stopped the xserver and Gnome so we could do other things without it getting in the way.

6. To install the drivers, do this: ```
sudo sh NVIDIA(then I press TAB so I don't have to type the whole filename out)
```. This assumes that you downloaded it to your home directory. If it is on your Desktop do this first: ```
cd Desktop
```.

6a. The Nvidia Install asks some questions about packages, but the right way around is to say yes to everything. At the end it will ask about making a xorg.conf file, and you also agree to that. 

7. Ah, here's the rub. Upon this, I had a bricked system again, however, with some determination, it was up again.
There are two steps to finishing the job.
First: ```
sudo lspci | grep VGA
``` This will show you the PCI numbers of your graphics cards. They are written like this: ##.##.# Write down this number for the next step.

Now edit xorg.conf with nano: ```
sudo nano /etc/X11/xorg.conf
``` This allows you to edit xorg.conf without a GUI or gedit.

In xorg.conf, go to the Device section, and add a line that reads ```
Busid      "PCI:#:#:#"
``` The numbers should be the numerical values that the first part of this step found, for me step one gave 01:00.0, so step two had "PCI:1:0:0". Save this file by doing ctrl+X, and pressing Y for yes.

8. Reboot and whatnot.

I believe these steps produced a working system for me, although the system insists that I have no restricted drivers at work (LIAR!). Sorry for the convoluted directions, this is day 3 of working on this problem for me and it's getting rather tiring. Hope this helps someone like in my previous situation.


PS: If you have SLI, your supposed to add ```
Option    "sli" "auto"
``` to the xorg.conf in the Device section.

PPS: Another step that may be optional is adding "nvidia" to /etc/modules. This may or may not launch the nvidia drivers when booting.

---

### Post by DeMus on 2009-02-01
> **Yoshiman007 said:**
> 
7. Ah, here's the rub. Upon this, I had a bricked system again, however, with some determination, it was up again.
There are two steps to finishing the job.
First: ```
sudo lspci | grep VGA
``` This will show you the PCI numbers of your graphics cards. They are written like this: ##.##.# Write down this number for the next step.

Now edit xorg.conf with nano: ```
sudo nano /etc/X11/xorg.conf
``` This allows you to edit xorg.conf w/o a GUI or gedit.

In xorg.conf, go to the Device section, and add a line that reads ```
Busid      "PCI:#:#:#"
``` The numbers should be the numerical values that the first part of this step found, for me step one gave 01:00.0, so step two had "PCI:1:0:0". Save this file by doing ctrl+X, and pressing Y for yes.

8. Reboot and whatnot.


Hi,

I have written the same "manual" as you have ([Look here](http://ubuntuforums.org/showthread.php?t=1054842)), found info on the nVidia website about how to install their drivers, but I must have missed one thing. Your step 7.
What does it do exactly and what is the difference with installing the driver without your step 7? Because I didn't do that at first, now I added the line to the xorg.conf file, rebooted, but see no real difference.

When I look at System | Administration | Hardware drivers I also don't see any drivers listed, just like you. Any idea why that is?

---

### Post by Yoshiman007 on 2009-02-01
> **DeMus said:**
> Hi,

I have written the same "manual" as you have ([Look here](http://ubuntuforums.org/showthread.php?t=1054842)), found info on the nVidia website about how to install their drivers, but I must have missed one thing. Your step 7.
What does it do exactly and what is the difference with installing the driver without your step 7? Because I didn't do that at first, now I added the line to the xorg.conf file, rebooted, but see no real difference.

When I look at System | Administration | Hardware drivers I also don't see any drivers listed, just like you. Any idea why that is?

The Step 7 was something i found [here]("http://ubuntuforums.org/showthread.php?t=1035873&highlight=nvidia+driver+intrepid") and [here]("http://ubuntuforums.org/showthread.php?t=965180&highlight=nvidia+driver+intrepid"). Sorry for the highlighting, I didn't want to screw up the links.

The only reason I did step 7 with my install is because I indeed did have a broken x after step 7 (with the no screens found error). This step identifies your GPU by it's PCI slot i.d. Then you input it into the xorg.conf that was made by the nvidia installer (using the Busid   "PCI:1:0:0 line [numbers depend on the previous step]). For me, this fixed the xserver when the regular install steps left it broken the same way. I'm not sure if it's necessary for every situation, but for mine it seemed to help (read: fix).

I really can't say why the driver isn't showing up in the Drivers page, but even more curious is that it's not in Synaptic either (doing a search for nvidia gives no relevant results). I'm really not sure why it's not showing up. It could be that we didn't use any type of package manager to install it, therefore it's not in any lists that the Driver manager uses. I would still think that the old drivers (173, 177) would be there. I'm pretty disappointed in my upgrade from Hardy in terms of compatibility with nvidia drivers. Good thing there was *a* method for making it work again.

Edit: I think it may be that via this method of install, a package called "nvidia-settings" is not put on the system. This could be why the drivers don't show up in the manager. I believe I completely removed this package, if it was there, in the step where I purged all nvidia related packages.

---

### Post by DeMus on 2009-02-01
Most important is that it works now. I have sweating a lot lately to get it working. I found info on the nVidia website about erasing old things and make sure other stuff is there before starting the installation program. Strange the program does not do that by itself, finding out what needs to be there, what may not be there, uninstall an old driver, etc.
Why they do that only in Windows? Why is it so easy to install a new video driver there and not in Linux. I have been reading more info on the nVidia site and I came on a page, a mile long, with all kinds of instructions to do and I thought, in Windows you simply start an .exe file and 10 seconds and a reboot later the driver is installed. I know downloading and installing .exe files is unsafe, but from a trusted source it can't do much harm, can it.
I really think nVidia should consider to make installations in Linux more friendlier. I have been looking around in this forum for a few days now and I see many people who can not get it to work.  That is not good.

But for us it works, we wrote the way to do it on the forum so hopefully more people will benefit from it.

Thanks for your help.

---

### Post by Yoshiman007 on 2009-02-01
> **DeMus said:**
> Most important is that it works now. I have sweating a lot lately to get it working. I found info on the nVidia website about erasing old things and make sure other stuff is there before starting the installation program. Strange the program does not do that by itself, finding out what needs to be there, what may not be there, uninstall an old driver, etc.
Why they do that only in Windows? Why is it so easy to install a new video driver there and not in Linux. I have been reading more info on the nVidia site and I came on a page, a mile long, with all kinds of instructions to do and I thought, in Windows you simply start an .exe file and 10 seconds and a reboot later the driver is installed. I know downloading and installing .exe files is unsafe, but from a trusted source it can't do much harm, can it.
I really think nVidia should consider to make installations in Linux more friendlier. I have been looking around in this forum for a few days now and I see many people who can not get it to work.  That is not good.

But for us it works, we wrote the way to do it on the forum so hopefully more people will benefit from it.

Thanks for your help.

I agree with you completely. It seems that Windows installations are much easier to cope with, but to a certain extent, .deb packages achieve some of the same goals. Now why Nvidia can't write a .deb that does everything in order to get a running install, I have no idea.

---

### Post by MrCharles on 2009-02-05
This thread has been very comprehensive, and I have a greater understanding of my issues at hand.  (Although now I've been out of a computer for 3 days.)  I'm shocked that there's a new Ubuntu Release with so many NVidia Conflicts.  It's not like its a rare piece of hardware, or from the Nvidia side, start supporting more of your friggin users!

---

### Post by Firestarter-Ibex on 2009-02-06
> **Yoshiman007 said:**
> I really hope this helps someone.


4. Before stopping the xserver, I downloaded the *latest* nvidia drivers, 180.22, from their site [here]("http://us.download.nvidia.com/XFree86/Linux-x86/180.22/NVIDIA-LINUX-x86-180.22-pkg1.run"). There is also 64 bit [here]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.22/NVIDIA-Linux-x86_64-180.22-pkg2.run"). Yea, it turns out I was delusional about having 64bit :-(. 

5. Once the package was downloaded, i did ctrl+alt+F1 in order to get to a command line outside of x and stopped x with ```
sudo /etc/init.d/gdm stop
``` This stopped the xserver so we could do other things without it getting in the way.

6. To install the drivers, do this: ```
sudo sh NVIDIA(then I press TAB so I don't have to type the whole filename out)
```



Hi, I am having the same problem but with 8600GTs in SLi.

My question is did you install these drivers from command line? I tried doing the same (with TAB) and it didn't work and I don't know the file path to nvidia driver that downloaded to my desktop.

Very new to linux and nvidia has ensured that it wasn't as a warm a welcome as I hoped for.

Thanks for your help

---

### Post by keenish27 on 2009-02-07
> **Firestarter-Ibex said:**
> Hi, I am having the same problem but with 8600GTs in SLi.

My question is did you install these drivers from command line? I tried doing the same (with TAB) and it didn't work and I don't know the file path to nvidia driver that downloaded to my desktop.

Very new to linux and nvidia has ensured that it wasn't as a warm a welcome as I hoped for.

Thanks for your help

Just gotta be sure your looking in the right place.  Your desktop would be Desktop/NVIDIA blah blah blah

just type Desktop/NVIDIA and hit tab.  It should work.

---

### Post by jhayes on 2009-02-08
i just want to say thanks.
the info in this post got me from broken low res mode after a kernal change, to getting the blob going and now in full resolution.

u guys are great.

---

### Post by whyameye on 2009-02-16
quick thanx. My intrepid machine was going into "low rez" mode after kernel update from 2.6.27-11 to 2.6.27-12. I was at my wit's end. Then this worked.

---

### Post by cjsheets on 2009-02-17
Thanks for the help, it is really appreciated. I worked for several days trying to get Nvidia drivers working and this did it.

---

### Post by gradysghost on 2009-02-21
I haven't tried this yet (I'm at work right now), but I wanted to let you know how freakin awesome you are for culling this information from all the different places I'd already been looking and compiling it all into a simple guide.  You even answered the last of the few questions I had on this matter.  I am almost positive this will solve all of my problems and bring about world peace.  Thankyouthankyouthankyou!

---

### Post by RedRat on 2009-02-21
> **DeMus said:**
> 
...
Why they do that only in Windows? Why is it so easy to install a new video driver there and not in Linux. I have been reading more info on the nVidia site and I came on a page, a mile long, with all kinds of instructions to do and I thought, in Windows you simply start an .exe file and 10 seconds and a reboot later the driver is installed. I know downloading and installing .exe files is unsafe, but from a trusted source it can't do much harm, can it.
I really think nVidia should consider to make installations in Linux more friendlier. I have been looking around in this forum for a few days now and I see many people who can not get it to work.  That is not good.
....
Thanks for your help.
Don't take this the wrong way, I do like Linux but the one thing I find truly annoying in Linux is this business with the video drivers. They seem to be overly difficult to install and get working. Everytime there is a kernel update (we have had about 4 or 5 in the past year or so) you have to go through all of these contortions. I wish the folks at Canonical could get this problem corrected. For me EnvyNG works pretty well, but I have spent far too much time fooling around get them installed. Hope someone can pass along these annoyances to the developers.

---

### Post by gradysghost on 2009-02-22
Wow.  I'm actually surprised that this didn't work for me.  It left me with the same old problems as before.  Guess I'll have to search elsewhere...

---

### Post by spliffeh on 2009-02-23
I'm pretty pissed off this didn't work for me either. Sounds like it should, I have dual Geforce 7800 GTX. I tried twice on fresh installs on Ubuntu 8.10 and then even tried Fedora 10.... exact...same...problem.... 

nvidia+sli+linux+xorg = 1000s of hours wasted

This sucks, hard.

---

### Post by mithbuntu on 2009-03-25
This didn't work for me either.

Quad core
4gb ram
2 Geforce 8800 GT in SLI config
Asus Mobo
Logitech g11/mx518

I knew something probably wasn't going to work after I followed your very first step

```

sudo apt-get remove --purge nvidia*

```

rebooted and was left in the exact same spot.  I never had X realize anything was wrong, even with xfix running, but I moved on.  I followed the rest of the guide and... no change.  Previously I had an error saying type1 module didn't exist, but I wasn't sure what that was...

Here is my /var/log/Xorg.0.log
```


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux mithbuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 25 03:27:49 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
**(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.**
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 9

**(!!) More than one possible primary device found**
(--) PCI: (0@1:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xcc000000/16777216, 0xb0000000/268435456, 0xca000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
(--) PCI: (0@3:0:0) nVidia Corporation GeForce 8800 GT rev 162, Mem @ 0xc8000000/16777216, 0xa0000000/268435456, 0xc6000000/33554432, I/O @ 0x00008c00/128, BIOS @ 0x????????/131072
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
(II) NVIDIA GLX Module  180.29  Thu Feb  5 00:05:47 PST 2009
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
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  180.29  Wed Feb  4 23:45:20 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: 
[b](EE) No devices detected.

Fatal server error:
no screens found
[/b]

```

FYI my two vcards were at 01:00.0 and 03:00.0, so I followed your guide and input it as PCI:1:0:0.

---

### Post by stratus75 on 2009-03-31
Hopefully i might have a solution.! the syntax in past posts is the same as i was using as soon as i change to this syntax it worked.
I have to add i got this from a post on the form havent been able to find it again yet, just passing it on):P
worked for me........ 


BusID    "X:0:0   (X= bus id number, and BusID probable case sensitive havent try it in lower case) 

I spent 2 weeks on and of and lost count of how many times i did a clean install of 8.10 then decieded to try Jaunty (which is what that i have working now wwwwoooohhhhoooo!!!

---

### Post by platinumriver on 2009-04-14
First off, thank you for taking the time to post this information. Your guide helped me quite a bit.

I have an NVIDIA GeForce GT120 running on 2.6.27-11 x64. The 180.22 version of the NVIDIA drivers did not work for me, but 180.44 worked.

Version: 180.44
Operating System: Linux x64 (AMD64/EM64T)
Release Date: March 30, 2009
[http://us.download.nvidia.com/XFree86/Linux-x86_64/180.44/NVIDIA-Linux-x86_64-180.44-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/180.44/NVIDIA-Linux-x86_64-180.44-pkg2.run")

Cheers.

---

### Post by David C. on 2009-04-24
Will this work on an old system?

 I have a Celeron 1.2gHz w/a four maybe five year old graphics card GForce FX (Nvidia), I think. Problem is I don't know which model. I still have the install disc and instructions, but naturally it doesn't identify the specific model. When I open the Hardware Drivers it tells me Version 96 recommended. 

Problem is when I enabled this my screen goes wonkers. Everything goes super large, when I opened a window and tried to click on a button the window would only move up, clicking it again it'd move down. The buttons were inactive. I ended up closing it by clicking on the close window icon. I checked my screen resolution, currently I'm sitting at 1280 x 1024 (5:4) w/out the card enabled. 

Previously, I had it enable and went to change the screen resolution due to a super large display; it went black and the monitor indicated that no input signal was found, so of course I'm hesitant to decrease the screen resolution now, because if the screen goes black and signal is lost. I have to redo the install, which would totally suck. Suggestions or ideas would be greatly appreciated.

---

### Post by Yoshiman007 on 2009-06-09
I'm glad that others have gotten some help from what has been posted here. I'm writing to say that I'm trying to follow my own guide again since I've finally found the time to switch to 64bit. I've so far had immense problems getting hardy to even install (had to put all_generic_ide=1 before booting into the live cd). So I'll post with my results, hopefully my own guide will allow for great success.

And I apologize to those let out in the cold, I forgot to check my post after a couple of weeks. If you're still having problems or have found solutions, please post them.

---

### Post by Yoshiman007 on 2009-06-09
I have so far had great success following my guide. The only issue is after changing the screen resolution, and accidentally the refresh rate, it would appear that it doesn't want to change the refresh rate or resolution. Can't win em all then.

Solution: Use the NVIDIA X Server Settings (manager) in System > Preferences. All is well in the resolution/refresh rate world!

---

### Post by vaikz on 2009-06-21
Hi, I just login to say thank you for the great tutorial. it works for me. Cheers

---

### Post by Jeruvy on 2009-06-21
> **Yoshiman007 said:**
> I have so far had great success following my guide. The only issue is after changing the screen resolution, and accidentally the refresh rate, it would appear that it doesn't want to change the refresh rate or resolution. Can't win em all then.

Solution: Use the NVIDIA X Server Settings (manager) in System > Preferences. All is well in the resolution/refresh rate world!

I just wanted to say thank you very much!  This guide has solved my problems with the nvidia drivers.  I did download the x64 185.18.14 drivers directly from nvidia and they worked like a charm.  Using the nvidia x server settings was required.

Now I can see both video cards fine and I enabled SLI.  I'm going to attempt to disable SLI and see if I can get all 4 monitors working, as it can only view the two on the card I configured X for.  I'm curious what would be the best approach whether to duplicate the device section for the other card and remove the SLI option, or something else.

Best wishes.

---

### Post by eznet on 2009-10-25
```
Busid      "PCI:#:#:#"
```

Thank you!  I recently upgraded to Karmic and have not been able to get the nVidia drivers to work - no devices found error...  This line was vital!

You rule!  Don't know why it didn't add by default, but manually adding it has fixed it for me!

---

