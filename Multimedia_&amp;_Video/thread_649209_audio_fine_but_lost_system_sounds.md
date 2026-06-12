---
title: "audio fine but lost system sounds"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by dannemil on 2007-12-24
I have seen posts on this same problem with almost no solutions. I can play audio (music) through XMMS, Quod Libet, etc. I even have the bongos at login. What I don't have after upgrading to Gutsy are any of the other system sounds (welcome, clicks, errors, etc.). While I admit this is not a major problem it is annoying as those sounds help provide feedback about specific events.

I have tried all of the suggested solutions for sound problem in the Comprehensive Sound thingee, I have compiled alsa from scratch, nothing works. When I click on those events to test them in System/Preferences/Sound/Sounds I get nothing, nada. But If I go to the /usr/share/sounds directory where those sounds live, I can play the sound files just fine (beeps, boops, errors, welcome, etc.).

One other symptom is that alsamixer will not hold my settings after reboot. In particular, whenever I reboot and ckeck alsamixer, the PC speaker is muted. I have executed the command from the console to save the alsamixer settings for my card, and it executes fine, but when I come back - PC speaker is muted. While this too is annoying, I don't think that is the issue because I can get audio (music) from external speakers or headphones, and on another system that has Ubuntu 7.1, the PC speaker is mute, but I still get system sounds.

I am reasonably savy when it comes to linux and ubuntu, but this one has me completely stumped.

---

### Post by heatpumpcontrol on 2007-12-24
Had the same issue. Here's your answer

[http://ubuntuforums.org/showthread.php?t=576328](http://ubuntuforums.org/showthread.php?t=576328)

In addition to installing mpg123, try installing mpg123-alsa & esound. You may have to reboot.

---

### Post by dannemil on 2007-12-25
> **heatpumpcontrol said:**
> Had the same issue. Here's your answer

[http://ubuntuforums.org/showthread.php?t=576328](http://ubuntuforums.org/showthread.php?t=576328)

In addition to installing mpg123, try installing mpg123-alsa & esound. You may have to reboot.

Thanks. Installed everything but still no system sounds, and no mouse-over sound for any kind of sound format. Basically, I can play audio files, but I have not system sounds. 

Any help?

---

