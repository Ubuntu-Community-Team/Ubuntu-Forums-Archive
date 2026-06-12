---
title: "smbd strange behavior"
date: 2010-08-16
forum: Networking &amp; Wireless
---

### Post by bilkay on 2010-08-16
Here's what I get when I invoke
```
$ sudo service smbd stop
stop: Unknown instance:
``` or ```
$ sudo service smbd restart
restart: Unknown instance:
```There's more:
```
$ sudo service smbd start
smbd start/running, process 11417

$ sudo service smbd status
smbd stop/waiting
```The status is always the same (stop/waiting) no matter what I do!

Incidentally, ubuntu 10.04 is installed on both a laptop and a desktop, but the above behavior is peculiar to the desktop.

---

