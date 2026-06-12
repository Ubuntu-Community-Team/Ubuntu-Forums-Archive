---
title: "Using pulseaudio simultanious output, need to route one input out this"
date: 2009-10-17
forum: Multimedia Software
---

### Post by Seaweed on 2009-10-17
Hi everyone, my current sound setup is this

Pulseaudio sound server, 
Onboard soundcard connected to one set of speakers
Second soundcard connected to another
Pulseaudio simultaneous output  

This was the perfect solution for my needs as it allowed me to use both my current sets of speakers at once for all my computers. However I currently have a problem regarding inputs which I have been unable to solve.

I would like to route the sound from my TV through both sets of speakers from the line-in on one of the sound cards. The closest I have got so far is by turning up the capture feedback on on of the cards, however the result of this is that the sound is routed only out one set of speakers and not through pulseaudio and the quality is poor.  

Any help getting this set up would be much appreciated, ideally I would like to use inputs on both sound cards to route sound from two different sources directly out the speakers, however one working input is my current priority.

---

### Post by Seaweed on 2009-10-21
I was under the impression this would be possible, can anyone let me know if this is not the case?

---

### Post by theresonant on 2010-04-08
Sorry for seeing this post so late, and for the late reply.

As far as I know, when you want to route audio, you want JACK. It's built on the "plug cable here" paradigm, where every program that makes sound has two "cables" (left and right) and you can plug those cables into other two "slots" (which are inputs of a program).

Apparently, PulseAudio supports routing through JACK. Please read on this matter, as it might help you.

Cheers!

---

