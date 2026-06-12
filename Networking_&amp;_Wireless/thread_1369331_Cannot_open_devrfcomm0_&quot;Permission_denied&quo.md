---
title: "Cannot open /dev/rfcomm0: &quot;Permission denied&quot;"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by mark bower on 2009-12-31
9.04 user. I am trying to use /dev/rfcomm0 to reach to a bluetooth printer adapter (and get the permission denied msg). I read what Paolo C. did (Bug #374075) as a work around, but I am inexperienced as to what specifically to enter on cmd line? His comments are,

"Manually adding:
$ sudo chown username:users /dev/rfcomm0
to rc.local "fixed" the issue."

so i tried: sudo chown rocky /dev/rfcomm0 and that did not work (rocky is my user name)
then i tried: sudo chown rc.local /dev/rfcomm0 and that did not work, would not accept format

seeing what I am trying to do, could you please supply specifc code lines needed. I have ordered 9.10 which I understand fixes the problem.

mark bower

---

