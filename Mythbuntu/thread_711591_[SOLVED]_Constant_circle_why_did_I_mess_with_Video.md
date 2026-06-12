---
title: "[SOLVED] Constant circle: why did I mess with Video drivers"
date: 2008-02-29
forum: Mythbuntu
---

### Post by volkswagner on 2008-02-29
Why didn't I leave well enough alone?  I guess I was after perfection!

I was trying to get a higher resolution for my LCD.  I was using restricted drivers for my Nvidia Geforce 6200.  I backed up my xorg.conf file.  I installed and ran envy for the latest nvidia drivers.  After running envy I would get black screen when trying to play recorded and live tv.

I tried to uninstall the nvidia drivers via envy.  I copied my backup into xorg.conf

No matter what I do for the past two days I cant get back my previous settings.  When I go through screen setup, I have tried to "install" /"enable" restricted drivers.  When I hit the test button, I get several screen flashes then myth opens.  No changes.  If I hit OK, I am prompted to log out all users.  After logging out and back in, I am greeted with the dreaded "Ubuntu is running in low graphics mode".  I then click configure and start the whole vicious cycle all over again.

I have also tried within mythbuntu-control-centre.  No matter what I do the settings go back to Vesa drivers.  I have tried serveral times to apply my backed up copy of xorg.conf.  Even when it sticks I still have no joy. 

If I  click on nvidia-settings I am told it is not running and I should run "nvidia-config".  When I run this, Nvidia creates a new xorg.conf file.  Great but I still get black screen on video play.

How can I get things back to the way they were?

Here is my old copy of xorg.conf  any clues?

Does it appear I was using restricted drivers?

I am so confused.  I don't even know how the checkbox works in the restricted drivers dialog.  I have seen the box checked and verbage says not in use.  I have seen it not checked and verbage driver in use???????

```

Section "ServerLayout"

        Identifier      "Default Layout"

  screen "Default Screen" 0 0

        Inputdevice     "Generic Keyboard"

        Inputdevice     "Configured Mouse"

EndSection



Section "Module"

        Load            "glx"

        Load            "vnc"

EndSection



Section "InputDevice"

        Identifier      "Generic Keyboard"

        Driver          "kbd"

        Option          "CoreKeyboard"

        Option          "XkbRules"      "xorg"

        Option          "XkbModel"      "pc105"

        Option          "XkbLayout"     "us"

EndSection



Section "InputDevice"

        Identifier      "Configured Mouse"

        Driver          "mouse"

        Option          "CorePointer"

        Option          "Device"        "/dev/input/mice"

        Option          "Protocol"      "ImPS/2"

        Option          "ZAxisMapping"  "4 5"

        Option          "Emulate3Buttons"       "true"

EndSection



Section "Monitor"

        Identifier      "Generic Monitor"

        Option          "DPMS"

EndSection



Section "Device"

        Identifier      "Generic Video Card"
 Driver          "nvidia"

        Option          "DPI"   "100x100"

        Option          "UseEvents"     "1"

        Option          "AddARGBVisuals"        "1"

        Option          "AddARGBGLXVisuals"     "1"

        Option          "NoLogo"        "1"

EndSection



Section "Screen"

        Identifier      "Default Screen"

        Device          "Generic Video Card"

        Monitor         "Generic Monitor"

        Defaultdepth    24

        SubSection "Display"

                Depth   24

                Modes           "nvidia-auto-select"    "1920x1080"     "1280x720"      "1024x768"      "720x480"       "800x600"       "640x480"

        EndSubSection

        Option          "SecurityTypes" "VncAuth"

        Option          "UserPasswdVerifier"    "VncAuth"
```

---

### Post by xeth_delta on 2008-02-29
If had to guess I would say it might be that the drivers you initially had on your system have not been properly reinstalled. I do not use restricted manager myself, since my laptop has an intel card, but I am wondering if you can purge the current configuration and reinstall.
For instance the package management system (apt-get/aptitude/synaptic/adept) has the option to purge a package and its associated configuration files.

---

### Post by billrad1 on 2008-02-29
I have the same problem on a desktop.  I installed the latest nvidia drivers, from nvidia's installer, and worked perfectly as root (per their instructions to install as root).

 However, now as myself logged in as the user, I am in some kind of loop the loop, with the low res box.

Ouch.

I guess I'll try purging the video drivers.

If I find the answer, I'll post it here. I have tried Envy, which usually works well

billrad1

---

