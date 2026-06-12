---
title: "jack rack ardour plugin?"
date: 2007-12-19
forum: Multimedia Production
---

### Post by sameoldude on 2007-12-19
hey, says here i can use the ladspa plugins on ardour to run jack rack, but there's no such thing as a jack rack plugin.
plz xzib.... wait, no, please ubuntu forum users, pimp my computer so it works as an effects station!

p.s: i wanna be able to record what i'm doing

much thanks!

---

### Post by Stochastic on 2007-12-19
Jack rack is merely a host for ladspa plugins, ardour runs its own host system that is very flexible.  What exactly are you trying to do?  If you'd like realtime effects through your soundcard as if it were a guitar pedal, use just jack rack (no ardour needed).  If you're trying to get a sound recorded that has signal processing on it, either record it plain into ardour then add ladspa plugins to that channel's mixer strip (this method gives you tweaking control) or send the input from jack to jack rack then the output of jack rack into the ardour input and record away.  Or are you wanting something entirely different?

---

