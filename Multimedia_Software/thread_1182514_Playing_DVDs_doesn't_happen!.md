---
title: "Playing DVDs doesn't happen!"
date: 2009-06-09
forum: Multimedia Software
---

### Post by Stochastic on 2009-06-09
So I've enabled the medibuntu repository, installed all the apps in the multimedia sticky guide, but still have yet to see a single DVD play on my computer.  What could be left for me to overlook?  (oh and I'm on 9.04)

---

### Post by lisati on 2009-06-09
Have you looked [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") yet?

---

### Post by Stochastic on 2009-06-09
hmm, maybe that bit at the bottom of that page could have something to do with my problem (the bit about region codes).  I'm in Canada and have always been here (bought the laptop here too) but when I run regionset this is the output (rather confusing what those HEX masks refer to) ```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:1
New mask: 0xFFFFFFFE, correct? [y/n]:y
Region code set successfully!

```

---

### Post by babarosa on 2009-06-09
Hi Stochastic!

Which player do you use?
For testing reasons, use christopher korn's ppa and install vlc 0.9.9 - to my mind it is one of the best players available.
Try if it works now.

If you are using mplayer, in preferences\misc change dvd device from dev\dvd to dev\scd0 (rvm's repo at launchpad delivers more recent versions of mplayer, mencoder, ...)

Regards, Michael

---

