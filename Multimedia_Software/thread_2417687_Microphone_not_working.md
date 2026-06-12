---
title: "Microphone not working"
date: 2019-04-26
forum: Multimedia Software
---

### Post by nnss on 2019-04-26
I already installed pavucontrol and checked alsamixer for further verification, but I don't see an end to my problem.
This is my alsa info 
[http://alsa-project.org/db/?f=377ea2cb7de1eb5d20230b4dc5a144616bb29a6d](http://alsa-project.org/db/?f=377ea2cb7de1eb5d20230b4dc5a144616bb29a6d)

---

### Post by wildmanne39 on 2019-04-26
*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

---

### Post by krenkz on 2019-04-28
Hello there,

I have similar issue, my mic does not work or is too low. Any ideas? I am using Creative Sound Blaster Z card.

Alsa info: [http://alsa-project.org/db/?f=968aafe21cdd34c3399864e98b3e5c1129f21fe9](http://alsa-project.org/db/?f=968aafe21cdd34c3399864e98b3e5c1129f21fe9)



/edit integrated sound card working on both systems Win10 also Linux. The Creative worsk on Win10 only

---

### Post by drvshrm on 2019-05-07
Have you checked sound settings...I faced the very same problem when I first used it...after searching a lot I found a very simple solution in sound settings....

1. Go to settings tab by clicking on top-right menu options.
2. Select "Sound" from the options tab.
3. In the "Input" tab switch between the options...

Check if it worked or not...In my case it worked...

---

### Post by nik.charles on 2019-05-08
@nnss - suggest you get firmware update to v306 and more recent kernel if possible
possible that updates will have better support for audio

(@krenkz - update kernel to v4.20 or later for supporting HD-audio CA0132 codec of creative card)

---

