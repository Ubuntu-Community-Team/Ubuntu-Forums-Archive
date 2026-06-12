---
title: "[SOLVED] VLC lags and hiccups on 8.04"
date: 2008-06-27
forum: Multimedia Software
---

### Post by kriukov on 2008-06-27
I decided to upgrade from Ubuntu 6.06 to 8.04; among many improvements I found those which were worth upgrading. (By upgrade I mean a fresh installation of the newer version.) However, VLC, which I use for virtually any type of media, does not work well on 8.04. Any file, even a small sound file, hiccups and lags in it. All other players seem to play well, but I would like to use VLC. Should I try an earlier version of VLC or compile from the source or just change the settings? This problem seems to persist as I tested it on another installation of Hardy and it was the same.

---

### Post by markbuntu on 2008-06-27
Try changing the audio and video output modules in vlc.../Settings/Preferences. Be prepared for crashes though because some changes will crash your system when vlc tries to use them. Also, and safer so try this first, change your desktop visual effects to none before using vlc.

---

### Post by kriukov on 2008-06-28
Tried that, but with no result. I think it is an audio problem because videos play smoothly but the sound hiccups just like in sound files. I don't ever use any desktop visual effects, and I did not observe any crashes; in fact, changing the settings did nothing. I still don't want to switch to a different player.

---

### Post by markola on 2008-06-28
I tried VLC when I first installed Ubuntu 8.04, switched to totem based on xine which seems to work with everything.

---

### Post by markbuntu on 2008-06-28
There is a fix for stuttering audio somewhere around here either at the top of the Multimedia and Video Forum or in the Tutorial and Tips Forum under Pulseaudio something or other. I remember reading about it in one of those.

OK, I found it for you:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by kriukov on 2008-06-29
markbuntu, thank you very much. I followed the instruction and tested VLC on some of the files. The AVI movie that had a bad sound quality in VLC is now playing fine, but MP3 and OGG files stutter just like before. I wonder if it is a VLC error and if anyone else is having the same problem.

---

### Post by markbuntu on 2008-06-29
Try changing the audio output in vlc preferences to alsa or pulseaudio instead of default.

---

### Post by kriukov on 2008-06-29
markbuntu, that worked! Thank you very much.

---

### Post by markbuntu on 2008-06-30
You are entirely welcome.

Now please mark this thread as solved in the thread tools menu.

---

