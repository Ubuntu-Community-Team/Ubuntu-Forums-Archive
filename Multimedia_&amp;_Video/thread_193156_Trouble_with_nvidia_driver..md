---
title: "Trouble with nvidia driver."
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by EnsilZah on 2006-06-09
I've recently installed dapper and i can't get the nvidia driver to work.
I tried installing it in many ways, including the ones tseliot keeps mentioning.

Every time after i install the driver and reboot the computer gets stuck on a black screen when starting x.

There's an error in Xorg.0.log that says "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)"

My GPU is a GeForce 6600 which seems to identify as a 6600 GT (I get that in windows too).
And the Mobo is Asus P4P800.

---

### Post by croak77 on 2006-06-09
Did you follow the wiki?

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by EnsilZah on 2006-06-09
Yes, among others.

---

### Post by tseliot on 2006-06-09
```
sudo dpkg-reconfigure xserver-xorg
```

and set the driver to "vesa"

Then try my script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by EnsilZah on 2006-06-09
Tried it.
Same problem.

Monitors go black and then shut off after a few seconds.

---

### Post by croak77 on 2006-06-09
Did X work before you installed the Nvidia driver? Did you make sure that nvidia-glx and linux-restricted-modules-XXX ( XXX corresponds to your linux-image) are installed if you are using the binary drivers?

---

### Post by EnsilZah on 2006-06-09
X works with the default nv driver.
I've tried installing the driver according to the guide mentioned above and the ones by tseliot, so yes, in atleast one of them i made sure those were installed.

---

### Post by plaguevc on 2006-06-10
yeah... same here. It was working fine with the NVIDIA binary drivers, but then I updatd to dapper, and it stopped working. The Open Source drivers still work though, but I'm not sure I canrun xgl withthe open source drivers.

---

### Post by blastus on 2006-06-10
Same problem here also with GeForce FX5600. /var/log/Xorg.0.log shows:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

This is why "glxinfo | grep direct" shows:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

