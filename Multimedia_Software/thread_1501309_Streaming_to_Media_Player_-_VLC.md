---
title: "Streaming to Media Player - VLC"
date: 2010-06-04
forum: Multimedia Software
---

### Post by slice16 on 2010-06-04
Hello All,

I am trying to stream a live dvb feed to windows media player on a number of desktops. I have VLC and all the codecs etc installed. 

I am starting my stream with the following command:

```
vlc -vvv tc.conf --sout '#transcode{vcodec=DIV3,vb=256,scale=1,acodec=mp3,ab=32,channels=2}:std{access=mmsh,mux=asfh,dst=:8080}
```

After vlc loads, I get the following error:

```
Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.
```

After some searching around, I found a guide on setting up ffmpeg at [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) which I have followed. I am still getting the error. 

Do I need to add any other codecs to make this work?

Thanks :)

---

### Post by ajgreeny on 2010-06-04
I do not know if this will help or not, but firstly, if you do not already have them, enable the [medibuntu]("http://www.medibuntu.org/") repos.  Then using synaptic do a name only search using the terms "libav extra".  5 packages will appear (or they should) and if you install any of those not already installed, you may be ok for your streaming.  This is because the standard dependencies of ffmpeg are for the versions of those 5 packages that are more limited than the "extra" versions.

I hope that helps.

---

### Post by slice16 on 2010-06-04
Hi ajgreeny,

Thats spot on thanks :) I am now able to stream using DIV3 and mp3. You dont happen to know how I can lower the resolution to stop the choppiness do you?

Thanks

---

### Post by ajgreeny on 2010-06-04
**System -Preferences -Monitors** should allow you to set a lower res for the monitor yopu are using.

---

### Post by slice16 on 2010-06-07
Thanks ajgreeny, I managed to keep an eye on the performance using both top and iptraf as I was connected via terminal. 

The mediabuntu repos worked a treat, and I have wrote up a swift article if anyone else is trying to do the same.

[http://paul-sanders.info/?p=50](http://paul-sanders.info/?p=50)

---

