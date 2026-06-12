---
title: "smbfs hangs shutdown, workaround?"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by fhsm on 2010-03-15
I have a couple of NASs that I mount manually with smbfs. That works. The problem is if I don't go through and explicitly unmount them prior to shut down the system hangs for a while. It looks like [this is a long standing bug]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/197346").

What I'd like is to have the system automagically mount the NAS on the network I'm currently on (NASs at home vs NAS at work) and then shutdown without hanging with no special effort on my part.

Can anyone suggest a way to accomplish this?

---

### Post by dmizer on 2010-03-15
There are some ideas for fixing it, as well as links to discussion threads, located in the troubleshooting section of the cifs howto in my sig (2nd link).

Here is a link to the current, and active, bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/211631/](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/211631/)

---

### Post by fhsm on 2010-03-16
Thanks for the reply.  I tried: ```

ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
```


Now the system just hangs without error at shutdown. How can I undo this change to try another solution?

Thanks.

---

### Post by dmizer on 2010-03-16
I have two fixes for the CIFS error on shutdown, try the second one as well (located under "******Jaunty USERS******"). If that does not fix your problem then you can remove the above edit by running this command:
```
sudo rm /etc/rc0.d/K15umountnfs.sh
sudo rm /etc/rc6.d/K15umountnfs.sh
```

---

