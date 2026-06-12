---
title: "hvr-1600 configuration"
date: 2013-04-26
forum: Mythbuntu
---

### Post by zapstrap on 2013-04-26
I'm looking for a more efficient way of handling tuning channels on the digital/QAM portion of the card. My cable provider has a habit of periodically moving around all of the channels. When this happens, it's a matter of rescanning and manually entering the schedule codes from schedules direct. It's a tedious process, and I wouldn't do it if involved any more than the five channels they usually leave unencrypted.

The issue is, when I run a scan with the backend setup, I get all of the encrypted channels, dozens of music-only channels, and the precious few channels I really want. Since everything's moved, there's no way of knowing what channel is what, so I'm forced to exit the backend setup, start the frontend, and try to tune each channel, making notes of which number corresponds to which station. Trying to tune an encrypted channel fails after around 30 seconds, and bounces me back into the top level menu on the frontend. Searching for 5 channels among 70 or 80 takes hours.

Is there a way to get the backend to ignore all encrypted and music only channels? 

If not, is there a way to manually attempt to tune the channels from a CLI just to see if they work? That way I could just delete them. I'd love to write script to automatically parse through the channels and just zap anything encrypted or just music.

I should add: Setting the scanner to TV (not TV+Radio, or ALL), selecting "Unencrypted only" and "Test for Decryptability" does not work. I still get myth asking if I want to add encrypted and music channels.

---

