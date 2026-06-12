---
title: "proxy settings"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by Abdullah Al-dughiyem on 2010-06-02
Hello 
I am using lubuntu I would like to ask how can i change the  system proxy settings to connect to a network.
I have done this for firefox and it worked . but it seems that the system did not change the settings in other word wen i want to update some packages the connection will time due to a proxy .

---

### Post by areskz on 2010-06-06
Developers have this in todo-list, so we have to wait, I suppose.

By the way, you are able to use aptitude behind a proxy. Just add your proxy settings to a file **/etc/apt/apt.conf**
It should look like this:

```
ACQUIRE {http::proxy "http://user:password@proxy:port/"
}
```

---

### Post by til on 2010-06-07
> **areskz said:**
> Developers have this in todo-list, so we have to wait, I suppose.

By the way, you are able to use aptitude behind a proxy. Just add your proxy settings to a file **/etc/apt/apt.conf**
It should look like this:

```
ACQUIRE {http::proxy "http://user:password@proxy:port/"
}
```

Thanks man! That worked for me.

---

