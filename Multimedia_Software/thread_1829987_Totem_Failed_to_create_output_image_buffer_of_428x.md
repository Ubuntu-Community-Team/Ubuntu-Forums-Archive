---
title: "Totem: Failed to create output image buffer of 428x240 pixels"
date: 2011-08-21
forum: Multimedia Software
---

### Post by mikewhatever on 2011-08-21
It's been about a year since I first saw that error, perhaps more, because it might have started in Karmic, and now in Lucid. It happens when I try playing vedeo files of all kinds - FLVs, AVIs, MP4s, but not all. Istead of starting to play the video, Totem pops up a notification box saying "Failed to create output image buffer of YYYxYYY pixels
". Other players like mplayer or VLC don't have that problem.
Does anyone have a fix?

If I try launching Totem from a terminal, the output is this:
> (totem:14978): GLib-GObject-WARNING **: IA__g_object_set_valist: object class `GstPlayBin2' has no property named `queue-threshold'
** Message: Error: Failed to create output image buffer of 428x240 pixels
xvimagesink.c(2384): gst_xvimagesink_show_frame (): /GstPlayBin2:play/GstPlaySink:playsink0/GstBin:vbin/GstGConfVideoSink:video-sink/GstBin:bin0/GstAutoVideoSink:autovideosink0/GstXvImageSink:autovideosink0-actual-sink-xvimage:
XServer allocated buffer size did not match input buffer


Some shady web sources suggest changing the values of kernel.shmmax and kernel.shmall, which I tried, but the problem remains.

```
kernel.shmmax=67108864
kernel.shmall=32768

```

Edit: I should probably provide some info on the videos. Well, here is the output of 'ffmpeg -i':
> Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 23.00 (23/1)
Input #0, flv, from 'video.flv':
  Metadata:
    metadatacreator : Yet Another Metadata Injector for FLV - Version 1.5
    hasKeyframes    : true
    hasVideo        : true
    hasAudio        : true
    hasMetadata     : true
    canSeekToEnd    : false
    duration        : 2095
    datasize        : 206640683
    videosize       : 188404130
    videocodecid    : 2
    width           : 428
    height          : 240
    framerate       : 23
    videodatarate   : 701
    audiosize       : 17723005
    audiocodecid    : 2
    audiosamplerate : 44100
    audiosamplesize : 16
    stereo          : true
    audiodatarate   : 63
    filesize        : 206713692
    lasttimestamp   : 2095
    lastkeyframetimestamp: 2095
    lastkeyframelocation: 206707051
  Duration: 00:34:55.04, start: 0.000000, bitrate: 781 kb/s
    Stream #0.0: Video: flv, yuv420p, 428x240, 717 kb/s, 23 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16, 64 kb/s
At least one output file must be specified


Since no one is ever going to read this far, I'll mention that August has been surprisingly bearable this year.

---

