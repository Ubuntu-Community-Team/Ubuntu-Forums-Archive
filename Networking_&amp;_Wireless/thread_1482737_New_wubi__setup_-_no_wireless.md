---
title: "New wubi  setup - no wireless"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by itsmoss on 2010-05-13
I am completely new to ubuntu. i dowloaded ubuntu 10.04 with the wubi installer. i do not have a disc. ndiswrapper and ndisgtk are foreign language to me. could anyone do me a great favor and walk me through the process of getting wireless internet to work with my dell inspiron laptop?

---

### Post by Iowan on 2010-05-13
Moved to it's own thread.

From a terminal (Applications>Accessories>Terminal) check ```
ifconfig -a
``` and ```
sudo lshw -C network
``` Post results (if possible) - more information if you need it.

---

