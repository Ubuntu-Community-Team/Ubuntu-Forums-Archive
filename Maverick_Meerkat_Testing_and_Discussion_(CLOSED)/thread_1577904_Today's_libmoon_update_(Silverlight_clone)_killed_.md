---
title: "Today's libmoon update (Silverlight clone) killed Google Chrome"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2010-09-19
Like the title says...

After I booted 10.10 this morning, I checked for updates.

The only updates involved *libmoon*, which is a free Silverlight 2.0 clone.

After the updates were completed, I tried to open Google Chrome (stable channel), but it was DOA.

Running Chrome via CLI (google-chrome) reported a segfault error while opening *libmoon*.

Firefox started, as normal.  Only Chrome was affected by the update.

The fix, for now, was to purge *libmoon*.

I can live without Silverlight -- but not so without Chrome...   :)

---

### Post by MacUntu on 2010-09-19
It's known and not limited to Chromium (also affects Thunderbird and Firefox 3/4). Strange thing: I don't see this on every machine.

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/621563/comments/8](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/621563/comments/8)

That bug seems abandoned, but there's another one - unfortunately I cannot find it.

There's your bug:

[https://bugs.launchpad.net/ubuntu/+source/moon/+bug/624062](https://bugs.launchpad.net/ubuntu/+source/moon/+bug/624062)

But there was another one with more information. Hm...

---

### Post by VinDSL on 2010-09-19
> **MacUntu said:**
> There's your bug:

[https://bugs.launchpad.net/ubuntu/+source/moon/+bug/624062](https://bugs.launchpad.net/ubuntu/+source/moon/+bug/624062)Thanks!

I marked the bug as affecting me, and added a comment.  ;)

---

