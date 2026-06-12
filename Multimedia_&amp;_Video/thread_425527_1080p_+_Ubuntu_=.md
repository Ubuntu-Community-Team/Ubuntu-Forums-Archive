---
title: "1080p + Ubuntu = ?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Filleokus on 2007-04-27
Hello folks!

We have bought ourself a new DTL-642E500. Since the tv has 1080p features i felt that i needed something to play this that on, so i bought a htpc. The htpc is a pretty powerful machine with a 4600+ and a 7300GT as the main hardware.

And now over to the problems. I cant get ubuntu to give me any decent resolutions, only up to like 1024x768.. Second the picture is not fitting on the screen, it is like an inch to big or something like that.
So what should i do to make this work?

Forgot to say that i use a dvi-hdmi adaptrer and not the vga port.

---

### Post by disturbedite on 2007-04-27
your xorg.conf is most likely your problem.  it doesn't always detect the right resolutions/frequencies.  (assuming you have the right monitor/video card selected and the right driver(s) installed) you have to edit your xorg.conf to get the correct ones.

its more complicated than i made it sound tho, look around the forum and net for instructions if you're not familiar with xorg.conf.

---

### Post by Filleokus on 2007-04-28
Thanks for the answer!

Well, i have edited the xorg.conf file with proper resolution and the right SyncFreq more then once. And still the screen resolution app seems to override it?

I will try again with a new fresh ubuntu install.

---

### Post by Filleokus on 2007-04-28
Okey now i got a a fresh ubuntu 7.04 install with nvidia drivers from automatix. No overscanning, but the resolution is only 800x600.

I'll know try to read some guide or something to get up to 1920x1080 and no overscanning.

EDIT:
So now i've edited xorg.conf so that every resolution except the 1920x1080 24 bits is comment out. But i does not want to work. I only get 720p out of the card. And in 720p its some serious overscanning.
I've tried to open the nvidia panel and mess around there. One problem is that in the "Flat panel information" it says that the hdtv's nativ resolution is 1280x720. And i've tried all combantions of the scaling methods on the left.
I think that i read somewhere that nvidia was a bit sensetive for high resolutions and 24 bits colour depth. I'm sure this will work, i only have to poke around in some config files.

EDIT #2:

Ive followed [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) tried every tip there but i only get 720p. Ive checked the log files and it says "(II) NV(0): Not using mode "1920x1080" (exceeds panel dimensions)" even tough it is a 1080p panel.

So now i am focusing to get the whole picture on the screen. I dont have any 1080p mateial after all so 720p is good for now.

---

### Post by Filleokus on 2007-04-28
awh, now i have tried all the tricks in the book, what should i do?
No one that has got this working?

---

### Post by sammao on 2007-04-29
I have the same problem. Ive installed Envy for my drivers. I had high hopes on Envy solving it but not. It works fine on my other LCD monitor a real computer one.. 
I to have tried every thing I found edit my xorg.conf file like crazy but no change except for some times to edit back since hook ups.. 
Right now It looks like this and no progress..

 Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEX T4211N"
    HorizSync       15.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
    Modeline "1920x1080@50" 143.55 1920 1952 2496 2528 1080 1103 1112 1135
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5600 Ultra"
    Option         "ModeValidation" "NoMaxPClkCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080@50"
    EndSubSection
EndSection

:confused:

---

### Post by sammao on 2007-04-29
[http://psubuntu.com/forum/viewtopic.php?t=13](http://psubuntu.com/forum/viewtopic.php?t=13)

Hi i found somthing that works for ps3 with ubuntu.. mayby ill try.. ehm kboot.conf cant find it.
kubuntu? but how do I do the same for ubuntu?

---

### Post by sammao on 2007-04-30
I still have the same LCD as you the Mirai one. And now i have manage to get 1360x768 res. Via DVI-HDMI adaptor. Im longing for 1920x1080p but this is a progress.. I CAN SEE THE FULL DESKTOP ;-) Im beginning to think that edid is reporting the VGA res so next is to try some off the modevalidation stuff found here: [http://www.mythtv.org/wiki/index.php/Modeline_Database#NVIDIA_Driver_ModePool](http://www.mythtv.org/wiki/index.php/Modeline_Database#NVIDIA_Driver_ModePool)
(look further down on that page)

This Is my xorg.conf se below. The only problem is that the nvidia-settings takes the rows away if I whant to use that tool and save to xorg.conf.. I do not now wich of the ModeValidation rows that does it, added all.. Had almost given up..

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:39:38 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEX T4211N"
    HorizSync       15.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5600 Ultra"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdidFreqs" "false"
    Option         "ModeValidation" "NoEdidDFPMaxSizeCheck"
    Option         "ModeValidation" "NoMaxPClkCheck"
    Option         "ModeValidation" "NoDFPNativeResolutionCheck"
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080_60"
    EndSubSection
EndSection

---

### Post by sammao on 2007-04-30
I now have the native res 1920x1080p with these lines.

 Option         "UseEdidFreqs" "false"
Option  "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVesaModes, NoXServerModes, NoPredefinedModes"

But humm just flickers..

---

### Post by sammao on 2007-04-30
HEHE
NOW IT WORKS!
HAVE Envy installed and added this to my xorg.conf

  Option         "UseEdidFreqs" "false"
Option  "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVesaModes, NoXServerModes, NoPredefinedModes"


BUT i have to Force GPU Scaling and use high digital vibrance... wonder.. any one with some tips.

DVI-HDMI

---

### Post by maww on 2007-05-02
Hello, 

Thanks to sammao I got my Samsung Syncmaster 225BW and my Mirai DTL-642E500 working as I want. I'm running my Samsung on 1680x1050 and my LCD Mirai on 1080P. 

I just want to post my xorg.conf here so that if there are other users who have the same problem I had. 

Took awhile but I learned alot about xorg.conf... :popcorn:

---

