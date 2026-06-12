---
title: "C-Media CM106 conflicts Pulse and Alsa?"
date: 2011-03-15
forum: Multimedia Software
---

### Post by xube on 2011-03-15
Hello people,

I have problem with input devices. My USB external sound card works almost perfect. With installed pulseaudio i have 5.1 and 7.1 support. Perfect! But when i want record something by input/mic suddenly my playback fail.

There si two scenarious:
[LIST]
[*]I can playback sound (startup sound, music and etc) but i cant record.
[*]I can record my mic is working but I cant play any music (Totem want play, Banshee the same..)
[/LIST]

**I want to hear my voice when i am recording.** But no chance! I tried almost everything on a blogs and this forum, nothing works.

If i want reinitialize my input device source i use this command:
```
pulseaudio -k
```

Sometimes it works. I have mic, but i cant hear my voice or play music.

Ubuntu 10.04.2

Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 15 2011 for kernel 2.6.32-29-generic (SMP).

pulseaudio 0.9.21-63-gd3efa-dirty

Any help?
Thanks

---

