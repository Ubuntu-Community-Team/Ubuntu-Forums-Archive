---
title: "SSH Local connection rejected"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by rowbird on 2010-09-22
Hi all, I am having trouble with my local ssh connection. In my hosts.deny I have ALL, and in my hosts.allow I have my computer. I cannot connect unless I comment out the ALL in hosts.deny. Why is it not allowing a connection? Thanks in advance.

---

### Post by Brandon Williams on 2010-09-22
With this hosts.allow:
```
sshd: my.allowed.host
```
And this hosts.deny:
```
ALL: *
```
I can connect from my.allowed.host via ssh and cannot connect from any other remote system or to any other service. Does this look similar to what you've got now?

---

