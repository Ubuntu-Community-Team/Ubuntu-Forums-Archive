---
title: "(Black screen) Screenshot a video playback on a desktop with ffmpeg"
date: 2012-03-27
forum: Multimedia Software
---

### Post by wilsonmak on 2012-03-27
Hi all,

I try to have a screenshot on my desktop that has a video playback.  But  it just shows a black/blank screen on the video portion.  All  screenshots of others stuffs on my desktop are fine.  

Command:
ffmpeg -f x11grab -r 25 -s 1920x1080 -i:0.0 -vcodec libx264 output.avi

P.S.  
1) I use gnome-mplayer with VDPAU enabled.
2) If I use VLC without hardware acceleration(very poor video quality), I can capture the video playback with ffmpeg 

Is it because of the hardware acceleration enabled by VDPAU?  
And how to fix that?

Many thanks,
Wilson

---

### Post by BicyclerBoy on 2012-03-27
VDPAU uses h/w video overlay &/or blitter to present rendered video.
Blitter is used if you use composite effects manager.

The screen snapshot just sees the dummy empty screen, it can't see the overlay.

You could try mplayer with opengl/XVideo etc..problem could be the same.

You could attempt to record in 1/4 speed playback.
No vaapi version of vlc can play 1080i50 10Mbps with yadif on a core2duo easy but ...

To play by s/w & capture means you have massive decoded video data streams from CPU to GPU & then GPU to CPU & encode..

core2duo can just manage to encode h264 HD 10Mbps in real time with no other load.

It would be more efficient to capture desktop & try use ffmpeg to encode the video & desktop into a stream/file. This way it is mostly all in the CPU.

---

### Post by wilsonmak on 2012-03-28
Thank you for your suggestion!

To be more precise, I need to take a screenshot of my desktop including video playback (VDPAU enabled) and save it as a JPEG.

Is there a way to achieve this?

P.S.  I try many screenshot tools, like xvidcap, gnome-sreenshot, ffmpeg.  It just shows black screen of the video part on the JPEG file 

Thanks,
Wilson

---

### Post by Jose Catre-Vandis on 2012-03-28
Only thing I can suggest as a workaround is you do some post processing in GIMP afterwards.

1. Take a screenshot of your desktop
2. Grab a frame form the video using ffmpeg (example)
```
ffmpeg -ss 00:00:01.01 -i /my_video_file_dir/video.flv -y -f image2 \
   -vcodec mjpeg -vframes 1 /image_dir/screenshot.jpg
```
3. Open up screenshot (1) in GIMP.
4. Insert frame grab (2) to black space in image
5. Save

---

### Post by wilsonmak on 2012-03-29
In fact, it's an application that has a video embedded into the browser.  So we don't know the time frame to have a screenshot.  And I have to do all in console mode as it's an application to others, like clicking a button to email the screenshot.

Thanks,
Wilson

---

### Post by Jose Catre-Vandis on 2012-04-02
This might help:
[http://www.youtube.com/watch?v=Oy3XjawQjlQ](http://www.youtube.com/watch?v=Oy3XjawQjlQ)
although I still think you may have trouble with the video...

You can also try turning off hardware acceleration or stop your video player from using the overlay

---

