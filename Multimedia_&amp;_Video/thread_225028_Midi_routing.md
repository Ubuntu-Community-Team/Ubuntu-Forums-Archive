---
title: "Midi routing"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by aaazhyd on 2006-07-28
Ok,

What would be the best method to do the following, as it seems LinuxSampler doesn't take JACK for input .. I want to route the midi out of something, say Rosegarden, then use that for the input into LinuxSampler. 

What's the best method to do the above? Some sort of midi routing application I would assume?

---

### Post by metasymbol on 2006-07-30
No app using JACK for midi I/O - because JACK Midi isn't ready yet. 

In this time we're using ALSA midi. If you're opening Rosegarden and Qsampler, a Linuxsampler ALSA midi instance will automaticly detected by Rosegarden. Very simple ;)

---

### Post by dolson on 2006-07-30
Just FYI, JACK Control had a MIDI connections window, but this is indeed connecting things via ALSA in the background.

---

