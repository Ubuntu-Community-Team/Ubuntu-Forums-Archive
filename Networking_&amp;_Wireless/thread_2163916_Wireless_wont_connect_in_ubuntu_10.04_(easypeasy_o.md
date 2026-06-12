---
title: "Wireless wont connect in ubuntu 10.04 (easypeasy os)"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by itsmedomp on 2013-07-20
I'm not sure if this is the right place to post this but I hope someone can help me out! :)
Here is a link to my video explaining my problem [http://www.youtube.com/watch?v=sbhyrcXvlYQ](http://www.youtube.com/watch?v=sbhyrcXvlYQ) I'd thought I would make a video because its easier to explain the problem. I would be very grateful if anyone could help me out, thanks! Also I don't have any access to a windows computer just to let you know.

---

### Post by praseodym on 2013-07-20
Hi,

please open a terminal and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
lsmod
```

---