and maybe why [I can't run my LCD at native resolution.](http://www.ubuntuforums.org/showthread.php?t=193391) I have also tried running dpkg-reconfigure xserver-xorg and tseliot's script but the results are the same--my display is unusable at 1280x1024 with the NVIDIA driver. The default nv driver, however, has no problem with 1280x1024. On Breezy the NVIDIA driver worked.

---

### Post by croak77 on 2006-06-10
OK...Did anyone try this:

[https://wiki.ubuntu.com/NvidiaTroubleshooting](https://wiki.ubuntu.com/NvidiaTroubleshooting)

---

### Post by tseliot on 2006-06-10
[QUOTE=blastus]Same problem here also with GeForce FX5600. /var/log/Xorg.0.log shows:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

This is why "glxinfo | grep direct" shows:
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

and maybe why [I can't run my LCD at native resolution.](http://www.ubuntuforums.org/showthread.php?t=193391) I have also tried running dpkg-reconfigure xserver-xorg and tseliot's script but the results are the same--my display is unusable at 1280x1024 with the NVIDIA driver. The default nv driver, however, has no problem with 1280x1024. On Breezy the NVIDIA driver worked.[/QUOTE]
There's something wrong with your driver (I have had the same problem).
1) Download the latest version of my script (0.36) which might do the trick for you.
2) About your resolution: read point 10 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by tseliot on 2006-06-10
[QUOTE=EnsilZah]X works with the default nv driver.
I've tried installing the driver according to the guide mentioned above and the ones by tseliot, so yes, in atleast one of them i made sure those were installed.[/QUOTE]
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then
```
sudo /etc/init.d/gdm start (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm start (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by tseliot on 2006-06-10
[QUOTE=plaguevc]yeah... same here. It was working fine with the NVIDIA binary drivers, but then I updatd to dapper, and it stopped working. The Open Source drivers still work though, but I'm not sure I canrun xgl withthe open source drivers.[/QUOTE]
Did you try version 0.36 of my script?

---

### Post by pla7ma on 2006-06-10
A bit strange, but in my case the nvidia caused problems after the update from dapper to 6.06 (all 64bit). "nv" worked but "nvidia" didn't. I tried the scripts of tselliot, no luck. Eventually it turned out that it was a problem of the kernelversion: there was no new kernel in grub,so I thought 15-18 is the latest one, but after a manual grub install I could start 15-23, reinstalled the removed nvidia-glx and then did nvidia-glx configure ... and everything is fantastic,incl openGL. I just don't understand why the update didn't do the grubinstall...
maybe this helps someone..

---

### Post by EnsilZah on 2006-06-10
tseliot, i did what you said up until the "startx -- -verbose 5 -logverbose 5" stage, and then i couldn't get back to the command line.

I copied the log file in recovery mode, but i have no idea when it's written, so it might just be useless.

---

### Post by blastus on 2006-06-10
[QUOTE=tseliot]There's something wrong with your driver (I have had the same problem).
1) Download the latest version of my script (0.36) which might do the trick for you.
2) About your resolution: read point 10 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")[/QUOTE]

After spending all night on this, I have come to the conclusion that the problem is that the FX5600 is not compliant with DVI specifications. I've literally tried everything to get 1280x1024 to work with a digital DVI cable and it is a no-go on both Windows XP and Linux--the results are the same. I was able to get DVI to work at 1280x1024 on Breezy though, but with a TwinView hack (even though I only have one monitor) that I don't understand. I did try point 10 of the Problems Sections but it did not fix the problem.

Futhermore, my monitor with a DVI cable reports that the maximum pixel clock is 140 Mhz which can't be used to drive 1280x1024 @ 75Hz (which appears to be the ONLY stable refresh rate I can use at 1280x1024.) However, using a D-Sub cable (CRT) reports a maximum pixel clock at 400 Mhz, and 1280x1024 works on both Windows XP and Linux. 

What's even more mysterious, is that my nvidia driver seems to have fixed itself. I have not tried to uninstall or reinstall it and now GLX works. Because there were so many variables in this equation I don't remember exactly what I did, but I noticed the driver started working as soon as I used a D-Sub cable instead of a digital DVI cable and rebooted. To give an example of some of the things I've tried, here's my xorg.conf file:

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    # V-freq: 75.00 Hz // h-freq: 80.42 KHz
    # Modeline "1280x1024@75" 151.83 1280 1360 1544 1888 1024 1024 1027 1072

    # V-freq: 71.13 Hz  // h-freq: 76.09 KHz
    # Modeline "1280x1024@71" 140.00  1280 1352 1520 1840  1024 1024 1027 1069 

    # Horizontal sync frequency: 64.73 kHz
    # Modeline "1280x1024@60" 114.98 1280 1312 1744 1776 1024 1045 1055 1076

EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Driver         "nvidia"
    BusID	   "PCI:1:0:0"
    # Option       "ConnectedMonitor" "DFP-0"
    # Option       "RenderAccel"           "true"
    # Option       "AllowGLXWithComposite" "true"
    # Option       "UseEDID" "False"
    # Option       "TwinView"
    # Option       "MetaModes" "DFP-0: 1280x1024@75, CRT-0: 1280x1024@75"
    # Option       "TwinViewOrientation" "Clone"
    # Option       "ConnectedMonitor" "CRT-0, DFP-0"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV31 [GeForce FX 5600]"
    Monitor        "Generic Monitor"
    DefaultDepth   16
    # Option       "ExactModeTimingsDVI" "TRUE" 
    # Option       "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoEdidModes, NoVesaModes"
    # Option       "ModeValidation" "DFP-0: AllowInterlacedModes, NoEdidMaxPClkCheck"
    # Option       "ModeValidation" "DFP-0: NoEdidMaxPClkCheck"
    SubSection     "Display"
        Depth      16
        Modes      "1280x1024"
    EndSubSection
```

Maybe DVI is not mature enough yet for mainstream use? There is no reason why it should not work with my video card with the latest NVIDIA drivers for both Windows XP and Linux. Until monitor manufacturers, video card manufacturers, and the people responsible for the DVI specification get their act together, I will not use DVI. Besides, the fact that DVI cables cost so much is an indication that DVI may not be not a mature technology--there's no reason why these cables have to cost so much.

Thanks for all your help tseliot :) I'm so glad you're around on these forums. :)

---

### Post by tseliot on 2006-06-11
[QUOTE=EnsilZah]tseliot, i did what you said up until the "startx -- -verbose 5 -logverbose 5" stage, and then i couldn't get back to the command line.

I copied the log file in recovery mode, but i have no idea when it's written, so it might just be useless.[/QUOTE]
I can't see the error there.

I can only suggest you to:
1) Make sure that all your repositories are enabled (universe and multiverse):
```
sudo nano -w /etc/apt/sources.list
```

2) Update the repositories list:
```
sudo apt-get update
```

3) Try my script again

---

### Post by tseliot on 2006-06-11
[QUOTE=blastus]Futhermore, my monitor with a DVI cable reports that the maximum pixel clock is 140 Mhz which can't be used to drive 1280x1024 @ 75Hz (which appears to be the ONLY stable refresh rate I can use at 1280x1024.)[/QUOTE]
Shouldn't you use 60Hz with a DVI cable ???

---

### Post by blastus on 2006-06-11
[QUOTE=tseliot]Shouldn't you use 60Hz with a DVI cable ???[/QUOTE]

I fixed my problem! The trick I found was the proper ModeLine and the AllowNon60HzDFPModes option. :) 

[NVIDIA: How I fixed my display resolution problem with DVI-D connection!](http://www.ubuntuforums.org/showthread.php?t=194531)

---

