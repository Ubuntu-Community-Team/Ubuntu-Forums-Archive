---
title: "Help with mencoder"
date: 2010-05-21
forum: Multimedia Software
---

### Post by flux7d on 2010-05-21
After lot of searching I found this script somewhere it this forums:

```
#!/bin/bash

OUTPUT="/home/shaul/Desktop/pvr/`date +%y%m%d-%H%M.xvid`"

mencoder tv:// -tv driver=v4l2:device=/dev/video0:input=1:width=640: height=480:alsa \
-of avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=3500 -oac \
mp3lame -lameopts cbr:br=128 -vf pp=lb -o test.avi -endpos 119:00

while [ ¨$(pidof mencoder)¨ != ¨¨ ]; do sync; sleep 15; done

sync

exit 0
```It records the video great, but i have problem with recording sound...
I can hear it if I unmute the microphone in the alsamixer, but I don't know what command to write to let mencoder record from it..
hope some can help me

ty

---

### Post by andrew.46 on 2010-05-21
Hi flux7d,

I no longer really use MEncoder but I wonder if your copy is setup for mp3 transcoding, it can be tested as follows:

```

andrew@skamandros~$ **[COLOR="Red"]mencoder -oac help[/COLOR]**
MEncoder SVN-r31189-4.3.3 (C) 2000-2010 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
  **[COLOR="Red"] mp3lame  - cbr/abr/vbr MP3 using libmp3lame[/COLOR]**
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   faac     - FAAC AAC audio encoder

```

All the best,

Andrew

---

### Post by flux7d on 2010-05-21
hi tnx for the reply, I didn't really understand you post, but you asked me to check the -oac help output?


```
MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Pentium(R) Dual-Core  CPU      E6300  @ 2.80GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

   copy     - frame copy, without re-encoding (useful for AC3)
   pcm      - uncompressed PCM audio
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame
   lavc     - FFmpeg audio encoder (MP2, AC3, ...)
   twolame  - Twolame MP2 audio encoder
   faac     - FAAC AAC audio encoder

```

---

### Post by flux7d on 2010-05-22
I found that you can use :adevice=hw.x and it should work, but for me it doesn't :( 
Isn't there a command that can tell me where is my mic?

thanks

---

### Post by xzero1 on 2010-05-22
I used to do this with adevice=/dev/dsp. This should record whatever the soundcard mixes together.

---

### Post by flux7d on 2010-05-22
mmm still nothing... whats wrong here??

---

### Post by xzero1 on 2010-05-22
It used to work... Install ivtv-utils then run the command v4l2-ctl --all. This should list info about your tuner including the audio input. But you said you want to record with a mic? Make sure you get a vu reading from your mike before recording anything. Click the sound icon, select sound preferences then input. When you speak into the mic you should see the input level following the sound.

---

