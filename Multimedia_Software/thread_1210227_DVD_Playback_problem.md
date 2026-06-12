---
title: "DVD Playback problem"
date: 2009-07-11
forum: Multimedia Software
---

### Post by Nico0020 on 2009-07-11
For starters, yes I have installed the codecs from the repos.  I can play any kind of filetype, but my dvds dont work.  I used to be able to play them a few distros back I think, but I can no longer.  I can't really describe what is happening so I will post a picture of it.  Every few seconds I get clear video, then it just goes back to this garbled up stuff.  

Interestingly enough, my friend gave me a .deb of LinDVD to try and see if I got better results.  When I tried it the DVDs play without this video error, but after about 5 mins of play the playback stops.  So im not sure if that means anything.

My current system setup is Ubuntu 9.04
Dell Inspiron E1505
1.6 Ghz Intel Centrino Duo
1GB of Ram
Nvidia GeForce Go Series card.  
I do not have desktop effects enabled either.  does anyone have an idea why this is happening?  If you need any other information just ask.  thanks in advance.

---

### Post by kixome on 2009-07-11
i have that problem sometimes(only when extra desktop effects are enabled though) have you tried libdvdcss2?

---

### Post by kixome on 2009-07-11
also try vlc media player! it can play most anything

---

### Post by Nico0020 on 2009-07-11
> **kixome said:**
> i have that problem sometimes(only when extra desktop effects are enabled though) have you tried libdvdcss2?

The ubuntu restricted extras?  yes I do have that installed.  I have tried VLC which has the same problems.

---

### Post by hansdown on 2009-07-11
Hi Nico0020.

```
Ubuntu restricted extras
``` and ```
libdvdcss2
``` are two different things.

You should try installing ```
libdvdcss2
``` and also ```
libdvdread4
```

There are a number of cards in the go series. Could you narrow it down a little?

[http://www.google.ca/search?q=Nvidia+GeForce+Go+Series++in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Nvidia+GeForce+Go+Series++in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Nico0020 on 2009-07-11
libdvdcss2 seems to have fixed the problem.  thanks alot.

---

