---
title: "Nvidia Resolution Settings"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by KingCandyCorn on 2008-01-13
Just converted my system from OpenSUSE 10.1 to Gutsy yesterday.

I see a lot of postings about the Nvidia resolution issues but my problem is a little different from the ones I've found.

Got the Nvidia drivers installed for my GeForce 6100 on my Jetway  J754GT3-PTD motherboard.  Everything was fine.  I changed my resolution from the default 1800x1440 and 50Hz to 1600x1200 and 61Hz.  No problems there.  Everything was working beautifully.

I install several packages to get other things set up.  Mostly this was Samba, Swat, Xinetd, Azureus, and a few Samba related utilities.  While trying to configure Samba through the System/Administration/Samba utility, Gnome locks up.  I jump over to tty6, poke around, can't unfreeze things.  Restart Gnome, no luck, it never comes up.  Go back to tty6 and restart the machine. 

Machine comes back up and it is back in 1800x1440 @ 50hz.  I go to change screen resolution through the System/Preferences/Screen Resolution utility and it ignores me.  It gives me the little accept/revert dialog but it doesn't actually change any settings.

I use the nvidia-settings utility and it doesn't let me change res either.  It does at least give me this error dialog when I hit "apply":
Failed to set MetaMode (2) 'CRT-0: 1600x1200 @1600x1200 +0+0' (Mode 1600x1200, id: 51) on X screen 0

My xorg.conf (which I never manually changed in this process) has these relevant sections:

Section "Device"
        Identifier      "nVidia Corporation C51G [GeForce 6100]"
        Driver          "nvidia"
        Busid           "PCI:0:5:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation C51G [GeForce 6100]"
        Monitor         "NOKIA 445PRO"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1800x1440"     "1600x1200"     "1280x1024"     "1024x768"      "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "Monitor"
        Identifier      "NOKIA 445PRO"
        Option          "DPMS"
EndSection

Section "Module"
        Load            "glx"
EndSection

I'm basically lost at this point.  I'd be able to live with this resolution if it weren't for the refresh rate.  Any ideas on what happened and/or how to fix this?

Thanks in advance.

---

