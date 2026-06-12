---
title: "Locked Screen after xdotool installation"
date: 2012-07-12
forum: Mythbuntu
---

### Post by wilsonmak on 2012-07-12
I am using MyTVbuntu 10.10 for an application that display video and image.
But suddenly it locked itself with Login screen (gnome-session LoginWindow)
I have already disabled Screen Saver and lock screen capability on the desktop (XFCE4)
And set the followings:

1) xorg.conf
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"

2) /etc/kbd/config
BLANK_TIME=0
BLANK_DPMS=off
POWERDOWN_TIME=0

3) xscreensaver has been removed.

Just wondering what other config files trigger this lock screen function.

P.S.  Before I install xdotool, it was working properly.

Thanks,
Wilson

---

