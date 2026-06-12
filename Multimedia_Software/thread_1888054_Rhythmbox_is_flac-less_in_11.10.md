---
title: "Rhythmbox is flac-less in 11.10?"
date: 2011-11-28
forum: Multimedia Software
---

### Post by Stray Wolf on 2011-11-28
Since I heard the next LTS will go back to using Rhythmbox instead of Banshee I decided to go back to Rhythmbox today.  I have a few new CD's I was going to rip flac (lossless) using Rhythmbox like I always had before.  There is a blank where flac should be in Rhythmbox>preferences>music>preferred formats.  When the blank space is selected the hierarchy example above the drop down menu shows flac so I tried it.  Nothing but an error.  Can anyone rip flac in rhythmbox on 11.10?

---

### Post by DariusKu on 2011-11-28
I have the same exact problem and would appreciate a solution.

---

### Post by MoreOrLess on 2011-11-28
You have to install the flac encoder package. (I suggest just grabbing the 'cuetools' package, which will install flac automatically).

---

### Post by mc4man on 2011-11-28
Rhythmbox's current treatment of audio cd's is currently a bit of a joke.

No flac encoding, the encoders it can do can't have their parameters changed, no musicbrainz support/cdinfo.

Now that it's the new default in 12.04 will be interesting if some of these & other accumulated bugs are fixed. (at least banshee addressed bugs in a timely fashion

bug on flac
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/879525](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/879525)

bug on musicbrainz
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/815585](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/815585)

More to follow after 12.04 A1 shows up.

---

