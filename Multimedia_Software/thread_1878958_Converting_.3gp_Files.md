---
title: "Converting .3gp Files"
date: 2011-11-10
forum: Multimedia Software
---

### Post by twistedcynical on 2011-11-10
I know this has been addressed but I still can't seem to get it to work. I have an audio file in .3pg format and I'd like to be able to listen to it from my laptop. Unfortunately, I can't seem to convert it. I've tried using avidemux but the only instructions I can find are more than a few years old and I'm afraid I'm doing it wrong. 
Anyone have an updated link? Or just good instructions? 

Many thanks for any and all help!

---

### Post by andrew.46 on 2011-11-11
With 3gp files you usually have either amr or aac sound and to tell the truth both should be able to be played on an Ubuntu installation without too much hassle and without the need for conversion.

Perhaps you could try with MPlayer and SMPlayer? Paste the following into a terminal window:

```
sudo apt-get install mplayer smplayer libavcodec-extra-53
```

and then try the files with SMPlayer?

---

### Post by davdo2004 on 2011-11-11
Try Mobile Media Converter. Real easy, drop the .3gp file in the gui and choose the output format.
[http://www.miksoft.net/mobileMediaConverterDown.htm](http://www.miksoft.net/mobileMediaConverterDown.htm)
Scroll down to the bottom of the page and click on ubuntu linux. You will need to also have mencoder installed.

---

