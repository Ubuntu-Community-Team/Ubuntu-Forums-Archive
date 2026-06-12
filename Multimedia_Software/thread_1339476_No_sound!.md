---
title: "No sound!"
date: 2009-11-27
forum: Multimedia Software
---

### Post by chinmaya_n on 2009-11-27
Previously also i've got this problem!
No sound but i could play video!
Sound is not coming in any player!
It says NO SOUNDCARD-- ```
sudo /etc/init.d/alsa-utils stop
[sudo] password for chinmaya: 
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1502: No soundcards found...'...                                              [fail] 
chinmaya@chinmaya-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...

```
Yesterday i did some updates as update manager poped up! 
This might be one of the reason, I dont know exactly..
I upgraded alsa to 1.0.21 previously as explained [here]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/") previously when i got this problem!
But now its not working!

Any Ideas ?:D

---

### Post by chinmaya_n on 2009-11-27
Same procedure worked again!!!
Thankx :popcorn:

---

