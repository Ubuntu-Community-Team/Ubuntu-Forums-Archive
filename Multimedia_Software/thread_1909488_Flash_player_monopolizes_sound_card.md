---
title: "Flash player monopolizes sound card"
date: 2012-01-15
forum: Multimedia Software
---

### Post by mindcircus on 2012-01-15
Hello,
I use Ubuntu Lucid Lynx and I have a little problem with my sound: I can't use at the same time Flash player and any other program that uses sound card.

If I start first open an mp3 file with totem and after that go to youtube to play a video, I get the following message in the terminal I used to open firefox:

```
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
```and I can't hear any sound from firefox.

If I open first  a video in youtube and after that open an mp3, I have sound from firefox, but totem doesn't even start to play the mp3. In this occasion I don't get any message in the terminals neither from totem nor from firefox. 

Totem is just an example. Exactly the same behaviour I encounter when I use any other media player.

Is it an alsa problem or do I have to install any missing gstreamer plugins?

---

