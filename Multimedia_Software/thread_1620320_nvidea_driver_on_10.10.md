---
title: "nvidea driver on 10.10"
date: 2010-11-12
forum: Multimedia Software
---

### Post by alvinmoneypit on 2010-11-12
Hello All,

Installing 10.10 on an old computer w/soyo MB, Amd processor and an off brand video card.  Installed over 8.04 as it had video problems also, and had nothing on it.  When running this system, screen resolution looks good, tests good on system testing.  I downloaded the nvidia driver as recommended by system update.  It said it was tested good on system update. After installing driver, can only achieve 680x420 resolution or one even smaller.  On my testing my system recognised my monitor, but with the driver enabled, it didn't see it calling it monitor 0 or something like that.  

I wonder what I don't have installed to make this work.  This is a brand new install with absolutely nothing new added so far.  Any suggestions appreciated.  Thanks.

---

### Post by tommcd on 2010-11-13
> **alvinmoneypit said:**
>  I downloaded the nvidia driver as recommended by system update.  It said it was tested good on system update. ...
What nvidia card do you have?
After installing Ubuntu, you will not automatically get the proprietary 3D nvidia driver with system updates. You have to deliberately install it either from: system > administration > hardware drivers, or from synaptic or with apt-get.
Did you install the driver from the Ubuntu repos? If so, then which one? If you do not know, post the output of:
```
aptitude search nvidia
```
Or do you mean that you installed the driver from nvidia.com?
Please answer *all* of these questions and we can go further to help you.

---

### Post by alvinmoneypit on 2010-11-13
thanks for responding.

Sorry my question was vague.  I'm using my other computer and since I only have on monitor I have to switch it back and forth.  

I used "update manager".  I didn't add any libraries yet, not even medibuntu.  So from whatever the libraries I had on there, I mark them all available.  I'm sure the driver was marked "tested good by Ubuntu developers.  

I have to go but later I'll post more when I can hook up the computer in question.

---

### Post by vcrpex on 2010-11-13
Hi Alvinmoneypit,
you can try the following.

sudo gedit /etc/X11/xorg.conf 

and set the monitor display to a bigger resolution like the following:

Section "Monitor"
Identifier "Configured Monitor"
DisplaySize 1920 1080
HorizSync 30-70
VertRefresh 60-75
EndSection

Please note that the horizsync and vertrefresh varies accordingly to your own monitor. Encounter same problem as you everytime I installed nvidia driver. This is what i do to display a bigger screen resolution.

---

### Post by alvinmoneypit on 2010-11-13
Hi again,

My video card is: 

	

    CHAINTECH LA-FX20-H GeForce FX 5200 128MB 64-bit DDR AGP 4X/8X Low Profile Video Card

the command "aptitude search nvidia yielded:

The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk

So I guess I don't have aptitude.


I can't post a screen shot - The scant info I get from Ubuntu on this driver is it's:

"NVIDIA accelerated graphics driver (version 173)[Recommended]
Tested by the Ubuntu Developers
License: Proprietary

As far as I know, I didn't get the driver from nvidia, although it is proprietary, I think it came from "restricted".  I have main, multiverse, universe, and restricted as my sources.

vcrpex,

Thanks for your kind reply.  As may be evident, I'm pretty much a novice with Ubuntu in general and terminal commands in particular.   I know enough to "hose" up my system if I'm not careful with it.  I'd rather get this thing working graphically if I can right now.  However, doing what you say, is that how you have to set it each time, or once you set it at a high resolution, you can go down from there on the nvidia graphic?  I wonder how to use the many features provided with this driver if I can't get just the resolution to work?  For some reason it seems to me that driver software is not getting the report of the display that Ubuntu collects.

---

### Post by vcrpex on 2010-11-14
> **alvinmoneypit said:**
> Hi again,

vcrpex,

Thanks for your kind reply.  As may be evident, I'm pretty much a novice with Ubuntu in general and terminal commands in particular.   I know enough to "hose" up my system if I'm not careful with it.  I'd rather get this thing working graphically if I can right now.  However, doing what you say, is that how you have to set it each time, or once you set it at a high resolution, you can go down from there on the nvidia graphic?  I wonder how to use the many features provided with this driver if I can't get just the resolution to work?  For some reason it seems to me that driver software is not getting the report of the display that Ubuntu collects.

hi alvinmoneypit,
you only have to set it once in that file and you can go down from there on the nvidia xserver setting after that. I also dunno why it doesnt detect the monitor, but I am using a lcd tv as a monitor, thus it cannot detect. I have the same fx5200 card on my older desktop with pentium 4. I was using the version 173 for that card and my current one which is onboard. hope it can help you, i know it look really bad when your screen can only be 640 by 480. I basically just save a copy of the xorg.conf file in my backup flash drive just in case when i need to do a fresh install of Ubuntu. Used the same file from 9.04 to 10.10 because my monitor remain the same lcd tv.

---

### Post by alvinmoneypit on 2010-11-16
So I'm still working on getting this card working.  
I saw on another thread where someone was trying to get an nvidia card working.  I followed a suggestion made there .  
code:
sudo nvidia-xconfig

