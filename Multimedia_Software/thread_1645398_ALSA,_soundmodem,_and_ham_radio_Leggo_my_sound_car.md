---
title: "ALSA, soundmodem, and ham radio: Leggo my sound card!"
date: 2010-12-14
forum: Multimedia Software
---

### Post by starkruzr on 2010-12-14
So, I am trying to use this: [http://www.baycom.org/~tom/ham/soundmodem/](http://www.baycom.org/~tom/ham/soundmodem/) which is in the Ubuntu repositories and all, to do some AX25 packet radio over Ham frequencies.  This kind of works.  Sort of.  I cannot get it to work reliably.

The main issue appears to be that *something* keeps grabbing control of my ALSA sound card device and preventing soundmodem from using it.  My solution to this was to load the snd-dummy sound card driver as the "zeroth" sound device, letting whatever keeps trying to seize control of audio grab that rather than my actual sound card.  This is the part that does not work reliably.  The snd-dummy device fails to load consistently.

I have Pulse disabled for this user, and it's not running.  I can't seem to permanently disable gnome-volume-control-applet, but even with that killed, reloading ALSA still doesn't let me either load the dummy driver reliably or use my sound device with soundmodem.  I tried installing xfce4 and using that as the user session in the hopes that it would be more lightweight with sound usage, no help.

Can someone help me figure out how to get the Ubuntu system to just load my sound drivers, create the devices, and STOP, without trying to do anything else with sound?  Or to get the snd-dummy driver to always be the zeroth card?

Thanks!

---

