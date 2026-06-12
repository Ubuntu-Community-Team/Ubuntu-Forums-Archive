---
title: "linuxsampler woes"
date: 2006-05-13
forum: Multimedia &amp; Video
---

### Post by p0llux on 2006-05-13
I'm currently struggeling to get linuxsampler working. At first, the JACK output wasn't detected even though jackd was running, so I had to recompile (apt-get source linuxsampler .. dpkg-buildpackage .. dpkg -i). Now, the JACK output issues seem to be fixed, but linuxsampler is unable to create an ALSA midi input:
```
00:53:56.552 New MIDI device lscp_create_midi_device: Error opening ALSA sequencer (errno=0)
00:53:56.557 New MIDI device Could not create device. Sorry.
ALSA lib seq.c:911:(snd_seq_open_conf) symbol _snd_seq_hw_open is not defined inside (null)
Error opening ALSA sequencer
```
This happens both with my self-compiled version and the version from the repositories (linuxsampler_0.3.2.99+0.3.3-cvs-0ubuntu1_i386).
I'm running the most current version of dapper. Any ideas? Cheers!

---

### Post by dolson on 2006-05-13
Well, from the error output, I think it is probably to do with not having the sequencer modules loaded.

[http://www.ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer](http://www.ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer)

Let me know if that works.

---

### Post by p0llux on 2006-05-14
Unfortunately not. The timidity synthesizer _does_ work but I've got big latency problems with it. Timidity can create the necessary midi input ports whilst linuxsampler can't. I'm guessing that it's either a bug in linuxsampler or has something to do with compiling against outdated alsa libs or something.

---

### Post by __VinT__ on 2006-05-22
Hi 
you nead to load module for you sound card 
for exampler for my card (Delta Audiophile 2496) is modprobe snd-card-ice1712
for creative for example is modprobe snd-emu10k1-synth

for details information you need know you sound card chip 
this information you find in [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

---

### Post by p0llux on 2006-05-22
the audio card's modules are loaded and working. timidity which has almost the same functionality works almost flawlessly, only the response time is rubbish.
I haven't got time for playing with the current cvs source of linuxsampler, but I'll probably look into it next weekend or so.

---

