---
title: "Rhapsody changes PCM  output level"
date: 2007-10-24
forum: Multimedia &amp; Video
---

### Post by hjallen on 2007-10-24
I am using Feisty.  When listening to Rhapsody, the PCM level is reset on each new song that is played.  This does not occur when using Pandora or local files using Rhythmbox.  Any thoughts on why this might occur?
Thanks

---

### Post by gatman3 on 2008-01-03
I noticed the same thing.  I reported it to Rhapsody support, but no useful response.  My ultimate solution was to buy an inline volume control for my headphones and let the Rhapsody plugin peg the level where it wants it but.  Then I adjust the volume manually with the external inline slide wheel.

The Rhapsody plugin seems to do some rather direct accesses to the sound device, and it doesn't support typical ALSA niceties like the .asoundrc settings.  In order to route it to my USB audio adapter (the headphone jack for my integrated audio adapter in my laptop is broken), I had to change the order that the sound modules get loaded in the /etc/modprobe.d/alsa-base file, which seems like a pretty draconian workaround to me.  My guess is that the plugin wants low level control of things in some futile attempt to prevent direct recording, or whatever.

---

