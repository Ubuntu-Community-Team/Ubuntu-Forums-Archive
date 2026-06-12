---
title: "[SOLVED] Audio pitch issues with Transcoder and ffmpeg"
date: 2008-09-12
forum: Multimedia Software
---

### Post by lovinglinux on 2008-09-12
I'm using transcoder and ffmpeg to record TV. The video image is fine, but the audio is weird. The "pitch" is accelerated so the audio track finishes a lot earlier than video track and everyone on TV sounds like speaking in fast motion.

Does someone knows hot to fix this?

I'm using a Gigabyte mobo with onboard HDA Intel sound card.

---

### Post by lovinglinux on 2008-09-13
I have managed to install my USB mic and to record from it or from the Line In (TV) using transcoder/ffmpeg or Audacity.

The sound recorded from the mic is normal on all recordings, but the sound from Line is accelerated, even when recording with Audacity.

Any idea why this is happening?

---

### Post by lovinglinux on 2008-09-18
I guess 5 days is enough to justify a bump right?

I can't fix this myself. I have searched everywhere, but couldn't find anything similar to my problem. Please heeeeeeeeelp....

---

### Post by lovinglinux on 2008-09-18
Nevermind. I figure out myself.

I was using transcode commands for NTSC while my card is PAL-M

The correct commands are:
```

#!/bin/sh

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

transcode \
        -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
        -g 640x480 \
        -i /dev/video0 \
        -p /dev/dsp1 \
        -e 32000,16,2 \
        -N 0x1 \
        -J resample,levels,smartyuv,pv \
        -w 4000 \
        -y ffmpeg \
        -F mjpeg \
        -o tvrecord-${TODAY}-${NOW}.avi \
        --avi_limit 1536
```

---

