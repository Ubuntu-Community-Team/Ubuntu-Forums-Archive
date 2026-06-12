---
title: "No sound in Amarok, all other players fine"
date: 2009-06-14
forum: Multimedia Software
---

### Post by potatopal on 2009-06-14
Just got my system up and running after a long stint with Windows.
Everything is working perfectly, except for this.

Whenever I play a song in Amarok 2.1 it speeds through the list of songs, in two or three seconds, and plays no sound.

Any help at all is appreciated.

---

### Post by potatopal on 2009-06-14
Not sure what other information would be helpful here, but I'm happy to provide if something would help.

Bump for music.

---

### Post by mc4man on 2009-06-14
Only had jaunty installed for a little while so can't be that helpful.

try this in a terminal (the phonon.... should be installed already, doesn't hurt to ck.

```
sudo apt-get install libxine1-ffmpeg phonon-backend-xine
```

I did notice that amarok 2 has no way to set the audio output, so you're at the mercy of pulseaudio there.


If you happen to have wma3(pro) or wma lossless and are running a **32 bit install** then this package will be useful

[http://packages.medibuntu.org/jaunty/w32codecs.html](http://packages.medibuntu.org/jaunty/w32codecs.html)

---

### Post by besnef on 2009-08-16
Thanks mc4man!

I'm not the original poster but I had exactly the same problem and this fixed it.  As you said, the phonon was already there but it did install the libxine1-ffmpeg.

---

### Post by EKa on 2010-11-10
> sudo apt-get install libxine1-ffmpeg phonon-backend-xine

But what if this doesn't work?

---

