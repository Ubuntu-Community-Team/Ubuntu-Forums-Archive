---
title: "Recorded with Audacity--but playback &quot;slow&quot; or &quot;downpitched&quot;"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2006-11-30
I (finally) got Audacity to record something tonight -- a major milestone for this n00b!--but when I played it back, Terry Gross sounded slowed-down!  I tried saving the file as both an .mp3 and an .ogg -- but they both were not properly pitched.

I recorded a streaming NPR feed -- from the "Fresh Air" website...

Any ideas?

---

### Post by halfvolle melk on 2006-11-30
That's a weird quirk in Audacity. Try recording it as a stereo track and the bug should go away.

---

### Post by wilberfan on 2006-11-30
Well, I would have said that I WAS recording in stereo (I've got 2 waveforms showing...)

As an experiment, I uninstalled version 1.2.6 (from the distro) and compiled the latest beta (1.3.2) and installed it.

The recording I just made is even S-L-O-W-E-R than I one I made using 1.2.6!   I thought the problem was happening when it *wrote* the mp3 or ogg file, but I played it back right out of Audacity and it was slow there.   So it's being *recorded* too slow?

---

### Post by bmillsap on 2006-11-30
I use Audacity (on Windows actually) to speed up podcasts, and it seems to be bad at detecting when the sample rate is something other than 44.1kHz, sometimes but not always.  You might try changing the sample rate in Audacity until the length/pitch are what you expect.

---

### Post by wilberfan on 2006-11-30
> **bmillsap said:**
> I use Audacity (on Windows actually) to speed up podcasts, and it seems to be bad at detecting when the sample rate is something other than 44.1kHz, sometimes but not always.  You might try changing the sample rate in Audacity until the length/pitch are what you expect.

Yeah, you may be right...  I made another recording at a (higher?) bitratre, and it was even SLOWER.   I think 44.1 was slow, and 48 was even slower...

Is this a bug in Audacity, or something having to do with Edgy?  Or Linux in general, or...?   I REALLY prefer not to have to do my LP rips on XP (I'm trying to wean myself off of Windoze before Vista takes over...!)

---

### Post by bmillsap on 2006-11-30
Try letting it record however it wants, then afterwards seeing if you can adjust the sample rate.  FYI, I have no problems recording from an analog source on Audacity on Windows, but I haven't tried capturing a stream.

---

