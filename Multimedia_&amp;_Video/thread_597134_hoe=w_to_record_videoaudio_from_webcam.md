---
title: "hoe=w to record video/audio from webcam"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by val67 on 2007-10-30
None of the posts helped me solve this issue.

Tried:

1.in Gutsy, xawtv is broken
2. tried cheese, but no sound (not from Ubuntu rep)
3. tried wxcam , but won't install (not from Ubuntu rep)


Using Logitech Messenger QuickCam

Thanks.

---

### Post by val67 on 2007-10-30
I want to completely forget about windows, but how can one use Linux when a simple thing like recording from webcam does not work?

Has anybody a solution?

---

### Post by val67 on 2007-11-10
well, i managed to use xawtv and recoed from webcam

The trick is to start it like:

xawtv -v -c /dev/video0 -C /dev/dsp1 -nodga -nogl -noconf

---

### Post by Anal on 2008-01-17
Thank you for posting that.

Too bad when I try to actually record, the system hangs.:lolflag:

---

### Post by sisco311 on 2008-01-17
mencoder:
>  mencoder tv:// -tv driver=v4l:width=320:height=240:device=/dev/video0:forceaudio:alsa:adevice=hw.0,0 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

---

### Post by Anal on 2008-01-17
Whoa!

That huge command line almost worked, thank you!
Too bad I can get no sound. I investigate.

---

### Post by sisco311 on 2008-01-17
you may find you need to use hw.1,0 or hw.2,0 , depending on the audio hardware on your system

---

### Post by Anal on 2008-01-18
Thanks again.

I managed to find out which device is (it's the webcam built-in microphone the one I need, and in ALSA here is 1,0). Too bad I can't record from it anyhow. **mencoder** gives me a mute video, while trying to record from **audacity** gives me suddenly an error when I try to start the recording.
Too bad, the audacity error is not very informative about the problem (more or like "check settings", something like that).

Thanks for any idea.

---

