---
title: "How do I rotate a video using Ubuntu Linux?"
date: 2014-06-19
forum: Multimedia Software
---

### Post by glennbates on 2014-06-19
[   ]("https://answers.yahoo.com/activity?show=D4RDFMIIYHYSEY32NME6IZMZ2I&t=g") 

       [h=1][/h]                  
 
     I have a video that was captured with a smart phone, not a very smart  one though, but the video is sideways. How do I turn it 90 deg?

---

### Post by SeijiSensei on 2014-06-19
Do you want to create a rotated version, or just view the one you have in the proper orientation?

For viewing, I recommend SMPlayer which is in the repositories ("sudo apt-get install smplayer").  It offers rotation as one of the options in the Video menu.

For conversions, the best tools like ffmpeg run at the command prompt.

---

### Post by glennbates on 2014-06-19
I want to upload it to youtube so I need it rotated first. How do I do it?

---

### Post by FakeOutdoorsman on 2014-06-19
Use a filter in ffmpeg; you have several to choose from. I'll assume you want it 90 degrees clockwise.

[transpose](http://ffmpeg.org/ffmpeg-filters.html#transpose):
```
ffmpeg -i input -vf transpose=2 -codec:v libx264 -codec:a copy -metadata:s:v:0 rotate=0 output.mkv
```

[rotate](http://ffmpeg.org/ffmpeg-filters.html#rotate):
```
ffmpeg -i input -vf "rotate=90*PI/180:bilinear=0" -codec:v libx264 -codec:a copy -metadata:s:v:0 rotate=0 output.mkv
```
[list]
[*]In these examples the audio is being [stream copied](ffmpeg.org/ffmpeg.html#Stream-copy) (re-muxed) instead of being re-encoded.
[*]See the [FFmpeg H.264 Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264) and [FFmpeg: Encoding for YouTube](https://trac.ffmpeg.org/wiki/Encode/YouTube) for more info and suggestions.
[*]Get a recent ffmpeg build from the [FFmpeg Download](http://ffmpeg.org/download.html#LinuxBuilds) page. The counterfeit version in the repo is garbage (and was removed as of 14.04).
[*]transpose is faster than rotate, but filtering (usually) is not the bottleneck
[/list]

---

### Post by hamishmb on 2014-06-19
You could use openshot, which is installable from Ubuntu Software Centre, and can also upload to youtube.

Hamish

---

### Post by MartyBuntu on 2014-06-19
There is a ROTATE feature in Avidemux...

---

### Post by shantiq on 2014-06-22
this is what i use on ffmpeg


```
ffmpeg -i in.mp4 -vf "transpose=0" -r 30 -qscale 0 -acodec copy out.mp4

```



0 = 90CounterCLockwise and Vertical Flip (default)
1 = 90Clockwise
2 = 90CounterClockwise
3 = 90Clockwise and Vertical Flip


and if you need 180 rotation  replace  -vf "transpose=0"     with    -vf "vflip,hflip"

---

