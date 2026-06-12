---
title: "sudo /etc/init.d/networking restart doesn't work?"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by ubducted on 2009-11-06
For a wired connection, my ubuntu 9.10 laptop will sometimes be turned on before I turn on my powerline ethernet adapters.  This results in the laptop not getting an IP address.  If I reboot, I will get an IP address.

Usually I do the following command but it doesn't work:

sudo /etc/init.d/networking restart  

I've also tried this other command and that doesn't work either:

sudo ifup eth0

Is there anything else I can try?

---

### Post by dvlchd3 on 2009-11-06
If the interface is up, you can attempt to request an ip address with:

```

sudo dhclient

```

---

### Post by ubducted on 2009-11-06
That does the trick nicely.  Thanks!

---

