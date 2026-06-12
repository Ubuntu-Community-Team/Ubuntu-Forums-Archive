---
title: "gxine after Gstreamer"
date: 2008-10-20
forum: Multimedia Software
---

### Post by MajinSaha on 2008-10-20
Hi, I've been using Gstreamer in my Ubuntu for a while. It seemed to work ok, I was able to watch almost all movies, except maybe some files "*.ogm". But there is a problem with playing DVDs ! Totem player says "An error occured. Could not read from the source" whenever I insert the DVD. I installed all the needed packages before that. Sometimes I can load VOB-files directly from the DVD folder, but not all of them. Anyway, I can't watch movies at this point. What could cause this problem ? I'm planning to install xine package as a solution. Will there be any conflict between xine and Gstreamer ? Is it ok to have both of them in one OS ?
I'm kinda new to Ubuntu, so I appreciate any help.
Thank you.

---

### Post by gandaran on 2008-10-20
> Will there be any conflict between xine and Gstreamer ? Is it ok to have both of them in one OS ?
no, if you install gxine, but if you install totem-xine without removing totem-gstreamer first there could be! 
you can install all the media players/codecs like totem and the gstreaner plugins/codecs, gxine or any xine based player with the libxine codecs or mplayer or mplayer clones with w32codecs or vlc which has it's own codecs
one question, have you installed all the gstreamer0-10 plugins for totem-gstreamer video and audio play? you also need to install libdvdcss2 for drm dvd protected playback 
add the medibuntu repo to get libdvdcss2 [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by MajinSaha on 2008-10-21
I installed many gstreamer 0.10 plugins from Synaptic. I don't know which ones exactly you mention. I'll do what you ask for libdvdcss2.

---

### Post by MajinSaha on 2008-10-26
I installed libdvdcss2 and DVD started working ! Thank you. But the quality of DVD movies isn't that great. While in Vista they look ok, in Ubuntu their frames vibrate sometimes. Does it mean I need Ubuntu compatible video driver or something like that ?

---

### Post by gandaran on 2008-10-26
> **MajinSaha said:**
> I installed libdvdcss2 and DVD started working ! Thank you. But the quality of DVD movies isn't that great. While in Vista they look ok, in Ubuntu their frames vibrate sometimes. Does it mean I need Ubuntu compatible video driver or something like that ?

if your media player is mplayer or vlc go to preferences video tab, change the video driver to xv, x11 or try all of them, see which one works best
don't know if gxine has that option

---

### Post by MajinSaha on 2008-10-27
I cannot play DVD with Mplayer. Only gxine and totem can do that. They don't have that option. What should I do ? I would like to make another player work since in those both I don't have an access to a needed chapter at any place but menu.

---

### Post by gandaran on 2008-10-27
mplayer needs the medibuntu **w32codecs** package to play
and try vlc player, it has it's own codecs already installed

---

### Post by MajinSaha on 2008-10-27
VLC is working with menus but the quality didn't get better even though I have w64codecs installed (because I have AMD 64 machine). I read a note on the Medibuntu site that w64codecs were actually designed for Ubuntu 7.**. Maybe that explains why the quality of the DVD video isn't great ?

---

