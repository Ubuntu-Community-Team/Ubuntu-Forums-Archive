---
title: "No sound effects"
date: 2009-01-18
forum: Multimedia Software
---

### Post by Pidgin on 2009-01-18
See my sound preferences in the attachment. It is all default settings. But my system never produces any sound effects except [COLOR="Blue"]Login[/COLOR].
8.10.
Thank you!

---

### Post by phanyx on 2009-02-07
Hi,

I had the same problem as you and I have solved it by following steps listed in this site: [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

To be short, all you have to do is:

1. add new repository address: deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main
2. sudo aptitude update
3. sudo aptitude safe-upgrade
4. reboot
5. should work by now.

In this particular case, problem is caused by outdated libcanberra 0.6 in ubuntu 8.10 repository. All you have to do is update it to the latest version. Gert Kulyk gently uploaded all necessary files to his repository, for ease of this operation.

---

