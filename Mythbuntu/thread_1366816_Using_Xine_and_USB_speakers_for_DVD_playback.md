---
title: "Using Xine and USB speakers for DVD playback"
date: 2009-12-28
forum: Mythbuntu
---

### Post by Calash on 2009-12-28
Been searching all afternoon bug cannot find any relevent information that is not more than 3 years old and seems too out of date for my setup.

I have my current Mythbuntu setup sending sound output to a set of USB powered speakers.  In the config I had to tell it to use /dev/dsp1 for this setup to work.


This works great for all internal applications.  However many of the DVDs that I got for Xmas do not play well on the internal player.  So I am trying to switch the DVD playback over to Xine.

Video is working fine but it ether wants to send the playback over the TV speaker or send nothing at all.

Can anybody help me out with getting Xine to work with the setup that MythTV is already using?

---

### Post by Calash on 2009-12-29
Came up with a solution, not the best mind you but it is working.


Disabled the on-board sound card so that only the USB speakers were left for the sound.  This caused Xine to use them by default.


Would still like to find a better solution but for now this works.

---

