---
title: "Why can't i play my videos on my psp?"
date: 2009-07-03
forum: Multimedia Software
---

### Post by Yvan300 on 2009-07-03
I'm just confused. I installed ffmpeg and downloaded a nautilus script from gnome-look, which allows a variety of conversions but when i convert my videos the mp4 and even mp3 for my psp they come up as unsupported or corrupted data. What could i be doing wrong?

---

### Post by Revolutionary101 on 2009-07-03
For the video you can't have the resolution higher than 480 x 272 and a bit rate no higher than 1500 kbps.

Are you using a GUI for ffmpeg? Because that can eliminate much of the confusion.

I suggest using Avidemux because it has a preset for PSP video. As for the audio i can't help you.

To get Avidemux type this into terminal.

```
sudo apt-get install avidemux
```Hope it helps.

---

