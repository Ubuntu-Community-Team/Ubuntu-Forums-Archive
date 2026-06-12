---
title: "Intel i965 3D driver, lcd high resolution and multimedia codecs problem"
date: 2006-11-20
forum: Multimedia &amp; Video
---

### Post by sir_skiner on 2006-11-20
Hi all!
First of all - I installed Ubuntu 6.10 couple days ago. Allthoght it's not my first time to linux I feel like a newbie, 'cause it's been a while since my last time using it. I'm charmed by Ubuntu but have some problems.

1. I cant properly configure my video controler. It's integrated GMA X3000; i965 on GA-965GM-S2. It works fine, except two things:
a) I dont know how to get 3d up and running. "i810" driver delivers 2d only. I  know that intel developed 3d drivers. I even d-loaded them from freedesktop git and cvs, but what next? I would like some step by step howto.
b) Second thing is that the display area on my lcd is shifted so I get striped slice of screen on left side, and black (empty) slice on right. It happens only in 1280x1024 res. Others work just fine.

2. I installed multimedia codecs as shown in unoficial starter guide, but stil can't force totem and mplayer to open some avi's (some do, some don't). What should I do?

Please, help

---

### Post by sir_skiner on 2006-11-21
BUMP

any ideas?

---

### Post by trubblemaker on 2006-11-21
well i810 does have 3d graphics, as I run them. didn't do anything fancy just upgraded to edgy and followed a howto for getting beryl working.

as for codecs: can you watch video's that you launch from commandline? 
```
 mplayer /path/to/movie.avi 
```

---

### Post by sir_skiner on 2006-11-22
> **trubblemaker said:**
> well i810 does have 3d graphics, as I run them. didn't do anything fancy just upgraded to edgy and followed a howto for getting beryl working.

well, not really for me. beryl crashes my xorg. glxinfo | grep direct` gives:
```
libGL warning: 3D driver claims to not support visual 0x5a
DRM_I830_CMDBUFFER: -22

```

```
as for codecs: can you watch video's that you launch from commandline? 
[code] mplayer /path/to/movie.avi 
```
[/CODE]
as for codecs... think we can live that. I gues I was missing some files now I don't. however is there a working quicktime firefox plugin?

---

### Post by trubblemaker on 2006-11-22
>  as for codecs... think we can live that. I gues I was missing some files now I don't. however is there a working quicktime firefox plugin?

not sure what you mean.  On my machine commandline works but Gui doesn't to play files, wondering if it was the same for you.

try adding this to /etc/X11/xorg.conf 

```
Section "Extensions"
        Option "Composite" "true"
EndSection

```
I can't remember spefically what it does but it has to do with rendering of 3d, and it necessary for xgl.

Hope this helps

---

### Post by sir_skiner on 2006-11-22
> **trubblemaker said:**
> 

try adding this to /etc/X11/xorg.conf 

```
Section "Extensions"
        Option "Composite" "true"
EndSection

```
I can't remember spefically what it does but it has to do with rendering of 3d, and it necessary for xgl.

Hope this helps
sorry, it wont... 
3D is just  not working. do you have G965 like mine?

---

### Post by trubblemaker on 2006-11-22
Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

my xorg.conf 

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
        Option "XAANoOffscreenPixmaps" "true"
        Option          "TripleBuffer" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "true"
EndSection

```

if you geel like reconfiguring your xorg.conf  here;s a command for you to try:

```
sudo dpkg-reconfigure xserver-xorg
```

try out the i810 driver, 

Another option 
```
lspci | grep Intel
```
pickout what looks like your graphics card, copy & paste into google, and you'll get posts about your card.  ( remove the id on the from of the link look like: 00:1e.0)

---

### Post by sir_skiner on 2006-11-25
I found something about bad mesa compile options and 2.6.17 kernel... where can I report it to the ubuntu devs, and are there any ways to get a new kernel without compiling?

---

### Post by trubblemaker on 2006-11-25
well don't think your at the launchpad bug report stage.

first you I haven't looked into it but I don't think you shouldn't be using the mesa driver you should try the intel ones.

second 3d works for the intel drivers, checkout the forums for your card and see if others have the same issue, your bug won't get confirmed (and worked on) unless you can have several other people report, or you have detailed debugging output.

and unfortunately no there isn't another way to get a new kernel without compiling. (slight lie there are some packages but they compile for you) 

you could might be able to try a 686 kernel, by deb install but to be honest I don't think your issue lies in that path.

---

