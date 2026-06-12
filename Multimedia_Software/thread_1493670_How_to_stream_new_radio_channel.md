---
title: "How to stream new radio channel"
date: 2010-05-26
forum: Multimedia Software
---

### Post by al_agha20 on 2010-05-26
how can i stream a new radio channel that uses mms example : mms://stream.rotanaradio.fm/rotana32

---

### Post by mc4man on 2010-05-26
You would simply use the url in a player or add a radio station to the player using the url if the player stores stations.
Ex.'s
rhythmbox - right click on radio -> new Internet radio station and paste your url in
totem - Movie -> Open location or use a .m3u
vlc - Media -> Open network stream or a .m3u
ect.

For gtstreamer players make sure these plugins are installed
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```


Some players, once the stream is opened, will have an option to 'save playlist to file', using that you can create an.m3u  (vlc, amarok, pana ect.) that you can click on to open the stream directly in default player or play.. 

Ex. of above stream (to make from here -  new text file, name rotana.m3u and paste this inside

```
#EXTM3U
#EXTINF:0,RADIO ROTANA 99.9 FM & 90.5 FM
mms://stream.rotanaradio.fm/rotana32
```

---

### Post by al_agha20 on 2010-05-26
thank you very much for the reply, it worked on totem i didn't have the plug-ins but still not working on rhythmbox

---

