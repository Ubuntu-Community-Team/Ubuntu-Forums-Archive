---
title: "Wireshark packet capture?"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by II Luis II on 2010-08-08
Well when I go to capture>interfaces I get this:

[IMG]http://i33.tinypic.com/1zn8xw4.jpg[/IMG]

Well how do I get it to show all the routers and what ever? also I think I need packet socket enable how can I get wireshark working and how can I get packet capturing


Thanks

---

### Post by Kudak on 2010-08-08
Hey,

you have to be in root to see the NIC interfaces.

---

### Post by II Luis II on 2010-08-08
sorry but that means nothing to me, could you explain>?

---

### Post by Kudak on 2010-08-10
you need to run wireshark as root which means:

sudo wireshark &

---

### Post by pat_bateman on 2010-08-10
or press ALT+F2 and type:
```
gksudo wireshark
```

-Pat

---

### Post by TAcadia on 2011-08-03
Thanks this really helped :)

---

### Post by wildmanne39 on 2013-04-24
Thread closed. Please do not post in old threads.

---

