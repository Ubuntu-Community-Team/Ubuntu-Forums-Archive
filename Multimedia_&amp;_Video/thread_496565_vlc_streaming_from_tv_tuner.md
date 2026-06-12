---
title: "vlc streaming from tv tuner"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by apple2_91 on 2007-07-09
Hi folks,
Yesterday I figured out how to stream from my tvtuner to a nokia 770 tablet. The problem is that the sound from the tvtuner comes from hw:1,0 so neither of the applications for watching tv has sound. One of the following fixes the sound on the particular computer:

sox -r 32000 -v 3 -w -t alsa hw:1,0 -t alsa pcm.default    or
sox -p -q -s -w -c 2 -r 48000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

But when streaming with vlc I can't think of a suitable file as audio input. It's /dev/dsp by default but it doesn't work (only video on the portable). Running sox during the streaming makes effect on the local pc but still no sound on the tablet. The biggest progress was by using /dev/dsp1 as audio device which made the local pc take out some noises but nothing on the tablet.

I was thinking about something with jack but I can't figure out what so any ideas will be highly appreciated.

---

### Post by apple2_91 on 2007-07-16
Any ideas?

---

