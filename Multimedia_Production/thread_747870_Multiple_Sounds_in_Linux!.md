---
title: "Multiple Sounds in Linux?!?"
date: 2008-04-07
forum: Multimedia Production
---

### Post by Slacker.ksg5 on 2008-04-07
Well I do know that this is a common discussion, but I just wanted to see if I could dig deeper.

So my question begins with why is it not possible to run simultaneous audio files?

My logic behind this as a beginning programmer is for whatever reason the audio drivers were never written to be implemented more than once? I want to say multi-threading... but thats not right.

Wouldn't it be a really simple fix if one wanted to simultaneously listen to multiple audio files?

Sorry I dont know much about the behind the scenes look at it, but I would certainly like to if someone would kindly point me in the right direction.

---

### Post by Gen2ly on 2008-04-07
Hmm my system does just fine with multiple streams.  What application(s) are not able to do the multiple audio streams?

---

### Post by SunnyRabbiera on 2008-04-07
well people are working ways around this, its gotten better as now I can more then one sound but it depends on what is running.

---

### Post by Slacker.ksg5 on 2008-04-07
how about wine  and xmms =(

---

### Post by thorgal on 2008-04-07
use pulseaudio for general sound purpose. Pulseaudio not only plays multiple streams  (aka from many apps) but also from your LAN if remote clients are allowed to access the pulseaudio server. This is really cool because you don't have to use stuff like JACK which are for very specific purposes. Even the flash player plugin runs through pulseaudio (you need the libflashsupport and declare "padsp" as your dsp wrapper in /etc/firefox/firefoxrc). Give it a try! I also use it through JACK since it has JACK support and redirect sound from my laptop to my studio PC connected to my pro speakers (I get a BIG sound from movies, amarok, etc). Pulseaudio is the way to go!

---

