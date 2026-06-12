---
title: "Ubuntu 10.04 can't recognize my iPod"
date: 2010-08-02
forum: Multimedia Software
---

### Post by suaf on 2010-08-02
I've just installed Ubuntu 10.04. I'm using and old iPod Shuffle which now can't be recognized as an external device. I had 9.10 before and didn't have that problem. 
Can anyone help me? I tried that:

[http://ubuntuforums.org/showthread.php?t=576065](http://ubuntuforums.org/showthread.php?t=576065)

No result.
It works fine in Windows.
The player itself charges the battery.

Please help

---

### Post by suaf on 2012-09-25
SOLVED: It was recognized by lsusb, but could not mount, and no players could read it. Finally, I found the solution in a bug thread - I had to remove libgpod-common and it worked! Two years later...
Hopefully this is still of use to somebody:

[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971)

---

