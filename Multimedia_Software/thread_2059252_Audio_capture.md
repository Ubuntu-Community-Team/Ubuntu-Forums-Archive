---
title: "Audio capture"
date: 2012-09-17
forum: Multimedia Software
---

### Post by RichLouth on 2012-09-17
In Ubuntu 12.04.

I'm trying to make Minecraft videos. I can successfully record the video with:

```
avconv -f x11grab -s 1280x800 -r 25 -i :0.0 -threads 4 -q 1 out.mkv
```

Now I'm trying to caputre the audio with:

```
avconv -f alsa -ac 2 -i pulse -f x11grab -s 1280x800 -r 25 -i :0.0 -threads 4 -q 1 out.mkv
```

But annoyingly this will only capture the microphone (if it is unmuted) and doesn't capture any of the system sounds. Namely, I want to capture the Minecraft sounds.

Any ideas?

Cheers

---

### Post by RichLouth on 2012-09-18
The problem was with the values in alsamixer.

---

