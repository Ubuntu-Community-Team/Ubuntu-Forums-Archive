---
title: "No sound in RealPlayer - Solution"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by dominikroblek on 2006-08-17
I didn't have any sound with RealPlayer 10 on Ubuntu 6.06 Dapper. After declaring the following environment variable, the sound was there:

export AUDIO=/dev/audio

I suggest to declare it as a global environment variable by putting the following line in /etc/environment file:

AUDIO=/dev/audio

/dev/audio worked fine with me, but maybe you should try other audio devices, if this one doesn't work, for example /dev/dsp2.

Dominik

PS. What exactly is the difference between /dev/audio, /dev/audio1, /dev/dsp and /dev/dsp1? I have only one sound card installed.

---

