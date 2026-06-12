---
title: "Alsa programs cut in and out on pulseaudio"
date: 2010-02-14
forum: Multimedia Software
---

### Post by wd5gnr on 2010-02-14
I generally like pulseaudio and most alsa programs work through it ok. But I have attempted to upgrade to the latest via PPA and still have the same persistent problem.

For whatever reason some ALSA programs seem to create and destroy the pulseaudio stream anytime sound "starts". In other words, when quiet, the stream goes away and then is recreated (watching the pa volume control). This makes the audio choppy. If there is enough noise the stream will stay open and its not choppy.

I've played with the usual settings in the server configuration. It would be great if you could provide some sort of timeout for a stream.

Any thoughts?

Yes I have read the million post thread and yes I've googled around. About the only thing I see is a patch for pulse from Fedora that sounds promising but I really don't want to rebuild everything unless I have to.

Any thoughts?

---

### Post by TenPlus1 on 2010-02-14
Disable PulseAudio, see if your sound will work perfectly using Alsa on it's own...

---

### Post by wd5gnr on 2010-02-14
Yes that has worked fine. The problem is clearly something to do with the alsa plugin for pa. Some ALSA call is causing the pulseaudio stream to close and reopen. There are several patches out with names that suggest they fix this, but I don't know that for sure.

---

