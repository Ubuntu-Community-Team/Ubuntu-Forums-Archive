---
title: "No internet connection"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by garyscott on 2012-08-15
I have lost all internet connections, wired and wireless.  Tried to reinstall a driver but get the following message:   W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb)
Size mismatch

I am not sure what version ubuntu I am using....(where to find?)

Any help?

---

### Post by wildmanne39 on 2012-08-16
*Thread moved to **Networking & Wireless**.*

---

### Post by rukiaEnix on 2012-08-16
You won't be able to install that driver because you need Internet, you will have to download it with other computer and then install it.

How to find Ubuntu version, type this command:

```

lsb_release -a

```

Also look for something about network in the logs, look at /var/log/messages or /var/log/syslog

---

