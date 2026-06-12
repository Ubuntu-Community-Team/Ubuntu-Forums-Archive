---
title: "Posting of default Sound-Juicer settings needed"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by dmneoblade on 2007-02-05
Hey... was updating my system over the last couple days... and somewhere along the line, I seem to have lost the default profiles for encoding music in Sound-Juicer. Could someone post thiers for me?

---

### Post by dmneoblade on 2007-02-06
Well, seeing as nobody was willing to answer my inquiry, I had to check it out myself. Booted the live CD and got this information:


CD Quality, Lossless
Used for converting to CD-quality audio, but with a lossless compression codec. Use this if you later want to edit the file or burn it to CD.
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc
flac


CD Quality, Lossy
Used for converting to CD-quality audio, but with a lossy compression codec. Use this for CD extraction and radio recordings.
 audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux
ogg


Voice, Lossless
Used for converting to lossless voice-quality audio. Use this for recording and editing speech.
audio/x-raw-int,rate=22050,channels=1 ! wavenc name=enc
wav

Voice, Lossy
Used for converting to lossy voice-quality audio. Use this for recording speech that doesn't need to be edited.
speexenc name=enc ! oggmux
ogg

---

### Post by ricardisimo on 2007-07-13
Weird, because the oggenc help page states that "3" is the default quality level, not "0.5".

---

