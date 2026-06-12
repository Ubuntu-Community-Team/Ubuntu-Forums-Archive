---
title: "netcat / nc question on amd64"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by ahmedre on 2010-02-01
hi,
i am running 64 bit ubuntu, and if i do nc or netcat with any echo at all, i get nothing back.  for example, from this thread: [http://ubuntuforums.org/showthread.php?t=828870](http://ubuntuforums.org/showthread.php?t=828870) - trying to run example 1

```
 echo -e "GET /kdist/finger_banner HTTP/1.0\r\n" | nc [www.kernel.org]("http://www.kernel.org/") 80 | grep latest
```returns nothing at all on my machine, but works fine on all the 32 bit machines i've tried it on.

is anyone else having this problem? :/  it only seems to happen when echo is involved...

thanks!

---

