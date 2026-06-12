---
title: "Networktools not working????"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by crazy bird on 2011-12-19
Hi, 
I've just installed these  programs: nictools-pci and nictools-nopc. But when i want to start these programs in a terminal i get as respond back: **nictools-pci: command not found**. How can Ubuntu not find a program which i just installed? And where did it get installed? Which folder?

---

### Post by jonobr on 2011-12-19
In a terminal , try typing 

```
which
```
and then the program name , it should show you where it is.

If its in a location not in your path, you will need to update your path.

---

### Post by crazy bird on 2011-12-19
> **jonobr said:**
> In a terminal , try typing 

```
which
```and then the program name , it should show you where it is.

If its in a location not in your path, you will need to update your path.

No location given. What seems the problem??

---

### Post by jonobr on 2011-12-19
maybe try

```
sudo find / -name nictools* 
```

see if that spits out anything of interest...

---

### Post by crazy bird on 2011-12-21
This is what i get:

> 
/usr/share/doc/nictools-nopci
/usr/share/doc/nictools-pci
/var/cache/apt/archives/nictools-nopci_1.3.3-1_i386.deb
/var/cache/apt/archives/nictools-pci_1.3.8-1.2_i386.deb
/var/lib/dpkg/info/nictools-pci.prerm
/var/lib/dpkg/info/nictools-nopci.postrm
/var/lib/dpkg/info/nictools-pci.postrm
/var/lib/dpkg/info/nictools-pci.postinst
/var/lib/dpkg/info/nictools-nopci.prerm
/var/lib/dpkg/info/nictools-pci.md5sums
/var/lib/dpkg/info/nictools-nopci.preinst
/var/lib/dpkg/info/nictools-nopci.postinst
/var/lib/dpkg/info/nictools-pci.preinst
/var/lib/dpkg/info/nictools-nopci.list
/var/lib/dpkg/info/nictools-pci.list
/var/lib/dpkg/info/nictools-nopci.md5sums


---

### Post by jonobr on 2011-12-21
Hi 

I noticed a post saying the author of these tools has not been active since 2009....

Anyway,


could you try

```
dpkg -s nictools-pci
```

---

