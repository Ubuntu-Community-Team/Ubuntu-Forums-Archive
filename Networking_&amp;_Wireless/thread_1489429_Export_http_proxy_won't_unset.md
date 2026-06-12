---
title: "Export http_proxy won't unset"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by Brodie337 on 2010-05-21
Hi all, I've got a funny problem here.

I use my laptop through a proxy and at home I don't. I've set the proxy at uni using export http_proxy="...", as well as ftp and https proxies. Now I'm at home, I go to unset them by typing export http_proxy="" and that works, until I close and reopen terminal, where "export" shows the proxy still set.

Any help would be much appreciated.

---

### Post by anomie on 2010-05-21
What OS / version? What does **echo $SHELL** say? 

Also check to see if you're setting http_proxy in one of your shell startup files. 
```
$ grep 'http_proxy' ~/.*
```

---

