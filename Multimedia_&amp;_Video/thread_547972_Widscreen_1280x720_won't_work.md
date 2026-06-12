---
title: "Widscreen 1280x720 won't work"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by StrayTheNomad on 2007-09-10
I'm running Ubuntu Feisty 7.04, I have an Intel 946gz integrated graphics chipset, and a 32" Akai HDTV for a monitor.
I have Windows Vista on my other partition, and it runs at a resolution of 1280*720 just perfectly.
Ubuntu will not give me any resolutions that fit a 16;9 aspect ratio.
I edited my xorg.conf file to include

SubSection "Display"
                Depth           24
                Modes           "1280x720" "1024x768" "852x480" "800x600" "720x$
EndSubSection

No luck.  1280x720 won't show up when I go to System->Administration->Screen Resolutions.
I downloaded 915 Resolution.
I found that block 5a contained a resolution mode I wouldn't need
In the terminal I typed
sudo nano /etc/default/915resolution
Which then included...
MODE=5a
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=1280
YRESO=720
#
As soon as Ubuntu would get to the login, the screen would go black and my monitor's OSD would read "Not Support"

Why wouldn't the monitor support it? Windows handles it just fine.
I've also tried reinstalling the newest Intel drivers, but this always seems to break Ubuntu. I'm on my seventh reinstall in only four days.
I'm a total Linux Newbie, and so far I'm not liking how difficult this is. I still can't get more than one program to play sound at the same time (full duplex support) like I could with Vista.
Please, someone set me straight. Help me out.

---

