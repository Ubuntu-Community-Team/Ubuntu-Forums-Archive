---
title: "REALLY want to Revert Gutsy Xorg/Xserver to Feisty - HOW???"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by OzzyFrank on 2007-12-17
OK, I've read enough threads to realise you can't roll back Gutsy to Feisty, and that's not what I want anyway. I just want to see if I can somehow revert to the Xorg/Xserver that Feisty has, as the ATI support for my card is messed up beyond belief. I've never been able to get "fglrx" to work, and trying the newest one doesn't change that. Using "radeon" never did much, but now it won't boot at all. But the worst part is the crappy "ati" driver, which at least gave me good video if not any desktop effects (without a script for Beryl), now gives me a garbled screen when I try to boot with it.

I am forced to use "vesa" which at least gives me a display, but video clips and DVD playback are so unbearably slow I am forced to reboot into Windows to watch them. No updates have fixed anything since Gutsy's release, so am wondering if there is a way to revert back to what I had video wise before the upgrade. Thanks

---

### Post by ajgreeny on 2007-12-17
Some older cards work well with the "ati" driver.  My 9200SE is ghreat, but I realise it's not the card for a gamer.  Great for compiz though without any problems or jumpy video, etc.

What card do you have, as it may just be better to bite the bullet and get an nvidia card, as they tend to be much better supported.

---

### Post by OzzyFrank on 2007-12-17
Mine is the Radeon 9200, and back in Feisty could only load Beryl with a script (it worked after installation but then didn't, till I found a script to load it with). I'm not even worried about Beryl/Compiz... I just want to run a better driver than crappy "vesa". I have seen HEAPS of posts with similar tales of woe from ATI card owners who upgraded to Gutsy... I just figured this may have been addressed by now (????).

The card runs fine in Feisty, but that is the past now, since one cannot rollback the whole OS. I try other distros like Sabayon and Compiz works even running the Live CD, on my crappy card, straight "out of the box". Seems the "just works" applies to any other distro running that card, not Ubuntu. Seems a shame they've made things worse for some ATI owners rather than better.

Anyway, I've tried basically ever driver xorg accepts and the only one that doesn't give me either a black screen that goes nowhere or a garbled screen that does get to the desktop but is totally unuseable is the "vesa" driver, which is of course pretty useless for playing back video and DVD, etc.

Has anyone got ideas on how to remedy this??

---

