---
title: "Problems starting SSH..."
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-02-05
So lately I've been having a lot of SSH problems, but I seen a thread very similar to this on another Linux forum, and I'm having the same problem, for some odd reason SSH is not starting, so I keep getting this error:```
ssh: connect to host localhost port 22: Connection refused
```
So I try to check the status of the SSH connection by running the following command:
```
/etc/init.d/sshd status
```
When I run that, these are the results I get:
```
status: stopped
```
So then obviously I try to start SSH up again, and I get the following:
```
/etc/init.d/sshd start
Bringing eth0 up...
Failed to bring eth0 up
```
Not really sure what it could be, I'm kind of stumped on this, any ideas. Thanks!

---

