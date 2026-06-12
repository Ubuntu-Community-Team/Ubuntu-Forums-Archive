---
title: "Jack as an official Ubuntu package?"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2006-07-28
I'm pretty sure that my laptop's sound in general stopped working after I installed Ubuntu Studio's recommended packages.  I also had to stop esd in order to be able to start jackd.  I suspect Ubuntu would make these issues would go away if they treated Jack as a supported part of its audio infrastructure, possibly even making it part of the default install.

Does anyone know the technical reasons that Jack isn't part of the audio infrastructure installed by default with Ubuntu?

If Jack was installed by default, would it monopolize the ALSA interfaces in a way that forced a lot of sound-producing applications to be rewritten for Jack output?  

Or is there a compatability layer available like what ALSA offers for OSS programs?

Thanks,
Christian

---

### Post by Cybolic on 2006-07-28
I guess it's because Jack can be quite tricky to setup and also that it wasn't designed for desktop use. That Gnome is fond of ESD, and Ubuntu is fond of Gnome might also have something to do with it... maybe it's possible to run ESD on top of Jack... (see below)

Yes, Jack monopolizes the ALSA interfaces.

There is an OSS layer available for Jack, I've only ever tried it with XMMS though:
[http://gige.xdv.org/libjackasyn/](http://gige.xdv.org/libjackasyn/)

---

