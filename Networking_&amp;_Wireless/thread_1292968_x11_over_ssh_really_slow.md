---
title: "x11 over ssh really slow"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by pavel989 on 2009-10-16
i set up my ssh server to forward X11, and now ssh is noticably slower, and X11 is so slow, its almost unresponsive.

i have done the usedns no, turned off the gasspi (or w.e) auth, and checked xauth. i connect using dyndns, not my ip.

any ideas?

---

### Post by scorp123 on 2009-10-16
You can squeeze out more speed by enabling compression and by using a faster algorithm. I personally like to use "blowfish" ... it's still secure, but a slight bit faster than the defaults.

Please read here:
[http://www.erlewein.net/2008/faster-ssh-by-using-blowfish/](http://www.erlewein.net/2008/faster-ssh-by-using-blowfish/)

---

