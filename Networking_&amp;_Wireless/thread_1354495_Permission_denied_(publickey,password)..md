---
title: "Permission denied (publickey,password)."
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by laeg_ on 2009-12-13
I've configured an openssh-server and created the RSA keys before using:
```

ssh-copy-id laeg@host 
chmod 644 .ssh/authorized_keys

```

but whenever I attempt to connect I receive the error:

> Permission denied (publickey).

I then tried:

```
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

This made no difference, how can I remedy this?

---

### Post by laeg_ on 2009-12-14
bump

---

### Post by jobix on 2009-12-14
If changing permissions didn't help, then maybe that's not the issue? Did you copy the key into the authorized_keys file? 

Try running ssh with the -v option. That should give you more information about what's happening.

> ssh -v your_machine

---

### Post by laeg_ on 2009-12-16
> **jobix said:**
> If changing permissions didn't help, then maybe that's not the issue? Did you copy the key into the authorized_keys file? 

Try running ssh with the -v option. That should give you more information about what's happening.

Thanks for the input. 

SOLVED ==>> Someone in #ssh on freenode had me:

```
ls -ld ~ ~/.ssh ~/.ssh/*
```

After pastebining the output they reported the permissions were incorrect and had me then:

```
chmod 600 ~/.ssh/*
```

It now accepts the key.

---

