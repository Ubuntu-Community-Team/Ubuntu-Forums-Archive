---
title: "Getting a high pitch with too much PCM"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by Jojan on 2008-02-22
Been playing around a bit with Audacity a bit and now when I get my PCM up to high a high piteched nosie comes out of my speakers. When using Audacious the pitch come at 65% of the volume.

Does anyone know what might have happend? Seen other threads with problem, but no one with [SOLVED].

---

### Post by Sam Lars on 2008-02-22
I don't think I've ever **not** experienced this.  I believe that's the way it works, if you turn up the gain too much, it peaks out.

---

### Post by hardyn on 2008-02-22
turn off the mic... your getting feedback.

---

### Post by Jojan on 2008-02-23
I have my mic off, but if it's like Sam Lars said, then it's OK.

---

### Post by MrClearPore on 2008-02-25
> Been playing around a bit with Audacity a bit and now when I get my PCM up to high a high piteched nosie comes out of my speakers

I was having the same problems with my **SoundBlaster 5.1 Live!** card after upgrading the ALSA drivers.  After playing around with the various mixer controls, I discovered that by muting the **AC97** control in **alsamixer**, I was able to remove the noise from my speakers whenever I upped the volume in PCM.

Mind you, this was for my SB Live! card.  I don't know what controls you have.  Plus, I'm using the Kubuntu distribution.  I suggest (if you haven't already done so) that you mute certain controls that you don't need (in my case, AC97 - but not the AC97 capture called **AC97 Cap** :) )  I don't even know what the AC97 control does anyway.  It doesn't seem to affect anything I do regarding sound on my system, so I leave it muted.  It's the only way I can get rid of the pitch noise.

Good luck!

---

