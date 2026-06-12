---
title: "audio manipulation software, looking for command line tools in"
date: 2019-10-17
forum: Multimedia Software
---

### Post by Skaperen on 2019-10-17
i am looking for _command line_ tools in audio manipulation software.  i have an audio file (in lossless .flac format) with a sample rate of _44100 Hz_.   i would like to "play" it (and record it to a new file) at _half speed_, including the frequency reduction, and store the result also in the same format (.flac), but without the _22050 Hz_ stepping noise that will interfere with other manipulations.  i managed to play it at a sample rate of _22050 Hz_ and that sounded like what i want.  but i don't want a _22050 Hz_ file; i want a clean _44100 Hz_ file.  so, i am looking for audio manipulation software that can do this ... without trying to keep the frequency the same.  it's like recording it on an analog reel-to-reel tape at _7.5 IPS_ and calling it _3.75 IPS_.  does anyone know of _command line_ tools that can do this?

---

### Post by uRock on 2019-10-18
Have you looked into ffmpeg? [http://muzso.hu/2015/04/25/how-to-speed-up-slow-down-an-audio-stream-with-ffmpeg](http://muzso.hu/2015/04/25/how-to-speed-up-slow-down-an-audio-stream-with-ffmpeg)

---

### Post by shantiq on 2019-12-04
[Sox]("http://sox.sourceforge.net/sox.html") often described as the Swiss-knife of audio   is the one you want here apart from/or ffmpeg

```
[COLOR=#000000][FONT=monospace]sudo apt-get install sox libsox-fmt-all[/FONT][/COLOR]
```

---

