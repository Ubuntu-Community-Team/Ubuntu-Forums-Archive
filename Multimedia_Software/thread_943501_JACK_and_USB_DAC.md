---
title: "JACK and USB DAC"
date: 2008-10-10
forum: Multimedia Software
---

### Post by zephyrusrain on 2008-10-10
Hello,
I've been trying to get my USB DAC (uses a TI PCM2702) to work with JACK on Ubuntu Studio but it has failed to do so.
Any ideas on how to solve it? It works fine on Alsa though.
Thanks.

This is what I get from the messages using JACK Control
```

01:50:58.256 JACK is starting...
01:50:58.256 jackstart -R -p128 -t5000 -dalsa -dhw:1 -r44100 -p32 -n3 -D -Phw:1
01:50:58.272 Could not start JACK. Sorry.
01:51:01.364 JACK was stopped with exit status=255.
01:51:01.365 Post-shutdown script...
01:51:01.367 killall jackd
jackd: no process killed
01:51:01.774 Post-shutdown script terminated with exit status=256.

```

And here's an image of my Jack Control settings
[URL=http://imageshack.us][IMG]http://img56.imageshack.us/img56/4774/screenshotbr6.png[/IMG]

---

### Post by zephyrusrain on 2008-10-12
Bumpers

---

