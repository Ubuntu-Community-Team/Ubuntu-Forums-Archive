---
title: "mkvtoolnix equilivilant for avi files?"
date: 2011-04-09
forum: Multimedia Software
---

### Post by p014k on 2011-04-09
Hello, I use mkvtoolnix daily for mkv files and it works great. I would like a similar program for avi files, mainly extracting tracks and getting information about avi files.

I have tried to install Avi-Ogm[ (http://www.xwing.info/index.php?p=avi_ogminfo]("http://www.xwing.info/index.php?p=avi_ogminfo")) Info via ubuntu debian package from their website. Ubuntu's software center displays an error:  "Dependency is not satisfiable: libavcodec1d (>= 0.cvs20070307)" I tried to do ```
sudo apt-get install libavcodec1d
``` but that doesn't work because the package was not found. I did some goggling and and all the support is for older versions of ubuntu (I'm running 10.10). I figured some of the same solutions should work (adding repositories, etc) but they do not. 

How do I go about installing this, or do you guys recommend a different (preferably better) alternative?

---

### Post by andrew.46 on 2011-04-09
I suspect that mkvtoolnix is pretty unique in the linux world :). Have you thought of simply converting all your avi files to mkv using mkvtoolnix? They would certainly all import nicely using the mkvmerge gui...

---

### Post by Russell Burrows on 2012-04-19
I converted every .avi file to mkv files.

Thats what I did and let me tell ya Mosu Rocks!! with MKVToolnix its all good!

I used to be an FFMpeg adherent but now its all about MKVToolnix!!:guitar:

---

### Post by p014k on 2012-04-23
> **Russell Burrows said:**
> I converted every .avi file to mkv files.

Thats what I did and let me tell ya Mosu Rocks!! with MKVToolnix its all good!

I used to be an FFMpeg adherent but now its all about MKVToolnix!!:guitar:
What method do you use for converting from avi to mkv? And does it create separate tracks for audio, video, and subtitles (Avi hard encodes subtitles into the video, from what I recall, so I'm guessing the answer for this one would be no.)

---

### Post by FakeOutdoorsman on 2012-04-23
You can losslessly extract tracks with ffmpeg. This example assumes the input contains MP3 audio:
```
ffmpeg -i input.avi -c:a copy output.mp3
```
Same as above but with older syntax:
```
ffmpeg -i input.avi -acodec copy output.mp3
```
To get information on an input:
```
ffmpeg -i input.avi
```
To copy all input streams to another container:
```
ffmpeg -i input.avi -c copy output.mkv
```
Older syntax:
```
ffmpeg -i input.avi -vcodec copy -acodec copy -scodec copy output.mkv
```
If you want to do the same to a directory of inputs:
```
mkdir outputdir
for input in *.avi; do ffmpeg -i "$input" -c copy outputdir/"${input%.avi}.mkv"; done
```
This should make mkv files from all avi inputs in the current directory (I didn't test it, so forgive any typos).

---

