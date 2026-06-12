---
title: "Dual monitor with nvidia and with Unity 3d"
date: 2011-05-05
forum: Multimedia Software
---

### Post by nathema on 2011-05-05
**[COLOR=Red]FIXED, working xorg.conf [here]("http://ubuntuforums.org/showpost.php?p=10800255&postcount=12")[/COLOR]**

**Opening post:**
How can i be able to enable dynamically my second monitor and use Unity at the same time?

_Summary system:_
HP Compaq 8710p laptop, Nvidia Quadra 320M, Natty 64bit, with attached 2nd 19" monitor

_ Description steps taken this far:_
By default ubuntu ships with the following xorg.conf conform the new minimalist trend:
```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```I use the nvidia-current binary drivers.

In this configuration:

[LIST]
[*]Unity works
[*]Xrandr sees 1 screen (so no configuration of second screen possible)
[*]Standard monitor configuration tool in Ubuntu shows 1 screen
[/LIST]
With [http://willem.engen.nl/projects/disper/](http://willem.engen.nl/projects/disper/)
```

disper -d auto -e
```my second monitor comes alive. My laptopscreen becomes dark (with moving mouse cursor). Unity / Ubuntu classic (no effects) go into scrambled mode. Mouse is moving, objects are not clickable.

Because the above (dynamic) steps did not work, i turned to the NVidia configuration UI:

[LIST]
[*]Twinview scrambles my screen like disper for Ubuntu classic (no effects). Unity did not show.
[*]2 seperate screen resulted in application errors.
[*]With Xinerama unity does not show, but at least i can be productive at work
[/LIST]
With Xinerama my xorg.conf is:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" RightOf "Screen1"
    Screen      1  "Screen1" 0 0
    Option         "Xinerama" "1"
EndSection

Section "ServerFlags"
    # Not working with Xinerama anyways.
    Option    "RandR" "on"
EndSection

Section "Files"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1916W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 320M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 320M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1680x1050 +0+0; DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by nathema on 2011-05-06
Is ATI/Intel dualscreen working out of the box and dynamically under Ubuntu 11.04 and even with unity?

---

### Post by nathema on 2011-05-08
I read statements that this is because a bug in the NVidia driver, not able to work properly with X server 1.10.

Can somebody confirm this? Do other distributions encounter the same problem?

---

### Post by nathema on 2011-05-08
[Lauchpad bug 703688]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/703688")
[Lauchpad bug 711409]("https://bugs.launchpad.net/ubuntu/natty/+source/nvidia-graphics-drivers/+bug/711409")
[https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html](https://lists.ubuntu.com/archives/ubuntu-x/2011-February/001050.html) (it is possible this message is outdated)

---

### Post by nathema on 2011-05-08
nvidia-current is the newest stable NVidia driver and NVidia says it works for X server 1.10.

So is this afterall an ubuntu thing?

---

### Post by MarcelSt on 2011-05-09
I got it working following this manual, [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html"). Just install nvidia-glx-185 and don't bother looking for the modules section where you need to replace nv with glx. It isn't there anymore.

Working like a charm now.

If you like i'll post my xorg.conf.

---

### Post by nathema on 2011-05-09
> **MarcelSt said:**
> I got it working following this manual, [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html). Just install nvidia-glx-185 and don't bother looking for the modules section where you need to replace nv with glx. It isn't there anymore.

Working like a charm now.

If you like i'll post my xorg.conf.

I'm quite interested in your xorg.conf!

Does it:
- provide unity 3d support on dualscreen
- and/or provide dynamically disabling the second screen. I have a laptop and sometimes switch location and disconnect the screen.

Postscript: nvidia-glx-185 is an transitional package and used for distro upgrades. It installs nvidia-current (which i use) and nvidia-settings.

---

### Post by nathema on 2011-05-09
Quite interesting [blog entry]("http://morgancollett.wordpress.com/2008/11/25/nvidia-twinview-and-xrandr/") about dynamic switching.

I'll also give this one a shot, but if my memory serves me correctly, in Twinview mode xrandr shows only 1 head. To be testen tomorrow @ work.

:EDIT:
Xinerama: 2 screen definition
Twinview: 1 screen definition
2 XServers: 2 devices with each 1 screen

Thinking of this maybe it's obvious xrandr shows only 1 screen. Checking tomorrow.

Point about Unity remains unaltered. Unity 3d still not working in Twinview/Xinerama resulting in an non-responsive/scrambled screen. 2 Xservers running, one for  each head is a possibility, but the errors I got were alarming. Checking tomorrow also.

PS. Most of this thread is an monologue, but I'm not giving up. Lot of gossip, lots of posts with people with equal resolution screens in fixed setup, not much working till now.
It was working under 10.04 tho.

---

### Post by nathema on 2011-05-09
Using the [NVidia Twinview documentation]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-g.html") i created the following untested xorg.conf with twinview:```

Section "ServerFlags"
    Option    "RandR" "on"
EndSection

Section "Device"
    Identifier     "quadra"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 320M"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "screen"
    Device         "quadra"
    DefaultDepth    24
    Option         "TwinView"
    Option         "MetaModes" "DFP-0: 1680x1050, CRT-0: 1400x900 @1400x1050"
    Option       "TwinViewOrientation" "CRT-0 RightOf DFP-0"
    Option         "HorizSync"   "CRT-0: 31 - 84; DFP-0: 30 - 75"
    Option         "VertRefresh" "CRT-0: 56-76; DFP-0: 60"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
Have to wait till wednesday to be able to test it at work.

---

### Post by JayBofMA on 2011-05-10
I have been struggling with a similar issue on a Dell Precision M65 with NVIDIA Quadro FX 350M.  I found the GUI editor to be inconsistent with what is updated when I "save" a change.  I have resorted to manually modifying the file.

I am just getting back into Linux after many years.  I had never used X in my Red Hat days, so I am unfamiliar with all the xorg.conf nuances.  I find it interesting that similar to what you have posted myh xorg.conf seemed to have two entries for "metamodes".  Although yours are listed for the laptop (DFP) whereas mine are listed for the CRT (aka DFP but what does X know?)  I presume that this indicates your laptop is secondary/Monitor 1?

Also, despite my having got Separate X and Xinerama "working" (to the extent that the second monitor displays unique content and I can drag windows to it), windows on my second display tend to hang if I try to interact with them: Eclipse actions freeze before completed; interaction with browser controls has no effect; the mouse pointer can be hidden.  All I can seem to do is activate the window menu from the keyboard to get a handle on the window to "move" it back to the primary monitor!

I am  thinking I have to run Windows under Ubuntu so that Windows can control the displays :-O

---

### Post by nathema on 2011-05-10
> **JayBofMA said:**
> I have been struggling with a similar issue on a Dell Precision M65 with NVIDIA Quadro FX 350M.  I found the GUI editor to be inconsistent with what is updated when I "save" a change.  I have resorted to manually modifying the file.

I am just getting back into Linux after many years.  I had never used X in my Red Hat days, so I am unfamiliar with all the xorg.conf nuances.  I find it interesting that similar to what you have posted myh xorg.conf seemed to have two entries for "metamodes".  Although yours are listed for the laptop (DFP) whereas mine are listed for the CRT (aka DFP but what does X know?)  I presume that this indicates your laptop is secondary/Monitor 1?

Also, despite my having got Separate X and Xinerama "working" (to the extent that the second monitor displays unique content and I can drag windows to it), windows on my second display tend to hang if I try to interact with them: Eclipse actions freeze before completed; interaction with browser controls has no effect; the mouse pointer can be hidden.  All I can seem to do is activate the window menu from the keyboard to get a handle on the window to "move" it back to the primary monitor!

I am  thinking I have to run Windows under Ubuntu so that Windows can control the displays :-O

CRT-0 and DFP-0 are unknown to X, but known to the driver. Some lines from /var/log/Xorg.<number>.log:
```
[   588.355] (--) NVIDIA(0): Connected display device(s) on Quadro NVS 320M at PCI:1:0:0
[   588.355] (--) NVIDIA(0):     Acer AL1916W (CRT-0)
[   588.355] (--) NVIDIA(0):     LPL (DFP-0)
```
You are correct.
X itself only sees in the case of Twinview a large resolution screen on 1 device and in Xinerama 2 screens on 2 devices. 

Like you, Xinerama works only in 2D mode with me: with a unity --replace i notice the Xrandr extension warnings. Maybe unity/compiz depends on xrandr extension?
Unity / Compiz works with Twinview with one monitor enabled (progress!), tomorrow i'll test my second head.

---

### Post by nathema on 2011-05-11
Woooohoooo, it's working, dynamically and with Unity 3d!!!!!!!!!!!!

```
Section "ServerFlags"
    Option    "RandR" "on"
EndSection

Section "Device"
    Identifier     "quadra"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 320M"
    BusID          "PCI:1:0:0"
    Option       "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "screen"
    Device         "quadra"
    DefaultDepth    24
    Option         "TwinView"
    Option         "MetaModes" "DFP-0: 1680x1050, CRT-0: 1440x900 @1440x1050"
    Option       "TwinViewOrientation" "CRT-0 RightOf DFP-0"
    Option         "HorizSync"   "CRT-0: 31 - 84; DFP-0: 30 - 75"
    Option         "VertRefresh" "CRT-0: 56-76; DFP-0: 60"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Maximizing windows perfectly per monitor!!!!

To be clear: This is no problem of Ubuntu 11.04, this is no problem of Nvidia and no problem of X. Just config the xorg.conf properly!

---

### Post by mvega on 2011-05-12
Am I too lazy?

After reading about the amazing disp, I just used gnome-session-properties to add "disper -d auto -e" as an application to run whenever gnome starts and now all my problems are solved!

Please send your comments on this approach.

---

### Post by JayBofMA on 2011-05-12
> **nathema said:**
> Woooohoooo, it's working, dynamically and with Unity 3d!!!!!!!!!!!!

```
Section "ServerFlags"
    Option    "RandR" "on"
EndSection

Section "Device"
    Identifier     "quadra"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 320M"
    BusID          "PCI:1:0:0"
    Option       "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "screen"
    Device         "quadra"
    DefaultDepth    24
    Option         "TwinView"
    Option         "MetaModes" "DFP-0: 1680x1050, CRT-0: 1440x900 @1440x1050"
    Option       "TwinViewOrientation" "CRT-0 RightOf DFP-0"
    Option         "HorizSync"   "CRT-0: 31 - 84; DFP-0: 30 - 75"
    Option         "VertRefresh" "CRT-0: 56-76; DFP-0: 60"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Maximizing windows perfectly per monitor!!!!

To be clear: This is no problem of Ubuntu 11.04, this is no problem of Nvidia and no problem of X. Just config the xorg.conf properly!

I am pleased to learn of your success.  I have updated my 350M xorg.conf and your snippet is a far cry better than what I have been able to piece together.  However, my card does not seem to recognize DFP-0 as primary and/or set CRT-0 to RightOf DFP-0.  At least I have two functional displays as opposed to my efforts with Separate X and Xinerama.

Th issue that I do have though, is that the entire screen of DFP-0 cannot be accessed.  Windows cannot be moved entirely onto that display.

More work to do on my end.

---

### Post by nathema on 2011-05-12
CRT-0 and DFP-0 are valid in my case. What the device names on your system are, u can check in /var/log/Xorg.0.log. Can you maybe list the file with your second monitor attached?

---

### Post by JayBofMA on 2011-05-13
I believe my issue is solved...  I noticed a warning in the log (thanks for pointing me there) warning of compositing and xinerama.  Since this older Precision M65 laptop has trouble with Unity, I run with No Effects.  But I still like having a loader, Docky.  And Docky warns on start if Compositing is not available.  So without realizing there was an issue, I had turned compositing-manager on.  Once this was toggled off in metacity, Docky threw up the familiar Compositing warning, but X immediately started rendering the separate display correctly (even here at home with a different CRT-0 and resolution).  Thanks for the help.

---

### Post by Steck! on 2011-05-13
Quick question, I'm running a GTX295 card, which xorg recognizes as 2 seperate cards, one running each monitor. how should a second device be reflected in the config file?

---

### Post by nathema on 2011-05-13
> **Steck! said:**
> Quick question, I'm running a GTX295 card, which xorg recognizes as 2 seperate cards, one running each monitor. how should a second device be reflected in the config file?

I think close to the xorg.conf in my opening post. There i have 2 devices with each 1 monitor and screen.
With ```
lspci
``` you can see the pci locations in the case you want to specify those hardcoded.

Please list the important bits from /var/log/Xorg.0.log and /etc/X11/xorg.conf.

---

### Post by Steck! on 2011-05-13
Here's what i've got right now, I gave up on Twinview/Xinerama yesterday, this is just with both monitors running seperate Xscreens

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ProView/EMC/PTS MLT3221"
    HorizSync       31.0 - 70.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 295"
    BusID          "PCI:7:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 295"
    BusID          "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "960x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by nathema on 2011-05-13
> **Steck! said:**
> Here's what i've got right now, I gave up on Twinview/Xinerama yesterday, this is just with both monitors running seperate Xscreens

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ProView/EMC/PTS MLT3221"
    HorizSync       31.0 - 70.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 295"
    BusID          "PCI:7:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 295"
    BusID          "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "960x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

The second device looks setup properly. But because you run a 2nd XServer you can't drag and drop windows/stuff between the 2 screens.
I would remove all the inputDevice lines/sections. X is setup to insert those dynamically.

---

### Post by Steck! on 2011-05-13
Yeah, it's working relatively well as is, (a bit of silliness with windows acting up in the second screen, but that's apparantly an actual bug).

I was asking how to enable Twinview using a second card. Something like this?

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

Section "ServerFlags"
    Option    "RandR" "on"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ProView/EMC/PTS MLT3221"
    HorizSync       31.0 - 70.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
    Option         "FlatPanelProperties" "native"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 295"
    BusID          "PCI:7:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 295"
    BusID          "PCI:6:0:0"
EndSection

Section "Screen"
    Identifier     "screen"
    Device         "Device0; Device1"
    DefaultDepth    24
    Option         "TwinView"
    Option         "MetaModes" "Monitor0: 960x720 @960x768, Monitor1: 1024x768"
    Option         "TwinViewOrientation" "Monitor1 RightOf Monitor0"
    Option         "HorizSync"   "Monitor0: 30.0 - 81.0; Monitor1: 31.0 - 70.0"
    Option         "VertRefresh" "Monitor0: 56.0 - 75.0; Monitor1: 56.0 - 85.0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by mvega on 2011-05-24
You may also consider combine the following:

1- Propietary NVIDIA drivers (nvidia-current)
2- A on-the-fly display switch utility like Disper. Add disper repository and install it by typing:
```
    sudo add-apt-repository ppa:disper-dev/ppa && sudo apt-get update
    sudo apt-get install disper
```3- Install a disper indicator (use Alexander Egger's python indicator found in [http://eggeral.blogspot.com/2011/04/disper-indicator-for-switching-nvidia.html](http://eggeral.blogspot.com/2011/04/disper-indicator-for-switching-nvidia.html)

Use the new indicator to select displays operation mode as needed.

---

