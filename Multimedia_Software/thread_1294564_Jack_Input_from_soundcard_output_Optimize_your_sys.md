---
title: "Jack Input from soundcard output Optimize your system for ultimate performance."
date: 2009-10-18
forum: Multimedia Software
---

### Post by simeon.mattes on 2009-10-18
Hi,

I'm quite new on JACK software, so please forgive my ignorance.

I was wondering if it is possible to have as input in JACK, the output of the soundcard. This would be useful If you use an application that doesn't support JACK.

Actually what I want to do is the following

I want to stream audio to an icecast2 server through campcaster. I have found that there is a way to do it through JACK and darkice but I was wondering if there is an easier way, since you have to crack the code of darkice in order to do it.

I have managed through darksnow and Qt GUI intreface of JACK to connect to the icecast2 server, but I can't connect campcaster with it. Campcaster has as an output my sound card which is hw:0,0.  In JACK options, using alsa as a driver, I can use Input device hw:0,0. This means that everything I send to hw:0,0 can recorded from JACK and send them to my icecast server?

Thanks in advance

---

