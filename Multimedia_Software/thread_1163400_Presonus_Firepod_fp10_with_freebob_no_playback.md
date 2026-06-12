---
title: "Presonus Firepod fp10 with freebob no playback"
date: 2009-05-18
forum: Multimedia Software
---

### Post by Firepod on 2009-05-18
QUESTION:

using audacity audio recorder, how do I get jack to playback WHILE I record (duplex audio)? 

PROBLEM:

When I set the output and input channels for audacity both to the "Jack" settings, set the option "Playback While Recording" to "true", and then I record with more than 1 track i get: Error while opening sound device. Please check the input device settings and the project sample rate.

I am unable to hear playback at all in any program


i attached screenshots from my connections page in the jack control gui (in case this is evidence of something)

Any help is greatly appreciated. Thank you very much

P.S. I originally posted this weeks ago with no responses. Please someone help!!!! Even if you know only a piece of the solution! I am that desperate!



INITIAL SETUP (if useful):
fresh ubuntu hardy heron install
through synaptic, I installed ubuntu studio
system>administration>ubuntu studio controls: checked all options, set memlock to 95%
set permissions as exactly specified by this: [http://freebob.sourceforge.net/index.php/FAQ](http://freebob.sourceforge.net/index.php/FAQ)
loaded jack control, in setup chose the following:
realtime
driver: freebob
interface: hw:0

---

