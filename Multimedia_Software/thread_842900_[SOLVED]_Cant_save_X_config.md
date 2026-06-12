---
title: "[SOLVED] Cant save X config"
date: 2008-06-27
forum: Multimedia Software
---

### Post by genexxa27 on 2008-06-27
I just updated my nvidia drivers to the new ones from nvidia. The install went well and it seems to work but it seems that i cant save my configuration file and i have to reset it everytime i reboot or shut down.Im not to well versed in linux im still learning. Is there something that i missed. Thank you in advance

---

### Post by flytripper on 2008-06-27
try opening up in terminal


sudo nvidia-settings

and then save the settings

---

### Post by genexxa27 on 2008-06-27
I tryed that and i got this:
patrick@patrick-desktop:~$ sudo nvidia-settings
[sudo] password for patrick: 

ERROR: Cannot open display 'patrick-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 22 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 23 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 24 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 25 of configuration
       file '/home/patrick/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 26 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 27 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 28 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 29 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 30 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 31 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 32 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 33 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 34 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 35 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 36 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 37 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 38 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 39 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 40 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 41 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 42 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 43 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 44 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 45 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 46 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 47 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 48
       of configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 49 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 50 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 51
       of configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       52 of configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 53 of
       configuration file '/home/patrick/.nvidia-settings-rc' (no Display
       connection).
its a whole list of errors im guessing it didnt install clean

---

### Post by stmartin on 2008-06-28
I got the same problem. I posted new thread, but I don't know what to do. Also, I can't save X config, and on every restart, it brings back the old resolution and tells me that my device is not properly found or something like that.

---

### Post by starcannon on 2008-06-28
Have the nvidia utility write the new file

```
sudo nvidia-xconfig
```

Write this part down if you need to

Ctrl-Alt-F1
```
sudo /etc/init.d/gdm restart
```

be sure the nvidia driver is loading at boot

Alt-F2
```
gksudo gedit /etc/modules
```
Add ```
nvidia
``` to the list.

Reboot, you should be golden.

---

### Post by stmartin on 2008-06-28
Thanks, but it didn't helped. When I first installed the drivers I went to Applications/System Tools/NVIDIA X Server Settings and I pressed Save Configuration File. It didn't work. Seems like I need to be logged as root all the time to save the configuration file. On the end of the installation, it asked me something like "Do you want to do 'nvidia-xconfig' on every start so you can use the drivers installed? " I tried with both "Yes" and "No" and again the same problem.
Here is what I got:
[[IMG]http://img71.imageshack.us/img71/7017/00001my7.th.jpg[/IMG]](http://img71.imageshack.us/my.php?image=00001my7.jpg)

---

### Post by genexxa27 on 2008-06-29
Thank you starcannon that seemed to work i have the X server working and both my screens are running independently the only thing now is when i restart my one screen starts up a little squished but atlest both screens are booting at start up after i log in
Thank you again

---

### Post by stmartin on 2008-06-29
genexxa do u get the same problem as on the picture on boot time?

---

### Post by genexxa27 on 2008-06-29
no i dont it boots up with the driver installed but it still the one screen is running at 60hz insted of 75hz so its squished so i have to manually reset it back to 75hz and it still wont save that part to the x-config file
its a minor inconvenience but i think in the larger scheme of things i can live with it lol.

---

