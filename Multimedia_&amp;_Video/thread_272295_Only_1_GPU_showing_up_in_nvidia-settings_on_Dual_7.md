---
title: "Only 1 GPU showing up in nvidia-settings on Dual 7800"
date: 2006-10-06
forum: Multimedia &amp; Video
---

### Post by eflux on 2006-10-06
I'm using Ubuntu 64bit dapper and I'm having trouble trying to get SLI to work.  I have dual 7800GT cards and I have installed the latest NVIDIA driver as per Method #1 (online).  

I can open up the nvidia settings and see the settings for gpu 0.0 but that's it.  When I go to the temperature settings, I only see temp for 1 GPU.  

Is there a way to get both GPU's working in SLI mode?  I have an ASUS a8n32 SLI motherboard running AMD 3800+ X2 64.

I have also ran nvidia-settings -q all and it only shows 1 GPU being reported.

The following command does return 2 results: 

lspci -n | grep 0300
------------
0000:03:00.0 0300: 10de:0092 (rev a1)
0000:06:00.0 0300: 10de:0092 (rev a1)
------------

It returns 2 identical results.  Does that mean that both GPU's are recognized but just not utilized by the driver yet?  

Any help is greatly appreciated!

Thanks,

eflux

---

### Post by Ferrat on 2006-10-06
```

lspci -n | grep 0300
------------
0000:[COLOR="Red"]03[/COLOR]:00.0 0300: 10de:0092 (rev a1)
0000:[COLOR="Red"]06[/COLOR]:00.0 0300: 10de:0092 (rev a1)
------------

```

They ain't identical but they register as two components that share the same ID, my guess would be that it's correct, my guess would be check at nVIDIAs support ect about setting up SLI in linux, if the driver even supports it

---

### Post by tseliot on 2006-10-06
Try enabling SLI:
```
sudo nvidia-xconfig --sli=Auto
```

then log out and press CTRL+ALT+Backspace and log in

---

### Post by eflux on 2006-10-06
First off... I have no idea how you deal with all these answers everyday...very impressive!

I ran the code you suggested:

sudo nvidia-xconfig --sli=Auto

and it wrote a new xorg.conf file, however when I bring up Nvidia-settings it still only shows 1 GPU

When i run the command: nvidia-settings -q all

I still only get back info from 1 graphics card.

I did notice that in my xorg.conf file, I now have an Option under SCREEN for SLI=auto.  I tried setting it to SLI=on as well, but everytime I restart x, I can still only get infor for 1 GPU.

Am I missing something? Is there a better way to test if SLI is enabled? Do you need any other information to help me further?

Just in case, here is the content of my xorg.conf

----------------------------------
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Acer AL2416W"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Acer AL2416W"
    DefaultDepth    24
    Option         "SLI" "Auto"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
------------------------------

Any help is greatly appreciated however I'm up and running fine with 1 GPU, so if you have to skip this one, I'll understand.\\:D/

eFlux

---

### Post by BuffaloX on 2006-10-07
> **tseliot said:**
> Try enabling SLI:
```
sudo nvidia-xconfig --sli=Auto
```

then log out and press CTRL+ALT+Backspace and log in

Thanx but it didn't work for me.

I have dual 6600 GT ( SLI ), but 3d only uses one.
I conclude this from the speed meassured by glxgears, which matches speed of single card config.

It works in Windows:rolleyes: , so the hardware is ok.

---

### Post by tseliot on 2006-10-07
post the output of this command:
```
grep -i sli /var/log/Xorg.0.log
```

---

### Post by BuffaloX on 2006-10-07
> **tseliot said:**
> post the output of this command:
```
grep -i sli /var/log/Xorg.0.log
```

My result:
bill@BuffaloX:~$ grep -i sli /var/log/Xorg.0.log
(**) NVIDIA(0): Option "SLI" "Auto"
(**) NVIDIA(0): NVIDIA SLI enabled; using auto-selected rendering method.

Strange it dosn't give any speed increase in glxgears, I know glxgears isn't meant for speedtest, but it has been quite reliable in the past.
I've tested with Geforce 6800, 7600gt, ATIradeon 9800, dual 6600GT SLI, only the SLI test dosn't perform as expected.

---

### Post by eflux on 2006-10-07
Output of command:

grep -i sli /var/log/Xorg.0.log

(**) NVIDIA(0): Option "SLI" "on"
(**) NVIDIA(0): NVIDIA SLI enabled; using auto-selected rendering method.

So if I understand correctly, SLI is enabled, however the nvidia-settings just won't show both GPU's?

Thanks again!

---

### Post by tseliot on 2006-10-08
> **eflux said:**
> Output of command:

grep -i sli /var/log/Xorg.0.log

(**) NVIDIA(0): Option "SLI" "on"
(**) NVIDIA(0): NVIDIA SLI enabled; using auto-selected rendering method.

So if I understand correctly, SLI is enabled, however the nvidia-settings just won't show both GPU's?

Thanks again!
SLI is enabled. It might be a problem of nvidia-settings.

I have never tried SLI therefore I can't help you with that. I can only suggest you to ask on the unofficial nvidia forum:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by thexaspect on 2006-10-12
sorry if i'm beating a dead horse here, but I'm having a similar problem. Dual 7600GT's, and dual monitors.
using thsi command:
x@eden:~$ grep -i sli /var/log/Xorg.0.log
i end up with:
(**) NVIDIA(0): Option "SLI" "Auto"
(**) NVIDIA(0): NVIDIA SLI enabled; using auto-selected rendering method.
(WW) NVIDIA(0): TwinView and SLI are not compatibile.  Disabling TwinView.
(WW) NVIDIA(0): Failed to initialize SLI!  Reason: Only one GPU detected.

I had been working on Twinview with the assumption that SLi was already working, and apparently i jacked it up again. Any suggestions?

lspci -n | grep 0300
returns:
0000:01:00.0 0300: 10de:0391 (rev a1)

My xorg.conf is as follows, and sorry, it's terribly messy:


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon May 15 14:17:32 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

#    Identifier     "Default Layout"
    Identifier     "TwinView Configuration"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Configured Mouse"
    InputDevice    "Generic Keyboard"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    Option         "Xinerama" "Off"
#    Screen         "Default Screen" 0 0
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL 2005FPW"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA 7600 GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA 7600 GT"
    Monitor        "DELL 2005FPW"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option         "NvAGP" "2"
    Option         "NoLogo" "1"
    Option         "RenderAccel" "0"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "ConnectedMonitor" "dfp, dfp"
    Option         "NoPowerConnectorCheck"
    Option         "TwinView" "0"
    Option         "Metamodes" "1680x1050,1680x1050; 1440x900,1440x900; 1680x1050,NULL; 1440x900,NULL"
    Option         "SecondMonitorHorizSync" "31-82"
    Option         "SecondMonitorVertRefresh" "56-76"
    # Option "NoTwinViewXineramaInfo"
    Option         "SLI" "Auto"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1440x900" "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1440x900" "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1440x900" "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1440x900" "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1440x900" "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x900" "1280x800"
    EndSubSection
EndSection

Any help would be appreciated =)

---

