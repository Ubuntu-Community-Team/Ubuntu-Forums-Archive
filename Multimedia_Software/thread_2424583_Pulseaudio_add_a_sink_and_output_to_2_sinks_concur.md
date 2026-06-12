---
title: "Pulseaudio: add a sink and output to 2 sinks concurrently"
date: 2019-08-11
forum: Multimedia Software
---

### Post by Skaperen on 2019-08-11
is this even possible?  i want to have my executable program be added to Pulseaudio as a sink.  i don't even know what format i'd get the audio stream in, yet.  i guess that would be described in its API documentation (when i find it).  i also would like have Pulseaudio concurrently output to 2 or 3 sinks.  i read one post somewhere that said this was impossible.  seeks like a silly design decision.

i read somewhere that Pulseaudio used shared memory to transfer audio samples with lower latency. i'm guessing some kind of ring buffer would be used.

---

### Post by Holger_Gehrke on 2019-08-11
No need to write your own pa-sink, just use module-pipe-sink to write the output to a fifo and read from that in your program. Format should be raw audio with configurable sample format, sample rate, channels and channel-mapping.

In Pulse a stream has one source and one sink. But there's module-combine-sink to create one virtual sink that links multiple sinks together.

See [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/) for more details, especially the section 'Modules'.

Holger

---

### Post by Skaperen on 2019-08-13
i want to be able to hear the audio uninterrupted when i engage and disengage my program from getting audio.  so i will need to get "module-combine-sink" going first, and hope that "module-pipe-sink" can go idle when nothing is reading the other end (just throw samples into the black-hole-sink).

i still think it's a wrong design for the core audio server to not distribute to as many sinks as requested.  i would have made it like a multi-channel mixer where every sink can get whatever mix of sources it is configured to get, through whatever filters are available.  a GUI app could change the mix settings and visually show a mixer board.

---

### Post by Skaperen on 2019-08-13
i wonder if *module-pipe-sink* can be tricked into writing directly to a regular file.

---

### Post by nik.charles on 2019-09-02
Easy way to have 'Virtual device for simultaneous output on all local sound cards'

install paprefs (Pulseaudio preferences)

Enable option in 'Simultaneous Output' tab

 > i would have made it like a multi-channel mixer where every sink can  get whatever mix of sources it is configured to get, through whatever  filters are available.  a GUI app could change the mix settings and  visually show a mixer board.         

can use JACK for that sort of thing rather Pulseaudio

[http://www.jackaudio.org/applications/](http://www.jackaudio.org/applications/)

---

### Post by Skaperen on 2019-09-03
a real mixer may have multiple outputs and each can output a mix of inputs or at least select among them.  digitally, this would be easy to just copy the same data when one input goes to  two outputs.  PA just doesn't have this concept.  it's big advantage is low latency which not everything needs (gaming does).  listening to music does not.  maybe JACK can do this better.

---

