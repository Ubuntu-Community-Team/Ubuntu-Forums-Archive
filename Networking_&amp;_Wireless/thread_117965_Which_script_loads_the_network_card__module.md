---
title: "Which script loads the network card  module?"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by wildwestwind on 2006-01-15
Hello everybody!

My problem's really simple I need to pass a parameter to my ethernet card module (8139too), and I'd like to do this in a proper way. The quick 'n' dirty option of doind a rmmod && modprobe after the boot works fine but I'd like to make it automatical. 
Could someone tell me where the module is initially loaded during bootstrap ?

Thank you in advance!

---

### Post by trancephorm on 2006-01-17
I'm very interested too... besides, i have another problem: ...

root@mm:/home/pyc# rmmod bttv
ERROR: Module bttv is in use by bt878
root@mm:/home/pyc# rmmod -f bttv
ERROR: Removing 'bttv': Resource temporarily unavailable

It's in ubuntu 5.1, with 5.04 everything was okay, I was able to remove module and load it again...

---

