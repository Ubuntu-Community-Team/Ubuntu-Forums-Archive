---
title: "Videos in Browser don't work"
date: 2009-08-18
forum: Multimedia Software
---

### Post by ComeAlive on 2009-08-18
Hello, I have Kubuntu 9.04 installed. Previously I had an old version of Fedora. When I installed Kubuntu, I found I can play videos from youtube.com, and video.google.com, but videos from places like metacafe.com, dailymotion.com, vids.myspace.com do not work. I have tried various browsers like firefox and seamonkey and epiphany but no luck.

Are my plugins conflicting with each other or something? I never had a problem with Fedora 7 playing videos online, but package updates are no longer made for it...

Thanks for any help, suggestions or guidance that may come my way.

---

### Post by ComeAlive on 2009-08-18
Just an update:

A fine fellow on kubuntu IRC, BluesKaj suggested I install some packages, which I did, but no observable difference resulted:

kubuntu-restricted
flashplugin-nonfree
w32codecs

---

### Post by ComeAlive on 2009-08-18
Update:
We got it to work! Thanks to BluesKaj and kaddi on #kubuntu IRC

in the end we had to remove swfdec-mozilla as it was conflicting with the other flash

phew!

---

