---
title: "Converting Ogg Video (theora) to Mpeg4 Using Gstreamer"
date: 2008-04-26
forum: Multimedia Software
---

### Post by Mr.Macdonald on 2008-04-26
I want a command line conversion of Ogg Video (theora) to Mpeg4 using Gstreamer

if someone has a python script (With commenting) that can do that i would be forever in debt.


Please respond with a working answer, because otherwise i will be digging around in Totem's nice 12.7 MB of code

Please help!!!!!!

---

### Post by rumli on 2008-04-26
Typing
```
man gst-launch-0.10
```
and scrolling down to Pipeline Examples gives some useful information.

Here's how to play an Ogg video (Theora/Vorbis):
```

gst-launch filesrc location=Kennedy_inauguration_footage.ogg ! oggdemux name=demuxer \
   demuxer. ! queue ! vorbisdec ! audioconvert ! audioresample ! osssink \
   demuxer. ! queue ! theoradec ! sdlvideosink

```

You will need to install the gstreamer0.10-sdl package to display video via SDL.

What's left is to figure out how to pipeline the audio and video and mux them into an MP4 container.


Edit:  I think I finally figured out how to do what you want.

You will need to first install some packages containing the various muxers, demuxers, encoders, and decoders:
```

sudo apt-get install gstreamer-tools gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse

```

```

gst-launch filesrc location=Kennedy_inauguration_footage.ogg ! oggdemux name=demux \
    { avimux name=mux ! filesink location=output.avi } \
    { demux. ! queue ! vorbisdec ! audioconvert ! lame ! queue ! mux. } \
    { demux. ! queue ! theoradec ! xvidenc ! mux. }

```

---

### Post by Mr.Macdonald on 2008-04-26
This is where i got stuck ... ...

I found under gst-inspect:

ffmpeg:  ffenc_mpeg4: FFMPEG MPEG-4 compatible video encoder
ffmpeg:  ffenc_mp2: FFMPEG MPEG-1 layer 2 audio encoder
ffmpeg:  ffenc_mpeg1video: FFMPEG MPEG-1 video encoder
ffmpeg:  ffenc_mpeg2video: FFMPEG MPEG-2 video encoder
lame:    lame: L.A.M.E. mp3 encoder

could any of these be useful. They all relate to MPEG

---

### Post by rumli on 2008-04-26
Try this:
```

gst-launch filesrc location=Kennedy_inauguration_footage.ogg ! oggdemux name=demux \
    { ffmux_mp4 name=mux ! filesink location=output.mp4 } \
    { demux. ! queue ! vorbisdec ! audioconvert ! faac ! queue ! mux. } \
    { demux. ! queue ! theoradec ! ffenc_mpeg4 ! mux. }

```

---

### Post by Mr.Macdonald on 2008-04-27
Kind of ... i got an output but it's audio was patchy and didn't match the video.

---

### Post by yelo3 on 2008-10-21
I'm really interested in a way to force the output file resolution to 320x200

this is my pipeline:

```
gst-launch-0.10 filesrc location="$1" ! decodebin name=demux \
{ ffmux_mp4 name=mux ! filesink location="$1".mp4 } \
{ demux. ! queue ! audioconvert ! ffenc_libfaac bitrate=96000 ! queue ! mux. } \
{ demux. ! queue ! ffenc_libx264 bitrate=500000 ! mux. }

```

maybe the decodebin for video should be attached to another sink before ffenc_libx264, but which one?
Can you help me?
thanks

---

