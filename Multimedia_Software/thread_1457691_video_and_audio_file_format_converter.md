---
title: "video and audio file format converter"
date: 2010-04-18
forum: Multimedia Software
---

### Post by real_magiz on 2010-04-18
Dear all

I would like to get one software using which we can convert one video file format to another. 
Like .mkv to .mpg  and .avi to mpg or .3gp to .avi . converting one to another.

The other software I need is about ripping and editing mp3.
From DVD video or VCD format, i would like to extract only audio mp3 files and i would like to cut some unwanted portion of those mp3 files.

Which software do I need? I dont want to install Ubuntu studio.
I now have installed Jaunty Destkop.

Big THanks
Real

---

### Post by WinterRain on 2010-04-19
> **real_magiz said:**
> Dear all

I would like to get one software using which we can convert one video file format to another. 
Like .mkv to .mpg  and .avi to mpg or .3gp to .avi . converting one to another.
Winff is good for that.
> **real_magiz said:**
> The other software I need is about ripping and editing mp3.
I like RipperX for that.
> **real_magiz said:**
> From DVD video or VCD format, i would like to extract only audio mp3 files and i would like to cut some unwanted portion of those mp3 files.
Not sure.

---

### Post by nothingspecial on 2010-04-19
ffmpeg will do everything you want but it is a command line tool

to put avi files in a format for ipod I use this

```
#!/bin/bash

#convert avi to mp4
for f in *.avi 
    do 
    ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
    -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.avi}.mp4 \
    "${f%.avi}.mp4"

done
```

That will batch covert all avi files in the current directory to mp4.

You can find the correct syntax for each operation on the internet. You can find instructions for everything you want to do [[COLOR="Red"]here[/COLOR]]("http://www.tuxradar.com/content/ffmpeg-made-easy")

Audacity is a good program for editing sound.

---

### Post by nothingspecial on 2010-04-19
> **real_magiz said:**
> Dear all

The other software I need is about ripping and editing mp3.
From DVD video or VCD format, i would like to extract only audio mp3 files 

Just found a cool tool for extracting audio from dvd

```
transcode -i /dev/dvd -x dvd -T 1,-1 -a 0 -y raw -m output.mp3
```

Put a dvd in, copy and paste that and you should end up with an mp3 file of your dvd.

Just having ago myself now.

---

### Post by pmooney78 on 2010-08-01
VLC also has a set of options to extract audio from DVDs/VCDs, and it's not a command-line tool. Go to the Media menu, and choose Convert/Save, then play with the options there. I've used it to extract music from DVDs before. It's pretty flexible.

---

