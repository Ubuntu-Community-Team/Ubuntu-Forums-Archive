---
title: "Gstreamer plugin problems"
date: 2009-12-20
forum: Multimedia Software
---

### Post by BabyTom219 on 2009-12-20
Hey guys, I'm a bit of a linux noob compared to many of you, and ive recently installed Ubuntu Netbook Remix on my Acer Aspire One 110L.
I've been having some problems getting rhythmbox to play mp3 and aac files. It initially couldn't find the right plugin to play the files, so i manually installed the ubuntu-restricted-extras package which seemed to be the correct one. The package has installed properly as youtube and other flash things work now, but rhythmbox, movie player etc cant play anything the gstreamer plugins should support. 
Ive tried uninstalling and reinstalling various packages, but UNR locks down certain programs like vlc that i would otherwise like to use. But thats another issue.
Any help greatly appreciated

---

### Post by Yellow Pasque on 2009-12-20
Maybe some of these commands will help. Obviously, replace SOMETHING with the name of your mp3. Also, if UNR doesn't use PulseAudio, then use alsasink.

```
cd <path to your music directory>
gst-launch-0.10 filesrc location="SOMETHING.mp3" ! decodebin ! audioconvert ! audioresample ! pulsesink
```

Inspect your mp3 decoders:
```
gst-inspect-0.10 | grep mp3
```

---

### Post by BabyTom219 on 2009-12-20
I tried the commands mentioned above, it gives me:
```
tom@Tom-netbook:~/Music$ gst-launch-0.10 filesrc location="test.mp3" ! decodebin ! audioconvert ! audioresample ! pulsesink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /GstPipeline:pipeline0/GstFileSrc:filesrc0: Internal data flow error.
Additional debug info:
gstbasesrc.c(2378): gst_base_src_loop (): /GstPipeline:pipeline0/GstFileSrc:filesrc0:
streaming task paused, reason not-linked (-1)
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...
```

and
```
tom@Tom-netbook:~/Music$ gst-inspect-0.10 | grep mp3
typefindfunctions: audio/mpeg: mpga, mp1, mp2, mp3
typefindfunctions: application/x-id3v1: tta, flac, ogg, mpga, mp1, mp2, mp3
typefindfunctions: application/x-id3v2: tta, flac, ogg, mpga, mp1, mp2, mp3

```

Not really sure what that means though. Wasnt sure if it used pulseaudio so tried alsasink as well but its the same output. Does that help at all?

---

### Post by Yellow Pasque on 2009-12-20
It looks like you're missing an mp3 decoder:
```
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by BabyTom219 on 2009-12-20
That worked, thanks very much. Had to update my sources first before it would install, but seems to be all sorted now. Rhythmbox also automagically found the .aac plugin this time, so I'm thinking all I had to do was update my sources after all...
I've been using linux for almost a year now and I still feel like I hardly know anything about it :-(

---