### Post by hyperair on 2008-03-01
Have you restarted xorg? If so post the following:
```

dmesg | grep -i nv

```
```

cat /var/log/Xorg.0.log

```

---

### Post by volkswagner on 2008-03-01
```
eric@Bedroom:~$ dmesg | grep -i nv
[    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff72000 (ACPI NVS)
[   18.487795] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
```


```
cat /var/log/Xorg.0.log
```

Attached complete log.  Here are some possible meaningful snippets. 

        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor


(II) NV(0): Max H-Image Size [cm]: horiz.: 4  vert.: 3
                         this is  a wide screen don't know why the above is true?

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I am using free drivers because I am not able to simply check the restricted drivers box...get running in low graphics mode.

---

### Post by xeth_delta on 2008-03-01
Ok, this method is not as elegant, but have you tried installing the nVidia drivers without making use of the restricted drivers manager. I mean, download the correct drivers version from nVidia and install? Have you also checked in the apt-get database? Maybe you can install the driver through the package management system.

---

### Post by volkswagner on 2008-03-01
> Have you also checked in the apt-get database? Maybe you can install the driver through the package management system.

Not sure what to do here.  Any details would be appreciated.  Is there any location I can look for the old drivers, in the file system?

I will check out Nvidia.com for the linux drivers.

---

### Post by xeth_delta on 2008-03-01
> **volkswagner said:**
> Not sure what to do here.  Any details would be appreciated.  Is there any location I can look for the old drivers, in the file system?

I will check out Nvidia.com for the linux drivers.

Open synaptic and search for nvidia or in the command line:
```
aptitude search nvidia
```

A list will be presented to you, and there you will be able to find some nvidia binaries and restricted modules. in the case of the command line an "i" indicates that some package is already installed.

I am not sure what the result will be, as I said, I don't have an nvidia card on this computer.

---

### Post by volkswagner on 2008-03-01
Since I still need some hand holding, see results of aptitude search:
```

eric@Bedroom:~$ aptitude search nvidia
p   nvidia-cg-toolkit               - NVIDIA Cg Toolkit installer               
c   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
c   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
i   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
c   nvidia-glx-new-dev              - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.7185          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.9639          -                                           
v   nvidia-kernel-100.14.19         -                                           
i A nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-legacy-kernel-source     - NVIDIA binary 'legacy' kernel module sourc
p   nvidia-new-kernel-source        - NVIDIA binary 'new' kernel module source  
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool 
```

I just checked the system and restricted is enabled but not in use.  Vesa drivers are being used.  What shall I purge and how?

What command restarts X?
If I am issuing commands via ssh on another machine, will using the -X argument cause any problems?  Will the commands not work because I am forwarding the x-session?
The reason I ask, I have a habit now of always using the -X argument for ease of using GUI tools/apps on the host machine.  Is this a bad habit?

---

### Post by volkswagner on 2008-03-02
Downloaded driver from Nvidia.com.  Installed drivers after shutting down Xserver.  Install said success, and I selected automatic config of xorg.  I was greeted with the hair pulling "Ubuntu is running in low graphics mode".  I select configure, now in the configuration the selection of open drivers or proprietary is grayed out.  Now the Mythbuntu-control-centre says proprietary drivers are in use.. WTF

In screen config Vesa is running...WTF

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Now I am not in low graphic mode.

Went into proprietory manager and checked the box for nvidia drivers.
Restart is required.  So I restart.

Greeted with the "ubuntu is running in low graphics mode"

I cant for the life of me get the proprietary drivers installed.
The best I can do is get the free Nvidia drivers running to give me a suitable screen resolution.  But this wont help for HD playback.


Here is the driver I installed  NVIDIA-Linux-x86-169.12-pkg1.run.

Shall I try an earlier version?

```
eric@Bedroom:~$ dmesg | grep -i nv
[    0.000000]  BIOS-e820: 000000007ff70000 - 000000007ff72000 (ACPI NVS)
[   18.676011] Simple Boot Flag value 0x87 read from CMOS RAM was invalid

```

```
cat /var/log/Xorg.0.log
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not foun

```

---

### Post by laga on 2008-03-02
Let's see.

The nvidia drivers in Ubuntu consist of two parts:

* the kernel modules in the linux-restricted-modules package
* the libraries which are shipped in nvidia-glx-legacy, nvidia-glx or nvidia-glx-new. Which package is used depends on the age of your VGA card.

