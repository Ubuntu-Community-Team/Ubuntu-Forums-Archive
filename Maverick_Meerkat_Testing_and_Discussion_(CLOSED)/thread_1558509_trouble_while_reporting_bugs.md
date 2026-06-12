---
title: "trouble while reporting bugs"
date: 2010-08-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfreak_ on 2010-08-22
So there was a bug and I tried to use apport to report it. So at the very end it said could connect as the connection has been blocked. I suspect this may be due to the fact that I am behind a proxy. In case of firefox, synaptic , etc I can set the proxy easily . but how to set proxy for apport?

---

### Post by ktp on 2010-08-22
> **jfreak_ said:**
> So there was a bug and I tried to use apport to report it. So at the very end it said could connect as the connection has been blocked. I suspect this may be due to the fact that I am behind a proxy. In case of firefox, synaptic , etc I can set the proxy easily . but how to set proxy for apport?

You can try following and try to use ubuntu-bug command, but it might not work:

[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto#Setting](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto#Setting) up apt-get to use a http-proxy

There are few bugs about this:

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/619610](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/619610)
[https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/94130](https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/94130)

---

