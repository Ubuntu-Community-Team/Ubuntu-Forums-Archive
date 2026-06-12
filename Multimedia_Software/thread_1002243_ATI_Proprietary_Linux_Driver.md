---
title: "ATI Proprietary Linux Driver"
date: 2008-12-04
forum: Multimedia Software
---

### Post by banjopikker on 2008-12-04
Hello, Does anyone know how to install the ATI Proprietary Linux Driver on  ubuntu 8.10, and does it work? Thanks.

---

### Post by EnGorDiaz on 2008-12-04
> **banjopikker said:**
> Hello, Does anyone know how to install the ATI Proprietary Linux Driver on  ubuntu 8.10, and does it work? Thanks.

search up envy in google

---

### Post by banjopikker on 2008-12-05
I have EnvyNG on my machine. I downloaded the linux proprietary driver to my desktop. What do I do now? when I open EnvyNg ,it lists some Nvidia drivers and an ati driver but there are red x's after them. How do I get EnvyNg to install the driver that I downloaded?  Thanks

---

### Post by markbuntu on 2008-12-05
The best way to get the ati driver in Intrepid is to use Hardware Manger and enable the restricted driver. This is the 8.10 driver with Ubuntu team support and tweaks expecially made for Intrepid.

You are really taking on a lot of unecessary risk by trying to get this driver from somewhere else or trying to use the newer 8.11 driver which numerous people have reported problems with.

---

### Post by zika on 2008-12-05
Since You do not have the driver now You do not have to uninstall it. I did. I even liked some time living with open-source driver and no compiz.
Then I've gone to ATI site, located the driver and dl-ed it. Let's call it t.t.
Then (in Terminal)```
(sudo) chmod +x t.t
``` and click on it in Nautilus.
Use ATICatalyst to adjust 3D.
Enjoy.

---

### Post by banjopikker on 2008-12-05
> **zika said:**
> Since You do not have the driver now You do not have to uninstall it. I did. I even liked some time living with open-source driver and no compiz.
Then I've gone to ATI site, located the driver and dl-ed it. Let's call it t.t.
Then (in Terminal)```
(sudo) chmod +x t.t
``` and click on it in Nautilus.
Use ATICatalyst to adjust 3D.
Enjoy.

Have you had good luck with the driver from the ATI site? Does TV output work? If so, could you please explain to a relative newbe with linux how to get it working? The card is an ATI all in wonder pro from a few years back. I have only a limited knowledge of using Terminal. Thanks

---

### Post by zika on 2008-12-06
> **banjopikker said:**
> Have you had good luck with the driver from the ATI site? Does TV output work? If so, could you please explain to a relative newbe with linux how to get it working? The card is an ATI all in wonder pro from a few years back. I have only a limited knowledge of using Terminal. Thanks

I do not use TV ... sorry.

Go to the ATI site. Choose "Grafic Drivers". Choose Your card. Press "Go". Download driver (let's call it "ati.run"). In Terminal go to the directory You chose to download to (Desktop is one ...). Type:```
 sudo chmod +x ati.run
``` to give that file permisson to be run. Open Nautilus (or whatever file manager You use) and navigate to the directory You chose to download to . Click on the ati.run. Or if You downloaded to Desktop simply click on it on the desktop. Choose "Complete Install"(or whatever but not "Custom"). You are done. In "Application" menu start "ATI Catalyst Center" to enable all the options You want (I swithed everything on, eventhough I rarely use 3D). You're done. Enyou.

The other option is to go "System->Administration->Hardware drivers" and let Ubuntu get You an older (but tested by Ubuntu crew) version of the (same) driver.

---

### Post by banjopikker on 2008-12-06
Thanks zika . I tried it and it caused problems. So I removed the card and put the stock card from Dell back in. Now I get an error saying that my screen resolution is running in reduced mode even though my resolution is 1024 x 768 . I have to click through two error boxes to get my screen back up. Is there any way to reset back to my original conf? Stupid me didn't back it up. thanks

---

### Post by zika on 2008-12-07
> **banjopikker said:**
> Thanks zika . I tried it and it caused problems. So I removed the card and put the stock card from Dell back in. Now I get an error saying that my screen resolution is running in reduced mode even though my resolution is 1024 x 768 . I have to click through two error boxes to get my screen back up. Is there any way to reset back to my original conf? Stupid me didn't back it up. thanks

From the top of my head, without information of which machine, card etc., I would suggest to boot with kernel ... (whatever kernel You are using now) in "recovery mode" and choose "reconfigure X" then "boot normally". But, do not hold me responsible ... :)

---

### Post by yutrero161 on 2008-12-07
success grows out of struggles to overcome difficulties.*----------------------------THE website offer Fast and Secure wow powerleveling service. [wow power leveling](http://www.wow-power-leveling.org/) 60-70, Cheap [WoW gold](http://www.live4game.com/)  10000G. The Professional [wow power leveling](http://www.wowgoldcc.com/)! Powerlevel  now. WOrld of warcraft Power Leveling,  [World Of Warcraft gold](http://www.live4game.com/) bloom of true love associated with this time of year! [Warcraft gold](http://www.live4game.com/),*

---

### Post by frogotronic on 2008-12-07
> **banjopikker said:**
> Thanks zika . I tried it and it caused problems. So I removed the card and put the stock card from Dell back in. Now I get an error saying that my screen resolution is running in reduced mode even though my resolution is 1024 x 768 . I have to click through two error boxes to get my screen back up. Is there any way to reset back to my original conf? Stupid me didn't back it up. thanks


Opps!  That was a mistake (swapping cards without reconfiguring X).  Don't worry - we can fix it.

0) Find another computer that has a working web access; point you browser to the following site: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide) 

1) Put your ATI card back in your machine.

2) Make a backup of your xorg.conf file (located at /etc/X11/xorg.conf)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backuppreATI
```

3) Follow the wiki guide.  I do all of this downloading and stuff in a Directory I've called ~/ATI.  **Warning, do not install the 8.11 drivers; they are buggy - you can use the 8.10 drivers and they seem pretty good.**  The link for the ATI download is here: [https://www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run](https://www2.ati.com/drivers/linux/ati-driver-installer-8-10-x86.x86_64.run) 

