---
title: "Getting Dual Monitor support working in Unity with NVIDIA"
date: 2011-06-21
forum: Multimedia Software
---

### Post by void.pointer on 2011-06-21
Hi,

I have an NVIDIA 9800 GTX. I have 2 DELL monitors connect to this card, one is a 24" and the other is 21".

I am unable to use Xinerama mode with Unity, because for some reason after logging in, I get no desktop interface, only background wallpaper, and I have to force reboot.

How can I setup dual monitors in Ubuntu using Unity properly? Note that I do NOT want to use TwinView, since this results in dead space around the smaller monitor.

Thanks. If you need more information please let me know.

---

### Post by 23dornot23d on 2011-06-21
If you could just let us know that the Nvidia driver is installed and working first of all

Check 

Nvidia-Settings .... and see what information it gives you back as regards the driver you are currently using ...

This is my set up - done initially through adding additional hardware drivers.

___________________________________________________

This is mine and the information that mine shows ..... 

It may be useful to others if you can add screenshots similar to this ...... or the driver you are currently using ....

I am using xorg-edgers latest display driver though .... so yours may be different .....

[IMG]http://img843.imageshack.us/img843/6151/screenshot19oh.jpg[/IMG]



[IMG]http://img651.imageshack.us/img651/3870/screenshot18or.jpg[/IMG]


I realise that you want to use xinerama .... so all I will do is show you what information may be useful to others to solve the problem 

( as screen resolutions and your current drivers will be important here ).

---

### Post by BicyclerBoy on 2011-06-21
AFAICT Xinerama does not work properly & it has been forgotten.

There is a big change coming to Xorg & its possible replacement so there will not be any effort wasted on xinerama.

So you have Twinview (supported works well) or separate X screens (works well).

Separate X screens allows full video & openGL performance, independent video modes.
But it does NOT allow dragging between screens, no icons/launches on 2nd screen.
You can force apps to launch on either with export DISPLAY:=0.1 && app

I'm not planning to use 11.04 unity with 2 monitors any time soon..

So you need (2) monitors with the same native resolution..then twinview should work fine.

---

### Post by 23dornot23d on 2011-06-21
I just had another quick look around too ..... good thread to look at for making decisions
its old but shows a poll of the usage and a lot of results from USERS too .....

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

link from that to *[Xinerama information]("http://ubuntuforums.org/showthread.php?p=1773624")*

A possible future .....
Plus what the Wayland Architecture is set up .... if this is the future .....

[http://wayland.freedesktop.org/architecture.html](http://wayland.freedesktop.org/architecture.html)

____________________________________________

Not sure if this is the way that UBUNTU is going for future releases though ... or how
long it will take to implement if they do ....... :confused:

Some more recent [interesting Information - the future is explained down at the bottom of this article]("http://nouveau.freedesktop.org/wiki/MultiMonitorDesktop")

[clutter ]("http://www.chaosreigns.com/wayland/background/")
**[wayland]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29")** 

>  Quote taken from above article and link ...
**Development**

 [Canonical Ltd.]("http://en.wikipedia.org/wiki/Canonical_Ltd."), owner of Ubuntu, hired Sam Spilsbury,[[27]]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-26") primary [Compiz]("http://en.wikipedia.org/wiki/Compiz")  developer. He has been moving Compiz dependencies on X into a plugin.  This will make it easier to enable Compiz to become a Wayland display  server.[[28]]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-27") Canonical is planning to help port Compiz to OpenGL ES, currently a requirement for Wayland display servers.[[29]]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-28")
 [KWin]("http://en.wikipedia.org/wiki/KWin"), the KDE window manager, added support for OpenGL ES output.[[30]]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-29") It will ship with [KDE SC 4.7]("http://en.wikipedia.org/wiki/KDE_Software_Compilation_4"). [[31]]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-30") So far [KWin]("http://en.wikipedia.org/wiki/KWin") has recieved it's initial port to Wayland.[[32]]("http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29#cite_note-31")

Kristian Hogsberg
[http://hoegsberg.blogspot.com/](http://hoegsberg.blogspot.com/)

---

### Post by void.pointer on 2011-06-21
So when is this big change to Xorg supposed to come? I don't really know what Xorg is, but if it gives me better options than TwinView on Unity that's great.

---

### Post by 23dornot23d on 2011-06-21
Well the next release is in October .... we wait and see ....

or we join the development team and do some testing ..... always got its ups and downs
but it does keep us in touch with some of the new changes ....

Search on ***[Oneiric .... but its 11.10 and as I say the development version]("http://ubuntuforums.org/forumdisplay.php?f=403")***.

---

### Post by phalantice on 2011-07-21
I finally got a dualhead setup going.  not seprate or twin. xinerama is turned on in the config though..    2 1440x900 pannels 1 normal the other verticle.  it took a little putzing around to get it to work.   when I upgraded to 11 it worked for a bit but I now get issues with opengl turned on in compiz.  If I turn compiz off screens back to 10.4 quality. My left screen is normal for video and regular usage.  and when I need to read an article etc it goes to the right screen which is set like a leagel sheet.  


```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Asus"
    ModelName      "ACI ASUS VW193T"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Viewsonic"
    ModelName      "ViewSonic VA1912wSERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
    # HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    Option         "rotate" "ccw"
    Option         "RandRRotation" "on"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

```and the server code

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
    Option         "Composite" "Enable"
    Option         "RANDR" "Enable"
    # Removed Option "Xinerama" "0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GS"
    BusID          "PCI:7:0:0"
    Screen          0
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GS"
    BusID          "PCI:7:0:0"
    Screen          1
    Option    "NoLogo"    "True"
    #Driver    "nouveau"
EndSection
```

---

### Post by BicyclerBoy on 2011-07-21
From the 275 driver readme..

> 
**Chapter 17. Using the XRandR Extension**

Workstation RGB or CI overlay visuals will function at lower performance and the video overlay will not be available when RandRRotation is enabled.

TwinView and rotation can be used together, but rotation affects the entire desktop.
**Chapter 23. Using the X Composite Extension**

The Composite extension is currently incompatible with Xinerama, due to limitations in the X.Org X server. Composite will be automatically disabled when Xinerama is enabled.


So no composite effects with xinerama..
To have independent rotated screens (with adequate performance), you have to use separate X screens.

---

