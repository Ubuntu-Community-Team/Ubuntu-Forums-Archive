---
title: "Wine+jack audio dies after a few seconds"
date: 2012-02-07
forum: Multimedia Software
---

### Post by buntuyu on 2012-02-07
When I run wine and audio apps, such as audacity (windows version), my jack audio works for a few seconds, then fails with qjackctl messages window saying:

subgraph starting at PulseAudio JACK Sink timed out (subgraph_wait_fd=24, status = 0, state = Finished, pollret = 0 revents = 0x0)
**** alsa_pcm: xrun of at least 1.657 msecs
14:39:04.698 JACK connection graph change.
14:39:04.710 XRUN callback (2).
14:39:04.811 JACK connection change.

---------------

I found out, by tinkering, that the duration of the audio working (the few seconds) changes as I change the "Frames/Period" value in the qjackctl settings. As I increase this value, from 512 --> 1024 --> 2048 --> 4096, the duration increases (I haven't timed it exactly to see if it doubles, in a linear correspondence to the doubling of the value)


Can anyone PLEASE offer tips on how to make jack work with wine!? 

It seems to ALMOST work --> it starts out fine, then dies.  If I restart the wine app, it resets and plays again, for the brief duration.

I'm on an up-to-date 10.10

TIA!

---

### Post by buntuyu on 2012-02-08
This is not to really to "bump" but to draw attention to a major correction. The original post said the "message window" is part of audacity. That was a gross error: it is the qjackctl message window that contains the xrun errors.

Also, if there is a way to record wine audio WITHOUT jack, i'll take THAT solution, too!

TIA

---

### Post by buntuyu on 2012-02-22
bump
(this time it IS a bump)

---

