---
title: "tv sync to sourcs rate?"
date: 2009-08-12
forum: Mythbuntu
---

### Post by tonycollinet on 2009-08-12
At the moment, a question on how it works.

AIUI, to get smooth video it is necessary to have the display frame rate match the source frame rate. Otherwise frames must be inserted, or dropped, causing glitches in the video stream.

For recorded tv this should not be too much of a problem - simply read frames off the disk and send them to the tv at the output frequency of the graphics card (assuming the gc frequency is close to the recorded video frequency.

For live tv it is more difficult - either the display frame rate must be synchronised to the broadcast frame rate, or there needs to be a hard disk buffer used, big enough to allow frame rate conversion for the duration of the program. Alternatively there must be a frame drop/insert strategy to match the frame rates, causing glitches again.

Does anyone know how this actually works? Are there any settings for optimistation?

Thanks.

---

