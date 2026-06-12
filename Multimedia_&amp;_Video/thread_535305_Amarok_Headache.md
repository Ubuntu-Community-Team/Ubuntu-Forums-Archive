---
title: "Amarok Headache"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by MusicMastaMike on 2007-08-26
I have Amarok running under Ubuntu Feisty.  It had been working great, but I formatted the hdd so I could take off my Winblows partition.  I reloaded Feisty and got everything set back up.  But now, every time I open Amarok and try and play a song, 1 of 2 things will happen.  It will either freeze up trying to add it, or it will give me an error saying mp3 playback not supported.  I've rebuilt the music database several times, reinstalled Amarok, installed xine plugins for KDE, and it still does the same thing.  If it's pertinent, I have about 23000 songs, and the database is built in SQLite.  Any ideas?

---

### Post by por100pre1 on 2007-08-26
Try reviewing your [mp3 plugins]("http://ubuntuforums.org/showthread.php?t=413624"):

> 
Video/audio codec, flash, mp3, dvd playback, and win32 Codec install for Feisty Fawn for beginners. If your a new user, copy and paste commands into the terminal, should be relatively easy from that point forward.

For mp3, etc.
Open up Add/Remove programs from your Application bar.

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)

    * "GStreamer ffmpeg video plugin"
    * "GStreamer extra plugins"
    * "GStreamer plugins for aac, xvid, mpeg2, faad"
    * "GStreamer plugins for mms, wavpack, quicktime, musepack"


Then go to Other subsection of Add/Remove and find

    * "Ubuntu restricted extras"


Try some uninstalling and reinstalling of those modules if needed. :)

---

### Post by MusicMastaMike on 2007-08-26
Thanks, but all are installed and work great in other media players, such as Totem.  Is there any way to get Amarok to use the GStreamer plugins instead of the default xine?

---

### Post by MusicMastaMike on 2007-08-26
Problem solved... I had to install libxine-extracodecs. :-)

---

