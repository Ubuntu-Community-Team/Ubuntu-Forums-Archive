---
title: "Sox mangles audio files...how can I fix it?"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by bpont on 2007-07-11
I've installed a package called 'grandfatherclock' that tolls at programmed intervals and plays a given audio file using sox.  The problem is that when sox plays the file, in this case, an .au file, it sounds totally distorted and overdriven.  I remember the same problem with the package 'amsn', which apparently was using sox as it's audio engine.

How can I get sox to play the file correctly, or alternatively, get grandfatherclock or other apps to use alsa, instead of sox?

---

### Post by Gremlinzzz on 2007-07-11
Remove the sox see what happens
:guitar:

---

### Post by bpont on 2007-07-11
> **Gremlinzzz said:**
> Remove the sox see what happens
:guitar:

I'd rather not screw up my system, since I don't know what else depends on sox being present.  Thanks anyway.

---

### Post by Gremlinzzz on 2007-07-12
A universal sound sample translator
SOX (SOund eXchange) is a generic utility for translating
sound files from one format to another, possibly performing
a sound effect at the same time. Sox is able to handle formats
like .ogg (vorbis), mp3, wav, aiff, voc, snd, au, gsm and several
more.

Homepage: [http://sox.sourceforge.net](http://sox.sourceforge.net)
:guitar:

---

### Post by bpont on 2007-07-12
> **Gremlinzzz said:**
> A universal sound sample translator
SOX (SOund eXchange) is a generic utility for translating
sound files from one format to another, possibly performing
a sound effect at the same time. Sox is able to handle formats
like .ogg (vorbis), mp3, wav, aiff, voc, snd, au, gsm and several
more.

Homepage: [http://sox.sourceforge.net](http://sox.sourceforge.net)
:guitar:

Yes, i already read the enormous man page too.  That still won't tell me what is depending on sox (not just this particular app), why sound files handled by sox (play) sound mangled, distorted and overdriven, how I can correct that, or if not possible, how I can get apps (like grandfatherclock) to use an alternative.

---

