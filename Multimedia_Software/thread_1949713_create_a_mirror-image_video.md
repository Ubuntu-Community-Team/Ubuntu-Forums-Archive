---
title: "create a mirror-image video"
date: 2012-03-30
forum: Multimedia Software
---

### Post by George Heine on 2012-03-30
Would like to create a mirror-image (flipped from left to right) of a video file.   I can use  

```
mplayer -vf mirror <video file>
```to play a mirror image of the file, but if I try to save it with (for example)

```
mplayer -vf mirror <video file> -dumpstream -dumpfile mirror.avi
```the result is just an identical (not flipped) copy of the original video.

Have tried this on Ubuntu 10.10 with MPlayer SVN-r1.0~rc3+svn20090426-4.4.3, also Ubuntu 11.04 with MPlayer SVN-r1.0-4.5.2.

Or am I using the wrong tool for this?  Have looked on the documentation for ffmpeg, but don't see  anything for flipping the image.   Have done a search of this forum and a general web search.  Perhaps there is something in the mplayer user archives, but they are difficult to search.

Thanks for any help.

---

### Post by Jose Catre-Vandis on 2012-03-30
You can compile ffmpeg from source, ensuring you enable the vf filters, then
```
ffmpeg -i in.avi -vf "hflip" out.avi
```

---

### Post by andrew.46 on 2012-03-30
Perhaps also use 'copy' for the audio and video codecs with Jose's commandline so you don't inherit the FFmpeg defaults.

---

### Post by Jose Catre-Vandis on 2012-03-31
That would be nice Andrew, but you have to re-encode to get the filters to work. Maybe use sameq for avi or qscale if converting mp4? Hmmm I guess it doesn't reverse the audio ;)

```
ffmpeg -i in.avi -sameq -vf "hflip" out.avi
ffmpeg -i in.mp4 -qscale 2 -vf "hflip" out.mp4
```


For completeness, here is the link to FakeOutDoorsman's wonderful guide to compiling the latest ffmpeg & h264 which includes the vf filters needed

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by George Heine on 2012-04-01
Jose and Andrew -

Well, not the simplest solution in the world, but it did work. 
I have marked this thread as "Solved'.
 
Thanks for the advice.  
Thanks also for the pointer to the thread on compiling ffmpeg with video-filter and other options enabled.

<<<<<<<<< gh >>>>>>>>>.

---

### Post by andrew.46 on 2012-04-01
> **Jose Catre-Vandis said:**
> That would be nice Andrew, but you have to re-encode to get the filters to work. 

Ooops, not the first or last time I have tendered dodgy advice :(. Apologies....

---

### Post by Jose Catre-Vandis on 2012-04-02
I did try it that way first (copy) too ;)

---

