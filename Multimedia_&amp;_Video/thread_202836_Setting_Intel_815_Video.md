---
title: "Setting Intel 815 Video"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by tlg on 2006-06-24
I have just installed Ubuntu for the first time, and I am a novice to Linux.
I have an Intel motherboard with an integrated 82815 video chipset.
The screen resolution has been set to 1024 X 768 by default during the setup.

When I try to set the screen resolution from System/Preferences menu, it shows only 60Hz refresh rate available for the 1024 x 768 resolution, but higher  refresh rates of 72 and 75 are available for 800 x 600 resolution.

I believe the chipset is capable of the higher refresh rates at 1024 x 768. (true?)
I've looked at the etc/X11/xorg.conf file as suggested in other posts but I can't see what to change there to get the higher rates.

Can anyone suggest how I should go about setting up the system for a higher refresh rate please?

Also, when I go to the Intel website to download Linux current drivers for the chipset, it offers an rpm file as download. Is this of any use on a Ubuntu system and if so how do I install from the rpm. If not is there another way of getting updated drivers please?

Thanks in advance for any help.

---

### Post by tlg on 2006-06-24
Run this from command line:
Code:

sudo dpkg-reconfigure xserver-xorg

Fixed. Thanks to lvhassel in later post.

---

