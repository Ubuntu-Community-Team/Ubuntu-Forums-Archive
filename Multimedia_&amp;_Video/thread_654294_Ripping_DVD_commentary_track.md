---
title: "Ripping DVD commentary track"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by DocForbin on 2007-12-30
Can anyone offer a how-to or some general tips/apps to use for creating an audio file from a DVD commentary track? I've tried using dvd::rip and mplayer, but can't seem to get dvd::rip to only rip the selected audio track. Any advice would be appreciated.

---

### Post by DocForbin on 2007-12-30
Also, I've tried using dvd decrypter with wine and I can create a .vob with just the commentary track (no video) on it, but haven't had any luck making a wav/ogg/whatever from that. Avidemux can't open the .vob, and when I use mplayer I get an error that it is missing the video stream.

edit: n/m, mplayer seems to be working now.

---

### Post by DocForbin on 2007-12-31
There are probably better ways, but, for the archives, here's the method I used:

**Create a VOB with the commentary track (no video) using DVD Decrypter** (requires wine)

- change the mode to IFO
- tools > settings > IFO Mode, check "Enable Stream Processing"
- click the stream processing tab, deselect all but the commentary track
- select "Demux"
- run decrypt

**Convert VOB to WAV with mplayer**

mplayer file.vob -ao pcm:file=file.wav

**Convert WAV to Vorbis**

lame -h --resample 44.1 file.wav file.ogg

---

