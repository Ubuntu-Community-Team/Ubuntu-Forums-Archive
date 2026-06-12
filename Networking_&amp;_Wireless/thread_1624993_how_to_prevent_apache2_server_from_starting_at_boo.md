---
title: "how to prevent apache2 server from starting at boot"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by gweinstein on 2010-11-18
One of my ubuntu 10.04 boxes starts apache2 server automatically at boot.  I know from the output of the command:

```
sudo /etc/init.d/apache2 status
```

I can't remember even setting that up, and I don't think it does so by default, since my other box in fact does not even have apache2 server installed.  I can stop the server once I login, but is there a way to stop it from automatically starting the server, or even better, completely uninstall the daemon.  I tried

```
sudo apt-get remove apache2
```

but that does not work.  I guess the daemon is part of some bigger package.  Thanks in advance.

---

### Post by csu1 on 2010-11-18
[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

manage services - this may be what you want.

---

### Post by gweinstein on 2010-11-18
> **csu1 said:**
> [http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

manage services - this may be what you want.

Thanks!  I think that did it.

---

