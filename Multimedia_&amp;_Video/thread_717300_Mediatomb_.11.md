---
title: "Mediatomb .11"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by Reducer on 2008-03-06
I see that MediaTomb .11 is available now from the MediaTomb repo.  I'm dying to get transcoding working, but it looks like there are some dependencies that that aren't filled by Ubuntu:

```
mediatomb-common:

Depends: libavcodec0d (>=0.cvs20050823) but it is not installable
Depends: libavformat0d (>=0.cvs20050823) but it is not installable
```

Anyone know if there is a repo somewhere where I could get my hands on these?

---

### Post by tgilber1 on 2008-03-07
In the  /etc/apt/sources.list file, check the following line

deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) _gutsy_ main

Make sure that the right Ubuntu version is populated.  I had the same error as you report because this line was set to feisty.  

Lastly, Also, update the GPG key following the instructions from the URL below

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


As soon as I changed the line in the sources.list file to gutsy and updated the GPG, the problem ceased.

---

### Post by Reducer on 2008-03-07
Thank you VERY much.  That worked great.

---

### Post by msubzwari on 2008-03-07
Thanks for this very useful tip.
Mediatomb site has the wrong info in gutsy section....it is still showing:
deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) **feisty** main

---

### Post by WookieBrew on 2008-06-08
I tried to do the install/update but got the following from my "sudo apt-get update" command:

Failed to fetch [http://apt.mediatomb.cc/dists/gusty/main/binary-i386/Packages.gz](http://apt.mediatomb.cc/dists/gusty/main/binary-i386/Packages.gz)  404 Not Found

Any ideas?

---

