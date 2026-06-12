---
title: "what audio codec supports multiple audio channels."
date: 2013-05-08
forum: Multimedia Software
---

### Post by Arminius on 2013-05-08
I'm using Openshot, to create a new video file, of a movie, that incorporates multiple fan audio's.
Depending on what audio codec I use, either all 4 audio channels get compressed into 1.
Or only 1 get's used.
Just want to right click on the video, and switch between the 5 different audio tracks.
With one of course being the original audio track that came with the video.

---

### Post by SeijiSensei on 2013-05-08
What container are you writing the file to?  Matroska (.mkv) supports multiple audio tracks by default.  I've not used Openshot so I can't help with that, but if you can choose the output container, try using Matroska.

The codec itself really shouldn't matter as long as the container supports multiple tracks.

---

### Post by evilsoup on 2013-05-08
'Audio channel' normally refers to mono (1 channel) vs. stereo (2 channels) vs. surround-sound (6 or more channels), btw.

*All* modern container formats should support multiple audio tracks. I think even AVI does (don't use AVI, though; use Matroska or MP4). Maybe Openshot can't support this kind of output. Are you doing any actual editing, or just trying to stick on these extra audio tracks?

---

