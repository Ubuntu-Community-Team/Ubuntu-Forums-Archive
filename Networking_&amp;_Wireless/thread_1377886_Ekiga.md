---
title: "Ekiga"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by kievking on 2010-01-10
I received this error message while after I reinstalled ekiga:

"error while starting the listener for the H.323 protocol" "You will not be able to receive incoming H.323 calls Please check that no other program is running on the port used by Ekiga"

How do I check that no other program is running on the same port?

Thanks

---

### Post by changingstate on 2010-01-11
A list of the ports ekiga uses is available here : [http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga](http://wiki.ekiga.org/index.php/Internet_ports_used_by_Ekiga)

To show which ports which programs are using which ports, for tcp use :

```
sudo lsof | grep TCP
```For udp use :

```
sudo lsof | grep UDP
```

---

