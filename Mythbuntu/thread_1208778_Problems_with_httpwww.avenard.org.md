---
title: "Problems with http://www.avenard.org"
date: 2009-07-09
forum: Mythbuntu
---

### Post by ian dobson on 2009-07-09
Hi,

I'm running the VDPAU backports from [http://www.avenard.org](http://www.avenard.org) on my frontend and for the last week of so apt-get update hangs with:-

```

OK   http://ch.archive.ubuntu.com intrepid-security/multiverse Sources
Ign http://www.avenard.org release/ Packages
Hole:1 http://www.avenard.org release/ Packages
96% [1 Packages gzip 0]

```

Looking at the releases directory I can see that the file Packages.gz is 0 bytes in size.

Anyone got an idea whats going on?

Regards
Ian Dobson

---

### Post by crez79 on 2009-07-09
Everything works for me on jaunty. Updated on july 4th. Have you tried to use aptitude or synaptic?

---

### Post by ian dobson on 2009-07-10
Hi,

Update manager also hangs on file 53 of 53 and the repositries on [www.avenard.org](www.avenard.org) are marked as fail.

If your not using the VDPAU backports -release this might not affect you.

Regards
Ian Dobson

---

### Post by crez79 on 2009-07-10
I am using ```
deb http://www.avenard.org/files/ubuntu-repos jaunty release
``` for the VDPAU  backports. 

According to his blog, this is probably his last update because he is moving to trunk.

---

### Post by ian dobson on 2009-07-10
Hi,

OK, I fscked root and reran apt-get update, upgrade and it seems to be working.

Thaks for the info about him going over to trunk. I'll stay on fixes for as long as I can (Maybe 9.10).

Regards
Ian Dobson

---

