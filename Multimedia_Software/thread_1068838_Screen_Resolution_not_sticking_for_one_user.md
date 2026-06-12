---
title: "Screen Resolution not sticking for one user"
date: 2009-02-13
forum: Multimedia Software
---

### Post by Spartachris on 2009-02-13
I know there are tons of threads on this, but I haven't seen my version of the problem.

I successfully changed the resolution for all the users but me. When I log in, screen resolution reverts to 1024x768. All other users stick at my preferred setting of 1152x864, including log-in screens.

I have tried everything I could find to get it to work, with no results.

I am pretty much a noob :(

Thanks!

---

### Post by overdrank on 2009-02-13
Hi and if you have used the command ```
gksu nvidia-settings
``` to set the resolution you will need to save it to the xconfiguration in the nvidia-settings.

---

### Post by Spartachris on 2009-02-13
overdrank--

Thanks. I just tried that command and got this in terminal:
```
ERROR: Cannot open display 'christopher-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 22 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 23 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 24 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 25 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 26 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 27 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 28
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 29
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 30 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 31 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 32 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 33 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line
       35 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 46
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line
       47 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line
       48 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 49 of
       configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line
       50 of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on
       line 51 of configuration file '/root/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52
       of configuration file '/root/.nvidia-settings-rc' (no Display
       connection).
```

It opened the Nvidia X Server Settings, though, and I changed the resolution to 1152x864, saved to X Configuration File, logged out and logged back in...only to have it reverted to 1024x768 again.

---

### Post by Spartachris on 2009-02-28
So after a restart, I'm not getting that list of errors anymore, but it is still the case that all users' settings are sticking, but not mine. I use the sudo command, it works until I restart. I revert to 1024x786, everyone else sticks at 1152x864.

---

### Post by Spartachris on 2009-08-14
Just looking through my subscribed threads and realized it is long solved. Sorry!:) 

But not sure how to mark it as solved....

---

### Post by bpinkston on 2009-12-18
I can't find the solution.  Same issue. 

sudo touch xorg.conf
rm xorg.conf xorg.backup
sudo nvidia-settings
save to x configuration  (it Succeeds)
Log in any other user and resolution sticks, but not for my user. 


Thanks, 

Brent

---

