---
title: "[SOLVED] Audacious plugins in 7.10"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Ardghal on 2007-10-21
I've noticed that the version of Audacious included in the Gutsy repositories, 1.3.2-4, doesn't include all the plugins other versions had. I don't know it that's an issue, but when I upgraded Ubuntu, I no longer had those plugins (NSF, SPC, GYM, PSF, AdLib, etc). So I went back to the old version I had.

On the other hand, my version of Audacious, 1.3.2-1, has some issue that, if I try to play an mp3, it crashes. If I could have the newer version of Audacious with all the old version plugins, I could get rid of XMMS! :) Also, the Upgrade Manager keeps annoying me saying there's an upgrade to the media player.


So, is there a way to upgrade to the new version, which plays mp3 without problem, and still keep the plugins for the other formats from the old version? :confused:

And in case the answer is no, is there a way to tell the Upgrade Manager to stop insisting that I upgrade my player?

---

### Post by Ardghal on 2007-10-26
Bump.

---

### Post by ekricyote on 2008-03-05
Only few months late, but people will likely appreciate the response.

The plugins you mentioned have been moved to another package, namely "audacious-plugins-extra".

You can install them via Synapctic (System -> Administration -> Synaptic Package Manager, then search for the above), or use the terminal

sudo apt-get install audacious-plugins-extra

It seems to have a problem with the SPC and NSF song file length. It always cuts out too early. Any suggestions?

---

### Post by ekricyote on 2008-03-05
> 
So, is there a way to upgrade to the new version, which plays mp3 without problem, and still keep the plugins for the other formats from the old version?

Only few months late, but people will likely appreciate the response.

The plugins you mentioned have been moved to another package, namely "audacious-plugins-extra".

You can install them via Synapctic (System -> Administration -> Synaptic Package Manager, then search for the above), or use the terminal
```

sudo apt-get install audacious-plugins-extra
```

It seems to have a problem with the SPC and NSF song file length. It always cuts out too early. Any suggestions?

---

