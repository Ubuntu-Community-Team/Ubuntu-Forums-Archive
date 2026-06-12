---
title: "Calibre problem after update 11.10"
date: 2011-10-24
forum: Multimedia Software
---

### Post by trinacriax on 2011-10-24
Hi, 
yesterday I had a 10.04 that worked very well, but I decided to upgrade my system to 11.10.
Actually, it's very nice, very OsX oriented, however my problem is that calibre doest not work.
I run it, but whenever I change the active window (alt+tab) segmentation fault occurs.
First I thought it was due to some library: update+upgrade
then I installed calibre from source...but again segmentation fault.

do you have any glue?

Cheers!

PS. If I run as root, it works and ALT button doesn't affect it

---

### Post by ergo-proxy on 2011-10-25
Try to reinstall it:
 
sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"

---

### Post by trinacriax on 2011-10-26
thx it works.

---

