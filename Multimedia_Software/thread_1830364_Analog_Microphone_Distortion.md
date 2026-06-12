---
title: "Analog Microphone Distortion"
date: 2011-08-21
forum: Multimedia Software
---

### Post by sgtv on 2011-08-21
I successfully installed 11.04 minimal.

I have a strange problem when recording the sound.

1. Playback itself fully works.
2. Internal mic (mono one, which is for webcam) works as expected.

3. Analog mic (where you plug something in jack) does work too, I can hear actual recording, but it produces a very broken, distorted sound. Like it interferes with something heavily or gets boosted / amplified to high levels.

In the meantime, when I plug something in analog jack Ubuntu correctly disables internal one (checked through alsamixer), so it can't be a problem.

Also, I checked recording on Windows and it sounds correctly. So the source signal is all right too.

Any ideas where to start? All threads I seem to see here are all about playback or mic doesn't work, can't find anything dealing with distortion of analog mic.

---

### Post by sgtv on 2011-08-21
Just in case, here's system information from alsamixer:

/proc/asound/version:
```
Advanced Linux Sound Architecture Driver Version 1.0.23
```

/proc/asound/cards
```
Intel         HDA-Intel - HDA Intel
              HDA Intel at 0x94700000 irq 45
```

/proc/asound/devices:
```
1:        : sequencer
2: [ 0- 3]: digital audio playback
3: [ 0- 1]: digital audio playback
4: [ 0- 0]: digital audio playback
5: [ 0- 0]: digital audio capture
6: [ 0- 2]: hardware dependent
7: [ 0- 0]: hardware dependent
8: [ 0]   : control
33:        : timer
```

/proc/asound/timers:
```
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE
```

/proc/asound/pcm:
```
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
00-01: Conexant Digital : Conexant Digital : playback 1
00-03: HDMI 0 : HDMI 0 : playback 1
```

---

### Post by sgtv on 2011-08-21
Just booted from live CD to check if problem comes from my minimal installation. No, same thing happens on live CD. Playback, internal mic ok, analog mic: fail.

To add more to this, the problem didn’t occur on Maverick on the same machine.

I guess I’m totally lost now :-)

Maybe it’s some kind of errant boost setting in audio config?

It would be a pain to constantly revert to Windows just to rec something.

---

### Post by birauser on 2012-01-29
I'm experiencing the same problem on 11.10, oneiric. the soundcard is a realtek intel hda. Playback works beautifully, whereas I have some sort of "bitcrusher-like" distortion whenever I record something through the internal mic - which works flawlessly on Win7.

---

### Post by birauser on 2012-01-29
sorry I didn't see this thread earlier, but, as a matter of fact, the distortion issue was really difficult to define with just a few unambiguous words. 

this workaround fixed the problem for me:

[http://ubuntuforums.org/showthread.php?t=1893142&highlight=distorted](http://ubuntuforums.org/showthread.php?t=1893142&highlight=distorted)

in short:

**if you are having a hard time getting recordings of a good quality due to a crackling noise that renders the audio input rather unusable, especially - but not only - with apps like skype**

here's the fix: you'll have to edit your  /etc/modprobe.d/alsa-base.conf file, adding one of the following lines. the latter worked for me:

```
options snd-hda-intel position_fix=1
```

or 

```
options snd-hda-intel position_fix=2
```

reboot and enjoy.

---

### Post by birauser on 2012-01-31
i must confess this issue baffles me. almost every soundcard out there is an intel hda: how on earth could they ever end up neglecting such an important issue?

---

