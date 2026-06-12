---
title: "samba issues"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by katj12480 on 2009-06-21
I have a wired computer w/ Ubuntu Hardy Heron LTS and a laptop dual boot w/ Vista and Ubuntu Jaunty 9.0.4 w/ wifi. I also have a crossover cable that I'd prefer to use.

The problem is I can transfer to and from the Heron systems in Vista but not in Jaunty. I've been banging my head against the wall for most of the day.

Heron can see Jaunty but can't pull up any files. Jaunty can see Heron's workgroup but not Heron. Everything is fine in both directions under Vista

---

### Post by dmizer on 2009-06-22
Please see the 6th link in my sig :)

---

### Post by katj12480 on 2009-06-23
I read both of the links re samba and made appropriate changes w no change. again, i'm not trying to connect to windows, i'm trying to connect from jaunty to heron. heron is clearly properly configured since it can communicate happily w/ vista. i changed my smb.conf file, made sure the firewall was disabled, installed winbind...

i really just want linux to talk to linux via any file transfer means

---

### Post by dmizer on 2009-06-23
> **katj12480 said:**
> i really just want linux to talk to linux via any file transfer means
Then use NFS instead. It's far less complicated to configure and works better than samba. There's a nice howto in the 4th link in my sig.

---

### Post by katj12480 on 2009-06-24
Thanks for helping! I am now able to transfer files.

---

