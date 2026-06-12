---
title: "Sound stopped working on Dell D610"
date: 2009-12-03
forum: Multimedia Software
---

### Post by nieldw on 2009-12-03
The sound on my mother's Dell Latitude D610 just stopped working. I am running ubuntu studio 9.04 with Kernel 2.6.28.16-generic. I did try some of the older kernel versions (there because of updates), but no joy. Any suggestions?

I tried working through the guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), even recompiling the alsa-driver. I did notice, however, that the main user was not part of the audio group. I found this strange because the sound did work before, and I then added the main user to the audio group in /etc/group. No joy yet.

The only thing I haven't tried, because of low bandwidth, is purging linux-sound-base and the alsa-packages, because I will have to reinstall ubuntu-desktop and ubuntustudio-desktop.

Any help will be appreciated.

---

