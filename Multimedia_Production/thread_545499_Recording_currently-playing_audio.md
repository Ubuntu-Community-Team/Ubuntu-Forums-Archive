---
title: "Recording currently-playing audio"
date: 2007-09-07
forum: Multimedia Production
---

### Post by professorchaos on 2007-09-07
I'm using ZynAddSubFX to play MIDI in Rosegarden, and trying to use Audacity (or any recording program) to record it, but whatever I try doesn't work. It plays fine, but trying to record it yields silence on playback. Anyone know how to record audio that is playing?

---

### Post by 5-HT on 2007-09-07
Are you using JACK with Rosegarden and ZynAddSubFX?
AFAIK, Audacity doesn't support JACK (yet?). Ardour will work perfectly though. Just configure the I/Os and channels as you like for JACK, as Ardour will not handle those itself (which is a good thing). Best bet is to run all three under JACK so that transport is not an issue (you can even sync up some sources, e.g., have Ardour start recording when playback in Rosegarden starts.)
cheers,

---

### Post by professorchaos on 2007-09-07
Yeah, I'm using JACK.
Sounds fine, but the thing is, I've done it with Audacity before, and I'm wondering if anyone can help me figure out how. But in the meantime I'll try Ardour, thanks.

---

### Post by professorchaos on 2007-09-08
Oh, and how do I...do those things?

---

### Post by professorchaos on 2007-09-10
Um, normally, I don't like to bump, but...BUMP.

---

### Post by professorchaos on 2007-09-13
Come on, someone must know....

---

### Post by kayosiii on 2007-09-13
The current beta version of Audacity supports Jack. You will however need to track down a suitable version or compile it yourself. It may be possible to get the stable version to use the soundcards output as the input device (certainly I used to do this with krec) unfortunately I have upgraded to the beta and no longer have the stable audacity so I can't help much.

My other suggestion would be to use something like time machine (simple recording program for jack). to record and simply open the resulting files in Audacity.

---

### Post by professorchaos on 2007-09-14
Thanks a lot, that's all I needed. Just something to record. Worked great!

---

