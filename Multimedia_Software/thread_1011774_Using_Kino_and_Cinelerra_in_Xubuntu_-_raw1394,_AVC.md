---
title: "Using Kino and Cinelerra in Xubuntu - raw1394, AV/C"
date: 2008-12-15
forum: Multimedia Software
---

### Post by Bucky Ball on 2008-12-15
Hi all,

I have Xubuntu loaded and then Ubuntu Studio audio and video packages loaded into there (no UStudio desktop). I am trying to get device control happening with my Panasonic NV-DS60 digital video camera. Works not problem in Windoze. I have tried the instructions on this page for Ubuntu::

[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)

Which started to get me excited. When I create a group in 'Users and Groups' called 'firewire' and add myself to that group, I start getting an error about GDM. Last time this happened, I had to reinstall in the end as things got so messed up.

So, something has struck me. GDM refers to Gnome? If I am running Xfce with no Gnome, is that going to cause a problem trying to use DV camera? Is there dependencies in Gnome that are required by Cinelerra and Kino, which is why neither sees my camera?

From my research, it appears I need to be using raw1394 driver to access the camera controls from the GUI. One thing works in Kino, I can stop the camera if I manually hit play!

Any help much appreciated ... :) Tnx in advance.

ps: incidentally, last time I went through this I actually rebooted after making the firewire group and appropriate permissions, wouldn't go to login as couldn't find a screen. Also, I am using the 2.6.24-22-rt real time kernel.

Also, this was at the end of my dmesg:

 ```
[ 3473.266477] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00804580b112cb7e]
[ 3473.268133] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 3473.389880] ieee1394: raw1394: /dev/raw1394 device initialized
[ 3473.408129]NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
```So, the plot thickens. dv1394 doesn't seem to be loading but this is telling me it is not required. Now i am confused (more). Maybe I should remove it completely? Is there a way I can blacklist it to prevent it loading when I turn the camera on? Some kind of conflict?

* Further clue. When I boot Kino, sees my camera no problem in Edit/Preferences/ieee1394. Manufacturer and even model. Gives the driver as /dev/dv1394/0 . But when I click on capture and then open preferences/ieee1394, the camera has disappeared. I must be pretty close! I'll keep experimenting and trawling.

---

### Post by DuncanNZ on 2009-02-23
Hi there, I've updated the instructions on [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) and would love it if you could take a look and let me know if you hit any problems. I'll try and help you in this thread.

---

### Post by POWMS on 2009-02-23
Bucky
I asked a similar question yesterday, but got no takers.
Searching the internet I found this:
[http://www.linux1394.org/](http://www.linux1394.org/)
I'm going to load the raw driver tonight and see if my Panasonic Dv will work. It seems Xubuntu does not come with this driver?

---

### Post by Bucky Ball on 2009-02-23
POWMS, you might want to have a look here:

[http://ubuntuforums.org/showthread.php?t=946708](http://ubuntuforums.org/showthread.php?t=946708)

I brought a camera home from uni, plugged it in and kino recognised it better than the macs at uni so I did all my video capture for the project with Kino! I had it right all along, it was my camera. The one from uni was a new Sony. Picked it up immediately. :)

I did find a list of dv cameras somewhere along the way and it did say my model worked a bit. So it did work a bit. I am about to try the same on a newly built machine running Ubuntu 8.04.2 using DuncanNZ's instructions. Same Panasonic I used originally so I'll see how it goes.

---

