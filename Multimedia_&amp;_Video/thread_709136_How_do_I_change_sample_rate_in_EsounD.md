---
title: "How do I change sample rate in EsounD?"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by Chessmaster on 2008-02-27
Hi there,

I have a USB sound card that runs at 48 kHz. 

As I understand, Esound (esd) runs at 44.1 kHz by default. I suspect this is causing my playback problems (I just get a single, high pitched tone instead of music!).

How do I go about changing the EsounD sample rate to 48 kHz?  I suspect that to do this I have to change something in the esd.config file - but what?

Any suggestions that I could try would be greatly appreciated. 

Thanks in advance.

---

### Post by Chessmaster on 2008-02-27
I managed to change the default settings in esd.conf (added the line: "default_options=-r 48000" to the bottom of the file).

Unfortunately this doesn't seem to make any difference, I still have a monotonous, monotone, constant beeeeeeeeeeeeeeep.

Any ideas....anyone....all suggestions welcome and willing to be tried!

---

