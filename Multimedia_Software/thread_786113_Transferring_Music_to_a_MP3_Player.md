---
title: "Transferring Music to a MP3 Player"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Pursuer on 2008-05-07
I have Ubuntu CE.
I had installed Rythmbox music player on my computer, but found that I cannot delete my MP3 player tracks or add anything from my computer to my MP3 Player using this.

What program could I use that would do this? Is there a program that I could use to do both transferring and playing of MP3's and other media functions? Much thanks in advance!

---

### Post by darth_indy on 2008-05-07
You need to post what type of mp3 player you have; some will work with Ubuntu and some won't. It won't be very easy for anyone to help you without that info :-)

---

### Post by Pursuer on 2008-05-08
DUH! Sorry about that. I have a RCA Lyra.

---

### Post by orkerone on 2008-05-08
Have you enabled the MTP Support in Rhythmbox Plugins ?

---

### Post by ErroneousBosch on 2008-05-09
I had this same issue with a Sansa m240 and literally solved it about 14 hours ago.

Reason: Ubuntu came with LibMTP which lets it see MTP devices, but not talk to them

Solution: Go into Synaptic and search for mtp-tools. Install this package. This contains all the tools needed to actually manipulate MTP devices. Restart RhythmBox if you are still in it and it should work.

---

