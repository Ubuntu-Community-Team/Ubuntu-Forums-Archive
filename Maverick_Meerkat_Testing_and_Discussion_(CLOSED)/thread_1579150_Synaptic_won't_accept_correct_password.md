---
title: "Synaptic won't accept correct password"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by RTrev on 2010-09-21
Got a weird situation that I can't find with a search.  I find similar situations, but never quite the same.

I installed Maverick Mini-CD and then pulled in ubuntu-desktop.

Things are working well, with the exception of Synaptic rejecting my password.  I've reinstalled Synaptic (which previously solved the problem on another Lubuntu Maverick install), reinstalled policykit-1, reinstalled all four of the aptdaemon packages, looked in the root directory and removed .synaptic, all of which were suggestions in other threads.  Nothing has worked yet.

If I choose Synaptic from the menu system, it rejects my password, but if I do a gksudo synaptic it accepts it.  I'm sure this is the wrong way to run Synaptic, judging by the convoluted command I see in the menu system.

To the best of my knowledge, I should have the latest versions of everything.. having just done upgrades from the Main U.S. server.

Any ideas?

Cheers,
Bob

ETA: 64-bit version, if that matters

---

### Post by cariboo on 2010-09-21
See [this]("http://ubuntuforums.org/showthread.php?t=1577781&highlight=gksu") thread for a solution to your problem.

---

### Post by RTrev on 2010-09-21
Bingo!  Thanks!

---

