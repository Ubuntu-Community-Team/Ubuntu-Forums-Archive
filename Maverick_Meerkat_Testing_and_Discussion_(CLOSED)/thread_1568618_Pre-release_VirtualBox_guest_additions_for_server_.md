---
title: "Pre-release VirtualBox guest additions for server 1.9"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-09-05
According to here: [http://www.virtualbox.org/ticket/5266#comment:83](http://www.virtualbox.org/ticket/5266#comment:83)

There is a pre-release guest additions iso that provides compatibility with xserver 1.9, which is nice. It's an iso, so mount and install as per normal.

[http://www.virtualbox.org/download/testcase/VBoxGuestAdditions-r65518.iso](http://www.virtualbox.org/download/testcase/VBoxGuestAdditions-r65518.iso)

Downloading to test now...

---

### Post by jfernyhough on 2010-09-05
That does the job. Just watch out for a jazzy screen when installing; a quick HOST+F1, HOST+DEL to switch out of X then reboot sorts it out.

---

### Post by cariboo on 2010-09-05
Thanks for that, it works as expected.

---

### Post by stmiller on 2010-09-05
Or just install this package, and reboot.

```
virtualbox-ose-guest-x11
```

:)

---

### Post by cariboo on 2010-09-05
I tried that on a different system, it didn't work, resolution was still stuck at 800X600, with the pre-release guest addition I'm able to change the resolution.

---

### Post by heavyt on 2010-09-07
Thanks works like a charm. :D

---

### Post by Daimoneze on 2010-10-08
> **jfernyhough said:**
> According to here: [http://www.virtualbox.org/ticket/5266#comment:83](http://www.virtualbox.org/ticket/5266#comment:83)

There is a pre-release guest additions iso that provides compatibility with xserver 1.9, which is nice. It's an iso, so mount and install as per normal.

[http://www.virtualbox.org/download/testcase/VBoxGuestAdditions-r65518.iso](http://www.virtualbox.org/download/testcase/VBoxGuestAdditions-r65518.iso)

Downloading to test now...

Did they kill this? I 404'ed. Any mirrors?

---

### Post by jfernyhough on 2010-10-08
Look like it's been removed. This could mean that the next release is imminent - which would be better!

---

### Post by xebian on 2010-10-08
There was a new release on 10/3 for maverick debs 3.2.8 but GA still a problem.  However, the pre-release GA.iso seems to work better with it.

---

