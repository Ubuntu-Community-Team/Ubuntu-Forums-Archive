---
title: "Gutsy WINE audio"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by DouglasAWh on 2007-11-07
I found [http://www.linuxjournal.com/article/8802](http://www.linuxjournal.com/article/8802), but I'm a little hesitant to use it, as it is from March 2006.  Does anyone know how I should get audio working in WINE on Gutsy?

The reason I want to do this is that PandoraFM does not work in Linux.  However, it appears to work under WINE.  However, a working PandoraFM is useless to me if there is no audio...

EDIT: so, I installed Ubuntu Studio and problem gone.  I feel like a threw a nuclear bomb at a mosquito, but with no help, I felt I had to.  Of course, installing Ubuntu Studio broke my wireless, so now off to fix that...

---

### Post by cogadh on 2007-11-07
Generally speaking, all you need to do to get sound working in Wine is run winecfg in the terminal, go to the Audio tab and select the appropriate sound driver. Currently the ALSA driver is the most actively developed one, but the old OSS driver does work better in some situations.

EDIT - Also, I can't seem to find PandoraFM in Wine's Application Database. That could indicate that it doesn't actually work at all in Wine, but it could also be an indication that no one has bothered to try it in Wine. I am not that familiar with PandoraFM, other than I know it is some kind of melding of Pandora and Last.FM. What exactly does it do and how does it do it?

---

