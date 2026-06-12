---
title: "Trying to get dvds to play"
date: 2013-03-06
forum: Multimedia Software
---

### Post by sarar on 2013-03-06
I'm a new Lubuntu user, and am in the process of trying to get dvds to play. I have GNOME MPlayer and Dragon Player. I downloaded libdvdread4, no luck. I tried sudo chmod 660 /dev/sr0; chgrp cdrom /dev/sr0, as many people suggested, and even with sudo I got the error message: chgrp: changing group of `/dev/sr0': Operation not permitted. I'm at a loss for what to do next.

---

### Post by SuperFreak on 2013-03-06
I had no problems with VLC (software centre)

```
sudo apt-get install lubuntu-restricted-extras
``` should add the restricted extras you need for playing DVDs

---

### Post by sarar on 2013-03-06
Success with VLC! Thank you.

---

### Post by carl4926 on 2013-03-06
You might also need to consider
[http://packages.medibuntu.org/quantal/libdvdcss2.html](http://packages.medibuntu.org/quantal/libdvdcss2.html)

---

