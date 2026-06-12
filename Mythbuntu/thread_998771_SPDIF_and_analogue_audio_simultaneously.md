---
title: "S/PDIF and analogue audio simultaneously"
date: 2008-12-01
forum: Mythbuntu
---

### Post by fatmonk on 2008-12-01
I've seen threads about this before, but I made a discovery last night that suprised me.

I would like to be able to output audio from Myth simultaneously on my motherboard's analogue audio output (to the TV's analogue audio in) and from the motherboard's S/PDIF optical output (to my 5.1 decoder etc).

I currently have the S/PDIF working fine and it sounds good, but having the analogue output working for watching bog standard 2.0 TV would save me (or the other half) having to switch the hi-fi on when watching no surround stuff (plus my plan down the line is to move the center speaker away from the TV when I eventually get around to putting a projector in).

What I spotted last night was that **both the analogue out and the S/PDIF are active when watching apple trailers through Myth!**

Only the S/PDIF is active elsewhere.

Is there a way to configure Myth so that both are active all of the time? It's obviously possible with the hardware and kernel I have...

Obviously it would require a downmix of the audio on the analogue out, but the system must be doing that anyway somewheer to be able to use the analogue at all...

-FM

---

### Post by ElGeraldo on 2008-12-12
> **fatmonk said:**
> 
I would like to be able to output audio from Myth simultaneously on my motherboard's analogue audio output (to the TV's analogue audio in) and from the motherboard's S/PDIF optical output (to my 5.1 decoder etc).
I have the same requirement, but on a different motherboard - ASUS M3A78-EM, and with Mythbuntu 8.04. I want the analogue output for the TV in my bedroom, but the SPDIF for the Yamaha 5.1 amp in the family room. The analogue audio out worked by default and I can get the SPDIF output working by changing the "Audio output device" setting in the Mythfrontend GUI from ALSA:default to ALSA:SPDIF. However, it doesn't matter how much I tinker with the Mythfrontend settings; I can only have one or the other.

Anyone know how you get both at once...?

---

### Post by Caps18 on 2008-12-12
I'm looking to do the same thing, but I haven't tried very hard to get it working.

Does anybody have a good soundcard that was easy to get this feature working in?

---

### Post by fatmonk on 2008-12-18
The thing that really makes me think that this must be possible is that it _just works_ in the streaming (Apple Trailers etc) function.

I have ALSA:SPDIF selected as my audio output device in the general setup screens, but the streaming video application within Myth also outputs audio on the analogue outs in there...

Somebody MUST know how to do this, surely?

Or at least know what the difference is between TV, local video and music playback and the streaming video playback...

-FM

---

