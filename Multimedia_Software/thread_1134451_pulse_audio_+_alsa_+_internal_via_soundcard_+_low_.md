---
title: "pulse audio + alsa + internal via soundcard + low volume"
date: 2009-04-23
forum: Multimedia Software
---

### Post by sefs on 2009-04-23
Hi all,

I've removed my SBLive sound card.  It had good volume.  I am now using my internal soundcard its a via but the sound is incredibly low.  Is there anyway to jack it up?

Thanks.

---

### Post by AlanPorter on 2009-04-25
From what I understand, your apps send the sound to PA, which sends it to ALSA, which actually talks to the hardware.

You can set the PA mixer levels using an app like pavucontrol.

You can set the ALSA mixer level using an app like alsamixer.

The trick, however, is to tell alsamixer to set the volume levels for the actual hardware card.  If PA is installed, it may just show you a single slider for "pulse", and it won't show you the sliders for your actual hardware.

You can use the "-c" command line option to specify which hardware (the actual card or pulse) to set volumes for.

For me, "alsamixer -c 0" shows the hardware volume levels, and "alsamixer" by itself shows a single slider for pulse.

Alan Porter

---

