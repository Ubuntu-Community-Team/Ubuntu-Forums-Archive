---
title: "Can nv-legacy w working tv-out be calibrated for mediacenter?"
date: 2008-07-03
forum: Multimedia Software
---

### Post by Redsandro on 2008-07-03
Hi,

I revived an older **P3 800MHz** with **512MB RAM** using **Xubuntu 8.04** and it runs really aresome. The idea was to make a headless media center for the television (with fileserver).

It has a **nVidia geForce2 MX 200** (or 100) with 32MB RAM, which has *composite* and *s-video* out. The new automatically installed *nvidia-glx* driver broke the resolution to a maximum of 640x480. I read people were saved with **Envy** so I installed that, making my video look like a 386. Uninstall, installed *nvidia-glx-legacy* instead. The *glx extension* didn't work according to *glxgears* untill I disabled composite in *xorg.conf*:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection
```
Now I can play oldskool 3d games as an indicator that I got the driver running correctly. However, with the legacy, *nvidia-settings* is not working. I found an old version on the web which worked, but didn't give me TwinView options.

I used *xorg.conf* from my 'new' computer [SIZE="1"](in which I used nvidia-settings to create the basis for it's xorg.conf)[/SIZE] as a reference. It has an **nVidia FX5200**. I know this is old, but at least it uses *glx-new* so it's new for me ;). So I changed all values to proper ones for the P3 machine, and all was well. Except for *tv-out*, it just wouldn't work.

For two days I messed with it, gave up, removed all the *TwinView* options and *metamodes*, and *then* suddenly I *could* get an image on tv by using any of the modes presented by **xrandr** except 0. 

Mode 0 was *1024x768*, my main monitor, and the highest resolution even though I added modes and metamodes for *1280x1024* as well. The rest was tv-only modes from *800x600* all the way to *320x240* (disabling the monitor). This would be acceptable because this would be a headless machine anyway, but the offset from the upperleft corner on tv was like three inches or so; unacceptable. Besides, the picture was very flat, low contrast.

I found out about a tool called **nvtv**. Long story short, only one mode *768x576* would give an acceptable underscan (negative overscan). But with **nvtv**, your desktop is still the original size [SIZE="1"](1024x768in my case)[/SIZE] so only part of my movies [SIZE="1"](or exellent mediacenter software called xbmc)[/SIZE] was on television. **Nvtv** is cooler than the **xrandr** modes because it does give a high contrast cool picture in stead of the dull one. This would work if I could show my desktop in 768x576 as well [SIZE="1"](correct full screen)[/SIZE], but the desktop will only show in *1024x768*. Than if I **xrandr**'ed to mode 1 (*800x600* on tv) I found that the desktop maintained that size for **nvtv** so I was a bit closer to *768x576*. But wherever I put that number in *xorg.conf*, it won't show up in **xrandr**.

Long story short, now I have 2 methods of enabling tv, both throwing the picture at the cathode ray tube like a drunk darter.

I would really like to just get a good picture on my television, one way or the other. I do have some signals where I want them to come out of the computer, but they are off and it feels like I am so close. I tried a lot and I am out of ideas. Who can help me?

---

### Post by Redsandro on 2008-07-04
After trying so much that I cannot order food anymore without requesting twinview, I got *xorg.conf* working the way I want to! The picture is good quality, though still not centered. If you know a fix, let me know.

During the xfce4 loading screen, both monitor and tv flicker like crazy, constant flickering with very slow drawing. The loading takes about 10 times as long. After that, most things are normal. [SIZE="1"](I don't mean the normal tv interlace flicker for which there's an option)[/SIZE].

I can disable the loading screen, than it just loads fast. But I don't want to show the building of the screen on my tv, just a nice image. And I cannot stand the fact that something's wrong.

Anyway, here's my xorg.conf. also for search purposes. 

Sentance for people using the search:
This xorg.conf uses twinview for a tv-out desktop clone for nvidia-glx-legacy drivers with an nvidia geforce2 mx100, mx200 or mx400:
```
# xorg.conf (X.Org X Window System server configuration file)
# Custom samengesteld door Sander 2008-07-03
# Als je met andere tooltjes deze config aanpast kloppen sommige shitjes niet meer



#
# Monitors
#

Section "Monitor"
    Identifier     "Monitor_VGA"
    VendorName     "Philips"
    ModelName      "Philips 107B(17inch/CM6800)"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 130.0
EndSection

Section "Monitor"
    Identifier     "TV_SVIDEO"
    VendorName     "Blaupunkt"
    ModelName      "Nageaapt van Grundig TV"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection



#
# Video kaarten
#

Section "Device"
        Identifier      "Video_MX200"
        Driver          "nvidia"
        VendorName      "nVidia Corp"
        BoardName       "nVidia Geforce2 MX200 (legacy)"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "AddARGBVisuals" "True"
        Screen          0 # deprecated?
EndSection



#
# Screens - verbindingen
#

Section "Screen"
# Monitor met TV Clone
        Identifier     "Screen_Both"
        Device         "Video_MX200"
        Monitor        "Monitor_VGA"
        DefaultDepth    24

        Option          "TwinView" "1"
        Option          "metamodes" "CRT: 1024x768 +0+0, TV: 800x600@1024x768; CRT: 800x600 +0+0, TV: 800x600 +0+0; CRT: 1280x1024 +0+0, TV: NULL; CRT: 1152x864 +0+0, TV: NULL;"
        Option          "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
        Option          "TVStandard" "PAL-B"
        Option          "RenderAccel" "On"
        Option          "HWcursor" "On"
        Option          "DamageEvents" "True"
        Option          "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth 24
                Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection





#
# Server Layouts - Resoluties beschikbaar voor Xserver
#

Section "ServerLayout"
    Identifier     "PrimaryLayout"
    Screen      0  "Screen_Both" 0 0
    InputDevice    "myKeyboard" "CoreKeyboard"
    InputDevice    "myMouse" "CorePointer"
EndSection






#
# Input devices
#

Section "InputDevice"
        Identifier      "myKeyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "myMouse"
    Driver         "mouse"
        Option          "CorePointer"
EndSection






#
# Overige ****
#

Section "Files"
EndSection

Section "Module"
        # gEJATTE gokjes
        Load "dbe"
        Load "extmod"
        Load "type1"
        Load "freetype"
    Load           "glx"
    Load           "v4l"
EndSection

# Anders doet glx het niet met legacy
Section "Extensions"
        Option "Composite" "Disable"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option         "TwinView" "1"
EndSection

```

Finally, when I disconnect my monitor (since this is a headless mediacenter for tv) and I boot, everything screws up and nvidia-glx-failsafe is loaded. [SIZE="3"]Is there a way of fooling X into thinking the monitor is attached?[/SIZE] Or pherhaps another option?

---

