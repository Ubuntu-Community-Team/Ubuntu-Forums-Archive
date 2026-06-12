---
title: "RTP MIDI: realtime broadcasting of MIDI over the internet"
date: 2008-10-16
forum: Multimedia Software
---

### Post by rekado on 2008-10-16
Hi all,
as the title suggests I'm looking for a way to broadcast MIDI events in real-time over the internet. I'm playing keyboards in a band in Germany but will move to China soon. Transmitting audio is tough through the internet as it consumes a lot of bandwidth and timing is hard to maintain. With MIDI it could be possible for me to remotely play the keyboard from China with the band members in Germany hearing it.
It's just a fancy idea and as I did some reading it seemed that some kind of RTP-MIDI is implemented in Apple's Mac OSX.

With VLC, pulseaudio, Jack and the like around it doesn't seem to be too much of a dream to set something like this up.

I have to say that I've got no experience with streaming any media (i.e. broadcasting) over RTP / UDP; it never actually worked.

Does anyone have an idea how to transmit MIDI from one machine and receive MIDI events on another one on the other side of the internet?

I would appreciate any comments on this.

---

### Post by markbuntu on 2008-10-16
I think you could do that with netjack though I personally have never tried it. From China to Germany latency will be a problem no matter how you do it.

---

### Post by rekado on 2008-10-17
Thanks, I will check out netjack and report back. From China to Germany latencies are pretty high, but I hope that it won't matter so much with MIDI. For one MIDI event it usually takes about 1ms per message. As MIDI is a serial protocol there is quite high a latency for the last transmitted note of a chord anyway. Using a USB-MIDI-Keyboard, the data reaches my computer much quicker than it would reach a synth over a standard MIDI connection. This speed advantage allows me to send the small data packages that MIDI is made of over the internet without being affected by network latencies too much.

At least this is the idea. I would hear myself through a local synth (either software or hardware) and I could hear the rest of the band through audio streaming (which is hard to achieve with these latencies, though).

---

### Post by rekado on 2008-11-09
Too busy, can't try it. Would be nice however to hear from somebody who actually made something like this work.

---

