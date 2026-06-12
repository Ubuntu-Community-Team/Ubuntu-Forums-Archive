---
title: "Lirc help"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by kb3hkg on 2007-03-01
I have a Dell Inspiron 9100 running Edgy. This has a built in IR port in the front. I would like to get Lirc up and running but I cannot get it configured.

First step I need help with is figuring out what driver I will need with this port, can someone please help me?

---

### Post by barney_1 on 2007-03-03
This post: 

[http://readlist.com/lists/linux-mandrake.com/expert/4/23936.html](http://readlist.com/lists/linux-mandrake.com/expert/4/23936.html)

Suggests that you might be trying to run LIRC with the wrong com port.  Try different ports and see if you have any luck.

---

### Post by kb3hkg on 2007-03-03
I checked and I have mine set to com 3, when I try runninf irrecord I get the following, am I missing something here?

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not init hardware (lircd running ? --> close it, check permissions)

---

