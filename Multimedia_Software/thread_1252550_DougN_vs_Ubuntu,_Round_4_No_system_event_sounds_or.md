---
title: "DougN vs Ubuntu, Round 4: No system event sounds or Flash 10 audio"
date: 2009-08-29
forum: Multimedia Software
---

### Post by figneutron on 2009-08-29
Doug vs Ubuntu 9.04, Round 4: I have established that I have the correct driver for my sound card installed. I have audio for music cds, movie dvds, and Internet radio. To address the system sounds issue, I was directed by a moderator here to run canberra-gtk-play on an Ubuntu sound file bell.ogg. The result was nada; it didn't play.

Concerning the Flash 10 audio problem, I was given a second directive to place libflashsupport.so in /usr/lib and run ldconfig. I did this, and bash responded */sbin/ldconfig.real: relative path 'libflash.so' used to build cache. *Then, I closed Firefox, re-opened it, and proceeded to YouTube where I played a music video. Again, the result was video without audio when running Flash 10. Previously, I had demonstrated that Flash 10 was installed and working correctly by going the Adobe Flash test webpage. Also, I checked the Firefox Tools/Add-ons listing and saw only one version of Flash there, that is, Flash 10. Using Opera, I have no audio with Flash 10 either.  

Last week I experimented and switched to the Guest account on several occasions. Curiously, almost every time I did so, I got system event sounds and Flash audio but with swfdec-mozilla-plugin running instead of Flash 10. Let me reiterate that this did not happen every time I switched. A few times nothing changed, as is the case when I tried a three times some minutes ago. Now, it seems that I can't reproduce the phenomenon.

I would appreciate coaching to help me win in Round 5.

---

