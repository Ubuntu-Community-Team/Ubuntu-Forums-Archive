---
title: "quick question about port 80 and 443"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by sid0972 on 2012-08-13
is it possible that if ports 80 and 443 are being used by skype under ubuntu, and are locked for other apps, they are locked under windows 7 too?

---

### Post by Lars Noodén on 2012-08-13
Ports lower than 1024 need root to be accessed, so Skype is not going to be able to use either port on your machine.  You can double check with [netstat](http://manpages.ubuntu.com/manpages/precise/en/man8/netstat.8.html).

```

netstat -ntp

```

Check the columns labeled 'Local Address' and 'PID/Program name'

---

### Post by sid0972 on 2012-08-14
thanks for the answer, but i solved my problem now

---

