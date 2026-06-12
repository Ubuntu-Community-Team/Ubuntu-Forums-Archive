---
title: "OSS + JACK + Ardour + Rosegarden?"
date: 2007-07-29
forum: Multimedia Production
---

### Post by HarmonicRhythm on 2007-07-29
Hi,

I'm planning on installing Ubuntu Studio and have done some reading to see if my hardware will work properly and I can make music without too much trouble.
However I've gotten some serious doubts about this now after reading about trouble ppl have had
.
I have a Lynx One soundcard which requires OSS drivers.
Will OSS allow me to use Ardour to record while synced to programs for MIDI (for external synth) such as Rosegarden through JACK? (and maybe also synced to JAMin etc)
Or would this get me into trouble and I'd better get a different soundcard (external USB) that ALSA supports?

Many thanks in advance,
Marcel

---

### Post by 5-HT on 2007-07-30
Shouldn't be a problem in general as long as your card has either ALSA or OSS support. JACK can use either as a backend interface to your hardware. OSS will be a bridge between you card and JACK. All sound apps will run through JACK (so long as they can use JACK: ardour needs to). Best to give it a try and see how things go first. If you don't have Ubuntu installed, just fire up a live CD, install JACK, ardour, rosegarden, and any other desired apps to do a test drive (they'll all be stored in RAM). No need to do a full install of Ubuntu Studio just to find out about  any problems after the fact.
cheers,

---

### Post by HarmonicRhythm on 2007-07-30
Thanks for the reply! Was hoping to hear this :)

---

### Post by HarmonicRhythm on 2007-07-30
Hmm couldn't help but do some more reading and found out that while many audio apps work with JACK just about no MIDI apps work with JACK MIDI (rosegarden won't for instance). Almost all MIDI apps use ALSA.
Also I must use SCALA ( for retuning / microtuning MIDI in realtime) and the SCALA needs ALSA virtual MIDI for this :(

So my question is, is it currently or will it very soon be possible to use ALSA while using OSS for soundcard driver?
I read something about virtual ALSA under the new OSS 4 but couldn't make much sense of it if it'll work for me or not.

---

### Post by HarmonicRhythm on 2007-07-30
Ah never mind.. f*ck Lynx Studio for not openly releasing driver info.

I'll go sell it and get something that has ALSA drivers and be happy.

---

### Post by fredj on 2007-08-03
Don't be too hasty. Have you checked on the Alsa website to see if your
soundcard is supported. Some Lynx soundcards are supported under Alsa.

---

