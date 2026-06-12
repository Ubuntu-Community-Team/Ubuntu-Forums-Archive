---
title: "MP4Box Hinting H264 &amp; DSS Problems"
date: 2009-05-06
forum: Multimedia Software
---

### Post by tkdiamond08 on 2009-05-06
Hey all,

I seem to be having some issues hinting an h264 MP4 file using MP4Box, I'm not exactly sure if I'm doing everything correctly, but i convert an mkv file using ffmpeg and it works perfectly. However when I use MP4Box to hint the file for streaming and place it in the correct folder for streaming with darwin, and open the stream on another computer, the video freezes up every few seconds and then plays all pixelated and blocky, and without audio. I have been able to successfully convert and then hint and play other non high def videos, but it doesn't seem to be working with this one.

I'm not sure what the culprit would be, MP4Box or Darwin

however, when hinting there seems to be a little warning/error message that I don't get hinting other videos, which I have searched up but led to no where. Here's the output:

MP4Box -hint file.mp4
Hinting file with Path-MTU 1450 Bytes
Hinting track ID 1 - Type "mp4v:mp4v" (MP4V-ES) - BW 5327 kbps
**[ODF] Error reading descriptor (tag 6 size 16): Invalid MPEG-4 Descriptor**
Hinting track ID 2 - Type "mp4a:mp4a" (mpeg4-generic) - BW 193 kbps
Saving file.mp4: 0.500 secs Interleaving    

Anyone know what might be going on?

Sorry for the wall of text, and thanks in advance

---

### Post by tkdiamond08 on 2009-05-07
Update: It's also possible that our school network is too slow to process the high def movies with no delay, and after further investigation the sound will play on other computers running ubuntu with vlc, however on the windows machines the sound with both vlc and quicktime don't work.
 
Any ideas why the sound would be working on vlc running on ubuntu, but not while running on windows?
 
thanks

---

