---
title: "Nvidia Geforce2 MX400 problems - PLEASE HELP!!"
date: 2009-06-12
forum: Multimedia Software
---

### Post by chinbo99 on 2009-06-12
Hi All,

Am at the end of my tether with this so lets see if anyone can help me.

Have tried multiple ways to get this graphics card working on my 8.10 install, and cannot for the life of me figure out why it won't.... except it sort of does!!!!

Let me explain. Choosing either the standard proprietary drivers recommended by ubuntu (the restricted ones), everything installs fine and there are no errors on boot. I have also managed to install them manually by downloading from Nvidia directly, also with no errors, in the Xorg log or otherwise, and also successfully with EnvyNG. I have followed many tutorials on how to configure the xorg.conf file successfully, adding various lines to load modules etc. with varying effects.

The problem comes in when the ubuntu desktop screen actually loads. I have the desktop to auto-login so don't see the login splash screen, but when the desktop loads it all goes into one big smeary mess that I can sometimes see and make out parts of and other times cannot. It lets me control the mouse for a few seconds and then locks up completely. On one occasion out of many I managed to get a completely working desktop with no problems, but with absolutely no changes to any configuration files, on reboot the same problems returned.

I know I haven't described the problem particularly well, but given that I am not getting any errors, I don't really know what information I can give you. The system functions fine with the open-source "nv" drivers that are part of ubuntu, but I can't use any desktop-effects or extra functions with this, and renders the graphics card pretty useless.

I don't know if it makes much difference but I'm running the setup on a system with an AMD Semperon processor, and I think I read somewhere that there can be problems with graphics and these processors?!??

Anyway, given what I've said, does anyone have any ideas, or anyone suffered similar problems? I'll happily give any other info needed, just not saw what to give at the moment

Chinbo99

---

### Post by gradinaruvasile on 2009-06-12
I have a computer with nvidia mx 440 (running on an Athlon XP 2500+) and never had any problems with it... Make sure u use the 96 or 71(i think this is the one for this old card) series drivers, not the latest ones (180). Also before u install the drivers try to remove the previous ones. Normally you dont have to edit stuff, the nvidia drivers worked for me perfectly with no configuration at all.
If u have edited xorg.conf, you could reconfigure it to the defaults with
sudo dpkg-reconfigure -phigh xserver-xorg
This command will reconfigure the xserver to its defaults (nv driver etc0. Next try to install the restricted drivers
Could be a hardware problem too.

---

### Post by chinbo99 on 2009-06-12
> **gradinaruvasile said:**
> I have a computer with nvidia mx 440 (running on an Athlon XP 2500+) and never had any problems with it... Make sure u use the 96 or 71(i think this is the one for this old card) series drivers, not the latest ones (180). Also before u install the drivers try to remove the previous ones. Normally you dont have to edit stuff, the nvidia drivers worked for me perfectly with no configuration at all.
If u have edited xorg.conf, you could reconfigure it to the defaults with
sudo dpkg-reconfigure -phigh xserver-xorg
This command will reconfigure the xserver to its defaults (nv driver etc0. Next try to install the restricted drivers
Could be a hardware problem too.

Thanks for the reply. I'm starting to think it may be a hardware problem, as I've tried everything you have said. I've used the correct drivers, 3 different versions actually, removed the correct files (purged) reconfigured X server multiple times, and still no joy. I've tried from a fresh install to enable the restricted drivers, without editing any config files and still the same problems.

Although, I dual-boot this machine with WinXp and have no problems with the drivers or card, and can fully utilise the cards features and 3d acceleration using the Official Nvidia drivers.

The mystery continues.....

---

### Post by aston4 on 2009-06-30
It's not a hardware problem, it is Ubuntu's problem.  I have an MX400 card, I think the board was made by MSI, it was very expensive back in the day.  Ubuntu 8.04 failed with this card, 9.04 failed also, the proprietary drivers simply don't work under Ubuntu, and it is a huge PITA, caused me to dump Ubuntu for a long time.  I'm typing this from windows now unfortunately, because I can't have dual monitors without proprietary drivers.  Experiencing exact same as you, if you search around the web more, many other people report this bug.

---

### Post by Davec.hh on 2009-07-19
I seem to be having a similar problem :(. I've replaced MS XP with Ubuntu 8.04 allowed it to update, all without problem all be it in 800x600 resolution. Then I allowed Ubuntu to get and install the NVIDIA drivers. Now the screen is a bit of a mess. I'm using an old Althlon with GeForce2 onboard adaptor.

Any suggestions - I can't view the screen to do anything sensible with the system.

---

### Post by wmasouthbay on 2010-01-25
Hi,
I have Nvidia Geforce2 MX400 graphic card installed with Sony sdm-hs73 lcd monitor that is capable of displaying 1280x1024. I have installed ubuntu 9.10. Before the restrict driver was installed, the max resolution were 800*640, but after installing the restrict driver, max resolution were dropped down to 640*480!
I would like to have resolution of 1280*1024 if possible or minimum of 1024*768.
Any idea??? Your help is appreciated.

The following is my xorg.cnf content:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by llawwehttam on 2010-01-25
> **wmasouthbay said:**
> Hi,
I have Nvidia Geforce2 MX400 graphic card installed with Sony sdm-hs73 lcd monitor that is capable of displaying 1280x1024. I have installed ubuntu 9.10. Before the restrict driver was installed, the max resolution were 800*640, but after installing the restrict driver, max resolution were dropped down to 640*480!
I would like to have resolution of 1280*1024 if possible or minimum of 1024*768.
Any idea??? Your help is appreciated.

The following is my xorg.cnf content:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Have you tried nvidia-config

---

### Post by wmasouthbay on 2010-01-25
> **llawwehttam said:**
> Have you tried nvidia-config

The following is an error message when I did "nvidia-xconfig" in terminal:

jae@jae-desktop:~$ nvidia-config
No command 'nvidia-config' found, did you mean:
 Command 'nvidia-xconfig' from package 'nvidia-glx-185' (restricted)
 Command 'nvidia-xconfig' from package 'nvidia-glx-96' (restricted)
 Command 'nvidia-xconfig' from package 'nvidia-glx-173' (restricted)
nvidia-config: command not found
jae@jae-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "(null)" referenced by Screen "Default
                  Screen".


ERROR: Unable to write to directory '/etc/X11'.

Any comment for this error message or how to fix the issue of limited resolution?

Many thanks in advance!

---

### Post by Yellow Pasque on 2010-01-25
```
sudo nvidia-config
```

---

### Post by hhlp on 2010-01-25
first backup your xorg config :

sudo cp /etc/X11/xorg.conf.backup

and replace the monitor with this one :

########################################################
# Monitor 'Nvidia Graphics Card' Layout
########################################################

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "record"
    Load           "vnc"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce2 MX/MX 400"
    BusID	   "PCI:1:0:0"
    Option  "NoLogo" "True"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "RenderAccel" "true"
    Option         "NVAGP" "3"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by wmasouthbay on 2010-01-25
It took me awhile to figure out how to edit in terminal.
I edited the xorg.cnf as described by "hhlp" but the results were same.It is limited to max 640*480.I am not sure what to do to correct the issue on hand. Any suggestion????

---

