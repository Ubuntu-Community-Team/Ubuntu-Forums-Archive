---
title: "Post-shutdown script terminated with exit status=256"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by ÜbR on 2008-01-19
Hello,

Jack gives me error "Post-shutdown script terminated with exit status=256
" when using hw:0.0. With Hw:0.2 everything works fine.

I think Hw:0.0 is reserved to system sound, so how I change default channel to hw:0.2? Or how to set system sounds fully disabled to get main channels available.

I've already removed asound.conf and esd.conf files, but sounds are still working. Is something changed with Ubuntu? I though those file were important to sounds. If I remember correctly, with my old computer main channel was changed with asound.conf or esd.conf file.

My sound card is **Hoontech ST audio DSP24 value**. (It uses envy24)

Please help me. Sound quality from channel hw:0.2 is from ***, so I need to get hw:0.0 work. Hydrogen is waiting for me.. :)

---

### Post by ÜbR on 2008-01-21
When I start Jack from terminal by typing "jackd -d alsa -d hw:0" I can use main channel. From GUI it doesn't work, Well I can live with this.. ;)

---

