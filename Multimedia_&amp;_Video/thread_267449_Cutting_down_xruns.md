---
title: "Cutting down xruns"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by paul cooke on 2006-09-28
shutting Azureus (Java based bittorrent client) down cured mine... I only get them now as transients when switching in a different instrument in ZynaddsubFX or when starting another program up. 

With Azureus running, the audio was crackly... with it closed down completely the audio is nice. 

Remember, some programs like azureus can still be running even if there isn't a window present.

---

### Post by dolson on 2006-09-28
Just as an FYI, ZynAddSubFX is horribly bad at being realtime-friendly in the user interface. I plan on not using the GUI mode when I do my actual recording to help avoid this.

Also, when apps connect to JACK as they start up, this always seems to cause Xruns. Not sure why, but it's a known issue, and it won't be solved by any config changes that I know of.

Also, the only time Xruns matter is during record operations, really. Obviously you can't work in condions where they occur all the time during playback either, but a few here or there won't do any damage.

---

### Post by zettberlin on 2006-09-29
> **dolson said:**
> Just as an FYI, ZynAddSubFX is horribly bad at being realtime-friendly in the user interface. 

This appeares to be improved somewhat in edgy. Zynadd now connects to jackd automagical and does not yield an xrun at startup on my laptop. Loading instruments still produce one...

---

