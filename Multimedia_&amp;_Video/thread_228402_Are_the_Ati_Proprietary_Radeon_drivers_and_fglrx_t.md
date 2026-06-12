---
title: "Are the Ati Proprietary Radeon drivers and fglrx the same thing?"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by thomas.hood on 2006-08-03
Confused...

Tom

---

### Post by 23meg on 2006-08-03
[http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)

---

### Post by whatever on 2006-08-03
yes

---

### Post by thomas.hood on 2006-08-03
...but after installing fglrx, my flgrxinfo says 8.26.18 whereas reading the ATI site suggests I should be getting 8.27.10. 

What is the update schedule for these and is there an advantage in using the installer versus the fglrx debs?

Thanks,

Tom

---

### Post by Dubbayoo on 2006-08-03
8.27.10 isn't in the repositories yet. You can install it manually.

---

### Post by gmcauley on 2006-08-03
Try adding this ```
# Seveas' packages (packages, GPG key: 1135D466)
deb http://mirror.ubuntulinux.nl dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror3.ubuntulinux.nl dapper-seveas all

``` to /etc/apt/sources.list

Then you can install 8.27.10 via apt.

See [http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/) for more info.

---

### Post by thomas.hood on 2006-08-04
Thanks!

---

