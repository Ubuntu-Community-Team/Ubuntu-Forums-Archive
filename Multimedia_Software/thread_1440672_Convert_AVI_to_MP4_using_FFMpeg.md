---
title: "Convert AVI to MP4 using FFMpeg"
date: 2010-03-27
forum: Multimedia Software
---

### Post by Sir Pepps on 2010-03-27
Hi Guys

Im new to linux and really enjoying it after being a Windows user for over 10 years!

I would like to convert an avi file into mp4.  I've downloaded FFmpeg.
Could anyone provide me with step by step instructions or a link on how to complete this task? As i am clueless to how the command lines work!

Regards

---

### Post by ron999 on 2010-03-27
Hi
Think about installing Handbrake.
This uses ffmpeg to make mp4 files with mpeg-4 or h264 codecs.
Look here:-[http://handbrake.fr/]("http://handbrake.fr/")

---

### Post by 2hot6ft2 on 2010-03-27
If you want it you can add it from it's PPA like this:

Installing handbrake in 9.10
Open a terminal
Applications > Accessories > Terminal
and run these one at a time
```
sudo add-apt-repository ppa:handbrake-ubuntu/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install handbrake-gtk
```
:popcorn:

There's also avidemux
Info from Synaptic Package Manager
> Avidemux is a free video editor designed for simple cutting, filtering and
encoding tasks. It supports many file types, including AVI, DVD compatible
MPEG files, MP4 and ASF, using a variety of codecs. Tasks can be automated
using projects, job queue and powerful scripting capabilities.
You can install it either by searching for it in
System > Administration > Synaptic Package Manager
or by using
```
sudo apt-get install avidemux
```

---

### Post by FakeOutdoorsman on 2010-03-28
If you don't mind the command-line, see some MP4 encoding examples here:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Fenris_rising on 2010-03-28
Sound convertor works as well though I am now trying Mobile Media Convertor as the resultant files I changed from MP4b to MP3 when played had a progress bar/time that didn't work true and the end of the files where 'clipped'. MMC seems to be doing the job well though so far.

regards

Fenris

---

