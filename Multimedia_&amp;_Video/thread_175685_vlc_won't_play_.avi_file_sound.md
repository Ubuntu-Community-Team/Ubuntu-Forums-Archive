---
title: "vlc won't play .avi file sound"
date: 2006-05-13
forum: Multimedia &amp; Video
---

### Post by gwenbasil on 2006-05-13
> VLC media player 0.8.4-svn20040920 Janus
ICE default IO error handler doing an exit(), pid = 24089, errno = 0
[00000303] oss audio output error: cannot open audio device (/dev/dsp)
[00000303] main audio output error: couldn't find a filter for the conversion
[00000303] main audio output error: couldn't set an output pipeline
signal 2 received, terminating vlc - do it again in case it gets stuck
[00000260] main playlist: stopping playback
[00000303] oss audio output error: cannot open audio device (/dev/dsp)
[00000303] main audio output error: couldn't find a filter for the conversion
[00000303] main audio output error: couldn't set an output pipeline
[00000260] main playlist: stopping playback


This happens when I open an .avi file with vlc. (Sound plays in none of the other programs I've tried -- mplayer, totem, kaffiene -- and it's not a problem with the file, it works fine on other computers.) I looked around for other threads for related issues, but I'm green and consequently need extra handholding... Help?

---

### Post by louis_nichols on 2006-05-13
Try enabling alsa as sound output module (Under Settings/Preferences/Audio>Output modules - making sure the advanced settings option on the lower right is checked)

If you don't have alsa in the dropdown, install the package vlc-plugin-alsa, restart vlc and try again. Choose alsa for putput for all apps, and this should ensure sound for them.

---

### Post by gwenbasil on 2006-05-13
worked! Thanks very much.

---

