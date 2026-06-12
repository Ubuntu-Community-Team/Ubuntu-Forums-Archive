---
title: "External monitor not automatically loading"
date: 2008-12-10
forum: Multimedia Software
---

### Post by mbwmex on 2008-12-10
I am running 8.10, dual boot win vista, on a Dell E 1505 with a Nvidia card, external monitor is a ViewSonic VX25035WM.

Installed the Nvidia driver, #173 with no problems.

I can only use the external monitor by using the FN/F8 key combination on the Dell Laptop.  

When I go the Nvidia X server settings, both the laptop and external monitors are recognized.  I have tried all the setups, twin, x and clone.  

When attempting to save the new settings I get this error msg. that the '/etc/X11/xorg.conf.backup'. can not be created.

What can be done so the external monitor loads automatically?  It does when in Win Vista.

Thanks for help

---

### Post by pwaldo on 2008-12-10
> **mbwmex said:**
> When attempting to save the new settings I get this error msg. that the '/etc/X11/xorg.conf.backup'. can not be created.
Try running ```
sudo nvidia-settings
```

---

### Post by mbwmex on 2008-12-10
result of command line sudo nvidia-settings
ERROR: Cannot open display 'DellLaptop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 22 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 23 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 24 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 25 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 26 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 27 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 28 of configuration
       file '/home/mbw/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 29 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 30 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 31 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 32 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 33 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 34 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 35 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 36 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 37 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 38 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 39 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 40 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 41 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 42 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 43 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 44 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 45 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 46 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 47 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 48 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       49 of configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       50 of configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 51 of
       configuration file '/home/mbw/.nvidia-settings-rc' (no Display
       connection).

Thanks for help.

---

### Post by pwaldo on 2008-12-10
OK, try this:```
gksudo nvidia-settings
```HTH!

---

### Post by mbwmex on 2008-12-10
Results of gksudo nvidia-settings;

The Nvidia x server settings control panel comes up.

Thanks for help.

---

