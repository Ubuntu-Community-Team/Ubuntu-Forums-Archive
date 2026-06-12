---
title: "Trashed audio in editing Canon T2i video -- can't get it clean"
date: 2010-06-30
forum: Multimedia Software
---

### Post by JackD on 2010-06-30
To make a documentary of the founder of Nyumbani (you can google it if you like), I have been working with a Canon T2i. Great video. MOV files are encoded with h.264 and Linear PCM. Plays well in VLC, movie, totem, xine--everything. But, there isn't an editor that I can find that works with the file without terrible audio playback.

When I use a video editor (Openshot, Cinellera, Avidemux, and KDenLive) the video is good, but the sound is static and stutters. I've tried to extract the PCM into AC or MP3 with ffmpeg/WinFF--and what is created is an auditory copy of the same static and stuttered audio.

Why is playback fine (so, I don't have a missing library) but the editors can play the audio ? I'm on 9.10 and until the Canon MOV files, I haven't had trouble editing video.

**************************
mplayer can coax out the pcm into wav, that I can use in any NLE:

 mplayer -vc dummy -vo null -ao pcm:file=test.wav MVI_0054.MOV

---

