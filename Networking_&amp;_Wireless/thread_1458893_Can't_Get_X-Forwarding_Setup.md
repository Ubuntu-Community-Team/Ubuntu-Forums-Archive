---
title: "Can't Get X-Forwarding Setup"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Mets on 2010-04-20
I'm trying to get X-Forwarding setup on my VPS, and I can't seem to get any programs to launch.  Whenever I call a program, I get 

```
Gtk-WARNING **: cannot open display: localhost:11.0

```

My sshd_config is setup to allow for X-forwarding.  My local box can forward programs from other boxes where X-forwarding has been known to work.

My Xwrapper.config should be ok
```
allowed_users=anybody

```

X-authority checks out just fine
```
mets@localhost:~$ ls -l .Xauthority
-rw------- 1 mets users 219 Apr 20 15:45 .Xauthority

```

Not sure what the problem might be and what else to check - any ideas?

---

