---
title: "Nvidia Settings Error"
date: 2008-07-28
forum: Multimedia Software
---

### Post by psycho5 on 2008-07-28
Everytime I open my nvidia-settings it takes a long idle time of 2 minutes before opening up.

I ran it through terminal and after I hit enter, after the wait of 2 minutes, these messages came up. 

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


(nvidia-settings:9440): Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Style_big has no size field

```

Can anyone tell me what is the problem?

---

### Post by ibutho on 2008-07-28
Were you logged into a GUI when you ran those commands? It seems like the application you are trying to run needs an Xserver to be running in order to function properly.

---

### Post by psycho5 on 2008-07-28
Yeah I just ran a session through GUI. It does run, it just displays all those errors..

---

