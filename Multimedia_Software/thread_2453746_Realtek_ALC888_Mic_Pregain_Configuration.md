---
title: "Realtek ALC888 Mic Pregain Configuration?"
date: 2020-11-16
forum: Multimedia Software
---

### Post by ve4cib on 2020-11-16
I have a Realtek ALC888 in a project I'm working on.  According to the datasheet ([http://www.hardwaresecrets.com/datasheets/ALC888_1-0.pdf](http://www.hardwaresecrets.com/datasheets/ALC888_1-0.pdf)) on page 2 there's a "Software selectable boost gain (+10/+20/+30dB) for analog microphone input."  Does anyone know how to actually select this, or if it's even a supported feature in ALSA and/or PulseAudio?  And if it is supported, how do I actually go about configuring it?

The problem I'm having is that turning up the input volume through alsmamixer or pulsemixer just seems to provide overall amplification, meaning there's a lot of background noise on the mic input.  I want to enable microphone pre-gain so that relevant noise is amplified, but not all the background stuff.  I can mitigate this with the echo-cancel PulseAudio module, but that introduces its own issues and digital processing noise.

From what research I've done it appears that Realtek's audio driver is now officially part of the kernel, but I haven't been able to find a list of the supported features, nor how to actually configure the boost gain on Linux.  This is my first time wading this deep into the bowels of Linux audio -- usually it's been a case if "it works well enough -- don't touch it!" for me.  If anyone knows if there's a specific config file I can edit, or parameters I can set when loading a specific PulseAudio module that would be fantastic.  Otherwise I'm stuck with pretty mess audio input for this project.

I'm using a command-line only installation of Ubuntu 18.04, fully updated.  I cannot upgrade the OS for this project, as I'm using ROS Melodic, which is only supported on 18.04.

---

### Post by CatKiller on 2020-11-16
Those selectable gain controls, if they're exposed, show up in alsamixer. It may well still be noisy; there's only so much shielding that's possible and cost effective in an electrically noisy environment like a motherboard.

---

### Post by ve4cib on 2020-11-17
Thanks, I found them.  For some reason I never actually noticed that there was a separate panel to expose all of the input controls.  Temporary selective UI blindness?

Unfortunately it looks like the mic boost was already maximized, which kind of sucks.  Means I might not be able to clean up the audio as much as I wanted.

---

