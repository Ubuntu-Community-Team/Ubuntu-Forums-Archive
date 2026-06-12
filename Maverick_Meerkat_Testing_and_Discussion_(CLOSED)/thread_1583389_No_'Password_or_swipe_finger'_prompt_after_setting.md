---
title: "No 'Password or swipe finger' prompt after setting up ThinkFinger (Ubuntu 10.10)"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tkane on 2010-09-27
Hi, I don't get neither 'Password or swipe finger' nor whatever gnome's graphical swipe your finger prompt is after setting up ThinkFinger. tf-tool --acquire and tf-tool --verify both return no problems.

Here's the relevant excerpt from my /etc/pam.d/common-auth
```

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]    pam_thinkfinger.so 
auth    [success=1 default=ignore]    pam_unix.so nullok_secure try_first_pass

```Wonder if anyone has got an idea what possibly went wrong.. thanks!

---

### Post by Iowan on 2010-09-27
Moved to Maverick Meerkat Testing and Discussion

---

### Post by ranch hand on 2010-09-27
This is a joke right?

Nobody would really name an ap "thinkfinger" would they?  If they did then what were they smoking.

---

### Post by cariboo on 2010-09-27
There's even a whole wiki page for [ThinkFinger]("https://wiki.ubuntu.com/ThinkFinger").

If I remember correctly this first showed up for IBM Thinkpads.

---

### Post by tkane on 2010-09-28
ThinkFInger ain't no joke... and it isn't working :-(

---

