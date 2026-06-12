---
title: "Standard query A eth0 ... What is it?"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by sefs on 2010-01-30
I was looking monitoring my connection and my computer continuously sends out DNS request of

```
Standard query A eth0
```

to which the router responds

```
Standard query response, No such name
```

Why is it doing this?  Is it normal?

Thanks.

---

### Post by sefs on 2010-02-03
It turns out that this is Samba.

samba.conf was bound to eth0 only, but i have no eth0 interface. So it constantly queries it from the dns.

My interface is wlan0.  I do not want samba on this interface all the time only sometimes.  Is there a way to set samba so it is not attached to any interface and is in a "disabled" state? 

Where it will not be sending useless dns queries for a non-existent interface?

Thanks.

---

### Post by sefs on 2010-02-05
setting ...

```

    interfaces = lo
    bind interfaces only = yes

```

... is what I was essentially looking for to "disable" the samba machine from the network.

---

