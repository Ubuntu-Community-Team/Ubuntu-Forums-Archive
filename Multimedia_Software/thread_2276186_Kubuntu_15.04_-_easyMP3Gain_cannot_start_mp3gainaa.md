---
title: "Kubuntu 15.04 - easyMP3Gain cannot start mp3gain/aacgain"
date: 2015-04-30
forum: Multimedia Software
---

### Post by stafio on 2015-04-30
Running Kubuntu 15.04, I installed easyMP3Gain and it is pretty useless because it can't start mp3gain or aacgain. Neither of them are available in repos either. Are there any alternatives?

---

### Post by stafio on 2015-04-30
It turns out mp3gain was [just removed from 15.04]("https://answers.launchpad.net/ubuntu/+source/mp3gain/+question/264529"), so I downloaded and installed the [package from Utopic]("http://packages.ubuntu.com/utopic/mp3gain"). There is a [ppa with aacgain]("https://launchpad.net/~stefanobalocco/+archive/ubuntu/ppa/+packages"). Similarly, I just downloaded and installed the aacgain package rather than adding the whole ppa.

---

### Post by karsta62 on 2015-06-07
> **stafio said:**
> It turns out mp3gain was [just removed from 15.04]("https://answers.launchpad.net/ubuntu/+source/mp3gain/+question/264529"), so I downloaded and installed the [package from Utopic]("http://packages.ubuntu.com/utopic/mp3gain"). There is a [ppa with aacgain]("https://launchpad.net/~stefanobalocco/+archive/ubuntu/ppa/+packages"). Similarly, I just downloaded and installed the aacgain package rather than adding the whole ppa.

Thanks. I wonder what might be the big idea of removing it?? 
Do they want us to start using windows??

- Karsta

---

### Post by Rich53201 on 2015-06-25
[URL="https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=761847"]
[/URL]"RM: mp3gain -- ROM; dead upstream, probably insecure.... 
"Please remove mp3gain from unstable. It is already gone from testing, dead upstream, probably insecure, the primary maintainer is MIA, and[COLOR=#800000] there is a better alternative (python-rgain)[/COLOR].
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=761847](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=761847)


Some info about rgain - ReplayGain
[https://bitbucket.org/fk/rgain/](https://bitbucket.org/fk/rgain/)
[http://packages.ubuntu.com/trusty/python/python-rgain](http://packages.ubuntu.com/trusty/python/python-rgain)

---

