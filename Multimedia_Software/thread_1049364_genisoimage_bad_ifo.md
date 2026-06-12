---
title: "genisoimage bad ifo"
date: 2009-01-24
forum: Multimedia Software
---

### Post by Error403 on 2009-01-24
Hi, I tried using a windows application to compile some kids avis to one huge video_ts directory so I can move it over to my ubuntu box and compile a .iso from it and burn it afterwards.  However, here's what genisoimage gives me:

```
phil@galactica:~$ mkisofs -dvd-video -v -o caillou.iso caillou
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage 1.1.6 (Linux)
Scanning caillou
Scanning caillou/VIDEO_TS
genisoimage: Implementation botch. Video pad for file VIDEO_TS.BUP is -1127032936
genisoimage: Either the *.IFO file is bad or you found a genisoimage bug.
```

I'm guessing my encoding software (roxio) is the culprit, because convertxtodvd works fine for single movies and simple compilations.  But now I'm trying to fit around 20 caillou episodes on that dvd, mindless of the compression.  So, is there a way to fit a few avi files in a dvd, in a CLI way? (I ssh to my box since I havent installed any GUI for performance reasons)

A friend of mine showed me how to make a dvd out of a .avi movie, but now I want to fit more than one of them.

---