4) Follow the rest of the wiki.  You'll have to install the *.debs you've created which will have a different number sequence that what is listed in the wiki instructions (8.542; not 8.552)

```
sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.542-0ubuntu1_i386.deb fglrx-modaliases_8.542-0ubuntu1_i386.deb
```


5)  Here's my working ATI xorg.conf file.  Yours might have to be different.  I use openGL overlay.  I have an HP 6910p laptop and I regularly used external projectors (1028x768 ) and secondary monitors (1280x1024).  My native laptop screen resolution is 1280x800.


```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "on"
	Option	    "DesktopSetup" "horizontal,reverse"
	Option	    "Capabilities" "0x00000800"
	Option	    "MonitorLayout" "AUTO,LVDS"
	Option	    "AIGLX" "True"
	Option	    "AddARGBGLXVisuals" "True"
	Option      "XAANoOffscreenPixmaps" "True"
	Option	    "HSync2" "31-80"
	Option	    "VRefresh2" "56-76"
	Option	    "EnablePrivateBackZ"
	Option      "UseFBDev" "True"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection
```


Good luck and post back if you can't get your ATI card working.

- CH

---

### Post by zika on 2008-12-07
Nice post, I've learned a lot.

What is the problem with 8.11 drivers. I have them and ... knock on wood ...

When I installed them I did just chmod +x on them, executed them and nothing more. Everything went automagically. Am I missing something?

My xorg.conf is much smaller:
```

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "amdcccle-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    Monitor    "amdcccle-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by markbuntu on 2008-12-07
xorg.conf is being deprecated. All configurations are being moved to the drivers or auxilliary programs. For flgrx you can use the Catalyst Control Center or the aticonfig command line.

---

### Post by frogotronic on 2008-12-07
> **zika said:**
> Nice post, I've learned a lot.

What is the problem with 8.11 drivers. I have them and ... knock on wood ...


On some systems they build fine, but won't load on reboot.  Doesn't seem to be an issue on Intrepid, but is an issue on some Hardy systems.

- CH

---

### Post by zika on 2008-12-08
> **markbuntu said:**
> xorg.conf is being deprecated. All configurations are being moved to the drivers or auxilliary programs. For flgrx you can use the Catalyst Control Center or the aticonfig command line.

I know that. The only thing I miss in Catalyst in Linux (that is present in Windows) is overclocking section ... ;) is there some alternative ...?

---

### Post by frogotronic on 2008-12-08
> **zika said:**
> I know that. The only thing I miss in Catalyst in Linux (that is present in Windows) is overclocking section ... ;) is there some alternative ...?

Hi,

  I've never tried.  It appears that this is not as an ATI GUI, but there is a utility:  [http://ubuntuforums.org/showthread.php?t=91108](http://ubuntuforums.org/showthread.php?t=91108) 

- CH

---

