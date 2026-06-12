---
title: "DVD audio playing through wrong sound card"
date: 2009-11-14
forum: Multimedia Software
---

### Post by FOSman on 2009-11-14
I'm currently running Kubuntu Karmic.  I have two sound cards.  An SB Live and a Realtek (built into the mobo).  I use the SB Live, and have that set to index=0.

Back with Hardy, sound worked perfectly.  No troubles.  Video (avi, mkv, etc.), flash, DVDs, CDs, and so on.  Everything was great.

Then I updated to Karmic.  (Well, technically I ran Jaunty for a short while, but I effectively skipped over it.  And Intrepid wasn't available for Kubuntu.)

DVDs no longer had sound.  The player didn't matter.  So, I messed around a bit, and finally got sound working for DVDs.  (I won't tell you how, for reasons that will become obvious.)  After getting sound working for my DVDs, I found I didn't have sound for anything else.  So, I started troubleshooting all over again, and found that my sound cards had switched indexes.  My SB Live was index=1 and the Realtek was index=0.  (The only way I can think of that this may have happened was after I did a "sudo alsactl store 0", since that's the only thing I did during the first troubleshooting that would have touched alsa-base.)  I switched them back, and once again had sound for everything else, but lost sound from DVDs.

So it appears that somehow the sound from DVDs is going through index 1, and sound for everything else is going through index 0.  I have no clue how this happened or why, and even less of an idea (if that's possible) of how to fix it.

How do I get all sound to go through the SB Live, like it used to?

---

### Post by Yellow Pasque on 2009-11-15
The easiest way would be to disable the onboard sound in the BIOS, if possible.

---

### Post by FOSman on 2009-11-16
I couldn't find anything in the BIOS that would let me do that, unfortunately.  Next idea?

---

### Post by FOSman on 2009-12-12
After a lot of pain and suffering and reinstalling and beating my head against the wall, I finally managed to solve this.

From the main menu, select Settings -> System Settings.  Then click the Multimedia button.  From there, you can put your device preferences for audio in/out in whatever order you prefer.

A very simple fix, but one that completely eluded me for some reason.  If anyone else has a similar problem, I hope this saves you lots of time.

P.S.  How do I set the thread to "[Solved]" like I see happen to others?

---

