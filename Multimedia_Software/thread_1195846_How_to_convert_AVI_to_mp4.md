---
title: "How to convert AVI to mp4"
date: 2009-06-24
forum: Multimedia Software
---

### Post by Mouseball on 2009-06-24
My knowledge of codecs is shaky at best, but what i need to do is have a particular video file be "H.264, MPEG-4 in .mp4, .m4v, or .mov"
I tried using WinFF, this gave me this error in a terminal window

[spoiler]
[NULL @ 0x9d8cd70]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/home/m0use/Videos/Paternity.avi':
  Duration: 00:43:12.34, start: 0.000000, bitrate: 1132 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 96 kb/s
Unknown encoder 'libx264'
[/spoiler]

I found mplayer and mencode, and after a very painful RTFM session wound up with this

[spoiler]
mencoder input.avi -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -oac copy -o /dev/null
mencoder input.avi -ovc lavc -lavcopts vcodec=mpeg4:mbd=2:trell:vpass=2 \
    -oac copy -o output.mp4
[/spoiler]

This is now running, it finished the first command but the second says it will take somewhere in the neighborhood of 5 hours.

Is there a simpler way for me to do this?

---

### Post by snek on 2009-06-24
Have a look at the program AviDemux. It's quite easy to use but also has quite advanced options if you want to get your hands dirty.

I just recently used it to transcode .divx files to .mp4 for my mobile and it did a splendid job!

It should be in the normal repositories so you can use Synaptic to install or do a simple
```

sudo aptitude install avidemux

```

Hope this helps :)

---

### Post by Noo on 2009-06-24
For h.264 you should use x264 (it's usually compiled into mencoder). I would also recommend using mp4box for multiplexing the video and the audio and run mencoder separately for audio and video.

for the video you use something like this (feel free to play around with the video parameters), it's currently set for quad core multithreading:
```

mencoder input.avi -vf harddup -oac pcm -ovc x264 -x264encopts bitrate=1132:frameref=5:bframes=5:b_pyramid:cabac:direct_pred=auto:weight_b:partitions=all:8x8dct:me=umh:merange=16:subq=6:chroma_me:mixed_refs:brdo:bime:trellis=2:fast_pskip:dct_decimate:nr=0:threads=4  -of rawvideo -o rawvidoutput.264

```

extract the audio stream out of the avi:
```

mencoder input.avi -novideo -oac copy -of rawaudio -o audio.mp3

```

multiplex audio and video into one file:
```

mp4box -add rawvidoutput.264#video:fps=23.976 -nodrop output.mp4
mp4box -add audio.mp3#audio -nodrop output.mp4

```

and yes, this process takes a long time!

---

### Post by paul.gevers on 2009-06-25
> **Mouseball said:**
> 
Unknown encoder 'libx264'


You need libavcodec-unstripped-52 to have libx264 work.

---

