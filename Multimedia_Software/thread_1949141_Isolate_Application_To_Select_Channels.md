---
title: "Isolate Application To Select Channels"
date: 2012-03-29
forum: Multimedia Software
---

### Post by user2037 on 2012-03-29
My audio device has 5 different channels with different output plugs for sets of speakers: center, front, back, stereo (front and back?). I'd like to use headphones for music and speakers for notifications.

Is there a way to isolate an application to certain channels?

---

### Post by MadHatter93 on 2012-03-30
I've never seen such fine-tined control using PulseAudio or ALSA, but if you are using a JACK session and applications that can port to JACK, you can easily send different signals to different output channels. 

Check out [http://jackaudio.org/]("http://jackaudio.org/") for more information on JACK and compatible programs

---

