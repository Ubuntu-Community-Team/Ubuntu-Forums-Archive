---
title: "Mplayer digital passthrough working, but no stereo?"
date: 2010-06-15
forum: Multimedia Software
---

### Post by colinmb on 2010-06-15
I have a SB Audigy 2 ZS with its digital output connected to one of the digital audio inputs on my Marantz receiver. The receiver is capable of decoding Dolby/DTS streams, so I want to pass such digital streams through to the receiver whenever possible. Otherwise, I simply want to play audio on the appropriate channels (i.e. stereo output to the two front speakers.)

According to the [Mplayer manual]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-surround.html"), I should include the following in the config file to enable AC-3 and DTS audio passthrough:

```
afm=hwac3
```This works -- if I play a movie with encoded multichannel audio, the audio is passed through and decoded correctly by the receiver. However, when I play a normal stereo audio file, I hear nothing at all.

To play stereo audio over the digital output, do I need an .asoundrc file, or does mplayer need additional configuration options?

--Colin

---

### Post by xzero1 on 2010-06-15
For movies you might need to add in fallbacks incase there is no ac3 track.
Say, mplayer ... -ac hwdts,hwac3,a52,mad ...

---

### Post by colinmb on 2010-06-16
> **xzero1 said:**
> For movies you might need to add in fallbacks incase there is no ac3 track.
Say, mplayer ... -ac hwdts,hwac3,a52,mad ...

According to the manual (section 4.1.3 [here]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-surround.html")), the fallback on other codecs should happen automatically when using the "afm" option.

In any case, this is solved. I had an .asoundrc in place, and digital stereo output began working when I removed it. Digital audio output also works through XBMC, in which I selected the options to indicate that my receiver is Dolby/DTS capable.

--Colin

---

