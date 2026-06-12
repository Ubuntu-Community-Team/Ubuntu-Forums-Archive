---
title: "Movie player glitches, closes out"
date: 2009-07-05
forum: Multimedia Software
---

### Post by br4ndonn4bors on 2009-07-05
I recently did updates and I do not know if I should rollback the updates, or if that is even possible

Before, I could play most videos with movie player. Now, when I play any extension of a video, it starts up and closes out. I have tried a different player as well, and various videos

any help would be appreciated

---

### Post by br4ndonn4bors on 2009-07-05
Thanks to a little extra research,

 Re: Video opens and immediately closes
You need to disable Xv in your video players and use X11 instead. Its a bug in your GPU drivers causing this.

To do this for each of the main media players:

Quote:
(helpful howto taken from here(clicky))
GSTREAMER:
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select X Window System (No Xv) for the plugin. Then restart Totem. This will work for any video application that uses gstreamer as it's video backend.

MPLAYER:
If you use MPlayer (GMplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select X11 (XImage/Shm)
then restart MPlayer. The issue here is that it won't go fullscreen with the video. I suggest using VLC or totem-gstreamer.

XINE:
If you use Xine then go to File -> Configure -> Preferences.
(make sure under experience_level you select Master Of The Known Universe)
You will get a tab at the top for Video. Under driver select xshm. Then restart Xine. This also works if you are using the totem-xine backend. Just run gxine at the terminal and follow the steps.

VLC:
For VLC select Settings -> Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to X11 video output. Then restart VLC

---

