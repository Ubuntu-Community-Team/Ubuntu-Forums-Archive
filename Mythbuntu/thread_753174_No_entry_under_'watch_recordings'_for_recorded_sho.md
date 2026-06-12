---
title: "No entry under 'watch recordings' for recorded shows"
date: 2008-04-12
forum: Mythbuntu
---

### Post by meanmrmustard on 2008-04-12
I've just done a fresh install of Mythbuntu 7.10. 
After completing the config steps I surfed a bit looking at a few live TV channels, then went to 'media library > watch tv'.  I had watched a few minutes of the Sci-Fi channel, a bit of Nickleodeon and something else. When I looked under the 'watch recordings" option, I was presented with a choice of genres... "children's", "science fiction" and another I don't remember, "drama" or something. I chose science fiction and it played what was recorded from the SCi-Fi channel. 
This is behavior I'd never seen before. However, this it has not been repeated since the first use of the new install.  Has anyone seen this besides me?

Later I set up a few programs to record.
The next day when I tried to watch the recordings there was only one of my choices in the menu.
The shows were in fact recorded - I found the mpg files in /var/lib/mythtv/recordings, but they were not in the gui (media library > watch recordings).:confused:


Another thing is that back when I was using Knoppmyth, programs that I watched on live tv ended up with entries in 'watch recordings' while under Mythbuntu this doesn't happen. Is this just Mythbuntu's default behavior, and can it be changed?

Anyone have a clue what may have gone wrong with this install?

---

### Post by volkswagner on 2008-04-12
> **meanmrmustard said:**
> I've just done a fresh install of Mythbuntu 7.10. 
After completing the config steps I surfed a bit looking at a few live TV channels, then went to 'media library > watch tv'.  I had watched a few minutes of the Sci-Fi channel, a bit of Nickleodeon and something else. When I looked under the 'watch recordings" option, I was presented with a choice of genres... "children's", "science fiction" and another I don't remember, "drama" or something. I chose science fiction and it played what was recorded from the SCi-Fi channel. 
This is behavior I'd never seen before. However, this it has not been repeated since the first use of the new install.  Has anyone seen this besides me?

Later I set up a few programs to record.
The next day when I tried to watch the recordings there was only one of my choices in the menu.
The shows were in fact recorded - I found the mpg files in /var/lib/mythtv/recordings, but they were not in the gui (media library > watch recordings).:confused:


Another thing is that back when I was using Knoppmyth, programs that I watched on live tv ended up with entries in 'watch recordings' while under Mythbuntu this doesn't happen. Is this just Mythbuntu's default behavior, and can it be changed?

Anyone have a clue what may have gone wrong with this install?

To add live tv cache to recording list, select it in playback settings in frontend setup>tv settings>playback>page 5/9.  This same setup screen has choices for default groups when displaying recordings directory.

---

