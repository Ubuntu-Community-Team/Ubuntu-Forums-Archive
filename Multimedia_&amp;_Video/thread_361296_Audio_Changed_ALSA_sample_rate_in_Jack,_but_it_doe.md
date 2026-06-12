---
title: "Audio: Changed ALSA sample rate in Jack, but it doesn't &quot;take&quot;"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by mjpatey on 2007-02-14
Hello, all-

I've been toying with Ardour, DAW software that uses Jack as its audio server.  I've tried invoking Jack through the command line and through Jack Control, and the results are the same:  I try to switch the ALSA sample rate from 48000 to 44100, it says I've done it, but the change doesn't really take place.

In the case of Jack Control, the GUI continues to display the old rate (48000) even after I tell it to switch, and regardless of which method I use, Ardour's sample rate stays at 48000.

Any idea how to make it switch to 44100 for real?  Should I maybe try using something other than ALSA?

Thanks for any help you my have!

-Mark

---

### Post by eric71 on 2007-02-27
Quite a few built-in or budget sound cards can only do 48000. They can't resample. For instance, that's all my laptop can do.  It might be that your sound card in not capable and the software is reflecting this.

---

### Post by mjpatey on 2007-02-27
The one on this machine can handle 44.1, from what I can tell.  Files recorded on my "real" audio production computer (with pro hardware) at 16 bit, 44.1 KHz play back fine in other apps.  In fact, when I switch Jack to OSS, it seems to handle 44.1 just fine.  Jack Control actually displays the sample rate as 44.1, rather than ignoring it and continuing to display (and play back) at 48.

Is there some downside to using Ardour with Jack set to use OSS rather than ALSA?  If not, I'll just keep it set to that.

---

