---
title: "Dell Inspirion 1300 alsa microphone problem"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by vanjakom on 2007-12-02
Hello

I tried to find solution for my problem on google and this forum but I didn't have any luck. Here is my problem. I have Dell inspirion 1300. With Edgy (6.10) when added options snd-hda-intel model=ref to /etc/modprobe.d/alsa-base everything gone right, but with Gutsy I can't make microphone work. I tried everything changing versions, latest version of alsa 1.0.15 but without any luck. I someone knows answer please help.

8086:2668
SigmaTel STAC9200
Conexant ID 2bfa

Thanks,
Vanja

---

### Post by deadgobby on 2007-12-02
Double click on the speaker icon and see if you have some options open up. Here is a screen shot. The main one is IEC958 is click on. 
Gobby
Good luck

---

### Post by vanjakom on 2007-12-06
After a small research i have following results:

1. After install of Xubuntu 7.10 there was no way to make sound work... Tried 1.0.15 alsa, also fresh install from source... Varies versions of alsa deb files, picked up from packages.ubuntu.com... No result.
2. After live cd boot of Ubuntu 7.10 and change of input source from mic to line everything suddenly worked out. Quality and strength of signal were ok.
3. I installed ubuntu 7.10 to my laptop and tried working combination but nothing changed...

Also I noticed:

1. When microphone is not working also command: arecord -d 5 -f cd test.wav never finish.
2. There are differences in alsamixer form Xubuntu and Ubuntu 7.10. For example in xubuntu I have IEC958 and in ubuntu i don't have. Please help me, I am going mad.

Vanja

---

### Post by xl_cheese on 2007-12-07
Try installing the latest alsa drivers from their site.

---

