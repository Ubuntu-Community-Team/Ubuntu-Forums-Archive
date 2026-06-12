---
title: "Ubuntu Studio and Roland Juno-G"
date: 2008-04-03
forum: Multimedia Production
---

### Post by AdrianStrays on 2008-04-03
Hopefully there are some musicians out there in Ubuntu Land.  I've got a Juno-G that I use primarily as a workstation and I was curious to know if it would work, and work well with Ubuntu.  Does anyone have an experience with the Juno-G and Ubuntu?

---

### Post by AdrianStrays on 2008-04-04
Bump

---

### Post by Stochastic on 2008-04-04
Well if it's a USB connection, chances are that the ALSA driver will be the MIDI link you want to look into.  Roland offers very few details on their website (typical) as to the specs of the computer transfers.
The  Roland website does however suggest that the USB connection does both MIDI and file transfers.  This makes me wonder if it's some proprietary chip inside the synth that redirects USB traffic to the appropriate area.  If you're only looking to do file transfers Ubuntu will probably be able to recognize the storage device and work with it.

If I were you, the first thing I would do is phone Roland (it's not actually going to help very much, but in the long run....) and say "Hi, I've been looking into buying a Roland Juno G for a while now as I'm very impressed by its features, but I'm worried that it won't work on the Linux computers at the studio.  Have you heard of anyone having success with the Juno G on Linux?"
They'll respond with no, because anyone who's had success with it on Linux didn't phone Roland to tell them - but it'll put the seed in their head that maybe they should support linux as a growing number of audio professionals are working with it.

The second step I'd try is to boot up the Live CD of Ubuntu, plug in your Juno G, open a terminal and run: lsusb
Then post the results to this thread.  That is of course if it doesn't "just work" upon initial plug.

Edit:  Upon checking the [ALSA driver support list for Roland](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Roland_Edirol) I noticed that there are a few USB synths listed here (VSYNTH for example) so there's good likelyhood that a similar technology is in the Juno G.  No guarantees though.

---

