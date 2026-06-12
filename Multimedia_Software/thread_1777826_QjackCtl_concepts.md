---
title: "QjackCtl concepts"
date: 2011-06-08
forum: Multimedia Software
---

### Post by Ed_Ziffel on 2011-06-08
Some concept clarification about QjackCtl 

Have a bunch of sound gear, amps, eqs, instruments, pedals etc.  To me input starts at the instrument, a guitar say, which outputs a signal as an input to the preamp which outputs a signal which is an input to the amp which outputs the amplified signal to the speakers.  Like duh huh.  In Qjackctl what is the concept of a Readable Client/ Outputs Ports and Writable Clients / Input Ports?

---

### Post by RaumTrug on 2011-06-08
hmm, yes like cables, actually quite simple. but also "relativity" madness:

I always mix up "input" and "output", for me the readables are "input", because you get input from them, and the writable's output, because you put something in to some "output". other way round of understanding this is of course saying the readables do some output to your jack system, while writables are input to something. important is just that you read the lines from left to right...:lolflag:

 the "readable" ports on the left supply some signal, the "writable" ports on the right make it possible to put a signal into, that is processed by a prog. or fed to the soundcard. so if you connect a readable to a writable, "sound" is read by jack from the readable and written into the writable. in chunks whose size is determined by the latency you configured.

obvious example: readable port of a mic input, writable port that represents you soundcard's output. connect them, and you'll hear on the souncard's output what the mic feeds to the input. like plugging a mic into an amplifier.

a program can of course convert signals from its writable port to a readable, so it can be fed to other program's/the sound card after processing. this is nothing that happens within jack, but within the program that does something with the sound, so it's not "visible" in qjackctl:

take something like jack_rack or whatever with, say, an lsdap reverb (say freeverb) plugin loaded. that should add readable and writable ports of jack_rack to your jack host. connecting the soundcards readable (mic) to rack's writable is like plugging your mic pre-amp into a reverb unit. then connecting the rack's readable to the soundcard's writable connects (like a cable) the reverb unit into the monitoring amp. you now hear your mic with artificial reverb.

if you visualize that like cables, there's now a cable between mic and rack, and one between rack and amp/speakers. the connection between rack input and output is not visualised - there's programs like "patchage", that replace qjackctl, but not jack itself, that let you, for example, arrange the readable/writable stuff like cables, like with jack_rack being a little box with inputs left and outputs right. many people like this a lot better as visualisation than the 2 lists qjackctl provides

obviously, recording software like ardour has writable ports that can be written to by connecting with a readable, and what is written to those ports can be, for example, recorded to disk by the program.

by the way, this is rather a "jack"/"jackd" concept than a "qjackctl" concept, qjackctl is just a gui that visualises what jack does in the background.

hope this clarifies

---

