---
title: "How to record all JACK output!???"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by lopzided on 2006-07-11
hey all,
i've been doing some pretty cool stuff by running 3-5 instances of amSynth and hydrogen at the same time, using hydrogen as my beat machine and my synths as basslines and such....

now i'd really like to record them while coming up with them!  what can i use to record all JACK output?  i've looked everywhere and haven't found a solution :((

thanks in advance!

lopz.

---

### Post by zettberlin on 2006-07-11
use qjackctl to connect the outputs to a jackaware audiorecorder of your choice.

I do as follows:

if i want only a stereowavefile that contains whatever outputs i like to capture i use qarecord --jack this is a little recorderapp that just writes any given input to a wavefile on disk. You may want to connect any outputs to its inputs.

if i want to do as described in your example, i create a project in ardour and use ardours track/bus-inspector to connect the outputs to seperate tracks inputs, enable "r" and hit the recordbutton - 

thats it ;-) :-)

---

### Post by lopzided on 2006-07-11
> **zettberlin said:**
> use qjackctl to connect the outputs to a jackaware audiorecorder of your choice.

I do as follows:

if i want only a stereowavefile that contains whatever outputs i like to capture i use qarecord --jack this is a little recorderapp that just writes any given input to a wavefile on disk. You may want to connect any outputs to its inputs.

if i want to do as described in your example, i create a project in ardour and use ardours track/bus-inspector to connect the outputs to seperate tracks inputs, enable "r" and hit the recordbutton - 

thats it ;-) :-)

the qarecord --jack does exactly what i wanted...a small, simple recorder....thanks, zettberlin!  :D:D

---

### Post by dolson on 2006-07-11
Another one that is handy to have running when you're just experimenting is TimeMachine.. If you come up with something good, just hit record and it will save the previous 10 seconds and continue recording until you hit stop. Or you can just hit record and play away and it'll do what you want.

---

