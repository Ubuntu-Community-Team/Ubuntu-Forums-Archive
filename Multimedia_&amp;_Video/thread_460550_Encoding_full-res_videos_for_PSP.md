---
title: "Encoding full-res videos for PSP"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by Andrew-buntu on 2007-05-31
Using ffmpeg, I'm able to create videos for my PSP at 320x240.  But it's now possible to watch 472x240 videos (I downloaded a Syphon Filter trailer at that res) and I can't seem to get that working.  Just bumping up the resolution and encoding in mpeg4 video creates a file that the PSP says is "unsupported data".  I read that it has to be an h264 video but I had the same problem when I used that as the "vcodec".
Does anyone know how to make full-res PSP videos using Ubuntu?  I'm perfectly happy (I prefer, actually) using the command line.
I tried pspvc and successfully installed it but it just creates a thumbnail and a 0k video.  And I don't really want to reinstall it because uninstallation was a pain that required tracking down every file with "pspvc" in the title. 
Thanks for the help!

---

### Post by Andrew-buntu on 2007-06-02
Anyone?  Is my question not clear or are all the PSP users as confused by this full-resolution video thing as I am?

---

### Post by skooter on 2007-07-08
At wikipedia it says: 
"As of firmware update version 3.30, H.264/MPEG-4 AVC Main Profile video files of the following sizes can be played: 720×480, 352×480, and 480×272." ([http://en.wikipedia.org/wiki/PlayStation_Portable#Multimedia_playback](http://en.wikipedia.org/wiki/PlayStation_Portable#Multimedia_playback))
... But of cause 320x240 is still supported.

This is what i do:
```
ffmpeg -y -i /home/whatever/video/file.mpg -f psp -r 29.97 -b 384k -vcodec h264 -acodec aac -ac 2 -ar 48000 -ab 64 -s 320x240 /home/whatever/psp/file.MP4
```

... I just have a little problem getting aac-codec to work, but thats a whole other talk.

---

