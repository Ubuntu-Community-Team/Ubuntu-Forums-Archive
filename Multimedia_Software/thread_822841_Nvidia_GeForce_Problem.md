---
title: "Nvidia GeForce Problem"
date: 2008-06-08
forum: Multimedia Software
---

### Post by fredsfurste on 2008-06-08
Hi,
I got a problem that I hope someone can help me with. I have installed the latest version of Unbuntu on my old Toshiba laptop. But I cannot get the graphic card to work as it should. The max resolution Ubuntu can display is 800x600 when my computer really can show 1024x768.  The driver is installed and working but I got a anoying black bar on the right side of the screen. I have followed this tutorial: 

[http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy]("http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy")

But I cannot get the last part working where I change the resolution settings with Ghex2. I tried to change byte 56 from C9 to the value 00 but nothing happens. I have no clue what to do. Please help me... becuse I really want to get the most out of my Ubuntu. I really love it...

Section "Screen"

        Identifier      "Default Screen"

        Monitor         "Configured Monitor"

        Device          "Configured Video Device"

        Option          "AddARGBGLXVisuals"     "True"

        Option          "UseDisplayDevice"      "DFP"

        Option          "CostumEDID" "DFP-0:/etc/X11/edid-new.bin"

        Defaultdepth    24

EndSection


Section "Device"

        Identifier      "Configured Video Device"

        Driver          "nvidia"

        Option          "NoLogo"        "True"

        Option          "UseDisplayDevice"      "DFP-0"

EndSection



Section "InputDevice"

        Identifier      "Generic Keyboard"

        Driver          "kbd"

        Option          "XkbRules"      "xorg"

        Option          "XkbModel"      "pc105"

        Option          "XkbLayout"     "se"

EndSection



Section "InputDevice"

        Identifier      "Configured Mouse"

        Driver          "mouse"

        Option          "CorePointer"

        Option          "Emulate3Buttons"       "true"

EndSection



Section "InputDevice"

        Identifier      "Synaptics Touchpad"

        Driver          "synaptics"

        Option          "SendCoreEvents"        "true"

        Option          "Device"        "/dev/psaux"

        Option          "Protocol"      "auto-dev"

        Option          "HorizEdgeScroll"       "0"

EndSection



Section "ServerLayout"

        Identifier      "Default Layout"

  screen "Default Screen"

        Inputdevice     "Synaptics Touchpad"

EndSection



Section "Module"

        Load            "glx"

EndSection



Section "Monitor"

        Identifier      "Configured Monitor"

EndSection



Section "Extensions"

        Option          "Composite"     "Enable"

EndSection



/Fredrik

---

### Post by Unix_Slayer on 2008-06-08
> **fredsfurste said:**
> Hi,
I got a problem that I hope someone can help me with. I have installed the latest version of Unbuntu on my old Toshiba laptop. But I cannot get the graphic card to work as it should. The max resolution Ubuntu can display is 800x600 when my computer really can show 1024x768.  The driver is installed and working but I got a anoying black bar on the right side of the screen. I have followed this tutorial: 

[http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy]("http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy")

But I cannot get the last part working where I change the resolution settings with Ghex2. I tried to change byte 56 from C9 to the value 00 but nothing happens. I have no clue what to do. Please help me... becuse I really want to get the most out of my Ubuntu. I really love it...

Section "Screen"

        Identifier      "Default Screen"

        Monitor         "Configured Monitor"

        Device          "Configured Video Device"

        Option          "AddARGBGLXVisuals"     "True"

        Option          "UseDisplayDevice"      "DFP"

        Option          "CostumEDID" "DFP-0:/etc/X11/edid-new.bin"

        Defaultdepth    24

EndSection


Section "Device"

        Identifier      "Configured Video Device"

        Driver          "nvidia"

        Option          "NoLogo"        "True"

        Option          "UseDisplayDevice"      "DFP-0"

EndSection



Section "InputDevice"

        Identifier      "Generic Keyboard"

        Driver          "kbd"

        Option          "XkbRules"      "xorg"

        Option          "XkbModel"      "pc105"

        Option          "XkbLayout"     "se"

EndSection



Section "InputDevice"

        Identifier      "Configured Mouse"

        Driver          "mouse"

        Option          "CorePointer"

        Option          "Emulate3Buttons"       "true"

EndSection



Section "InputDevice"

        Identifier      "Synaptics Touchpad"

        Driver          "synaptics"

        Option          "SendCoreEvents"        "true"

        Option          "Device"        "/dev/psaux"

        Option          "Protocol"      "auto-dev"

        Option          "HorizEdgeScroll"       "0"

EndSection



Section "ServerLayout"

        Identifier      "Default Layout"

  screen "Default Screen"

        Inputdevice     "Synaptics Touchpad"

EndSection



Section "Module"

        Load            "glx"

EndSection



Section "Monitor"

        Identifier      "Configured Monitor"

