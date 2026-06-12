---
title: "No Sound with Hauppauge PVR 150 under Feisty (as FM tuner)"
date: 2008-05-21
forum: Multimedia Software
---

### Post by hellion0 on 2008-05-21
Don't know if this is the right place, but I think it fits. 

I'm running Feisty on my desktop machine, and today I hooked a Hauppauge PVR 150 (this one has an FM radio input) up to it. Feisty seems to see the card fine as /dev/radio0. I installed Gnomeradio thru Synaptic, and fired it up... and there's no sound from it. Plenty of signal, just no sound.

Sound on the system runs fine otherwise (ALSA through a C-Media PCI CMI8738), it is only when I try to listen to FM radio that there's no sound. 

I've never tried working with a FM/TV tuner card before, so I don't know where to start other than the obvious "Is sound broken" question. I've checked, and while there's plenty of info on getting live TV working, there's little info on working with the FM tuner.

For all I know, it's just one minor broken config that's easily fixed with nano. I'm just in over my head on this one with no idea where to begin.

Thanks in advance for any assistance.

---

### Post by wolfen69 on 2008-05-25
did you install ivtv-utils?

---

### Post by hellion0 on 2008-05-28
I just installed ivtv-utils and tried "ivtv-radio -f 105.30" (a fairly good signal in this location).

```
taralyn@gardevoir:~$ ivtv-radio -f 105.30
set to freq 105.30
Running: aplay -f dat < /dev/video24
Playing raw data 'stdin' : Signed 16 bit Little Endian, Rate 48000 Hz, Stereo
```

It's seeing a stereo signal, so at least it's picking up signals. There is still absolutely no sound from FM radio.

I tried routing the sound directly to my sound card (which I'm assuming is /dev/audio), but then I get this:

```
taralyn@gardevoir:~$ ivtv-radio -f 105.30 -i /dev/audio 
set to freq 105.30
/dev/audio belongs to a different ivtv driver then /dev/radio0.
Run ivtv-detect to discover the correct radio/PCM out combination.
```

There's no ivtv-detect to be found on my system, even after installing everything related to ivtv on my system.

---

