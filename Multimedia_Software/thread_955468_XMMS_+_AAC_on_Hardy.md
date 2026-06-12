---
title: "XMMS + AAC on Hardy"
date: 2008-10-22
forum: Multimedia Software
---

### Post by realn on 2008-10-22
Hello,

I need help, please: I cannot play AAC streaming URLs through xmms. I looked all around, the best I could find was a xmms-mp4 deb package on launchpad which I try to install manually and refuses to install because of the libglib.1.2 unresolved dependency. I would be very grateful to anyone who can help me with that. I would like to add that I have installed xmms through the deb package from launchpad, too (thanks to whomever put it there).
 As for why the xmms was removed altogether from HH, now, I would like  - off-topicly - to express my opinion: WTF?. I read some links about how it's obsolete, about how many bugs it has, about the plugins no longer maintained, etc. Yeap, it's obsolete, but everybody wants it. PLEASE, don't force people use software which they don't like. There are enough companies doing that, let's not do the same.
Thanks a bunch !

---

### Post by SuperSonic4 on 2008-10-22
Isn't XMMS default on Xubuntu rather than Kubuntu :p

Try looking for the faad2-xmms package or similar (faad2 is aac decode)

```
sudo apt-get install faad2-xmms
```

---

### Post by realn on 2008-10-22
xmms is no longer available in repos in Hardy Heron, no matter which version - xubuntu or kubuntu.

As for faad2-xmms, is no longer there, too:

sudo apt-get install faad2-xmms
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package faad2-xmms

---

### Post by markbuntu on 2008-10-22
There is an offer of a fix for the libglib1.2 and libglib1.2dbl dependency problem on the amd64 xmms build. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

---

### Post by realn on 2008-10-22
Markbuntu, thanks a lot for the suggestion. I had already browsed that post, it solves the problem of installing xmms on hardy on 32& 64 bits.
My problem is about AAC support on xmms on hardy. That guy had the same problem:
[http://ubuntuforums.org/showpost.php?p=5802236&postcount=19]("http://ubuntuforums.org/showpost.php?p=5802236&postcount=19")

So - what's the answer? I'm starting to get confused/frustrated - should I just downgrade to gutsy? Or get away from ubuntu ? such a pity ...

---

### Post by realn on 2008-10-22
Well, I managed to install the AAC plugin for XMMS. The problem is that it cannot play the AAC streams (AAC+ files). I'll update thread title and still looking for advice. I am not even sure that such plugin ever worked (even existed).

---

### Post by realn on 2008-10-22
How do I update thread title?

---

