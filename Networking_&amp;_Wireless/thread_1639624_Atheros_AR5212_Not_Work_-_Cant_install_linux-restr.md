---
title: "Atheros AR5212 Not Work - Cant install linux-restricted-modules"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by Finnius on 2010-12-06
Hello,

I am trying to get my laptop on-board wireless card working, and from browsing the web it looks like i should install the linux-restricted-modules...

I am using Lucid with an Atheros AR5212 chipset.

However it says the package cant be found:
```
~$ sudo apt-get install linux-restricted-modules-2.6.32-21-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.32-21-generic

```I have the restricted repositories enabled and all the update repositories.
Is the restricted modules still available for Lucid?

Also, is 'linux-restricted-modules' even the right package i need to get the wireless working as it does not show up in iwconfig nor does any of its LEDs come on when i switch the switch?

Any ideas?
Thanks

---

### Post by Finnius on 2010-12-07
*bump*
I really need to get the on board wireless working.

---

### Post by walt.smith1960 on 2010-12-07
Try enabling backports?  Sometimes that helps, sometimes not.

---

