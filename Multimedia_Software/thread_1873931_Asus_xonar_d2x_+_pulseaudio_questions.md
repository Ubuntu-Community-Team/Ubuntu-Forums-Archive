---
title: "Asus xonar d2x + pulseaudio questions"
date: 2011-11-02
forum: Multimedia Software
---

### Post by d0m1nation on 2011-11-02
I recently bought the Xonar d2x for my media machine. And overall I'm happy with it, I didn't have to install any drivers it was pretty much plug in play.

I've been tinkering a bit with /etc/pulse/daemon.conf to up the sound quality. These are the the values I run today:

```

resample-method = src-sinc-best-quality
high-priority = yes
default-sample-channels = 2
default-sample-format = float32le
default-sample-rate = 96000
default-fragments = 8
default-fragment-size-msec = 5

```

But checking my process tree pulse audio is pretty cpu intensive.
I thought having a separate hardware audio card would put the load on the actual card and not the cpu or is there something I've missed?
I've read that pulse can be a real cpu hog and that it might not be the optimal solution for my setup but having tried to change audio manager in the past and it always ended up with failure I find the whole thing quite scary.

I pretty much just wanna get as much as I can out of this card.

My setup:
i3-2100
ASUS P8H67
Corsair XMS3 4GB DDR3
Asus Xonar d2x

Media players I use:
mpd
xbmc

---

### Post by DrLabman on 2011-12-06
Most audio is output to pulse audio at 44100hz or 48000hz at 16bit, you are telling pulseaudio to resample this to a 32bit float at 96000hz using the best quality resampling algorithm and submit it to your sound card. This resampling is done by the CPU before it gets to the sound card.

To lower the CPU usage either change the default sample rate so that it matches what most audio streams use so that resampling doesn't have to happen or lower the resampling algorithm quality.

---

### Post by swejuggalo on 2012-06-20
I have this soundcard too now. I've found this link stating that you do not need to set the default-sample-rate.

[http://proaudio.tuxfamily.org/wiki/index.php?title=PulseAudio](http://proaudio.tuxfamily.org/wiki/index.php?title=PulseAudio)

---

