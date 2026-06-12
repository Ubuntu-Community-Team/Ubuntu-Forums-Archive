---
title: "DVDAuthor wont write video in 16:9"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by mister_p_1998 on 2007-01-15
Hi all,
got a niggling little problem,
Ive copied a TV recording from my PVR (Topfield 5800) Demuxed it through ProjectX, made a Mpeg2 file with Avidemux, but even though I tell Avidemux the source is 16:9 and the output is 16:9, it still creates Mpeg2 in 4:3. 

What am I doing wrong?
The M2V file is in 16:9, but Avidemux keeps forcing it to 4:3, are there any other programs I can use to create an Mpeg2 from M2V and MP2 sources?

DVDauthor still creates a 4:3 movie

---

### Post by david_2001 on 2007-01-15
If you have MJPEG Tools installed from the multiverse repository then you can use mplex to mux the video and audio together in dvd format:
```
mplex -f 8 -o output_file.mpg input_file.m2v input_file.mp2
```
If that doesn't work then, don't take offense, are you certain that the video is genuine 16:9 anamorphic and not letterboxed 4:3, and is not a mixture of 4:3 and 16:9?  So, if you run the video from the command line with mplayer, does the mplayer console output include something like (this is from a 16:9 anamorphic PAL recording):
> Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 704x576 => 1024x576 Planar YV12 
and not (4:3 PAL recording):
> Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12 

---

### Post by mister_p_1998 on 2007-01-16
> **david_2001 said:**
> If you have MJPEG Tools installed from the multiverse repository then you can use mplex to mux the video and audio together in dvd format:
```
mplex -f 8 -o output_file.mpg input_file.m2v input_file.mp2
```
If that doesn't work then, don't take offense, are you certain that the video is genuine 16:9 anamorphic and not letterboxed 4:3, and is not a mixture of 4:3 and 16:9?  So, if you run the video from the command line with mplayer, does the mplayer console output include something like (this is from a 16:9 anamorphic PAL recording):

and not (4:3 PAL recording):

This is the output:
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12
alsa-space: xrun of at least 3.522 msecs. resetting stream?,?% 1 0
alsa-uninit: pcm closed 0.002 ct:  0.013  94/ 94 21% 22%  1.9% 33 0

---

### Post by mister_p_1998 on 2007-01-16
Yep, looks like its technically 4:3 doesnt it? so was it broadcast in 4:3 with the black lines pushing it out to 4:3 then or what?
because the M2V still plays fine in (visually) 16:9. Is there a way I can force it?

---

### Post by david_2001 on 2007-01-16
Anamorphic video is compressed horizontally during transmission/storage and then expanded to the correct aspect ratio when it's played.   You'll see what I mean if you open a true 16:9 anamorphic video file in avidemux, as avidemux does not expand the picture to the correct aspect ratio for display.  For more information, take a look at the BBC's guide to TV picture size [[COLOR="Blue"]_here_[/COLOR]]("http://www.bbc.co.uk/commissioning/tvbranding/picturesize.shtml").

Converting a 4:3 letterboxed widescreen video to 16:9 anamorphic will mean loss of image quality.  The whole video would have to be re-encoded (mpeg is lossy) in order to upscale the picture content to the full vertical resolution (more loss of quality) and then compress it horizontally.

It is certainly possible to patch mpeg file headers to force an aspect ratio change but this would just result in the picture being stretched out unnaturally when played.  My best advice is to leave well alone this time around and check whether your PVR has some recording settings that can be tweaked for next time.

---

### Post by mister_p_1998 on 2007-01-17
Yeah, in the end I left it in 4:3 and changed the output mode onm the TV from auto to 16:9, I'd rather keep better quality. Thanks for your help anyway.
Steve

---

