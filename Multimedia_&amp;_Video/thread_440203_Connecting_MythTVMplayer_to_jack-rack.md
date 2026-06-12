---
title: "Connecting MythTV/Mplayer to jack-rack?"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by DDM on 2007-05-11
I've had a MythTV setup for a while now, and I'm trying to get MythTV and Mplayer to connect to Jack-Rack in order to use a compressor so that I can level out the volume output to my TV, which is pretty low due to long 25' cables. I can't simply increase the volume of the TV, since the cables seem to generate lots of noise.

I can connect mplayer to JACK with mplayer -ao jack fine, but according to Patchage it automatically gets routed to alsa_pcm playback. MythTV, even though I compiled it with JACK enabled and replaced /dev/dsp with JACK: in the MythTV settings, never connects to the JACK daemon. 

Has anyone had success doing something similar? And is there a way I can load jackd on bootup as well as route all programs through jack-rack automatically and have jack-rack load my effect preset so I don't have to manually set everything by hand upon every reboot?

---

