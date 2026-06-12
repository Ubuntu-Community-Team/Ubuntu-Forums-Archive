---
title: "I think i lost LAME mp3"
date: 2008-12-31
forum: Multimedia Software
---

### Post by bolex100 on 2008-12-31
I can't select an MP3 option in Sound Juicer.  It used to work.  I think that installing Ubuntu Studio may have changed things.

I tried;
dave@takadhall:~$ gst-inspect-0.10 | grep mp3
mpegaudioparse:  mp3parse: MPEG1 Audio Parser
mad:  mad: mad mp3 decoder
ffmpeg:  ffdemux_mp3: FFMPEG MPEG audio demuxer
ffmpeg:  ffdec_mp3on4: FFMPEG MP3ON4 decoder
ffmpeg:  ffdec_mp3adu: FFMPEG ADU-formatted MPEG-1 layer 3 audio decoder
ffmpeg:  ffdec_mp3: FFMPEG MPEG-1 layer 3 audio decoder
typefindfunctions: audio/mpeg: mpga, mp1, mp2, mp3
typefindfunctions: application/x-id3v1: tta, flac, ogg, mpga, mp1, mp2, mp3
typefindfunctions: application/x-id3v2: tta, flac, ogg, mpga, mp1, mp2, mp3
dave@takadhall:~$ 


No LAME there.  I read a thread that suggested reinstalling 
gstreamer0.10-plugins-ugly
but no joy.  Unfortunatly while I have that installed, I can't install any other gsteamer.
help!!:confused:

---

### Post by cozmicharlie on 2008-12-31
Strange but you can install LAME from Synaptic.  Just search lame and install it.

---

### Post by wolfen69 on 2008-12-31
i got it to work by installing the *gstreamer0.10-plugins-ugly-multiverse* package in synaptic. or do ```
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

 first uninstall the gstreamer plugin you installed and do ```
sudo apt-get clean && sudo apt-get autoremove
``` then install the above package.

can't help you beyond that, except that you can try another ripping app like ripperx.

---

### Post by bolex100 on 2009-01-01
I can't see why the terminal worked where synaptic didn't.  That's exactly the gstreamer that i reinstalled in my original post.  
Thanks

---

