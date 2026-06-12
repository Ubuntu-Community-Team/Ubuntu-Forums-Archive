---
title: "rhythmbox: accessing disk every few seconds while playing"
date: 2010-05-18
forum: Multimedia Software
---

### Post by Antenne on 2010-05-18
Hi all.

I'm running Lucid and have an annoying problem with Rhythmbox: while playing, it constantly accesses the disk, every 2-3 seconds *drrrrd* *drrrrd*. Listening to some silent music is horrible - the output of the speakers is lower than the noise of the local disk.

Maybe relevant settings in Edit->Preferences:
Playback -> Network Buffer Size: 1024 kB
Music -> Watch my library for new files: off

Is there anything else one can change? It can't be that difficult to read a <10MB file into memory right from the start and not touch the disk  *drrrrd* every few seconds?!

Thanks!


P.S. I verified by turning off the speakers and start/stop playback - the noise there on playback and not if turned off. Reliably.

---

### Post by Antenne on 2010-06-02
Anyone?

---

### Post by sanderd17 on 2010-06-02
1024KB = 1MB but this is not the maximum ram contens.

You should try to find the rhythmbox settings file and see if there's a maximum memory setting in, maybe you can get it up.

---

### Post by Antenne on 2010-06-02
> **sanderd17 said:**
> 1024KB = 1MB but this is not the maximum ram contens.
But it's also the *network* buffer size. Hard disk is local.

---

