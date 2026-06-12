---
title: "[SOLVED] Sound Choppy - Dell Inspiron 9400"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by dan_s28 on 2007-09-17
Hello,
I am having a strange sound problem. Sounds works perfectly in XMMS / Mplayer / Firefox (YouTube) and even simultaneously while running sound bouth in xmms and youtube.

The problem is any game, it is choppy - and not just a little pop, but it is unsuably choppy.

Games I have tried: Frozen Bubble, Second Life, these applications could be using OSS?
NOTE: Abuse sounded ok, even with XMMS playing.

Thanks for any help.

Here is my sndstat output:

Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux dsubnix01 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xefffc000 irq 20

Audio devices:
0: STAC92xx Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: SigmaTel STAC9200

---

### Post by dan_s28 on 2007-09-18
This is partially solved. 
If I maximize the game (i.e Frozen Bubble or Second Life) the sound problem gets better, not perfect but better. This is such an odd issue to see on a high powered machine... i mean frozen bubble isnt exactly quake4! In GLXGears with the window maximized I am getting over 1000 FPS, with it windowed 17,000.

This shows me it is related to the video card drivers. I figured this out browsing the [http://www.fmod.org/](http://www.fmod.org/) forums. 

I used Envy ([http://albertomilone.com/pmwiki/pmwiki.php?n=Main.HomePage](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.HomePage)) to update my Nvidia driver to the latest. Which worked correctly (except it set my default screen to 16bit depth -switched it back to 24bit in xorg.conf).

I will just live with the sound issues for now, it appears to be as good as it gets. 

Thanks,
D

---

