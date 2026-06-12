---
title: "gnuboy lags with sound on. SDL problem?"
date: 2009-07-14
forum: Multimedia Software
---

### Post by loup.vaillant on 2009-07-14
Hello,

I am trying to use a game boy emulator. I managed to run gnuboy (sdlgnuboy) and Visual Boy Advance.

Both run flawlessly with the sound turned off.
Both lag with the sound turned on. They also make a crackling noise.

If I lower the sound sample rate of gnuboy to unacceptable levels (like under 8000), it doesn't lag anymore. According to top, the CPU isn't the bottleneck —30% at most with gnuboy, sampling rate to 44100.

I run Ubuntu 9.04 with a laptop which have Intel hardware (HDA Intel-ALC883 according to my sound control panel). gnuboy and visual boy advance are installed through synaptic. As far as I know, my system is up to date.

I also folowed the guide to have better intel graphics drivers (newer kernel and such), if that matters.

My question is, can I make gnuboy run with no lag and good sound? How so?
Thanks,
Loup

---

### Post by igorzwx on 2009-07-14
In theory, games should not work with PulseAudio on an old box.
In practice, I have never tried.

---

### Post by loup.vaillant on 2009-07-15
Ok, thanks.

Now, how do I avoid Pulse Audio?
Is it just some configuration thing or do I have to compile gnuboy (or SDL_mixer) myself?

---

### Post by igorzwx on 2009-07-15
It is not difficult to get rid of Pulse.
But this may cause other problems.
You can, for example, change to OSS4 sound system,
but USB audio devices are not supported, and
something else too.

read this:
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

---

### Post by loup.vaillant on 2009-07-15
As it turns out, I *didn't* use pulseaudio for sdl games.

@Igorzwx: thanks for your hint, it made me look here:
[http://doc.ubuntu-fr.org/pulseaudio](http://doc.ubuntu-fr.org/pulseaudio) (french)
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

So, I installed the [libsdl1.2debian-pulseaudio]("apt://libsdl1.2debian-pulseaudio") package, (and uninstalled [libsdl1.2debian-alsa]("apt://libsdl1.2debian-alsa") which was there in the first place).

Now, gnuboy works like a charm (I think). No lag, and the sound is almost perfect (still a few cracks, but that may be to gnuboy's fault, I don't know).

Virtual Boy Advance still lags, but differently: the sound doesn't lag at all, and frames are skiped at some times.

Cheers,
Loup

---

