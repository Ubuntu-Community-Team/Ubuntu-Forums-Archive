---
title: "Audio JACK output stop working."
date: 2010-06-12
forum: Mythbuntu
---

### Post by agkbill on 2010-06-12
I had a mythtv configured with JACK output 5.1 that was working very well.
Got all 6 signals into JACK and I could route them as I like to my 4.0 loudspeaker setup.

But now, maybe after update (running nightly auto builds) it have stoped working.

I get :

--------------------------------------------------------------------------
2010-06-11 22:32:50.464 AudioPlayer: Disabling Audio, params(0,2,44100)
SSE2 detected
2010-06-11 22:32:50.492 AudioOutput Error: AOJack, ERROR: No ports available to connect to
2010-06-11 22:32:50.493 AO: Resampling from 44 kHz to 48 kHz with quality medium
2010-06-11 22:32:50.493 AO: Opening audio device 'output' ch 2(2) sr 48000 sf 32 bit floating point reenc 0
SSE2 detected
2010-06-11 22:32:50.523 AudioOutput Error: AOJack, ERROR: No ports available to connect to
2010-06-11 22:32:50.523 AO: Aborting reconfigure
2010-06-11 22:32:50.523 AudioPlayer: Disabling Audio, reason is: AOJack, ERROR: No ports available to connect to
2010-06-11 22:32:50.524 playCtx, Error: AOJack, ERROR: No ports available to connect to
--------------------------------------------------------------------------

When I start the player in mythth no readable client get up in JACK.


Any ideas what that gone wrong and where I could start trying to fix this?

Best regards,
/Christer

---

