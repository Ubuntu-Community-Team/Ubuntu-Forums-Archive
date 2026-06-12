---
title: "NVIDIA Config settings won't save"
date: 2009-05-24
forum: Multimedia Software
---

### Post by CompanyCalls405 on 2009-05-24
When I first started Ubuntu 9.04 the default resolution was 800x600. I had to download some NVIDIA graphics drivers to let me use 1024x768. That all worked fine, but the problem is that when rebooting, my configuration settings were not saved and I was back at 800x600 and I had to once again open nvida settings and reconfigure.

I found a thread here that dealt with my exact problem:

[http://ubuntuforums.org/showthread.php?t=471256](http://ubuntuforums.org/showthread.php?t=471256)

I did exactly what was said, opening it in terminal with 'sudo' including renaming the save file 'xorg.conf.backup', but still, when I reboot, I'm back to 800x600.

Not sure if this is relevant but when I boot via terminal I get several error messages within the terminal:

     Quote:> 
                                                 ERROR: Unable to assign attribute CursorShadow specified on line 20 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 21 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 22 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 23 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 24 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 25 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 26 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 27 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 28 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 29 of configuration
       file '/home/kit/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 30 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 31 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 32 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 33 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 34 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 35 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 36 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 37 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 38 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 39 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 40 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 41 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 42 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 43 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 44 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 45 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       46 of configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       47 of configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 48 of
       configuration file '/home/kit/.nvidia-settings-rc' (no Display
       connection).                                 
Thanks in advance for any help.Note: I posted this in "desktop enviornments" before noticing there was a board specifically for this sort of thing. My mistake.

---

### Post by ad_267 on 2009-05-24
How did you download the nvidia drivers? Did you use the default Ubuntu drivers from System - Administration - Hardware Drivers.

You should be able to change your settings by pressing Alt+F2 and running "gksu nvidia-settings". That will run the nvidia settings application as root. You can then remove your ~/.nvidia-settings-rc file.

---

### Post by CompanyCalls405 on 2009-05-24
> **ad_267 said:**
> How did you download the nvidia drivers? Did you use the default Ubuntu drivers from System - Administration - Hardware Drivers.

You should be able to change your settings by pressing Alt+F2 and running "gksu nvidia-settings". That will run the nvidia settings application as root. You can then remove your ~/.nvidia-settings-rc file.

Yes, I downloaded them that way. I've ran the settings as a root before but haven't tried to delete anything...how exactly would I go about removing  ~/.nvidia-settings-rc? Is that the default file it's accessing instead?

---

### Post by ad_267 on 2009-05-24
That's your user specific settings file, rather than the system wide settings. I think they may be over-riding the system settings. The "~" just means your home directory. In the file browser you can show hidden files (Ctrl+H) and then delete that file. Files that start with a "." are hidden in Linux. Then log out and in again and run nvidia-settings as root using "gksu nvidia-settings". Hopefully that will sort everything out.

---

### Post by CompanyCalls405 on 2009-05-24
> **ad_267 said:**
> That's your user specific settings file, rather than the system wide settings. I think they may be over-riding the system settings. The "~" just means your home directory. In the file browser you can show hidden files (Ctrl+H) and then delete that file. Files that start with a "." are hidden in Linux. Then log out and in again and run nvidia-settings as root using "gksu nvidia-settings". Hopefully that will sort everything out.

Unfortunately this didn't work...not sure if this will help but some more info:

I can tell by the size of the pointer icon what resolution I'm booting too in the first few seconds of black screen before everything appears. At first it's the 1024x763 size, then the screen goes black and it appears bigger, and the resolution is 800x600.
Not sure if that means anything but it seems like it's attempting to boot to the res I want but is ovveridden.

When saving my config in nvidia-settings, it saves to '/etc/X11/xorg.conf. Is that correct?




Also, this is the "Preview" file I can bring up when saving my settings

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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 60.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768 +0+0; 1024x768_60 +0+0;+0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; 1024x768_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by CompanyCalls405 on 2009-05-24
bump

---

### Post by xc3RnbFO8P on 2009-05-24
Try to add:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
    **Option         "ModeValidation" "NoDFPNativeResolutionCheck"**
EndSection

---

### Post by CompanyCalls405 on 2009-05-24
> **Ringi said:**
> Try to add:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
    **Option         "ModeValidation" "NoDFPNativeResolutionCheck"**
EndSection

This made me boot in low graphics mode...anything specific I'm supposed to do in that? I booted in 800x600 after it.

---

### Post by xc3RnbFO8P on 2009-05-24
Remove the Option "ModeValidation" "NoDFPNativeResolutionCheck"
and change 
Option         "metamodes" "1024x768 +0+0; 1024x768_60 +0+0"
to 
Option         "metamodes" "1024x768_60 +0+0"

---

### Post by CompanyCalls405 on 2009-05-24
> **Ringi said:**
> Remove the Option "ModeValidation" "NoDFPNativeResolutionCheck"
and change 
Option         "metamodes" "1024x768 +0+0; 1024x768_60 +0+0"
to 
Option         "metamodes" "1024x768_60 +0+0"

Same result as before.

---

### Post by xc3RnbFO8P on 2009-05-24
Do have VGA or DVI cable, and is it  CRT or LCD monitor?

---

### Post by Cillys on 2009-05-24
I ran into this as well .... i just got around it by having the NVIDIA apply the changes ....

when you go to save the configuration .. did like you did and preview it ... copy the whole selection ..
then from a terminal window ....

sudo gedit /etc/X11/xorg.conf

paste in the new code ... and save that way ...

worked for me ...

you can make a back up if you want

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak

what you are doing is running the sudo command .. which opens the file as root user ... allows you absolute control then ...

good luck

---

### Post by CompanyCalls405 on 2009-05-24
> **Cillys said:**
> I ran into this as well .... i just got around it by having the NVIDIA apply the changes ....

when you go to save the configuration .. did like you did and preview it ... copy the whole selection ..
then from a terminal window ....

sudo gedit /etc/X11/xorg.conf

paste in the new code ... and save that way ...

worked for me ...

you can make a back up if you want

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak

what you are doing is running the sudo command .. which opens the file as root user ... allows you absolute control then ...

good luck

I'm having a hard time understanding why this didn't work. On reboot I'm back at 800x600, but when I bring up the code using  sudo gedit /etc/X11/xorg.conf it shows this in the "screen" section.

> Section "Screen"
 
   Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Isn't Option 1024x768 exactly what I want?? 
This is getting very frustrating =/

---

### Post by CompanyCalls405 on 2009-05-24
It appears I solved my own problem. Not using the terminal, I went to System>Preferences>Display and I was asked whether or not I wanted to use the NVIDIA tool. I clicked No and was brought to what I suppose is the default Ubuntu display config tool. From there I could select 1024x768 (something I couldn't do in this config before installing NVIDIA drivers.)
I hit apply and selected to use these settings.
On reboot I was at 1024x768!

I'm unsure why this worked, my only guess is that that my Ubuntus settings were ovveriding NVIDIAs.

Thanks to everyone who helped out.

---

### Post by WIldDude92 on 2009-06-01
I had the same problem.  Tried all the suggestions over the past 2 weeks.  The last one worked:  Save settings via System -> Preferences -> Display

Thanks.

---

### Post by dpacifico on 2010-01-02
Try using the System / Preferences / Display ( "gnome-display-properties"). Force 'No' when asked if you want to use the driver from the manufacturer of your video.

I believe the Ubuntu display configurator should be overwriting the settings of NVIDIA display configurator.

I had the same problem and it worked!

Good luck!

---

### Post by nephlim on 2010-01-10
> **CompanyCalls405 said:**
> It appears I solved my own problem. Not using the terminal, I went to System>Preferences>Display and I was asked whether or not I wanted to use the NVIDIA tool. I clicked No and was brought to what I suppose is the default Ubuntu display config tool. From there I could select 1024x768 (something I couldn't do in this config before installing NVIDIA drivers.)
I hit apply and selected to use these settings.
On reboot I was at 1024x768!

I'm unsure why this worked, my only guess is that that my Ubuntus settings were ovveriding NVIDIAs.

Thanks to everyone who helped out.

I had the exact same problem. This worked like a charm.

---

