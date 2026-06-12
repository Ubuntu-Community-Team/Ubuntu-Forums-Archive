---
title: "Will I be able to run Ndiswrapper and B44?"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by gmstalk on 2009-06-03
If I load B44 for my wired Ethernet, it depends on SSB, which breaks ndiswrapper (wireless). SSB cannot be blacklisted if B44 is to be loaded. So I have a binary decision
1) have wireless work by blacklisting b44 and SSB, but no wired connection
2) Have the wired connection work by loading b44, but no wireless.

I will try creating an RC.LOCAL with modprobe b44 in it and see how that works. This seems kind of janky though.

---

### Post by gmstalk on 2009-06-03
This post should work, I will test it out. 
[http://ubuntuforums.org/showthread.php?t=731177](http://ubuntuforums.org/showthread.php?t=731177)
still, an rc.local file to automate the rmmod of b44, ssb, and ndiswrapper, then a mode probe in the reverse order is still a little janky. Is there a better solution?

---

