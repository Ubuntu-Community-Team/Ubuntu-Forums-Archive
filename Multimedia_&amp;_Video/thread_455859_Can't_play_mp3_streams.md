---
title: "Can't play mp3 streams"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by wootwoot123 on 2007-05-27
Hello I have Ubuntu 7.04 and installed all of the multimedia codecs using Automatix. The problem is that no matter what program I use: xmms, amarok, mplayer, xine, I am unable to play an mp3 stream. Here is the output I get from xine.

xine [http://listen.radiostation.net:8469](http://listen.radiostation.net:8469)
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  13 ()
  Serial number of failed request:  25628
  Current serial number in output stream:  25635

---

### Post by fenian on 2007-05-27
Is it just that stream you cant listen to?

can you listen to this stream (copy and paste the line into a terminal)...

mplayer [http://64.236.34.97:80/stream/1073](http://64.236.34.97:80/stream/1073)

---

### Post by lexarrow on 2007-05-27
go [here]("http://ubuntuforums.org/showthread.php?t=413626&highlight=enable+codecs") for a howto

---

### Post by jrasith on 2007-05-30
I am having the exact same problem, I have tried using gstreamer based apps with no luck, xine based players also no luck, realplayer no go, vlc is also a no go and mplayer also doesn't work... All of them are complaining about either opening or connecting to the stream... I have tried two different mp3 streams one the lounge mix from di.fm and the other is mpr.org's mp3 stream both will not work but work fine on a Windows box.

I have installed the gstreamer bad, ugly (and their multiverse counter parts), fluendo (probably spelled that wrong), the extra xine codecs. Oh, and I am using Ubuntu 7.04 on two separate machines. Anyone have any ideas?

Peace;
-Joshua

---

