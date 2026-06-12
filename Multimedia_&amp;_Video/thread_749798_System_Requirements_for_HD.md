---
title: "System Requirements for HD"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by dover19 on 2008-04-08
I was wondering if anyone knew what were the minimum system requirements to watch 1080p H.264 or MPEG-4 AVC video files using ubuntu.

Thanks

---

### Post by shirilover on 2008-04-08
Dual core processor ~2.4 GHz or better

---

### Post by dover19 on 2008-04-08
lol, yeah....right.

I can watch HD on my XP machine that's only P4 1.8.

---

### Post by shirilover on 2008-04-09
You can watch 1080p H.264 on a P4 1.8.
I find that extremely difficult to believe.
I rather doubt that setup would play 720p H.264 without dropping frames like mad.
In any case, below are the hardware recommendations from Apple:
```

Recommended Hardware Configurations for H.264 High Definition (HD) Playback

To play high definition video, a large amount of data must be processed by your computer. A powerful system will deliver the best playback experience.

For 1920x1080 (1080p) video at 24 frames per second:
QuickTime 7 for Mac OS X:

    * Dual 2.0 GHz PowerMac G5 or faster Macintosh computer; 2.0 GHz Intel Core Duo or faster
    * At least 512MB of RAM
    * 128MB or greater video card

QuickTime 7 for Windows:

    * 3.0 Ghz Intel Pentium D (dual-core) or faster processor
    * At least 1GB of RAM
    * 64MB or greater video card
    * Windows XP Service Pack 2 or Vista

```

---

### Post by dover19 on 2008-04-09
Sorry, I dunno why I said 1.8, it's a 2.6, but still not a dual core. 

As you said, those stats are from Apple. Since Linux is better at not wasting resources than Windows or Mac, I figured the minimum requirements would be lower and that's what I was trying to figure out. It's crazy the things you can do on such a low end PC with Linux compared to the same PC using Windows.

---

### Post by diplomat.x on 2008-04-09
Intel E6750 or better.
AMD X2 6000+ or better.
24 inch screen.
HD enabled graphics.

---

### Post by jbman on 2008-04-09
if  you have a supported video card that does HD then all you need is a dual core 3200+ cpu

---

### Post by aeiah on 2008-04-09
i dont think any video cards have hardware x264 accelleration in linux, but you will need a graphics card with the installed drivers. 

mine play fine on my system, which is:
AMD x2 3800, 1gb ram, Nvidia 7800 GT. i find i get the best results with mplayer, with multithread set, although xine does a good enough job (i just get errors in the AC3 audio sometimes with xine).

its hard to gauge system requirements though, because the cpu usage can vary greatly. i can play 2 720p movies at once and it wont struggle, but if i watch the intro to 'planet earth' in 720p my machine nearly dies when 2000 seaguls fly across the screen

---

### Post by soga_genzo on 2008-04-09
I have an AMD Athlon64 X2 3800+. Any h264-encoded 1080p material is a no-go under Linux for me. And under Windows, too, I can't watch it properly without resorting to using CoreAVC. Mplayer usually works best for all things HD, but unfortunately its multithreading support (or rather libavcodec's) is so far only very, very basic.

---

