---
title: "How do you get Kaffeine to play DivX 5 files?"
date: 2006-10-22
forum: Multimedia &amp; Video
---

### Post by theosib on 2006-10-22
I was wondering if anyone knew how to get DivX 5 files to work with Kaffeine.

I have installed a load of win32 codecs from mplayerhq (or whatever it's called).  I've installed libavcodec-dev.  I've installed the official DivX codec (6.1.1 or something).

No matter what, I simply cannot get Kaffeine to play certain avi files.  Kaffine (xine) always complains that there is no codec available for "DivX 5".

Has anyone ever gotten this to work?  Or is Kaffeine simply unable to play these files, no matter what?

Thanks.

---

### Post by qamelian on 2006-10-22
Not sure what's causing your problem, but I can confirm that kaffeine can play DivX files with w32codecs and the xine backend installed.

---

### Post by theosib on 2006-10-22
Well, I managed to get w32codecs installed, but still no go.  Kaffine insists that there is no codec for it.

I'm also noticing something odd.  I'm looking at this page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

No matter what I enabled in /etc/apt/sources.list, I absolutely cannot get libxine-extracodecs to be available as a package.

---

### Post by theosib on 2006-10-23
BUMP.  I've been trying other things, and nothing works.  Please help!

---

### Post by qamelian on 2006-10-23
You need to enable multiverse to get libxine-extracodecs installed. Once you enable multiverse in /etc/apt/sources.list, bring up a terminal and type ```
sudo aptitude update
``` to make sure your cache is up to date.
Then do ```
sudo aptitude install libxine-extracodecs
``` and it should install.

---

