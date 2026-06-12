---
title: "Would reinstalling help restore microphone?"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Declan on 2007-04-20
Hi all,

I've been upgrading since herd 4 and had no problems. I've seen  many bug reports about the microphones, but didn't manage to understand why it is that although the microphone appears to work, it will not record any sound. I could always reinstall the final version, if that might sort out the problem, but I'm not sure if the bug is even resolved, or if reinstalling would do the trick.
I don't know what information is pertinent. I have IXP150 AC'97 Audio on this Toshiba Satellite A60-302. Actually, I imagine there's a fairly simple solution, but I don't know what it is. I have confirmed with alsamixer that microphone 1 is switched on. The sound comes through the speakers, but nothing gets recorded with arecord, sound-recorder, audacity or ardour. 
Any ideas?

Declan

---

### Post by garybrlow on 2007-04-20
You won't be able to record anything is sound capture is turned off. Inalsa mixer go to the capture tab by pressing tab. Make sure that the mic column <  Mic  > has the LR CAPTUR on, if not select the mic using arrow keys left or right until you get there and press the spacebar to turn LR CAPTUR on. Make sure that the <Capture> column has LR CAPTUR on as well, if not do the same as before. No sound can be recorded/captured to file in audacity or any other sound recording application if the volume settings of <Capture> is set to 0, so turn the capture volume up so you can do recording.

You can also look at some suggested solutions found here [http://ubuntuforums.org/showthread.php?p=2422276#post2422276](http://ubuntuforums.org/showthread.php?p=2422276#post2422276). It includes the ALSA and Linux Sound Modules reinstall which avoids a total Ubuntu/OS reinstall. If all else fails of course, what's left is to do a total system reinstall using the latest version.

Cheers!!!

GaryBrlow :biggrin:

---

### Post by Declan on 2007-04-20
I did what was suggested, I think correctly, including the remove and reinstall of the sound bits: it still doesn't work. This may be an outstanding bug...  I wonder what information is useful to include in a bug report. I don't think I reported it during the beta stages since I saw a number of similar sounding reports already there. That's one of the difficulties for the non-expert: how to understand what information is needed for useful bug reports.
Anyway, thanks for the help thus far.

Declan

---

### Post by jjalocha on 2007-04-22
Maybe [this post]("http://ubuntuforums.org/showthread.php?t=418396") helps... it has some screenshots.

---

