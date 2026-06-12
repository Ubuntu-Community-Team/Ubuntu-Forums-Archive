---
title: "mencoder -sstep to non-key-frame position?"
date: 2010-08-19
forum: Multimedia Software
---

### Post by wdaniels on 2010-08-19
Hi!

Does anybody know a way to make mencoder chop the first n seconds from the beginning of a file without using -sstep parameter? The problem with -sstep is that it will seek to the next key frame after the time index given, which can be a few seconds out in my tests, and it's just too inaccurate for what I need :(

Maybe there is another way to do this more precisely? Any help much appreciated.

---

