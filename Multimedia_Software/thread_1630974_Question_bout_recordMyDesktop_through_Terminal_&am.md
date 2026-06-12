---
title: "Question bout recordMyDesktop through Terminal &amp; update on Skype with mic"
date: 2010-11-26
forum: Multimedia Software
---

### Post by throese on 2010-11-26
I use the following command:

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1200x800 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.avi
```

I was wondering what the commands are.

I know "q" stops and finishes the video. But what pauses it and what makes it play again?

Also, I got my mic to work on my computer (and Skype)! I have to have my webcam plugged in for the mic to work and I had to DL GNOME Alsa Mixer and uncheck mute on "Line-in" and "Mic" but it FINALLY works!

Thanks everyone in advance and those who tried to help me previously with the Skype/Mic prob!

---

