---
title: "Slow apt D/L Speeds"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by DMonkey08 on 2008-12-16
I just installed Hardy on my computer (I was having problems with Intrepid) and noticed that apt download times are really slow - about a 20th of download times with firefox.  It's really getting on my nerves - can anyone help?

---

### Post by chrisamiller on 2008-12-16
Try using a different d/l mirror, preferably one close to your location.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bck
sudo gedit /etc/apt/sources.list
```

use find and replace to make the changes. So if I wanted to use the University of Utah mirror, I'd change this line:

```
deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
```

to this line:
```
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid main restricted
```

Make the same change throughout your file.

A list of mirrors can be found here:
[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

---

### Post by DMonkey08 on 2008-12-16
Thanks for answering my noobish question.  It's running waaaay faster!

---

