---
title: "How do U install xmms in ubuntu 8.10"
date: 2008-11-27
forum: Multimedia Software
---

### Post by vistadude on 2008-11-27
I keep trying sudo apt-get install xmms but what i end up getting is 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

---

### Post by mgmiller on 2008-11-27
A quick trip to synaptic shows that xmms has been replaced by xmms2.  You could command line install that one alone, and it should bring it all its dependencies.  

After you install it, if you search in synpatic for xmms2, you will find a whole shopping list of associated addons for it.

---

### Post by vistadude on 2008-11-27
thx, i turns out if i replace it with the fallowing it works great

```
sudo apt-get install xmms2
```

---

