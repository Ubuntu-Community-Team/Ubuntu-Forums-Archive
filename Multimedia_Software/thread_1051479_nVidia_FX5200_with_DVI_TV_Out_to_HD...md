---
title: "nVidia FX5200 with DVI TV Out to HD..?"
date: 2009-01-26
forum: Multimedia Software
---

### Post by digitalis_46613 on 2009-01-26
I have seen many people ask questions, and get no responses.  I guess this is my turn now.  I have a dual-head video card, and I would LIKE to run Multiterminal with my wireless keyboard/mouse on the HDTV.  I think i might have the basics down for xorg, but I'm not entirely sure.  I found tutorials online but they are all for older systems.  Would someone be able to help me achieve this?
Also why does the nvidia-settings program allow a separate X session if there is no support for it?
All I want to do is watch videos on the TV and be able to use the mouse/keyboard.  I'd settle for a Clone view, like windows would do, but I dont see that option.
Help!!

---

### Post by smo0th on 2009-01-26
hi,

I also have a 5200 card and configured it with dual output, actually having separate sessions works better, I have all compiz fusion effects in my monitor and I keep the TV's session plain just to see the videos, it works sweet in both sessions.

so... howto do it!!... well there's a GUI we have to install as follows:

```
sudo apt-get install nvidia-settings
```
Then it's installed, run it going to System>Administration>Nvidia X Server Settings OR using:
```
sudo nvidia-settings
```

Go to X Server Display Configuration and set your monitors there.

Hope this helps, if not please post back I'll be tracking this =)

---

### Post by digitalis_46613 on 2009-01-27
been there.. installed that.  I have two separate X sessions.  How do i use the 'other' session?

---

### Post by smo0th on 2009-01-27
You use the 'other' session just by dragging your mouse pointer in and using it as normal... does your 'other' session work good? do you see a black screen or something? you need to configure the right resolution for your HDTV, normally 1920x1080 or 1280x768 work fine.

---

### Post by digitalis_46613 on 2009-01-27
when i open a window on the TV with the mouse, it opens on the PC instead, and nothing on the TV.  
How do i get two separate sessions with separate keyboard/mouse control?

---

### Post by smo0th on 2009-01-27
hooo! now I get it, I've never seen that before, can you post your /etc/X11/xorg.conf here?

---

### Post by digitalis_46613 on 2009-01-28
Sure.  I've read something about using the ServerLayout area to identify  keyboard "wireless" and mouse "wireless" and such.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection 

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "hp f1523"
    HorizSync       30.0 - 61.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       26.0 - 68.0
    VertRefresh     23.0 - 61.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
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

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


from what I read, I should be able do to something like this:
```
Section "ServerLayout"
        # The Identifier value will be used in the command-line call.
        Identifier      "Layout0"
        Screen          "Default Screen 0"
        InputDevice     "USB Keyboard"
        InputDevice     "Generic Mouse"

        Option          "SingleCard"
EndSection

Section "ServerLayout"
        # The Identifier value will be used in the command-line call.
        Identifier      "Layout1"
        Screen          "Default Screen 1"
        InputDevice     "Wireless Keyboard"
        InputDevice     "Wireless Mouse"

        Option          "SingleCard"
EndSection


Section "InputDevice"
        Identifier      "Wireless Keyboard"
        Driver          "kbd"

        # Change the value of the "Dev Phys" option to the physical
        # address of the corresponding keyboard, found in the file
        # /proc/bus/input/devices .
        Option          "Protocol"      "evdev"
        Option          "Dev Phys"      "usb-0000:00:09.1-2/input0"

        # Configure your keyboard as usual
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "CoreKeyboard"
EndSection

Section "InputDevice"
        Identifier      "USB Keyboard"
        Driver          "kbd"

        # Change the value of the "Dev Phys" option to the physical
        # address of the corresponding keyboard, found in the file
        # /proc/bus/input/devices .
        Option          "Protocol"      "evdev"
        Option          "Dev Phys"      "usb-0000:00:10.0-2/input0"

        # Configure your keyboard as usual
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "CoreKeyboard"
EndSection


Section "InputDevice"
        Identifier      "Wireless Mouse"
        Driver          "mouse"

        # Change the value of the "Dev Phys" option to the physical
        # address of the corresponding mouse, found in the file
        # /proc/bus/input/devices .
        Option          "Protocol"      "evdev"
        Option          "Dev Phys"      "usb-0000:00:09.1-2/input1"

        # All mice should have "CorePointer"
        Option          "CorePointer"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

I'm not quite sure how to use it yet though.  I did get it going last night enough with wireless to use the TV to watch a movie.  I just don't have independent control.

---

### Post by smo0th on 2009-01-28
right, you have some missing parameters in your xorg.conf, here's mine so you can compare them:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Feb 14 18:13:41 PST 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Thu Jun  5 09:27:12 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "Mitsubishi NSB1107U"
    HorizSync       30.0 - 121.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SHARP LCD"
    HorizSync       31.0 - 75.0
    VertRefresh     55.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: 1280x1024_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-0: 1280x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

that's for your reference just in case you want to compare them.

You may try ```
sudo nvidia-xconfig
``` and if that doesn't help you try ```
sudo dpkg-reconfigure xserver-xorg
``` as the command says, these should allow you to reconfigure your xserver so it works good with your input devices.

Hope it works, please post back your results =)

---

### Post by digitalis_46613 on 2009-01-29
that pretty much defaulted my conf file.. i restored the backup.  I need to see a proper file of declaring keyboard and mouse devices, as mine are default, and not physicaly declared.  then i need to compare to the ServerLayout and add that.

---

### Post by smo0th on 2009-01-29
well, my configuration file works good so you may take that as an example on how to properly declare parameters, however I don't have wireless mouse/keyboard, I don't know if wireless devices need to be declared different. Just try to merge your config file with mine using your devices and it should work, oh yeah and don't forget to restart the xserver using ctrl+alt+backspace so the changes you made to the xorg.conf file take effect, this however will close all running programs so make sure to save everything before proceeding.

---

### Post by digitalis_46613 on 2009-01-30
You don't have two keyboards, do you?  I am looking at that and only see one keyboard configured.  I read somewhere that the kernel can't route data from both keyboards without intervention from another module.  I've seen references to Xephyr, and other programs.  I found a site that describes it, i think, but reading through it, I don't want to start, and get stuck in the middle....
[http://netpatia.blogspot.com/2008/02/multiseat-on-ubuntu-804-ii.html](http://netpatia.blogspot.com/2008/02/multiseat-on-ubuntu-804-ii.html)
plus, this is for 8.04 and I have 8.10.  some people have claimed their setup worked on 8.04 but not on 8.10.

---

### Post by smo0th on 2009-01-30
right I only have 1 keyboard and 1 mouse, sorry this is as far as I go.

---

