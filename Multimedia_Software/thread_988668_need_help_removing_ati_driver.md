---
title: "need help removing ati driver"
date: 2008-11-20
forum: Multimedia Software
---

### Post by b0b138 on 2008-11-20
I download ati-driver-installer-8-11-x86.x86_64.run to see if it would work with my card, radeon 9200. It doesn't appear to or I'm just doing something wrong. Right now I'm stuck on the mesa drivers at 800x600. How do I remove the ati driver and go back to the default driver?

---

### Post by NT4usB on 2008-11-20
afaik, you don't need to remove the old one.```
sudo dpkg-reconfigure -phigh xserver-xorg
```might get you going.
Have you tried Envy? It's in the repos*. It has options to remove stuff, as well as install.

*assuming you're running a current release of Ubuntu, since you don't say.

---

