---
title: "How to find out what encryption wifi uses?"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by redstring on 2012-07-15
I'm trying to figure out what kind of encryption a wifi broadcast uses that isn't *my *wireless.  I know how to find it when using Windows 7 but on Xubuntu I'm a bit lost.

Thanks

---

### Post by steeldriver on 2012-07-15
if you're using Network-Manager then you can type

```
nm-tool
```

which will list (among other things) all the visible access points / encryption standards

---

### Post by redstring on 2012-07-21
> **steeldriver said:**
> if you're using Network-Manager then you can type

```
nm-tool
```which will list (among other things) all the visible access points / encryption standards

  Thanks, just what I needed.

---

