---
title: "VLC - .flv video works, but no sound"
date: 2008-04-26
forum: Multimedia Software
---

### Post by enixexpo on 2008-04-26
I have installed VLC through Synaptic, using ubuntu 8.04, and when I play an '.flv' file it plays video but not the sound.

I have tried using this code:

```
sudo apt-get install vlc-plugin-*
```

to install all plugins, but there is still no sound.

I tried looking into audio settings, but not exactly sure what output audio device to select/input.

I already searched the forums and google, but couldn't find a solution that worked for me. 

Any other ideas to get this to work?

---

### Post by technotika on 2008-05-01
hi m8 i just had that and went into the codec section of pref and saw ffmeg codec and just ticked everything. It worked!!

I tried to undo my steps bit by bit to see which tick did it  but cant seem to find what did it.

Let me know!!!

---

### Post by Bubba64 on 2008-05-01
Ubuntu restricted in add remove will lhelp all around and the gstreamer sets. There is also a gstreamer ffmpeg there to. I always install these sets from add remove rather than synaptic, I suspect you get more stuff this way, but I don't really know other than I have never had a problem by doing it this way, it's much faster than hunting and pecking through synaptic. The terminal will do the same basic thing I believe.

---

### Post by pd0x on 2008-08-27
Thanks technotika. I was having the same issue. I went to Miscellaneous->Preferences->Input/Codecs->Other Codecs.  Ticked the two 'hurry up' options under FFmpeg without using the advanced options and all my .flv files are playing with sound!

---

