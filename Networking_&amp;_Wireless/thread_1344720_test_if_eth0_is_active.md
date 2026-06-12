---
title: "test if eth0 is active"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by sanderd17 on 2009-12-03
Is there a way to test if the eth0 connection is active? I would like to use this in a script.

I know it's possible to do with 
```

$ ethtool eth0 | grep Link

```
But I don't like this command because it has to be executed as super user. And I want my script to be executed as a normal user.

---

### Post by memilanuk on 2009-12-03
'ifconfig eth0' ?

Though you might want configure your script to check that it has an IP address assigned to it as well that it exists.

---

### Post by hal10000 on 2009-12-03
To check if it has an ip-address, use:
```
 ifconfig eth0 | grep -i 'inet address'
```

---

### Post by sanderd17 on 2010-01-15
Thanks, could now make a script to autologin on the internet via a web page (together with greasemonkey)

---

