---
title: "FFmpeg/alsa sound recording problem"
date: 2017-01-05
forum: Multimedia Software
---

### Post by benignindividual on 2017-01-05
I am attempting to stream audio from a webcam attached to my netbook and stream over lan using rtp via ffmpeg.

I get the error "Alsa @ 0x97be640" cannot set channel count to 2 (invalid argument) hw:1,0: input/output error"

I found this command "ffmpeg -f alsa -i hw:0 -c:a libmp3lame -ar 11025 -f rtp rtp://192.168.0.7:8099"

trying to use "hw:1,0"

as the hardware input option

"arecord -l" confirms the webcam usb audio as "card 1"



I also tried the following solution but it did not work "https://ubuntuforums.org/showthread.php?t=1649336"

---

