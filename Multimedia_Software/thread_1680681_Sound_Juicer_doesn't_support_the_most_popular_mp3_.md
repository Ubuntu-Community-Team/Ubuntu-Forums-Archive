---
title: "Sound Juicer doesn't support the most popular mp3 tag format(?)"
date: 2011-02-02
forum: Multimedia Software
---

### Post by svref on 2011-02-02
I rip a CD with sound juicer, load the resulting files onto an MP3 player, and the player displays the song title, artist, and album all as "unknown". Analyzing the files in MP3 Diags, it complains "No ID3V2.3.0 tag found, although this is the most popular tag for storing song information". 

Grip used to just win. But Ubuntu discontinued support for it a long time ago. I still have no working replacement. :(

What's the shortest path to Do-What-I-Mean mp3 ripping?

---

### Post by svref on 2011-02-02
sudo apt-get install libgnomeui-dev libvte-dev libcurl3-openssl-dev 
Then download the grip tarball and install it from source. :P

---

### Post by samfuzz on 2011-02-03
in soudjuicer / Preferences /profiles

replace id3v2mux with id3mux in the mp3 gstreamer profile for id3v2.3 tag

eg 
preset insane  = 320 CBR :
```
audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc target=1 bitrate=320 cbr=1 ! id3mux
```

preset fast standard  ~ 190 VBR :
```
audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc quality=2 ! xingmux ! id3mux
```

more option with id3mux with :
```
gst-inspect id3mux
```
default is to write only id3v2.3 tag
but id3mux can write both id3v1.1 / (id3v2.3 or id3v2.4) tags
(see gst-inspect id3mux)

---

