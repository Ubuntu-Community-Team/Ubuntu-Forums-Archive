---
title: "Digital Output Format"
date: 2013-05-19
forum: Multimedia Software
---

### Post by Sunfist on 2013-05-19
In windows there is a place you can go to configure the digital output format of your sound card or dac. Where in Ubuntu do you go to do the same thing?

---

### Post by CatKiller on 2013-05-19
Pulse-client.conf, although I think it defaults to the sample rate of whatever you're playing. You can tell it not to do that in the same place. Also, if you use JACK, that has its own setting. My sound card also has a hardware sample-rate lock that I could access through alsamixer.

---

