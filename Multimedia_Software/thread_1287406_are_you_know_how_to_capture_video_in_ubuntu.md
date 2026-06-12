---
title: "are you know how to capture video in ubuntu??"
date: 2009-10-10
forum: Multimedia Software
---

### Post by sandyverden on 2009-10-10
how to captute video in ubuntu for make tutorial ???

---

### Post by mikewhatever on 2009-10-10
Do you mean screen capture, in other words, record whatever happens on the screen, or video capture with a camera?

---

### Post by Captain Giraffe on 2009-10-10
I am also looking for screen capture software. video/sound capture like camtasia. Any suggestions would be welcome. 

/Captain

---

### Post by mikewhatever on 2009-10-10
> **Captain Giraffe said:**
> I am also looking for screen capture software. video/sound capture like camtasia. Any suggestions would be welcome. 

/Captain

xvidcap
gtk-recordmydesktop
istunbul

all in the repositories.

Edit: Just tested recordmydesktop, everything works, but the GUI package is gtk-recordmydesktop.

---

### Post by Captain Giraffe on 2009-10-10
Thanks Mike.

---

### Post by laceration on 2009-10-10
How about one that actually works?

---

### Post by cor2y on 2009-10-10
ffmpeg using x11grab
```
 ffmpeg -f x11grab  -s 1920x1200 -g 300 -r 30 -i :0.0 -vcodec libx264 -vpre hq -crf 22 -threads 0 recording01.mp4 
```The settings
-f = what format ffmpeg will use in this case grabbing video from the x11 display
-s = the size of your desktop resolution adjust to fit.
-g = the group of picture size i find it helps when doing x11 but not necessary
-r = frame rate 30 fps in this case but it can be adjusted to anything
-i = input/where to take the capture from in this case its the main monitor :0.0 adjust if you have more than one monitor 
-vcodec= wjhat video codec you wish to encode to in this case its x264 
-vpre= what preset if any to use with x264, hq (high quality selected) there are several
-crf = the quality of the encode/compression (since its one pass this is needed for good compression the higher the number the better the vid quality)
-threads= how many cores to use while encoding important if you have a multicore cpu (0 means to use all available cores)
recording01.mp4= what the capture is saved as you can use any container providied it can support the video codec you encode with so this could have been a mkv/avi/ogm container.

Finally to give the capture some polish and reduce the resolution (the video will be captured in the size of your desktop resolution) use either kdenlive/cinelerra/openmovie editor/Lives (to add transitions/effects/audio voice over/soundtrack) or avidemux/mencoder/ffmpeg (to just resize and or add an audio track)

---

### Post by laceration on 2009-10-10
Much appreciated Cor2y, I'll try using ffmpeg using your guide.  Of the 3 programs suggested above only recordMyDesktop sort-of works.

---

### Post by mikewhatever on 2009-10-10
> **laceration said:**
> How about one that actually works?

It does, check out the link.
[http://www.sendspace.com/file/lu5e9d](http://www.sendspace.com/file/lu5e9d)

---

### Post by sdowney717 on 2009-10-10
is this using a camera?
look into using  vlc?

[http://ubuntuforums.org/showthread.php?t=143732](http://ubuntuforums.org/showthread.php?t=143732)

use open capture device
figure out what device your camera is

then when it is showing the video, right click view select advanced controls and you get a red record button. click it and it records mpg into your home folder.

I currently can capture video and sound from an adaptec avc-2010 off any tv camcorder video

(note with vlc 1.0.2 i have to run from terminal vlc /dev/video0 to open the stream) vlc1.0.1 i can use vlc menus open capture device

---

### Post by FakeOutdoorsman on 2009-10-10
> **cor2y said:**
> ffmpeg using x11grab
```
 ffmpeg -f x11grab  -s 1920x1200 -g 300 -r 30 -i :0.0 -vcodec libx264 -vpre hq -crf 22 -threads 0 recording01.mp4 
```
...

That FFmpeg command would require quite the computer because it would definitely be too slow for my ancient, shambling beast of a P4.  The following should be faster (command lifted from Nixie Pixel's post [Re: gtk-recordmydesktop + compiz cube effects = severe tearing](http://ubuntuforums.org/showpost.php?p=7437652&postcount=21)):

```
ffmpeg -r 30 -s 1680x1050 -f x11grab -i :0.0 -g 300 -threads 0 -vcodec libx264 -vpre fastfirstpass -vpre baseline -sc_threshold -1 -cqp 22 -flags -loop screencapture.mp4
```

It could make a fairly large file but it would allow a faster capture.  You can then take this output and re-encode it later to make it a more manageable size using a command similar to your example:

```
ffmpeg -i screencapture.mp4 -vcodec libx264 -vpre hq -crf 22 -threads 0 screencapture_reencode.mp4
```

---