I did this and rebooted and it totally hosed my video, after reboot no video with the message" Signal frequency out of range FH>95.3kHz FV>60.0Hz
Please change signal timing"  So I guessed how to enter safe mode and went in and removed the nvidia driver.  I still can't figure out why Ubuntu sees the monitor but upon investigation trying to troubleshoot the driver error while in safe mode I verified that the card does not see the monitor or any info from it.  I did a search in the terminal for the card and it reports back 
"nVidia Corporation NV34 [GEforce FX5200] (rev a1)" 

I did a search in synaptic package manager for nVidia and found I have installed:
nvidia common
jockey-common
jockey-gtk
nvidia173-modaliases
nvidia96-modaliases
nvidia-current-modaliases
xserver-xorg-video-nauveau
xserver-xorg-video-nauveau-dbg
xserver-xorg-video-nauveau-nv

These are all the latest versions available according to synaptic.   I wonder if I've something missing or I should try an earlier driver.  If I do another driver, how do I get ubuntu to allow it's install since it's against the recommended 173 driver?

---

### Post by meanmrmustard on 2010-11-16
I'm having the same issue with the 173 driver and just found the quote below at [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes:](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes:)

"The new Xorg 1.9 available in Maverick is not compatible with nVidia based chipsets that use the (nvidia-96) and (nvidia-173) drivers. (626974)"

Evidently Nvidia had released a driver for Meerkat on September 30 though I haven't installed it yet, others have - apparently the repos just aren't updated to include it?

