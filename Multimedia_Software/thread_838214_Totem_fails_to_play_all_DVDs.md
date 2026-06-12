---
title: "Totem fails to play all DVDs"
date: 2008-06-23
forum: Multimedia Software
---

### Post by finite9 on 2008-06-23
why does Totem not always play DVD's (either commercial or downloaded torrents), whereas VLC never has any issues?

I sometimes download a DVD torrent or play a rented DVD and the ISO/rented disc will not play in totem and it will give an Error Occurred message, but If I open the same ISO in VLC or Mplayer it works fine.  Does anyone know what the issue is?  It's certainly not all DVDs that do this, just the odd one.  Is it due to the way they were ripped or produced?

---

### Post by mc4man on 2008-06-23
> Is it due to the way they were ripped or produced? 
More than likely, if your using totem-gstreamer I'd switch to totem-xine. The gstreamer ver. is ill-suited to dvd playback
For Hardy you'd just install totem-xine and switch over with 
```
sudo update-alternatives --config totem
```
for gutsy remove totem-gstreamer and then install totem-xine

---

### Post by jualin on 2008-06-23
try this > totem-xine dvd://absolute/path/to/your/iso/file.iso. Hope this help.

---

### Post by finite9 on 2008-06-24
When I ran Dapper Drake, I remember switching between xine and gstreamer quite a bit cause I couldn't make up my mind which to use.  I seem to remember there were some drawbacks to using xine, but now it's a few years ago and I can't for the life of me remember what the drawbacks with xine were!  Are you aware of the advantages of gstreamer over xine specifically with totem?

---

### Post by gandaran on 2008-06-24
the xine engine is the best thing you can get for media play in linux today. it's superior to any gstreamer player or mplayer with it's w32codecs, xine uses both xine-ffmpeg and w32codecs for decoding, with many front-ends,  totem-xine, gxine and xine-ui, but still it's not perfect, I have a couple .avi files that only totem-gstreamer plays, can't play them on xine or mplayer!

do you have 'libdvdcss2' installed?

---

