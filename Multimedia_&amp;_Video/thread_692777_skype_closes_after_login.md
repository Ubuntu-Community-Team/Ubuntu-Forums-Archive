---
title: "skype closes after login"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by monkman on 2008-02-10
ubuntu 7.10
skype(actual deb from skype.com)

when i login into skype it closes itself with the following message:

```
skype: RtAudio/rtaudio-3.0.3/RtAudio.cpp:3958: virtual void RtApiAlsa::initialize(): Assertion `snd_config' failed.

```


what is wrong here? it used to work some days ago...



thanx!!

---

### Post by me98278 on 2008-02-11
hi monkman,

try running sudo ldconfig... it gave me  a partial solution..i was able to login but when i tried to make a call it failed.

did u install OSS ?? there seems to be some problem while using skype with OSS installed.

---

### Post by monkman on 2008-02-15
aah, okay. yes i use oss, because i have a maudio revolution 5.1 and have to use the headphone output which doesn't work with alsa...


thx..

---

