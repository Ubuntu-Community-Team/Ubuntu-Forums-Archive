---
title: "modline does not work in 8.10"
date: 2008-12-07
forum: Multimedia Software
---

### Post by ChaosMonkey on 2008-12-07
Iam trying to get 1080p to work on my HDTV and hit a few snags. The auto detection appears to have detected a invalid configuration for the TV.  

No big deal happens all the time so I manually updated xorg.conf to use a lower resolution that was auto discovered in /var/log/Xorg.0.log which works.

So I decided to get fancy and set if I could get the 1080 to work or at least adjust the settings to remove the overscanning on the TV so I added a Modeline to the "Monitor" Section.

When I add a manual Modeline to xorg.conf even a complete copy of the line in Xorg.0.log with a different name it fails. Its acting like it does not know about the added Modeline.

Am I specifying it incorrectly or is there a problem with the intel driver that causes it to only use "discovered" ModeLines?

Any help would be appreciated.

Iam using ubuntu 8.10 2.6.27-9-generic

xorg.conf ===>

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Modeline "1872x1080" 135.500 1872 1944 1976 2032 1080 1086 1091 1111 -hsync -vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24

SubSection "Display"
Depth 24
Modes "1872x1080"
EndSubSection
EndSection

---

