---
title: "(RC 8.10) Mythbuntu Nvidia Ultra 5600 low resolution"
date: 2008-10-27
forum: Mythbuntu
---

### Post by scsever on 2008-10-27
I did a clean install of RC 8.10 and after reboot selected to use the recommended Nvidia proprietary driver version 173, however I am not able to get better than 640x480 resolution.  I've also tried using Envy to update the driver and have the same problem there, Envy also recommended version 173, there were two other options offered by Envy but those did not work either.  I also tried creating a new Xorg with "sudo dpkg-reconfigure -phigh xserver-xorg" which didn't help.
One thing I find is missing is the option to configure Xorg from the Mythbuntu Control Center, this is where I would configure my display on previous versions of MythBuntu.  From Mythbuntu Control Centre I would select "Proprietary Drivers" and then "Launch Xorg Config", but "Launch Xorg Config" can not be selected now, it's shaded out.  In this same window if I select "Launch Restricted Drivers Manager" I see that the Version 173 driver is activated and if I select "Launch NVIDIA Settings" I see an option to select Auto, 640x480 or 320x240 (Auto is currently selected).  I do recall on previous versions of Mythbuntu that unless I used "Launch Xorg Config" from the Control Centre I could not get my display configured properly.  Any one know why that would not be a usable option now?  Or have other ideas?
I used the alternate 64bit install and have done all updates.  The driver version is 173.14.12.  Below is my xorg.conf, minus the commented out stuff.  Not much to see but I seem to recall that recent xorg.conf files have not had much in them.

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

---

### Post by clickwir on 2009-03-25
I just reinstalled 8.10 with an NVIDIA 5200 and can't get better than 640x480 either. 

My xorg.conf shows more resolutions but I can't use them. I'm not using TV out on this setup, it's going to a monitor that's capable of much more. 

nvidia-settings only shows the 2 options, like the above stated post.

What's my option for changing the resolution?

---

