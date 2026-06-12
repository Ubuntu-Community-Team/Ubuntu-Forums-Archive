---
title: "Wireless WNDA3100"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by Tadikin on 2012-10-25
To start I would like to thank you for reading My post and hope you can help.
I have been working on trying to get my Netgear WNDA3100 wireless adapter to work with Ubuntu 12.10. I installed ndiswrapper from the Ubuntu software center. I installed the BCMWLHIGH6.inf and it gave me this Error message:

```
Module could not be loaded. Error:
Fatal: Module ndiswrapper not found.
is the ndiswrapper module installed?
```I clicked ok it appeared in the list. it showed the hardware was present but didn't do anything else. 

I apologize if I sound uninformed and I hope you can help.
Thank you in advance.

---

### Post by chili555 on 2012-10-26
Please run and post the result of these terminal commands:```
sudo modprobe ndiswrapper
ndiswrapper -l
arch
lsusb
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by NIMDog on 2013-04-15
I am having the exact same problem! This is what I get when I run the code: [COLOR=#000000][/COLOR]FATAL: Module ndiswrapper not found.
I then went to the software center to get ndiswrapper, and it said it was installed!!

---

### Post by gorkypah on 2013-04-15
...

---

### Post by gorkypah on 2013-04-15
Also try installing ndisgtk (sudo apt-get install ndisgtk).  Its a great graphical front-end to managing your ndiswrapper drivers.

---

### Post by NIMDog on 2013-04-15
The Wireless Network Driver thing recognizes that the hardware is there, but I am still getting the exact same window with this text in it:

Module could not be loaded. Error was:


FATAL: Module ndiswrapper not found.


Is the ndiswrapper module installed?

---

### Post by gorkypah on 2013-04-15
...

---

### Post by NIMDog on 2013-05-13
I ended up ditching that wireless adaptor and going with another one that works great. That is one thing I don't like about Ubuntu, it is not that great for people who know what they want to do, but aren't sure how to do it!

---

