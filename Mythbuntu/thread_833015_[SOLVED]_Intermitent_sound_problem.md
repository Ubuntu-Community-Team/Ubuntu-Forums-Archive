---
title: "[SOLVED] Intermitent sound problem"
date: 2008-06-18
forum: Mythbuntu
---

### Post by xfred on 2008-06-18
I've been using mythbuntu for a while now and there is one problem that I've so far been unable to fix.  When I turn on the box it randomly fails to detect the soundcard.  To be specific, I'm running an asus p5kpl motherboard with a built-in Realtek ALC662 soundcard.  When a bootup works and sound is present "cat /proc/asound/modules" produces:

```
 0 snd_hda_intel
 1 cx88_alsa
 2 cx88_alsa
```

where I assume snd_hda_intel is the soundcard and cx88_alsa is most likely just my two dtv200h tuner cards.  When it's not working I get:

```
 0 cx88_alsa
 1 cx88_alsa
```

and no sound :(.  Following instructions in a thread I seem to have lost I did add the following line to /etc/modprobe.d/alsa-base

```
options snd_hda_intel index=0
```

which improved things (before that the list order was also random and sound would fail if snd_hda_intel didn't happen to get randomly put at the top), but I still have the problem of the soundcard not being detected at all for some startups.  It doesn't follow any pattern I can see - sometimes I'll go for weeks without seeing the problem, other times I need to restart the system multiple times before I get sound.

Any suggestions?  I've put off posting this because I thought it might be something easy that I could figure out for myself, but I'm afraid it's got me beat.

---

### Post by xfred on 2008-06-20
Note: just to clear things up - I'm not expecting anyone to use some latent psychic abilities to diagnose the exact fault at a distance ;).  Realistically what I'm looking for are thoughts and suggestions about how I should go about diagnosing and fixing the problem.  Like, say, what sort of messages might appear in a logfile connected to a problem like this (what phrases should I be searching for)?  Or has anyone had similar experiences (and how did you approach them)?

---

### Post by xfred on 2008-06-29
*bump* Anyone at all?

---

### Post by xfred on 2008-09-09
OK, apparently not.  Anyhow, I found a solution: for various reasons The box contained two identical TV tuner cards.  For various reasons I removed one and bingo, the problem vanished.  I do plan on putting back a second TV card at some point, but I'll make sure it's not identical to the first (also makes it much easier to tell what's what during setup if your tuner cards are distinguishable).

PS: am I perhaps phrasing my questions badly?  Is that why I get no responses?

---

