---
title: "Audacity records fine, but won't play back."
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Envergure on 2008-03-12
Audacity recorde fine, but when I try to play sound from it it says "Error while opening sound device. Please check the output device settings and the project sample rate."

It worked fine until a week ago, then it just stopped.  I've tried rebooting, reinstalling and removing software I've installed since then, but nothing works.

Other stuff like VLC and Rhythmbox work fine.

Any ideas?

---

### Post by gleeadnauseam on 2008-03-31
i am experiencing the same problem.
not quite sure of an answer though.

---

### Post by hdixon on 2008-04-18
Same thing here - found the post in here about Audacity not liking ANYthing else that could grab the Audio ports, even firefox. I shutdown everything that _could_ use Audio and then I was able to change the prefs to the appropriate ALSA device and playback mp3s.

---

### Post by Endolith on 2008-05-07
Bug? [https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/202791](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/202791)

---

### Post by i8bugs on 2008-07-23
This finally worked for me:

sudo apt-get remove jackd

or, go to Synaptic and search for "jacked" and remove it.  I tried everything else and this was the only thing that worked.

i8bugs

---

