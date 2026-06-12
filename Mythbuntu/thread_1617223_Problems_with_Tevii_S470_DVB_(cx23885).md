---
title: "Problems with Tevii S470 DVB (cx23885)"
date: 2010-11-09
forum: Mythbuntu
---

### Post by Brandoo_NZ on 2010-11-09
I've now been using Mythbuntu coming up a year.

I've got a Tevii S470 PCIe DVB card.

With 9.10 and 10.04 it worked fine. I had to compile the kernel module from source (tevii_ds3000.tar.gz) and it worked well.

I decided to try out the 10.10 beta and after a fresh Ubuntu install (installing Mythbuntu via apt-get) everything worked out of the box... no need to compile drivers.

When 10.10 was released I used update manager to install everything - and the tuner stopped working.

I've since reinstalled Mythbuntu 10.10 and again, it's not working.

The device is found and can be configured - but when I try and tune channels via the backend, I get nothing - just No Lock (even though signal is around 80%).

The driver above wont compile and I've also tried using s2-liplianin-351-e2aad25623b9 but this doesn't work either.

Anyone seen this/have any suggestions?

Thanks!

---

### Post by gilson585 on 2010-11-16
It's probably the same issue lots of us are having, look here [http://ubuntuforums.org/showthread.php?t=1593695](http://ubuntuforums.org/showthread.php?t=1593695)

---

