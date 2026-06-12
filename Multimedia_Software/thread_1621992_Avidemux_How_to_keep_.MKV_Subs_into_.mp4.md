---
title: "Avidemux: How to keep .MKV Subs into .mp4?"
date: 2010-11-14
forum: Multimedia Software
---

### Post by killboymota on 2010-11-14
hello,

im trying to convert a .mkv video with subs into a .mp4 video but in the the video is ok but the subs are gone. 

Anybody knows how to do this? 
thanks in advance

---

### Post by lovinglinux on 2010-11-14
mkv subtitles are not embedded in the video stream, so you will probably need to extract them. I guess you can do that with mkvtoolnix.

---

### Post by killboymota on 2010-11-15
are you sure? i have been using PSPVC (a conversor for windows) that keeps the subtitles of mkv or any other format. 

But hey, thank you!

---

### Post by lovinglinux on 2010-11-15
> **killboymota said:**
> are you sure? i have been using PSPVC (a conversor for windows) that keeps the subtitles of mkv or any other format. 

But hey, thank you!

Yes, I'm sure. The mkv format allows to mux several audio, video and subtitle tracks, so they are not hardcoded, otherwise multiple subtitle tracks would overlap. I'm not aware of a program that can convert directly from mkv to mp4 keeping the subtitles. Perhaps mp4box.

Check this out:

[http://www.sharewareguide.net/article/Tip/mpeg-4(mp4)--how-tos.html#mp4howto2](http://www.sharewareguide.net/article/Tip/mpeg-4(mp4)--how-tos.html#mp4howto2)

---

### Post by killboymota on 2010-11-16
ok, thanks! 

I need to know more commands, how can i extract the subs with that tool?

---

### Post by lovinglinux on 2010-11-17
> **killboymota said:**
> ok, thanks! 

I need to know more commands, how can i extract the subs with that tool?

[http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvextract.html](http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvextract.html)

---

### Post by shantiq on 2010-11-17
have you tried with [handbrake]("http://handbrake.fr/downloads.php")might be able to   


[B]Also

[/B]
```
man mkvextract
``` although the instructions are far from clear


  once you have installed


```
sudo apt-get install mkvtoolnix mkvtoolnix-gui
```

---

