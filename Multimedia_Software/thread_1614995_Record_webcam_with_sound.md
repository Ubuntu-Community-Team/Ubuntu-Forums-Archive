---
title: "Record webcam with sound?"
date: 2010-11-06
forum: Multimedia Software
---

### Post by gaz514 on 2010-11-06
Hi,

Is there currently any way to record a webcam video with sound? This used to be possible back in the day before PulseAudio was installed by default (by using Mencoder, following guides such as [https://wiki.archlinux.org/index.php/Webcam](https://wiki.archlinux.org/index.php/Webcam) and [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) ) but that method doesn't work any more: /dev/dsp doesn't exist. I've also tried Cheese and that again just records a video with no audio. All the articles I can find on the topic are from the good old pre-Pulse days.

I've tried messing about with the commands a bit to use the Alsa Pulse device (defined in /etc/asound.conf) since neither mencoder or ffmpeg seem to have built in Pulse input support:

```
ffmpeg -f alsa -i pulse -f video4linux2 -s 640x480 -i /dev/video0 out.mpg
```
- this works, but the audio is more than a second out of sync with the video, which is a bit useless (I'm trying to record myself playing guitar), and the video is very slow (<1 fps) for the first few seconds.

```
mencoder tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0:fps=30:forceaudio:alsa:adevice=pulse -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o test.avi
```
- this doesn't work, I get the following error:
```

v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
Selected input hasn't got a tuner!
v4l2: Cannot get fps
Floating point exception

```

Any ideas? The Mencoder method always used to work fine for me before I started using Pulse.

Video and audio work fine for me on Skype so there's no issue with hardware or drivers. I could also record the audio and video at the same time using different programs, or just boot into Windows since it has a sound system that isn't a joke so I can't imagine it'll have any such problems, but surely I shouldn't have to resort to that?

Thanks.

---

### Post by no2498 on 2010-11-07
try this program wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


hope it helps you

---

