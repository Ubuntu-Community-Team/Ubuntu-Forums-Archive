---
title: "ATI Xorg Options?"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by wyth on 2007-04-21
Where can one find the possible xorg options for a video card?

I have an ATI Radeon R250, and since the Xorg 7.2 update, fglrx won't work.  So I'm using the open ati driver.  It works *alright*, but could be better.  At least Desktop Effects is reasonably functional. 

But I've found there are options you can enable under Device in xorg.conf to make your card run better, things like ```
Option  "ColorTiling"  "true"
```What I can't seem to find is what specific options are available for specific card versions.  The man pages are very general.  Not all of the options available will work with all cards; some options are only for more recent cards, and some require numbers and not just boolean terms.  So I'm sure I probably have some unnecessary things in my xorg.conf, and am most likely missing some good options and/or have them misconstrued  (I'm baffled by which AGPMode and AGPSize I should run, or why).

Anyone know of a place that describes the options?

---

### Post by wyth on 2007-04-22
Bumpin' this; I can't be the only one curious about it, and there's plenty of views, but just no responses.

---

### Post by Talon2 on 2007-04-22
This is a very good question.  I wish I had the answer.

---

### Post by wyth on 2007-04-22
This offered up some info: ```
man radeon
``` But that's for those using Radeon cards. And although the info is good, I get the feeling it's incomplete.

For instance, [this thread]("http://ubuntuforums.org/showthread.php?t=331372") points out that if you choose, say, ```
Option  "AccelMethod"  "EXA"
``` then you want to be sure to use ```
Option  "XAANoOffscreenPixmaps"
``` and not ```
Option "EXANoOffscreenPixmaps"
```
But that actually conflicts with what's suggested on the [Beryl on Edgy wiki]("http://doc.gwos.org/index.php/BerylOnEdgy"), and neither XAANoOffscreenPixmaps nor EXANoOffscreenPixmaps are in the man page for the Radeon driver.

This is what I'm getting at.   A repository of info for at least the open source driver options would be immensely helpful.

---

