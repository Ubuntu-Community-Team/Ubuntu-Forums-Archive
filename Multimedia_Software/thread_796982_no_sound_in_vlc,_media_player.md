---
title: "no sound in vlc, media player"
date: 2008-05-16
forum: Multimedia Software
---

### Post by phoenix23 on 2008-05-16
Since installing Hardy, all system sounds are working. However, there is no sound in vlc or the default media player when I play any video file.

Is anyone else having a similar problem? Know of a solution?

---

### Post by mc4man on 2008-05-16
The first thing to try is go to preferences -> sound and change music and movies from auto detect to alsa. You can also make that change in vlc from settings -> prefs -> audio -> output module (enable advanced options)

---

### Post by Bubba64 on 2008-05-16
> **phoenix23 said:**
> Since installing Hardy, all system sounds are working. However, there is no sound in vlc or the default media player when I play any video file.

Is anyone else having a similar problem? Know of a solution?

Since you enabled VLC from add remove did you also add Ubuntu restricted extras and any Gstreamer stuff. I am not sure this is an answer to your problem, but will save a lot of time hunting for codecs and plugins.

---

### Post by friendofpugs on 2008-05-18
I just had this problem. I downloaded the gkstreamer codecs and I got Totem to play the DVD with sound, but VLC is still silent. Oh well, one out of two isn't bad. Download the other codecs and you should be okay.:)

---

### Post by jorge87 on 2008-05-20
I'm having the same problem here.  Everything else works fine (youtube, ubuntu sounds), but there's no sound in any of my video players.  anybody know what´s the name of the plugin that I should download? TIA

---

### Post by jorge87 on 2008-05-20
oh, and i already tried switching the audio module to ALSA (and OSS too), but that didn´t do anything.

---

### Post by jorge87 on 2008-05-20
now this is weird: i downloaded mplayer to see if it could play my videos with sound...turns out it didn´t have the codec for wmv, but it somehow made my VLC player able to play sounds :)

---

