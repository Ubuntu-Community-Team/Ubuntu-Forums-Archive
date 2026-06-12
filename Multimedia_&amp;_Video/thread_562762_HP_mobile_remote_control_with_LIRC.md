---
title: "HP mobile remote control with LIRC"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by aelmahmoudy on 2007-09-29
Hello,

  I got an HP laptop with an HP mobile remote control
(Image URL: [http://hpshopping.speedera.net/www.shopping.hp.com/shopping/images/products/el623aa_150.gif](http://hpshopping.speedera.net/www.shopping.hp.com/shopping/images/products/el623aa_150.gif)),

it is working without even installing LIRC, most of the buttons are already mapped to some keys, actually it even works when I'm still in GRUB. The problem is that a key or two are not mapped, and I want to change the mapping of a key, so I though of installing lirc & so I did. So I ran 'sudo irrecord test' to detect the remote control, and it gave me this:
irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

So, can anyone help me configure this remote control with lirc ?

---

### Post by fenx7 on 2008-02-11
I also have this problem. The remote works and I can not find lirc conf files in the home directory. I have mythfrontend installed, but wish to use the remote control and adjust some keys.

---