It looks like you still have the nvidia-glx-new package installed which explains the error you're seeing in Xorg.0.log when you're using the free driver. The glx lib is complaining that the Nvidia driver isn't used, but it#s not critical (for X, at least).

I was just looking at the envy website and it seems there's a command to uninstall all drivers. If you're using envy-ng, it might be as simple as running ```
envyng --uninstall-all
```. For regular envy, ```
envy --uninstall-all
``` should do the trick. Have you read the FAQ on [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ?

--laga

---

### Post by volkswagner on 2008-03-02
I already uninstalled envy.  So those commands wont work.  I uninstalled the drivers via envy GUI.  Then I removed envy via synaptic, in hopes it would help get rid of everything.

Do you know what command to issue to purge what needs to be purged?

---

### Post by xeth_delta on 2008-03-02
> **volkswagner said:**
> Since I still need some hand holding, see results of aptitude search:
```

eric@Bedroom:~$ aptitude search nvidia
p   nvidia-cg-toolkit               - NVIDIA Cg Toolkit installer               
c   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
c   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
i   nvidia-glx-new                  - NVIDIA binary XFree86 4.x/X.Org 'new' driv
c   nvidia-glx-new-dev              - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.7185          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.9639          -                                           
v   nvidia-kernel-100.14.19         -                                           
i A nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source        
p   nvidia-legacy-kernel-source     - NVIDIA binary 'legacy' kernel module sourc
p   nvidia-new-kernel-source        - NVIDIA binary 'new' kernel module source  
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool 
```

I just checked the system and restricted is enabled but not in use.  Vesa drivers are being used.  What shall I purge and how?

What command restarts X?
If I am issuing commands via ssh on another machine, will using the -X argument cause any problems?  Will the commands not work because I am forwarding the x-session?
The reason I ask, I have a habit now of always using the -X argument for ease of using GUI tools/apps on the host machine.  Is this a bad habit?

If you want to purge a package from the system via apt, you use "sudo aptitude purge package_name". For example, if you want to purge "nvidia-glx":
```
sudo aptitude purge nvidia-glx
```
The "i" in front of a package means it is installed, a "p" that there is no trace of it on the system, "c" that the package was uninstalled but that the config files are still on the system (to remove them, you have to use purge). The "v" refers to a virtual package.

---

### Post by volkswagner on 2008-03-02
> **xeth_delta said:**
> If you want to purge a package from the system via apt, you use "sudo aptitude purge package_name". For example, if you want to purge "nvidia-glx":
```
sudo aptitude purge nvidia-glx
```
The "i" in front of a package means it is installed, a "p" that there is no trace of it on the system, "c" that the package was uninstalled but that the config files are still on the system (to remove them, you have to use purge). The "v" refers to a virtual package.

Thanks this helped.  I had to stop xserver then flush.

I now have the latest nvida drivers 169.xx.x

I still have X crash when trying to view live tv.  I don't know what I screwed up.  I may have to start over with older drivers.

---

### Post by volkswagner on 2008-03-17
I will try to remember all the steps I took to get my restricted drivers back.

Here is what I did, I am not sure if all or any of the following are required.

I used Envy to remove the drivers so If you don't have it installed, install it now.  Don't run Envy though.

I also disabled all autostart programs(settings>autostart programs>deselect all

at the local machine (pc with driver you want to remove), stop X-server

```
sudo /etc/init.d/gdm stop
```

Create an SSH session from another machine on the LAN (this may not be required, I was not able to get a console on my machine with X-server stopped).  Don't enable forward -X.

```
ssh username@ip
```

Change directory to /

```
cd /
```

Run Envy in text mode

```
envy -t
```

choose choice 6 "Clean the installation of any Nvidia drivers" (ATI choices avail also)

```
6
```

Follow an remaining steps

Restart

```
8
```


At the local machine if running in low graphics mode>select continue

Open mythbuntu control centre from the applications menu.

Go to restricted drivers, check box for enable

Restart X-server (this may need to be done on a remote machine as I did)

```
sudo /etc/init.d/gdm restart
```

Open Mythbuntu-control-centre to see if under restricted driver manager you can open Nvidia settings.  If you can set your screen resolution.

If can or can't a sytem restart may be necessary.

You should have joy with restricted drivers.  Don't forget to enable the autostart programs

Restart again to see if it all stayed

I hope I did not forget anything.  After my one hundredth try I started to keep a log of my steps.  Got tired of that after another 10-20 tries.  I finally discovered these steps around try number 150 :mad:

---

