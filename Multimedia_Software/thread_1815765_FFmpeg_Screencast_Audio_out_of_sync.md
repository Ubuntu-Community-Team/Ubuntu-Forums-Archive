---
title: "FFmpeg Screencast Audio out of sync"
date: 2011-07-31
forum: Multimedia Software
---

### Post by io5cml4z on 2011-07-31
When I try to record a screencast with FFmpeg, it seems to work perfectly, except that the audio gradually gets more and more out of sync. Here is the command that I use:
ffmpeg -f alsa -ac 1 -i hw:0,0 -f x11grab -r 15 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 2 output.mkv

---

### Post by io5cml4z on 2011-08-01
Bump.

---

### Post by io5cml4z on 2011-08-01
Bump.

---

### Post by FakeOutdoorsman on 2011-08-01
Does it play correctly with *ffplay*?  If yes, blame whatever player you're using.

---

### Post by io5cml4z on 2011-08-01
Unfortunately it is still out of sync with ffplay.

---

### Post by io5cml4z on 2011-08-01
I just discovered something odd. When I use -i pulse instead of -i hw:0,0 the audio is in perfect sync. However, using pulse I can only record my microphone and not the system audio. Is there a way that I can record both?

---

### Post by io5cml4z on 2011-08-01
Anyone? How can I record more than just the default input using pulseaudio?
e.g. "ffmpeg -f alsa -i pulse..." Would record my microphone, but I also need it to record my system sound, or maybe if I wanted to use a different microphone.

---

### Post by FakeOutdoorsman on 2011-08-01
See **Q: How can I control PulseAudio input? (e.g. capture application audio instead of mic)** in [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026).

---

### Post by io5cml4z on 2011-08-01
Thanks for the help. With that I can change the audio source, but I can't figure out how to capture 2 audio sources at once. (Microphone + PC)

---

### Post by io5cml4z on 2011-08-02
Bump. I can record 2 pulseaudio streams at once and set one to record PC audio, and one to record the mic, but when I play back the file, there is no audio at all.

---

### Post by io5cml4z on 2011-08-02
Bump...

---

### Post by io5cml4z on 2011-08-03
Bump again...

---

### Post by io5cml4z on 2011-08-08
Bump.

---

### Post by io5cml4z on 2011-08-16
Bump.

---

### Post by FakeOutdoorsman on 2011-08-17
Might be time to ask this question on the [ffmpeg-user](http://ffmpeg.org/contact.html) mailing list or at the *#ffmpeg* IRC channel.

---

