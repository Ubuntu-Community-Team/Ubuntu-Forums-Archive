---
title: "network not working"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by Kit46 on 2009-08-10
I can no longer access the internet via network connection.   It worked fine this morning but when I logged onto my computer (dell mini 9 ) this afternoon the network connection icon was gone from my panel and when i went into the systems-admin-newtwork settings I could not access wireless, wired, or point to point connection.  I unlocked it and still nothing.  Anyone know why this could've happened.  Thank you .

---

### Post by Iowan on 2009-08-10
Check **ifconfig -a** to see if an interface has an IP address. Lacking that, check **lshw -C network** to see if interfaces are recognized.

---

### Post by Kit46 on 2009-08-11
thank you very much Iowan .  I will try that.

---

### Post by Kit46 on 2009-08-22
Still could not connect so I  click on the network manager and nothing comes up.  Seems not to be installed anymore.  I went into apps and it seems to be installed but nothing happens...

---

