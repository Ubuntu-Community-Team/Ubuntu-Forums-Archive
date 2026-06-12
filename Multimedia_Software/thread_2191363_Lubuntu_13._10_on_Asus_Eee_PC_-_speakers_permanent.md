---
title: "Lubuntu 13. 10 on Asus Eee PC - speakers permanently hissing loudly"
date: 2013-12-02
forum: Multimedia Software
---

### Post by bram.vana on 2013-12-02
Lubuntu 13.10 running on a netbook - Eee PC 1000H

Made a video of it.

[http://www.youtube.com/watch?v=rITFM6Co9pM]("http://spliced.org/x.php/http://www.youtube.com/watch?v=rITFM6Co9pM")

It's running from a bootable flash drive to test it. Speakers don't work properly; they make noise at 100% volume level.

If sound is on, it makes noise. No way to make it stop, unless by muting the sound. Reducing levels in Alsamixer doesn't do anything.

Before I install it, I need to know this can be solved.

Any ideas?

---

### Post by sudodus on 2013-12-02
Welcome to the Ubuntu Forums :-)

One way to solve it might be to use PulseAudio and PavuControl

Install them via Synaptic or a terminal window

```
 sudo apt-get install pulseaudio pavucontrol
```

---

