---
title: "[SOLVED] Sound configured just fine - remains silent though"
date: 2008-07-19
forum: Multimedia Software
---

### Post by krizz_two on 2008-07-19
Hello everybody!

My current situation: I have recently installed Ubuntu Hardy Heron 8.04.1 Server LTS Edition - At first without a graphical interface, but now I added the Desktop, too.

The problem I have now: The sound seems to be configured just fine - still I get to hear nothing at all.

I wanted to see if this was a general Ubuntu 8.04-Problem with my hardware, so I booted into the Desktop Live-CD (Ubuntu 8.04 too), and the sound works straight away.

According to that "Comprehensive Sound Problems Solution Guide", everything is the way it should be:

```
root@themachine:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And I checked alsamixer, nothing is muted, everthing set to max.
No application complains about not being able open a sound device.
The gnome audio settings look fine too - I tried different combinations here, but nothing changes. The test buttons always open a window that tells me the test sound is playing, no error messages here either.


Is there any way to easily migrate every sound related setting from the Live CD (where it magically works) to my regular installation - where it mysteriosly doesn't work?

Thanks for any help in advance!

Chris

PS: Whatever you need to know in addition to what I told you already, just ask - I'll post it asap. Didn't want to make this too long to read.

---

### Post by krizz_two on 2008-07-19
Alright, although trying every possible combinations of switches is NP-complete - it sometimes helps. Some stupid hidden mixer setting muted the damn thing.
Sorry to bother you anyway.

---

### Post by phunqe on 2008-07-25
Could you please list which switch(es) you found working?

---

### Post by krizz_two on 2008-07-25
I finally discovered a slider labeled "Front", which was muted. Turning off the mute on that one did it. Hope that helps you too.

Watch out for both things: Channels can be muted AND turned all the way down.

---

### Post by phunqe on 2008-07-25
I'll check that out, cheers.

---

### Post by msmr on 2008-07-25
I actually am having the same problem but with mine it's. 

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
msmr@TARDIS:~$ 
```

I don't know how to put in the command you put in, bascially I decided to go into my bios and turn on my intergrated sounded, however, even though ALSA detects it, nothing plays.

I went into alsamixer and everything is unmuted.

I have no tried the live CD to see if it works, but maybe I will.

---

### Post by msmr on 2008-07-25
Nope in live CD and still no sound.

---

### Post by krizz_two on 2008-07-26
I'd play around some more, even try to mute a few channels then. Soundcards sometimes have the weirdest features, such as "virtual surround" and such crap. And that is often controlled via channel sliders.

---

