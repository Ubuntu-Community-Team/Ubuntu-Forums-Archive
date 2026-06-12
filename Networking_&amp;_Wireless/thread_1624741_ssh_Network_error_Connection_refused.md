---
title: "ssh: Network error: Connection refused"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by Kljuka on 2010-11-18
Hello,
I've been having quite a strange problem with my server lately. When I try to connect to my server with putty in about 3 out of 5 times putty fails with message:
> Network error: Connection refusedI've checked in /var/log/auth.log if someone was trying to break in, but no sign of that there.
I've checked with "last" command if someone indeed broke in but again: nothing.

I ran
 ```
netstat -nlp
``` to see which port sshd is listening on and got:
```
tcp6    0    0    :::22    :::*    LISTEN    31655/sshd
```Does it mean that sshd is only listening on IPv6 address? And is it possible that putty tries to connect mostly using IPv4 (and fails) and sometimes IPv6 (and succeeds)?
Do you have any other idea, what could be wrong? And how could I force sshd to listen on both tcp and tcp6?

---

