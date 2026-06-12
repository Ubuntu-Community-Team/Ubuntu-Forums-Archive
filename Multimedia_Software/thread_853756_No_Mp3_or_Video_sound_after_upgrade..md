---
title: "No Mp3 or Video sound after upgrade."
date: 2008-07-08
forum: Multimedia Software
---

### Post by Stelmate on 2008-07-08
After I upgraded to 8.04 I no longer get any sound when trying to play video or audio files. I do however get sound when using firefox and playing mp3s from the command line with mpg321. Audio doesn't work with totem,vlc, or xine (I'm using totem-xine, but totem-gstreamer doesn't work either) It is very strange. I tried all my alsamixer settings and reinstalling everything alsa related and the restricted-extras package but nothing works! Any ideas?

---

### Post by stats on 2008-07-09
make sure those program are using alsa. goto their options->audio settings and make sure its alsa. alsa have a look at system->preferences->sound, default audio devices.

---

### Post by Stelmate on 2008-07-09
I tried that, the test work fine in Preferences->Audio and I actually hear a beep. Just no sound in xine/totem.

---

