---
title: "videoplayer show no picture"
date: 2010-05-13
forum: Multimedia Software
---

### Post by stn21 on 2010-05-13
Hi,

my notebook has an external monitor connected with 1280x1024 pixels.

As long as the resolution of the external monitor is set to 1024x768 I can watch video with VLC, mplayer etc.

But once I set its resolution to 1280x1024 all mediaplayer play only sound.
This happens on the external screen and on the built-in screen of the notebook.
The desktop is extended to the external screen.

Is there anything I can do about that?

THX,stn

---

### Post by stn21 on 2010-06-01
Finally found the solution.

The Intel-Drivers allow video-acceleration only up to a maximum total screen-width and -height of 2048 pixels. In my case the extended screen is 1024+1280 pixels wide. 

In that case the players don't give an error-message oder hint. Instead the video simply gets switched off.

Two possible solutions:

1) configure the external screen below or above the internal screen. Then the total height is 768+1024 pixels and the width is 1280. The video works but it can be irritating because the virtual screen-positions do not match the physical ones.

2) reconfigure the player:

* VLC, Menu  Extras/Settings/Video, in drop-down "Video-Output" select "OpenGL" or  "X11" , then restart VLC.


* Gnome  MPlayer: Menu "Settings", in drop-down "Video-Output" select "x11" or  "gl2"


* Totem-Player: did not find any of those settings.


I am not sure how the controls are called in the english versions of the players so the instructions may be inaccurate.

---

