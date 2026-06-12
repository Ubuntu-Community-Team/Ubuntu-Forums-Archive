---
title: "mandvd on jaunty 9.04 slideshow problem"
date: 2009-05-20
forum: Multimedia Software
---

### Post by timcredible on 2009-05-20
in case anyone is trying to create a slideshow with mandvd in 9.04 jaunty, you'll need to do this to get it to work:

with jaunty, and dvd-slideshow 0.8.2, you need to do this:
```

sudo gedit /usr/bin/dvd-slideshow

```
and then do a replace all of "-compose src-over" with a space.  the problem turned out to be that dvd-slideshow was sending this parameter to the program "composite", which doesn't know what that parameter is.

---

