---
title: "Gnomad2 for Creative Zen X-Fi"
date: 2011-04-18
forum: Multimedia Software
---

### Post by 1234blizzard on 2011-04-18
Hi, I installed gnomad2 on my ubuntu 10.10 system but it won't mount my Creative Zen X-Fi. Ubuntu itself recognizes it but Gnomad2 doesn't. The error message is this...

Device 0 (VID=041e and PID=4162) is a Creative ZEN X-Fi.
PTP_ERROR_IO: Trying again after re-initializing USB interface
Queried Creative ZEN X-Fi
Segmentation fault

Thanks in advance!!

---

### Post by IamI'mMe on 2011-04-30
Hi 1234blizzard,

For some reason Ubuntu decided to "not support gnomad2" (in "" because you can still use it in Ubuntu).

The problem is not gnomad2 or ubuntu 10.10, not even ubuntu natty narwahl. It is a library called: libtmp8, that handles the data exchange between Ubuntu and you Creative ZEN X-Fi. The biggest problem is the right configuration between libmtp8, gnomad2 and Ubuntu.

I use the following configuration:
- libmtp8: libmtp8_0.3.7-3ubuntu2_i386.deb
- gnomad2: gnomad2_2.9.4-0ubuntu1_i386.deb

The release of Ubuntu is not relevant if you do the following each time you upgrade to a new release of Ubuntu, or if the version of libmtp8 is overwritten because of an update.

Steps to follow:
- open synaptic
- search for: libmtp8
- mark libtmp8 for complete removal and remove it
- close synaptic
- install: libmtp8_0.3.7-3ubuntu2_i386.deb using GDebi
- open synaptic
- search for: libmtp8 again and lock this version so it can not be updated
- close synaptic
- install: gnomad2_2.9.4-0ubuntu1_i386.deb using GDebi
- connect your ZEN: it will be automatically mounted in Ubuntu 10.10
- unmount you ZEN
- open gnomad2........:guitar:

If for some reason gnomad2 is not working correctly always check the version of libtmp8 and repeat the steps above.

Sources:
libtmp8: [http://archive.ubuntu.com/ubuntu/pool/main/libm/libmtp/](http://archive.ubuntu.com/ubuntu/pool/main/libm/libmtp/)
gnomad2: [http://archive.ubuntu.com/ubuntu/pool/universe/g/gnomad2/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnomad2/)

Cheers!

---

### Post by 1234blizzard on 2011-04-30
Thank you so much! It worked like a charm.

---

