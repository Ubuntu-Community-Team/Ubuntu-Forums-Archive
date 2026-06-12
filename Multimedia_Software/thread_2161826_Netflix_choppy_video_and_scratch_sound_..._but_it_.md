---
title: "Netflix choppy video and scratch sound ... but it worked yesterday."
date: 2013-07-12
forum: Multimedia Software
---

### Post by xigen on 2013-07-12
Ubuntu 12.04   w/ a very new Nvidia graphics card.

I installed Netflix via the ppa and sudo apt-get install netflix-desktop.
It worked yesterday.

Today, after updates, Netflix has choppy video and very scratchy sound.

Here is what I attempted... without improvement in Netflix. 

 441  rm -Rf ~/.wine-browser
  442  sudo apt-get update
  443  sudo apt-get remove netflix-desktop
  444  sudo apt-get update
  445  sudo apt-get install netflix-desktop
  446  netflix-desktop&
  447  netflix-desktop --showdebug
  448  netflix-desktop&
  449  sudo rm -Rf ~/.wine-browser
  450  history

Suggestions?

---

### Post by xigen on 2013-07-12
Well.. hmmm!   

If I let Netflix buffer for 5-10 minutes it works.  Very strange.

---

### Post by evilsoup on 2013-07-12
Are you testing on the same videos? It could be that netflix is serving some videos in standard definition, and others in high-definition (which means more data for the netflix player to deal with).

---

