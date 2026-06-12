---
title: "Ardour/Jack quality"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by cmbryan on 2006-12-06
Hello, this is my first post to the forum.

I've been using (k)ubuntu on my desktop for a few months with great results, and I'm running edgy now on a new dell 1505 with

"Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)"

and

"IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)"

I have JACK, etc. installed, and working great with most apps except for Ardour.

The default ardour latency produces a quick, periodic clicking or popping, which changes frequency as I change the latency (of ardour)!  Strangely, setting the latency to 32 (the smallest value) removes the periodic artifacts, but produces aperiodic hesitations and a load of xruns, as would be expected with < 1ms latency :???:  I'm just playing a single track, with no effects.

So, why do higher latencies have issues?  Why only ardour?  Is it the kernel, the hard drive, or the audio card?

Any info or guesses are appreciated :D

---

### Post by cmbryan on 2006-12-07
Sucess! :-D

After more playing with Jack settings, I found that the "periods/buffer" parameter was the key.  For me it needs to be > 2.

My settings:

Frames/Period: 32
Sample Rate: 44100
Periods/Buffer: 4


Latency: 2.9 msec

Woohoo!! :-D

p.s. This is with the 64studio kernel on edgy, which does everything except support the 2nd core of my duo... I'm now rebooting into the stock kernel to see what performance I get there.

---

### Post by Max-B on 2007-01-03
Thanks very much! Your suggestion was very useful also for me!!
MAx-B

---

