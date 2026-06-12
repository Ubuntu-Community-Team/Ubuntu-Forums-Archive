---
title: "Kdenlive: fixed video display now sound won't play"
date: 2007-10-25
forum: Multimedia Production
---

### Post by squirage on 2007-10-25
Hi All,

  I have been unable to find a solution to this. I installed kdenlive and had the video problem associated with not updating the graphics chip stuff, from i810 to i915 or something to that effect.

  The problem had been that when i played a clip the preview would go black. I could hear the audio, but I could only see the video when it was paused or stopped.

  So I got that fixed, great I can see the video but now no sound. I can strip the audio and hear the stripped audio in a player, but it will not be audible in kdenlive.

Any thoughts?

Thanks.

Sean

---

### Post by squirage on 2007-10-26
Bumping my own thread again.

I am wondering about the effect that Gutsy will have on Kdenlive.

The impetus for me to try ubuntu in the first place was frustration with video editing in windows and I haven't been able to get a workable fix.:(

---

### Post by BLTicklemonster on 2007-10-27
I'm new to kdenlive, and have had fits trying to find any help with it.

I did find this, perhaps it will help:

[http://en.wikibooks.org/wiki/Kdenlive](http://en.wikibooks.org/wiki/Kdenlive)

Good luck getting your problem resolved.

---

### Post by squirage on 2007-11-07
Hi,

  Well here I am a week later and still no love from kdenlive. The un-install then re-install just broke dependencies and left me unable to update at all.
```
sudo apt-get install -f
``` wouldn't work because it wouldn't overwrite the mlt libraries and the same thing happened after running the "broken" filter, which identified kdenlive as the problem. Re-installing or removing kdenlive with synaptic gave the same error due to the mlt stuff. So I went back to the terminal and tried this```
sudo apt-get --purge remove mlt mlt++ kdenllive
```
and after a reboot, low and behold, I could update normally. Of course I still haven't gotten back to re-installing kdenlive.#-o

I'll post back.

---