Available for download here:
[http://www.nvnews.net/vbulletin/showthread.php?p=2326225](http://www.nvnews.net/vbulletin/showthread.php?p=2326225)

---

### Post by alvinmoneypit on 2010-11-16
meany,

I downloaded the package, but how do I unpack it and make the system see it?

---

### Post by alvinmoneypit on 2010-11-16
This is what I have on the system.

```
aptitude search nvidia
c   nvidia-173                      - NVIDIA binary Xorg driver, kernel module a
p   nvidia-173-dev                  - NVIDIA binary Xorg driver development file
p   nvidia-173-kernel-source        - Transitional package for nvidia-glx-173-ke
i   nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-180-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-180-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-180-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-185-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-185-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-185-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-185-modaliases           - Transitional package for nvidia-185-modali
i A nvidia-96                       - NVIDIA binary Xorg driver, kernel module a
p   nvidia-96-dev                   - NVIDIA binary Xorg driver development file
p   nvidia-96-kernel-source         - Transitional package for nvidia-glx-96-ker
i   nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - Cg Toolkit - GPU Shader Authoring Language
i   nvidia-common                   - Find obsolete NVIDIA drivers              
p   nvidia-current                  - NVIDIA binary Xorg driver, kernel module a
p   nvidia-current-dev              - NVIDIA binary Xorg driver development file
i   nvidia-current-modaliases       - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-glx-173                  - Transitional package for nvidia-glx-173   
p   nvidia-glx-173-dev              - Transitional package for nvidia-glx-173-de
p   nvidia-glx-180                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-180-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-185                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-185-dev              - Transitional package for nvidia-glx-185-de
i   nvidia-glx-96                   - Transitional package for nvidia-glx-96    
p   nvidia-glx-96-dev               - Transitional package for nvidia-glx-96-dev
p   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
v   nvidia-va-driver
```

does anyone know if I'm missing anything?

---

### Post by alvinmoneypit on 2010-11-16
vcrpex,

I tried your solution and added my monitor configs instead of yours - it did absolutely nothing that I could tell.  The same problem.

When I don't have the nvidia driver enabled, I go to "preferences>monitors, my correct monitor is displayed along with full functionality of my resolutions and refresh rate.  When I enable the driver and have it active, preferences>monitors no longer 'sees' the monitor reporting "unknown" with the low resolutions of 640x480 and 620x240 only available.

I was looking around in the nvidia driver program and it wasn't reporting a bus ID that I could tell, only "?=?=?" or something like that.  but most everything else appeared to be working including visual effects.

---

### Post by meanmrmustard on 2010-11-16
> **alvinmoneypit said:**
> meany,

I downloaded the package, but how do I unpack it and make the system see it?

This explains it

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

post your success when you get it installed :P

Mr. M

---

### Post by alvinmoneypit on 2010-11-17
MeanMr,

It worked like the howTo stated, but it won't continue.  with the message, "ERROR: nVidia-installer must be run as root"  Then there is an "OK" to which I hit enter and the terminal, installer closes.  There is a lengthy "HowTo" at the NVidia site, but it doesn't work either, it says to start with root terminal but terminal says it can't unpack the .run file.   Reading on it says I need a "linker" which I don't know if I have and don't know how to look for it, and that is just page 2 of like a 30 page howTo.  

It simply is not worth the time, I'll fix it later when a convenient solution comes along or I won't.  I need to move on and see if I can even see video with this system or not.  I also want to get WINE working.

---

### Post by tommcd on 2010-11-17
> **alvinmoneypit said:**
> This is what I have on the system.
```

c   nvidia-173                      - NVIDIA binary Xorg driver, kernel module a
i A nvidia-96                       - NVIDIA binary Xorg driver, kernel module a

```
does anyone know if I'm missing anything?
It seems that aptitude is no longer included by default in Ubuntu 10.10. That is why you got this:
```
The program 'aptitude' can be found in the following packages:
* aptitude
* aptitude-gtk
```
I am using Lubuntu 10.10 now, so I thought that the omission of aptitude was only a Lubuntu thing. Anyway, glad you figured that out and installed aptitude.

As for the nvidia-173 driver:
According to this:[http://www.nvnews.net/vbulletin/showthread.php?p=2326225](http://www.nvnews.net/vbulletin/showthread.php?p=2326225) The nvidia 173.14.28 driver fixes the incompatibility with Xorg 1.9. And Maverick 10.10 includes the nvidia 173.14.28 driver:
[http://packages.ubuntu.com/maverick/nvidia-173](http://packages.ubuntu.com/maverick/nvidia-173)
Your output of "*aptitude search nvidia*" that you posted in post #10 in this thread indicates that you do not have nvidia-173 installed. It says you have nvidia-96 installed, which is likely what is giving you problems, since nvidia-96 is still incompatible with Xorg 1.9 as far as I know. 
Do this:
Uninstall nvidia-96:
```
sudo apt-get remove --purge nvidia-96
```
Then install nvidia-173 and nvidia-settings:
```
sudo apt-get install nvidia-173 nvidia-settings
```
Then backup whatever xorg.conf you have now, and then configure the nvidia driver.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig

```
Then reboot and (hopefully!!) you should have a properly configured desktop with the nvidia driver running.

---

### Post by alvinmoneypit on 2010-11-17
Tom,

Thanks for joining in.

I followed most of your instructions.

When I get to backing the xorg file, I get:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
cp: cannot stat `/etc/X11/xorg.conf': No such file or directory

```

Then the next command is not found:
```
sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
```


I had the installed correct version originally, I installed the 96 driver to try to find a solution.  I noticed this during install:

```
nvidia-173.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-22-generic/updates/dkms/

depmod....

DKMS: install Completed.

```

So ubuntu is not finding my file or directory?

---

### Post by alvinmoneypit on 2010-11-17
I rebooted after completing the above sans creation/config of xorg.  Still the same result - not seeing the display, with only 640x480 and 320x240 resolutions available.

---

### Post by alvinmoneypit on 2010-11-17
after uninstalling and reinstalling, here is what currently is installed:```
aptitude search nvidia
c   nvidia-173                      - NVIDIA binary Xorg driver, kernel module a
p   nvidia-173-dev                  - NVIDIA binary Xorg driver development file
p   nvidia-173-kernel-source        - Transitional package for nvidia-glx-173-ke
i   nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-180-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-180-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-180-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-185-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-185-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-185-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-185-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-96                       - NVIDIA binary Xorg driver, kernel module a
p   nvidia-96-dev                   - NVIDIA binary Xorg driver development file
p   nvidia-96-kernel-source         - Transitional package for nvidia-glx-96-ker
i   nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - Cg Toolkit - GPU Shader Authoring Language
i   nvidia-common                   - Find obsolete NVIDIA drivers              
p   nvidia-current                  - NVIDIA binary Xorg driver, kernel module a
p   nvidia-current-dev              - NVIDIA binary Xorg driver development file
i   nvidia-current-modaliases       - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-glx-173                  - Transitional package for nvidia-glx-173   
p   nvidia-glx-173-dev              - Transitional package for nvidia-glx-173-de
p   nvidia-glx-180                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-180-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-185                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-185-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-96                   - Transitional package for nvidia-glx-96    
p   nvidia-glx-96-dev               - Transitional package for nvidia-glx-96-dev
p   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
v   nvidia-va-driver  
```

---

### Post by toasterboy1 on 2010-11-17
I had problems with the nvidia driver on my laptop after going to 10.10 as well. After installing, uninstalling, configuring, unconfiguring here is what worked, if I remember right. Open terminal/console/command prompt, whatever you want to call it.
Remove all nvidia related stuff:
```
sudo apt-get purge nvidia*
```
I added the xorg-edgers ppa to my repository:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
Ran update and dist-upgrade:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Installed newest nvidia driver.
```
sudo apt-get install nvidia-current
```
Ran nvidia-xconfig
```
sudo nvidia-xconfig
```
Logout and back in. If all works try to reboot.
I always had problems after a reboot until I logged out and back in before I rebooted. I do not know why. I hope this works for you.

---

### Post by alvinmoneypit on 2010-11-17
still not working.  All the commands and software downloads apparently worked except the last one:
```
sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found
```

---

### Post by alvinmoneypit on 2010-11-17
after logging out and rebooting, here is what I've got now:
```
p   nvidia-173                      - NVIDIA binary Xorg driver, kernel module a
p   nvidia-173-dev                  - NVIDIA binary Xorg driver development file
p   nvidia-173-kernel-source        - Transitional package for nvidia-glx-173-ke
p   nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-180-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-180-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-180-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-180-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-185-kernel-source        - Transitional package for nvidia-glx-185-ke
p   nvidia-185-libvdpau             - Transitional package for nvidia-185-libvdp
p   nvidia-185-libvdpau-dev         - Transitional package for nvidia-185-libvdp
p   nvidia-185-modaliases           - Transitional package for nvidia-185-modali
p   nvidia-96                       - NVIDIA binary Xorg driver, kernel module a
p   nvidia-96-dev                   - NVIDIA binary Xorg driver development file
p   nvidia-96-kernel-source         - Transitional package for nvidia-glx-96-ker
p   nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-cg-toolkit               - Cg Toolkit - GPU Shader Authoring Language
p   nvidia-common                   - Find obsolete NVIDIA drivers              
i   nvidia-current                  - NVIDIA binary Xorg driver, kernel module a
p   nvidia-current-dev              - NVIDIA binary Xorg driver development file
p   nvidia-current-modaliases       - Modaliases for the NVIDIA binary X.Org dri
p   nvidia-glx-173                  - Transitional package for nvidia-glx-173   
p   nvidia-glx-173-dev              - Transitional package for nvidia-glx-173-de
p   nvidia-glx-180                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-180-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-185                  - Transitional package for nvidia-glx-185   
p   nvidia-glx-185-dev              - Transitional package for nvidia-glx-185-de
p   nvidia-glx-96                   - Transitional package for nvidia-glx-96    
p   nvidia-glx-96-dev               - Transitional package for nvidia-glx-96-dev
p   nvidia-kernel-common            - NVIDIA binary kernel module common files  
i A nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
v   nvidia-va-driver 
```

---

### Post by alvinmoneypit on 2010-11-17
now the nvidia 173 driver doesn't appear as available nor recommended whewn searching for available drivers.  The driver installed is only labelled "current" and the graphic states it is not activated.

---

### Post by toasterboy1 on 2010-11-17
The nvidia 173 driver will not show up unless you install the package, atleast from my experience. Previous versions seem to find your hardware and allow you to install the drivers from jockey, the additional drivers program, but 10.10 does not seem to. I had to install all my drivers using apt or synaptic. Does it allow you to activate nvidia-current? If not you may be able to create a xorg.conf file to activate it. Here is mine:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

---

### Post by alvinmoneypit on 2010-11-17
Toasterboy,

I'm sorry, I miss typed my post.  The driver window says that the "current" driver is "activated, but not in use"  I'm not sure how this could be or what it means except that I'm missing some dependencies. If this is so, I wonder what is driving my display?
Sure I can copy and paste some commands, but installing a xorg.conf file, as rudimentary as I'm sure it is, is probably beyond me without instruction or a link to an easy howTo..

---

### Post by toasterboy1 on 2010-11-17
Mine says the same but if you open the nvidia settings it will show everything if it is working right. I read somewhere that it did that in previous ubuntu versions as well even though it is working. You should not have to worry about the xorg if the nvidia X server settings program shows your running nvidia driver. Still stumped why nvidia-xconfig did not work. If it says you need to run nvidia-xconfig open you konsole and:
```
sudo nano /etc/X11/xorg.conf
```
Scroll down to the "Device" section and change driver to
```
Driver    "nvidia"
```
then reboot

---

### Post by alvinmoneypit on 2010-11-17
maybe this system is just too old for 10.10.

I mean I had an old Dell Latitude laptop running Windows98.  I'd never dream of putting XP on it, even though I had a license.

This system (not the same system I have in my signature) is an old Athalon XP3200 running on a Soyo K7VKPE Dragon Plus 2.0 motherboard, an old board from an out-of-business maker. 

 The BIOS has the newest firmware I could find (and still trust) and it's from 2005.  Sometimes this system boots, sometimes it doesn't, it just goes to a screen where it shows the components and stays there - I used to think it was the hard drive, but now I'm fairly convinced there is something wrong with a component somewhere on the board or the processor (since I've replaced both the hard drive and the SATA cable.

The video card is not old (new in 2009), but an older design - a Chaintech Nvidia 128mB GEForce FX5200- not the best, but running Windows I was so frustrated with ATI cards (they never seemed to work consistently) that I just wanted to try something different that may be better so I got a new one of these for like $20.00 and that was over a year ago, you probably can't buy a new one of these today. Yet under XP, I never had a video problem from the moment I installed it until I installed a new WD HD and put in Ubuntu.

Maybe it would be better to drop down to 10.04 or even 9.10 - any thoughts?

---

### Post by toasterboy1 on 2010-11-17
I like running the latest and greatest on my laptop but my desktop and my make shift server usually runs whatever the newest LTS is. Both of them are fairly old. Hardware drivers seemed to install easier in 10.04 for me but I remember having to use envy to install any nvidia drivers.

---

### Post by alvinmoneypit on 2010-11-17
I don't have any nVidia control screen any more, at least in the graphical interface.  I'm not sure how to run it in terminal.

I just did your command, I guess to edit the xorg file - it appears to be a completely blank file, all I have is the control function list at the bottom.

---

### Post by alvinmoneypit on 2010-11-17
I believe I have some 3D rendering although Ubuntu doesn't still doesn't enable visual effects.  When I put in the nVidia 173 package and enabled the driver, I noticed my chess program wouldn't display in 3D, currently it does, but it always did before I enabled the 173.

---

### Post by toasterboy1 on 2010-11-17
I would install nvidia-settings
```
sudo apt-get install nvidia-settings
```

It does not sound like your nvidia driver is running right if there is nothing in the xorg.conf file. Try installing nvidia-settings. Then run it. It will probably want you to run nvidia-xconfig as root. I would try running nvidia-xconfig again. Maybe it is part of the nvidia-settings package.

---

### Post by alvinmoneypit on 2010-11-17
Hi Toaster,

It says Nvidia settings are already there. 0 upgraded, 0 removed, 5 not upgraded.  xconfig not found.

---

### Post by toasterboy1 on 2010-11-17
Run
```
nvidia-settings
```

Should pull up the nvidia X server setting program. You should be able to change resolutions and such in there if the driver is indeed installed right.

---

### Post by alvinmoneypit on 2010-11-17
this caused a dialog to open and an error message: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
So I closed it and the configuration dialog which stated that the configuration would be saved upon "quit".  

tried running "nvidia-xconfig" again, this time the same message came up, but not in a dialog box as before, only in the terminal. 

 xconfig - command not found again.

---

### Post by alvinmoneypit on 2010-11-17
I've been reading some more of that 30 page How To at nVidia and found this interesting and wonder if this could be an issue here.

> The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer, as well as precompiled versions for many of the kernels provided by popular Linux distributions.

When the installer is run, it will determine if it has a precompiled kernel interface for the kernel you are running. If it does not have one, the installer will check your system for the required kernel sources and compile the interface for you. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some distributions, no additional packages are required (e.g. Fedora Core 3, Red Hat Enterprise Linux 4).

After the correct kernel interface has been identified (either included in the .run file or compiled from source code), the kernel interface will be linked with the closed-source portion of the NVIDIA kernel module. This requires that you have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. You must have a linker installed prior to installing the NVIDIA driver.

---

### Post by tommcd on 2010-11-18
> **alvinmoneypit said:**
> now the nvidia 173 driver doesn't appear as available nor recommended whewn searching for available drivers.  The driver installed is only labelled "current" and the graphic states it is not activated.
The nvidia-current driver that you have installed does not support the nvidia 5000 series cards:
[http://packages.ubuntu.com/maverick/nvidia-current](http://packages.ubuntu.com/maverick/nvidia-current)
> GPUs such as GeForce series 6 or newer are supported. 
You need to use the nvidia-173 driver, since that is the driver that supports your 5200. It is in the Ubuntu repos:
[http://packages.ubuntu.com/maverick/nvidia-173](http://packages.ubuntu.com/maverick/nvidia-173)
> GPUs ranging from GeForce series 5 to Geforce series 9 are supported. 
Since you added that PPA repo for the nvidia driver, it may be preventing you from finding the nvidia-173 driver, since the 173 driver should be available to you. 
You seem to be installing every driver except the correct one.
Get rid of that PPA repo, since nvidia-current does not support your 5200. Just comment out the PPA repo (i.e., put a # in front of it in your */etc/apt/sources.list* file.
Then run "*sudo apt-get update*"
Then purge all nvidia drivers, then install the 173 driver. You have already confirmed that nvidia-current and nvidia-96 will not work for you, so you need to install the nvidia-173 driver, which is the correct driver for your card.
Your outputs from "*aptitude search nvidia*" indicate that you do not have nvidia-173 installed. Any installed package will have an "i" in front of it in the output from aptitude.

I don't know why you are getting the command not found message when running *nvidia-xconfig*. As for the xorg.conf file, you can enable the driver manually just by editing your xorg.conf file and changing the driver to nvidia. The reason your xorg.conf is blank is because you have not properly installed the nvidia driver. After verifying that the nvidia-173 driver is properly installed, edit your xorg.conf file and put this in it:
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```
That should enable the nvidia driver if you have properly installed the driver that supports your card.

---

### Post by alvinmoneypit on 2010-11-18
Tom,

After booting 10.10 for the first time, I downloaded and installed the nVidia 173 driver.  From page 1 of this thread:

> I can't post a screen shot - The scant info I get from Ubuntu on this driver is it's:

"NVIDIA accelerated graphics driver (version 173)[Recommended]
Tested by the Ubuntu Developers
License: Proprietary


.  However, I'll try to install it again and edit the file as you suggest.

---

### Post by toasterboy1 on 2010-11-18
To correctly purge the ppa you need to install ppa-purge and run sudo ppa-purge xorg-edgers
```
sudo apt-get install ppa-purge
sudo ppa-purge xorg-edgers
```

Sorry if I caused you more problems but I thought that there was a problem with the nvidia 173 driver and the xorg installed with maverick that is why I was using nvidia-current. Link to one of many bug posts [https://bugs.launchpad.net/ubuntu/+bug/657140]("https://bugs.launchpad.net/ubuntu/+bug/657140")

It did not even occur to me that the 5200 would not supported by that driver.

---

### Post by alvinmoneypit on 2010-11-19
I could not see any drivers anymore so I reinstalled the operating system.  I installed the recommended 173 driver as before - immediately, first thing after installing the operating system (10.10).  I remembered something someone said so I was sure to logout and login before I restarted.  Same problem, only seeing 640x480 resolution with an option to go to 320x240. 

 I have the nVidia settings program in administration as before.  As Tom suggested, I edited the xorg,conf file exactly as he described by cutting and pasting it to the end of the file.  I'd note that there was already a 'Section "Device"' section further up, but not exactly the same as he'd posted, it's minus the "nVidia Corporation part among minor other differences.  Anyway, I logged out logged in, rebooted again still the same result.  The driver, or program whatever appears to not be seeing my monitor hardware at all.  "nVidia settings" correctly notes my card.  My resolution on default (without any additional proprietary driver) is fine and adjustable.  It plays internet video fine, haven't tried a DVD yet as I'm bare bones here still.  Ubuntu Preferences>Monitors correctly identifies my monitor (16" NEC), but after I installed the 173 driver, this info changes to "unknown Monitor".

I just think it's being restricted by Ubuntu to report to the driver, or I'm missing a dependency somewhere - I just don't know where to look, or what to look for.

Thanks for all the input so far and the patience.

---

### Post by beew on 2010-11-19
> **alvinmoneypit said:**
> I could not see any drivers anymore so I reinstalled the operating system.  I installed the recommended 173 driver as before - immediately, first thing after installing the operating system (10.10).  I remembered something someone said so I was sure to logout and login before I restarted.  Same problem, only seeing 640x480 resolution with an option to go to 320x240. 

 I have the nVidia settings program in administration as before.  As Tom suggested, I edited the xorg,conf file exactly as he described by cutting and pasting it to the end of the file.  I'd note that there was already a 'Section "Device"' section further up, but not exactly the same as he'd posted, it's minus the "nVidia Corporation part among minor other differences.  Anyway, I logged out logged in, rebooted again still the same result.  The driver, or program whatever appears to not be seeing my monitor hardware at all.  "nVidia settings" correctly notes my card.  My resolution on default (without any additional proprietary driver) is fine and adjustable.  It plays internet video fine, haven't tried a DVD yet as I'm bare bones here still.  Ubuntu Preferences>Monitors correctly identifies my monitor (16" NEC), but after I installed the 173 driver, this info changes to "unknown Monitor".

I just think it's being restricted by Ubuntu to report to the driver, or I'm missing a dependency somewhere - I just don't know where to look, or what to look for.

Thanks for all the input so far and the patience.

Haven't read through all the posts, but it seems that for some reasons it doesn't work if you install the nvidia driver yourself from Synaptic. You need to let "Additional Driver" to detect, download and install the driver. Otherwise you get "activated but not in use".

If you let "Additional driver" install your driver you shouldn't need to edit xorg.conf manually (which doesn't exist in 10.10 as far as I know so I am not sure how you edit it) After the driver is installed just run "sudo nvidia-xconfig" in the terminal,--this should create the proper xorg.conf file,--then reboot and it should work.

---

### Post by alvinmoneypit on 2010-11-19
Beew,

I did do it the way you said.

I installed the operating system, wiped the whole drive.  I had Administration>AdditioanlDrivers locate the program to download.  I let it download and install it.
It is currently marked "Activated and in use".

After I checked it and logged out, logged in, check my resolutions again both in the Administration>Nvidia and in Preferences>Monitors and seeing neither were working, then I made the edit suggested by Tom, after first logging out, logging and and rebooting after each change.

It still isn't working.

I ran "sudo nvidia-xconfig". logged out, logged in, rebooted.  No Change.

---

### Post by beew on 2010-11-19
This is weird. As someone said earlier the Nvidia-96 and Nvidia-173 drivers were not compatible with Ubuntu10.10, the 173 driver is supposed to be upgraded recently, but may be there are still bugs in it.

Well I have successfully installed Nvidia-96 in 10.10 and get the high resolution and all the 3D effects and at least one person reported success by using the same method for 173 (that was probably before the 173 driver was supposedly upgraded). The method basically involves downgrading xorg to the version in Ubuntu 10.04.  For whatever it is worth, here is the link.
[http://ubuntuforums.org/showthread.php?t=1598591](http://ubuntuforums.org/showthread.php?t=1598591)

Took me a while to get it to work and there wasn't much help from the forums. I hope it will be useful to someone else. :)

---

### Post by tommcd on 2010-11-20
> **alvinmoneypit said:**
> 
... I had Administration>AdditioanlDrivers locate the program to download.  I let it download and install it.
It is currently marked "Activated and in use".
To verify that the nvidia driver is running properly post the output of:
```
glxinfo | grep -i render
```
It should report "*direct rendering: Yes*" and have your graphics card listed after 
"*OpenGL renderer string*" like this:
```

tom[data]$ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, 

```
Also, if you go into nvidia-settings and click on *OpenGL/GLX Information* on the left pane, it should say *Direct Rendering Yes* under GLX Information on the right pane.
> **alvinmoneypit said:**
> 
After I checked it and logged out, logged in, check my resolutions again both in the Administration>Nvidia and in Preferences>Monitors and seeing neither were working ...
If the nvidia driver is running properly as determined by the output of *glxinfo*, and you stil can not get your proper resolutions, then try using **xrandr** to set the proper resolution. See this on nvidia:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
And this on using xrandr: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
> **alvinmoneypit said:**
> 
I ran "sudo nvidia-xconfig". logged out, logged in, rebooted.  No Change.
So I assume that the nvidia-xconfig command ran ok this time. Is that correct? If so, then that is at least some progress here I guess.

---

### Post by alvinmoneypit on 2010-11-20
tom,

The output of 'glxinfo | grep -i render' is:

```
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
```

Should I install mesa-utils?

---

### Post by alvinmoneypit on 2010-11-20
it doesn't give me any info in terminal, but Administrator > Nvidia Settings does say under "open GL/GLX information 'Direct rendering : Yes'

---

### Post by alvinmoneypit on 2010-11-20
I downloaded mesa-utils from earlier terminal suggestion.

Now I have at least part of what Tom said - $ glxinfo | grep -i render
direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!

I noticed I don't have the details after that.

I tried to set resolution in "xrandr" but got this 
```
 xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
```

"glxinfo" yield a good bit of info including tables where the final column was either "ncon" or "none" about equal amounts of each designation.  Following is the beginning part of the output:
```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 173.14.28
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_half_float_pixel, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_S3_s3tc, GL_EXT_texture_env_add, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, GL_EXT_Cg_shader, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_two_side, 
    GL_EXT_stencil_wrap, GL_EXT_texture3D, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

120 GLX Visuals

```

I logged out and logged in, then rebooted after each attempted change, with no result that I could see.  Still at 6430x480.

---

### Post by alvinmoneypit on 2010-11-20
the output of xrandr:
```
xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

```

---

### Post by alvinmoneypit on 2010-11-20
here is the output of my xorg.conf file:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Sep 29 10:19:47 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by JavaBeanHead on 2010-11-20
I have been lurking this thread, and believe I know how to fix it. I have the same issue and worked it all day and just fixed it. (bit of a pro at this because I went through this a long time ago and fixed it)

What's your monitor make and model?

---

### Post by alvinmoneypit on 2010-11-20
Hi JBH,

It's a crt - NEC Multisync FE771SB

the default driver sees it as NEC 16"
The Nvidia 173 driver sees nothing

---

### Post by JavaBeanHead on 2010-11-20
Okay, here is my advice on what you need to do. Follow it verbatim and let me know what happens. I see that you have already reinstalled 10.10 a couple of times . . . so you should be getting skilled at it by now.

So that we can isolate the problem, if I were you, I'd reinstall it again. It will only cost you 30 minutes of your time, and will guarantee a clean slate.

Next, once the restart is done (after the install) boot into the clean OS again and let it download and install what updates it needs. This may seem unrelated, but I'm just giving you the steps I completed only moments ago. [System >> Administration >> Update Manager]. Don't fiddle with anything else - not the resolution or the display drivers.

Once the updates are done, it will ask for a restart. Comply.

After restart, go to System >> Administration >> Additional Drivers (you've been down this road before). Install (a.k.a. "activate") the RECOMMENDED driver.

Reboot.

Here's where the critical path comes in . . . hit ALT+F2 and type "gnome-terminal".  

```
sudo nvidia-xconfig
```

This will make a backup copy of your /etc/X11/xorg.conf file (which doesn't really exist at this point), and generate a new one in its place, as you have already done previously.

Now by whatever means you like, (nano, vi, whatever) edit the xorg.conf file:

```
sudo nano /etc/X11/xorg.conf
```
or
```
sudo vi /etc/X11/xorg.conf
```

Here is what you need (at minimums):

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "KDS"
    ModelName      "K-22MDWB"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
```

SPECIFICALLY you need the "correct entries" for HorizSync, and VertRefresh, formatted as you see mine. These specifications need to come from your manufacturer's specifications from the monitor (i.e. go to the website for the manufacturer for your monitor, and look up the "model" and find what the correct values are.  What you name the Identifier, VendorName, and ModelName is arbitrary, so long as you keep it consistent throughout the xorg.conf file (recommend not changing those values - just leave them).

I did this for you, and found that the [FE771SB]("http://www.amazon.com/NEC-MultiSync-FE771SB-Display-white/dp/B000068IGA") is 

```
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
```

The Section "Device" should already be there, no changes need made. 

The Section "Screen" should already be there, no changes need made.

Hence, you've only changed the values for HorizSync and VertRefresh.

Save the xorg.conf file, and reboot.

On reboot, access System >> Administration >> NVIDIA X Server Settings. Choose X Server Display Configuration on the left . . . and on the right-hand window-pane, you'll see perfectly updated values for your resolution. Pick whatever one you like.  Choose **Save to X Configuration File**.

Voila!

Shoot holes in it, but it works for me.  I solved this one time before and as illustrated, it "just works" --> [http://ubuntuforums.org/showthread.php?t=1228884](http://ubuntuforums.org/showthread.php?t=1228884)

[BTW, the resolutions supported for your monitor are 

```
640 x 480 @ 60 to 120 Hz 	Some systems may not support all modes listed.
800 x 600 @ 50 to 110 Hz
832 x 624 @ 50 to 106 Hz
1024 x 768 @ 50 to 87 Hz ....................... NEC-Mitsubishi Electronics Display cites recommended resolution at 87 Hz for optimal display performance.
1152 x 864 @ 50 to 77 Hz
1280 x 1024 @ 50 to 66 Hz
```]

Good luck.

---

### Post by alvinmoneypit on 2010-11-20
thanks, JBH,

I 'll do this tomorrow evening as I have to work tomorrow and it looks like an hour or so of stuff.  I'll post back here when I've done it.

---

### Post by alvinmoneypit on 2010-11-21
JBH,

Someone tried to have me do something like this earlier.

I don't know how to change anything in terminal with these programs without specific instruction.

Nano - What does ^Y mean, it obvious doesn't mean the keys ^Y, because it did not allow me to edit the line.

---

### Post by JavaBeanHead on 2010-11-21
Carrot (^) and letter mean to hit CTRL+<key-specified>. Have another go at it. Use Nano - it's a simple text editor. Vi has a steeper learning curve to it.

:)

---

### Post by alvinmoneypit on 2010-11-21
JBH,

Thanks for the quick reply, albeit, I guessed it before I read your reply.

YES
THIS 
FINALLY
WORKED!!

It offers a lot more resolutions than I thought possible.

The only thing is it still doesn't know the monitor, but who cares, it's working for now.  ]
It looks like all the configuration parameters are functioning as well.  Before there was one screen in the settings program that would crash it every time I navigated to it - Now even that one is working, all the sliders, etc.  I hit "detect monitor" thinking my resolutions would disappear, but they didn't, they stayed.

Thanks to you, JBH, for sticking with this thread.  Also all the others that added suggestions, even though they all didn't work, I learned a good bit.  Thanks, Tom, MeanMrMustard (say Hi to 'polythene Pam), vcr, and everyone who cared enough to add a suggestion.


I'LL MARK THIS ONE SOLVED.

Thanks again, JBH, If your ever near Cambridge, Ohio, I owe you one.

---

### Post by JavaBeanHead on 2010-11-21
Woo hoo! All that was worth it, wasn't it!!?? :guitar:

(I'll be honest, I was so sure of myself on this one, that I simply knew it would work . . . and I'm certainly glad it did! ):P )

So, for the record - the salient point, for anyone who runs into this down the road - put in the Vertical and Horizontal refresh values for YOUR monitor. 

Enjoy your new Ubuntu, as will I! And I do occasionally find myself going through Cambridge . . . from Akron here. :)

Happy Holidays,
JavaBeanHead

---

### Post by toasterboy1 on 2010-11-22
Glad to see this got fixed. Sorry if I lead you down the wrong road. Congrats for sticking with it.

---

### Post by tommcd on 2010-11-22
> **alvinmoneypit said:**
> 
YES
THIS 
FINALLY
WORKED!!
It offers a lot more resolutions than I thought possible.

Alvin,
Glad you finally got this figured out! From your output of "*glxinfo | grep -i render*", your nvidia driver is working properly.
JavaBeanHead,
Good pickup here.I never thought that it would be something as simple as setting the proper screen resolution in xorg.conf, especially since Xorg is supposed to set that up automagically, and without even a need for an xorg.conf file these days.

---

### Post by modprob on 2011-04-11
thanks solved my 6 month old issue.  (been running RH forever, wanted to learn about Ubuntu)

screen so big you cant push buttons. ( chick and egg, can run anything)cept command line.
my screen was  not supported , it's an old flat LCD Acer. 
so i followed java posted instructions.
added my Horz and vert , parameters,
it came up with my GF6200  and 1024x768 size 
sweet !

thanks 1 more time !

no other forums or help could get me here.  

CHeers !

---

### Post by JavaBeanHead on 2011-04-12
> **modprob said:**
> thanks solved my 6 month old issue.  (been running RH forever, wanted to learn about Ubuntu)

screen so big you cant push buttons. ( chick and egg, can run anything)cept command line.
my screen was  not supported , it's an old flat LCD Acer. 
so i followed java posted instructions.
added my Horz and vert , parameters,
it came up with my GF6200  and 1024x768 size 
sweet !

thanks 1 more time !

no other forums or help could get me here.  

CHeers !

Great! Glad to hear that others are still getting mileage out of this.

---

