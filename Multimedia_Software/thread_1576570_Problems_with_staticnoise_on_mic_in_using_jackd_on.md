---
title: "Problems with static/noise on mic in using jackd on aspire one netbook"
date: 2010-09-17
forum: Multimedia Software
---

### Post by coolman12304 on 2010-09-17
Hi all, I'm using 10.1 ubuntu and have alsa and jackd installed.  The problem I am having is that whenever i plug in any audio cable to the microphone in jack on my aspire one netbook and use jack I get a horrible static that is not due to cable interference.  The built in mic works just fine with no interference or anything.  I'm trying to use jackd and rakarrack for my guitar.  Any Ideas?

---

### Post by transmogrifox on 2010-09-18
First of all, a mic input is not designed for the high impedance instrument input.

Also, a computer mic jack puts DC voltage onto the line which is intended to bias the active element in a microphone.

DC current going through a guitar pickup or instrument can increase the noise significantly, while the probability of improper bias puts the mic preamp into a higher noise state.

The solution is to use an electrical interface that is designed to be plugged into a microphone jack.

Really the best solution is to get an inexpensive USB audio interface designed for guitar, like the Behringer UCG-102
[http://www.behringer.com/EN/Products/UCG102.aspx](http://www.behringer.com/EN/Products/UCG102.aspx)

Otherwise you can try to find  a "sweet spot" where turning the volume knob on your guitar...this can be really fiddley because you are essentially using the resistance of the volume pot to ground as a means to bias the microphone input.

If you have a Line input, then it is better to use a good preamp for the guitar and drive the left or right channel with the guitar.

If you don't have money for a proper preamp or audio interface designed for a guitar, then you will have to tolerate the noise.

With Rakarrack you can somewhat get around it by inserting a noise gate or Expander as the first module in the effects chain.  There is plenty of information about this in Rakarrack help (F1)...both about hardware interfaces and about how to use Expander or Noise Gate.  Notice that a dynamic noise gating device only gets rid of the background static....when you play and the gate is open, then the noise is there too...but maybe more tolerable since you can also hear the guitar.

There may be a plugin that uses the FFT for noise removal.  Advanced signal processing comes at a CPU load cost...but it is one software solution for noise reduction.

---

