---
title: "desktop video capture fails on sound card detect"
date: 2009-04-25
forum: Multimedia Software
---

### Post by bootdoc on 2009-04-25
I have trying to make a howto video using xvidcap, istanbul, and recordMyDesktop.  All fail on opening sound card.

xvidcap gives:
xtoffmpeg.c add_audio_stream(): error opening input file /dev/dsp: -2
Segmentation fault

gtkrecordMyDesktop crash.log:
Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device

recordMyDesktop has exited with staus:768
could not open/configure soundcard.

istanbul hangs, terminal output:
DEBUG: final pipeline: oggmux name=mux ! filesink location=/tmp/tmpGwUsTk istximagesrc name=videosource display-name=:20.0 screen-num=0 ! video/x-raw-rgb,framerate=10/1 ! videorate ! ffmpegcolorspace ! videoscale method=1 ! video/x-raw-yuv,width=720,height=450,framerate=10/1 ! theoraenc ! queue ! mux. gconfaudiosrc name=audiosource ! audioconvert ! vorbisenc ! queue ! mux.

---

