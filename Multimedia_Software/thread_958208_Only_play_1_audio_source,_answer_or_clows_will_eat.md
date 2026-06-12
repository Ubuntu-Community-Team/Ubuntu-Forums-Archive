---
title: "Only play 1 audio source, answer or clows will eat your brains"
date: 2008-10-25
forum: Multimedia Software
---

### Post by Peter_G on 2008-10-25
*clowns

Hello, I am currently on ubuntu Hardy, and have only had this problem for the past few weeks, and it is starting to get annoying, I can only play audio from one source, so, I could play a video game, but the audio wont work on teamspeak, I could listen to some music on amarok, but I couldn't play a flash game with sound, but I can listen to multiple youtube videos, you get the idea, right? If you can answer this then I would be REALLY greatfull.

Thanks!

---

### Post by mindoms on 2008-10-25
This is a frequent question and there are several threads about this:
e.g.
[http://ubuntuforums.org/showthread.php?t=933155](http://ubuntuforums.org/showthread.php?t=933155)

In this case a simple
```

asoundconf set-pulseaudio

```
typed into a terminal (and maybe a reboot) did the trick

hth, stefan

---

