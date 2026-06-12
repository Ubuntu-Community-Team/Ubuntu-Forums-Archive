---
title: "Video Downscaling"
date: 2013-02-05
forum: Multimedia Software
---

### Post by lizandeen on 2013-02-05
My laptop has a pretty rubbish graphics card so I was wondering if there is a media player that can downscale 1080p,(I'm trying to avoid the time consuming task of converting the files) during playback? Thanks, lizandeen

---

### Post by BicyclerBoy on 2013-02-05
All media players I have used can scale..

Video is encoded at a specific resolution & has to be decoded to the same. 
Scaling is a feature in video playback post processing.
This function can be performed in openGL/VDAPU/VAAPI using video h/w (shaders).

Good scaling is very CPU/GPU intensive for non-linear transforms & good picture quality.
AIUI Simple linear scaling is okay for <10% size change.

The video post processing (scale/de-interlace/colourspace/denoise/sharpen) is more CPU/GPU intensive than decoding.

This is why tablet/phone devices require exact video formats & no interlacing (no post processing capability).

---

### Post by lizandeen on 2013-02-05
Sorry, could you translate that into language for idiots please? (maybe using vlc as an example). Ta

---

### Post by papibe on 2013-02-05
Hi lizandeen.

BicyclerBoy is right.

In simple words: no while you playing it. You need to convert the file to a lower resolution first.

Take a look at [handbrake]("http://handbrake.fr/") ([here]("http://ubuntuforums.org/showthread.php?t=1966026&highlight=handbrake") are the 2 installation options), and [ffmpeg]("https://help.ubuntu.com/community/FFmpeg").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2013-02-05
The player has to decode the frames before they can be rescaled.  So unless you rescale first and then play it, you won't gain anything in terms of performance.

Is that clearer?

Is 1080p the only version you have available?  The difference between 1080p and 720p is substantial in terms of file size and decoding requirements.  Since what matters is the total number of pixels per frame, a 1080p frame consists of 2,074 million pixels (=1920x1080).  A 720p frame is 921,600 (=1280x720).  Obviously that is a lot less data for your processor to decode.

---

### Post by BicyclerBoy on 2013-02-05
I didn't read your question properly..
You want to transcode the files to lower resolution/ easier decoding?

How can converting during playback be "time consuming" if it is fast as real-time?
Do you not want to view? 

Could try ffmpeg/avconv or winff/handbrake.

VLC can transcode/stream &/or playback.
Fairly sure VLC can transcode only.

VLC & handbrake winff  have GUI interface.

Video transcoding requires CPU & memory..a core2 duo can manage about real-time H264 encoding.
Note that H264 can be 1/3 to 1/2 filesize of mpeg2video.

Do you know exactly what laptop graphics ?
There could be some/partial h/w accelerated video playback features.

---

### Post by lizandeen on 2013-02-05
Sorry, when I said time consuming, I meant having to convert the files before being able to watch the video.

---

### Post by BicyclerBoy on 2013-02-05
How bad is the graphics ? What model/chipset ?

You might get better performance from (s)mplayer, some people highly recommend it.
I find it a bit hopeless with AV sync & mpegts files & +/-100ms steps is a joke.

Both mplayer & vlc can take advantage of some video h/w support but this has to be configured etc.
VLC has support for VAAPI which is probably best for intel h/w from ironlake. (experimental GPU decoding).

I believe SMplayer will support VAAPI if the underlying mplayer is built with VAAPI support.

---

