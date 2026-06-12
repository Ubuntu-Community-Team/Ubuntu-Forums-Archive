---
title: "alc850 and coax spdif out not working anymore"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by azidrane on 2007-05-02
Greetings,
I had this working on a fresh install of Fiesty. Then I tried to play with it to get AC3 pass through working, and since then i've been unable to play anything through spdif. Originaly, on the fresh install, I had 2.1 working (or maybe it was 2 and the amp was putting the .1 in) either way, it was working. Then I got greedy and tried to get the pass through working so I could watch DVD's in in Dolby Digital (like in windows) and somewhere i messed it up. Right now I'm as close to fresh install as I think i can get w/o reinstalling. 

.asoundrc is blank
I've run  
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

then reinstalled them and that does nothing.

Any clue's any one? Its an Nforce4 board, A8N-E SLI

---

### Post by azidrane on 2007-05-03
FYI ~ Never got this fixed. Just reinstalled. Seems to work fine after that as long as I don't touch the asoundrc file.

---

