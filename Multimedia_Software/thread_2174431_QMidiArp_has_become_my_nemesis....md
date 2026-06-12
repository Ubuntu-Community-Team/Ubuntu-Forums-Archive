---
title: "QMidiArp has become my nemesis..."
date: 2013-09-14
forum: Multimedia Software
---

### Post by geist171 on 2013-09-14
So I want to mess around with the music software and at this point the one thing I simply cannot manage to get to work properly is QMidiArp.  I don't have a physical midi input device (keyboard or midi controller) so I haven't messed with those yet, but I've tried four different virtual midi keyboards, three different synths, and a couple of the connection controls (QJackCtrl and Patchage to be precise) and I still can't manage to get sound if Qmidiarp is connected to anything in any way.  I've read through the solved threads, tried those things, and still not managed to get results.

As yet, the most successful configuration has been jack-keyboard->qmidiarp in the midi channel of qjackctrl, that will get an active event log in qmidiarp.  I've tried loading the demos to audio test and nothing.  I can get drumstick's keyboard to connect directly to amsynth with success, ZynAddSubFX works fairly well on it's own, I haven't managed to get VMPK or Jack-Keyboard to connect to anything that actually produces sound, and if QMidiArp is connected anywhere, nothing produces sound at all.  

Searching the internet has not yielded a working result, so I'm hoping there's something simple that I'm not doing.  I also can't seem to get qmidiarp to exist in the alsa channel of qjackctrl as one of the solutions recommends, so not sure what to do about that either.  

I've been at this for a couple of days now, so any help would be appreciated.

---

