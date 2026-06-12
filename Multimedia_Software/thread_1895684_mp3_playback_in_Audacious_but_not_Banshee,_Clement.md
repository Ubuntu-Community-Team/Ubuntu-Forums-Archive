---
title: "mp3 playback in Audacious but not Banshee, Clementine, Rhythmbox"
date: 2011-12-15
forum: Multimedia Software
---

### Post by erchinoald on 2011-12-15
Having a weird mp3 playback issue. I'm running Lubuntu 11.10 on a Samsung NC10. Whenever I open an mp3 in Audacious, it plays just fine, but other media players are struggling for different reasons.

In Banshee, when I try and play an mp3 in the library, it tries to start playing, but is unable to, and skips to the next track. It then cycles through all the songs in a playlist or library as if it can't find the location they've been imported from. If I open an mp3 directly from file manager, it does the same - loads it but skips it as if nothing is there.

Clementine essentially does the same - loads mp3s but cannot play them.

In Rhythmbox, playing an mp3 simply closes the application abruptly. Again, this occurs regardless of whether I've queued it from the library or opened from file manager.

I feel like I'm missing something basic here, but can't work out what it is. The appropriate gstreamer codecs are all installed. Can anyone help me out?

Cheers,
Ed

---

### Post by erchinoald on 2011-12-15
Resolved: after much poking around and uninstalling/reinstalling of things, on a whim I installed 'gstreamer0.10-alsa' which for whatever reason hadn't been installed along with other gstreamer codecs. I still don't even know what ALSA is - now to find out...

---

### Post by locojets54 on 2012-02-02
thanks a lot for sharing this fix. worked for me as well.

---

### Post by timofeivitch on 2012-04-06
Thank you, It works for me too (lubuntu11.10, clementine, rhythmbox)

---

