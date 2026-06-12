---
title: "Linksys wireless usb adapter driver wusb600n"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by DeMartini on 2011-01-30
Has anyone any idea how to get this adapter to work, thanks in advance

Linksys WUSB600N dual band ver.2 

running ubuntu ver. 10.10

---

### Post by bkratz on 2011-01-30
> **DeMartini said:**
> Has anyone any idea how to get this adapter to work, thanks in advance

Linksys WUSB600N dual band ver.2 

running ubuntu ver. 10.10



See if this version 2 document applies to you

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N](https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N)

---

### Post by ihc100 on 2011-01-30
I have been struggling with this today.

The tutorial is o.k. but for 10.10 you have to change two lines, otherwise it will not compile.

In /os/linux/...
usb_buffer_alloc  into usb_alloc_c...
usb_buffer_free   into usb_free_c....

Don't know it out of the head anymore.
There is another post on the forum.
I tried the now available rt3572 5.0.0 did not work for me.
an older one (3.0.0) worked very nice.

---

