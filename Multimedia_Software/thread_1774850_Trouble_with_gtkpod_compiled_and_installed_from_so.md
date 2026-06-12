---
title: "Trouble with gtkpod compiled and installed from source"
date: 2011-06-03
forum: Multimedia Software
---

### Post by ub-newb on 2011-06-03
Hi, I successfully compiled gtkpod 2.0.1 from source, and I thought everything went hunky-dory (my first attempt at compiling). After installation, when I launch the program I get this error:

```
/usr/local/bin/gtkpod: error while loading shared libraries: libgtkpod.so.1: cannot open shared object file: No such file or directory
```

when I browse to /usr/local/lib, I can see libgtkpod.so.1, which is a link pointing to libgtkpod.so.1.0.0

I don't know enough to know what to do. I did previously have gtkpod 1.0 intstalled from the ubuntu repositories, however I did uninstall it before compiling 2.0.1. Perhaps I didn't uninstall it correctly?

---

### Post by mc4man on 2011-06-03
for starters run 
```
sudo ldconfig
```

---

### Post by ub-newb on 2011-06-04
> **mc4man said:**
> for starters run 
```
sudo ldconfig
```

That worked great!... however I cannot add files or directories to the main library or my ipod... when I select items to add, nothing happens.

gtkpod retained the database from my previous install of 1.0.0, so obviously I did not completely remove that before installing 2.0.1.

Is my install broken?

---

