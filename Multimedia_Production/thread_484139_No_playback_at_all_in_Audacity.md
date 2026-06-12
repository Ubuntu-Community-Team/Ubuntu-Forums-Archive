---
title: "No playback at all in Audacity"
date: 2007-06-25
forum: Multimedia Production
---

### Post by ricardisimo on 2007-06-25
For playback I have the "ALSA: Intel ICH5: Intel ICH5 - IEC958 (hw:0,4)" device selected. I didn't select it by hand, mind you. That's just what was always selected, so far as I can tell. The graphical output meter shows a good signal, and files that I export work fine in other apps, including my mp3 player... I just can't preview anything while I'm working with it in Audacity, which is a tad unnerving. Here's my sound card:
```
Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```
Thanks in advance for any help.

P.S. - What's the difference between FLAC signed 24-bit PCM on the one hand and FLAC 16-bit on the other? Is it just a waste of disk space to select one over the other? Thanks.

---

### Post by dabl on 2007-06-26
Among other possibilities, I noticed that Firefox seems to "grab" the sound output device, and then Audacity can't play.  Try closing your browser, then run Audacity and try to play a file.

---

### Post by ricardisimo on 2007-06-27
Firefox isn't the only app with which Audacity won't share, but yeah, I already tried that. I even tried restarting the entire computer and only opening Audacity, and still no sound. I checked all of the levels in alsamixer as well. Any ideas?

---

### Post by dabl on 2007-06-27
Did you open the volume control, then go to "Edit>Preferences" and make sure all channels are enabled with a checkmark or "x" or whatever it is?  Also, look at the alsamixer gui and make sure nothing is muted that might be needed, like PCM and "front" and things like that.

---

