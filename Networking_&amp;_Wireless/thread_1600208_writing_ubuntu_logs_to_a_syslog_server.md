---
title: "writing ubuntu logs to a syslog server?"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by badger_fruit on 2010-10-18
how does one configure a Ubuntu 10.4 machine to write its logs to a syslog server?
thank you in advance for any replies!!

---

### Post by SeijiSensei on 2010-10-18
Edit /etc/rsyslog.d/50-default.conf and replace the appropriate filenames with @servername.  See [http://linux.die.net/man/5/syslog.conf](http://linux.die.net/man/5/syslog.conf) for details.

---

