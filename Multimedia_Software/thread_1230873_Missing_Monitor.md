---
title: "Missing Monitor?"
date: 2009-08-03
forum: Multimedia Software
---

### Post by vaerer on 2009-08-03
I just installed Xubuntu yesterday and I've spent hours banging my head against the wall trying to get my second monitor to do anything other than play copy cat with the first.

Here's a weird screen shot of my settings pages:

[http://h.imagehost.org/0625/Screenshot.png](http://h.imagehost.org/0625/Screenshot.png)

Desktop shows that I have two "monitors" while Display only shows only one "screen". I assume screens and monitors mean the same thing?

My graphics card is a ATI Radian X300 with a VGA and a DVI output socket.

If it helps, my xorg.conf file is as follows:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "False"
EndSection
```


Very grateful if someone could shove my forcefully in the right direction :)

---

### Post by vaerer on 2009-08-06
**Update**

I looked at Big Desktop but couldn't install the drivers. It seems they don't work with the new kernel.

I tried MergedFB but couldn't get anything to happen no matter what sensible things I changed. Not even a lousy error message, it just stayed in clone mode :(

I tried Xinerama and after several edits and logging into single user mod I was able to get it to "start" without any errors. However the main monitor only had graphic gliches (that looked like dancing mexicans) and blue lines on it and the second one didn't display anything. Because there were no errors I couldn't work out what was wrong, though I did try changing several settings to no effect.

I currently have it working with separate buffers, meaning I can move the mouse across the monitors but can't move any programs. There's also a strange ghost mouse that looks weird.

I'm thinking I might either go back to windows xp or buy a new graphics card. Though I'm unsure if a new graphics card will fix the problem or not.


If someone wants to have a look at the two versions of my xorg.conf file to see if there's a solution:

```

#**Xinerama**

Section "Screen"
    Identifier    "0 Screen"
    Monitor        "0 Monitor"
    Device        "0 ATI Radeon"
#    SubSection "Display"
#         Virtual    2720 1024
#     EndSubSection
EndSection

Section "Screen"
    Identifier    "1 Screen"
    Monitor        "1 Monitor"
    Device        "1 ATI Radeon"
#    SubSection "Display"
#         Virtual    2720 1024
#     EndSubSection
EndSection

Section "Device"
    Identifier    "0 ATI Radeon"
    Driver        "ati"
    Screen        0
    Option        "DDCMode" "True"
    Option        "MonitorLayout" "TMDS,TMDS"
EndSection

Section "Device"
    Identifier    "1 ATI Radeon"
    Driver        "ati"
    Screen        1
    Option        "DDCMode" "True"
    Option        "MonitorLayout" "TMDS,TMDS"
EndSection

Section "InputDevice"
    Identifier    "Microsoft Natural Ergonomic Keyboard 4000"
    Driver        "keyboard"
    Option        "CoreKeyboard"
    Option        "XkbLayout"    "us"
    Option        "XkbVariant"    "dvp"
    Option        "XkbOptions"    "compose:102,numpad:shift3,kpdl:semi,keypad:atm,caps:shift"
EndSection

Section "InputDevice"
    Identifier    "Default Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen    "0 Screen"
    Screen    "1 Screen" RightOf "0 Screen"
    InputDevice    "Microsoft Natural Ergonomic Keyboard 4000"
    InputDevice    "Default Mouse"
    Option        "Xinerama" "true"
EndSection

Section "Monitor"
    Identifier    "0 Monitor"
EndSection

Section "Monitor"
    Identifier    "1 Monitor"
EndSection

Section "ServerFlags"
        Option        "DontZap"    "False"
EndSection

``````

#**MergedFB**

Section "Screen"
    Identifier    "0 Screen"
    Monitor        "0 Monitor"
    Device        "0 ATI Radeon"
    SubSection "Display"
        Depth 24
        Virtual 2720 1024
    EndSubSection
    SubSection "Display"
         Depth 24
         Modes "1440x900 1280x1024 1024x900"
    EndSubSection
EndSection

Section "Device"
    Identifier    "0 ATI Radeon"
    Driver        "radeon"
    Option    "MergedFB"    "true"
    Option    "MonitorLayout"    "CRT, TMDS" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
    Option    "CRT2Hsync"    "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
    Option    "CRT2VRefresh"    "50-60" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
#    Option    "OverlayOnCRTC2"    "true" # depreciated and ignored ?
    Option    "CRT2Position"    "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
    Option    "MetaModes"    "1440x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
    Option    "MergedXineramaCRT2IsScreen0"    "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
    Option    "MergedNonRectangular"    "true"
    Option    "EnablePageFlip" "false"
EndSection

Section "InputDevice"
    Identifier    "Microsoft Natural Ergonomic Keyboard 4000"
    Driver        "keyboard"
    Option        "CoreKeyboard"
    Option        "XkbLayout"    "us"
    Option        "XkbVariant"    "dvp"
    Option        "XkbOptions"    "compose:102,numpad:shift3,kpdl:semi,keypad:atm,caps:shift"
EndSection

Section "InputDevice"
    Identifier    "Default Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "0 Screen"
    InputDevice    "Microsoft Natural Ergonomic Keyboard 4000"
    InputDevice    "Default Mouse"
EndSection

Section "Monitor"
    Identifier    "0 Monitor"
    Horizsync    30-65
    Vertrefresh    50-60
EndSection

Section "ServerFlags"
        Option        "DontZap"    "False"
EndSection

```

---

### Post by vaerer on 2009-08-08
*bump*

---

### Post by vaerer on 2009-08-12
I should probably make it clear, the initial problem of the second monitor not showing up in the settings display page has been resolved.

The problem now is that I can only get the second monitor to work as a second .... separate thing.

Which means it's really, really slow and I never use it because I can't move windows across to it.

Is there any way I can get Xinerama or FramedBF to work?

Would it helped if I changed to Ubuntu or Kubuntu? Maybe Xubuntu won't work with my graphics card.

---

