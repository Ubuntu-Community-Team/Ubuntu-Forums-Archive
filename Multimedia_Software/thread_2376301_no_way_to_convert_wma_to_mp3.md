---
title: "no way to convert wma to mp3"
date: 2017-11-01
forum: Multimedia Software
---

### Post by spikespapa on 2017-11-01
i have looked high and low for ways to convert my wma files to mp3. there always seems to be a plugin that isnt installed or Gstreamer isnt available or some kind of codecs arent supported . . . ALWAYS something! all i want to do is play some of my music files (songs) ,that happen to be WMA files, on Clementine. I am knowledgeable enough to ditch windows and install ubuntu on all my computers,so over time i have learned that trying to change wma files is not possible. NOT POSSIBLE!! yes,that is a challenge. thank you,    xubuntu 14.04

---

### Post by coldraven on 2017-11-01
You can play them or convert them to mp3 using VLC. I just tried both options, no problems.

---

### Post by HermanAB on 2017-11-01
That is what Sound Exchange (sox) is for.

---

### Post by ajgreeny on 2017-11-01
You can also use ffmpeg with command ```
ffmpeg -i *filename*.wma -ab 320k *filename*.mp3
``` from the folder where the wma files are sitting, but as coldraven says you should also be able to play them without converting using vlc.  You can use a different bitrate instead of the 320k I show if you prefer.

I've never used clementine but I am surprised that it's not possible to play .wma files using that; have you installed the **restricted extras** package for your *ubuntu version?

---

### Post by spikespapa on 2017-11-01
thank you very much,friends. yes i found that i can play them on VLC. i'm still working on the converting process. im sure i will figure this out if i can hold my frustration at bay.:p thanks again so much.

---

### Post by deadflowr on 2017-11-01
*Thread moved to** Multimedia Software***

---

### Post by oldos2er on 2017-11-01
If you have ffmpeg installed, there are some script suggestions here: [https://askubuntu.com/questions/508278/how-to-use-ffmpeg-to-convert-wma-to-mp3-recursively-importing-from-txt-file](https://askubuntu.com/questions/508278/how-to-use-ffmpeg-to-convert-wma-to-mp3-recursively-importing-from-txt-file)

---

### Post by ajgreeny on 2017-11-01
And to add to my post #4, the command I showed is the same as one that is incorporated in a **Custom Action** script that I use in thunar, the file manager of Xubuntu.

I can simply right click on a file or group of files which do not all need to be .wma but any audio or video files, and choose the custom action "Convert to mp3".  It may be possible to do similarly in nautilus, the Ubuntu file manager, but I do not use it so can not help with that; if you can do so it will save you a huge amount of time.

---

### Post by mc4man on 2017-11-01
> **spikespapa said:**
> i have looked high and low for ways to convert my wma files to mp3. there always seems to be a plugin that isnt installed or Gstreamer isnt available or some kind of codecs arent supported . . .   xubuntu 14.04 
The main issue there is clementine in 14.04 is old & uses gstreamer-0.10 which doesn't do wma.
If you  could upgrade to 16.04 this wouldn't be an issue or if you found a clementine ppa with a newer clementine that uses gstreamer1.0 then you'd also be ok.
1 ex. - [https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine](https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine)

---

### Post by spikespapa on 2017-11-02
sir, mc4man, that is what i have been wanting! i did a quick search of clementine upgrade and found the installation from mr davidsansome. typed it into the terminal. and everything works perfect. thanks a million. you all are the best.

---

### Post by Yellow Pasque on 2017-11-02
Please mark the thread solved (thread tools menu above the first post.)

Also be aware that xubuntu 14.04 uses avconv command (in libav-tools package) instead of ffmpeg.

---

