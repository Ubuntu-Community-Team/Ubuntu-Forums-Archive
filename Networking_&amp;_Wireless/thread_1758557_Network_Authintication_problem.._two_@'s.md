---
title: "Network Authintication problem.. two @'s"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by marwa7a on 2011-05-14
so I had an authentication problem and [Osberox]("http://ubuntuforums.org/member.php?u=1299934") helped me solve it here: [http://ubuntuforums.org/showthread.php?p=10816082#post10816082](http://ubuntuforums.org/showthread.php?p=10816082#post10816082) but now I'm stuck in an amazingly silly problem..
this is the etc/apt/apt.conf file:
 ```

Acquire::http::proxy "http://user@user:pass@pass@172.16.1.5:8080/";
Acquire::ftp::proxy "ftp://user@user:pass@pass@172.16.1.5:8080/";
Acquire::https::proxy "https://user@user:pass@pass@172.16.1.5:8080/";
```

my network authentication password is two words separated by an '@' and so now the system thinks the proxy is "pass@172.16.1.5" when in fact the password is "pass@pass".. the thing is I can't really change the password my self since they give it to us at the company and so now I have no idea what to do..

---

