---
title: "ffmpeg: LPCM to AC3 problem"
date: 2008-10-13
forum: Multimedia Software
---

### Post by theirishfozz on 2008-10-13
Hi everyone.

I've been trying to use ffmpeg to convert a dvd from pal to ntsc and I've come across a problem. After fiddling for ages to even get it to convert (had to enable so many things...ugh) I found that all the menu and title videos has converted properly except for the two main menu videos (subtitles on/off videos I think). All that was there were two vob files with only the soundtrack, no video. 

I started out with a number of vob files, 3 title and 6 menu. All input vob files were mpeg2 with ac3 audio at 224kbps with the exception of the two main menu videos which were LPCM at the same sample rate (48000) but at an unknown bitrate. All the output vob files were mpeg2 with ac3 audio at 448kbps with the exception of the two main menu videos which had no video component whatsoever. 

It doesn't take a rocket-based brain surgeon to work out its something to do with LPCM. Here is the command I've been using to convert:

> ffmpeg -i vob_01m_001.vob -target ntsc-dvd -s 720x480 -r 29.970 new-vob_01m_001.vob

I understand ntsc requires at least 1 ac3 audio channel (or something to that effect, dont ask me where I heard it) so Im guessing ffmpeg is trying to convert to ac3 but..perhaps...cant convert the audio AND video in one go? Is there a way maybe..to convert just the video and then combine the processed video with the processed audio? An easier solution would be to ..perhaps define the input audio codec as LPCM but i have no idea how. The ffmpeg help page goes past the shell buffer limit. Not too sure I'll find any useful info in there.

thanks in advance.

fozz

EDIT: I discovered the same thing happens even if I don't specify framerate, resolution or target.

---

### Post by theirishfozz on 2008-10-14
I posted this as an ffmpeg bug: [https://roundup.mplayerhq.hu/roundup/ffmpeg/issue691](https://roundup.mplayerhq.hu/roundup/ffmpeg/issue691)

---

