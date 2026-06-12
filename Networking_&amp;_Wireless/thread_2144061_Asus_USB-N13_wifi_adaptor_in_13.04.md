---
title: "Asus USB-N13 wifi adaptor in 13.04"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by meldroc on 2013-05-11
The only way I can get it working at all is if I downgrade to an older kernel (I have a copy of 3.5.0 from 12.10.)

But now if I use an older kernel, I can't get the Nvidia drivers working. So I have to pick between having working 3-D acceleration, and having Internet.

This is incredibly frustrating. Is there any way to get in touch with a kernel developer who knows how to dig under the hood and figure out what broke? I would really just like to get the N13 working with the stock kernel, so I don't have to stumble around with half-working hacks!

Please help!

---

### Post by mörgæs on 2013-05-11
Have you reported the bug in Launchpad?

---

### Post by praseodym on 2013-05-11
Obviously, you should try an earlier version of the NVIDIA-driver for the downgraded kernel.

[http://packages.ubuntu.com/quantal-updates/nvidia-current](http://packages.ubuntu.com/quantal-updates/nvidia-current)

from 12.10

---

