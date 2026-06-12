---
title: "totem won't play wmv, or plays with no sound"
date: 2010-05-31
forum: Multimedia Software
---

### Post by sbalfour on 2010-05-31
I'm on Kubuntu 9.10, using Totem to play .wmv files, and certain of them cause
the player to search for an audio codec (wmap?) that is never found.  The video
played without audio after that.  So I followed  advice to remove ~/.gstreamer-0.10, and reboot.  A new .gstreamer-0.10 directory appeared, but now, Totem will not even
play the video.  It recognizes the audio codec however.  The video codec shows up
as "Windows Media..." but resolution is 0 x 0, and nothing ever appears in the window.
I tried uninstalling and re-installing w32codecs and non-free-codecs, and removing
the registry files under ~/gstreamer-0.10 and using gst-inspect to rebuild the database,
but nothing helps.

---

### Post by lovinglinux on 2010-05-31
Remove totem and get gecko-mediaplayer. Is a better plugin IMO. See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

