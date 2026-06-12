---
title: "Word clocking nightmare with Jack."
date: 2011-01-21
forum: Multimedia Software
---

### Post by pepsifx357 on 2011-01-21
Hey guys, I've run into a new problem with my studio setup.  I have a RME MADI interface and an Alpha MADI converter.  I've been using the RME interface as a master clock to control the clock of the Alpha's converters.  I've changed the configuration to the opposite.  Now the Alpha Controls the RME card over a word clock cable.  Now that I have done this, Jack will not start at sample rates higher than 48Khz.  It must have something to do with the alsamixers options for the RME HDSP MADI, because under Windows, there were more options for double sample rates and stuff like that.  I could be wrong.  Like I said, these sample rates worked before I changed the word clock configuration.  It still works if I change the RME from slave to master clock.

I really need help with this.  I need to know the limitations of Linux and Jack under these conditions, if there are any.  The reason I changed the configuration, is because it was starting to get old having to go to the alsamixer and scroll over 64 channels to get to the sample rate and change it.  The Alpha has a sample rate button right on the face and would make it easier to switch sample rates.

Thanks

---

### Post by pepsifx357 on 2011-01-22
Bump

---

