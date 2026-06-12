---
title: "swfdec and jackd..."
date: 2008-08-17
forum: Multimedia Software
---

### Post by mback99 on 2008-08-17
Hi ..
I want the sound from swfdec to go through jackd..
It uses alsa.. I just cant figure out how to do it
Help would be apreciated

---

### Post by markbuntu on 2008-08-18
You can look at my guide, it is fairly long and involved but it will give you an idea how to proceed. Once you can get all your alsa apps to play through pulse, the jack section has a method to get any pulseaudio stream into jackd. I never had any real success getting alsa apps to play into jackd but they can all play at once in jack when they play through the pulseaudio jack sink.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The jack section is near the bottom.

---

