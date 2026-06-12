---
title: "Audio Track Length Tag Incorrect"
date: 2008-03-27
forum: Multimedia Production
---

### Post by Oysterville on 2008-03-27
If this wasn't to achieve a childhood dream of becoming a radio personality, I would have given up long ago.  As it is, I haven't so here I go again.

I created a one hour radio show using IDJC and several audio files. The resulting file is a full hour long, and the file size goes along with that assessment. However, if I go to play the audio file in any Linux audio program (VLC, mplayer, Audacity, etc) the program gets to the end of the first song and stops, occasionally panicking because there is more data than what the track length is showing.

Is there a way to strip this track length information from the file? I even burned to audio CD and back to FLAC and have the SAME PROBLEM. It's maddening.

Thanks for any and all help you can give me.

---

### Post by StephenF on 2008-03-27
Could you upload the audio file you are having problems with to [www.rapidshare.com](www.rapidshare.com) and send me the download link via Private Message?

This will allow me to troubleshoot it.

---

### Post by Oysterville on 2008-03-28
Got the first one fixed I think by burning to audio cd and then re-encoding it.  Of course, I'd rather not do that every time so [here's a small clip]("http://rapidshare.com/files/103127570/idjc._2008-03-28__13_51_58_.01.ogg") of my next project.  Fast forward to about 04:15 (so you can ignore my amateur DJ chatter) and watch what happens in the next 15 seconds.  For me, at least, the play errors out.

---

### Post by StephenF on 2008-03-28
I have tested the file on several media players listed below.

```
Tested     |     Pass/Fail
--------------------------
mplayer            pass
audacious          pass
play (sox)         pass
ogg123             pass
idjc               pass
kaboodle           pass
noatun             pass
realplayer         pass
vlc                8/10
amarok             5/10
xine               fail
ffplay             fail
totem              fail
```

VLC inserts an audible gap between the two tracks and the seek bar misbehaves.

Amarok will play the second track when the Helix engine is selected. The Xine engine fails but then so does Xine.

Totem fails in the manner you described. I believe this is a gstreamer based media player. There is reportedly a [gstreamer update]("http://blogs.gnome.org/uraeus/2007/12/11/the-end-of-a-bug/") in the pipeline to fix this issue so maybe it will be in a software update some six months from now.

As a workaround, forget burning to a CD. To avoid the issues, try this instead (in a console):
```
oggdec -o - infile.ogg | oggenc -q 7 -o outfile.ogg -
```

Remember to change infile and outfile and choose a suitable encoding quality and it is also a good idea to record the source with a very high bitrate to reduce quality degredation from the reencode. This 'trick' requires at least oggdec version 1.2.0 in order to work.

---

