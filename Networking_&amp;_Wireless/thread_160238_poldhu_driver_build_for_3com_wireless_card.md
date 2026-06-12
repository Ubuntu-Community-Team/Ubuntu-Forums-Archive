---
title: "poldhu driver build for 3com wireless card"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by dasratsel on 2006-04-14
hi:
i have a 3com 3CRWE62092A PCMCIA wireless card. i found that the driver i need is called "poldhu" which i could only find online as source. (i found poldhu-0.3.1 and 0.3.2jserv). however, when i follow the instructions (apt get linux-source and pcmcia-cs source) i get the following build output:

```
set -e ; for d in clients config  ; do make -C $d ; done
make[1]: Entering directory `/usr/src/poldhu_j/clients'
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/poldhu_j/clients modules
make[2]: Entering directory `/lib/modules/2.6.12-10-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.12-10-386/build'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/poldhu_j/clients'
make: *** [all] Error 2
```

did i untar my kernel sources incorrectly, or do i need some other source package or something of that sort?

~Xavier

---

### Post by Canman on 2006-04-21
Hi,

I have the same wifi card and I can´t for my life get it to work.
I hope that some one as a solution for this.

The device manager identifies the card but it wont show up in the network admin thingie.

I have tried to install the poldhu driver with similar result as the original post.

So if there is some person out there that has a solution to this problem I would appreciate it.

Best regards
/Canman

---

