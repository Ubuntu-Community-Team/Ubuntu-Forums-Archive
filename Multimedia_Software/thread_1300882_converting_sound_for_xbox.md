---
title: "converting sound for xbox"
date: 2009-10-25
forum: Multimedia Software
---

### Post by yester64 on 2009-10-25
Hi, i have some videos that do not play on the xbox. So i would have to change the sound codec in the file.
But how can i do that without touching the video codec?
I am not really an expert regarding converting so i am not sure how to do it. But i was trying to use ffmpeg but my results where bad as far as video goes.

---

### Post by vinutux on 2009-10-25
use handbrake x264 with mp4 container....

---

### Post by rsambuca on 2009-10-25
It would help if you provide a little more specific information regarding the files.  If you are trying to convert x264 .mkv files for the XBox 360, then you can just use Avidemux.  Copy the video, change the audio to faac (stereo), and put it in an mp4 container.

Edit:  You will also have to name it with a .mov extension for it to play on the XBox360.

---

### Post by vinutux on 2009-10-25
yueh avidemux is another good tool.... and there is aut-mode for psp ipod etc too........

---

### Post by yester64 on 2009-10-31
> **rsambuca said:**
> It would help if you provide a little more specific information regarding the files.  If you are trying to convert x264 .mkv files for the XBox 360, then you can just use Avidemux.  Copy the video, change the audio to faac (stereo), and put it in an mp4 container.

Edit:  You will also have to name it with a .mov extension for it to play on the XBox360.

My mp4 (encoded with handbrake) contain (video) H.264 / AVC and (sound) MPEG-4 AAC audio. They play fine with .mp4 extension.
No, i have some file which have a different  sound codec which can not be used (apperantly) by the xbox.
(video) DivX MS-MPEG-4 Version 3 (sound) Dolby Digital (AC-3)
Not sure which one of them does not compute with the xbox.

Avidemux looks like the tool i was looking for. thanks ! no after i switched over to 9.10 i have some soundproblems. :( but i think that was exactly the tool i needed. Have to study that. :)

Handbrake does not help in my case, since i don't have the source anymore. :(

---

