---
title: "[SOLVED] nvidia-settings problem"
date: 2008-10-16
forum: Multimedia Software
---

### Post by psycho5 on 2008-10-16
Can someone help please...

from terminal I run nvidia-settings, it takes very long to load and then loads up after returning these errors..

```
:~$ nvidia-settings

ERROR: Cannot open display 'ubuntupwr:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 22 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 23 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 24 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 25 of configuration
       file '/home/oj/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 26 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 27 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 28 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 29 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 30 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 31 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 32 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 33 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 34 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 35 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 36 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 37 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 38 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 39 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 40 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 41 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 42 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 43 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 44 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 45 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 46 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 47 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 48 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 49
       of configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 50 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       51 of configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/oj/.nvidia-settings-rc' (no Display
       connection).

```



here's the content of my .nvidia-settings-rc file

```
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sun Jun 29 03:37:30 2008
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = No
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000

# Attributes:

ubuntupwr:0.0/DigitalVibrance[CRT-0]=0
ubuntupwr:0.0/SyncToVBlank=0
ubuntupwr:0.0/AllowFlipping=1
ubuntupwr:0.0/LogAniso=0
ubuntupwr:0.0/FSAA=0
ubuntupwr:0.0/TextureSharpen=0
ubuntupwr:0.0/ForceGenericCpu=0
ubuntupwr:0.0/GammaCorrectedAALines=0
ubuntupwr:0.0/CursorShadow=0
ubuntupwr:0.0/CursorShadowXOffset=4
ubuntupwr:0.0/CursorShadowYOffset=2
ubuntupwr:0.0/CursorShadowAlpha=64
ubuntupwr:0.0/CursorShadowRed=0
ubuntupwr:0.0/CursorShadowGreen=0
ubuntupwr:0.0/CursorShadowBlue=0
ubuntupwr:0.0/FSAAAppControlled=1
ubuntupwr:0.0/LogAnisoAppControlled=1
ubuntupwr:0.0/FSAAAppEnhanced=0
ubuntupwr:0.0/RedBrightness=0.000000
ubuntupwr:0.0/GreenBrightness=0.000000
ubuntupwr:0.0/BlueBrightness=0.000000
ubuntupwr:0.0/RedContrast=0.000000
ubuntupwr:0.0/GreenContrast=0.000000
ubuntupwr:0.0/BlueContrast=0.000000
ubuntupwr:0.0/RedGamma=1.000000
ubuntupwr:0.0/GreenGamma=1.000000
ubuntupwr:0.0/BlueGamma=1.000000
ubuntupwr:0.0/OpenGLImageSettings=1
ubuntupwr:0.0/XVideoTextureBrightness=0
ubuntupwr:0.0/XVideoTextureContrast=4054
ubuntupwr:0.0/XVideoTextureSyncToVBlank=1
ubuntupwr:0.0/XVideoSyncToDisplay=1

```

What's going on here? I appreciate your help. Thanks

---

### Post by overdrank on 2008-10-16
Hi and have you tried the command ```
gksu nvidia-settings
```

---

### Post by kpkeerthi on 2008-10-16
Probably a permission issue on ~/.nvidia-settings-rc
Check the permission and change it
```
ls -l ~/.nvidia-settings-rc
```

Or just remove the file and it will be recreated when you open nvidia-settings (without gksudo)
```
sudo rm ~/.nvidia-settings-rc
```

---

### Post by psycho5 on 2008-10-16
Thank you, removing the file did the trick.

---

