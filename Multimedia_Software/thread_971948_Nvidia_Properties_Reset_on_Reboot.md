---
title: "Nvidia Properties Reset on Reboot"
date: 2008-11-05
forum: Multimedia Software
---

### Post by joel.whitney on 2008-11-05
Hi, Guys.  This is my first week with Ubuntu, and I'm liking it a lot.  I do have an issue, though:

My graphics properties are resetting after each reboot.  I'm running an Nvidia 6000GT card, with dual monitors.  The monitors are set up as twinview and at different resolutions.  I'm able to set them up with the Nvidia utility, and they work just the way I like them.  When I restart, however, it reverts to just one monitor at an incorrect resolution.

I've tried saving the conf file, which saves it to my home folder, but it doesn't seem to make a difference.  If I click the button in the utility interface marked "save as X" (or whatever it says - I'm at work at the moment), it actually closes down the utility, so I'm not sure if it's doing something correctly.

Any ideas?  Please let me know what info I need to share for you to look at.
Thanks!

---

### Post by overdrank on 2008-11-05
> **joel.whitney said:**
> Hi, Guys.  This is my first week with Ubuntu, and I'm liking it a lot.  I do have an issue, though:

My graphics properties are resetting after each reboot.  I'm running an Nvidia 6000GT card, with dual monitors.  The monitors are set up as twinview and at different resolutions.  I'm able to set them up with the Nvidia utility, and they work just the way I like them.  When I restart, however, it reverts to just one monitor at an incorrect resolution.

I've tried saving the conf file, which saves it to my home folder, but it doesn't seem to make a difference.  If I click the button in the utility interface marked "save as X" (or whatever it says - I'm at work at the moment), it actually closes down the utility, so I'm not sure if it's doing something correctly.

Any ideas?  Please let me know what info I need to share for you to look at.
Thanks!

Hi and welcome, What version of ubuntu are your using, 8.04 Hardy, Intrepid 8.10?
Have you tried using the command ```
gksu nvidia-settings 
``` to save the configuration?

---

### Post by joel.whitney on 2008-11-05
Hi, sorry for leaving out that I'm using Intrepid.  Told you I was new to this!

I have not tried using that command to save, as I assumed it was saving directly from the Nvidia utility.  How should that work -- do I configure my screen setup to my liking, and then just run that command from Terminal?

Thanks for your help.

Edit:  I may well be going about this all wrong.  I'm accessing the Nvidia utility through Gnome-Do, if that makes any difference.
Thanks again!

---

### Post by overdrank on 2008-11-05
> **joel.whitney said:**
> Hi, sorry for leaving out that I'm using Intrepid.  Told you I was new to this!

I have not tried using that command to save, as I assumed it was saving directly from the Nvidia utility.  How should that work -- do I configure my screen setup to my liking, and then just run that command from Terminal?

Thanks for your help.

Edit:  I may well be going about this all wrong.  I'm accessing the Nvidia utility through Gnome-Do, if that makes any difference.
Thanks again!

Hi and just use that command to open the nvidia-settings, you can use the alt, F2 keys and enter that command and then when you save the settings should stay in place.

---

### Post by joel.whitney on 2008-11-05
Okay, that didn't seem to do the trick.  I'm seeing the same problem.

I am seeing something interesting, though.  Now that I'm running the Nvidia utility from the command line, I see this error displayed:

[INDENT]j@J-Ubuntu:~$ gksu nvidia-settings
ERROR: Invalid display device CRT-1 specified on line 21 of configuration
       file '/root/.nvidia-settings-rc' (the currently enabled display
       devices are CRT-0 on J-Ubuntu:0.0).


ERROR: Invalid display device CRT-1 specified on line 23 of configuration
       file '/root/.nvidia-settings-rc' (the currently enabled display
       devices are CRT-0 on J-Ubuntu:0.0).[/INDENT]



And the text from the config file:

[INDENT]#
# /home/j/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Wed Nov  5 07:44:47 2008
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

J-Ubuntu:0.0/DigitalVibrance[CRT-0]=0
J-Ubuntu:0.0/ImageSharpening[CRT-0]=0
J-Ubuntu:0.0/SyncToVBlank=0
J-Ubuntu:0.0/AllowFlipping=1
J-Ubuntu:0.0/LogAniso=0
J-Ubuntu:0.0/FSAA=0
J-Ubuntu:0.0/TextureSharpen=0
J-Ubuntu:0.0/CursorShadow=0
J-Ubuntu:0.0/CursorShadowXOffset=4
J-Ubuntu:0.0/CursorShadowYOffset=2
J-Ubuntu:0.0/CursorShadowAlpha=64
J-Ubuntu:0.0/CursorShadowRed=0
J-Ubuntu:0.0/CursorShadowGreen=0
J-Ubuntu:0.0/CursorShadowBlue=0
J-Ubuntu:0.0/FSAAAppControlled=1
J-Ubuntu:0.0/LogAnisoAppControlled=1
J-Ubuntu:0.0/RedBrightness=0.000000
J-Ubuntu:0.0/GreenBrightness=0.000000
J-Ubuntu:0.0/BlueBrightness=0.000000
J-Ubuntu:0.0/RedContrast=0.000000
J-Ubuntu:0.0/GreenContrast=0.000000
J-Ubuntu:0.0/BlueContrast=0.000000
J-Ubuntu:0.0/RedGamma=1.000000
J-Ubuntu:0.0/GreenGamma=1.000000
J-Ubuntu:0.0/BlueGamma=1.000000
J-Ubuntu:0.0/OpenGLImageSettings=1
J-Ubuntu:0.0/XVideoTextureSyncToVBlank=1
J-Ubuntu:0.0/XVideoBlitterSyncToVBlank=0
J-Ubuntu:0.0/XVideoSyncToDisplay=1[/INDENT]

Any ideas?  And thanks for all your help!

---

### Post by mistervino on 2008-11-06
This seems to be the same problem: [http://ubuntuforums.org/showthread.php?t=964143]("http://ubuntuforums.org/showthread.php?t=964143")

---

### Post by joel.whitney on 2008-11-06
That is in fact the same problem, and my setup is now fixed with that solution.  

Thank you very much!

---

