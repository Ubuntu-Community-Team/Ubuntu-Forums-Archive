---
title: "Kdenlive without AC3 support?"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by Florib on 2008-01-06
I installed Kdenlive 0.5 from the universe repositories, and it's working fine but for one problem: Importing MPEG files from my DV camera only imports the video stream. Kdenlive does not recognize the AC3 audio stream and displays "Audio: None" in the clip properties.

There's a bug on the kdenlive bug tracker ([http://www.kdenlive.org/mantis/view.php?id=54](http://www.kdenlive.org/mantis/view.php?id=54)) where the suggested resolution is to compile ffmpeg with ac3 support (liba52). I did that, and now ffplay correctly plays video+audio, Kdenlive however still doesn't recognize the audio.

Compiling kdenlive 0.5 didn't work for me for some reason (there are thousands of linker problems). 
Compiling kdenlive 0.6 from svn worked, but the program crashes as soon as I open/load a project.

Does anyone have AC3 audio working in ubuntu's Kdenlive? How did you do it?

---

### Post by philsurette on 2008-01-13
I am having exactly the same problem with KDenLive 0.5 (package install). I have some .MOD files from my JVC Everio HDD camera. They play fine, with sound, in Totem Movie Player 2.20, which reports the .MOD files as having AC-3 Audio, stereo, 48000Hz sample rate, 384 kbps. KDenLive does not recognize the .MOD type but when I drag the .MOD files into KDenLive from the filemanager, it can play them fine but with no sound. It shows the Video codec as mpeg2video but the audio coded is empty, FPS is 0 and audio is none.

---

### Post by Florib on 2008-01-14
And I thought I was the only one... The kdenlive team has not yet responded to my bug report, unfortunately.I tried the ubuntu irc chat rooms, but nobody could help.

In the meantime, what I did was transcoding all my video to xvid with mp3 audio. I'm not happy with the solution, however. Adding more encodings to the process will only degrade my video quality, and it takes time that I'd rather spend working on the video itself.

---

### Post by daka on 2008-01-19
I want to get rid of the poor quality audio from handycam and merge quality audio from other zoom H4 recorder.  Does this mean that my JVC handycam will be ideal?  Will kdenlive allow me to merge a high quality MP3 file with the camcorder video???  (it arrives this week!!!)

daka

---

