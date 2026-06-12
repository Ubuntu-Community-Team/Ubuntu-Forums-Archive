---
title: "solving your 11.10 networking problems"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by kforum on 2011-12-25
My scenario was that after heavy load, networkmanager would just DC and all sorts of other weirdness were going on, tried everything... till i found that all of this had to do with mr.Crappy O'kernel 3.x, and the old one worked just fine, no hangs.

So here is what we'll do:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/)
Go there and download Linux header_all, header_yourArch, and image_yourArch.
And install them in that order.

After that all you got to do is select the appropriate kernel(2.6.x) at boot, or edit grub to favor it.
If you choose to edit grub files, check here:
[http://ubuntuforums.org/showthread.php?t=1305116](http://ubuntuforums.org/showthread.php?t=1305116)
should still work i guess, i simply select the old kernel at boot.

Good luck to all, hope this solves your nightmares too.

Cheers!

---

