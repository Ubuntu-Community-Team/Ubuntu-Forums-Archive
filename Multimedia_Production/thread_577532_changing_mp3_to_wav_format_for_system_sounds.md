---
title: "changing mp3 to wav format for system sounds"
date: 2007-10-16
forum: Multimedia Production
---

### Post by ljonesj on 2007-10-16
i would like to change some of my shorter mp3 files to my system files and i have tried audacity to change them to wav but i keep getting a output error to a device which program will do this easily

---

### Post by paulg on 2007-10-18
I recently discovered a program called 'sox' in another post when I was looking for a way to convert a stereo wav file to a mono wav file. You need to call up a terminal to use it. Try 'sox --help' or 'man sox' for more information. However, I think that this might *just * work to transcode mp3 to wav:
```
~/$ sox file.mp3 file.wav
```

I'm not at my linux PC right now to verify this but that's my best guess given my little experience with the program. Good luck!.

---

