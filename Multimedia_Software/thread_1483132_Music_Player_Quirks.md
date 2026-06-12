---
title: "Music Player Quirks"
date: 2010-05-14
forum: Multimedia Software
---

### Post by adam22 on 2010-05-14
When I open Banshee and play a song, it will skip a few times during the song.

When I play a song in R-Box it plays fine, but when it first opens it tries to search for a suitable plugin.

I have the mediubuntu repo added, and it's 64 bit 10.04. Any ideas? I'm mostly interested in fixing Banshee.

---

### Post by adam22 on 2010-05-14
Anyone?

---

### Post by boombox1387 on 2010-05-26
Hmm, that's strange.  There are a couple of things to look at, if you want to get the Banshee issue straightened out:

First of all, what type of audio are you trying to play?  Does the problem happen with mp3, ogg (or oga), and flac?  If you could test all three, that might be useful.

Which gstreamer plugins do you have installed (sorry, I don't remember what comes with Medibuntu).  Since Banshee's playback is bad and Rhythmbox thinks a codec is missing, you might want to look in Synaptic and make sure that you have the gstreamer -good, -bad, and -ugly plugins installed, especially if this problem happens with mp3s. 

If you're lucky, you might get some useful information if you run Banshee from terminal with the debug option:
```
banshee --debug
```

Watch the console for output when you're playing music.  With any luck, a warning or error will show up in the log.  That will give us some major clues as to the cause of the problem.  If you want, you can post the log here and I'll take a look at it too.

---

