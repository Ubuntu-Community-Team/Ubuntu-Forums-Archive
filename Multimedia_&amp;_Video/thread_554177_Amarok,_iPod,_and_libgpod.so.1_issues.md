---
title: "Amarok, iPod, and libgpod.so.1 issues"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by Adanac on 2007-09-18
I am having difficulty updating my iPod. It is one of the old nanos and it worked before, but now it doesn't work with Gtkpod or Amarok. I get the errror : 
KLibLoader could not load the plugin:
libamarok_ipod-mediadevice

Error message:
libgpod.so.1: cannot open shared object file: No such file or directory

After some digging, I discovered that I have libgpod.so.2 on my computer, and that many people are fixing the problem by compiling Amarok with the new libgpod. However, I don't know how to compile anything, so help do that, or any other way to fix this problem, would be appreciated.

---

### Post by Adanac on 2007-09-19
Alright I downgraded libgpod to 4.2 and that seems to be working, but I guess thats just a temporary fix for now. Any help is still welcomed.

---

### Post by nonewmsgs on 2007-09-30
there's all sorts of crazy issues happening because of that....im working on fixing mine so i can use gtkpod again

```

sudo cp /usr/lib/libgpod.so.2 /usr/lib/libgpod.so.1

```

that fixes it

---

