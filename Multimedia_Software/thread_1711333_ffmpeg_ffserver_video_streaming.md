---
title: "ffmpeg ffserver video streaming"
date: 2011-03-21
forum: Multimedia Software
---

### Post by evan54 on 2011-03-21
Hi all,

the problem:

trying to stream video and audio from my video camera.

things I know:

run ffserver with some .conf file (ideally the default one?)
run ffmpeg -f video4linux <other video options> -i /dev/video0 -f alsa <other audio options> -i <audio location> [http://localhost:8090/feed1.ffm](http://localhost:8090/feed1.ffm)

things I need help with:
- editing the .conf file for the ffserver command if that is needed
- filling in the other options part as indicated above
- What to use for audio input... I saw something like /dev/dsp but this didn't work, have also used something like hw:0,0 but also didn't work.


thanks!

---

