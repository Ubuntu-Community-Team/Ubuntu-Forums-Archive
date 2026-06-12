---
title: "IPTables unknown option '--dport'"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by Ryutatsu on 2012-02-10
Title pretty much says it all. I try the line:

```
sudo iptables -I INPUT 1 --dport 80 -j ACCEPT
```

and get the error listed in the title.

EDIT: Fixed. I forgot that you have to list a protocol in order to use port. Changing line to:

```
sudo iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT
```

worked

---

