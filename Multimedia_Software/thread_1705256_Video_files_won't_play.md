---
title: "Video files won't play"
date: 2011-03-11
forum: Multimedia Software
---

### Post by Nitewalker on 2011-03-11
I am trying to play a video file on Ubuntu 10.10 from a web site, but when I click on it it just shows it loading, but won't play.

---

### Post by tommcd on 2011-03-12
What kind of video file is it?
Have you installed flash and the multimedia codecs?
If not, then install the *flashplugin-installer* and enable the medibuntu repository and install the codecs you need:
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Be sure to get the *w32codecs* for 32bit Ubuntu, or the *w64codecs* for 64bit Ubuntu, so you can play wmv files. And get *libdvdcss2* for playing DVDs.
Or you can just take the everything-but-the-kitchen-sink approach and install the 
*ubuntu-restricted-extras* package, which installs all of this stuff:
[http://packages.ubuntu.com/maverick/ubuntu-restricted-extras](http://packages.ubuntu.com/maverick/ubuntu-restricted-extras)
I prefer to take a more conservative approach though, so I only install what I need.

---

### Post by andrew.46 on 2011-03-12
> **tommcd said:**
> Be sure to get the *w32codecs* for 32bit Ubuntu.....

It is completely sideways of this question, for which my apologies, but you may be interested to know that MPlayer has bundled a much more comprehensive set of codecs in January 2011 for 32 bit systems:

[http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/)

Medibuntu packages an older and less complete version...

---

