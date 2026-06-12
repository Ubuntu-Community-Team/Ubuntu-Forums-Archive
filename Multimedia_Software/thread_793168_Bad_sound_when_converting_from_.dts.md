---
title: "Bad sound when converting from .dts"
date: 2008-05-13
forum: Multimedia Software
---

### Post by BeholdMyGlory on 2008-05-13
I've got a movie(Matroska Video, .mkv) with audio encoded wth dts, but I want to edit the movie with Avidemux, but when I try to open the movie, Avidemux complains about not being able to find a suitable codec, or something like that.
I tried searching the web and found that Avidemux don't support dts audio in a .mkv container.
So, I need to encode it to something else, such as AAC, but I can't get it to work. So, again I searched the web, and found a guide:
> 1)Convert the audio in the movie in WAV PCM:
nice -n 10 mencoder input_video.avi -oac pcm -ovc copy -o output_movie.avi
2)Extract the WAV file from the new AVI:
nice -n 10 ffmpeg -i output_movie.avi -acodec copy movie_audio.wav
3)Convert the WAV to AC3 Stereo
nice -n 10 ffmpeg -i movie_audio.wav -ac 2 -ab 192 -ar 48000 audio.ac3
Only problem here is that when doing the second step, i get really terrible audio. Kind of a small clicking sound every 1 or 2 seconds (there's probably a word for it, but my english is far from perfect).
The file output_movie.avi in step 1 doesn't have this problem, and plays fine in for example VLC.
Anyone know what I'm doing wrong, or have another solution? (what I really want to do here, is hardcode subs inte the movie, and encode video and audio to xvid/x264 and aac, to put on my iPod. The subs is in ***/SSA)

Edit: Haha... Ubuntuforums consored a file type/codec... but hopefully you know what i mean.

---

### Post by BeholdMyGlory on 2008-05-14
I really don't like to bump threads, but alas, I need help.
Bump!

---

