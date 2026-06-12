---
title: "Problem playing 5.1 sound"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by digTro on 2006-11-11
While I was playing around with sound settings I somehow borked 5.1 sound output. When I try to play an AC3 encoded movie, Totem refuses to play saying audio device is busy (but it happily plays movies with stereo soundtrack). I followed this sticky  [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") and purged alsa and reinstalled it again, but the problem still persists. I'm able to play all other sounds. The problem is only with 5.1 encoded soundtracks.

---

### Post by digTro on 2006-11-18
The problem was solved by deleting the .asoundrc and .asoundrc.asoundconf files from my home directory as mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=204030]("http://ubuntuforums.org/showthread.php?t=204030").

---

### Post by bettola on 2007-03-07
The problem is not solved...thoose file are the settings to set my usb sound card...if I delete them, sound output become laptop speaker instead my 5.1 system

---

