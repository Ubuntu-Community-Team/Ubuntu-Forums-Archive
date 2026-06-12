---
title: "rhythmbox does not play flac or ogg files over daap"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by cateraut on 2006-11-03
I have a Debian server running mt-daapd and avahi to share my music. I can use Rhythmbox on my Ubuntu box to listen to mp3s over daap with no problems, but flac and ogg files do not work -- it just skips over them with the red error sign.

I can play such files locally with no problem. The daap server configuration file seems to indicate it supports streaming such files -- and it indexes them, so it seems like rhythmbox (or gstreamer?) is not interpreting something correctly.

Any ideas?

---

### Post by cateraut on 2006-11-03
According to the [bug reports for mt-daapd]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=394082"), the server is transcoding *all* files to WAV. So this is definitely a rhythmbox/gstreamer problem.

---

### Post by vegardh on 2007-02-02
Same problem here. If I check Properties for a failed file, it reads data flow error. 

Dapper. 

I _am_ able to play a flac file locally.

Any clues?

---

### Post by robwicks on 2007-03-16
I'm having the same problem. I've install every gstreamer plugin, too. I thought maybe the vorbis plugin was needed, but I still get nothing.

---

### Post by robwicks on 2007-03-16
Looks like I was wrong. I had a corrupt file. I downloaded another ogg file, and it streamed just fine. I don't know about a Windows client, though.

---

### Post by Eddy5 on 2007-11-04
I've got this issue in RhythmBox in Gutsy, streaming from Firefly. Firefly transcodes the ogg files to wavs which won't play. MP3s are fine off Firefly.
I can play wav files in RhythmBox, but for some reason they don't work off the daap server.
I get the error "Cannot determine stream type".
Does anyone have any advice?

---

