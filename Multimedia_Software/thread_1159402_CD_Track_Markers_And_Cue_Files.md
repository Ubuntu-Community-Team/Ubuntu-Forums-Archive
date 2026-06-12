---
title: "CD Track Markers And Cue Files"
date: 2009-05-14
forum: Multimedia Software
---

### Post by SocratesTNR on 2009-05-14
Where to begin...

So I've got this 46 minute Pink Floyd album, rescued from a twenty year old tape, in a 500 MB file...

First I run:

**shntool pad Meddle.wav**

and get Meddle-padded.wav with an audio data length divisible by 2352.

Then import to Audacity, with the Wotyamacallit set to 00:00+frames, snap-to, 44100Hz and 16-bit...

I drop the track markers...

Export them to lables.txt and convert to a cuefile with lable2cue...

Then I try and run:

**wodim -dao cuefile=Meddle-padded.cue -dev1,0,0**

and I get told to get lost because the data length is wrong...

**Bad audio track size 486969884**


But running:

**shntool info Meddle-padded.wav**

tells me that the audio data has been nicely and properly arranged...
[B]
Data size:                    486969840 bytes
Chunk size:                   486969876 bytes
Total size (chunk size + 8):  486969884 bytes
Actual file size:             486969884[/B]


but wodim is taking the length as data + 8, which won't work...

After 2 days... I'm stuck.

---

### Post by SocratesTNR on 2009-05-15
o poo, no-one knows...

---

