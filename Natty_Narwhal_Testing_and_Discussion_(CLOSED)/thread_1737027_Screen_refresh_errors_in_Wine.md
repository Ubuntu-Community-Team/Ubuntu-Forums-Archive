---
title: "Screen refresh errors in Wine?"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by scradock on 2011-04-22
I have been using Wine in previous Ubuntu releases with only minor problems, but using Natty I can't get rid of an annoying glitch. I have several different Natty installs (partly to check this out) - so this happens using Unity, Unity2d, Classic and Xubuntu. Same machine, same video card/drivers (OS -ati/radeon) works fine in maverick/10.10.

Using Spider solitaire as an example, when the cards deal the screen seems slow to refresh, and there is often a black area left after cards have swept across the screen. Once I start to play, the card that moves is fine, but other cards seem to get "lost", and only re-appear when I click on where they ought to be - it seems that the screen area gets re-loaded from an old buffer, as the card underneath shows up, but is not playable. This happens to only some columns of cards, randomly as far as I can see.

Sometimes I can play the game out, though slowly (not being able to see the cards slows me down!); if so, the whole screen refreshes at the end and the green background appears intact - the black areas go away. Other times, Wine crashes ("Wine has encountered a serious problem") and the game is unplayable.

Anyone else have the same experience? I've looked for threads here, and checked launchpad, but no luck so far.

BTW - yes, I have tried wine 1.2, wine1.3 from the repo, AND 1.3 from the ppa. All do the same stuff. It looks like an incompatibility between my video drivers and wine, but I don't see errors if I start wine from a terminal, etc. Baffled.....

---

