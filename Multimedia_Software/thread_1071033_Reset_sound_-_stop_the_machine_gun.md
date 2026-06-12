---
title: "Reset sound - stop the machine gun"
date: 2009-02-15
forum: Multimedia Software
---

### Post by lingenfr on 2009-02-15
Normally it happens when I am playing a game. All of the sudden I get a repeating sound like a machine gun. I have tried the advice here:

[http://ubuntuforums.org/showthread.php?p=2742327](http://ubuntuforums.org/showthread.php?p=2742327)

and alsa-utils reset. There may or may not be an app using PCM (like openarena) which I can kill. How every as soon as alsa starts back up, the sound continues.

My sound card is:

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller


The only way that I have found to stop the sound is to reboot. There has to be a better way. Thanks.

---

### Post by lingenfr on 2009-02-23
bump

---

### Post by wolfen69 on 2009-02-23
are you using pulseaudio? sometimes uninstalling pulse and just going with alsa will fix it. just google "remove pulsaudio ubuntu".

---

### Post by lingenfr on 2009-02-23
Thanks for the pointer. Next time this happens I will check pulse audio and see if a client is connected. If so, I will try the kill client command to see if that works. I will report back. Thanks.

---

