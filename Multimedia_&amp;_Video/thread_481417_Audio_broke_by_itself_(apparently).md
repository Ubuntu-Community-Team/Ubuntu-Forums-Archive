---
title: "Audio broke by itself (apparently)"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by don_eros on 2007-06-22
Hi there,

this morning my Feisty box started to sound like a broken phonograph. I don't know what happened, the audio card works fine when I reboot into Windows and it had worked fine ever since the first installation of Feisty a couple of months ago. Now every audio file is distorted (wave, mp3, ogg doesn't matter).

I tried a few obvious things (like fiddling with every possible volume combination), but nothing changed. I don't really know where to start, I can fix more "traditional" Linux stuff, like an Apache server, but the Linux sound system is still a big mystery to me.

Can anyone help me please? Where do I start?

The system is a Toshiba Satellite A100 317 (Intel sound card).

Thanks,
E

---

### Post by kkinder on 2007-06-22
Me too, although I don't get sound at all. Did something go through with an upgrade last night?

---

### Post by r4ik on 2007-06-22
A bit old but worth a try,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by jlk on 2007-06-22
I had similar problem during Dapper -> Edgy -> Feisty upgrade.  Found the problem to be  the PCM control was muted and set to zero.

Right click on the volume control and select "Open Volume Control"  Un-muting the PCM and moving the slider to mid-way worked for me.  YMMV

---

### Post by don_eros on 2007-06-23
> **r4ik said:**
> A bit old but worth a try,

[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !
Thanks for the tip but unfortunately that didn't help: that guide only deals with driver installation (i.e. if you have no sound).

My problem is I have *distorted* sound. I tried stopping alsa:

```
/etc/init.d/alsa-utils stop
```

Audio still works and the distortion is gone. I'm guessing the system starts using another engine. The problem is that, while the distortion goes away, now I get an annoying hissing sound (it's low but still noticeable).

Any idea what might be wrong?

---

