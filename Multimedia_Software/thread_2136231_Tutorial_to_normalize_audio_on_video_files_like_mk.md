---
title: "Tutorial to normalize audio on video files like mkv"
date: 2013-04-16
forum: Multimedia Software
---

### Post by pgainf on 2013-04-16
Greetings!

For ages I've been trying to find a way to normalize the audio on movies and videos.

Now I found a method.
I'm using Lubuntu 12.10

1. Use WinFF program to extract audio from the video file.
Settings are:
-Output details
  Convert to audio
  Preset MP3
-Audio
  Audio Channels 2

2. Use EasyMP3gain program to normalize the MP3 created before.
Settings:
Target Volume 95
And then apply track gain

3. Use Mkvmerge GUI program to join it back together to a mkv file.
On 'Input files' select the mp3 and the video file.
On 'Tracks, Chapters and Tags' deselect the unwanted AC3 or DTS audio track and select the MP3 audio.
On 'General track options' make the Mpeg layer 1 (MP3) 'default track flag' 'yes'.

4. Click Start Muxing at the bottom of the program window.
The process will take some seconds and a new video file with the suffix (1) will be created.

The sound volume now is good and Stereo. 
The voices / dialog volume will be good and no more super loud explosions when watching movies late at night.

Delete the old video file.

My regards!

---

