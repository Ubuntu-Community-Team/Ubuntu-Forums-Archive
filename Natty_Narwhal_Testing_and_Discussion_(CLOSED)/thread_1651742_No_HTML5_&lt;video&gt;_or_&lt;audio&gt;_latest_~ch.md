---
title: "No HTML5 &lt;video&gt; or &lt;audio&gt; latest ~chromium-daily"
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hugmenot on 2010-12-23
Am I the only one who get disabled HTML5 media elements in the most recent Chromium builds from the daily PPA?

I get 0/20 for video and audio on this page:

[http://html5test.com/](http://html5test.com/)

---

### Post by jfernyhough on 2010-12-23
Could be. I got 22/27 for Video and 20/20 for Audio.

```
Chromium	10.0.620.0 (Developer Build 70025) Ubuntu 10.10
WebKit		534.16
V8		3.0.4.1
```

---

### Post by hugmenot on 2010-12-23
Ja, but that is Maverick. On my other Maverick machine it works too, but not on natty.

Can you test the same for Natty as well?

---

### Post by cariboo on 2010-12-23
I'm running a fully up-to-date Natty install, and I get 22/27 on video and 20/20 on audio. I'm running chromium  8.0.552.224(68599)

---

### Post by hugmenot on 2010-12-23
> **cariboo907 said:**
> I'm running a fully up-to-date Natty install, and I get 22/27 on video and 20/20 on audio. I'm running chromium  8.0.552.224(68599)

Thanks, but I’m talking about chromium-daily.

jfernyhough’s version was the right one (10.0.620.0), but the wrong series (10.10)

---

### Post by anders_c_ on 2010-12-23
10.0.620.0 (70025) Ubuntu 11.04

Video 0
Audio 0

64 bit

---

### Post by Mr. Picklesworth on 2010-12-23
Yeah, it comes and goes in the dev and beta channels ;)
I can confirm that with the recent 32-bit build for Maverick.
There's actually a [stable Chromium ppa]("https://launchpad.net/~chromium-daily/+archive/stable") now. Whenever this happens, I contemplate switching to that but eventually some little thing (OMG WebGL is on by default!) pulls me back to the bleeding edge.

---

### Post by cariboo on 2010-12-23
With today's updates, html5 video doesn't work, audio does, no matter what that web pages says.

---

### Post by cg9999 on 2011-01-03
Still seems to be broken today (64bit Natty and Chromium-daily) 
Dev and beta seem to be broken too, so maybe it's related to an external lib?

---

### Post by cariboo on 2011-01-03
I suggest you check what mirror you are upgrading from, as the problem has been fixed with updates for me.

---

### Post by zika on 2011-01-03
I have 10.0.627.0 (70377) Ubuntu 11.04 and no HTML5...
It works in (among many others) GoogleChrome 10.0.612.1 dev ...

---

### Post by cg9999 on 2011-01-03
> **zika said:**
> 
It works in (among many others) GoogleChrome 10.0.612.1 dev ...

I tried downgrading to dev again, version 10.0.612.1 (Developer Build 69289)

Still no luck with html5 video.
Did you try the different versions on the same box?

> **cariboo907 said:**
> I suggest you check what mirror you are upgrading from, as the problem has been fixed with updates for me.

I'm using fi.archive.ubuntu.com (alias for ubuntu.trumpetti.atm.tut.fi) which according to this page should be up to date: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
also I'm getting the latest updates announced on natty-changes ml

---

### Post by zika on 2011-01-04
> **cg9999 said:**
> I tried downgrading to dev again, version 10.0.612.1 (Developer Build 69289)

Still no luck with html5 video.
Did you try the different versions on the same box?

No, HTML5 is not high on the list of my priorities and I have a dozen of browsers installed, so...
I get the latest version from chromium-daily...
I think that numbering is not the same for GoogleChrome & Chromium...

---

### Post by kaldor on 2011-01-04
Using the daily build on OS X and HTML5 videos do not load; not just on Ubuntu in that case.

Version 10.0.628.0 (70392) on Snow Leopard.

---

### Post by hugmenot on 2011-01-07
Works again after [this upload]("https://lists.ubuntu.com/archives/natty-changes/2011-January/004895.html").

Thanks for testing.

---

