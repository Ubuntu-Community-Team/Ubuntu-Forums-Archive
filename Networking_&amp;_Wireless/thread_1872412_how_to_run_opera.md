---
title: "how to run opera?"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by Matrix01 on 2011-10-30
downloaded opera,
how do u run it?

---

### Post by tartalo on 2011-10-30
[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by Matrix01 on 2011-10-30
i am not sure where to start.
can i get help?

> **tartalo said:**
> [https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

---

### Post by tartalo on 2011-10-31
In the link I gave you the recommendation is to install it from Opera's official repository, they link to this documentation in Opera's site:
[http://deb.opera.com/](http://deb.opera.com/)

There they explain you what to add to your sources.list file, but if that's difficult for you they also mention that it will be automatically added the first time you install Opera for Ubuntu, therefore the easiest way is to download Opera for ubuntu form here (default package, not tar.gz not tar.bz2):
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

So you will download a file called opera_blah_blah_whatever.deb

To install this .deb file you can double click it, Ubuntu software center will open automatically and offer you to install it.

If that doesn't work open a terminal, go to the folder where your opera_xxx.deb file is and type:```
dpkg -i opera_blah_blah_whatever.deb
```

---

