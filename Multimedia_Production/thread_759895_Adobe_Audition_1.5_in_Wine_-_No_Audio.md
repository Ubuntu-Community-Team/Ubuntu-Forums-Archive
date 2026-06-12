---
title: "Adobe Audition 1.5 in Wine - No Audio"
date: 2008-04-19
forum: Multimedia Production
---

### Post by malocite on 2008-04-19
I have installed Wine .9.4.6 under Ubuntu Gutsy with all updates installed.

I am trying to run Adobe Audition 1.5 which says it works on the winedb.

I am able to install and run the program, but when I play any sounds I get just a garbled hiss.  

I guess you can all agree that sound on Adobe Audition is sort of important.  Does anyone have any ideas as to why this happens?  Other than the generic 'wine never works' answer? :)  Or how to fix it?

--malocite

---

### Post by dperfors on 2008-04-21
First I didn't work with the wine/Audition combination at all, so this could not be the answer you are expecting :)

Do you know if other programs produce understandable sound from within wine? if not it could be a problem in your configuration...

---

### Post by trippinnik on 2008-04-23
when you set the sound emulation for wine in winecfg which method are you using?  I recommend trying another option like full driver emulation or something.  Also do you have the wine repo so you can get the latest wine.

---

### Post by thorgal on 2008-04-24
I would suggest the following :

- update wine (v0.9.60)
- install wineasio (v0.5 or v0.7.3)
- in winecfg, select ALSA only (no OSS, no JACK)
Make sure you have a drive (e.g. Z:\) mapped to your / (root) directory.

OK, now the tricky part : get jackd up and running. It could be easy or not, depending on your hardware. Try the GUI qjackctl to run jackd. You may try first without real-time priviledges, just to check that it can run. If you have a PCI card, then set the buffer size to 1024 and the frame period to 2. If you have a USB sound device, set the frame period to 3.
If you have a firewire device, then jackd can run with the freebob driver but then, I don't know how Wine would handle that.

If you get jackd running, then in Adobe Audition, select wineasio as the sound driver. That should work without problems. If you get that far, to improve performance a good deal, get a real-time kernel, make sure you can run processes with RT priviledges (look into /etc/security/limits.conf and google around, there is tons of info regarding RT stuff in UbuntuStudio) and restart jackd through qjackctl after toggling the RT mode. Then you can decrease the buffer sizes to lower values (512, 256 or even lower) and see if your system can take it (it's to achieve a reasonably low latency).

Hope this helps.

---

