---
title: "Monitor Refresh Rate"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by forchessonly on 2007-04-25
Hi,

I just installed the newest nvidia driver on Ubuntu Dapper and they work, but when I go to System->Preferences->ScreenResolution the only available refresh rate for any resolution is 85Hz. Before installing the new videocard driver I could pick from many available refresh rates from 50-120Hz. 

I would like to be able to drop the refresh rate down to 65Hz so I can set the resolution up to 1600x1200. My monitor has problems when the refresh rate is turned up to 85Hz at 1600x1200 resolution. 

Any suggestions? 

Thanks

---

### Post by cookieofdoom on 2007-04-25
Run nvidia-settings. There should be an option in there to adjust refresh rate and resolution.

---

### Post by jcconnor on 2007-04-25
Do you have a menu option for:

Nvidia X Server Settings

(Sorry I use edgy and had that available to me when I installed the latest nvidia driver).  If you do, you should be able to use that to set both the refresh rate and the resolution.

John

---

### Post by forchessonly on 2007-04-25
Hi again,

"Run nvidia-settings. There should be an option in there to adjust refresh rate and resolution."

My nvidia-settings doesn't have a refresh rate option. In the menu there is:

> user-desktop:0.0
X Server Color Correction
X Server XVideo Settings
Cursor Shadow
OpenGL Settings
OpenGL/GLX Information
Antialiasing Settings

> Display Device
HP P1130

> nvidia-settings Configuration

You would think that the refresh rate would be under Display Devices -> HP P1130, but the only options are for Digital Vibrance and Image Sharpening. There isn't anything related to the refresh rate under nvidia-setting Configuration either. 

============================================
"Do you have a menu option for:
Nvidia X Server Settings?"

Yes, that's what I listed about. But there's nothing in there related to my refresh rate... :-(

---

### Post by forchessonly on 2007-04-25
Um, any other possible solutions? ... Anybody?

Thanks

---

### Post by Erlander on 2007-04-25
The second menu item from the top should be "X Server Display Configuration" and it would be in there.

Try uninstalling and re-installing Nvidia-Settings in Synapatic.

Rob

Edit:  I just had a look at this.  NVidia_settings is part of the Restricted Drivers Package and can't be overwritten by the package in Synapatic.  I tried to in order to see what happened.

Rob

---

### Post by f_s on 2007-08-15
try

gksudo nvidia-settings

every config option should thereafter appear

cheerzow

F

---

