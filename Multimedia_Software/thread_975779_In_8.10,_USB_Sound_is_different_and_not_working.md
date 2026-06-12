---
title: "In 8.10, USB Sound is different and not working"
date: 2008-11-08
forum: Multimedia Software
---

### Post by falkaholic on 2008-11-08
After doing a fresh install of 8.10, I have found something has changed in the sound somehow.

For the past few releases of ubuntu, I've used my Griffen iMic USB sound in/out device with no problems. I plugged it in, it was recognized as a ALSA sound device, and more or less worked.

Now, it seems it shows as a ALSA and OSS (OSS listed twice) in the Sound control panel. ALSA doesn't work and the test button gives an error. Only the OSS works.

With OSS, programs don't have any sound, even if i choose OSS in their options. Apps like Amarok, Songbird, Firefox, Movie Player, Kaffine, VLC. Kaffine I finally go to play but it seems to show as muted.

I'm out of things to try, is this a bug or a feature? I want my sound back!

---

### Post by falkaholic on 2008-11-08
This tips solved it: [http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

Removing pulseaudio

---

