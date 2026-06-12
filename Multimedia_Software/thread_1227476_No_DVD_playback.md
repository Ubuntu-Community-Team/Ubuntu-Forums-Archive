---
title: "No DVD playback"
date: 2009-07-30
forum: Multimedia Software
---

### Post by BrynC on 2009-07-30
I've attempted DVD playback in GXine and Totem, both are giving me errors stating they can't locate my DVD drive. I'm running Jaunty, on an Acer Aspire 5535, and can't for the life of me think what's going wrong as I've been running discs from that drive since I installed Ubunntu on here...

Anything'd be appreciated.
Cheers.

---

### Post by Raffles10 on 2009-07-30
Do you have libdvdcss2 ? It is required to read encrypted dvd's.

To install it you need to enable the medibuntu repository: [Medibuntu]("http://www.medibuntu.org/")

Follow the repository how-to and then:

```
sudo apt-get install libdvdcss2
```

---

### Post by igorzwx on 2009-07-30
Very good advice!

The best codecs are in Medibuntu.

I would propose to install a little more:
**[Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready]("http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html")**

[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

If you have already a wrong codec installed, you may need to
clean this hidden folder in your home folder:

~/.dvdcss

---

