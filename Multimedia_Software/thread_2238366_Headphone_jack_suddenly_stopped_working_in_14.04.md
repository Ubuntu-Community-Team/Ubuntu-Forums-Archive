---
title: "Headphone jack suddenly stopped working in 14.04"
date: 2014-08-07
forum: Multimedia Software
---

### Post by Jon_Goiri on 2014-08-07
Hello,

Just a few weeks ago I bought a new XPS13 9333 laptop and successfully got Lubuntu 14.04 running on it. It was working great until yesterday I booted into my system and my usual headphones didn't work. I tried a few different sets that work fine with my phone but still couldn't get any output from the computer, while my speakers work just fine.

Strangely, I could almost get them working if I didn't plug them in all the way and wiggled them around a certain way, but after deleting my .config/pulse folder this is no longer the case. Opening alsamixer and plugging them into and out of the jack I see that the speakers get muted and unmuted automatically, so I assume that mens they're detected. I really hope this isn't a hardware problem, but the fact that they're detected gives me hope, as well as the fact that as they're being plugged in I get the usual crackling sound until they're in all the way.

Does anyone know how I can fix this, or at least diagnose the problem? I am comfortable on the command line, but am not an expert when it comes to all the system configuration files.

Any help is appreciated, thank you!

---

### Post by Jon_Goiri on 2014-08-07
Computers work in mysterious ways. I don't know what caused my sound to get messed up but I was relieved to find out my computer wasn't able to hear the input from my microphone. The fix was to reinstall all the drivers and kill all my settings:

```

rm -r ~/.config/pulse ~/.config/pavucontrol.ini

```
I believe depending on what you're using, the pulse settings might be under ~/.pulse

```

sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload
sudo reboot

```

I confess I'm not sure if the third command on the block above is necessary, but it didn't hurt. Special thanks to [itsfoss]("http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/").

---

