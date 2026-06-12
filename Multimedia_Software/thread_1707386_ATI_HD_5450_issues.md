---
title: "ATI HD 5450 issues"
date: 2011-03-15
forum: Multimedia Software
---

### Post by jamesd256 on 2011-03-15
Hi,

I'm running Ubuntu 10.10 32bit with an ATI 5450.

Out of the box, and using xrandr, things are dual head-tastic and nicely 2d accelerated.

Wishing to add 3d acceleration, I installed fglrx via apt-get, and things went well, but I had two small but important issues.

1) The mouse pointer was corrupt on the second monitor
2) Jedit (didn't try other swing apps) started to have trouble rendering the window components

The Jedit thing was the worst.  Panels would disappear until rolled over or clicked.

On reading a report of the cursor issue by someone else, it seems it is fixed in the latest catalyst drivers, so I went to ATI to install them.  After installation, there was no 2d acceleration, so scrolling and window movement was very slow and cpu intensive.

Is there a driver for 10.10 which gets around all these issues?

I couldn't see an option on the ATI site to obtain an older version, and in any case, I wouldn't know which one to choose.

I read the hardware list on the open source radeon driver pages and the HD 5450 is not listed.  I think it's quite new (and crap) but it will do for open arena.

I've gone back to the out of the box driver and xrandr for now, so it's fine, but no 3d.

Cheers,

---

### Post by jamesd256 on 2011-03-16
Anyone know about ATI drivers?

Is this even the right forum?

---

### Post by argued.logic on 2011-03-16
> **jamesd256 said:**
> Anyone know about ATI drivers?

Is this even the right forum?

Hi there, one thing you could try is using the dedicated ppa
for proprietary drivers - that solves many if not all issues for
most of us. The howto is [_HERE_]("http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/")

---

### Post by jamesd256 on 2011-03-16
> **argued.logic said:**
> Hi there, one thing you could try is using the dedicated ppa
for proprietary drivers - that solves many if not all issues for
most of us. The howto is [_HERE_]("http://www.ubuntugamer.com/2010/10/how-to-install-the-latest-proprietary-graphics-driver-in-ubuntu/")

This is exactly the information I was looking for.

As it turns out, using the PPA sorted out both issues, so thanks for taking the time to post.

---

### Post by argued.logic on 2011-03-19
> **jamesd256 said:**
> This is exactly the information I was looking for.

As it turns out, using the PPA sorted out both issues, so thanks for taking the time to post.

As always I am glad to help - now just mark the thread as solved and welcome 
back with any questions you find on the way.

---