EndSection



Section "Extensions"

        Option          "Composite"     "Enable"

EndSection



/Fredrik

**Have checked to see if the driver is in use?**

[IMG]http://www.r3uk.com/images/stories/site_content/tips/nvidia/gutsy-restricted.jpg[/IMG]


**After that I would assume your monitor is not setup properly**

---

### Post by fredsfurste on 2008-06-08
Yes, the driver is in use. I have not done any setup for the monitor... don't know how. /F

---

### Post by Unix_Slayer on 2008-06-08
> **fredsfurste said:**
> Yes, the driver is in use. I have not done any setup for the monitor... don't know how. /F

Has it worked prior? I was wondering if you had an old xorg.conf file in your /etc/X11 directory when it was working normally. You need to configure the proper monitor device in your xorg.conf. Mine is below. The automatic device setup apparently in your case is not correct. This would need to be setup by nvidia-xconfig properly.

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "LGE"
    ModelName      "LG L194WT"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

---

### Post by Erlander on 2008-06-08
I have 2 systems running Ubuntu 8.04.  The main one specs are as below.  No video problems using the nvidia glx new driver.

The second system has a 7600 GS display card which with the automatic install will not give better than 800 x 600.  I tried everything including Envy.  Nothing worked until with Envy I removed the driver reverting back to the nv driver as opposed to the NVIDIA.  This gives the full range of resolutions but no video acceleration.  its not good but better than 800 x 600.

Rob

---

### Post by Unix_Slayer on 2008-06-08
> **Erlander said:**
> I have 2 systems running Ubuntu 8.04.  The main one specs are as below.  No video problems using the nvidia glx new driver.

The second system has a 7600 GS display card which with the automatic install will not give better than 800 x 600.  I tried everything including Envy.  Nothing worked until with Envy I removed the driver reverting back to the nv driver as opposed to the NVIDIA.  This gives the full range of resolutions but no video acceleration.  its not good but better than 800 x 600.

Rob

Are both of your systems using the same monitor? I really don't like the nvidia-glx-new driver. Causes more problems. Are you running KDE or Gnome?

---

### Post by Erlander on 2008-06-08
The second system has a Dell P1130 20" monitor on the 7600 GS and won't work on the Nvidia new drivers.

Gnome on both.

Rob

---

### Post by Unix_Slayer on 2008-06-08
> **Erlander said:**
> The second system has a Dell P1130 20" monitor on the 7600 GS and won't work on the Nvidia new drivers.

Gnome on both.

Rob

So you've tried to switch monitors from system, to system to see the results? Two Gnomes... I would switch one of them to KDE4. I know a lot of people like Gnome better, but the new KDE4 is really working nice. And it's easier to config. But getting back to your problem..... running nvidia-xconfig should fix the monitor situation. Have you run nvidia-xconfig lately? And have you checked the timestamp on the xorg.conf? I'm wondering if it's saving the configuration at all.

---

### Post by Erlander on 2008-06-08
No I haven't.

Not sure I want to risk it.  The main system is running well and I want to keep it that way. 

I will think about trying it later today.

Rob

---

### Post by Unix_Slayer on 2008-06-08
> **Erlander said:**
> No I haven't.

Not sure I want to risk it.  The main system is running well and I want to keep it that way. 

I will think about trying it later today.

Rob

I would think at least the generic response from nvidia-xconfig would work.

---

### Post by fredsfurste on 2008-06-09
Hi, it's me again.

Do you smart people think that it might to do with the driver to my laptop screen that gives me problems? Becuse the 3D works... it is just the resolution that is missing. As you can see I know nothing about what I am asking about. But is there a way to try to configure the screen to make it to show higher resolution?

/Fredrik from Sweden

---

### Post by Pjotr123 on 2008-06-09
Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by Unix_Slayer on 2008-06-09
> **fredsfurste said:**
> Hi, it's me again.

Do you smart people think that it might to do with the driver to my laptop screen that gives me problems? Becuse the 3D works... it is just the resolution that is missing. As you can see I know nothing about what I am asking about. But is there a way to try to configure the screen to make it to show higher resolution?

/Fredrik from Sweden


In /etc/X11 directory would be the xorg.conf  Please make a backup before you try messing with it:

```
sudo cp xorg.conf xorg.conf.works
```

Under the monitor section you can tell it what resolution you prefer. For instance:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Modes   "800x600"   **[COLOR="Red"]<====here is your resolution[/COLOR]**
        EndSubSection
```


If you change it to 1440x900 or 1024x768. Whatever your monitor will take, that's what you put in there. But I can't stress more about backing up your xorg.conf before beginning. I hope you know how to run nano, or gedit. You will need an editor to change settings manually. If it screws up your X11 completely, and won't start. Just replace the xorg.conf with the xorg.conf.works file like so:

```
sudo cp xorg.conf.works xorg.conf
```



This will restore it to the way it was..

---

