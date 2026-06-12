---
title: "xorg.conf keeps getting reset upon reboot"
date: 2008-03-20
forum: Mythbuntu
---

### Post by jfirebau on 2008-03-20
I just installed MythBuntu 7.10 (after having some issues with MythBuntu 8.04) on machines that were running MythBuntu 7.10 before without problems.

I'm not sure if this makes sense, but it seems as if there are newer features this time on my installation, which means the installer must look for newer packages while installing.  I did a destructive install reformating the harddrives.

The issue I have now is that everytime my MythBuntu Frontend Only machine reboots the xorg.conf file seems to get replaced with default screen size values of 640x480.  When I edit the file or use NVidia's Tool to set the screensize back to 1280x720 -- everything works exactly like I want it until the next reboot.

[COLOR="Blue"]Is there some new process during the boot scenario that I can dissable to keep this from happening?[/COLOR]

In case it matters, I have a LCD TV connected to my Nvidia MX440 DVI port using a HDMI cable and HDMI to DVI dongle at PC.

I suppose I may have given up on MythBuntu 8.04 a little too early because one of the reasons I decided to revert back to 7.10 was this issue -- as well as an issue where my frontend only machine was always asking for the superuser password upon each boot and not starting MythTV Frontend -- and Alsa didn't seem to be set up correctly either.  Now that I list the problems -- maybe I did do the right thing and go back... :)

---

### Post by kbrunsting on 2008-03-20
I have the same problem.... I also recently did a complete reinstall using 7.10 and noticed if I tried restarting X, it would go back to 640x480 and I had to copy back my good xorg.conf to get it back to the correct resolution.

---

