---
title: "kdenlive crashes, produces asynced audio/video, etc"
date: 2009-10-05
forum: Multimedia Software
---

### Post by barna on 2009-10-05
Hi,
I have been using cinelerra for a while, not being too happy with it, and when I lost several days' work when it kept crashing during rendering, I decided to never start this program again.
I gave a trial to kdenlive with ubuntu-9.10 alpha. It started up, it imported the AVI files from a Nikon-D90 camera (HD, mjpeg), and rendered it to different output formats. I did not check the online playback, etc, because I only wanted to make a fadein/fadeout + crossfade effects at clip boundaries. Rendered output was perfect.
Now I made an update of the packages, and
- kdenlive crashes 50% of the time when I open a project file
- it crashes if I change the project setting (movie size)
- I managed to export a small clip, originally a HD AVI file from the camera, to h.264+mp3 (my own export profile derived from the official h.264 export profiles, replacing libfaac to libmp3lame, because libfaac is not available in ubuntu). It worked very nicely before the updating, but now it produces asynced audio/video.
- I have converted the original video via ffmpeg -i orig.AVI -acodec ac3 -vcodec libx264 new.mp4, and tried to use this as the input file. Although mplayer plays back this mp4 file correctly, kdenlive produces a chirping audio on the online playback, and also in the rendered file.

I give up. If one wants to make video editing (even the simplest things), I think there is no other way than buying a commercial product, which works. 

Ok, I know that 9.10 is still in beta, but I am not too optimistic, to be honest.

---

### Post by barna on 2009-10-05
The audio/video async occurs when I crop my clip at the beginning. If I export the whole clip, the audio/video is in sync.

---

### Post by barna on 2009-10-05
If I first convert the original file to DVD format, then trim the clip, and export, then I have no audio/video async.
Why? I do not want to spend several hours to figure out, which input formats will produce correct output. DVD is not the highest resolution. In this specific simple case it was sufficient for me, but if I want to make something more serious in the future, what input format should I use to avoid the async problem? Why does it occur at all?

---

