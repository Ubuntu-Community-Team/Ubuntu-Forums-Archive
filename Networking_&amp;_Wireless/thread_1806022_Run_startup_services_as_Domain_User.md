---
title: "Run startup services as Domain User"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by QuinRiva on 2011-07-17
I run a bunch of services (daemons) at startup as a DomainUser, however when I get the error:
```
start-stop-daemon: user 'DomainUser' not found
chown: invalid user: DomainUser
```
This is also a problem for mounting disks, as they are mounted with privileges from the DomainUser.

The DomainController is a Windows 2008 R2 machine.

Once the machine is started I can login and mount disk, run the daemons as DomainUser, but it is frustrating having to manually run everything after each reboot.

I presume that the startup scripts are started before the network, so any ideas on how to fix this?

---

### Post by QuinRiva on 2011-08-31
Bump.

---

