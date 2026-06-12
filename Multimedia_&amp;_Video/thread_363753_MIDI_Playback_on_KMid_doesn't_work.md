---
title: "MIDI Playback on KMid doesn't work"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by PacShady on 2007-02-17
Hey all

Trying to get MIDI playback working on Kubuntu Dapper (so I can listen to MIDI files), and I'm having no end of trouble with it.

First, I tried using KMid, and it complained of a /dev/sequencer error. On searching the forum, I found an apparent solution:

```
sudo bash
modprobe snd-seq
echo snd-seq >> /etc/modules
exit
```

Well, that stopped the /dev/sequencer error coming up, but I'm still not getting any sound. KMid seems to be playing the file, but there's no sound coming from the speakers.

I've tried a few other programs, such as qsynth and playmidi, but none of them worked either (qsynth complained of a JACK error, and playmidi couldn't find the device to play to, even when I specified /dev/sequencer).

Any ideas?

'Shady

---

### Post by sgx on 2007-02-17
googlesearch terms: kmid tutorial sequencer 
this yields some answers and tips! Have a great weekend...

---

### Post by PacShady on 2007-02-18
I managed to get MIDI working in Timidity, but I don't like the default lack of GUI. If I play a file, for instance, from Firefox, if I want to stop it I need to run *killall timidity* in the terminal. Also, it seems that volume doesn't like being controlled for them either.

'Shady

---

### Post by axs on 2007-02-21
Hi PacShady,
your post helped me setup my /dev/sequencer. I hope I can help you as well: timidity uses a software synth (that means it emulates a midi device using cpu and /dev/dsp,/dev/audio or such) - KMid on the other hand needs a MIDI Interface like a compatible USB-Midi-Device or onboard MIDI Device. If you have one or more of them configured there is a good chance of your being able to select it in KMid's configuration dialog for Midi options.

An external MIDI Interface is usually used to connect all your keyboards,synthesizers or samplers to use them with sequencing (MIDI =Multiple Instruments Digital Interface) software.

I HTH
AXS

---

