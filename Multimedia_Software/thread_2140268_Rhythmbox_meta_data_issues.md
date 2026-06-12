---
title: "Rhythmbox meta data issues"
date: 2013-04-29
forum: Multimedia Software
---

### Post by bugbear6502 on 2013-04-29
I'm using rhythmbox primarily as a library management tool for music files, prior to moving them to my mp3 player.

I'm using the meta data editing, and (in particular)
[https://launchpad.net/rb-fileorganizer](https://launchpad.net/rb-fileorganizer)
to get everything "nice".

This was working fine under 11.04.

I'm now on 12.04 (can't use 12.10 due to my non-PAE cpu).

I ran across the big meta data disaster, and fixed it by installing 2.97

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/996150](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/996150)

[http://www.webupd8.org/2012/06/rhythmbox-297-released-with-improved.html](http://www.webupd8.org/2012/06/rhythmbox-297-released-with-improved.html)

But.

Metadata/ID3 editing is now VERY slow for me, both on single files, but especially
on multiple files. The slowness effects both opening the edit dialog, and
the subsequent writeback.

Worse, yesterday, Ubuntu itself crashed twice whilst performing
such edits.

I've tried to google, but the applicable terms are very
general, leading to non-useful results.

Any assistance, either in fixes or diagnosis, would be very welcome.

   BugBear

---

### Post by bugbear6502 on 2013-04-30
Odd - on re-trying last night (on my home laptop) the opening of the "bulk edit"
dialog was reasonably fast. Writing changes back is still slow though.

 BugBear

---

### Post by bugbear6502 on 2013-05-24
Yet more empirical data;
I've had a couple more crashes, both whilst editing large (40 minute or more) mp3 files.

The crash reports spoke of OpenBox having some poorly defined "trouble" with libtiff4, which (interestingly) wasn't installed.

So I've installed it, and subsequently, I had a terribly ... interesting instance where
various windows flashed and redisplayed, but the system stayed up.

So I suspect I've "bodged it" if not actually "fixed it"

 BugBear

---

