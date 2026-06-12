---
title: "Network manager and wireless adaptor + Wicd"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by ringsofsaturn on 2009-01-09
Hello,

Have an ibook G3 (New World) with 192 MB RAM and 500MHZ PowerPC processor. It has currently got 6.06 Xubuntu installed but have problem with wireless. Ibook has no airport card and I was wondering if I could install later version of Network Manager (or possibly install Wicd?) that supported wireless.I have ZyXEL USB adaptor.

Downloaded Network Manager 0.6.6 0ubuntu5 but wouldn't install: "Error: Dependency is not satisfiable: dhcdbd". Am assuming it's not compatible with 6.06.

I installed Ubuntu 8.04 recently and went online wirelessly with previously mentioned adaptor but 8.04 VERY slow even with Xfce4 desktop. Also had serious display issues. See thread: "Re: Xubuntu 7.10 on ibook PowerPC not loading" if you are interested.

Have posted this on Apple users forum but thought this forum may be more relevant and attract different answers.

I am NOT particularly proficient with Linux or experienced but will "have a go" .


Many thanks.

Thought I'd posted this earlier but couldn't find the thread... :confused:

---

### Post by imdano on 2009-01-09
> **ringsofsaturn said:**
> Downloaded Network Manager 0.6.6 0ubuntu5 but wouldn't install: "Error: Dependency is not satisfiable: dhcdbd". Am assuming it's not compatible with 6.06.
Actually, NM **requires** dhcdbd.  Try downloading through apt-get and see if you can install NM then.

---

### Post by ringsofsaturn on 2009-01-09
Thanks imdano, but it's already installed.

---

