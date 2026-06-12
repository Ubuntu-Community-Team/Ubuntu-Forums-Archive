---
title: "No alsaconf!!! help!!!"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by tvs on 2007-06-28
I've just started using Ubuntu and I've noticed that alsaconf does not exist!!!

I have a Dell Inspiron 1505 notebook that has attached a Creative Labs Live 24 USB external card; how should I select that card instead of the internal card? (it's simple to do it with alsaconf, but it's not there).

Regards,

---

### Post by joe.turion64x2 on 2007-06-28
> **tvs said:**
> I've just started using Ubuntu and I've noticed that alsaconf does not exist!!!

I have a Dell Inspiron 1505 notebook that has attached a Creative Labs Live 24 USB external card; how should I select that card instead of the internal card? (it's simple to do it with alsaconf, but it's not there).

Regards,
Open Synaptic (System -> Administration) and search alsa there. Perhaps there are missing packages there.

---

### Post by tvs on 2007-06-28
> **joe.turion64x2 said:**
> Open Synaptic (System -> Administration) and search alsa there. Perhaps there are missing packages there.

No, I'm 99.99% sure that ubuntu doesn't have 'alsaconf'; you can verify that with:
** apt-file update; apt-file search alsaconf**



PD: I'm coming from debian sid (I was a little disappointed with the continous problems with 'non-free' modules ... but it looks ubuntu has its own problems also :( )

---

