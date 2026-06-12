---
title: "how do i make nvidia settings sticky ?"
date: 2010-03-11
forum: Multimedia Software
---

### Post by Beowulf.1000 on 2010-03-11
I can't seem to make my nvidia settings configuration sticky. I go to System: Admin: NVIDIA Configuration and then save the nvidia config file from that GUI and it saves to ~/.nvidia-settings-rc and contains the following (below). But when I reboot, none of the settings have taken effects (most noticably brightness and contrast). Ideas? Solution?

Ubuntu 9.10 65bit Desktop on AMD quad core PC, 8GB.

#
# /home/beowulf/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Thu Mar 11 14:27:25 2010
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=1
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=5
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=0
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/RedBrightness=-0.409396
0/GreenBrightness=-0.409396
0/BlueBrightness=-0.409396
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/ImageSharpening[DFP-0]=0
0/GPUScaling[DFP-0]=65537
0/XVideoTextureSyncToVBlank=1
0/XVideoBlitterSyncToVBlank=0
0/XVideoSyncToDisplay=65536

---

### Post by 2hot6ft2 on 2010-03-11
Start nvidia-settings as root using this in a terminal then they should be saved.
```
gksu nvidia-settings
```
since saving it as a regular user doesn't work.

The second option from the top on the left has "save to X configuration file" in the lower right and
The last option at the bottom on the left has "Save Current Configuration" in the lower right.

---

### Post by Beowulf.1000 on 2010-03-11
> **2hot6ft2 said:**
> Start nvidia-settings as root using this in a terminal then they should be saved.
```
gksu nvidia-settings
```
since saving it as a regular user doesn't work.

The second option from the top on the left has "save to X configuration file" in the lower right and
The last option at the bottom on the left has "Save Current Configuration" in the lower right.

Did that, but then an error dialogue popped up saying it was unable to parse /etc/X11/xorg.conf

I have an xorg.conf file there-- looks like it had some errors from my tweaking it (and botching it up apparently!). I copied the listed failsafe xorg file to xorg.conf then ran the config program again and it saved it to xorg.conf fine, going to reboot now and hope for the best!

---

### Post by Beowulf.1000 on 2010-03-11
None of the /home/beowulf/.nvidia-settings-rc settings I see in that file are found in the xorg.conf file, settings on color, hues, etc. so I am not sure how xorg.conf would even know to make the color/brightness settings stick during boot? Those settings are not sticking at this point, frustrating.

---

### Post by Beowulf.1000 on 2010-03-11
Solved ! Here is some useful info too that led me to the final solution (in addition to what has been said so far in this thread):
[http://linux.die.net/man/1/nvidia-settings](http://linux.die.net/man/1/nvidia-settings)

The key to making the settings stick is to go into the System: Preferences: StartupApplications menu and then 'add an application' and just give this command line:

   nvidia-settings --load-config-only &

which will load the hidden file /home/beowulf/.nvidia-settings-rc on boot, setting the colors brightness saturation etc. into the nvidia card.

---

### Post by mookie60 on 2010-04-14
Thanks Beowulf.   The only change I had to make was to change the permissions on the nvidia-settings-rc file.   I'm not really sure what was necessary, but I just opened full read/write for everyone, then resaved the file (from within the nvidia utility) and that worked.

John

---

