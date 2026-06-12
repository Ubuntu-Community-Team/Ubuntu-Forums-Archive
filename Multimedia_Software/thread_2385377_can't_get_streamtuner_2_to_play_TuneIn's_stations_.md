---
title: "can't get streamtuner 2 to play TuneIn's stations (files)"
date: 2018-02-19
forum: Multimedia Software
---

### Post by norm-thom-g on 2018-02-19
I have come back to Ubuntu after a couple of years away and discovered again just how frustrating using it can be.
I really need help with getting the files from TuneIn radio to play on Audacious via Streamtuner2.
They play fine on Clementine but this is not a suitable alternative (as they create labels on Clementine that need to be erased at some point).
I would appreciate any help offered

---

### Post by mc4man on 2018-02-20
Works ok here in 16.04 (in 18.04 repo version is broken on tunein, upstream package works fine
Whenever a station is played a .m3u is created in /tmp/streamtuner2. Try playing one of those .m3u directly in audacious
(- make sure the .m3u has something in it other than just #EXTM3U

If playing the .m3u doesn't work then open the .m3u in text editor, copy the url & try that in audacious > File > Add url

---

