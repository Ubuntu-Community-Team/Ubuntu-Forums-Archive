---
title: "Pidgin cannot start"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by mzar on 2008-12-17
Hi,

I've problem with my pidgin. It latest from package install. Today when i click pidgin it now appear. The i test from terminal. The error show "segmentation fault".

So i decide to install 2.5.2 version. But it keep tell 
```

checking for GTK... no
no
configure: error:

You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you want to build only Finch then specify --disable-gtkui when running configure.
```

I dont know what it's mean by that. Anyone can help me?

---

### Post by ibutho on 2008-12-17
You need to install libgtk2.0-dev to resolve that problem.

---

### Post by mzar on 2008-12-18
Also it show it need pargo and cairo. Is it has in package manager? The current version that come with ubuntu got bug.

I have to upgrade to the latest version. But so tricky want to install from source. Not available for .deb.

---

### Post by kevdog on 2008-12-18
You want to compile:

[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

It takes a little while to compile, but you end up with a much better version!!!

---

