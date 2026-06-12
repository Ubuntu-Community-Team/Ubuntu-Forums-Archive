---
title: "need to turn up the master valume"
date: 2008-01-18
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-18
Even with the volume turned all the way up in mythtv it much lower than any of my other components. I then have to crank up the volume on the tv to compensate and then If I use one of my other components its blasting loud. How can I bring the myth box up to a more normal level?

---

### Post by volkswagner on 2008-01-18
in a terminal run

```
alsamixer
```

check your output sliders and play there.

---

### Post by tgm4883 on 2008-01-19
You can also turn up the recording volume on each card.  This would be in mythtv-setup

---

### Post by aaltieri on 2008-01-19
Just one comment.  I'm not sure if I did something weird or not, but for me to SAVE any of my volume settings after a reboot, I had to run:

sudo alsamixer


That saved them.  Running alsamixer as myself did little more than amuse the box and frustrate the living hell out of me.

Also, mplayer has its own volume setting!  That may be set low, as it could be in myth.  Depends how your audio is set up.

--anthony

---

### Post by Weidbrewer on 2008-03-03
> **tgm4883 said:**
> You can also turn up the recording volume on each card.  This would be in mythtv-setup

Which section in setup?   There was only one that I found had any sliders (one had a default of 70/100) and changing that didn't seem to effect the master volume at all.   I also have all of my alsa sliders at max.

---

### Post by Weidbrewer on 2008-03-05
Update:  The rest having this problem, here's what I did - 

[LIST=1]
[*]Open the alsa mixer by double-clicking the speaker icon.
[*]Went in to preference and added the Capture slider to my choices
[*]Adjusted this, and I was good to go.
[/LIST]

The only thing I ran in to was, if I set it too loud, the sound started to fuzz out.   Other than that, I was able to find a sweet spot.

---

