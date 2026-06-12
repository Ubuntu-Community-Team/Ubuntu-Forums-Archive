---
title: "Problems playing xvid and some .avi files"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by Frank98 on 2007-05-29
Hi,

I followed the guide at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs) to enable multimedia playback in feisty. Some of my .avi files work except for xvid and one .avi that starts up ok but then freezes after playing 30 seconds into the movie. 

Any ideas on how to fix this is appreciated. 
Thanks

---

### Post by clay_leblanc on 2008-01-09
I'm having the same problem too!

---

### Post by eye208 on 2008-01-09
> **Frank98 said:**
> Some of my .avi files work except for xvid
Install the *gstreamer0.10-ffmpeg* package.

You see, that's why I don't like those tutorials which get passed around here. The developers have equipped Totem with automatic stream type recognition and codec download capability. It you open a file which Totem cannot play, it will make a suggestion which codec to download. There is no need to use external repositories to enable multimedia playback in Ubuntu. The only exception is libdvdcss for DVD playback which should be obtained straight from the developers' website [http://www.videolan.org/](http://www.videolan.org/). There's no need to install Windows codecs either. Windows Media 9 support was added to FFMPEG more than a year ago. But as you can see, the tutorial doesn't even mention the FFMPEG GStreamer plugin.

> and one .avi that starts up ok but then freezes after playing 30 seconds into the movie.
It's probably broken. Try playing it in MPlayer. If MPlayer can't play it, it must be broken.

---

### Post by clay_leblanc on 2008-01-09
I have tried this, to no avail.

The gstreamer is already installed....

---

### Post by eye208 on 2008-01-09
What exactly happens when you try to play an Xvid AVI? Are there any error messages? Do you experience the problem with Totem only? Do VLC and MPlayer work?

---

### Post by clay_leblanc on 2008-01-09
There are really no error messages. It doesn't even show information of the video file...

VLC and MPlayer work fine under the desktop GUI, but under the MythTV frontend it doesn't work.

All it does is list the filename, and when I try to play it, it says "loading Big Bang Theory..." for a sec, and then that disappears.

That's all it really does :(

---

