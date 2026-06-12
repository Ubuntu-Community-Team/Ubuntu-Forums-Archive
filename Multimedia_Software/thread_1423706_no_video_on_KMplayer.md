---
title: "no video on KMplayer"
date: 2010-03-07
forum: Multimedia Software
---

### Post by eranga1988 on 2010-03-07
Hey guyz, I installed KMplayer but I cant play video files...No video output but can get only the audio output...So how to make this work for videos???

---

### Post by pickarooney on 2010-03-07
It could be a number of things, but start by making sure you have all he necessary 
codecs installed. 

Type this from a terminal or konsole:
> sudo apt-get install ubuntu-restricted-extras


If you're stll having no luck, try with several files from different sources to make sure it's not just the file.

---

### Post by GameOverDood on 2010-03-07
> **eranga1988 said:**
> Hey guyz, I installed KMplayer but I cant play video files...No video output but can get only the audio output...So how to make this work for videos???

Either the video is corrupted or you're missing the codecs as pickarooney mentioned. First test to see that the movie plays fine on another player like VLC Media Player. If you do, then your file is okay but you're just missing codecs or otherwise KMplayer just isn't doing its job.

---

