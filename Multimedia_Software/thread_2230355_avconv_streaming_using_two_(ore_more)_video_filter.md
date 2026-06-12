---
title: "avconv streaming: using two (ore more) video filters eg drawtext and movie"
date: 2014-06-18
forum: Multimedia Software
---

### Post by luminarycrush on 2014-06-18
Hi, I'm trying to use two video filters - a combination of drawtext to render text on the video as well as place a watermark/logo in the lower right corner of the screen.
The text works fine by itself, as does the logo.  However, when I try to do both, only the logo appears and the text disappears.

Here's my CLI:

avconv -i rtsp:/192.168.204.16:5554/mpeg4/media.amp -vf "drawtext=fontfile='/usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf':text='test text':x=text_w:y=50:fontsize=24:fontcolor=black" -vf "movie=/opt/jtvtools/lib/logo-72p.png [watermark]; [in][watermark] overlay=880:688 [out]" -f flv -ac 1 -ar 22050 -vcodec libx264 -g 10 -keyint_min 10 -b:v 500k -minrate 500k -maxrate 500k -pix_fmt yuv420p -s 960x768 -preset ultrafast -tune film -acodec libmp3lame -threads 0 -strict normal -bufsize 500k " <destination RTMP>

I don't get any errors - it simply doesn't draw the text.  What's wrong with my syntax?

Thanks...

---

