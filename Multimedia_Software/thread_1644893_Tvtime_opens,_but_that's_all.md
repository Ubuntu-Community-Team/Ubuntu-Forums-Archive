---
title: "Tvtime opens, but that's all"
date: 2010-12-13
forum: Multimedia Software
---

### Post by dianemeeks on 2010-12-13
I have been using tvtime for several years, and have never had trouble getting video. However, I recently tried to set up to attempt to record, and now my tvtime doesn't work at all. The window opens, but shows nothing and it can only be closed from the terminal, not from the tvtime window. The only things changed were: I installed mencoder and I ran the following script.
 #!/bin/sh
 killall tvtime
 TODAY=$( date +%Y%m%d )
 NOW=$( date +%H:%M )
 sleep 4 && amixer -q set "Line" 100% unmute
 sleep 1 && amixer -q set "Analog Mix" 100% unmute
 ################################################## ###################
 transcode -x v4l2,v4l2 \
 -M 2 \
 -i /dev/video0 \
 -p /dev/dsp \
 -w 6000 \
 -y ffmpeg \
 -F mpeg4 \
 -g 720x420 \
 -f 0,4 \
 -I 1 \
 -J resample,levels,smartyuv,pv \
 -u 100 \
 -Q 3 \
 -Z 640x480,fast \
 -E 48000,16,2 \
 -o ~/-${TODAY}-${NOW}.avi \
 ################################################## ###################
dianemeeks is offline     Reply With Quote

---

### Post by dianemeeks on 2010-12-16
Still not getting a picture, but I briefly did. I started tv-viewer and it finely found channels.  I opened tvtime while it was scanning and the scanning channels were visible in tvtime.  However, I haven't gotten either one to let me view anything else. Also, I am getting a fine picture when using a different partition so it isn't the card.

---

