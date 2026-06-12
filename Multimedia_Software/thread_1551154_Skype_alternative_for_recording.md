---
title: "Skype alternative for recording"
date: 2010-08-11
forum: Multimedia Software
---

### Post by Gannin on 2010-08-11
Right now in order to do some recording I use Skype and Skype Call Recorder, but Skype only does audio at 16Khz.  Is there some other similar program that could be used that could also be recorded at a higher quality?

---

### Post by LuridCinema on 2010-08-12
try this from a terminal 

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x720 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```

it will record your desktop and any audio playing on your system.. you might need to install Pulse Audio Volume Control to get sound working

---

### Post by Gannin on 2010-08-12
I appreciate the effort, however, will that also record the other person I'm on Skype with?  And even if it did, because the Skype audio stream is natively 16Khz, won't it still sound like, well, 16Khz?

The idea I'm going for is a different voice chat program that can record that has higher audio quality than Skype.

---

