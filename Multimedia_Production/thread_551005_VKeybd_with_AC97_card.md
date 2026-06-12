---
title: "VKeybd with AC97 card"
date: 2007-09-14
forum: Multimedia Production
---

### Post by Coburn on 2007-09-14
I've tried just about everything I've seen suggested to get VKeybd to make sound.  I am using an AC97 PCI sound card, which is apparently not easy to work with.

FluidSynth gives the following:

```
linda@bluegreen:~$ sudo fluidsynth -m alsa_seq /usr/share/sounds/sf2/EPIANO1.SF2
cca_open_socket: could not connect to host 'localhost', service '14541'
cca_init: could not connect to server 'localhost' - disabling ladcca
fluidsynth: warning: Requested a period size of 64, got 940 instead
fluidsynth: ALSA driver: Using format s16, rw, interleaved

fluidsynth version 1.0.6
Copyright (C) 2000-2002 Peter Hanappe and others.
FLUID Synth comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; see the COPYING file for details.
SoundFont(R) is a registered trademark of E-mu Systems, Inc.

Type 'help' to get information on the shell commands.

>
```

TiMidity does:

```
linda@bluegreen:~$ timidity -iA -B2,8 -Os1l -s 44100 
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 60208, period size 3760 bytes
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3
```

Sorry, no sound with either one.  Obviously they are both running.

Why, BTW is localhost not able to open under FluidSynth?

I don't have snd-intel8x0m running, although on my host computer it _is_ the modem driver.  This was a problem under Hoary.

Another thing I've tried is following the seq24 HowTo and installing everything in the sound universe -- seq24, Hydrogen, etc, etc. and going through the process to make a sample song, and still VKeybd does not make noise.  The other apps do.

> <rant>
Ideally VKeybd should be _packaged_ with a simple soundfont and the proper dependencies to make it not only run, but perform, out of the box, with a variety of hardware configurations.
</rant>

So, as you see, I've tried more things than I've ever had to try to get anything to work on Ubuntu, and still no work.

Let's prove the critics wrong by bridging the gulf between the dev's and the desktop in this one instance .

Thanks,

Coby

---

### Post by Coburn on 2007-09-15
Solved :oops:

In my case all I had to do was post my problem (that helps me think about it more carefully) and sleep on it.  Then I tried to find a way to connect VKeybd's output with a software synthesizer, since I know my AC97 card does not have synth capability.

Using QJackCtl to hook VKeybd to TiMidity (with a soundfont enabled in its config file) was all I needed.

Now if I can just figure out how to put the sounds in realtime with the keystrokes...

Thanks, guys.  Hoipe this is an inspiration to someone.

---

