---
title: "NVIDIA settings stopped detecting TV"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Sylos on 2009-12-30
Hello all,
For the last year or so I have been happily using my Hardy Heron and Geforce FX5200 graphics card to display onto my TV as well as the monitor (mainly for watchin films etc). Today I go to watch something and the TV display wont work. All connections are good and I have tested the card in windows and it displays to the TV fine. 
Using the Nvidia-settings tool I try to set it up again but when i press ¨detect displays¨ nothing happens. Under ubuntu the Nvidia tool wont detect the TV.
I have tried reinstalling the nvidia-glx-new package and tried using the older nvidia-glx package from synaptic but with no progress. It still wont detect the TV. Below is my xorg.conf file 


[PHP]Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NUL"
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
EndSection
[/PHP]

I should also add that there is no display going to the TV during the splash/login sequence.

---

### Post by Sylos on 2010-01-02
An update on this.
Since I couldnt find any solutions to this on the net I decided to bite the bullet and upgrade from Hardy to 9.10 assuming that whatever setting was messed up would be wiped and sorted out. 
It turns out that is not the case. Having installed the restricted drivers I still cant get the NVIDIA settings tool to detect the TV.
If any one out there has had any similar issues please throw me a bone cos I am stumped.
Thanks,

---

### Post by anksush on 2010-01-02
Hey Sylos...

You are not alone..I have been facing the same problem....but I had all going fine with 9.04 and then after the update to 9.10 it just wont detect...if I restart in windows it does but otherwise it wont....

Unfortunately no solution ...If I get something to work, I will post here, plz do let me know if something works for u...

---

### Post by Sylos on 2010-01-03
Hi there and cheers for the post.
I am getting somewhere with this but not yet working as I want.
Not sure what level of skill you have with Ubuntu (mine is pretty low) but so far I have discovered that you can force Nvidia to use the TV out by modifying the Xorg.conf file with the following line under the "Device" section:

Options     "ConnectedMonitor" "TV"

The only problem is this only uses the TV and requires X to be restarted with the new config file every time you want to see something through the TV. What makes it worse is that my TV is old with bad definition so I can watch video on it but reading anything in dialogue boxes is pretty impossible.

If any knows of a way I can force the card to use the TV and the CRT monitor option as clones that would be great.

Im gonna carry on the quest. Here is a link to some good info on how to alter the xorg.conf file:

[http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-9626/README/appendix-g.html](http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-9626/README/appendix-g.html)

Good luck.

---

### Post by Sylos on 2010-01-03
Hello again. I have (miraculously) got this working.
Im not sure exactly how but having modified some lines in xorg.conf I tried using the Nvidia-settings tool again. This time the option for the twin view was live (probabbly because I manually added the option). I managed to select it and set it as a clone. I then saved the settings to the config file and restarted. Hey presto - It works. Below is a copy of my now working xorg.config.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NUL"
    HorizSync       31.0 - 60.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    Option         "ConnectedMonitor" "CRT, TV"
    Option         "TVStandard" "PAL-I"
    Option         "TVOutFormat" "SVIDEO"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinViewOrientation" "Clone"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768 +0+0, TV: nvidia-auto-select +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

If you need any other info then I'll do my best to help you out with it.
Good Luck.

---

### Post by anksush on 2010-03-19
The problem is with the latest Nvidia driver, the one that ubuntu says recommended. In order to make your TV Out work, you must uninstall the latest release version and install the one just lower than that. (The working version for me was 173.) Then follow these steps:

sudo nvidia-xconfig

sudo reboot

sudo nvidia-settings

Detailed steps then on:

[http://makegadgetswork.blogspot.com/2009/09/sony-vaio-n-vidia-setup-to-make-s-video.html]("http://makegadgetswork.blogspot.com/2009/09/sony-vaio-n-vidia-setup-to-make-s-video.html")

---

