---
title: "Rotating Output"
date: 2011-01-14
forum: Multimedia Software
---

### Post by Geffers on 2011-01-14
Embarrassingly I have had to use Windows Movie Maker to rotate a video by 270 so that it displays correctly on screen.

Is there an ffmpeg command to do this as naturally I would prefer to do this under Linux.

Geffers

---

### Post by ron999 on 2011-01-14
Hi
Check to see if your version of ffmpeg has the 'transpose' filter included.
Use command:-
```
ffmpeg -filters
```
If it's there on the list you can use a command like this:-
```
ffmpeg -i *filename* -vf transpose=2 *newfilename*
```

270 degrees clockwise is same as 90 degrees anticlockwise.
The information is here:- [http://www.ffmpeg.org/ffmpeg-doc.html#SEC93]("http://www.ffmpeg.org/ffmpeg-doc.html#SEC93")

---

### Post by FakeOutdoorsman on 2011-01-14
As of Ubuntu Maverick Meerkat 10.10 FFmpeg from the repository does not have any filters enabled, so if you want to use *transpose* as ron999 shows you'll need to compile FFmpeg. Not hard to do with this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Geffers on 2011-01-16
> **ron999 said:**
> Hi
Check to see if your version of ffmpeg has the 'transpose' filter included.
Use command:-
```
ffmpeg -filters
```
If it's there on the list you can use a command like this:-
```
ffmpeg -i *filename* -vf transpose=2 *newfilename*
```

270 degrees clockwise is same as 90 degrees anticlockwise.
The information is here:- [http://www.ffmpeg.org/ffmpeg-doc.html#SEC93]("http://www.ffmpeg.org/ffmpeg-doc.html#SEC93")

Thanks, that worked fine though I used transpose=1, 2 turned it upright but mirrored my file.

Geffers

---

### Post by Geffers on 2011-01-16
> **FakeOutdoorsman said:**
> As of Ubuntu Maverick Meerkat 10.10 FFmpeg from the repository does not have any filters enabled, so if you want to use *transpose* as ron999 shows you'll need to compile FFmpeg. Not hard to do with this guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

How do you know all that, it worked a dream but took longer than my initial installation.

Thanks for the info.

Geffers

---

