---
title: "Gathering info on ssh connections"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by ooobooontooo on 2009-05-29
Hi,

How do I find out where ssh requests are coming from? Is there a log that keeps track of this? Thanks in advance.

---

### Post by puppywhacker on 2009-05-29
sshd doesn't log by default, you can enable logging to syslog in the configuration file. The list of users that are logged in to a terminal can be shown by "last"

---

### Post by ooobooontooo on 2009-05-29
> **puppywhacker said:**
> sshd doesn't log by default, you can enable logging to syslog in the configuration file. The list of users that are logged in to a terminal can be shown by "last"

Thanks a lot. The "last" command was exactly what I needed.

---

