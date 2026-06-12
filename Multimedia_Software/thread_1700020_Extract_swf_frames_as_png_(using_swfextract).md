---
title: "Extract swf frames as png (using swfextract?)"
date: 2011-03-04
forum: Multimedia Software
---

### Post by DrPL on 2011-03-04
Hi,
This has me flummoxed! Hopefully someone can help.

I saw a nice swf movie of a candle the other day ( [http://www.youtube.com/watch?v=8kl5Yf-rHtI&feature=related](http://www.youtube.com/watch?v=8kl5Yf-rHtI&feature=related) ) and would like pngs of the movie. I have tried
swfextract but I get the following info:

Objects in file candle3.swf:
 [-i] 67 Shapes: ID(s) 1, 2, 4, 6, 9, 13, 15, 17, 19, 21, 23, 25, 27, 29, 30, 33, 34, 37, 39, 40, 43, 45, 47, 49, 51, 53, 55, 56, 59-63, 65, 66, 69, 70, 73, 75, 77, 78, 81, 82, 85, 86, 89, 90, 94, 96, 97, 101, 103, 106, 108, 110, 112, 116, 118, 120-123, 125, 127, 129, 131, 133
 [-i] 60 MovieClips: ID(s) 3, 5, 7, 8, 10-12, 14, 16, 18, 20, 22, 24, 26, 28, 31, 32, 35, 36, 38, 41, 42, 44, 46, 48, 50, 52, 54, 57, 58, 64, 67, 68, 71, 72, 74, 76, 79, 80, 83, 84, 87, 93, 100, 104, 107, 109, 111, 113-115, 117, 119, 124, 126, 128, 130, 132, 134, 137
 [-p] 1 PNG: ID(s) 135
 [-f] 1 Frame: ID(s) 0

- I have tried using the png ID to try and extract the frames but this didn't work (looking at the code, its clear that the movie is made up of individual objects and not individual frames). I am at a loss as to what to do next! A very long winded solution would be to record the file as it plays using something like recorditnow and then convert the resulant .ogv/.ogg file to png files using something like ffmpeg, but this seems very laborious.
Is there a simple way?

Best wishes

Paul

---

### Post by ron999 on 2011-03-04
Hi
I suppose you could download the video from YouTube then create png files like this:-
```
ffmpeg -i *[COLOR="Red"]filename[/COLOR]* f%d.png
```

---

### Post by DrPL on 2011-03-04
I've tried that but ffmpeg doesn't recognise swf file formats.

---

### Post by ron999 on 2011-03-04
> **DrPL said:**
> I've tried that but ffmpeg doesn't recognise swf file formats.
The videos on YouTube don't use swf format.

---

### Post by DrPL on 2011-03-04
I'm suing a video downloader (firefox plugin) and swf is the only file format provided.

---

### Post by ron999 on 2011-03-04
> **DrPL said:**
> I'm suing a video downloader (firefox plugin) and swf is the only file format provided.

Hi
Try **youtube-dl** instead.
Like this:-
Install it.
```
sudo apt-get install youtube-dl
```
Update it.
```
sudo youtube-dl -U 
```
Download candle.flv.
```
youtube-dl -o candle.flv "http://www.youtube.com/watch?v=8kl5Yf-rHtI&feature=related"
```
Make png files.
```
ffmpeg -i candle.flv f%d.png
```

---

### Post by DrPL on 2011-03-04
Thank you, it works! (Had to update it twice for some bizarre reason, but many thanks!)

---

