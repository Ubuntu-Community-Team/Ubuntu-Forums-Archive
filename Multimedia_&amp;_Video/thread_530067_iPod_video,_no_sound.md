---
title: "iPod video, no sound"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by coolen on 2007-08-20
I recently got an iPod, 30Gb video.
I put all my music on there using gtkpod, and it was good. I put a short film from my desktop on there. Sweet.
Then, I got to my other videos. I've followed five different (although surprisingly similar) howtos, used Vive, ThinLiquidFilm, and Floola, and none of them have been able to handle it properly.
After I encode them, I have sound on my computer, but once I transfer to my iPod, there's nothing. Video's fine, just no audio.
I'ver been using h264 codec, kept the audio bitrate below 160, and I'm using the Medibuntu version of ffmpeg. I've tried it on vob and avi files.
Has anyone else had this problem? Any fixes?

---

### Post by briguy on 2007-08-29
Have you tried Amarok?  That's what I use for putting all my videos on the iPod.

---

### Post by coolen on 2007-08-29
Yeah, still nothing. I get the feeling it's an iPod issue. When I play the music post encode, it has sound, when I transfar back to my computer, it has sound.
As I said, I've kept the audio bitrate below 160. I've used MP4Box, too, and still nothing.

Here's one of the scripts I've used for converting:
```
#!/bin/bash
ffmpeg -y -i "$1" -v 1 -threads 1 -vcodec h264 -b 500 -bt 175 -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb8x8 1 -me full -subq 6 -brdo 1 -me_range 21 -chroma 1 -slice 2 -max_b_frames 0 -level 13 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 35 -max_qdiff 4 -i_quant_factor 0.71428572 -b_quant_factor 0.76923078 -rc_max_rate 768 -rc_buffer_size 244 -cmp 1 -s 640x480 -acodec aac -ab 160 -ar 48000 -ac 2 -f mp4 -pass 1 "$2"
ffmpeg -y -i "$1" -v 1 -threads 1 -vcodec h264 -b 500 -bt 175 -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb8x8 1 -me full -subq 6 -brdo 1 -me_range 21 -chroma 1 -slice 2 -max_b_frames 0 -level 13 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 35 -max_qdiff 4 -i_quant_factor 0.71428572 -b_quant_factor 0.76923078 -rc_max_rate 768 -rc_buffer_size 244 -cmp 1 -s 640x480 -acodec aac -ab 160 -ar 48000 -ac 2 -f mp4 -pass 2 "$2"
```

Everything else I've used is basically just a frontend to ffmpeg anyways, and they all have similar results. Xvid seemed to work better, but still no sound.
The short movie that went across successfully is a .mov, ISO mpeg-4 video, aac 2.0 audio (at 44100 Hz sample rate). Doesn't know the bitrate. I got it from the net.

---

### Post by manki on 2007-12-28
I think I know the solution for this problem.  I also faced this same problem today.  After some random retries, I found that my source audio was Dolby AC3 **6 channels**.  Forcing the encoded video to use only 2 channels for audio fixed it for me.  I use Avidemux for encoding.  I selected *Audio > Filters > Mixer > Stereo* to force 2-channels.  I don't know how you would do that with ffmpeg.  Hope this helps.

---

### Post by crush304 on 2008-01-01
I've had a lot of problems getting anything encoded with faac to play on my ipod or in quicktime 7.3. If you are still having problems you might try the nero encoder for aac.

[http://ubuntuforums.org/showthread.php?t=526932]("http://ubuntuforums.org/showthread.php?t=526932")

---

