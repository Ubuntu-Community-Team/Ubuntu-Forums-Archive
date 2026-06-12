---
title: "Cinelerra .avi playback error? (video/x-avi-unknown decoder)"
date: 2009-05-18
forum: Multimedia Software
---

### Post by AllTheGoodNamesAreGone on 2009-05-18
Hey all,

I just installed Cinelerra to play around with video editing (trying really hard to get off of Windows) and I rendered a small video using a tutorial found online (Akirad Project site) and when attempting to playback the rendered .avi, I get an error window attempting to find Multimedia plugins, and when I have it search for the plugin to use, it cannot find any.  Apparently Im in need of:

video/x-avi-unknown decoder

Ive tried to search online for what I might need, but Im still pretty new to Linux/Ubuntu and have no idea how to go about getting what Im looking for and then installing it properly.  Any help would be appreciated.

Thanks

Steve

---

### Post by mosestruong on 2009-10-01
Not sure if you found your solution yet, but the easiest way to play the AVI file would be to install gnome-mplayer (you can do that by running ```
sudo apt-get install gnome-mplayer
```.)


Also, if you install some codecs for gstreamer, 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-bad gstreamer0.10-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-good gstreamer0.10-ugly gstreamer0.10-ugly-multiverse
``` this would allow you to play most of the audio/video formats in the default totem player.

---

### Post by gvmax on 2010-11-20
sorry, that command did not work
could any one give the correct action

---

### Post by no2498 on 2010-11-22
open your package manager
look for gstreamer

you need the

good,bad,ugly, and 10 installed

---

### Post by luisritx on 2012-03-01
Thank you no2498 
But I still can't play .avi on my Ubuntu11.10 64bits. I have the gstreamer, vlc, good bad and ugly, gnome player, etc... I still get the

video/x-avi-unknown decoder

Anyone, please? :o

---

