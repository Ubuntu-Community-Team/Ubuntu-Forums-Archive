---
title: "Pausing gstreamer playback crashes pulseaudio"
date: 2008-06-11
forum: Multimedia Software
---

### Post by bejurne on 2008-06-11
I use pulseaudio as my primary sound server. Everything works perfectly and I can see all the individual streams in pavucontrol. 

There is just one problem when pausing the playback of gstreamer applications (I tried totem and rhythmbox). After pausing the playback for longer than about 2 minutes pulseaudio crashes when I try to resume the playback. Pavucontrol says that there is no connection to the sound server and the applications will refuse to start playing. I tried restarting the sound server with "/etc/init.d/pulseaudio restart" but no joy. Restarting X solves the problem untill I pause the playback again... 

Pausing for only a couple of seconds causes no problems though. I blame gstreamer since there are no problems with audacious, mplayer or flash.

I am on Ubuntu Hardy with all the latest updates btw. My sound card is a sound blaser live 5.1 with surround output enabled.

---

### Post by wolfen69 on 2008-06-11
[THIS]("http://ubuntuforums.org/showthread.php?t=776739") should work.

---

