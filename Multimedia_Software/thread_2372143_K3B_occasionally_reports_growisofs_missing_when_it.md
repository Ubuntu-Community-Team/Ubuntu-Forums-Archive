---
title: "K3B occasionally reports growisofs missing when it's installed"
date: 2017-09-21
forum: Multimedia Software
---

### Post by accounts0 on 2017-09-21
Running Ubuntu Server 16.04.3 LTS with Kubuntu desktop installed & of course using K3B. Occasionally, maybe half the time I start it, seemingly at random, it'll return an error screen at startup [1] complaining about growisofs missing- when it's not. The error message says it needs version >5.10 & to install dvd+rw-tools, but I have both installed at 7.1-11. Shown in below referenced screenshot.

[1]
[https://imgur.com/W9QRAO0](https://imgur.com/W9QRAO0)

---

### Post by accounts0 on 2017-10-17
bump

---

### Post by Yellow Pasque on 2017-10-18
I find k3b to be quirky with permissions. Can you take a screenshot of the setup screen?
I've always had best success with checking the 'use burning group' option and set the group to be 'cdrom' (assuming cdrom group exists and user is in it, which is the default for Ubuntu IIRC).

---

