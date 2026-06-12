---
title: "blue skin in movies"
date: 2008-05-23
forum: Multimedia Software
---

### Post by galliard on 2008-05-23
hello, I have a problem watching movies. in every one of them (even animated) people have blue skin. other colors are also broken but not as much.
today i installed randomly many plugins to have my audioplayer work right, maybe one of those plugins/codecs is responsible for it.

anybody has ideas what should i install/uninstall to have my proper colors back?

regards

---

### Post by nlbs on 2008-05-23
which player you are trying ?

---

### Post by cor2y on 2008-05-23
Let me guess Nvidia card using the closed source drivers?
Open up Totem (Application->Sound & Video->Movie Player) and go to the display settings tab (Edit->Preferences) and adjust the HUE setting either to the max or min , then in whatever media player you choose the video should now have the correct color.
This is due to nvidia resetting how the HUE color is displayed in video with their closed source driver (they reversed the settings) and they have no plan to correct this.

---

### Post by el Arm on 2008-05-25
> **cor2y said:**
> Let me guess Nvidia card using the closed source drivers?

Thanks for this, I was getting the same problem and this fixes it nicely.

There may be more a more complicated interaction that is causing it though. I have been watching videos (avi) happily since Hardy came out but, similar to the OP, yesterday I installed a whole batch of players and other packages in a (so far futile) attempt to get DVD playback working, and today the blue started.

It occured in all players (MPlayer, totem-xine, totem-gstreamer, VLC, xine) so that definitely points to a lower-level issue like the graphics drivers but or course it worked originally and the drivers haven't changed.

For the record, I'm on 8.04 amd64 using the NVIDIA restricted drivers.

---

### Post by pjbgravely on 2008-07-19
I had the color inversion and fixed it with the work arounds. The result was a normal but degraded picture.

Looking through the bug reports I see there are 3 different causes for the same problem.

Sometimes the problem is caused by installing gxine. Something in the configuration files is doing it. The fix is to completely remove gxine.

sudo apt-get purge gxine

Restart X and if that was the cause your problem will be fixed without work arounds.

Paul

---

### Post by jon_herr on 2008-12-05
Use 'smplayer'

sudo apt-get install smplayer

Funny how if it's nvidias fault then it only shows up in Movie Player and not 'vlc' or 'smplayer'...  I think the problem is something else...  Anyway, smplayer works.

---

